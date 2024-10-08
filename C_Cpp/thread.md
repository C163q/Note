# 目录
- [目录](#目录)
- [MSVC中的std::thread](#msvc中的stdthread)
  - [构造与线程创建](#构造与线程创建)
    - [前置知识](#前置知识)
      - [unique\_ptr](#unique_ptr)
      - [Windows中针对C/C++的启动线程API](#windows中针对cc的启动线程api)
      - [完美转发(forward)](#完美转发forward)
      - [元组(tuple)](#元组tuple)
      - [std::integer\_sequence](#stdinteger_sequence)
      - [std::invoke](#stdinvoke)
    - [构造函数](#构造函数)
    - [\_Get\_invoke](#_get_invoke)
    - [其他问题](#其他问题)


# MSVC中的std::thread
## 构造与线程创建
### 前置知识
#### unique_ptr
使用`std::unique_ptr`类能够传入一个指针`ptr`,当该类执行析构时,会调用`delete ptr;`实现对内存的回收.

例如:
````C++
void func() {
    ::std::unique_ptr<int> p(new int(2));
    // do something
} // 此处局部变量unique_ptr析构,会执行delete.
````

使用`release()`将指针释放,`std::unique_ptr`将不再拥有对内存的管理权.

例如:
````C++
void func() {
    ::std::unique_ptr<int> p(new int(2));
    int* pi = p.release();
    delete pi;  // 必须手动delete
}
````

#### Windows中针对C/C++的启动线程API
Windows针对C/C++有专门的启动线程的API: `_beginthreadex`.

函数申明如下:
````C
_ACRTIMP uintptr_t __cdecl _beginthreadex(
    _In_opt_  void*                    _Security,
    _In_      unsigned                 _StackSize,
    _In_      _beginthreadex_proc_type _StartAddress,
    _In_opt_  void*                    _ArgList,
    _In_      unsigned                 _InitFlag,
    _Out_opt_ unsigned*                _ThrdAddr
    );
````
细节可以查看[MSDN](https://learn.microsoft.com/en-us/cpp/c-runtime-library/reference/beginthread-beginthreadex?view=msvc-170)

现在只关心参数`_StartAddress`和`_ArgList`.

`_StartAddress`的类型是`_beginthreadex_proc_type`即`unsigned(*)(void*)`的函数指针,返回值为`unsigned`,即线程运行结束的返回值,`void*`是指向存储的数据的指针.

`_ArgList`是要传入参数的列表,类型是`void*`,即指向传入参数的数据结构的指针.

#### 完美转发(forward)
不多赘述.

#### 元组(tuple)

#### std::integer_sequence

#### std::invoke

### 构造函数
MSVC中,构造函数如下:
````C++
template <class _Fn, class... _Args, enable_if_t<!is_same_v<_Remove_cvref_t<_Fn>, thread>, int> = 0>
_NODISCARD_CTOR_THREAD explicit thread(_Fn&& _Fx, _Args&&... _Ax) {
    _Start(_STD forward<_Fn>(_Fx), _STD forward<_Args>(_Ax)...);
}
````
其调用`_Start`函数,并用完美转发将参数原样传入.

此处`_Fn`是调用的函数,`_Args`参数包包含所有传入的参数.

`_Start`函数如下:
````C++
template <class _Fn, class... _Args>
void _Start(_Fn&& _Fx, _Args&&... _Ax) {
    using _Tuple                 = tuple<decay_t<_Fn>, decay_t<_Args>...>;
    auto _Decay_copied           = _STD make_unique<_Tuple>(_STD forward<_Fn>(_Fx), _STD forward<_Args>(_Ax)...);
    constexpr auto _Invoker_proc = _Get_invoke<_Tuple>(make_index_sequence<1 + sizeof...(_Args)>{});

    _Thr._Hnd =
        reinterpret_cast<void*>(_CSTD _beginthreadex(nullptr, 0, _Invoker_proc, _Decay_copied.get(), 0, &_Thr._Id));

    if (_Thr._Hnd) { // ownership transferred to the thread
        (void) _Decay_copied.release();
    } else { // failed to start thread
        _Thr._Id = 0;
        _Throw_Cpp_error(_RESOURCE_UNAVAILABLE_TRY_AGAIN);
    }
}
````
首先定义`_Tuple`是`tuple<decay_t<_Fn>, decay_t<_Args>...>`.

此处使用`decay_t`表明数据以函数传参形式传入,即以变量直接传入,将会导致复制构造.`std::ref()`传入为引用.`std::move()`传入为移动构造.

`auto _Decay_copied = _STD make_unique<_Tuple>(_STD forward<_Fn>(_Fx), _STD forward<_Args>(_Ax)...);`将所有参数(包括函数本身)整合至一个元组当中,该元组是通过`new`分配在堆中的,并存储到一个`unique_ptr`中.目的是当发生异常导致函数退出时,能够自动delete这个元组的内存.

`constexpr auto _Invoker_proc = _Get_invoke<_Tuple>(make_index_sequence<1 + sizeof...(_Args)>{});`给出了线程所调用的函数的内存地址,这个下面再讲解.

`_Thr._Hnd = reinterpret_cast<void*>(_CSTD _beginthreadex(nullptr, 0, _Invoker_proc, _Decay_copied.get(), 0, &_Thr._Id));`调用`_beginthreadex`来启动线程,返回值为线程的句柄.

下面,当线程句柄存在时,说明线程启动成功,此时数据的操作权转移给了其他线程,因此使用`(void) _Decay_copied.release();`来放弃对数据的控制.至于内存管理问题,下面再讲解.

若线程句柄为0,表明线程启动失败,抛出异常.

### _Get_invoke
为了获取所调用函数的地址,使用了`_Get_invoke`函数.该函数的声明为:
````C++
template <class _Tuple, size_t... _Indices>
_NODISCARD static constexpr auto _Get_invoke(index_sequence<_Indices...>) noexcept {
    return &_Invoke<_Tuple, _Indices...>;
}
````
即返回了`_Invoke<_Tuple, _Indices...>`函数的地址.其中`_Tuple`就是需要线程调用函数及其参数组成的元组的类型,`_Indices`是一个整数序列,通过`index_sequence<_Indices...>`构造而来,方便通过参数包依次调用元组内的内容.

`_Invoke`函数的声明如下:
````C++
template <class _Tuple, size_t... _Indices>
static unsigned int __stdcall _Invoke(void* _RawVals) noexcept /* terminates */ {
    // adapt invoke of user's callable object to _beginthreadex's thread procedure
    const unique_ptr<_Tuple> _FnVals(static_cast<_Tuple*>(_RawVals));
    _Tuple& _Tup = *_FnVals.get(); // avoid ADL, handle incomplete types
    _STD invoke(_STD move(_STD get<_Indices>(_Tup))...);
    _Cnd_do_broadcast_at_thread_exit(); // TRANSITION, ABI
    return 0;
}
````
按照要求,它应该是返回`unsigned`,接收一个`void*`的函数.

由于`void*`事实上是`_Decay_copied.get()`,即之前`unique_ptr`指向的`需要线程调用函数及其参数组成的元组`的指针,因此,此处直接将其类型转换为`_Tuple*`,并放入一个新的`unique_ptr`,这样,当线程(本意所要调用的函数,存在于元组中)退出后,上面再堆内存中创建的元组就会自动被释放.

最后,调用`std::invoke`,正式在新的线程中调用我们想要执行的函数.

### 其他问题

Q: 为什么元组需要创建在堆中?  
A: 如果创建在栈中,当`std::thread`的构造函数退出后,元组就会被释放,传入的参数无意义.如果直接使用原始数据,那么对于临时变量,也会被释放,因此创建在堆中最为合适.此外,新的线程拥有自己的栈,而堆是共享的,因此创建在堆中显然比在栈中更加合适.


