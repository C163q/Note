<head>
    <title>C++ Note Collection 1</title>
    <style type="text/css">
        body {
            font-family: "cascadia code", 幼圆, 宋体;
        }
        code {
            color: burlywood;
        }
    </style>
</head>

# 目录
- [目录](#目录)
- [底层内存管理](#底层内存管理)
	- [关于new](#关于new)
	- [关于delete](#关于delete)
	- [关于operator new和operator delete的结合性](#关于operator-new和operator-delete的结合性)
	- [关于new和delete的结合性](#关于new和delete的结合性)
	- [关于placement new](#关于placement-new)
	- [自定义operator new](#自定义operator-new)
	- [声明的注意事项](#声明的注意事项)
- [异常](#异常)
	- [异常安全](#异常安全)
- [协程(coroutine)](#协程coroutine)
	- [创建协程](#创建协程)
		- [promise\_type](#promise_type)
		- [coroutine\_handle](#coroutine_handle)
		- [co\_await返回值要求](#co_await返回值要求)
		- [协程步骤](#协程步骤)
		- [简单示例](#简单示例)
		- [变量作用域相关问题](#变量作用域相关问题)
		- [co\_yield](#co_yield)
		- [co\_return](#co_return)
		- [数据传输示例](#数据传输示例)
- [并发(concurrency)](#并发concurrency)
	- [shared state(共享状态)](#shared-state共享状态)
	- [async()](#async)
		- [发射策略](#发射策略)
		- [处理异常](#处理异常)
		- [传递实参](#传递实参)
	- [future](#future)
		- [get(), wait()](#get-wait)
		- [wait\_for(), wait\_until()](#wait_for-wait_until)
		- [future所有操作](#future所有操作)
	- [future\_status](#future_status)
	- [shared\_future](#shared_future)
	- [thread](#thread)
		- [Detached Thread](#detached-thread)
		- [thread ID](#thread-id)
		- [thread可用操作](#thread可用操作)
	- [promise](#promise)
		- [promise所有操作](#promise所有操作)
	- [packaged\_task](#packaged_task)
		- [packaged\_task所有操作](#packaged_task所有操作)
	- [this\_thread命名空间](#this_thread命名空间)
	- [线程同步化与并发问题](#线程同步化与并发问题)
		- [为什么会有问题](#为什么会有问题)
		- [有什么问题](#有什么问题)
			- [未同步化的数据访问](#未同步化的数据访问)
			- [写至半途的数据](#写至半途的数据)
			- [重新安排的语句](#重新安排的语句)
			- [解决问题所需要的性质](#解决问题所需要的性质)
			- [volatile与并行](#volatile与并行)
	- [Mutex和Lock](#mutex和lock)
		- [recursive(递归的) lock](#recursive递归的-lock)
		- [尝试性lock及带时间性的lock](#尝试性lock及带时间性的lock)
		- [处理多个lock](#处理多个lock)
		- [lock\_guard](#lock_guard)
		- [unique\_lock](#unique_lock)
		- [所有mutex](#所有mutex)
		- [call\_once](#call_once)
	- [Condition Variable](#condition-variable)
		- [condition\_variable所有操作](#condition_variable所有操作)
		- [condition\_variable\_any](#condition_variable_any)
	- [Atomic](#atomic)
		- [Atomic的C风格接口](#atomic的c风格接口)
		- [低层接口](#低层接口)
- [术语](#术语)
	- [trivial（平凡的）](#trivial平凡的)
	- [未定义行为(ud)](#未定义行为ud)


# 底层内存管理
## 关于new
`new`可以视作是`malloc`和构造的结合

`operator new`可以视作就是malloc，它（其中一个重载）输入的参数为void*，输出void*。例如：
```C++
class A;
::A* p = static_cast<::A*>(operator new(sizeof(A) * 2));
```

## 关于delete
`delete`可以视作是析构与`free`的结合

对于`delete[]`，其释放内存的方向为从数组的最后到最前

`operator delete`可以视作就是`free`，它（其中一个重载）是void*

## 关于operator new和operator delete的结合性
（以下仅针对某个重载）

经过实测，`operator new`与malloc或calloc可互换

`operator delete`与free可互换

例如（以下代码实测可运行）：
```C++
::A* p = static_cast<::A*>(operator new(sizeof(A) * 2));
p[0] = ::A(1);
p[1] = ::A(2);
std::cout << "test" << std::endl;
std::cout << p[0].a << std::endl;
for (int i = 1; i >= 0; --i) {
	p[i].~A();
}
free(p);
```
```C++
::A* p = static_cast<::A*>(calloc(2, sizeof(A)));
p[0] = ::A(1);
p[1] = ::A(2);
std::cout << "test" << std::endl;
std::cout << p[0].a << std::endl;
for (int i = 1; i >= 0; --i) {
	p[i].~A();
}
operator delete(p);
```

## 关于new和delete的结合性
`new`和`delete`理论上不能与`malloc`和`free`互换，因此与`operator new`和`operator delete`不兼容

***(强烈警告该做法错误)*** 在特定情况下使用`operator new`和`delete`或者`new`和`operator delete`并无问题，只要做好空间管理，但面对**以下情况**：

对于已用`operator new`分配空间的位置，由于未初始化，使用`delete`将导致其调用析构函数时访问未初始化变量。此外，对于含有virtual方法的继承类，将导致其调用析构函数指针发生错误（析构函数指针未初始化）

对于已用`operator new`分配空间的位置，使用`delete[]`初始化将会因为未知的原因，导致先释放空间，后析构，导致析构函数成员访问异常。 ***待寻找原因***

对于使用`new[]`分配空间而用`operator delete`释放空间是不合法的（两者不匹配），在MSVC中将导致调用`__debugbreak()`

## 关于placement new
语法: `new(void*) T();`,`T()`为构造函数.

`placement new`的目的是调用构造函数并将其置于指定内存中.

不使用`=`直接赋值的原因是对于类似`std::unique_ptr`这样的类来说,赋值会使它处理原本处于该内存空间的元素(对于`std::unique_ptr`来说,是析构其指向的元素).但对于使用`operator new`的元素来说,所谓的元素并不存在,则可能会导致未定义的情况发生.

使用例:
````C++
::std::string* ps{ static_cast<::std::string*>(::operator new(sizeof(::std::string))) };	// 分配内存
::new(ps) ::std::string("PLACEMRNT NEW");	// placement new
::std::cout << *ps << ::std::endl;
::delete ps;	// 内存回收
````

## 自定义operator new
一个`operator new`的自定义重载可能如下:
````C++
void* operator new(size_t size) {
	auto handler = ::std::get_new_handler();	// 获取new_handler,这个是由用户自己定义的,默认为空
	int retry{ 3 };		// 尝试申请3次
	while (retry--) {
		void* ptr = malloc(size);	// 申请空间
		if (ptr) {		// 申请成功即返回
			return ptr;
		}
		if (handler) {	// 申请失败若有new_handler,则调用
			handler();
		}
	}
	throw ::std::bad_alloc();	// 全部失败则抛出异常
}
````

new_handler由用户自己定义
````C++
::std::set_new_handler([] { ::std::cout << "do something..." << ::std::endl; });
````

## 声明的注意事项
考虑以下代码:
````C++
// a.h
class A;

// b.h
class B {
private:
	A* p = nullptr;
public:
	B();
	~B() { delete p; }
	void show();
};

// main.cpp
int main() {
	B b;
	b.show();
	return 0;
}

// a.cpp
class A {
public:
	A() { std::cout << "A()" << std::endl; }
	~A() { std::cout << "~A()" << std::endl; }
	void show() { std::cout << 1 << std::endl; }
};

// b.cpp
B::B() { p = new A(); }
void B::show() { p->show(); }
````
注释表示的是各个声明和定义所在的文件.

上述代码的执行结果为:
```
A()
1
```
此外,编译器还会警告:
```
C4150	删除指向不完整“A”类型的指针；没有调用析构函数
```
该警告表明对于`B`而言,由于`~A()`未定义,因此`delete p`实际上**没有调用析构函数**,可能会导致内存泄漏.

正确的写法:
````C++
// a.h
class A;

// b.h
class B {
private:
	A* p = nullptr;
public:
	B();
	~B();					// 此处修改
	void show();
};

// main.cpp
int main() {
	B b;
	b.show();
	return 0;
}

// a.cpp
class A {
public:
	A() { std::cout << "A()" << std::endl; }
	~A() { std::cout << "~A()" << std::endl; }
	void show() { std::cout << 1 << std::endl; }
};

// b.cpp
B::B() { p = new A(); }
void B::show() { p->show(); }
B::~B() { delete p; }		// 此处修改
````
运行结果为:
```
A()
1
~A()
```
行为正确.

<br>

# 异常
## 异常安全
考虑对于以下自定义vector中的_copy函数：
```C++
namespace my {
	template<typename Ty>
	class vector
	{
	public:
		using value_type = Ty;
		using reference = Ty&;
		using const_reference = const Ty&;
		// ...
	private:
		Ty* _data;
		::size_t _size;
		::size_t _capacity;
	public:
		// ...
	private:
		void _copy(const vector& rhs) {
			_data = static_cast<Ty*>(::operator new(rhs._capacity * sizeof(Ty)));

			_size = 0;
			_capacity = rhs._capacity;

			try
			{
				for (::size_t i = 0; i < rhs._size; ++i) {
					::new(_data + i) Ty(rhs._data[i]);
					++_size;
				}
			}
			catch (...)
			{
				for (::size_t i = 0; i < _size; ++i) {
					_data[i].~Ty();
				}

				::operator delete(_data);
                throw;
			}
		}
		// ...
	};
}
```
_copy函数将vector复制到一个空vector中。对于将rhs中的元素赋值构造到vector管理的数组中时，若产生异常，将导致已分配的内存未回收，因此非异常安全。可以用上述方法，当赋值构造元素时，捕获所有异常，并析构已分配元素、回收内存，最终将异常重新抛出，以实现异常安全。

# 协程(coroutine)
协程是一个能够挂起和恢复的特殊函数.协程是无栈的.定义一个协程,需要使用关键词`co_await`或`co_yield`或`co_return`.

例如:
````C++
CoRet func() {
	Input input;
	co_return input;
}

CoRet foo() {
	Input input;
	co_yield input;
}
````

## 创建协程
在一个协程中,如果没有显式定义`CoRet::promise_type`(即`承诺对象`,承诺对象和`std::promise`没有任何关系),编译器会隐式创建`std::coroutine_traits<CoRet, Args...>::promise_type`.

### promise_type
`promise_type`具体包含以下函数:
- `initial_suspend`: 协程在创建并产生`promise_type`时,会`co_await`并执行该方法(即`co_await promise.initial_suspend();`),指示协程创建时其行为.包括:
	- `suspend_never`: 协程创建后继续执行.
	- `suspend_always`: 协程创建后挂起(暂停).
	- `自定义返回类型`
- `final_suspend`: 协程在执行完所有代码之后(或使用`co_return`后),会`co_await`并执行该方法(即`co_await promise.final_suspend();`),指示协程结束时其行为.此时恢复协程是ud.包括:
	- `suspend_never`: 协程结束后立刻销毁.
	- `suspend_always`: 协程结束后挂起并等待销毁.
	- `自定义返回类型`
- `unhandled_exception`: 协程的异常处理.
- `get_return_object`: 获取协程的返回值.
- `return_value`或`return_void`: 返回值或空(两者只能存在其一).

### coroutine_handle
`coroutine_handle`: 一个标准库的模板类,用于指代暂停或执行中的协程,包含方法:
- `resume`: 控制协程继续执行.
- `operator()`: 等价于`resume()`.
- `promise`: 返回协程的`promise`.
- `from_promise`: [static]由协程的`promise`对象创建`coroutine_handle`.
- `address`: 导出底层地址,即支撑协程的指针.
- `from_address`: [static]从指针导入协程.
- `done`: 协程在其最终暂停点暂停则返回`true`,否则`false`.*注意:函数`co_await promise.final_suspend();`执行且返回`suspend_never`导致协程销毁,其返回值也为`false`.*

### co_await返回值要求
`co_await`返回值要求:  
`suspend_never`,`suspend_always`满足`co_await`的返回值要求.`自定义返回类型`也需要满足要求,具体为:
- `await_ready`: 返回`bool`类型,表明遇到`co_await`时,是否需要挂起协程.`true`表明已经准备完毕,可以向下执行.`false`表明需要挂起等待.
- `await_suspend`: 指明在协程挂起并跳转前执行的操作.其参数为`协程的handle`,可以的值例如`coroutine_handle<CoRet::promise_type>`.其返回值为协程挂起后跳转的地方(如另一个协程的handle),若为`void`,则跳转回调用方.若为`bool`,则若值为`true`,将控制返回给当前协程的调用方/恢复方;值为`false`,恢复当前协程.
- `await_resume`: 当协程重新获得控制时(无论协程是否被暂停过),调用`await_resume()`,它的结果就是整个 `co_await`表达式的结果,其值被协程内部获得.

即`co_await expr`执行后,按照如下顺序运行: `expr.await_ready()`,若为`true`,调用`expr.await_resume()`;若为`false`,调用`expr.await_suspend()`,并挂起,当协程恢复时,调用`expr.await_resume()`.

### 协程步骤
1. 用`operator new`分配协程状态对象(`CoRet`).
2. 将所有函数形参复制到协程状态中:按值传递的形参被移动或复制,按引用传递的形参保持为引用.
3. 调用承诺对象`promise`的构造函数.如果承诺类型拥有接收所有协程形参的构造函数,那么以复制后的协程实参调用该构造函数.否则调用其默认构造函数.
4. 调用`promise.get_return_object()`并将结果保存在局部变量中(该调用的结果将在协程首次暂停时返回给调用方).至此并包含这个步骤为止,任何抛出的异常均传播回调用方,而非置于承诺中.
5. 调用`promise.initial_suspend()`并`co_await`它的结果.一般返回`std::suspend_always`或`std::suspend_never`.
6. 当`co_await promise.initial_suspend()`恢复时,开始协程体的执行.
7. 当协程抵达`co_return`语句时,它进行下列操作:
	- 对下列情形调用`promise.return_void()`:
		- `co_return;`
  		- `co_return expr;`,其中`expr`具有`void`类型.
    - 或对于`co_return expr;`,其中`expr`具有非void类型时,调用`promise.return_value(expr)`
8. 以创建顺序的逆序销毁所有具有自动存储期的变量.
9. 调用`promise.final_suspend()`并`co_await`它的结果.

### 简单示例
示例:
````C++
struct CoRet {
	struct promise_type	{
		::std::suspend_never initial_suspend() { return {}; }
		::std::suspend_never final_suspend() noexcept { return {}; }
		void unhandled_exception() {}
		CoRet get_return_object() {
			return { ::std::coroutine_handle<promise_type>::from_promise(*this) };
		}
		void return_void() {}
	};
	::std::coroutine_handle<promise_type> handle;
};

struct Input {
	bool await_ready() { return false; }
	void await_suspend(::std::coroutine_handle<CoRet::promise_type> h) {}
	int await_resume() { return 0; }
};

CoRet myCoRoutine() {
	Input input;
	int v = co_await input;
	::std::cout << "Coroutine " << v << ::std::endl;
}

int main() {
	auto ret = myCoRoutine();
	::std::cout << "Start a coroutine..." << ::std::endl;
	ret.handle();
}
````

### 变量作用域相关问题
示例:
````C++
struct S
{
    int i;
    coroutine f()
    {
        std::cout << i;
        co_return;
    }
};

void bad1()
{
    coroutine h = S{0}.f();
    // S{0} 被销毁
    h.resume(); // 协程恢复并执行了 std::cout << i，这在释放之后使用了 S::i
    h.destroy();
}
 
coroutine bad2()
{
    S s{0};
    return s.f(); // 返回的协程不能被恢复执行，否则会导致释放后使用
}
 
void bad3()
{
    coroutine h = [i = 0]() -> coroutine // 一个 lambda，同时也是个协程
    {
        std::cout << i;
        co_return;
    }(); // 立即调用
    // lambda 被销毁
    h.resume(); // 释放后使用了 (匿名 lambda 类型)::i
    h.destroy();
}
 
void good()
{
    coroutine h = [](int i) -> coroutine // i 是一个协程形参
    {
        std::cout << i;
        co_return;
    }(0);
    // lambda 被销毁
    h.resume(); // 没有问题，i 已经作为按值传递的形参被复制到协程帧中
    h.destroy();
}
````

### co_yield
`co_yield`表达式向调用方返回一个值并暂停当前协程.

`co_yield expr`等价于`co_await promise.yield_value(expr)`。
因此必须存在`yield_value`.

`yield_value`: 返回一个满足`co_await返回值要求`的类.若要返回数据,考虑在`promise`中定义一个数据类型,在该函数中赋予特定值.

### co_return
`co_return`用于结束一个协程.

`co_return;`或`co_return [void];`将调用`promise.return_void`.
`co_return expr;`将调用`promise.return_value(expr)`.
注意,两者的返回值为`void`.若要传递数据,考虑在`promise`中定义一个数据类型,在该函数中赋予特定值.

具体调度见:[协程步骤](#协程步骤).

### 数据传输示例
示例:
````C++
struct CoRet {
	struct promise_type	{
		int _res = 0;
		int _out = 0;

		::std::suspend_never initial_suspend() { return {}; }
		::std::suspend_always final_suspend() noexcept { return {}; }
		void unhandled_exception() {}
		CoRet get_return_object() {
			return { ::std::coroutine_handle<promise_type>::from_promise(*this) };
		}
		void return_value(int r) {
			_res = r;
		}
		::std::suspend_never yield_value(int v) {
			_out = v;
			return {};
		}
	};
	::std::coroutine_handle<promise_type> handle;
};

struct Input {
	int _guess;
	bool await_ready() { return false; }
	void await_suspend(::std::coroutine_handle<CoRet::promise_type> h) {}
	int await_resume() const { return _guess; }
};

CoRet guess_num(Input& input) {
	::std::default_random_engine re{ static_cast<unsigned>(::std::time(nullptr) % (static_cast<unsigned long long>(::std::numeric_limits<unsigned>::max()) + 1))};
	::std::uniform_int_distribution<int> ud(0, 50);
	int rn = ud(re);
	int res = -1;
	for (int i = 5; i > 0; --i) {
		co_yield i;
		int guess = co_await input;
		res = (guess == rn ? 0 : (guess > rn ? 1 : -1));
		co_yield res;
		co_await ::std::suspend_always{};
		if (!res) break;
	}
	co_return rn;
}

int main() {
	Input g{};
	CoRet h = guess_num(g);
	while (!h.handle.done()) {
		std::cout << h.handle.promise()._out << " times left." << "\nGuess:";
		int MyGuess{};
		std::cin >> MyGuess;
		g._guess = MyGuess;
		h.handle();
		int hint = h.handle.promise()._out;
		if (!hint) {
			std::cout << "Right." << std::endl;
		}
		else if (hint == 1) {
			std::cout << "Should be smaller." << std::endl;
		}
		else {
			std::cout << "Should be larger." << std::endl;
		}
		h.handle();
	}
	std::cout << "The right answer: " << h.handle.promise()._res << std::endl;
	h.handle.destroy();
	return 0;
}
````

# 并发(concurrency)
## shared state(共享状态)
`shared state`能够和"处理其结果"(`asynchronous return object`)的对象相互沟通.`share state`通常被实现为一个`reference-counted object`(当它被最后一个使用者释放时即被销毁).

详见:[C++草案-Concurrency support library.Futures.Shared state](https://eel.is/c++draft/futures.state)

许多`未来体(futures)类`使用一些状态来交换值.这些`shared state(共享状态)`包含`状态信息`和`结果(有可能是void)`或`异常`.
> 1. `future`, `shared_future`, `promise`, `package_task`都会引用一个`shared state`.
>
> 2. 所谓`结果`,可以是任何类型的对象,甚至是待计算结果的函数.

一个`异步返回对象(asynchronous return object)`能够读取`shared state`当中的结果.`异步返回对象`的等待函数会隐式阻塞线程以等待共享状态处于`ready`状态.如果等待函数可能会在共享状态处于`ready`前就返回了(例如`timeout`),那么该函数就是`timed waiting function(定时等待函数)`,否则,它是`non-timed waiting function(非定时等待函数)`.

一个`异步提供器(asynchronous provider)`是一个为`shared state`提供结果的对象.该结果由异步提供器各自的函数所设置.
> `promise`和`packaged_task`属于`asynchronous provider`.

这意味着设置`shared state`的结果由创建state对象的类或函数指定.

当一个`异步返回对象`或一个`异步提供器`释放了其共享对象,则:
- 如果其持有`shared state`的最后一个引用,则`shared state`被摧毁.
- 其放弃指向`shared state`的引用.
- 上面的操作不会影响`shared state`变成`ready`的状态.但当满足以下所有条件时,该操作会被阻止:
  - `shared state`是通过调用`std::async`创建的.
  - `shared state`还未具有`ready`状态.
  - 该引用是`shared state`的最后一个引用.

当一个`异步提供器`将要把`shared state`设置为`ready`状态,这表明:
- 其将`shared state`设置为`ready`.
- 其取消任何等待`shared state`变成`ready`的`执行代理(execution agents)`的阻塞状态.

当一个`异步提供器`要终止其`shared state`,这表明:
- 如果状态不是`ready`,则其:
  - 存储一个`future_error`类型的异常并夹带错误码`broken_promise`.
  - 使`shared state`为`ready`.
- 其释放共享对象.

`shared state`处于`ready`状态当且仅当持有一个值或一个异常以待被获取.

等待`shared state`的状态为`ready`可能在等待线程会调用代码来计算结果(如果指定了相关代码).

调用函数设置`shared state`的结果(包括`ready`状态)异步于调用函数获取`shared state`的状态.调用函数存储结果至`shared state`异步于调用函数等待并返回其结果.

一些函数(例如`promise::set_value_at_thread_exit`)直至线程结束时才将`shared state`设置为`ready`.具有线程生存期的变量在这些函数将`shared state`设置为`ready`前析构.

获取相同`shared state`的结果可能会导致`冲突(conflict)`.
> 这显式指明仅能允许在避免`data race`的条件下`shared state`的结果在引用`shared state`的对象中可见.  
> 例如,并发引用`shared_future::get()`的返回值必须是只读的或者提供额外的同步化.

## async()
`async()`位于`<future>`头文件.用于尝试启动一个新的线程.其参数为函数或可调用对象及其参数,返回值为`future`,用于返回`async()`调用的函数的返回值或异常(如果抛出的话).如果调用函数无返回值,则返回其特化`future<void>`.

其声明为:
````C++
template< class F, class... Args >
std::future<RetType> async( F&& f, Args&&... args );
````

调用`async()`函数会产生两种结果:
- 无法开始一个新的线程,启动被延后.
- 启动一个新的线程.

使用`future<>.get()`方法将等待线程结束并获取其返回值,使用该方法会产生三种结果:
- 线程启用并已返回结果,则立即返回结果.
- 线程启用但尚未结束,`get()`会引发停滞待线程返回结果.
- 线程尚未启动,则会被强制启动,如同同步调用.`get()`会引发停滞待线程返回结果.

例如:
````C++
int do_something(char a) {
	std::default_random_engine re(a);
	std::uniform_int_distribution<int> ud(100, 300);
	for (int i = 0; i < 10; ++i) {
		std::this_thread::sleep_for(std::chrono::milliseconds(ud(re)));
		std::cout << a << ' ';
	}
	return ud(re);
}
int main() {
	std::future<int> f1 = std::async(do_something, '.');
	std::future<int> f2 = std::async(do_something, ',');
	std::cout << f1.get() << std::endl;
	std::cout << f2.get() << std::endl;
}
````
可能的输出:
```
. , . , , . , . , . , . , , . , . , . . 288
222
```
对于仅支持单线程的设备(多线程启动失败):
```
. . . . . . . . . . 288
, , , , , , , , , , 222
```

当未调用`future<>.get()`方法获取线程结果(`future<void>`包括在内)但`future`即将被销毁时:
- 如果`future`无共享状态,则直接销毁.否则,
- 如果`future`不是通过`async()`获得的,直接销毁.否则,
- 如果线程已经启动但未完成,且`future`为`shared state`的最后持有者,则调用`future<>.wait()`等待线程结束后销毁.否则
- 直接销毁`future`.

因此,如果`async()`返回的`future`未被接收,则如果线程未启动,函数不会被调用.如果线程被启动,则等待线程结束:
````C++
int do_something(int a) {
	::std::this_thread::sleep_for(std::chrono::seconds(a));
	return a + 1;
}
int main() {
	auto f = std::async(do_something, 2);
	std::cout << 0 << std::endl;
}
````

### 发射策略
允许向`async()`函数传入发射策略,函数的重载为:
````C++
template< class F, class... Args >
std::future<RetType> async( std::launch policy, F&& f, Args&&... args );
````
发射策略`std::launch::async`强制`async()`以异步的方式启动目标函数:
````C++
auto res = std::async(std::launch::async, func);
````
如果异步调用无法实现,则抛出异常`std::system_error`并带差错码`std::async::resource_unavailable_try_again`.

该策略下被启动的线程保证在程序结束前完成,除非程序中途失败(abort).

发射策略`std::launch::deferred`强制推迟执行线程:
````C++
auto res = std::async(std::launch::deferred, func);
````
这保证函数绝不会在调用`get()`或`wait()`前启动.

发射策略`std::launch::async | std::launch::deferred`与不传入策略的效果相同.表示如果创建新线程行不通的话,则会推迟启动,而不是抛出异常.

发射策略为`0`或其他值是未定义行为.

### 处理异常
当`async()`调用的函数内部抛出异常时,对`future`调用`get()`会将异常传播出去:
````C++
int do_something(int a) {
	std::default_random_engine re(a);
	std::uniform_int_distribution<int> ud(100, 300);
	throw std::exception();
	return ud(re);
}
int main() {
	std::future<int> f = std::async(do_something, 2);
	::std::cin.get();
	try {
		f.get();
	}
	catch (std::exception&) {
		std::cout << "Exception occurred." << std::endl;
	}
}
````

### 传递实参
上述例子中已经展示了传递实参的方法.即对于无发射策略的重载,第一个参数为函数或可调用对象,参数包传入其参数.对于有发射策略的重载,第一个参数为发射策略,第二个参数为函数或可调用对象,参数包传入其参数.

此外,对于参数包内的参数函数,`async()`函数会将其**退化为右值**,对于返回值,也会将其退化为右值.因此,想要通过引用的方式传入参数需要使用`std::ref()`.  

例如:  
参数被退化:
````C++
void do_something(const int& a) {
	std::cout << "thread: " << &a << std::endl;
}
int main() {
	int a = 2;
	std::cout << "main(): " << &a << std::endl;
	auto f = std::async(do_something, a);
	f.get();
}
````
可能的输出:
```
main(): 000000638A1BF8F4
thread: 00000175AF657948
```

使用`std::ref`将参数包装:
````C++
void do_something(const int& a) {
	std::cout << "thread: " << &a << std::endl;
}
int main() {
	int a = 2;
	std::cout << "main(): " << &a << std::endl;
	auto f = std::async(do_something, std::ref(a));
	f.get();
}
````
可能的输出:
```
main(): 000000AA2BB7F7F4
thread: 000000AA2BB7F7F4
```
使用lambda引用捕获:
````C++
void do_something(const int& a) {
	std::cout << "thread: " << &a << std::endl;
}
int main() {
	int a = 2;
	std::cout << "main(): " << &a << std::endl;
	auto f = std::async([&a] {do_something(a); });
	f.get();
}
````
可能的输出:
```
main(): 0000001DEDFBF9D4
thread: 0000001DEDFBF9D4
```
但注意,如果函数本身参数就不是引用,即使是`std::ref`也无能为力:
````C++
void func(int a) {
	std::cout << &a << std::endl;
}
int main() {
	int a = 0;
	std::cout << &a << std::endl;
	func(std::ref(a));
}
````
可能的输出
```
000000D8505AF904
000000D8505AF8E0
```

**注意**:使用引用传递参数时,可能会发生`data race`.

允许传递成员方法,这种情况下,位于成员函数名称之后的第一个实参必须是个`reference`或`pointer`,指向某个对象:
````C++
class X {
public:
	void mem(int num);
};
X x;
auto a = std::async(&X::mem, x, 42);
````

## future
`future`是`asynchronous return object`,能够获取其指向的`shared state`中存储的结果或异常.可被`std::async()`或`std::package_task`或`promise`创建出来.

所谓`future`,即为保存某个将来时刻的结果,其结果可能并不存在,但`future`允许在`shared state`为`ready`时返回该结果(或异常).

返回值(抛出异常除外):
- 若`future`的结果为无物,则使用特化`future<void>`,使用`get()`不会返回值.
- 若`future`的模板参数为reference,则`get()`返回一个指向返回值的引用.
- 否则返回值被移动赋值或移动构造(取决于返回值是否支持移动赋值或移动构造).

> 引用自上文:
> 
> 使用`future<>.get()`方法将等待线程结束并获取其返回值,使用该方法会产生三种结果:
> - 线程启用并已返回结果,则立即返回结果.
> - 线程启用但尚未结束,`get()`会引发停滞待线程返回结果.
> - 线程尚未启动,则会被强制启动,如同同步调用.`get()`会引发停滞待线程返回结果.
> 
> 当未调用`future<>.get()`方法获取线程结果(`future<void>`包括在内)但`future`即将被销毁时:
> - 如果`future`无共享状态,则直接销毁.否则,
> - 如果`future`不是通过`async()`获得的,直接销毁.否则,
> - 如果线程已经启动但未完成,且`future`为`shared state`的最后持有者,则调用`future<>.wait()`等待线程结束后销毁.否则
> - 直接销毁`future`.

若销毁的`future`为`shared state`的最后持有者,则销毁`shared state`.销毁的`future`放弃其`shared state`的引用

`future`在默认构造或被移动或调用`get()`后处于无效状态(不指代共享状态,成员函数`valid()`返回`false`).此时调用任何析构函数,移动赋值运算符或`valid`以外的成员函数都是未定义行为(尽管鼓励实现在此情况下抛出指示`std::future_error::no_state`的`std::future_error`).

`future`不支持复制构造.

`share()`会将`share state`的控制权交给`shared_future`,该函数返回一个`shared_future`.

### get(), wait()
若`future`由`async()`返回且相关线程处于推迟状态,对其调用`get()`或`wait()`会启动线程.

`future`只允许调用一次`get()`(若调用时,`shared state`有状态,换而言之,成员函数`valid()`返回`false`).此后`future`处于无效状态(成员函数`valid()`返回`false`).

`get()`等待线程完成并返回其结果(或抛出异常).[详见上文](#async)  
其定义为:
````C++
T get();
T& get();	// std::future<T&> 特化
void get();	// std::future<void> 特化
````

`wait()`等待线程完成而不处理其结果.这个接口可以被调用一次以上.  
其定义为:
````C++
void wait() const;
````

### wait_for(), wait_until()
`wait_for()`和`wait_until()`不会使推迟的线程启动.

`wait_for()`接收一个时间段参数,可以等待异步操作一段有限时间.  
其定义为:
````C++
template< class Rep, class Period >
std::future_status wait_for( const std::chrono::duration<Rep,Period>& timeout_duration ) const;
````
例如:
````C++
std::future<int> f(std::async(func));
...
f.wait_for(std::chrono::seconds(10));	// 至多等10秒
````

`wait_until()`接收一个时间点参数,可以等待异步操作直至特定时间点.  
其定义为:
````C++
template< class Clock, class Duration >
std::future_status wait_until( const std::chrono::time_point<Clock,Duration>& timeout_time ) const;
````
例如:
````C++
std::future<int> f(std::async(func));
...
f.wait_until(std::system_clock::now() + std::chrono::minutes(1));
````

两个方法返回[`future_status`枚举](#future_status).

使用例:
````C++
int quick_computation();	// 运算快速但不精确
int accurate_computation();	// 运算慢但精确
std::future<int> f;	// 定义在函数外,因为accurate_computation()的生命周期可能长于best_result_in_time()

int best_result_in_time() {	// 要求在一定时间内计算出结果
	auto tp = std::chrono::system_clock::now() + std::chrono::minutes(1);	// 期限设定为1分钟
	// 同时开始快速运算与精确运算
	f = std::async(std::launch::async, accurate_computation);
	int guess = quick_computation();
	std::future_status s = f.wait_until(tp);
	// 返回最好的计算结果
	if (s == std::future_status::ready) {
		return f.get();
	}
	else {
		return guess;
	}
}
````

如果`wait_for`传入一个0时间段或负数时间段,或者`wait_until`传入现在或过去时间点,则会立刻返回线程当前状态:
````C++
using namespace std;
future<int> f(async(task));
...
if (f.wait_for(chrono::seconds(0)) != future_status::deferred) {	// 如果线程被推迟,则直接跳过轮询,因为该情况下,线程永远不会结束
	while (f.wait_for(chrono::seconds(0)) != future_status::ready) {
		...
		this_thread::yield();	// 无限循环可能会占用处理器大量资源,使用该函数让操作系统重新调度CPU资源.也可以睡眠一小段时间.
	}
}
...
auto res = f.get();	// 如果线程被推迟,此处强制开始执行
````
如果系统时间发生调整,`wait_for()`和`wait_until()`会有所不同.

### future所有操作
- `默认构造函数`: 建立一个无共享状态(`valid()`返回`false`)的`future`.
- `移动构造函数`: 建立一个`future`,状态取自右值,并令右值无效.
- `析构函数`: 销毁自己.
- `valid()`: 如果状态有效,则返回`true`,否则返回`false`.
- `get()`: 阻塞直到线程完成(准确来说是直到`future`有状态),返回结果或异常,并令其状态失效,并使.它会迫使被推迟的线程同步启动.
- `wait()`: 阻塞直到后台操作完成.它会迫使被推迟的线程同步启动.
- `wait_for(dur)`: 阻塞`dur`时间段,或直到后台操作完成.但被推迟的线程并不会被强制启动.
- `wait_until(tp)`: 阻塞直到到达时间点`tp`,或直到后台操作完成.但被推迟的线程并不会被强制启动.
- `share()`: 产生一个`shared_future`带有当前状态,并令自身状态失效.

## future_status
`future_status`是有作用域的枚举类型.

其可能值为:
- `std::future_status::deferred`: `async()`延缓了线程启动且没有调用`wait()`或`get()`以强制启动.此时`future`和`shared_future`的成员函数`wait_for()`和`wait_until()`会立即返回.
- `std::future_status::timeout`: 某个操作被异步启动但尚未结束,为等待时间又已逾期(对于给定的时间段而言).
- `std::future_status::ready`: 操作已完成.

## shared_future
`shared_future`允许多次调用`get()`,它会返回相同的结果或者抛出同一个异常.`get()`不会令`shared state`状态失效.

其`get()`函数的返回值与`future`有一些区别:
````C++
const T& get() const;
T& get() const;		// std::shared_future<T&> 特化
void get() const;	// std::shared_future<void> 特化
````
非特化模板返回类型`T`的常引用,而非右值.

`shared_future`允许拷贝构造,拷贝将会使多个`shared_future`指向同一个`shared state`,它们可以共享结果(或异常).也可以使用引用的方式传递`shared_future`,这样相当于对同一个`shared_future`多次调用`get()`,这也是合法的,但需要注意作用域范围的问题.

`shared_future`不提供`share()`方法.

其余方法与`future`相同.

例如:
````C++
using namespace std;
int query_num() {
	cout << "read number: ";
	int num;
	cin >> num;
	if (!cin) {
		throw runtime_error("no number read");
	}
	return num;
}
void do_something(char c, shared_future<int>& f) {
	try {
		int num = f.get();
		for (int i = 0; i < num; ++i) {
			this_thread::sleep_for(chrono::milliseconds(100));
			cout.put(c).flush();
		}
	}
	catch (const exception& e) {
		cerr << "EXCEPTION in thread " << this_thread::get_id() << ": " << e.what() << endl;
	}
}
int main() {
	try {
		shared_future<int> f = async(query_num);

		auto f1 = async(launch::async, do_something, '.', ::std::ref(f));
		auto f2 = async(launch::async, do_something, '+', ::std::ref(f));
		auto f3 = async(launch::async, do_something, '*', ::std::ref(f));

		f1.get();
		f2.get();
		f3.get();
	}
	catch (const exception& e) {
		cout << "EXCEPTION: " << e.what() << endl;
	}
	cout << "\ndone" << endl;
}
````
可能的输出(`5`为输入值):
```
read number: 5
.+**+.*+.*.+*.+
done
```
可能的输出(输入值`EOF`):
```
read number: ^D
EXCEPTION in thread EXCEPTION in thread 8760: no number readEXCEPTION in thread 11500: no number read
15044: no number read


done
```

**注意**:对于`get()`的重载2,由于是引用,表明可以对线程产生的结果进行赋值操作.虽然`shared state`是同步的,且读写是不同时的.但是`shared_future`对于结果的读写却**没有此保证**,因此需要外部的同步化技术.  
例如:
````C++
using namespace std;
class A {
public:
	int a = 0;
	int b = 0;
	int c = 0;
	int d = 0;
	A& operator=(const A& other) noexcept {
		a = other.a;
		b = other.b;
		this_thread::sleep_for(chrono::milliseconds(1));	// do many things here
		c = other.c;
		d = other.d;
		return *this;
	}
};
ostream& operator<<(ostream& os, const A& v) {
	cout << "a: " << v.a << " b: " << v.b << " c: " << v.c << " d: " << v.d;
	return os;
}

void set_num(shared_future<A&> f) {
	f.get() = {136764823, 257194194, 195917515, 916591725 };
}
void get_num(shared_future<A&> f) {
	A value = f.get();
	cout << value << endl;
}
int main() {
	A a = {213125667, 314214750, 612814250, 124515646 };
	shared_future<A&> f = async([&a]()->A& {cout << a << endl; return a; });
	auto f1 = async(get_num, ref(f));
	auto f2 = async(set_num, ref(f));
	f1.get();
	f2.get();
}
````
可能的输出:
```
a: 213125667 b: 314214750 c: 612814250 d: 124515646
a: 136764823 b: 257194194 c: 612814250 d: 124515646
```

如果是抛出异常,由于`C++`语言本身的特性,`throw`永远抛出异常的拷贝,但`rethrow_exception()`**是否创建异常的拷贝是未指定的**,因此:
````C++
void put_exception() {
	std::exception e;
	std::cout << "thread" << std::this_thread::get_id() << " put exception: " << &e << std::endl;
	throw e;
}
void get_exception(std::shared_future<void> f, std::mutex& m) {
	try {
		f.get();
	}
	catch (std::exception& e) {
		std::lock_guard lg(m);
		std::cout << "thread" << std::this_thread::get_id() << " get exception: " << &e << std::endl;
	}
}
int main() {
	std::mutex m;
	std::shared_future<void> f = std::async(put_exception);
	auto f1 = std::async(get_exception, f, std::ref(m));
	auto f2 = std::async(get_exception, f, std::ref(m));
	f1.get();
	f2.get();
}
````
上述代码的可能**三个异常变量的地址各不相同**,也可能**后两个异常变量的地址相同**.  
以下是一种可能的输出:
```
thread16364 put exception: 0000005FBCEFDD88
thread21480 get exception: 0000005FBD0FD710
thread22220 get exception: 0000005FBCFFD480
```
也可能输出:
```
thread16364 put exception: 0000005FBCEFDD88
thread21480 get exception: 0000005FBD0FD710
thread22220 get exception: 0000005FBD0FD710
```
因此,**在不进行同步化的情况下**对异常的修改可能会导致读取异常的线程出现未定义的行为.

## thread
`thread`的构造函数允许传入函数或可调用对象作为其参数:
````C++
template< class F, class... Args >
explicit thread( F&& f, Args&&... args );
````
上面构造函数调用后,一个新的线程就会被启动,如果无法启动一个新的线程,则抛出`std::system_error`并带着错误码`std::errc::resource_unavailable_try_again`或另一实现决定的错误码.

`thread`处理返回值或者异常需要借助`std::promise`.可以获得线程独一无二的ID.

如果发生错误,但未被捕捉于线程之内,程序会立刻中止并调用`std::terminate()`.想让异常传播出去,需要使用`std::exception_ptr`与`std::promise`.

必须声明是否要等待线程结束(`join()`)或者打算将线程卸离,使它运行于后台而不受任何控制(`detach()`).如果不在`thread`对象的声明周期结束前这么做,或者期间调用了其移动赋值函数,程序就会中止并调用`std::terminate()`.  
以下程序都会被调用终止(`terminate()`):
````C++
using namespace std;
int main() {
	{
		std::thread t([] {this_thread::sleep_for(chrono::milliseconds(100)); });
	}
	cout << "Cannot be reached" << endl;
}
````
````C++
using namespace std;
int main() {
	std::thread t([] {this_thread::sleep_for(chrono::milliseconds(100)); });
	std::thread tmp;
	t = std::move(tmp);
	cout << "Cannot be reached" << endl;
}
````
````C++
using namespace std;
int main() {
	std::thread t([] {this_thread::sleep_for(chrono::milliseconds(100)); });
	cout << "Will terminate soon." << endl;
}
````
如果让线程运行于后台而`main()`结束了,所有线程会被硬性地终止(存疑):
````C++
using namespace std;
int main() {
	std::thread t([] {this_thread::sleep_for(chrono::milliseconds(100)); cout << "Terminate?" << endl; });
	t.detach();
	quick_exit(0);	// 不做清理,防止cout被析构导致未定义行为.
}
````

### Detached Thread
卸离后的线程是丧失控制权的,因此没有办法得知它是否允许.因此如果让其访问寿命已经结束的对象(例如,通过引用传递的局部变量或者程序结束后线程仍在运行且正在访问全局变量或静态变量).

对于`Detached thread`,建议遵循如下原则:
- 卸离的线程宁可只访问本地变量(副本).
- 如果卸离的线程需要访问全局变量或静态变量,则:
  - 确保卸离后的线程先于主程序结束.可以使用的方法是通过`condition_variable`来发信号表明线程已结束.
  - 以调用`quick_exit()`的方式结束程序.这个函数会在不调用全局变量和静态变量的析构函数的情况下结束程序.

经验法则表明:终止`detached thread`的唯一安全方法是搭配`...at_thread_exit()`函数群的某一个.这会强制主线程等待卸离的线程真正结束.

### thread ID
`std::this_thread::get_id()`能够返回当前线程的ID.使用`thread`的成员方法`get_id`获得线程的ID.其类型为`std::thread::id`.每一个线程ID都是独一无二的.

通过`std::thread::id`的默认构造函数,会产生一个独一无二的ID表示`无线程`.

线程唯一能做的就是操作就是比较以及输出至某个流中以及获取其`hash`.线程ID是动态生成的,不能提前预知其ID是多少,**甚至表示`无线程`的ID都无法预知**.实现有可能直到被申请获得ID时才动态生成这些ID.

````C++
using namespace std;
int main() {
	std::thread t1([] {});
	std::thread t2([] {});
	std::thread t3([] {});
	cout << "t3 ID:       " << t3.get_id() << endl;
	cout << "main ID:     " << this_thread::get_id() << endl;
	cout << "nothread ID: " << thread::id() << std::endl;
	t1.join();
	t2.join();
	t3.join();
}
````
可能的输出:
```
t3 ID:       15560
main ID:     8920
nothread ID: 0
```
已结束的线程的ID可能会被系统拿去重复使用.

如果`thread`对象关联至某个线程,它就是可连接的(调用`joinable()`返回`true`).此时调用`get_id()`会获得不同于`std::thread::id()`的值,否则等于`std::thread::id()`.

### thread可用操作
- `thread t`: 创建一个不可连接的`thread`对象.
- `thread t(f, ...)`: 创建并启用线程执行`f`,或是抛出`std::system_error`.
- `thread t(rv)`: 执行后`rv`无状态.
- `t = rv`: 执行后`rv`无状态.如果`t.joinable()`为`true`,调用`std::terminate()`.
- *`复制构造`或`复制赋值`是被**禁止**的.*
- `~thread()`: 如果被析构对象的`joinable()`为`true`,调用`std::terminate()`.
- `joinable()`: 当thread有关联线程时,返回`true`.
- `join()`: 等待关联线程完成工作.此后对象是不可连接的.
- `detach()`: 解除对象与线程之间的关联并且让线程继续运行.此后对象是不可连接的.
- `get_id()`: 如果线程是可连接的,返回线程ID,否则返回`std::thread::id()`.
- `native_handle()`: 返回一个依赖于平台的类型`native_handle_type`,用于不具可移植性的扩展.
- [静态]`hardware_concurrency`: 返回可能的线程数量.该数量只是个参考值,不保证准确.如果数量不可计算或不明确,返回值是0.

## promise
`promise`是一个`asynchronous provider`.能够线程安全地给`shared state`提供数据(或者异常),以供`future`获取.  
例如:
````C++
void func(std::promise<int>& p) {
	try {
	int a;
	std::cin >> a;
		if (!std::cin) {
			throw std::runtime_error("broken stream");
		}
		p.set_value(a);
	}
	catch (...) {
		p.set_exception(std::current_exception());
		// current_exception()获取当前异常,并返回一个异常指针.
	}
}
int main() {
	try {
		std::promise<int> p;
		// promise必须以引用的形式传递,否则无效.
		std::thread t(func, std::ref(p));
		std::future<int> f(p.get_future());	// 此处p和f将共享一个shared state.
		// 尝试重复调用get_future()或对一个无状态的promise调用get_future()将会抛出std::future_error并分别携带错误码future_already_retrieved和no_state.
		t.detach();
		// 此处可用detach(),因为下面f.get()必然会等待p被赋予值或异常,而此时线程函数将要结束.
		std::cout << f.get() << std::endl;
	}
	catch (const std::exception& e) {
		std::cerr << "EXCEPTION: " << e.what() << std::endl;
	}
}
````
可能的输出(输入`2`):
```
2
2
```
可能的输出(输入`EOF`):
```
^D
EXCEPTION: broken stream
```

除了上述的解释.`set_value()`可以在`promise`(的`shared state`)中存放一个值.`set_exception()`则可以存放一个异常指针.存放完成后,`shared state`的状态就为`true`.此时与其共享状态的`future`(通过`get_future()`建立)就可以取出其值或异常.

注意:如果`std::current_exception()`发现当前无异常,则会生成一个`nullptr`,而`set_exception(nullptr)`是未定义行为.

`set_value()`定义为:
````C++
void set_value( const R& value );	// 主模板
void set_value( R&& value );		// 主模板
void set_value( R& value );	//std::promise<R&> 特化
void set_value();			//std::promise<void> 特化
````
`set_exception()`定义为:
````C++
void set_exception( std::exception_ptr p );
````

如果想要设置值或异常,但希望在线程结束时(此时线程生存期变量已经析构)`shared state`才变成`ready`,可以使用`set_value_at_thread_exit()`或`set_exception_at_thread_exit()`.

`set_value_at_thread_exit()`定义为:
````C++
void set_value_at_thread_exit( const R& value );	// 主模板
void set_value_at_thread_exit( R&& value );			// 主模板
void set_value_at_thread_exit( R& value );	// std::promise<R&> 特化
void set_value_at_thread_exit();	// std::promise<void> 特化
````
`set_exception_at_thread_exit()`定义为:
````C++
void set_exception_at_thread_exit( std::exception_ptr p );
````

注意:如果`promise`已经被设置了值(不可兼)或异常,则再次设置值或异常会抛出`std::future_error`并设置错误码为`promise_already_satisfied`,即使此时`shared state`不为`ready`.此外,如果尝试给无状态的`promise`设置值或异常,则也会抛出`std::future_error`并设置错误码为`no_state`.  
`catch`块中也可能会抛出异常,比如使用`set_exception()`或`set_exception_at_thread_exit()`时.

调用`set_value`,`set_exception`,`set_value_at_thread_exit`和`set_exception_at_thread_exit`和对`get_future`的调用之间不会造成数据竞争.

`promise`对共享状态的更新受到互斥体的保护,因此是线程安全的.

### promise所有操作
- `promise p`: 建立一个空共享状态的promise.
- `promise p(std::allocator_arg, alloc)`: 建立一个空共享状态的promise,以`alloc`为分配器.其中`std::allocator_arg`是一个`std::allocator_arg_t`类型的用于消除歧义的占位符.
- `promise p(rv)`: 移动构造函数.执行后`rv`为空共享状态.
- `~promise()`:
  - 如果共享状态不是`ready`,且无值也无异常,则存储一个`std::future_error`异常并夹带`broken_promise`异常.并将共享状态设置为`ready`.
  - 释放共享状态.
- `p = rv`: 移动赋值.如果`p`不是`ready`,按照上述析构函数的操作进行,然后执行赋值操作.
- [非成员函数]`swap(p1, p2)`: 互换p1和p2的状态.
- [成员函数]`p1.swap(p2)`: 互换p1和p2的状态.
- `get_future()`: 产生一个`future`并与其共享`shared state`.
- `set_value(val)`: 设val为值并令状态为`ready`(或抛出`std::future_error`).
- `set_value_at_thread_exit(val)`: 设val为值并在当前线程结束时设置状态为`ready`(或抛出`std::future_error`).
- `set_exception(e)`: 设e为异常并令状态为`ready`(或抛出`std::future_error`).
- `set_exception_at_thread_exit(e)`: 设e为异常并在当前线程结束时设置状态为`ready`(或抛出`std::future_error`).

## packaged_task
`package_task`是一个`asynchronous provider`.不同于`async()`,`package_task`允许创建一个任务,这个任务不会立刻运行,而是能够控制其在何时启动线程并运行.  
其类定义为:
````C++
template< class > class packaged_task; // 不予定义
template< class R, class ...ArgTypes >
class packaged_task<R(ArgTypes...)>;
````
例如:
````C++
int func(int a, int b) {
	std::cout << "start a + b" << std::endl;
	std::this_thread::sleep_for(std::chrono::milliseconds(100));
	return a + b;
}
int main() {
	std::packaged_task<int(int, int)> task(func);
	std::future<int> f = task.get_future();	// 使用get_future()使packaged_task返回一个future,并与其共享shared state.
	// 尝试重复调用get_future()或对一个无状态的promise调用get_future()将会抛出std::future_error并分别携带错误码future_already_retrieved和no_state.
	std::cout << "do something..." << std::endl;
	std::this_thread::sleep_for(std::chrono::milliseconds(100));
	task(5, 7);	// 调用存储的任务.
	/* 在以下情况抛出std::future_error:
	 * 存储的任务已经被调用过.此时设置错误类别为 promise_already_satisfied.
	 * 自身没有共享状态.此时设置错误类别为no_state.
	 */
	std::cout << f.get();
}
````
可能的输出:
```
do something...
start a + b
12
```

注意:构造函数可能会因为内存不足等原因出现异常.

`析构函数`和`reset()`会释放`shared state`.如果`shared state`尚未`ready`,就存储一个`std::future_error`异常并带错误码`std::future_errc::broken_promise`并令状态变成`ready`.

`make_ready_at_thread_exit()`方法也会启动任务,但是只有在**当前线程**(指的是**启动任务的线程**,而非任务线程)退出,并销毁所有线程局域存储期对象后,共享状态才会就绪.尝试在启动任务的线程执行`future.get()`会导致程序死锁,C++标准允许检测死锁并抛出`std::system_error`并带差错码`resource_deadlock_would_occur`.

### packaged_task所有操作
- `packaged_task pt`: 默认构造函数,建立一个不带状态的不带任务的`packaged_task`.
- `packaged_task pt(f)`: 建立一个`packaged_task`携带任务`f`.
- `packaged_task pt(std::allocator_arg, alloc, f)`: *(C++17 前)* 建立一个`packaged_task`携带任务`f`,使用分配器`alloc`.
- `packaged_task pt(rv)`: 移动构造函数.使用后`rv`无共享状态,也不带任务.
- `~packaged_task()`: 析构函数.效果见上文.
- `pt = rv`: 移动赋值函数.运行后`rv`无共享状态.
- [非成员函数]`swap(pt1, pt2)`: 两个`packaged_task`互换.
- [成员函数]`pt1.swap(pt2)`: 两个`packaged_task`互换.
- `valid()`: 如果有`shared state`就返回`true`.
- `get_future()`: 返回一个`future`,并与其共享`shared state`.
- `pt(args)`: 调用任务,并在任务结束后将`shared state`设置为`ready`.
- `make_ready_at_thread_exit(args)`: 调用任务,并在调用此方法的线程结束时才令`shared state`变成`ready`.
- `reset()`: 等价于`*this = packaged_task(std::move(f))`.重置状态,抛弃先前执行的结果.构造新的共享状态.抛弃先前执行的结果时,效果见上文.此外,有以下异常会被抛出:
  - 若本身无共享状态则为`std::future_error`.设置错误条件为`no_state`.
  - 若无足够内存以分配新的共享状态则为`std::bad_alloc`.
  - 新`packaged_task`的移动构造函数所抛的任何异常.

## this_thread命名空间
- `this_thread::get_id()`: 获得当前线程的ID.
- `this_thread::sleep_for(dur)`: 将某个线程阻塞`dur`时间段.
- `this_thread::sleep_until(tp)`: 将某个线程阻塞直到时间点`tp`.
- `this_thread::yield()`: 建议释放控制以便重新调度让下一个线程能够执行.

注意:当处理系统时间调整时,`sleep_for()`和`sleep_until()`会有所不同.

`this_thread::yield()`能够告诉操作系统放弃当前线程的时间切片余额是有好处的,这将使运行环境得以重新调度.  
使用例是等待或者轮询另一个线程:
````C++
while (!readyFlag) {
	std::this_thread::yield();
}
````

## 线程同步化与并发问题
> **多个线程并发处理相同的数据而又不曾同步化,那么唯一安全的情况就是:*所有*线程只*读取*数据**

自C++11后每个变量都确保会有自己的内存区(`bitfield`例外,不同的`bitfield`可能共享一块内存),因此,对于相同内存变量的读写,如果不曾同步化,则可能会发生`data race`.

`data race`的定义如下:
> 不同线程中的两个相互冲突的动作,其中至少一个动作不是`atomic`(不可分割的),而且无一个动作发生在另一动作之前(的保证).

### 为什么会有问题
`C++`的语句和操作并非与其产生的汇编码一一对应.标准描述的是`what`,实现决定`how`.

行为一般不会被太谨慎地定义以至于只有一种实现.甚至有可能有未定义的行为.这是为了给予编译器和硬件厂商自由度和能力去生成最佳代码.编译器允许将代码无限优化,只要可观测的行为保持稳定.

> 任何实现可以自由忽视国际标准的任何规定,只要最终成果貌似遵守了那些规定--这可由程序的可观测行为加以判断.例如,一个现实实现不需要核算表达式的某一部分--如果它可以推演而知其值未被使用且又不至于影响程序所产生的可观测行为.
> 
> <p style="text-align: right"> -- C++ standard</p>

### 有什么问题
#### 未同步化的数据访问
**未同步化的数据访问**:并行的两个线程读和写同一笔数据,不知道哪一个语句先来.

````C++
if (val >= 0) {
	f(val);
}
else {
	f(-val);
}
````
上面语句在多线程环境中有可能会因为`if子句`和`调用f()`之间`val`发生改变而造成负值传入`f()`.

> **除非另有说明,C++标准库提供的函数通常不支持"写或读"动作与另一个"写"动作(写至同一笔数据)并发执行.**

**C++标准库提供的一般性并发保证:**
- 一般而言多个线程共享同一个程序库对象而其中至少一个线程改动该对象时,可能会导致不明确的行为.
> 面对被多线程共享的某个标准库类型的某个对象,改动它会造成`导致不明确行为`的风险.除非该类型的对象被明确指定为`sharable without data races`或者使用者为它提供了一个`locking`机制.
>
> <p style="text-align: right"> -- C++ standard</p>
- 某个线程的对象构造期间,另一个线程使用了该对象,会导致不明确行为.同样,在某个线程中析构对象,而另一个线程正在使用它,也会导致不明确行为.这些甚至适用于针对线程同步而提供的对象.
- `STL容器`和`容器适配器`提供以下保证:
  - 并发的只读访问是允许的.这意味着调用非常成员函数`begin()`,`end()`,`rbegin()`,`rend()`,`front()`,`back()`,`data()`,`find()`,`lower_bound()`,`upper_bound()`,`equal_range()`,`at()`,`operator[]`(关联式容器除外),以及通过迭代器进行只读访问,都是允许的.
  - 并发处理同一容器内的不同元素是可以的(除了`class vector<bool>`).因此,不同的线程可以并发地读写相同容器内的*不同元素*.
- 对标准流进行格式化输入和输出(它们与C I/O同步)的并发处理是可能的,虽然导致插叙字符也是可能的(多数实现能够保证例如`cout << num << endl`在多线程中保证`num`的输出是完整且不会插入其他的字符,但`num`与`endl`之间是否会插入其他字符是不明确的).上述保证适用于`std::cin`,`std::cout`,`std::cerr`.然而对于`string stream`,`file stream`或`stream buffer`,并发处理会导致不明确的行为.
- `atexit()`和`at_quick_exit()`的并发调用是同步的.相同情况适用于那些设定或取得`new`,`terminate`或`unexpected handler`的函数(亦即`set_new_handler()`,`set_unexpected()`,`set_terminate()`及相应的`getter`).此外,`getenv()`也是同步的.
- 默认分配器的所有成员函数,除了析构函数,其并发处理都被同步.
- C++标准库保证它不存在任何隐形副作用会破会"对不同对象的并发处理",因此,C++标准库:
  - 不会去访问`reachable object`,除非某个操作特别指定要那些东西.
  - 不会允许在其内部引入`shared static object`却未令其同步.
  - 唯有在"对程序员不存在可见副作用"的情况下才允许编译器将操作并行.

#### 写至半途的数据
````C++
long long x = 0;
// 在某个线程对它写入数值:
x = -1;
// 另一个线程读取它:
std::cout << x;
````
其可能的输出结果包括:
- `0`:旧值,第一线程尚未赋予它`-1`.
- `-1`:新值,第一线程已经赋予它`-1`.
- `其他任何值`:若对`long long`的赋值操作不是不可分割的(例如在32位计算机上),第二个线程读取值的时候第一个线程正在赋值.

标准不保证任何数据类型的读写是`atomic`(不可分割的).

#### 重新安排的语句
````C++
long long data = 0;
bool readyFlag = false;
// 在供应端:
data = 42;
readyFlag = true;
// 在消费端:
while (!readyFlag);
func(data);
````
上面的代码会有问题,因为C++规则允许**重新安排**语句顺序,只要编译所得的代码*在单一线程内的可观测行为正确*.因此,在供应端允许重新安排为:
````C++
readyFlag = true;
data = 42;
````
在消费端也允许安排为:
````C++
func(data);
while (!readyFlag);
````
只要不影响其可观测行为.

#### 解决问题所需要的性质
- `Atomicity`(不可切割性):读写一个变量或是一连串语句,其行为是独占的,排他的,无任何打断的.其他线程不可能读到其中间状态.
- `Order`(次序):需要能够保证`指定次序`的方法.

以下概念可以保证`atomicity`或`order`:
- `future`和`promise`保证`atomicity`和`order`,对于相同`shared state`的读和写不会并发发生.
- `mutex`和`lock`授予独占权力.两种提供`atomicity`,它会阻塞所有其他需要使用`lock`的线程,直到作用于相同资源身上的`lock`释放.不保证不同线程之间的运行次序.
- `condition_variable`能令某线程等待被另一线程控制的`谓词`为`true`.允许保证`order`.
- `atomic`保证变量的`atomicity`以及可选的上下文的`order`.

#### volatile与并行
`volatile`在`C++`中用来阻止"过度优化".即该关键字只具体表示对外部资源的访问不该被优化掉.如果没有`volatile`编译器也许会消除对同一块共享内存看似多余的加载.

**但`volatile`既不提供`atomicity`也不提供特别的`order`.**(不同于Java)

## Mutex和Lock
`mutex`(mutual exclusion(互斥体))用于对资源独占访问.当一个线程锁定`mutex`,其他线程也要锁定`mutex`时,就必须等待第一个`mutex`解锁.

````C++
int val = 0;
std::mutex valMutex;
// 线程1
valMutex.lock();
setVal(val);
valMutex.unlock();
// 线程2
valMutex.lock();
++val;
valMutex.unlock();
````
两个线程中同时只能有一个线程能够访问`val`.后调用`lock()`的必须等待先调用`lock()`的`unlock()`才能继续执行.

**若抛出异常,可能会导致资源永远被锁住,此时需要使用`lock_guard`.**

根据C++的[RAII守则](https://zh.cppreference.com/w/cpp/language/raii),不应当自己来锁定或解锁`mutex`,而应当利用局部变量的生命周期:
````C++
int val = 0;
std::mutex valMutex;
// 线程1
{
	std::lock_guard<std::mutex> lg(valMutex);	// 构造函数调用lock()
	setVal(val);
}	// 析构函数调用unlock()
// 线程2
{
	std::lock_guard<std::mutex> lg(valMutex);
	++val;
}
````
实例:
````C++
void things_cost_time() {
	std::vector<int> v;
	v.reserve(10000);
	for (int i = 0; i < 10000; ++i) {
		v.push_back(i);
	}
	std::sort(v.begin(), v.end());
}
void func(const std::string& str, std::mutex& m) {
	things_cost_time();
	std::lock_guard<std::mutex> lg(m);
	for (char c : str) {
		std::cout.put(c);
	}
	std::cout << std::endl;
}
int main() {
	std::mutex m;
	auto f1 = std::async(func, "Hello from first thread", std::ref(m));
	auto f2 = std::async(func, "Hello from second thread", std::ref(m));
	auto f3 = std::async(func, "Hello from third thread", std::ref(m));
	func("Hello from main thread", m);
}
````
可能的输出:
```
Hello from main thread
Hello from second thread
Hello from first thread
Hello from third thread
```
`mutex`不保证顺序,因此以上4行文字可能会有次序变化.

**普通的`mutex`不支持递归锁定,尝试递归锁定会导致死锁**,C++标准允许检测死锁并抛出`std::system_error`并带差错码`resource_deadlock_would_occur`.

### recursive(递归的) lock
递归锁定有时候是必要的.

`recursive_mutex`允许同一线程内多次锁定,并在最后一次(即与`lock()`次数相等的`unlock()`)时释放`lock`:
````C++
void things_cost_time() {
	std::vector<int> v;
	v.reserve(10000);
	for (int i = 0; i < 10000; ++i) {
		v.push_back(i);
	}
	std::sort(v.begin(), v.end());
}
void func3(std::recursive_mutex& m) {
	{
		std::lock_guard<std::recursive_mutex> lg(m);	// 递归lock
		things_cost_time();
	}
}
void func2(std::recursive_mutex& m) {
	{
		std::lock_guard<std::recursive_mutex> lg(m);	// 递归lock
		func3(m);
	}
}
void func1(std::recursive_mutex& m) {
	{
		std::lock_guard<std::recursive_mutex> lg(m);	// 递归lock,不会死锁
		std::cout << "recursive" << std::endl;
		func2(m);
	}
}
int main() {
	std::recursive_mutex m;
	auto f = std::async(func1, std::ref(m));
	std::this_thread::sleep_for(std::chrono::milliseconds(3));
	{
		std::lock_guard<std::recursive_mutex> lg(m);
		std::cout << "done" << std::endl;
	}
	f.get();
}
````
### 尝试性lock及带时间性的lock
如果想要获得一个lock但如果不成功的话不希望它会阻塞,可以使用`try_lock()`方法.如果`lock`成功,返回`true`,失败则返回`false`.

`try_lock()`可能会假性失败,即可能没有其他线程`lock`也有可能会失败(为了`memory-ordering`,*暂时忽略*).

为`lock_guard`提供一个标签类型`std::adopt_lock_t`的`std::adopt_lock`,可以构造`lock_guard`而不让其调用`lock()`,但仍然能够调用`unlock()`.
````C++
void func1(std::mutex& m) {
	if (m.try_lock() == false) {
		std::cout << "fail to lock" << std::endl;
	}
	else {
		// try_lock()执行成功,所以此处mutex已经被锁住,lock_guard不应当调用lock()
		std::lock_guard<std::mutex> lg(m, std::adopt_lock);	// 不调用lock()而构造
		std::cout << "succeed to lock" << std::endl;
		things_cost_time();
	}	// lock_guard正常调用unlock()
}
int main() {
	std::mutex m;
	auto f = std::async(func1, std::ref(m));
	std::this_thread::sleep_for(std::chrono::microseconds(1));
	{
		std::lock_guard<std::mutex> lg(m);
		std::cout << "main() lock" << std::endl;
		things_cost_time();
	}
	f.get();
}
````
可能的输出:
```
main() lock
fail to lock
```
或者:
```
succeed to lock
main() lock
```
如果需要限制等待时间,可以选用`std::timed_mutex`和`std::recursive_timed_mutex`.其允许调用`try_lock_for()`或`try_lock_until()`用以等待某个时间段,或直至抵达某个时间点:
````C++
std::timed_mutex m;
if (m.try_lock_for(std::chrono::seconds(1))) {
	std::lock_guard<std::timed_mutex> lg(m, std::adopt_lock);
	...
}
else {
	could_not_get_the_lock();
}
````

### 处理多个lock
当一个线程都需要锁住多个mutex(例如,mutex1和mutex2),可能会出现某个线程`mutex1`(外层)已锁而`mutex2`等待其他线程解锁.而另一线程锁住`mutex2`后需要锁住`mutex1`,导致死锁.

`std::lock()`能够锁住传给它的所有`mutex`,而且阻塞直到所有都被锁定或直到抛出异常.如果是后者,则锁定的`mutex`都会被解锁.`std::lock()`提供了`死锁回避`机制,即当一个`mutex`锁定失败时,其他已锁的`mutex`都会被解锁,直到能够将所有`mutex`都锁住为止,但这也意味着多个`mutex`锁定次序并不明确:
````C++
void func(std::mutex& m1, std::mutex& m2) {
	std::lock_guard<std::mutex> lg1(m1);
	std::this_thread::sleep_for(std::chrono::milliseconds(50));
	std::cout << "func1" << std::endl;

	std::lock_guard<std::mutex> lg2(m2);
	std::this_thread::sleep_for(std::chrono::milliseconds(50));
	std::cout << "func2" << std::endl;
}
int main() {
	std::mutex m1;
	std::mutex m2;
	auto f = std::async(func, std::ref(m1), std::ref(m2));
	std::this_thread::sleep_for(std::chrono::milliseconds(10));
	std::lock(m2, m1);
	std::lock_guard<std::mutex> lg1(m1, std::adopt_lock);
	std::lock_guard<std::mutex> lg2(m2, std::adopt_lock);
	std::cout << "main" << std::endl;
	f.get();
}
````

`std::try_lock()`会按参数顺序尝试锁定所有`mutex`,它不会阻塞线程.在锁住所有`mutex`的情况下返回`-1`,否则返回第一个失败的`mutex`的索引,且如果这样的话所有成功锁住的`mutex`会又被`unlock()`:
````C++
std::mutex m1;
std::mutex m2;
int idx = std::try_lock(m1, m2);
if (idx < 0) {	// -1 -> both locks succeeded
	std::lock_guard<std::mutex> lock1(m1, std::adopt_lock);
	std::lock_guard<std::mutex> lock2(m2, std::adopt_lock);
	...
}	// automatically unlock all mutexes
else {
	// idx has zero-based index of first failed lock
	std::cerr << "could not lock mutex m" << idx + 1 << std::endl;
}
````
`try_lock()`不提供`死锁回避`机制,但它保证以出现于实参列的次序来试着完成锁定.

注意,调用完`lock()`或`try_lock()`之后,如果成功了,需要给`mutex`过继(adopt)给一个`lock_guard`:
````C++
std::lock(m1, m2);
std::lock_guard<std::mutex> lock1(m1, std::adopt_lock);
std::lock_guard<std::mutex> lock2(m2, std::adopt_lock);	// 必要,如果不手动使用unlock()的话
...
````

### lock_guard
`lock_guard`详细使用见上.`lock_guard`确保`mutex`离开作用域时总是被`unlock`.其关联的`mutex`要么在构造时`lock`,要么在构造时被接受(adopted).

所有操作:
- `lock_guard lg(m)`:为`m`建立一个`lock_guard`并调用`m.lock()`.
- `lock_guard lg(m, adopt_lock)`:为已经锁定的`m`建立一个`lock_guard`而不会调用`lock()`.
- `~lock_guard()`:调用`m.unlock()`并销毁`lock_guard`.

### unique_lock
`unique_lock<>`不同于`lock_guard<>`,其生命周期中允许`mutex`不被锁定(`lock_guard`的生命周期内`mutex`必然锁定).`unique_lock`允许使用`owns_lock()`或`bool()`来查询其`mutex`目前是否被锁住.

其析构函数在`mutex`锁住时调用`unlock()`,而在其没锁住时不做任何事.

`unique_lock`的构造函数包括:
- `unique_lock() noexcept;`:构造无关联互斥体的`unique_lock`.
- `unique_lock( unique_lock&& other ) noexcept;`
- `explicit unique_lock( mutex_type& m );`:调用`m.lock()`.
- `unique_lock( mutex_type& m, std::defer_lock_t t ) noexcept;`:尚未打算锁住互斥体.
- `unique_lock( mutex_type& m, std::try_to_lock_t t );`:调用`m.try_lock()`尝试锁定关联互斥体而不阻塞.
- `unique_lock( mutex_type& m, std::adopt_lock_t t );`:假定互斥体已经锁住.
- `template<class Rep, class Period> unique_lock( mutex_type& m, const std::chrono::duration<Rep, Period>& timeout_duration );`:调用`m.try_lock_for(timeout_duration)`尝试锁定关联互斥体.
- `template<class Clock, class Duration> unique_lock( mutex_type& m, const std::chrono::time_point<Clock, Duration>& timeout_time );`:调用`m.try_lock_until(timeout_time)`尝试锁定关联互斥体.

可以使用`release()`来释放`mutex`,其返回所存互斥体的指针.也可以使用`移动赋值`来转移所有权.
````C++
bool readyFlag = false;
std::mutex readyFlagMutex;
void func() {
	std::this_thread::sleep_for(std::chrono::milliseconds(200));	// do something func needs as preparation
	std::lock_guard<std::mutex> lg(readyFlagMutex);
	std::cout << "ready" << std::endl;
	readyFlag = true;
}
int main() {
	auto f = std::async(std::launch::async, func);
	{	// wait until readyFlag is true
		std::unique_lock<std::mutex> ul(readyFlagMutex);
		while (!readyFlag) {
			ul.unlock();
			std::this_thread::yield();
			ul.lock();
		}
	}
	std::cout << "after ready" << std::endl;
	f.get();
}
````
输出(无异常):
```
ready
after ready
```
此处对于`readyFlag`的读和写永远不会同时发生.因为`readyFlag`的读写永远处于`readyFlagMutex`锁住的状态.  
`readyFlag`永远不会因为代码优化而导致其移出`mutex`锁定区域以外.  
但上述代码使用`condition_variable`会更好.

其他所有操作:
- `~unique_lock()`:解锁`mutex`(如果`owns_lock()`为`true`)并销毁自身.
- `l = rv`:移动赋值.将`lock_state`从`rv`移至`l`,调用后`rv`不关联任何`mutex`.
- (非成员)`swap(l1, l2)`:交换.
- (成员)`swap(l)`:交换.
- `release()`:返回一个`pointer`指向关联的`mutex`并释放它.
- `owns_lock()`:如果关联的`mutex`被锁定则返回`true`.
- `explicit operator bool()`:如果关联的`mutex`被锁定则返回`true`.
- `mutex()`:返回一个`pointer`指向关联的`mutex`.
- `lock()`:锁住关联的`mutex`.
- `try_lock()`:尝试锁住关联的`mutex`(如果成功就返回`true`).
- `try_lock_for(dur)`:尝试在时间段`dur`内锁住关联的`mutex`(如果成功就返回`true`).
- `try_lock_until(tp)`:尝试在时间点`tp`之前锁住关联的`mutex`(如果成功就返回`true`).
- `unlock()`:解除`mutex`的锁定.

`lock()`抛出的异常由其中`mutex.lock()`传播出来.若`own_locks()`为`false`的情况下调用`unlock()`会抛出`std::system_error`并夹带错误码`operation_not_permitted`(而非未定义行为).

### 所有mutex
`std::mutex`:同一时间只能被一个线程锁定.
`std::recursive_mutex`:允许在同一时间多次被同一线程获得其`lock`.
`std::timed_mutex`:允许传递一个时间段或时间点,用来定义等待允许`lock`的最长时间.
`std::recursive_timed_mutex`:允许同一线程多次获得其`lock`,可指定期限.

可用操作:
- `默认构造`:建立一个未锁定的互斥体.
- `析构函数`:销毁互斥体,如果互斥体此时仍被锁定,则行为未定义.
- `lock()`:锁住互斥体(未锁住时会造成阻塞).
- `try_lock()`:尝试锁住互斥体.如果锁定成功返回`true`,否则`false`.
- `try_lock_for(dur)`:仅支持`timed_mutex`和`recursive_timed_mutex`.尝试在时间段dur内锁定.如果锁定成功就返回`true`.
- `try_lock_until(tp)`:仅支持`timed_mutex`和`recursive_timed_mutex`.尝试在时间点tp前锁定.如果锁定成功就返回`true`.
- `unlock()`:解除锁定.如果互斥体未被锁定,则行为未定义.线程尝试`unlock`不是该线程`lock`的互斥体,也是未定义行为.
- `native_handle()`:返回一个因平台而异的类型`native_handle_type`,这是为了不具可移植性的扩展.

`lock()`有可能抛出`std::system_error`,此情况下**不锁定**互斥体.异常可能的错误码如下:
- `operation_not_permitted`:线程的特权级不足以执行此操作.
- `resource_deadlock_would_occur`:平台侦测到有个死锁即将发生.
- `device_or_resource_busy`:互斥体已锁定而又无法形成阻塞.

### call_once
例如多个线程共享某一个资源,但只希望多个线程当中,该初始化函数只调用一次(不论是哪个线程调用的),可以使用`call_once()`函数.

`std::once_flag`用于辅助判断`std::call_once()`是否曾被调用且执行成功:
````C++
std::default_random_engine dre(static_cast<unsigned>(time(nullptr) % std::numeric_limits<unsigned>::max()));
std::uniform_int_distribution<int> ud(10, 20);
void do_something() {
	std::this_thread::sleep_for(std::chrono::milliseconds(ud(dre)));
}
void ini_func(int& ini_data, const std::thread::id& id) {
	std::cout << "call ini_func() from thread " << id << std::endl;
	std::cin >> ini_data;
}
void func(std::once_flag& oc, std::mutex& m, int& shared_data) {
	do_something();
	std::lock_guard lg(m);
	std::call_once(oc, ini_func, shared_data, std::this_thread::get_id());
	std::cout << "get share_data: " << shared_data << " in thread " << std::this_thread::get_id() << std::endl;
}
int main() {
	int shared_data = 0;
	std::mutex m;
	std::once_flag oc;
	auto f1 = std::async(func, std::ref(oc), std::ref(m), std::ref(shared_data));
	auto f2 = std::async(func, std::ref(oc), std::ref(m), std::ref(shared_data));
	f1.get();
	f2.get();
}
````
可能的输出(输入`42`):
```
call ini_func() from thread 5484
42
get share_data: 42 in thread 5484
get share_data: 42 in thread 2612
```
`call_once()`中用于调用函数的参数**不会被退化**.  
`once_flag`一旦被`call_once()`调用状态就会修改,此后传入相同的`once_flag`(状态被修改)调用`call_once()`会立刻返回而不执行函数(即使被调函数不同).  
`call_once()`以及`once_flag`是线程安全的.  
被调函数的任何异常都会被`call_once()`抛出,此时调用不被视为成功,`once_flag`状态不会改变.

## Condition Variable
`std::condition_variable`能够做到一个线程唤醒一个或多个其他等待中的线程.

`std::condition_variable`与`std::mutex`一起使用来进行线程同步.其依赖`mutex`来阻塞线程,直至修改共享变量的线程通知`std::condition_variable`.

修改共享变量的线程必须:
1. 对`mutex`调用`lock()`(常通过`std::lock_guard`)
2. 在保有锁时修改共享变量,通常是指涉及`condition_variable`判断条件的变量.
3. 在`std::condition_variable`上执行`notify_one()`或`notify_all()`(可以释放锁后再通知).

注意:即使共享变量是原子的,也必须再拥有互斥体时修改它,一八修改发布到等待的线程.详见[stackoverflow](https://stackoverflow.com/questions/38147825/shared-atomic-variable-is-not-properly-published-if-it-is-not-modified-under-mut).

使用`std::condition_variable`等待的线程必须:
1. 在用于保护共享变量的互斥体上获得`std::unique_lock<std::mutex>`.
2. 对于无谓词的`wait`组方法:
   1. 检测条件,是否为已更新且已提醒的情况.(不需要自己检测)
   2. 调用`std::condition_variable`的`wait`,`wait_for`或`wait_until`(原子地`unlock`互斥体并暂停线程执行,直到条件变量被通知,时限过期,或发生[虚假唤醒](https://en.wikipedia.org/wiki/Spurious_wakeup),然后再返回前自动`lock`互斥体).
   3. 检查条件,并在未满足的情况下继续等待(通常是因为假醒).
3. 如果`wait`组方法传入了谓词,则包揽了以上三个步骤.

> 上面`等待的线程`中第2条的可能代码是:
> ````C++
> while (!readyFlag) {
>     condVar.wait(ul);	
> }
> ````
> 等价于第3条中使用谓词的代码:
> ````C++
> condVar.wait(ul, []{ return readyFlag; });
> ````

`std::condition_variable`只允许与`std::unique_lock<std::mutex>`使用.

示例:
````C++
std::default_random_engine dre(static_cast<unsigned>(time(nullptr) % std::numeric_limits<unsigned>::max()));
std::uniform_int_distribution<int> ud(10, 20);

bool readyFlag = false;
std::mutex readyMutex;
std::condition_variable condVar;

void do_something() {
	std::this_thread::sleep_for(std::chrono::milliseconds(ud(dre)));
}

void thread1(int& shared_data) {
	do_something();
	std::cout << "<return>" << std::endl;
	std::cin >> shared_data;
	// 上面这段代码可以放在lock_guard内,但是这与condition_variable的条件无关,因此不放在里面也是没问题的,放在外面反而可以减少mutex锁定的时间从而减少mutex内部轮询带来的效率损失.lock的时间要尽可能少.
	{
		std::lock_guard<std::mutex> lg(readyMutex);
		// 即使只有readyFlag,且它是原子的,也必须使用mutex保护
		readyFlag = true;
		std::cout << "everything gets ready" << std::endl;
	}
	condVar.notify_one();	// 建议放在lock_guard的外面以避免等待线程才被唤醒就阻塞
}
void thread2(int& shared_data) {
	std::cout << "wait for thread 1" << std::endl;
	{
		std::unique_lock<std::mutex> ul(readyMutex);
		// 此处mutex被锁住
		// 下面调用wait()后mutex又被释放锁定
		condVar.wait(ul, [] { return readyFlag; });
		// condVar被唤醒(或超时或假醒)后会调用lock
	}	// 此处必然会调用unlock()
	std::cout << "thread 2 gets " << shared_data << std::endl;
}
int main() {
	int shared_data = 0;
	auto f1 = std::async(thread1, std::ref(shared_data));
	auto f2 = std::async(thread2, std::ref(shared_data));
}
````
可能的输出(输入`42`):
````
wait for thread 1
<return>
42
everything gets ready
thread 2 gets 42
````

### condition_variable所有操作
- `默认构造`
- `析构函数`
- `notify_one()`:唤醒一个等待者(线程).
- `notify_all()`:唤醒所有等待者(线程).
- `wait(ul)`:使用`unique_lock ul`来等待通知.
- `wait(ul, pred)`:使用`unique_lock ul`来等待通知,并且直到`pred`在苏醒后`pred`结果为`true`.
- `wait_for(ul, dur)`:带期限的`wait(ul)`.
- `wait_for(ul, dur, pred)`:带期限的`wait(ul, pred)`
- `wait_until(ul, tp)`:带期限的`wait(ul)`.
- `wait_until(ul, tp, pred)`:带期限的`wait(ul, pred)`
- `native_handle()`:返回一个因平台而异的类型`native_handle_type`,为的是不具可移植性的扩展.
- (非成员)`notify_all_at_thread_exit(cv, ul)`:在线程结束时通知所有等待`condition_variable cv`的线程,并代为`ul`解除锁定.

````C++
void thread_func() {
    thread_local std::string thread_local_data = "42";
    std::unique_lock<std::mutex> lk(m);
    result = thread_local_data;
    ready = true;
    std::notify_all_at_thread_exit(cv, std::move(lk));	// 为避免死锁,建议在调用完之后就返回函数,使用这个函数只是为了在通知前完成清理工作,清理工作不得造成阻塞
}
// 清理thread_local的thread_local_data
// 对传入的ul(由lk移动构造)中存储的m调用unlock()
// cv.notify_all()
````

`wait`族方法用以让`condition_variable`所在的线程等待通知.

`notify`族方法用于通知等待中的`condition_variable`(通知和等待的条件变量必须是同一个).

若无法建立`condition_variable`,构造函数会抛出`system_error`,并夹带错误码`resource_unavailable_try_again`.

不允许复制或赋值.

所有通知都是同步化的,并发调用不会有问题.

被传入的`wait`族方法的`pred`总会在`lock`情况下被调用,所以是线程安全的.

对于不接受`pred`的`wait_for()`和`wait_until()`返回`std::cv_status`枚举,其值可能为:
- `std::cv_status::timeout`:如果发生不容置疑的超时.
- `std::cv_status::no_timeout`:如果发生通知.

对于接受`pred`的`wait_for()`和`wait_until()`返回`pred`的结果.

调用`wait`族方法时,若`lock.owns_lock()`为`false`,则行为未定义.

`wait`族方法返回后,`lock.owns_lock()`为`true`.

`notify_all_at_thread_exit()`可用于控制一个`detached thread`.

### condition_variable_any
`std::condition_variable_any`不要求使用`std::unique_lock`(但仍要求是`<std::mutex>`).对于搭配`condition_variable_any`的`lock`,必须满足`BasicLockable`具名要求.

## Atomic
`std::atomic`模板类提供原子操作,多线程上对同一个对象的读写不会造成数据竞争.

下面将上面使用`lock`和`condition_variable`的代码改用为`atomic`:
````C++
std::default_random_engine dre(static_cast<unsigned>(time(nullptr) % std::numeric_limits<unsigned>::max()));
std::uniform_int_distribution<int> ud(10, 20);

std::atomic<bool> readyFlag(false);

void do_something() {
	std::this_thread::sleep_for(std::chrono::milliseconds(ud(dre)));
}

void thread1(int& shared_data) {
	do_something();
	std::cout << "<return>" << std::endl;
	std::cin >> shared_data;
	readyFlag.store(true);
}
void thread2(int& shared_data) {
	std::cout << "wait for thread 1" << std::endl;
	while (!readyFlag.load()) {
		std::this_thread::yield();
	}
	std::cout << "thread 2 gets " << shared_data << std::endl;
}
int main() {
	int shared_data = 0;
	auto f1 = std::async(thread1, std::ref(shared_data));
	auto f2 = std::async(thread2, std::ref(shared_data));
}
````

`std::atomic<T>`模板的`T`必须满足:
- `可平凡赋值`
- `可复制构造`
- `可移动构造`
- `可复制赋值`
- `可移动赋值`

声明一个`atomic`应总是将其初始化:
````C++
std::atomic<bool> readyFlag(false);	// 该操作不是原子的
````
如果确实需要之后初始化,或需要与`C`兼容,则必须使用非成员函数`atomic_init()`初始化(C++20启用,默认构造函数不是`零初始化`,而是`值初始化`,且该操作非原子的):
````C++
std::atomic<bool> readyFlag;	// 默认构造是平凡的
...
std::atomic_init(&readyFlag, false);	// 该操作不是原子的
````
**需要初始化的原因是其内部的锁需要被初始化.**

`atomic`默认情况下使用`std::memory_order_seq_cst`,即在编译器优化后,其操作所在的位置,前面的操作永远不会置于操作后,后面的操作永远不会至于操作前.

可使用低层的`atomic`操作放宽这一次序保证.

一般而言,`atomic`所有操作的返回值是`copy`而非`reference`.

除了接受`T`类型的值的构造函数以外的所有方法**都是原子的**.

所有方法,除了构造函数,都被重载为`volatile`和`非volatile`两个版本.

- `store(val)`方法能够赋予一个新值
- `load()`方法能够获取当前值
- `operator=(val)`:等价于`store(val)`,但返回所附值的**副本**.原子变量不能复制(或移动)赋值.
- `operator T()`:等价于`load()`.
- `is_lock_free()`:如果类型内部不使用`lock`则返回`true`.
- `exchange(val)`:赋值`val`并返回旧值的拷贝.
- `compare_exchange_strong(exp, des)`:CAS操作(见下)
- `compare_exchange_weak(exp, des)`:Weak CAS操作(见下)

CAS操作,即`compare-and-swap`,比较所给值与自身是否相等,相等则更新为另一给定的新值,其`伪代码`如下:
````C++ ?
bool compare_exchange_strong(T& expected, T desired) {
	if (this->load() == expected) {
		this->store(desired);
		return true;
	}
	else {
		expected = this->load();
		return false;
	}
}
````
对于`weak形式`有可能会出现`假失败(spuriously fail)`,即期望值出现的情况下仍然返回`false`.但是`weak`形式有时候比`strong`形式更高效.

`std::atomic<T>`对以下类型偏特化:
- `std::atomic<U*>`:指针类型
- `std::atomic<std::shared_ptr<U>>`和`std::atomic<std::weak_ptr<U>>`

`std::atomic<T>`对所有整型(C++20允许浮点数)特化(包括字符类型不包括`bool`),以支持额外的原子操作(见下).

为整数,浮点数(C++20起)和指针类型特化:
- `fetch_add`:`t+=val`,返回调用前的值.
- `fetch_sub`:`t-=val`,返回调用前的值.
- `operator+=`:`t+=val`,返回结果.
- `operator-=`:`t-=val`,返回结果.

仅为整数和指针类型特化:
- `operator++`
- `operator++(int)`
- `operator--`
- `operator--(int)`

仅为整数类型特化:
- `fetch_and`:按位与,返回调用前的值.
- `fetch_or`:按位或,返回调用前的值.
- `fetch_xor`:按位异或,返回调用前的值.
- `operator&=`:按位与,返回其结果.
- `operator|=`:按位或,返回其结果.
- `operator^=`:按位异或,返回其结果.

### Atomic的C风格接口
例如:
````C++
std::atomic_bool ab;
std::atomic_init(&ab, false);
...
std::atomic_store(&ab, true);
...
if (std::atomic_load(&ab)) { ... }
````
对于`C语言`:
- `atomic_bool` -> `std::atomic<bool>`
- `atomic_char` -> `std::atomic<char>`
- ...

### 低层接口
以下操作允许传入一个`memory_order`类型的枚举(C++20是带作用域的枚举,并声明了别名以兼容之前的命名)以改变内存处理次序,默认参数是`std::memory_order_seq_cst`(其作用见上文):
- `store()`
- `load()`
- `exchange()`
- `compare_exchange_weak`:允许传入两个`memory_order`,以分别指定成功时和失败时的内存处理次序.也允许只传入一个`memory_order`.
- `compare_exchange_strong`:允许传入两个`memory_order`,以分别指定成功时和失败时的内存处理次序.也允许只传入一个`memory_order`.
- `fetch_add`
- `fetch_sub`
- `fetch_and`
- `fetch_or`
- `fetch_xor`

`atomic_thread_fence()`和`atomic_thread_fence()`非成员函数能够控制内存访问重安排的界限.



# 术语
## trivial（平凡的）
平凡类型包含：标量类型、平凡类类型、上述类型的数组、这些类型的有cv限定的版本。

其中，标量类型包括：算数类型（整型和浮点型）、枚举类型、指针类型、成员指针类型、std::nullptr_t、这些类型的有cv限定的版本。

## 未定义行为(ud)
C++标准没有定义某种操作的后果,因此会导致在不同的实现中会有不同的结果.
