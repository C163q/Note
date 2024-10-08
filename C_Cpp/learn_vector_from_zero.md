
# MSVC STL vector
## vector模板
模板参数为`_Ty`和`_Alloc`分别表示vector的元素类型和分配器的类型,`_Alloc`默认为`std::allocator<_Ty>`

成员变量为`_Compressed_pair<_Alty, _Scary_val> _Mypair`.

所谓`_Compressed_pair<_Alty, _Scary_val>`,只是编译器内置的一个特殊pair,第一个被类私有继承,第二个类在内部存储为`_Myval2`.

所谓`_Alty`,有定义`using _Alty = std::allocator_traits<_Alloc>::rebind_alloc<_Ty>`,使用该定义的原因可能是对于`_Alloc`,若传入的元素类型为`int`而传入的分配器类型为`std::allocator<double>`,可以用该操作得到`std::allocator<int>`.

所谓`_Scary_val`,有定义`using _Scary_val = _Vector_val<conditional_t<_Is_simple_alloc_v<_Alty>,_Simple_types<_Ty>,_Vec_iter_types<_Ty, size_type, difference_type, pointer, const_pointer>>>`.
其中,`_Vector_val`是一个类,包含三个成员变量:`_Myfirst`,`_Mylast`,`_Myend`,分别表示vector的起始位置,vector有元素的尾位置,vector申请空间的尾位置.

`using conditional_t = conditional<_Test, _Ty1, _Ty2>::type`,对于`conditional`,如果_Test为真,选择_Ty1,否则选择_Ty2.

即上述`_Scary_val`,如果满足`_Is_simple_alloc_v<_Alty>`,就使用`_Simple_type<_Ty>`,否则使用`_Vec_iter_types<_Ty, size_type, difference_type, pointer, const_pointer>`,所谓`_Is_simple_alloc_v<_Alty>`,就是判断分配器遵循`size_type`为`size_t`,`difference_type`为`ptrdiff_t`,`pointer`为`value_type*`,`const pointer`为`const value_type*`.总之,最终得到的`_Vector_val`一定是`pointer`为`allocator_trait<_Alty>::pointer`这种的.

因此,`_Mypair`的第一个类型参数,也就是分配器会被私有继承,而第二个类型参数,是一个类`_Scary_val`,会被实例化,名为`_Myval2`,包含上面讲过的三个指针.

此处,`_Vector_val`还继承了`_Container_base`,此处先暂时不讨论该基类及其成员变量`_Alloc_proxy`.

默认构造`vector();`无特别的.

`vector(const _Alloc& _Al);`向中`_Al`传入`_Mypair`的private继承类.之后的`const _Alloc&`参数同理.

`vector(const size_type _Count, const _Alloc& _Al = _Alloc());`调用`_Construct_n(_Count)`


## vector<bool>特化