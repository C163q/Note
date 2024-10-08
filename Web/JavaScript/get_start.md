<head>
    <title>This is a CSS note.</title>
    <style type="text/css">
        body {
            font-family: "cascadia code", 幼圆, 宋体;
        }
        code {
            color: burlywood;
        }
        .red_font {
            color: crimson;
        }
        .yellow_font {
            color: orange;
        }
    </style>
</head>

# 目录
- [目录](#目录)
- [认识JavaScript](#认识javascript)
  - [ECMAScript](#ecmascript)
  - [DOM](#dom)
  - [BOM](#bom)
- [HTML中的JavaScript](#html中的javascript)
  - [\<script\>元素](#script元素)
  - [嵌入](#嵌入)
    - [行内嵌入](#行内嵌入)
    - [外部嵌入](#外部嵌入)
  - [元素详解](#元素详解)
    - [标签位置](#标签位置)
    - [推迟执行脚本(defer)](#推迟执行脚本defer)
    - [异步执行脚本(async)](#异步执行脚本async)
    - [动态加载脚本](#动态加载脚本)
    - [关于type](#关于type)
  - [XHTML中的JS](#xhtml中的js)
  - [\<noscript\>元素](#noscript元素)
- [语言基础](#语言基础)
  - [基本语法](#基本语法)
    - [标识符](#标识符)
    - [注释](#注释)
    - [严格模式](#严格模式)
    - [语句](#语句)
  - [关键字和保留字](#关键字和保留字)
  - [变量](#变量)
    - [var](#var)
    - [let](#let)
    - [const](#const)
    - [推荐使用方式](#推荐使用方式)
  - [数据类型](#数据类型)
    - [typeof操作符](#typeof操作符)
    - [Undefined类型](#undefined类型)
    - [Null类型](#null类型)
    - [Boolean类型](#boolean类型)
    - [Number类型](#number类型)
      - [整数](#整数)
      - [浮点数](#浮点数)
      - [值的范围](#值的范围)
      - [NaN](#nan)
      - [数值转换](#数值转换)
    - [String类型](#string类型)
      - [toString()方法](#tostring方法)
      - [String()转型函数](#string转型函数)
      - [模板字面量](#模板字面量)
      - [原始字符串](#原始字符串)
    - [Symbol类型](#symbol类型)
      - [基本用法](#基本用法)
      - [使用全局符号注册表](#使用全局符号注册表)
      - [使用符号作为属性](#使用符号作为属性)
      - [常用内置符号](#常用内置符号)
        - [Symbol.asyncIterator](#symbolasynciterator)
        - [Symbol.hasInstance](#symbolhasinstance)
        - [Symbol.isConcatSpreadable](#symbolisconcatspreadable)
        - [Symbol.iterator](#symboliterator)
        - [Symbol.match](#symbolmatch)
        - [Symbol.replace](#symbolreplace)
        - [Symbol.search](#symbolsearch)
        - [Symbol.species](#symbolspecies)
        - [Symbol.split](#symbolsplit)
        - [Symbol.toPrimitive](#symboltoprimitive)
        - [Symbol.toStringTag](#symboltostringtag)
        - [Symbol.unscopables](#symbolunscopables)
    - [Object类型](#object类型)
  - [操作符](#操作符)
    - [一元操作符](#一元操作符)
      - [递增/递减](#递增递减)
      - [一元加和减](#一元加和减)
    - [位运算符](#位运算符)
    - [布尔操作符](#布尔操作符)
    - [乘性操作符](#乘性操作符)
    - [指数操作符](#指数操作符)
    - [加性操作符](#加性操作符)
    - [关系操作符](#关系操作符)
    - [相等运算符](#相等运算符)
    - [条件操作符](#条件操作符)
    - [赋值操作符](#赋值操作符)
    - [逗号操作符](#逗号操作符)
  - [语句](#语句-1)
    - [if语句](#if语句)
    - [do-while语句](#do-while语句)
    - [while语句](#while语句)
    - [for语句](#for语句)
    - [for-in语句](#for-in语句)
    - [for-of语句](#for-of语句)
    - [标签语句](#标签语句)
    - [break和continue](#break和continue)
    - [with语句(已弃用)](#with语句已弃用)
    - [switch语句](#switch语句)
  - [函数](#函数)
- [变量,作用域与内存](#变量作用域与内存)
  - [原始值与引用值](#原始值与引用值)
    - [动态属性](#动态属性)
    - [复制值](#复制值)
    - [传递参数](#传递参数)
    - [确定类型](#确定类型)
  - [执行上下文与作用域](#执行上下文与作用域)
    - [作用域链增强](#作用域链增强)
    - [变量声明](#变量声明)
  - [垃圾回收](#垃圾回收)
    - [标记清理](#标记清理)
    - [引用计数](#引用计数)
    - [性能](#性能)
    - [内存管理](#内存管理)
      - [内存泄漏](#内存泄漏)
      - [静态分配和对象池](#静态分配和对象池)
- [基本引用类型](#基本引用类型)
  - [Date](#date)
    - [继承的方法](#继承的方法)
    - [日期格式化方法](#日期格式化方法)
    - [其他方法](#其他方法)
  - [RegExp](#regexp)
    - [属性](#属性)
    - [方法](#方法)
    - [构造函数属性](#构造函数属性)
    - [其他内容](#其他内容)
  - [原始值包装类型](#原始值包装类型)
    - [Boolean](#boolean)
    - [Number](#number)
    - [String](#string)
      - [JS字符](#js字符)
      - [normalize()方法](#normalize方法)
      - [字符串操作方法](#字符串操作方法)
  - [单例内置对象](#单例内置对象)
    - [Global](#global)
      - [URI编码方法](#uri编码方法)
      - [eval()方法](#eval方法)
      - [对象属性](#对象属性)
      - [window对象与Global](#window对象与global)
    - [Math](#math)
      - [属性](#属性-1)
      - [max()和min()](#max和min)
      - [舍入方法(静态)](#舍入方法静态)
      - [random()静态方法](#random静态方法)
      - [其他静态方法](#其他静态方法)
- [集合引用类型](#集合引用类型)
  - [Object](#object)
  - [Array](#array)
    - [创建数组](#创建数组)
- [迭代器与生成器](#迭代器与生成器)
- [对象,类,面向对象编程](#对象类面向对象编程)
  - [对象](#对象)
    - [属性的类型](#属性的类型)
      - [数据属性](#数据属性)
      - [访问器属性](#访问器属性)
    - [定义多个属性](#定义多个属性)
    - [读取属性的特性](#读取属性的特性)
    - [合并对象](#合并对象)
    - [对象标识及相等判定](#对象标识及相等判定)
    - [增强的对象语法](#增强的对象语法)
      - [属性值简写](#属性值简写)
      - [可计算属性](#可计算属性)
      - [简写对象名](#简写对象名)
    - [对象解构](#对象解构)
      - [嵌套解构](#嵌套解构)
      - [部分解构](#部分解构)
      - [参数上下文匹配](#参数上下文匹配)
  - [创建对象](#创建对象)
    - [构造函数](#构造函数)
      - [构造函数也是函数](#构造函数也是函数)
      - [构造函数的问题](#构造函数的问题)
    - [原型模式](#原型模式)
      - [原型原理](#原型原理)
      - [原型层级](#原型层级)
      - [原型和in操作符](#原型和in操作符)
      - [属性枚举顺序](#属性枚举顺序)
    - [对象迭代](#对象迭代)
      - [其他原型语法](#其他原型语法)
      - [原型的动态性](#原型的动态性)
      - [原生对象原型](#原生对象原型)
      - [原生属性覆盖问题](#原生属性覆盖问题)
  - [继承](#继承)
    - [原型链](#原型链)
      - [默认原型](#默认原型)
      - [原型与继承关系](#原型与继承关系)
      - [关于方法](#关于方法)
      - [原型链的问题](#原型链的问题)
    - [盗用构造函数](#盗用构造函数)
      - [传递参数](#传递参数-1)
      - [盗用构造函数的问题](#盗用构造函数的问题)
    - [组合继承](#组合继承)
    - [原型式继承](#原型式继承)
    - [寄生式继承](#寄生式继承)
    - [寄生式组合继承](#寄生式组合继承)
  - [类](#类)
    - [类定义](#类定义)
    - [类构造函数](#类构造函数)
      - [实例化](#实例化)
      - [把类当成特殊函数](#把类当成特殊函数)
    - [实例,原型和类成员](#实例原型和类成员)
      - [实例成员](#实例成员)
      - [原型方法与访问器](#原型方法与访问器)
      - [静态类方法](#静态类方法)
      - [非函数原型和类成员](#非函数原型和类成员)
      - [迭代器和生成器方法](#迭代器和生成器方法)
    - [继承](#继承-1)
      - [继承](#继承-2)
      - [构造函数, HomeObject和super()](#构造函数-homeobject和super)
      - [抽象基类](#抽象基类)
      - [继承内置类型](#继承内置类型)
      - [类混入](#类混入)
    - [新增特性](#新增特性)
      - [私有属性(ES2022)(*待补充*)](#私有属性es2022待补充)
- [代理和反射](#代理和反射)
  - [代理基础](#代理基础)
    - [创建空代理](#创建空代理)
    - [定义捕获器](#定义捕获器)
    - [捕获器参数和反射API](#捕获器参数和反射api)
    - [捕获器不变式](#捕获器不变式)
    - [可撤销代理](#可撤销代理)
    - [使用反射API](#使用反射api)
      - [反射API与对象API](#反射api与对象api)
      - [状态标记](#状态标记)
      - [等价函数替代操作符](#等价函数替代操作符)
      - [安全地应用函数](#安全地应用函数)
    - [代理另一个代理](#代理另一个代理)
    - [代理的问题与不足](#代理的问题与不足)
      - [代理中的this](#代理中的this)
      - [代理与内部插槽](#代理与内部插槽)
  - [代理捕获器与反射方法](#代理捕获器与反射方法)
    - [必要说明](#必要说明)
    - [get()](#get)
      - [返回值](#返回值)
      - [拦截的操作](#拦截的操作)
      - [捕获器处理程序参数](#捕获器处理程序参数)
      - [捕获器不变式](#捕获器不变式-1)
    - [set()](#set)
      - [返回值](#返回值-1)
      - [拦截的操作](#拦截的操作-1)
      - [捕获器处理程序参数](#捕获器处理程序参数-1)
      - [捕获器不变式](#捕获器不变式-2)
    - [has()](#has)
      - [返回值](#返回值-2)
      - [拦截的操作](#拦截的操作-2)
      - [捕获器处理程序参数](#捕获器处理程序参数-2)
      - [捕获器不变式](#捕获器不变式-3)
    - [defineProperty()](#defineproperty)
      - [返回值](#返回值-3)
      - [拦截的操作](#拦截的操作-3)
      - [捕获器处理程序参数](#捕获器处理程序参数-3)
      - [捕获器不变式](#捕获器不变式-4)
    - [getOwnPropertyDescriptor()](#getownpropertydescriptor)
      - [返回值](#返回值-4)
      - [拦截的操作](#拦截的操作-4)
      - [捕获器处理程序参数](#捕获器处理程序参数-4)
      - [捕获器不变式](#捕获器不变式-5)
    - [deleteProperty()](#deleteproperty)
      - [返回值](#返回值-5)
      - [拦截的操作](#拦截的操作-5)
      - [捕获器处理程序参数](#捕获器处理程序参数-5)
      - [捕获器不变式](#捕获器不变式-6)
      - [ownKeys()](#ownkeys)
      - [返回值](#返回值-6)
      - [拦截的操作](#拦截的操作-6)
      - [捕获器处理程序参数](#捕获器处理程序参数-6)
      - [捕获器不变式](#捕获器不变式-7)
    - [getPrototypeOf()](#getprototypeof)
      - [返回值](#返回值-7)
      - [拦截的操作](#拦截的操作-7)
      - [捕获器处理程序参数](#捕获器处理程序参数-7)
      - [捕获器不变式](#捕获器不变式-8)
    - [setPrototypeOf()](#setprototypeof)
      - [返回值](#返回值-8)
      - [拦截的操作](#拦截的操作-8)
      - [捕获器处理程序参数](#捕获器处理程序参数-8)
      - [捕获器不变式](#捕获器不变式-9)
    - [isExtensible()](#isextensible)
      - [返回值](#返回值-9)
      - [拦截的操作](#拦截的操作-9)
      - [捕获器处理程序参数](#捕获器处理程序参数-9)
      - [捕获器不变式](#捕获器不变式-10)
    - [preventExtensions()](#preventextensions)
      - [返回值](#返回值-10)
      - [拦截的操作](#拦截的操作-10)
      - [捕获器处理程序参数](#捕获器处理程序参数-10)
      - [捕获器不变式](#捕获器不变式-11)
    - [apply()](#apply)
      - [返回值](#返回值-11)
      - [拦截的操作](#拦截的操作-11)
      - [捕获器处理程序参数](#捕获器处理程序参数-11)
      - [捕获器不变式](#捕获器不变式-12)
    - [construct()](#construct)
      - [返回值](#返回值-12)
      - [拦截的操作](#拦截的操作-12)
      - [捕获器处理程序参数](#捕获器处理程序参数-12)
      - [捕获器不变式](#捕获器不变式-13)
  - [代理模式](#代理模式)
    - [跟踪属性访问](#跟踪属性访问)
    - [隐藏属性](#隐藏属性)
    - [属性验证](#属性验证)
    - [函数与构造函数参数验证](#函数与构造函数参数验证)
    - [数据绑定与可观察对象](#数据绑定与可观察对象)
- [函数](#函数-1)
  - [箭头函数](#箭头函数)
  - [函数名](#函数名)
  - [理解参数](#理解参数)
    - [箭头函数中的参数](#箭头函数中的参数)
  - [没有重载](#没有重载)
  - [默认参数值](#默认参数值)
    - [默认参数作用域与暂时性死区](#默认参数作用域与暂时性死区)
  - [参数扩展与收集](#参数扩展与收集)
    - [扩展参数](#扩展参数)
    - [收集参数](#收集参数)
  - [函数声明与函数表达式](#函数声明与函数表达式)
  - [函数作为值](#函数作为值)
  - [函数内部](#函数内部)
    - [arguments](#arguments)
    - [this](#this)
    - [caller](#caller)
    - [new.target](#newtarget)
  - [函数属性与方法](#函数属性与方法)
  - [函数表达式](#函数表达式)
  - [递归](#递归)
  - [尾调用优化](#尾调用优化)
    - [尾调用优化条件](#尾调用优化条件)
    - [使用尾调用优化](#使用尾调用优化)
  - [闭包](#闭包)
    - [this对象](#this对象)
    - [内存泄漏](#内存泄漏-1)
  - [立即调用的函数表达式](#立即调用的函数表达式)
  - [私有变量](#私有变量)
- [期约与异步函数](#期约与异步函数)

# 认识JavaScript
`JavaScript`包含: 核心(ECMAScript), 文档对象模型(DOM), 浏览器对象模型(BOM).

## ECMAScript
`ECMAScript`,即ECMA-262定义的语言.早期为了标准化JavaScript而建立的.`ECMAScript`用于建立脚本语言的基础,再次之上可以建立如`JavaScript`,`Adobe ActionScript`等语言.

`ECMAScript`的实现的宿主环境(host environment)不仅限于Web浏览器.宿主环境提供`ECMAScript`的基准实现和与自身交互的扩展.

`ECMAScript`不包含`输入`,`输出`,但定义了:
- 语法
- 类型
- 语句
- 关键字
- 保留字
- 操作符
- 全局对象

## DOM
`文档对象模型(DOM, Document Object Model)`是一个API.包含`DOM Core`和`DOM HTML`.  
前者提供了对`XML`访问和操作的功能,后者扩展并提供了对`HTML`的支持.

`DOM`将HTML解析为一个个节点  
如:
```
html
 ├---head
 |    └---title
 └---body
      ├---div
      |    └---img
      └---p
```

其他语言也提供了自己对`DOM`的扩展.

## BOM
`浏览器对象模型(BOM)`用于支持访问和操作浏览器的窗口,可以操控浏览器显示页面之外的部分.  
`BOM`没有标准的`JavaScript`实现,因此不同的浏览器的`BOM`不相同.

# HTML中的JavaScript
## &lt;script&gt;元素
将`JavaScript`插入`HTML`的主要方式是使用`<script>`元素.

`<script>`元素有下列属性:
- `async`: 布尔属性,可选.表示应该非阻塞并行下载脚本.只对外部脚本有效.
- `crossorigin`: 可选.配置相关请求的CORS(跨源资源共享)设置.默认不使用CORS.可选值见:[MDN-HTML-attributes-crossorigin](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Attributes/crossorigin).
- `defer`: 布尔属性,可选.表示脚本可以延迟到文档完全被解析和显示后再执行.只对外部脚本文件有效.
- `integrity`: 可选.允许比对接收到的资源和指定的加密签名以验证子资源完整性(SRI).如果接收到的资源的签名与这个属性指定的签名不匹配,则页面会报错,脚本不会执行.
- `src`: 可选.这个属性定义引用外部脚本的URI,这可以用来代替直接在文档中嵌入脚本.
- `type`:可选.该属性表示所代表的脚本类型(MIME类型).省略该属性或者值为空将默认为`text/javascript`.

## 嵌入
### 行内嵌入
可以直接将JS代码放入`<script>`元素.  
如:
````HTML
<script>
    function sayHi() {
        console.log("Hi");
    }
</script>
````
`<script>`中的代码会被从上到下解释.上述代码中的函数定义会被保存在解释器环境中.

默认情况下,`<script>`元素中的代码被计算完成前,其余内容不会被加载,也不会显示.

`行内代码`中出现`</script>`将会导致行内JS结束,即使是在字符串或注释中:
````HTML
<script>
    function sayHi() {
        // </script> Error
        console.log("</script>");
    }
</script>
````

使用转义字符`\`来避免错误:
````HTML
<script>
    function sayHi() {
        // <\/script> Error
        console.log("<\/script>");
    }
</script>
````

### 外部嵌入
使用`src`属性来嵌入外部代码.`src`的值是一个`URL`,指向包含`JavaScript`代码的文件,比如: `<script src="example.js"></script>`

在`XHTML`中,可以使用`<script src="example.js" />`.

注: 浏览器不会根据后缀名`.js`来判断是否是`JavaScript`.但服务器可能会根据后缀来响应`MIME类型`.

此外,如果外部嵌入代码中使用行内嵌入,如`<script src="example.js">function func() {}</script>`.则浏览器会忽略行内嵌入代码,仅执行外部代码.

此外,`URL`允许指向不是同一个域的JS文件,例如`<script src="http://example.com/afile.js"></script>`.

除非指定`defer`和`async`属性,否则浏览器会按照`<script>`在页面中出现的顺序依次解释.

**建议使用该方法引入JS**,原因如下:
- 易维护: 能够独立于HTML来编辑JS,且可以在多个页面中使用同一个JS文件
- 缓存: 若多个页面都使用到同一个文件,那么该文件就只需要下载一次.

建议将大的JS文件分割成多个小的JS文件.


## 元素详解
### 标签位置
`<script>`元素可以放到`<head>`标签内,但这会导致需要把这些代码下载,解析,解释完后,才会渲染(浏览器需要解析到`<body>`的起始标签时才会开始渲染).

现代Web应用程序通常会将所有JavaScript引用放在`<body>`元素中的页面元素的后面,如:
````HTML
<html>
    <head>
        <title>example</title>
    </head>
    <body>
        <!-- 页面内容 -->
        <script src="example1.js"></script>
        <script src="example2.js"></script>
    </body>
</html>
````

### 推迟执行脚本(defer)
`defer`布尔属性表示脚本在执行的时候不会改变页面的结构.脚本会延迟到整个页面都被解析完毕后再运行.

如:
````HTML
<!-- 立即下载,但延迟执行 -->
<script defer src="example1.js"></script>
<script defer src="example2.js"></script>
````
第一个推迟的脚本会在第二个推迟的脚本之前执行,而且两者都会在`DOMContentLoaded`事件之前执行. 在实际当中,少数情况下不一定会按照如上的顺序,因此最好只包含一个`defer`属性的脚本.

`HTML5`规定`defer`仅对外部脚本有效.

注:`XHTML`中,`defer`属性应写成`defer="defer"`

### 异步执行脚本(async)
`async`只适用于外部脚本,它告诉浏览器立刻执行下载,但不阻塞其他页面的加载,也不保证脚本的执行顺序(即使都是async的),即异步加载.

异步脚本保证在`load`事件前执行,但可能会在`DOMContentLoaded`之前或之后. 使用`async`也会告诉页面不会使用`document.write`.

注:`XHTML`中,`async`属性应写成`async="async"`

### 动态加载脚本
`JavaScript`可以使用`DOM API`通过向`DOM`中动态添加`script`来加载指定脚本.

如:
````JS
let script = document.createElement('script');
script.src = 'example.js';
document.head.appendChild(script);
````
上述代码在把`HTMLElement`发送到`DOM`且执行前,都不会发送请求.默认情况下,这种创建`<script>`元素的方式是异步的.使用`script.async=false`可以明确其为同步加载.

这种方式获取的资源对于预加载器是不可见的.会严重影响性能和资源获取队列的优先级.要让预加载器知道这些动态请求的链接存在,可以在文档的`<head>`中显式声明: `<link rel="preload" href="example.js">`

### 关于type
由于`MIME类型`没有跨浏览器标准化,导致浏览器可能会跳过`<script>`从而不执行其中的内容,因此,最好不指定`type`属性.

## XHTML中的JS
*XHTML已被弃用.*

`XHTML`中使用`JavaScript`必须指定`type`属性且值为`text/javascript`.

`HTML`中解析`<script>`会使用特殊规则,所以使用`<`和`>`不会有问题.

但是在`XHTML`中,`<`会被解析为一个标签的开始,所以应当使用`&lt;`.  
也可以把所有代码都包含到一个`CDATE块`中,在`XHTML`(以及`XML`)中,CDATA块中的文本都不会作为标签解析.
````XHTML
<script type="text/javascript"><![CDATA[
    function compare(a, b) {
        if (a < b) {
            console.log(1);
        }
        else if (a > b) {
            console.log(2);
        }
        else {
            console.log(3);
        }
    }
]]></script>
````
为了兼容不支持XHTML的浏览器,可以使用JS注释抵消,在支持XHTML的浏览器中也可以正常显示.
````XHTML
<script type="text/javascript">
//<![CDATA[
    function compare(a, b) {
        if (a < b) {
            console.log(1);
        }
        else if (a > b) {
            console.log(2);
        }
        else {
            console.log(3);
        }
    }
//]]>
</script>
````

## &lt;noscript&gt;元素
为了兼容早期不支持JavaScript的浏览器,使用`<noscript>`.

当出现以下情况之一时,`<noscript>`内的内容会被渲染:
- 浏览器不支持脚本
- 浏览器对脚本的支持被关闭

否则不会被渲染.


# 语言基础
## 基本语法
JavaScript是区分大小写的.

### 标识符
标识符,即变量,函数,属性,函数参数等的名称.标识符须满足以下要求:
- 第一个字符必须是`字母`,`_`或`$`.
- 剩下的符号可以是`字母`,`_`,`$`或`数字`.
- `字母`可以是扩展`ASCII`中的字母,也可以是Unicode的字母字符(但不推荐这样做).
- `ECMAScript`惯例使用驼峰法表示,如`doSomethingImportant`.该写法不是强制性的.
- 关键字,保留字,`true`,`false`,`null`不可以作为标识符.

### 注释
`JavaScript`使用`C`和`C++`风格的注释.
````JS
// comment

/*
 comment
*/
````

### 严格模式
ES5(ECMAScript 5)增加了严格模式的概念.严格模式是一种不同的JS解析和执行模型.一些不规范写法再这种模式下会被处理,不安全的活动将会抛出错误.

要启用严格模式,在脚本开头写上:
````JS
"use strict";
````
也可以单独让某个函数在严格模式下执行:
````JS
function doSomething() {
    "use strict";
    // ...
}
````
`"use strict";`实际上是一个预处理指令.

*严格模式所影响到的会在之后指出*

### 语句
ES中的语句以`;`结尾.若省略分号,则表明由解析器确定语句在哪里结尾,如:
````JS
let sum = a + b     // 有效,但不推荐
let diff = a - b;   // 有效,且推荐
````

多语句代码块可以合并多个语句.代码块由一个`{`开始,由一个`}`结束.

## 关键字和保留字
ES6中关键字包括:
- break
- case
- catch
- class
- const
- continue
- debugger
- default
- delete
- do
- else
- export
- extends
- finally
- for
- function
- if
- import
- in
- instanceof
- new
- return
- super
- switch
- this
- throw
- try
- typeof
- var
- void
- while
- with
- yield

ES6中未来的保留字:
- 始终保留:
  - enum
- 严格模式下保留:
  - implements
  - interface
  - let
  - package
  - protected
  - private
  - public
  - static
- 模块代码中保留:
  - await

## 变量
ES的变量是松散类型的,变量是保存任意值的占位符.声明变量的关键词有3个:`var`,`const`,`let`.  
`const`和`let`只能用于ES6及以上.

### var
定义变量,可以使用`var 变量名;`,如: `var message;`.  
`message`可以存储任何类型的值,若不初始化,则其值为`undefined`.

使用`var 变量名 = 值;`来初始化.
````JS
var message = "abc";    // 初始化
message = 100;  // message不会和字符串类型绑定,因此合法
````

`var`操作符定义的变量的作用域为整个函数:
如:
````JS
function test() {
    var message = "hi";
}
test();
console.log(message);   // Error, message is not defined
````
去掉`var`操作符将会定义全局变量,即使不是在全局范围定义的.(注意,不推荐这么做)  
如:
````JS
function test() {
    message = "hi";
}
test(); // 调用test()就会定义全局变量
console.log(message);   // YES,message是全局变量
````
*在严格模式下,这样给未声明的变量赋值会导致抛出ReferenceError.*

定义多个变量时,可以在一条语句内用逗号分隔每个变量(及其初始化).
如:
````JS
var message = "hi", found = false, undefinedValue, age = 29;
````
*严格模式下,不能定义名为`eval`和`arguments`的变量,否则会导致语法错误.*

**声明提升**:`var`声明的变量会自动提升到函数作用域顶部,如:
````JS
function test() {
    console.log(message);
    {
        var message = "hi";
    }
}
test();
````
等价于:
````JS
function test() {
    var message;
    console.log(message);   // undefined
    {
        message = "hi";
    }
}
test();
````
因此,反复声明同一个变量将会视作只声明一次:
````JS
function test() {
    var age = 16;
    var age = 26;
    var age = 36;
    console.log(age);   // 36
}
test();
````

### let
`let`与`var`的作用相似,但有区别.

`let`的声明范围时块作用域的,而`var`是函数作用域的,如:
````JS
function test1() {
    {
        let message = "hi";
    }
    console.log(message);   // Error, message is not defined
}
function test2() {
    {
        var message = "hi";
    }
    console.log(message);   // OK
}
test1();
test2();
````

但不同于`var`,`let`不允许同一个块作用域中出现冗余声明.
````JS
var name;
var name;

let age;
let age;    // Syntax Error
````

但依然遵循作用域大者隐藏的原则,如:
````JS
var a = 1;
console.log(a); // 1
{
    var a = 2;
    console.log(a); // 2
}

let b = 3;
console.log(b); // 3
{
    let b = 4;
    console.log(b); // 4
}
````

声明冗余不会因为混用`let`和`var`而受影响,因为这种两种声明方法声明的变量都是相同的,只是作用域不同,如:
````JS
var name;
let name;   // SyntaxError

let age;
var age;    // SyntaxError
````

*`let`声明的变量不会再作用域中被提升*,如:
````JS
console.log(age);   // ReferenceError
let age = 26;
````

使用`let`在全局作用域中声明的变量不会成为`window`对象的属性,但`var`会.(不过仍然是全局变量)
````JS
var name = "abc";
console.log(window.name);   // abc

var age = 18;
console.log(window.age);    // undefined
````

在HTML中要尤其注意变量是否声明过.
````HTML
<script>
    var name;
    let age;
</script>
<script>
    var name;   // OK
    let age;    // SyntaxError
</script>
````

在`for`中使用`let`声明可以避免作用域渗透的问题:
````JS
for (var i = 0; i < 5; ++i) {
    //...
}
console.log(i); // 5

for (let i = 0; i < 5; ++i) {
    //...
}
console.log(i); // ReferenceError

for (var i = 0; i < 5; ++i) {
    setTimeout(() => console.log(i), 0);
}
// 输出 5 5 5 5 5

for (let i = 0; i < 5; ++i) {
    setTimeout(() => console.log(i), 0);
}
// 输出 0 1 2 3 4
````

### const
`const`的行为与`let`类似.其行为包括:
- 不允许重复声明
- 作用域为块级
- 不能修改const声明的变量
- 必须在声明时初始化

注意:`const`的含义是该变量永远指向某个对象的引用而不改变.因此虽然不能再指向其他引用,但允许修改对象内部的属性.
````JS
const person = {};
person.name = 'abc';    // OK
````

想让整个对象都不能修改,可以使用`Object.freeze()`,这样再给对象赋值时虽然不会报错,但会静默失败:
````JS
const obj = Object.freeze({});
obj.name = "aaa";
console.log(obj.name);  // undefined
````

由于`for`每次迭代就创建一个新的循环变量,因此以下情况是合法的:
````JS
for (const value of [1,2,3,4,5]) {
    console.log(value);
}
// 1 2 3 4 5
````

### 推荐使用方式
不建议使用`var`.  
`const`优先,`let`次之.

## 数据类型
ES6的简单数据类型(原始类型)包括: `Undefined`,`Null`,`Boolean`,`Number`,`String`,`Symbol`(ES6新增).  
复杂数据类型为`Object`.`Object`是无序键值对的集合.

### typeof操作符
`typeof`操作符会返回下列字符串之一:
- `"undefined"`:值未定义
- `"boolean"`:布尔值
- `"string"`:字符串
- `"number"`:数值
- `"object"`:对象或`null`
- `"function"`:函数(严格来讲,ES中函数属于对象)
- `symbol`:符号

`typeof`不是函数,因此不需要使用参数写法:
````JS
let message = "some string";
console.log(typeof message);    // string
console.log(typeof(message));   // string
console.log(typeof 1);          // number
````

### Undefined类型
当`var`或`let`未初始化时,相当于给变量赋予了`undefined`值:
````JS
let msg;    // 等价于 let msg = undefined;
console.log(msg == undefined);  // true
````
`undefined`与未声明变量有本质区别.`undefined`变量可以使用,而未声明变量无法使用.对未声明变量使用`delete`不会报错,也无意义,但在严格模式下会抛出错误.

`typeof`操作符对`undefined`变量和未声明变量都返回`"undefined"`:
````JS
let msg;
console.log(typeof msg);    // undefined
console.log(typeof nope);   // undefined
````

`undefined`是一个假值(`false`):
````JS
let msg;
if (msg) {}     // NO
if (!msg) {}    // YES
if (nope) {}    // Error
````

### Null类型
`Null`类型只有一个值`null`.

`null`表示一个空对象指针.

`undefined`值是由`null`值派生而来的,因此表达式`null == undefined`返回true(此过程包含隐式转换).

`null`是一个假值(false).

### Boolean类型
`Boolean`类型有两个字面值:`true`和`false`.

注意:布尔值不同于数值,因此`true`不等于`1`,`false`不等于0.

使用`Boolean()`转型函数可以将其他类型转换为布尔值.
````JS
let value = true;
let msg = "abc";
value = Boolean(msg);
````
转换满足以下规则:
- Boolean
  - true -> true
  - false -> false
- String
  - 非空字符串 -> true
  - ""(空字符串) -> false
- Number
  - 非零数值(包括无穷值) -> true
  - 0 -> false
  - NaN -> false
- Object
  - 任意对象 -> true
  - null -> false
- Undefined
  - undefined -> false

对于`if`等流程控制语句,会自动执行其他类型到布尔值的转换.

### Number类型
`Number`类型使用IEEE 754格式表示整数和浮点数(双精度浮点小数).

#### 整数
整数上限为`2^53-1`,超过将变成浮点数.

````JS
// 十进制整数:
55
-1
// 八进制整数:
070     // 56
079     // 无效八进制,解析为79
// 注意: 在ES6中,要求八进制以0o(区分大小写)开头
0o70    // 56
// 在严格模式下,前缀0是错误语法,需要使用前缀0o
// 十六进制整数,前缀0x(区分大小写):
0xA     // 10
0x1f    // 31
````
注意,由于JS保存数值的方法,实际可能存在`+0`和`-0`的情况,但两者在任何情况下都相等.

#### 浮点数
定义一个浮点数,需要包含一个小数点,且小数点后面必须至少有一个数字:
````JS
1.1
0.1
.1
````
存储浮点数的空间是存储整数的两倍,因此ES优先将值存储为整数:
````JS
1.0     // 整数
1.      // 整数
````
可以使用科学计数法来表示数值,要求是整数或浮点数后跟大写或小写e,再加上要乘的(10)次幂:
````JS
3.125e7 // 31250000
3e-7    // 0.0000007
````
在转换为字符串或输出时,默认情况下如果小数点后包含至少6个0的小数会被转换为科学计数法.

注意,由于精度损失,使用`==`比较浮点数是不可取的.

#### 值的范围
`Number`的正最小值保存在`Number.MIN_VALUE`中,多数浏览器中是`5e-324`.最大值保存在`Number.MAX_VALUE`中,多数浏览器中是`1.7976931348623157e+308`.大于该值将会自动转换为`Infinity`,对于负数,则为`-Infinity`.

`Infinity`不能用于进一步的计算.可以使用`isFinite()`函数判断数值是否有穷. 如:
````JS
let res = Number.MAX_VALUE + Number.MAX_VALUE;
console.log(isFinite(res)); // false
````
使用`Number.NEGATIVE_INFINITY`获得`-Infinity`,使用`Number.POSITIVE_INFINITY`获得`Infinity`.

#### NaN
`NaN`意思是`不是数值(Not a Number)`,用于表示原来本来要返回数值的操作失败了(而不是抛出异常).

如:
````JS
0/0     // NaN
-0/+0   // NaN
````
若分子是非0值,则返回无穷.
````JS
5/0     // Infinity
5/-0    // -Infinity
````

任何涉及`NaN`的操作返回`NaN`.
````JS
NaN + 10    // NaN
````
`NaN`不等于包括`NaN`在内的任何数:
````JS
NaN == NaN  // false
````

`isNaN()`可以尝试将任意类型转换为`Number`,若转换结果不为`NaN`,则为`false`,否则为`true`. 例如:
````JS
isNaN(NaN);     // true
isNaN(10);      // false
isNaN("10");    // false
isNaN("blue");  // true
isNaN(true);    // false
````

#### 数值转换
数值转换的函数有3个:`Number()`,`parseInt()`和`parseFloat()`.

`Number()`函数的转换规则如下:
- Boolean
  - true -> 1
  - false -> 0
- Number: 直接返回
- null: 0
- undefined: NaN
- 字符串
  - 如果字符串包含数值字符,包括数值字符前面的`+`或`-`的情况,则转换为一个十进制数值. 如`Number("1") -> 1`, `Number("012") -> 12`, `Number("-14") -> -14`. 但`Number("12ab") -> NaN`.
  - 如果字符串包含有效的浮点数格式,如`1.1`,则会转换为响应的浮点数.
  - 如果字符串包含有效的(严格模式)八进制格式,如`0o70`,则转换为八进制对应的十进制.
  - 如果字符串包含有效的十六进制格式,如`0xf`,则转换为十六进制对应的十进制.
  - 空字符串返回0
  - 上述情况以外返回NaN
- 对象,调用`valueOf()`方法,并按上述方法转换返回值.如果返回NaN,则调用`toString()`方法,并按照字符串的转换规则.

一元加操作符与`Number()`函数遵循相同的转换规则.

`parseInt()`将数值转换为整数,它只关注字符串是否包含数值.  
例如:
````JS
parseInt("1234blue");   // 1234
parseInt("");           // NaN
parseInt("0xA");        // 10
parseInt("22.5");       // 22
````
可以给第二个参数提供进制:
````JS
parseInt("0xAF", 16);   // 175
parseInt("AF", 16);     // 175
parseInt("AF");         // NaN
parseInt("10", 2);      // 2
````

`parseFloat()`函数转换为浮点数(或整数),*只能解析十进制*  
例如:
````JS
parseFloat("1234blue"); // 1234,整数
parseFloat("0xA");      // 0
parseFloat("22.5");     // 22.5
parseFloat("22.34.5");  // 22.34
parseFloat("0908.5");   // 908.5
parseFloat("3.125e7");  // 31250000
````

### String类型
`String`能够表示0个或多个16位`Unicode`字符序列.  
字符串可以使用`"`(双引号),`'`(单引号),<code>`</code>(反引号)表示,这三种引号没有区别.

JS中同样支持转义字符:
```
\n \t \b \r \f \\ \' \" \` \xnn \unnnn(Unicode字符)
```
转义序列解析为1个字符.

使用`length`属性获取字符串中16位字符的个数.(若存在双字节字符,length返回的可能不是精确值)

ES中字符串是不可变的,变量指向的是字符串的引用.例如:
````JS
let lang = "Java";      // lang中包含"Java"
lang = lang + "Script";
/* lang指向"Java"和"Script"的字符串组合,即"JavaScript",此过程会先分配10个字符的空间.
随后会销毁原始字符串"Java"和"Script". */
````

#### toString()方法
数值,布尔值,对象和字符串都拥有`toString()`方法.  
对于字符串,返回其副本.
````JS
let a = 11;
a.toString();   // "11"
let b = true;
b.toString();   // "true"
11.toString();  // Error,方法不能用于数字字面量之后.
````
`null`和`undefined`不存在`toString()`方法.

对于数值类型,`toString()`允许接收一个参数,表明转换为几进制.
````JS
let num = 10;
num.toString(2);    // "1010"
````

#### String()转型函数
`String()`转型函数遵循以下规则:
- 如果有`toString()`方法,则调用该方法(无参),并返回其结果.
- 如果是`null`,则返回`"null"`.
- 如果是`undefined`,则返回`"undefined"`.

使用`值 + ""`,将会自动将前者转换为字符串.

#### 模板字面量
ES6支持通过反引号<code>`</code>来定义模板字面量

模板字符串允许保留换行字符.  
例如:
````JS
let myString = `first line
second line`;
let multiLineString = 'first line\nsecond line';

console.log(myString);
console.log(myString == multiLineString);
````
输出:
```
first line
second line
true
```

模板字面量支持字符串插值.模板字面量本质上不算字符串,但其求值之后为一个字符串.

字符串插值使用`${}`  
例如:
````JS
let value = 5;
let exponent = 'second';
// 非插值:
let interpolatedString = value + ' to the ' + exponent + ' power is ' + (value * value);
// 插值:
let interpolatedTemplateLiteral = `${value} to the ${exponent} power is ${value * value}`;

console.log(interpolatedString);            // 5 to the second power is 25
console.log(interpolatedTemplateLiteral);   // 5 to the second power is 25
````
所有插入的值都会调用`toString()`以转型为字符串:
````JS
let foo = { toString: () => 'World' };
console.log(`Hello, ${foo}!`);  // Hello, World!
````
嵌套的模板字符串无须转义:
````JS
console.log(`Hello, ${`World`}!`);  // Hello, World!
````
在插值表达式中可以调用函数和方法:
````JS
function capitalize(word) {
    return `${ word[0].toUpperCase() }${ word.slice(1) }`;
}
console.log(`${ capitalize('hello') }, ${ capitalize('world') }!`); // Hello, World!

let value = '';
function append() {
    value = `${value}abc`;
    console.log(value);
}
append();   // abc
append();   // abcabc
append();   // abcabcabc
````

模板字面量支持标签函数,标签函数本身式一个常规函数,通过前缀到模板字面量来应用自定义行为.  
例如:
````JS
let a = 6;
let b = 9;

function simpleTag(strings, aValExpression, bValExpression, sumExpression) {
    console.log(strings);
    console.log(aValExpression);
    console.log(bValExpression);
    console.log(sumExpression);
    return 'foobar';
}

let untaggedResult = `${a} + ${b} = ${a+b}`;
let taggedResult = simpleTag`${a} + ${b} = ${a + b}`;
// ["", " + ", " = ", ""]
// 6
// 9
// 15

console.log(untaggedResult);    // 6 + 9 = 15
console.log(taggedResult);      // foobar
````
因为表达式的参数往往是可变的,所以通常使用剩余操作符将它们收集到一个数组中:
````JS
function simpleTag(strings, ...expressions) {
    console.log(strings);
    for (const expression of expressions) {
        console.log(expression);
    }
    return 'foobar';
}
````
想要返回原始字符串,可以使用:
````JS
let a = 6;
let b = 9;

function zipTag(strings, ...expressions) {
    return strings[0] + expressions.map((e,i) => `${e}${strings[i + 1]}`).join('');
}

let untaggedResult = `${a} + ${b} = ${a + b}`;
let taggedResult = zipTag`${a} + ${b} = ${a + b}`;

console.log(untaggedResult);    // 6 + 9 = 15
console.log(taggedResult);      // 6 + 9 = 15
````

#### 原始字符串
使用JS默认的`String.raw`标签函数可以获取原始的模板字面量内容:  
````JS
console.log(`\u00A9`);  // ©
console.log(String.raw`\u00A9`);    // \u00A9

console.log(`first line\nsecond line`);
/*
first line
second line
*/
console.log(String.raw`first line\nsecond line`);   // first line\nsecond line
````
使用`.raw`属性获取每个字符串的原始内容:
````JS
function printRaw(strings) {
    for (const rawString of strings.raw) {
        console.log(rawString);
    }
}
printRaw`\u00A9${ 'separator' }\n`;
// \u00A9
// \n
````

### Symbol类型
`Symbol`(符号)是ES6新增的数据类型.符号是原始值,且符号示例是唯一,不可改变的.符号的用途是确保对象属性使用唯一标识符,不会发生属性冲突的危险.

#### 基本用法
符号需要使用`Symbol()`函数初始化.`typeof`操作符对符号返回`symbol`.
````JS
let sym = Symbol();
console.log(typeof sym);    // symbol
````
调用`Symbol()`函数时,也可以传入一个字符串参数作为对符号的描述,将来可以通过这个字符串来调试代码.但是,这个字符串参数与符号定义或标识符完全无关:
````JS
let fooSym = Symbol('foo');
let otherFooSym = Symbol('foo');

console.log(fooSym == otherFooSym); // false
````
符号没有字面量.

`Symbol()`不可与`new`关键字一起作为构造函数使用.而`Boolean`等类型允许构造函数且可以用于初始化包含原始值的包装对象(object):
````JS
let MyBool = new Boolean(); // OK
console.log(typeof myBool); // object

let Mysym = new Symbol();   // Error
````
如果确实想要使用符号包装对象,可以借用`Object()`函数:
````JS
let mySymbol = Symbol();
let myWrappedSymbol = Object(mySymbol);
console.log(myWrappedSymbol);   // object
````

#### 使用全局符号注册表
如果运行时的不同部分需要共享和重用符号示例,那么可以用一个字符串作为键,在全局符号注册表中创建并重用符号.  
为此,需要使用`Symbol.for()`方法.  
`Symbol.for()`会检查全局运行时注册表,若不存在对应符号,就会生成一个新符号示例并添加到注册表中,若存在符号,就会返回该符号示例:
````JS
let fooGlobalSymbol = Symbol.for('foo');    // 创建新符号
console.log(typeof fooGlobalSymbol);    // symbol
let otherFooGlobalSymbol = Symbol.for('foo');   // 重用已有符号
console.log(fooGlobalSymbol === otherFooGlobalSymbol);   // true
````
但全局注册表中定义的符号和使用`Symbol()`定义的符号并不等同:
````JS
let localSym = Symbol('foo');
let globalSym = Symbol.for('foo');
console.log(localSym === globalSymbol); // false
````
全局注册表中的符号必须使用字符串来创建,因此其参数会被转换为字符串.注册表中使用的键同时也会被用作符号描述:
````JS
let emptyGlobalSymbol = Symbol.for();
console.log(emptyGlobalSymbol);     // Symbol(undefined)
````
使用`Symbol.keyFor()`来查询全局注册表,这个方法接收符号,返回全局符号对应的字符串键.如果不是全局符号,则返回`undefined`.如果不是符号,则抛出`TypeError`:
````JS
let s = Symbol.for('foo');
console.log(Symbol.keyFor(s));  // foo

let s2 = Symbol('bar');
console.log(Symbol.keyFor(s2)); // undefined

Symbol.keyFor(123); // TypeError
````
#### 使用符号作为属性
能够使用字符串或者数值作为属性的地方,都可以使用符号.这就包括了`Object.defineProperty()`和`Object.defineProperties()`定义的属性:
````JS
let s1 = Symbol('foo'),
    s2 = Symbol('bar'),
    s3 = Symbol('baz'),
    s4 = Symbol('qux');
let o = {
    [s1]: 'foo val' // 符号只能通过计算属性语法来作为属性名定义
}
// 这样也可以: o[s1] = 'foo val';
console.log(o);
// {Symbol(foo): 'foo val'}
Object.defineProperty(o, s2, {value: 'bar val'});
console.log(o);
// {Symbol(foo): 'foo val', Symbol(bar): 'bar val'}
Object.defineProperties(o, {
    [s3]: {value: 'baz val'},
    [s4]: {value: 'qux val'}
});
console.log(o);
// {Symbol(foo): 'foo val', Symbol(bar): 'bar val',
// Symbol(baz): 'baz val', Symbol(qux): 'qux val'}
````
`Object.getOwnPropertyNames()`返回对象实例属性(非符号)数组,`Object.getOwnPropertySymbols()`返回对象实例的符号属性数值.两者互斥.  
`Object.getOwnPropertyDescriptors()`会返回同时包含常规和符号属性描述符的对象.`Reflect.ownKeys()`会返回两种类型的键.  
详见[对象](#对象)一节.

符号属性是对内存中符号的引用,所以直接创建并用作属性的符号不会丢失.但是,如果没有显式地保存这些属性的引用,那么必须遍历对象的所有符号属性才能找到相应的属性键:
````JS
let o = {
    [Symbol('foo')]: 'foo val',
    [Symbol('bar')]: 'bar val'
};
console.log(o);
// {Symbol(foo): "foo val", Symbol(bar): "bar val"}
let barSymbol = Object.getOwnPropertySymbols(o).find((symbol) => symbol.toString().match(/bar/));
console.log(barSymbol);
// Symbol(bar)
````

#### 常用内置符号
ES6引入了一批`常用内置符号`,用于暴露语言内部行为,开发者可以直接访问,重写或模拟这些行为.这些内置符号都以`Symbol`工厂函数字符串属性的形式存在.

可以通过重新定义内置符号来改变原生结构的行为.例如:`for-of`循环会在相关对象上使用`Symbol.iterator`属性,那么就可以通过在自定义对象上重新定义`Symbol.iterator`的值来改变`for-of`在迭代该对象时的行为.

这些内置符号是全局函数`Symbol`的普通字符串属性,指向一个符号的实例.所有内置符号属性都是不可写,不可枚举,不可配置的.

ES规范中使用前缀`@@`来表示符号,例如`@@iterator`表示`Symbol.iterator`.

##### Symbol.asyncIterator
该符号表示一个方法,该方法返回对象默认的`AsyncIterator`.由`for-await-of`语句使用,即实现异步迭代器API的函数.

`for-await-of`会调用以`AsyncIterator`为键的函数,并期望这个函数返回一个实现迭代器API的对象.该对象能够通过其`next()`方法陆续返回`Promise`实例.很多时候,返回的是`AsyncGenerator`:
````JS
class Foo {
    async *[Symbol.asyncIterator]() {}
}
let f = new Foo();
console.log(f[Symbol.asyncIterator]());
// AsyncGenerator(<suspended>)
````
````JS
class Emitter {
    constructor(max) {
        this.max = max;
        this.asyncIdx = 0;
    }
    async *[Symbol.asyncIterator]() {
        while (this.asyncIdx < this.max) {
            yield new Promise((resolve) => resolve(this.asyncIdx++));
        }
    }
}
async function asyncCount() {
    let emitter = new Emitter(5);
    for await (const x of emitter) {
        console.log(x);
    }
}
asyncCount();
// 0
// 1
// 2
// 3
// 4
````

##### Symbol.hasInstance
该符号表示一个方法,该方法决定一个构造器对象是否认可一个对象是它的实例.由`instanceof`操作符使用:
````JS
function Foo() {}
let f = new Foo();
console.log(f instanceof Foo);  // true
console.log(Foo[Symbol.hasInstance](f));    // true
class Bar {}
let b = new Bar();
console.log(b instanceof Bar);  // true
console.log(Bar[Symbol.hasInstance](b));    // true
````
这个属性定义在`Function`的原型上,因此默认在所有函数和类上都可以调用.可以在类上通过静态方法重新定义这个函数:
````JS
class Baz extends Bar {
    static [Symbol.hasInstance]() {
        return false;
    }
}
let bz = new Baz();
console.log(Bar[Symbol.hasInstance](bz));   // true
console.log(bz instanceof Bar); // true
console.log(Baz[Symbol.hasInstance](bz));   // false
console.log(bz instanceof Baz); // false
````

##### Symbol.isConcatSpreadable
该符号表示一个布尔值,如果为`true`,则对象应该用`Array.prototype.concat()`打平其数组元素.

**解释:**  
`Array.prototype.concat()`能够将数组与其他(类)数组的元素合并形成一个新的数组(原数组不受影响).

所谓打平,指的是针对参数(而非被调用方法的对象)而言:
> 若`arr = [1,2,3,4]`,`b = [2,3,4,5]`,参数打平时使用`arr.concat(b)`,其返回`[1,2,3,4,2,3,4,5]`.  
> 非打平时使用`arr.concat(b)`,其返回`[1,2,3,4,[2,3,4,5]]`  
> 打平只能针对类数组对象使用,而非打平能够针对一切对象使用.

一个对象的`Symbol.isConcatSpreadable`默认是`undefined`,这意味着对于`Array.prototype.concat()`,若其:
- 是数组,打平.
- 是类数组,非打平.
- 是其他对象,非打平.

若`Symbol.isConcatSpreadable`是`false`,这意味着对于`Array.prototype.concat()`,一切对象都是非打平的.

若`Symbol.isConcatSpreadable`是`true`,这意味着对于`Array.prototype.concat()`,若其:
- 是数组,打平.
- 是类数组,打平.
- 是其他对象,忽略.

例如:
````JS
let ini = ['foo'];

let arr = ['bar'];
console.log(arr[Symbol.isConcatSpreadable]);    // undefined
console.log(ini.concat(arr));   // ['foo','bar']
arr[Symbol.isConcatSpreadable] = false;
console.log(ini.concat(arr));   // ['foo',Array(1)]

let arrLikeObj = {length: 1, 0: 'baz'};
console.log(arrLikeObj[Symbol.isConcatSpreadable]); // undefined
console.log(ini.concat(arrLikeObj));    // ['foo',{...}]
arrLikeObj[Symbol.isConcatSpreadable] = true;
console.log(ini.concat(arrLikeObj));    // ['foo','baz']

let otherObj = new Set().add('qux');
console.log(otherObj[Symbol.isConcatSpreadable]);   // undefined
console.log(ini.concat(otherObj));  // ['foo', Set(1)]
otherObj[Symbol.isConcatSpreadable] = true;
console.log(ini.concat(otherObj));  // ['foo']
````

##### Symbol.iterator
该符号表示一个方法,该方法返回对象默认的迭代器.由`for-of`语句使用.即该符号表示实现迭代器API的函数.

`for-of`语句会调用以`Symbol.iterator`为键的函数,该函数应当返回一个实现迭代器API的对象.该对象能够通过其`next()`方法陆续返回值.很多时候,返回的对象是实现该API的`Generator`:
````JS
class Foo {
    async *[Symbol.iterator]() {}
}
let f = new Foo();
console.log(f[Symbol.iterator]());
// Generator(<suspended>)
````
````JS
class Emitter {
    constructor(max) {
        this.max = max;
        this.idx = 0;
    }
    *[Symbol.iterator]() {
        while (this.idx < this.max) {
            yield this.idx++;
        }
    }
}
function count() {
    let emitter = new Emitter(5);
    for (const x of emitter) {
        console.log(x);
    }
}
count();
// 0
// 1
// 2
// 3
// 4
````

##### Symbol.match
该符号表示一个正则表达式方法,该方法使用正则表达式去匹配字符串.由`String.prototype.match()`方法使用:
````JS
console.log(RegExp.prototype[Symbol.match]);
// ƒ [Symbol.match]() { [native code] }
console.log('foobar'.match(/bar/)); // match方法会使用RegExp的Symbol.match符号
// { 0: "bar", groups: undefined, index: 3, input: "foobar", length: 1, [[Prototype]]: Array }
````
给该方法传入`[Symbol.match]`为`undefined`的类型会被类型转换为正则表达式(若未定义,只有`RegExp`的`[Symbol.match]`不为`undefined`).

可重新定义`Symbol.match`(接受一个参数),其返回值没有限制:
````JS
class FooMatcher {
    static [Symbol.match](target) {
        return target.includes('foo')
    }
}
console.log('foobar'.match(FooMatcher));    // true
console.log('barbaz'.match(FooMatcher));    // false
````

##### Symbol.replace
该符号表示一个正则表达式方法,该方法替换一个字符串中匹配的子串.由`String.prototype.replace()`方法使用:
````JS
console.log(RegExp.prototype[Symbol.replace]);
// ƒ [Symbol.replace]() { [native code] }
console.log('foobarbaz'.replace(/bar/. 'qux')); // replace方法会使用RegExp的Symbol.replace符号
// 'fooquxbaz'
````
给该方法传入`[Symbol.replace]`为`undefined`的类型会被类型转换为正则表达式(若未定义,只有`RegExp`的`[Symbol.replace]`不为`undefined`).

可重新定义`Symbol.replace`(接受两个参数),其返回值没有限制:
````JS
class FooReplacer {
    static [Symbol.replace](target, replacement) {
        return target.split('foo').join(replacement);
    }
}
console.log('barfoobaz'.replace(FooReplacer, 'qux'));
// "barquxbaz"
````

##### Symbol.search
该符号表示一个正则表达式,该方法返回字符串中匹配正则表达式的索引.由`String.prototype.search()`方法使用.
````JS
console.log(RegExp.prototype[Symbol.search]);
// ƒ [Symbol.search]() { [native code] }
console.log('foobarbaz'.search(/bar/)); // search方法会使用RegExp的Symbol.search符号
// 3
````
给该方法传入`[Symbol.search]`为`undefined`的类型会被类型转换为正则表达式(若未定义,只有`RegExp`的`[Symbol.search]`不为`undefined`).

可重新定义`Symbol.search`(接受一个参数),其返回值没有限制:

````JS
class FooSearcher {
    static [Symbol.search](target) {
        return target.indexOf('foo');
    }
}
console.log('foobar'.search(FooSearcher));  // 0
console.log('barfoo'.search(FooSearcher));  // 3
console.log('barbaz'.search(FooSearcher));  // -1
````

##### Symbol.species
该符号表示一个函数,该函数作为创建派生对象的构造函数.要覆盖该符号,可以将其定义为静态获取器方法.该方法能够让调用方法时创建的是`Symbol.species`所指定的类型(例如阻止返回值的协变):
````JS
class Bar extends Array {}
class Baz extends Array {
    static get [Symbol.species]() {
        return Array;
    }
}
let bar = new Bar();
console.log(bar instanceof Array);  // true
console.log(bar instanceof Bar);    // true
bar = bar.concat('bar');
console.log(bar instanceof Array);  // true
console.log(bar instanceof Bar);    // true

let baz = new Baz();
console.log(baz instanceof Array);  // true
console.log(baz instanceof Baz);    // true
baz = baz.concat('baz');
console.log(baz instanceof Array);  // true
console.log(baz instanceof Baz);    // false
````

##### Symbol.split
该符号表示一个正则表达式方法,该方法在匹配正则表达式的索引位置拆分字符串.由`String.prototype.split()`方法使用:
````JS
console.log(RegExp.prototype[Symbol.split]);
// ƒ [Symbol.split]() { [native code] }
console.log('foobarbaz'.split(/bar/)); // split方法会使用RegExp的Symbol.split符号
// ['foo','baz']
````
给该方法传入`[Symbol.split]`为`undefined`的类型会被类型转换为正则表达式(若未定义,只有`RegExp`的`[Symbol.split]`不为`undefined`).

可重新定义`Symbol.split`(接受一个参数),其返回值没有限制:
````JS
class FooSplitter {
    static [Symbol.split](target) {
        return target.split('foo');
    }
}
console.log('barfoobaz'.split(FooSplitter));
// ['bar','baz']
````

##### Symbol.toPrimitive
该符号表示一个方法,该方法能够将对象转换为相应的原始值.由`ToPrimitive`抽象操作使用:
````JS
class Foo {}
let foo = new Foo();
console.log(3 + foo);   // "3[object Object]"
console.log(3 - foo);   // NaN
console.log(String(foo));   // "[object Object]"

class Bar {
    constructor() {
        this[Symbol.toPrimitive] = function(hint) {
            switch (hint) {
                case 'number':
                    return 3;
                case 'string':
                    return 'string bar';
                default:
                    return 'default bar';
            }
        }
    }
}
let bar = new Bar();
console.log(3 + bar);   // "3default bar"
console.log(3 - bar);   // 0
console.log(String(bar));   // "string bar"
````

##### Symbol.toStringTag
该符号表示一个字符串,该字符串用于创建对象的默认字符串描述.由内置方法`Object.prototype.toString`使用,默认为`"Object"`:
````JS
let s = new Set();  // 内置类型一般已经指定了值
console.log(s); // Set(0) {}
console.log(s.toString());  // [object Set]
console.log(s[Symbol.toStringTag]); // Set

class Foo {}
let foo = new Foo();    // 该自定义类型未指定值
console.log(foo);   // Foo {}
console.log(foo.toString());    // [object Object]
console.log(foo[Symbol.toStringTag]);   // undefined

class Bar {
    constructor() {
        this[Symbol.toStringTag] = 'Bar';
    }
}
let bar = new Bar();    // 该自定义类型指定了值
console.log(bar);   // Bar {}
console.log(bar.toString());    // [object Bar]
console.log(bar[Symbol.toStringTag]);   // Bar
````

##### Symbol.unscopables
该属性表示一个对象,该对象所有的以及继承的属性,都会从关联对象的`with`环境绑定中排除.设置这个符号并让其映射对应属性的键值为`true`,就可以阻止该属性出现在`with`环境绑定中:
````JS
let o = {foo: 'bar'};
with (o) {
    console.log(foo);   // bar
}
o[Symbol.unscopables] = {
    foo: true
};
with (o) {
    console.log(foo);   // ReferenceError
}
````

**<b class="yellow_font">由于`with`已经弃用,因此不推荐使用`Symbol.unscopables`.</b>**

### Object类型
对象是一组数据和功能的集合.对象通过`new`操作符后跟对象类型的名称来创建.

````JS
let o = new Object();
````
若构造时无参,允许省略括号(不推荐):
````JS
let o = new Object;
````

`Object`是派生其他对象的基类.`Object`类型的所有属性和方法在派生的对象上同样存在:
- `constructor`: 该属性用于创建当前对象的函数.对于`Object`,这个属性的值就是`Object()`函数.
- `hasOwnProperty(propertyName)`: 用于判断当前对象示例是否存在给定的属性.其中,`propertyName`必须是字符串或符号.
- `isPrototypeOf(object)`: 用于判断当前对象是否为另一个对象的原型.
- `propertyIsEnumerable(propertyName)`: 用于判断给定的属性是否可以使用`for-in`语句枚举.`propertyName`必须是字符串或符号.
- `toLocaleString()`: 返回对象的字符串表示.该字符串反映对象所在的本地化执行环境.
- `toString()`: 返回对象的字符串表示.
- `valueOf()`: 返回对象对应的字符串,数值或布尔值表示.通常与`toString()`的返回值相同.

*注意: 由于JS中还有BOM和DOM对象,这些对象可能不会继承于ES标准中的Object.*

## 操作符
操作符可以用于各种值,包括字符串,数值,布尔值和对象.在应用给对象时,操作符通常会调用`valueOf()`和/或`toString()`方法.
### 一元操作符
#### 递增/递减
*同C*

````JS
let age = 29;
++age;
--age;
age++;
age--;
````
- 对于字符串,会尝试转换为数值并计算,变量类型转换为数值.如果转换失败,变量的值为`NaN`.
- 对于布尔值,`false`转换为`0`,`true`转换为`1`,并执行计算,类型转变为数值.
- 对于浮点数,加1或减1.
- 对于对象,先调用其`valueOf()`方法,并应用上述规则.如果结果为`NaN`,则调用`toString()`并再次应用上述规则,类型转变为数值.

#### 一元加和减
*同C*

````JS
let num = 25;
num = +num; // 不变
num = -num; // 取相反数
````
对于非`Number`,执行`Number()`并使用该运算符,返回`Number`类型.

### 位运算符
JS中,64位整数存储格式是不可见,因此会法值转换位32位整数,进行操作之后,再把结果转换为64位.

32位存储格式与C++中`__int32`的存储结构一致,且默认情况下,ES中所有整数都为有符号的.

对于`NaN`和`Infinity`,在位操作中都会被当成`0`处理.

对于非数值,会使用`Number()`函数将值转换为数值.

*运算符的计算方法与C相同:*
- `~`(波浪号): 按位非
- `&`(和号): 按位与
- `|`(管道符): 按位或
- `^`(脱字符): 按位异或
- `<<`: 左移
- `>>`: 有符号右移(负数右移补1)
- `>>>`: 无符号右移(负数右移补0)

### 布尔操作符
*运算符的计算方法与C相同:*
- `!`(叹号): 逻辑非
- `&&`: 逻辑与(存在逻辑短路)
- `||`: 逻辑或(存在逻辑短路)

对于`!`,如果操作数不为`Boolean`类型,则会使用`Boolean()`转换类型后操作.

对于`&&`:
- 如果第一个操作数是对象,则返回第二个操作数.
- 如果第二个操作数是对象,则只有第一个操作数求值为true才会返回该对象.
- 如果两个操作数都是对象,则返回第二个操作数.
- 如果有一个操作数为`null`,则返回`null`.
- 如果有一个操作数为`NaN`,则返回`NaN`.
- 如果有一个操作数为`undefined`,则返回`undefined`.

对于`||`:
- 如果第一个操作数是对象,则返回第一个操作数.
- 如果第一个操作数求值结果为false,则返回第二个操作数.
- 如果两个操作数都是对象,则返回第一个操作数.
- 如果两个操作数都为`null`,则返回`null`.
- 如果两个操作数都为`NaN`,则返回`NaN`.
- 如果两个操作数都为`undefined`,则返回`undefined`.

### 乘性操作符
- `*`(星号): 乘法
- `/`(斜杠): 除法(*不是整除*)
- `%`(百分比符号): 取模

对于`*`:
- 如果不能用`Number`表示结果,返回`Infinity`或`-Infinity`.
- 任一操作数为`NaN`,则返回`NaN`.
- `Infinity`乘以`0`返回`NaN`.
- `Infinity`乘以非`0`数(包括`Infinity`),返回`Infinity`或`-Infinity`.
- 若操作数不是数值,先用`Number()`转换为数值后,应用上述规则.

对于`/`:
- 如果不能用`Number`表示结果,返回`Infinity`或`-Infinity`.
- 任一操作数为`NaN`,则返回`NaN`.
- `Infinity`除以`Infinity`返回`NaN`.
- `0`除以`0`返回`NaN`.
- 非`0`除以`0`,返回`Infinity`或`-Infinity`.
- `Infinity`除以任何数,返回`Infinity`或`-Infinity`.
- 若操作数不是数值,先用`Number()`转换为数值后,应用上述规则.

对于`%`:
- 无限值模有限值,返回`NaN`.
- 任一操作数为`NaN`,则返回`NaN`.
- `Infinity`模`Infinity`返回`NaN`.
- 有限值模`0`返回`NaN`.
- 有限值模无限值,返回该有限值.
- 若操作数不是数值,先用`Number()`转换为数值后,应用上述规则.

### 指数操作符
ES7新增了指数操作符`**`,等价于`Math.pow()`.

````JS
console.log(Math.pow(3, 2));    // 9
console.log(3 ** 2);            // 9
````

此外,允许使用`**=`.

### 加性操作符
- `+`: 加法
- `-`: 减法

对于`+`:
- 任一操作数为`NaN`,返回`NaN`.
- 如果`Infinity`加`Infinity`,返回`Infinity`.
- 如果`-Infinity`加`-Infinity`,返回`-Infinity`.
- 如果`Infinity`加`-Infinity`,返回`NaN`.
- 如果有一个操作数为字符串,则:
  - 两个操作数都为字符串,字符串拼接.
  - 如果有一个操作数是字符串,则将另一个操作数转换为字符串(即调用`toString()`方法,对于`undefined`和`null`,则调用`String()`函数)

对于`-`:
- 任一操作数为`NaN`,返回`NaN`.
- 如果`Infinity`减`-Infinity`,返回`Infinity`.
- 如果`-Infinity`减`Infinity`,返回`-Infinity`.
- 如果`Infinity`减`Infinity`,返回`NaN`.
- 如果`-Infinity`减`-Infinity`,返回`NaN`.
- 对于字符串,布尔值,null,undefined,使用`Number()`将其转换为数值后,应用上述规则.
- 对于对象,调用`valueOf`方法,并应用上述规则,如果其值为`NaN`,则使用`toString()`方法(即使用`Number()`函数),再应用上述规则.

### 关系操作符
- `<`: 小于
- `>`: 大于
- `<=`: 小于等于
- `>=`: 大于等于

规则如下:
- 如果操作数都是数值,执行数值比较.
- 如果操作数都是字符串,则逐个字符比较编码.
- 如果任一操作数为数值,则将另一操作数转换为数值(使用`Number()`).
- 如果任一操作数是对象,使用`Number()`函数转换.
- 如果有`Boolean`,将其转换为数值再执行比较.
- 任何比较涉及`NaN`,返回`false`.

如:
````JS
"23" < 3    // 23 < 3, false
"a" < 3     // NaN < 3, false
````

### 相等运算符
- `==`: 等于
- `!=`: 不等于
- `===`: 全等
- `!==`: 不全等

`==`与`!=`遵循以下规则:
- `Boolean`类型的操作数转换为数值.
- 字符串与数值比较,将字符串转换为数值.
- 一个操作数是对象,另一个不是,则调用对象的`valueOf`方法取得原始值,再根据之前的规则比较.

比较时,遵循以下规则:
- `null`和`undefined`相等.
- `null`和`undefined`不能转换为其他类型的值再进行比较.
- 任一操作数为`NaN`,则`==`返回`false`,`!=`返回`true`(`NaN == NaN`返回`false`).
- 两个操作数都是对象,若两个操作数指向同一个对象,两者相等.

对于`===`和`!==`操作符,比较时不执行类型转换,只有当类型与值完全相同时,才算相等,否则不等:
````JS
"55" === 55     // false
"55" !== 55     // true
null === undefined  // false
````

### 条件操作符
语法: `condition ? exp1 : exp2`.*与C相同*.

### 赋值操作符
`=`: 简单赋值.
如:
````JS
let num = 10;
num = 20;
````

复合赋值:
- `*=`
- `/=`
- `%=`
- `+=`
- `-=`
- `<<=`
- `>>=`
- `>>>=`

这些操作符仅仅是简写语法,使用它们不会提升性能.

### 逗号操作符
`,`: 逗号操作符,*同C*.

## 语句
流程控制语句中所有条件判断的表达式都会使用`Boolean()`函数转换为布尔值.

### if语句
*同C*

语法:
- `if (condition) statement`
- `if (condition) statement1 else statement2`
- `if (condition1) statement1 else if (condition2) statement2 else statement3`

允许使用`{}`合并多个语句:
````JS
if (condition) {
    // statement1
    // statement2
    // ...
}
````

### do-while语句
*同C*

````JS
do {
    statement
} while (expression);
````

### while语句
*同C*

````JS
while (expression) statement
````

### for语句
*同C*

````JS
for (initialization; expression; post-loop-expression) statement
````

### for-in语句
`for-in`语句是一种严格的迭代语句,用于枚举对象中的非符号键属性,语法为:
````JS
for (property in expression) statement
````
例如:
````JS
for (const propName in window) {
    document.write(propName);
}
````
上例使用`for-in`循环显示了`BOM`对象`window`的所有属性.

对象的属性是无序的(取决于浏览器),因此`for-in`不能保证返回对象属性的顺序.

### for-of语句
`for-of`语句是一种严格的迭代语句,用于遍历可迭代对象的元素,语法为:
````JS
for (property of expression) statement
````
例如:
````JS
for (const e1 of [2,4,6,8]) {
    document.write(e1);
}
````
`for-of`循环会按照可迭代对象的`next()`方法产生值的顺序迭代元素.如果尝试迭代的变量不支持迭代,则`for-of`语句会抛出错误.

ES2018增加了`for-await-of`循环.

### 标签语句
标签语句用于给语句加标签,语法如下:
````JS
label: statement
````
例如:
````JS
start: for (let i = 0; i < count; ++i) {
    console.log(i);
}
````
标签可以在后面通过`break`或`continue`语句引用.典型应用场景是嵌套循环.

### break和continue
*同C,但允许配合标签语句使用*

无标签:
````JS
for (let i = 1; i < 10; ++i) {
    if (i % 5 == 0) break;
    console.log(i);
}
for (let i = 1; i < 10; ++i) {
    if (i % 5 == 0) continue;
    console.log(i);
}
````

使用标签:
````JS
let num = 0;
outer1:
for (let i = 0; i < 10; ++i) {
    for (let j = 0; j < 10; ++j) {
        if (i == 5 && j == 5) {
            break outer1;
        }
        ++num;
    }
}
console.log(num);   // 55
// break outer1; 指示break退出的循环是外层的,因此运行到该行时,会退出两层循环.

num = 0;
outer2:
for (let i = 0; i < 10; ++i) {
    for (let j = 0; j < 10; ++j) {
        if (i == 5 && j == 5) {
            continue outer2;
        }
        ++num;
    }
}
console.log(num);   // 95
// continue outer2; 指示continue跳过的一次循环是外层的.
````

### with语句(已弃用)

> **<b class="red_font">已弃用,请不要在新的网站中使用</b>**

`with`语句的用途是将代码的作用域设置为特定的对象,其语法为: `with (expression) statement`.

例如,对于代码:
````JS
let qs = location.search.substring(1);
let homeName = location.hostname;
let url = location.href;
````
可以使用`with`简化为:
````JS
with (location) {
    let qs = search.substring(1);
    let hostName = hostname;
    let url = href;
}
````
类似于C++中在一个作用域内使用`using namespace`;

*注意: with语句会影响性能且难以调试其中的代码.*

*注意: 该特性已弃用.*

*严格模式下不允许使用with语句,否则会抛出错误.*

### switch语句
*类似C*

除了C语言中的用法,JS中,`case`后的值可以是变量或表达式,且允许比较任意类型.  
例如:
````JS
switch ("hello world") {
    case "hello" + " world":
        console.log("Greeting");
        break;
    case "goodbye":
        console.log("Closing");
        break;
    case "falling down":
        console.log("Nope");
    default:
        console.log("Unexpected");
        break;
}

let num = 25;
switch (true) {
    case num < 0:   // (num < 0) === true
        console.log("Less than 0.");
        break;
    case num >= 0 && num <= 10:     // (num >= 0 && num <= 10) === true
        console.log("Between 0 and 10.");
        break;
    default:
        console.log("More than 20.");
        break;
}
````
`switch`语句在比较每个条件的值时会使用全等操作符,因此不会强制转换数据类型.

## 函数
使用`function`关键字来声明函数:
````JS
function functionName(arg0, arg1,..., argN) {
    statement
}
````
使用`return`返回一个值:
````JS
function sum(num1, num2) {
    return num1 + num2;
}
````
执行完`return`后,之后的语句都不会执行.

使用`let result = sum(1, 2);`来调用并接收其返回值.

`return;`或没有`return`语句,将会返回`undefined`.

*在严格模式下:*
- 函数不能以`eval`或`arguments`作为名称.
- 函数的参数不能叫`eval`或`arguments`.
- 两个命名参数不能拥有同一个名称.

# 变量,作用域与内存
## 原始值与引用值
ES变量可以包含两种不同类型的数据: `原始值`和`引用值`.

原始值是最简单的数据,包括`Undefined`,`Null`,`Boolean`,`Number`,`String`,`Symbol`等.保存原始值的变量是按值访问的.

引用值是由多个值构成的对象.操作对象时,实际上操作的是对该变量引用的对象的操作,是按引用访问的.

### 动态属性
对于引用值而言,可以随时添加,修改和删除其属性和方法.  
例如:
````JS
let person = new Object();
person.name = "aaa";
console.log(person.name);   // aaa
````
原始值则不能有属性,尽管尝试给原始值添加属性不会报错:
````JS
let name = "aaa";
name.age = 27;
console.log(name.age);  // undefined
````

原始类型的初始化可以只使用原始字面量形式.如果使用了`new`关键字,则JS会创建一个`Object`类型的示例,但其行为类似原始值(但其实已经是引用类型了).  
例如:
````JS
let a = new String("aaa");
let b = String("bbb");
console.log(typeof a);  // object
console.log(typeof b);  // string
let c = a;
a.age = 27;
b.age = 27;
console.log(a.age);     // 27
console.log(b.age);     // undefined
console.log(c.age);     // 27
````

### 复制值
对于原始值,将一个变量赋值给另一个变量时,原始值会被复制到新的位置.  
![原始值赋值](img/get_start/value.jpg)

对于引用值,将一个变量赋值给另一个变量时,仅会将指针进行复制,两个指针指向同一个对象.  
![引用值赋值](img/get_start/reference.jpg)

### 传递参数
ES中所有函数的参数都是按值传递的,对于引用值来说,按值传递意思是复制一份指针并传入函数参数,两种仍然指向同一个变量.例如:  
````JS
function setName(obj) {
    obj.name = "aaa";   // obj->[old memory]<-person
    obj = new Object(); // obj->[new memory]  person->[old memory]
    obj.name = "bbb";
}
let person = new Object();
setName(person);
console.log(person.name);   // aaa
````
对于原始值,就是单纯的值的复制:
````JS
function addTen(num) {
    num += 10;
    return num;
}
let count = 20;
let result = addTen(count);
console.log(count);     // 20
console.log(result);    // 30
````

### 确定类型
由于`typeof`操作符对于所有对象或者`null`都返回`"object"`,因此针对引用值,要知道它是什么类型的对象,需要使用`instanceof`操作符.

语法: `result = variable instanceof constructor`.  
例如:
````JS
console.log(person instanceof Object);
console.log(colors instanceof Array);
console.log(pattern instanceof RegExp);
````
如果变量是给定引用类型(由其原型链决定)的实例,则`instanceof`操作符返回`true`.

`typeof`在检测函数时会返回`"function"`,此外任何实现内部`[[call]]`方法的对象都会在`typeof`检测时返回`"function"`.

## 执行上下文与作用域
变量或函数的执行上下文(以下简称"上下文")决定了它们可以访问哪些数据,以及它们的行为.每个上下文都有一个关联的变量对象,而这个上下文中定义的所有变量和函数都存在于这个对象上.虽然无法通过代码访问变量对象,但后台处理数据会用到它.

全局上下文是最外层的上下文.根据ES实现的宿主环境,表示全局上下文的对象可能不一样.在浏览器中,全局上下文是`window`对象.因此所有`var`定义的全局变量和函数都会成为`window`对象的属性和方法.使用`let`和`const`的顶级声明不会定义在全局上下文中,但在作用域链解析上效果是一样的.上下文在其所有代码都执行完毕后会被销毁,包括其上的变量和函数.

每个函数都有自己的上下文.调用函数时,函数进入上下文栈中.函数执行完后,上下文栈弹出该函数上下文,将控制权返还给之前的执行上下文.

上下文中的代码在执行的时候,会创建对象的作用域链.这个作用域链决定了各级上下文中的代码在访问变量和函数时的顺序.代码正在执行的上下文的变量对象始终位于作用域链的最前端.如果上下文是函数,则其活动对象用作变量对象.

代码执行时的标识符是通过沿作用域链逐级搜索标识符名称完成的.搜索过程从当前位置开始,逐级向前搜向顶级,且仅会沿链向外搜索.

例如:
````JS
var color = "blue";
function changeColor() {
    let anotherColor = "red";
    function swapColors() {
        let tempColor = anotherColor;
        anotherColor = color;
        color = tempColor;
        // 这里可以访问color, anotherColor, tempColor
    }
    // 这里可以访问color, anotherColor
    swapColors();
}
// 这里只能访问color
changeColor();
````
其作用域链为:
```
windows
 ├---color
 └---changeColor()
      ├---anotherColor
      └---swapColors()
           ├---swapColors
           └---tempColor
```

### 作用域链增强
执行上下文主要有全局上下文,函数上下文.

某些语句会导致在作用域链前端临时添加一个上下文,这个上下文会在上述语句执行后删除,这陈志伟作用域链增强.  
通常在两种情况下会出现这个现象:
- try/catch语句的catch块
- with语句

with语句会向作用域链前端添加指定的对象;对catch语句而言,则会创建一个新的变量对象,这个变量对象会包含要抛出的错误对象的声明.例如:
````JS
function buildUrl() {
    let qs = "?debug=true";
    with (location) {   // location被添加到作用域链前端,location已经预定义过了
        var url = href + qs;    // href指的是location.href
    }
    return url; // var定义的url会被提前到函数开头,因此此处可以访问
}
````

### 变量声明
见:
- [var](#var)
- [let](#let)
- [const](#const)

## 垃圾回收
JS是使用垃圾回收的语言,也就是执行环境负责在代码执行时管理内存.JS垃圾回收的思路是:确定哪个变量不会再使用,然后释放它占用的内存.这个过程是周期性的,即垃圾回收程序每隔一定事件就会自动运行.

确定变量不会使用的方法: `标记清理`和`引用计数`.

### 标记清理
JS最常用的垃圾回收策略是标记清理.当变量进入上下文,比如在函数内部声明一个变量时,这个变量就会被加上存在于上下文中的标记.此时永远不应该释放它们的内存.当变量离开上下文时,也会被加上离开上下文的标记.(加标记的方法有多种,但策略远重要于标记过程)

垃圾回收程序运行的时候,会标记内存中存储的所有变量,然后删除所有在上下文中的变量的标记,以及被上下文中引用的变量的标记.剩下未被删除标记的变量就是待删除的.随后就进行内存清理.

### 引用计数
思路是每个值都被记录它被引用的次数,当值被引用时,引用数加1,取消引用时,引用数减1.当一个值的引用数为0时,说明没办法访问到这个值了,因此可以安全的回收其内存了.

但这可能会导致循环引用,即`A`引用`B`,`B`引用`A`,两者的引用都为2,导致两者引用永远无法变成0.  
例如:
````JS
let element = document.getElementById("some_element");
let myObject = new Object();
myObject.element = element;
element.someObject = myObject;
````

早期浏览器会采用引用计数的方法.此外IE8及更早的版本中,BOM和DOM是C++实现的组件对象模型(COM),而COM对象使用引用计数实现垃圾回收.  
为了避免类似的循环引用问题,应该在确保不使用的情况下切断JS对象和DOM元素之间的连接.比如:  
````JS
myObject.element = null;
element.someObject = null;
````

### 性能
垃圾回收程序会周期性运行,如果内存中分配了很多变量,则会造成性能损失,因此垃圾回收的调度非常重要.

某些浏览器中可能运行主动触发垃圾回收的,但不推荐.

### 内存管理
使用垃圾回收的编程环境中,开发者通常无须关心内存管理,但是,浏览器的内存通常比分配给桌面软件的要少很多.因此将内存占用量保持在一个较小的值可以让页面的性能更好.

将全局变量和全局对象的属性设置为`null`(在其不必要时),可以释放其引用(解除引用).例如:
````JS
let globalObj = new Object();
// ...
globalObj = null;
````

使用`let`和`const`而不是`var`可以尽早的进行垃圾回收.

`Chrome`的`V8 JavaScript`使用隐藏类来优化性能.即避免动态属性赋值,并在构造函数中一次性声明所有属性,此时就共享一个隐藏类.例如:
````JS
function Article(opt_author) {
    this.title = 'aaa';
    this.author = opt_author;
}
let a1 = new Article();
let a2 = new Article('J');
````

但使用`delete`动态删除属性或者动态添加属性都会导致生成一个隐藏类:
````JS
delete a1.author;
a2.tmp = 0;
````
但可以尝试把不想要的属性设置为`null`:
````JS
a1.author = null;
````

#### 内存泄漏
写的不好的JS会导致内存泄漏问题.

意外的全局声明导致作为`window`的属性来创建:
````JS
function setName() {
    name = 'Jake';
}
````

定时器的回调通过闭包引用了外部对象:
````JS
let name = 'Jake';
setInterval(() => {
    console.log(name);
}, 100);
````

闭包造成内存泄漏:
````JS
let outer = function() {
    let name = 'Jake';  // 被引用
    return function() {
        return name;
    }
}
````

#### 静态分配和对象池
为了减少频繁垃圾回收导致的性能损失,可以合理使用分配的内存,避免多余的垃圾回收.

- 使用已经存在的对象:
````JS
// 原
function addVector(a, b) {
    let resultant = new Vector();
    resultant.x = a.x + b.x;
    resultant.y = a.y + b.y;
    return resultant;
}
// 改
function addVector(a, b, resultant) {
    resultant.x = a.x + b.x;
    resultant.y = a.y + b.y;
    return resultant;
}
````

- 使用对象池.  
在初始化的某一时刻,可以创建一个对象池,用来管理一组可回收的对象.应用程序可以向这个对象池请求一个对象.在操作完成后把它返回给对象池.对象池可以使用数组实现.例如:
````JS
let vectorList = new Array(100);
let vector = new Vector();
vectorList.push(vector);
````
JS数组是可变了,当容量超限时,会创建一个新的数组,并删除原来的数组,为避免上述操作,可以事先预测数组的大小.

# 基本引用类型
ES6之前不存在`类`,只存在引用类型,即把数据和功能组织到一起的结构.引用类型也被称为对象定义.

对象时某个特定引用类型的实例.新对象通过使用`new`操作符后跟一个`构造函数`来创建(不要尝试舍弃`new`,这将导致调用转型函数).例如:
````JS
let now = new Date();   // 默认构造
````

函数也是一种引用类型.

ES中提供了很多原生的引用类型.

## Date
`Date`类型将时间保存为自协调世界时(UTC, Universal Time Coordinated)时间1970年1月1日0时(UNIX纪元)至今所经过的毫秒数.能够记录自那时起之前及之后285616年的日期.

要创建日期对象,使用构造函数:
````JS
let now = new Date();
````
无参时,创建的对象将保存当前日期和时间.要基于其他日期和时间创建日期对象,必须传入其毫秒表示.

`Date.parse()`静态方法接收一个表示日期的字符串参数,尝试将这个字符串转换为表示该日期的毫秒数.其支持的格式为:
- `月/日/年`: 如`"5/23/2019"`.
- `月名 日, 年`: 如`"May 23, 2019"`.
- `周几 月名 日 年 时:分:秒 时区`: 如`"Tue May 23 2019 00:00:00 GMT-0700"`.
- `ISO 8601扩展格式"YYYY-MM-DDTHH:mm:ss.sssZ"`: 如`"2019-05-23T00:00:00"`.

创建一个表示2019年5月23日的日期对象:
````JS
let someDate = new Date(Date.parse("May 23, 2019"));
````

如果字符串无效,`Date.parse()`返回`NaN`.

将字符串传给`Date`构造函数,将会后台调用`Date.parse()`.

`Date.UTC()`静态方法也返回日期的毫秒表示,其接受的参数是年,0起点的月数(1月为0,2月为1...),日(1-31),时(0-23),分,秒和毫秒.这些参数中,中有前两个是必需的,如果不提供日,默认为1,其他的默认为0.

例如:
````JS
// 2005年5月5日下午5时55分55秒(GMT)
let day = new Date(Date.UTC(2005,4,5,17,55,55));
````

和`Date.parse()`一样,`Date.UTC()`也会被`Date`构造函数隐式调用,但这种情况下创建的是本地日期,**不是**GMT日期:
````JS
// 本地时间2000年1月1日0点
let day = new Date(2000, 0);
````

`Date.now()`静态方法返回表示方法执行时日期和时间的毫秒数:
````JS
let start = Date.now();

doSomething();

let stop = Date.now();
let result = stop - start;
````

### 继承的方法
`Date`类型重写了`toLocaleString()`,`toString()`和`valueOf()`方法.

`toLocaleString()`与浏览器和本地运行环境有关.  
例如:
````JS
let day = new Date(2024,0); // UTC+8
console.log(day.toString());
console.log(day.toLocaleString());
````
其结果为:
```
Mon Jan 01 2024 00:00:00 GMT+0800 (中国标准时间)
2024/1/1 00:00:00
```

`valueOf`方法不返回字符串,这个方法被重写后返回的是日期的毫秒表示.因此,操作符(如小于号和大于号)可以直接使用它返回的值.  
例如:
````JS
let date1 = new Date(2019,0,1);
let date2 = new Date(2019,1,1);

console.log(date1 < date2); // true
console.log(date1 > date2); // false
````

### 日期格式化方法
`Date`类型有专门几个用于格式化日期的方法,它们都会返回字符串.
- `toDateString()`
- `toTimeString()`
- `toLocaleDateString()`
- `toLocaleTimeString()`
- `toUTCString`

### 其他方法
详见[MDN-Date](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date),注意,方法中存在着`UTC`字眼的(`toUTCString`除外),表示没有时区偏移,即将日期转换为`GMT`(`UTC+0`)时的时间.

## RegExp
ES通过`RegExp`类型支持正则表达式.

用`字面量`创建正则表达式的语法为: `let expression = /pattern/flags;`  
其中`pattern`就是要匹配的正则表达式.每个正则表达式可以带0个或多个`flags`,用于控制正则表达式的行为.

匹配模式的标记`flags`包括:
- `g`: 全局模式,表示查找字符串的全部内容,而不是找到第一个匹配的内容就结束.
- `i`: 不区分大小写,表示在查找匹配时忽略`pattern`和字符串的大小写.
- `m`: 多行模式,表示查找到一行文本末尾时会继续查找.
- `y`: 黏附模式,表示只查找从`lastIndex`开始及之后的字符串.
- `u`: Unicode模式,启用Unicode匹配.
- `s`: dotAll模式,表示元字符.匹配任何字符(包括`\n`和`\r`).

例如:
````JS
// 匹配第一个"bat"或"cat",忽略大小写.
let pattern1 = /[bc]at/i;

// 匹配所有以"at"结尾的三字符组合,忽略大小写.
let pattern2 = /.at/gi;
````
`元字符`在正则表达式中都有一种或多种特殊功能,要匹配这些字符本身,`元字符`必须转义,包括:
` ( [ { \ ^ $ | ) ] } ? * + . `

例如:
````JS
// 匹配第一个"[bc]at",忽略大小写.
let pattern = /\[bc\]at/i;
````

使用构造函数创建正则表达式时,其构造函数接受两个参数: 模式字符串和(可选的)标记字符串.  
例如:
````JS
// 使用构造函数创建,相当于 /[bc]at/i
let pattern = new RegExp("[bc]at", "i");
````

注意,由于字符串中的`\\`代表`\`,因此所有元字符必须二次转义,例如:
```JS
/\[bc\]at/      ->  "\\[bc\\]at"
/\.at/          ->  "\\.at"
/name\/age/     ->  "name\\/age"
/\d.\d{1,2}/    -> "\\d.\\d{1,2}"
/\w\\hello\\123/-> "\\w\\\\hello\\\\123"
```

此外,`RegExp`允许基于已有的正则表达式示例,选择性的修改它们的标记:
````JS
const re1 = /cat/g;
console.log(re1);   // "/cat/g"
const re2 = new RegExp(re1);
console.log(re2);   // "/cat/g"
const re3 = new RegExp(re1, "i");
console.log(re3);   // "/cat/i"
````

### 属性
- `global`: 布尔值,表示是否设置了`g`标记.
- `ignoreCase`: 布尔值,表示是否设置了`i`标记.
- `unicode`: 布尔值,表示是否设置了`u`标记.
- `sticky`: 布尔值,表示是否设置了`y`标记.
- `lastIndex`: 静态属性,整数,表示在源字符串中下一次搜索的开始位置,字符从0开始.
- `multiline`: 布尔值,表示是否设置了`m`标记.
- `dotAll`: 布尔值,表示是否设置了`s`标记.
- `source`: 正则表达式的字面量字符串(不是传给构造函数的模式字符串),没有开头和结尾的`/`.
- `flags`: 正则表达式的标记字符串.始终以字面量而非传入构造函数的字符串模式形式返回(没有`/`).

例如:
````JS
let p = /\[bc\]at/i;
console.log(p.global);      // false
console.log(p.ignoreCase);  // true
console.log(p.multiline);   // false
console.log(p.lastIndex);   // 0
console.log(p.source);      // "\[bc\]at"
console.log(p.flags);       // "i"
````

### 方法
`exec()`方法用于匹配字符串,主要用于配合捕获组使用(即正则表达式语法中的`捕获`),该方法接受一个参数,即要匹配的字符串.如果找到了匹配项,则返回包含第一个匹配信息的数组.如果没有找到项,则返回`null`.返回的数组是`Array`的实例,且包含两个额外的属性:`index`和`input`.`index`是字符串中匹配模式的起始位置,`input`是要查找的字符串.数组的第一个元素是匹配整个模式的字符串,其他元素是正则表达式中捕获组匹配的字符串.如果没有捕获,则数组中只包含1个元素.

例如:
````JS
let text = "mom and dad and baby";
let p = /mom( and dad( and baby)?)?/gi;
let matches = p.exec(text);
console.log(matches.index); // 0
console.log(matches.input); // "mom and dad and baby"
console.log(matches[0]);    // "mom and dad and baby"
console.log(matches[1]);    // " and dad and baby"
console.log(matches[2]);    // " and baby"
````
设置全局标记则每次调用`exec()`方法都会返回下一个匹配的信息.如果没有设置全局标记,则无论对同一个字符串调用多少次`exec()`,也只会返回第一个匹配的信息.  
例如:
````JS
let t = "cat, bat, sat, fat";
let p = /.at/;
let m = p.exec(t);
console.log(m.index);       // 0
console.log(m[0]);          // cat
console.log(m.lastIndex);   // 0

m = p.exec(t);
console.log(m.index);       // 0
console.log(m[0]);          // cat
console.log(m.lastIndex);   // 0
````
````JS
let t = "cat, bat, sat, fat";
let p = /.at/g;
let m = p.exec(t);
console.log(m.index);       // 0
console.log(m[0]);          // cat
console.log(m.lastIndex);   // 3

m = p.exec(t);
console.log(m.index);       // 5
console.log(m[0]);          // bat
console.log(m.lastIndex);   // 8

m = p.exec(t);
console.log(m.index);       // 10
console.log(m[0]);          // sat
console.log(m.lastIndex);   // 13
````
对于黏附标记`y`,请看下面的示例:
````JS
let t = "cat, bat, sat, fat";
let p = /.at/y;
let m = p.exec(t);
console.log(m.index);       // 0
console.log(m[0]);          // cat
console.log(m.lastIndex);   // 3

// 以索引3对应的字符开头找不到匹配项,因此exec()返回null
// exec()没有找到匹配项,因此把lastIndex设置为0
m = p.exec(t);
console.log(m);             // null
console.log(m.lastIndex);   // 0

// 向前设置lastIndex可以让黏附的模式通过exec()找到下一个匹配项:
p.lastIndex = 5;
m = p.exec(t);
console.log(m.index);       // 5
console.log(m[0]);          // bat
console.log(p.lastIndex);   // 8
````

`test()`方法接收一个字符串,如果输入的文本存在匹配项,则返回`true`,否则返回`false`.  
例如:
````JS
let text = "000-00-0000";
let pattern = /\d{3}-\d{2}-\d{4}/;

if (pattern.test(text)) {
    console.log("The pattern was matched.");
}
````

`toLocaleString()`和`toString()`方法都返回其字面量的形式.`valueOf()`方法返回正则表达式本身.

### 构造函数属性
*非标准,请尽量不要在生产环境中使用它!*

- `input($_)`
- `lastMatch($&)`
- `lastParen($+)`
- <code>leftContext($`)</code>
- `rightContext($')`
- `$1`~`$9`

### 其他内容
更多内容详见:
- [MDN-JS-RegExp](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/RegExp)
- [正则表达式参考网站](https://www.regular-expressions.info/)
- [MDN-正则表达式](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Regular_expressions)

## 原始值包装类型
为了方便操作原始值,JS提供了3中特殊的引用类型`Boolean`,`Number`,`String`.

原始值不存在方法和属性,当尝试对某个原始值进行方法调用或者使用属性时,后台会创建一个相应原始包装类型的对象,从而暴露出操作原始值的各种操作.例如:  
````JS
let s1 = "some text";
let s2 = s1.substring(2);
````
此时,后台会执行以下3步:
````JS
let s_tmp = new String(s1); // 创建String原始值包装类型
let s2 = s_tmp.substring(2);    // 调用实例上的特定方法
s_tmp = null;   // 销毁实例
````
`Boolean`,`Number`类似.

因此,尝试给原始值添加属性,其实是给其临时原始值包装对象添加属性,再添加完属性后会立即销毁,因此最终获取属性时,结果为`undefined`.

可以显式地使用`Boolean`,`Number`和`String`构造函数创建原始包装对象.虽然其拥有一套方便操作数据的方法,不过只在必要时才这么做.原始包装类型使用`typeof`返回`"object"`,使用`Boolean()`转型函数返回`true`.

原始包装类型允许使用`instanceof`来判断类型,而对于原始值,始终返回`false`.
````JS
let obj = new Object("some text");
console.log(obj instanceof String); // true

let value = "some text";
console.log(value instanceof String);   // false
````

原始包装类型是引用类型,必须使用`new`创建,否则会认为调用其转型函数.例如:
````JS
let value = "25";
let num = Number(value);    // 转型函数
console.log(typeof num);    // "number"
let obj = new Number(value);    // 构造函数
console.log(typeof obj);    // "object"
````

### Boolean
`Boolean`是布尔值对应的引用类型.要创建`Boolean`对象,需要使用`Boolean`构造函数并传入`true`或`false`.例如:
````JS
let booleanObj = new Boolean(true);
````

`Boolean`的实例会重写`valueOf()`方法,返回原始值`true`或`false`.`toString()`方法返回字符串`"true"`或`"false"`.

`Boolean`对象用得极少.因为在条件表达式中,任何非`null`引用类型调用`Boolean()`转型函数返回`true`,因此导致:
````JS
let falseObj = new Boolean(false);
let result = falseObj && true;
console.log(result);    // true

let falseValue = false;
result = falseValue && true;
console.log(result);    // false
````
这将会导致错误发生.

### Number
`Number`是数值对应的引用类型.要创建`Number`对象,需要使用`Number`构造函数并传入一个数值.例如:
````JS
let numberObj = new Number(10);
````

`Number`类型重写了`valueOf()`,`toLocaleString()`和`toString()`方法.`valueOf()`返回`Number`对象的原始数值,另外两个方法返回数值的字符串.

`toString()`方法可选择性接收一个表示基数的参数,并返回相应基数进制的数值的字符串,默认十进制.
````JS
let num = 10;
console.log(num.toString());    // "10"
console.log(num.toString(2));   // "1010"
console.log(num.toString(8));   // "12"
console.log(num.toString(10));  // "10"
console.log(num.toString(16));  // "a"
````

`toFixed()`方法返回包含指定小数位数(可选参数,默认为0)的数值字符串,四舍五入.通常支持`0`~`20`小数位.
````JS
let num = 10;
console.log(num.toFixed(2));    // "10.00"
num = 10.005;
console.log(num.toFixed(2));    // "10.01"
````

`toExponential()`方法返回科学计数法的字符串,可选择性接收一个参数,表示小数位数,四舍五入.
````JS
let num = 10;
console.log(num.toExponential(1));  // "1.0e+1"
````

`toPrecision()`方法根据指定小数点位数返回最合理的输出结果,可能是定点表示法,也可能是科学计数法.通常支持`0`~`21`小数位.
````JS
let num = 99;
console.log(num.toPrecision(1));    // "1e+2"
console.log(num.toPrecision(2));    // "99"
console.log(num.toPrecision(3));    // "99.0"
````

`isInteger()`静态方法用于辨别一个数值是否保存为整数.例如:
````JS
Number.isInteger(1);    // true
Number.isInteger(1.00); // true
Number.isInteger(1.01); // false
````

`isSafeInteger()`静态方法用于辨别一个整数是否在`Number.MIN_SAFE_INTEGER`(-2^53+1)到`Number.MAX_SAFE_INTEGER`(2^53-1)之间.超出这个范围的整数可能会导致精度损失.

### String
`String`是字符串对应的引用类型.要创建`String`对象,需要使用`String`构造函数并传入一个字符串.例如:
````JS
let stringObj = new String("hello world");
````

`valueOf()`,`toLocaleString()`,`toString()`都返回对象的原始字符串值.

`length`属性返回字符串中的字符数量.(注意:ES中字符串是双字节字符组成的)

`charAt()`方法返回指定索引的字符.
````JS
let msg = "abcde";
console.log(msg.charAt(2)); // c
````

#### JS字符
JS字符串由16位码元构成的.多数字符每16个码元构成一个字符.

例如:
````JS
let str1 = "字符串string";
console.log(str1.length);   // 9
let str2 = "𰻝";     // 这个字是biang
console.log(str2.length);   // 2,单个字超出UTF-16的码位限制,需要用两个码位表示
````
JS字符串使用了两种Unicode编码混合策略: `UCS-2`和`UTF-16`.

`charCodeAt()`返回指定索引的字符的编码.
````JS
let msg = "abcde";
console.log(msg.charCodeAt(2)); // 99
````

`fromCharCode()`静态方法根据给定的UTF-16码元创建字符串中的字符.多个数值则会将其结果拼接.
````JS
console.log(String.fromCharCode(0x61,98,99,0x64,0x65)); // "abcde"
````

对于使用但码元的字符,Unicode中称为`基本多语言平面(BMP)`,对于其他字符,需要使用另外16位去选择一个`增补平面`,使用两个16位码元的策略称为`代理对`.

例如:
`````JS
let msg = "ab😊de";
console.log(msg.length);        // 6
console.log(msg.charAt(2));     // �
console.log(msg.charAt(3));     // �
console.log(msg.charCodeAt(2)); // 55357
console.log(msg.charCodeAt(3)); // 56842
console.log(String.fromCodePoint(0x1F60A)); // 😊
console.log(String.fromCharCode(97, 98, 55357, 56842, 100, 101))    // ab😊de
`````

`码点`是Unicode中一个字符的完整标识,它可能是16位,也可能是32位.例如:`c`的码点为`0x0063`,而`😊`为`0x1F60A`.

`codePointAt()`方法可以从指定码元位置识别完整的码点.
````JS
let msg = "ab😊de";
console.log(msg.charPointAt(2)); // 128522
console.log(msg.charPointAt(3)); // 56842
````
迭代字符串可以智能地识别代理对的码点:
````JS
console.log([..."ab😊de"]); // ['a', 'b', '😊', 'd', 'e']
````

`fromCodePoint()`方法接收任意数量的码点,返回对应字符拼接起来的字符串:
````JS
console.log(String.fromCharCode(97, 98, 128522, 100, 101)); // ab😊de
````

#### normalize()方法
有些Unicode字符有多种编码方法:
````JS
console.log(String.fromCharCode(0x00C5));   // 拉丁字母 Å
console.log(String.fromCharCode(0x212B));   // 单位 Å
console.log(String.fromCharCode(0x0041, 0x030A));   // 拉丁字母A上加圆圈 Å
````
三者不相等因为编码不相同.

Unicode提供了四种规范化来解决上述问题,规范化形式分别为:`NFD`,`NFC`,`NFKD`,`NFKC`.

通过对字符调用`normalize()`来应用规范化:
````JS
let a1 = String.fromCharCode(0x00C5),
    a2 = String.fromCharCode(0x212B);

console.log(a1 === a2);     // false
console.log(a1.normalize("NFD") === a2.normalize("NFD"));       // true
````

#### 字符串操作方法
`concat()`方法:将字符串拼接.
````JS
let str = "hello ";
let res = str.concat("world", "!");
console.log(res);   // "hello world!"
````

`slice()`方法:获取子串,不会修改原字符串.
````JS
let str = "hello world";
// 从3索引开始到结尾
console.log(str.slice(3));  // lo world
// 从3索引开始,到7索引结束,左闭右开
console.log(str.slice(3, 7));   // lo w
// 后3个字符
console.log(str.slice(-3));     // rld
// 从倒数第4个字符到倒数第1个字符,左闭右开
console.log(str.slice(-4, -1)); // orl
````

`substr()`方法 *(已弃用)*:获取子串,不会修改原字符串.
````JS
let str = "hello world";
// 从3索引开始到结尾
console.log(str.substr(3));  // lo world
// 从3索引开始,七个字符
console.log(str.substr(3, 7));   // lo worl
// 后3个字符
console.log(str.substr(-3));     // rld
// 第二个参数为负数时转换为0
console.log(str.substr(-4, -1)); // 
````

`substring()`方法:获取子串,不会修改原字符串.
````JS
let str = "hello world";
// 从3索引开始到结尾
console.log(str.substring(3));  // lo world
// 从3索引开始,到7索引结束,左闭右开
console.log(str.substring(3, 7));   // lo w
// 负数转换为0
console.log(str.substring(-3));     // hello world
// 负数转换为0
console.log(str.substring(-4, -1)); // 
````

`indexOf`:查找子串.第一个参数为查找到子串,第二个参数为开始查找的位置(默认值为0).返回第一个找到的子串的位置,如果没有,返回-1.

`lastIndexOf`:向前查找子串.第一个参数为查找到子串,第二个参数为开始查找的位置(默认值为`str.length - substr.length`).返回第一个找到的子串的位置(即指定位置之前最后的子串),如果没有,返回-1.

注:
````JS
let str = "hello world";
console.log(str.lastIndexOf("hello world", 0)); // 0
````
能够查找得到.

`startsWith()`:字符串是否以指定子串开始.第一个参数传入搜索的子串,第二个参数(可选,默认为0)指定检查开始的索引.

`endsWith()`:字符串是否以指定子串结尾.第一个参数传入搜索的子串,第二个参数(可选,默认为`str.length - substr.length`)指定检查开始的索引.

`includes()`:字符串是否包含指定子串.第一个参数传入搜索的子串,第二个参数(可选,默认为0)指定检查开始的索引.

`trim()`:创建字符串的副本,并删除其前后的空白符,并返回.

`trimLeft()`:删除起始的空白符.

`trimRight()`:删除末尾的空白符.

`repeat()`:接收一个整数参数,表示字符串复制的次数,返回拼接所有副本后的结果.

`padStart()`:若字符串小于指定长度,则在左侧填充指定字符串.第一个参数传入长度,第二个参数(可选)传入填充的字符串,默认为空格.不会截断.

`padEnd()`:若字符串小于指定长度,则在右侧填充指定字符串.第一个参数传入长度,第二个参数(可选)传入填充的字符串,默认为空格.不会截断.

`@@iterator`方法可以迭代字符串的每个字符:
````JS
let message = "abc";
let strIter = message[Symbol.iterator]();
console.log(strIter.next());    // {value: "a", done: false}
console.log(strIter.next());    // {value: "b", done: false}
console.log(strIter.next());    // {value: "c", done: false}
console.log(strIter.next());    // {value: undefined, done: true}
for (const c of "abc") {
    console.log(c);
}
// a
// b
// c
````
利用迭代器,可以用解构操作符来解构:
````JS
let msg = "abcde";
console.log([...msg]);  // ["a", "b", "c", "d", "e"]
````

`toUpperCase()`:转换为大写.

`toLocaleUpperCase()`:基于地区转换为大写.

`toLowerCase()`:转换为小写.

`toLocaleLowerCase()`:基于地区转换为小写.

`match()`:接收一个`RegExp`或其字面量,用于应用正则表达式匹配,返回值与RegExp.exec()相同.

`search()`:接收一个`RegExp`或其字面量,返回第一个匹配正则表达式的索引,如果没有,返回-1.始终从头开始匹配.

`replace()`:第一个参数接收`RegExp`或一个字符串,第二个参数可以是一个字符串或一个函数.将匹配正则表达式(如果要替换所有匹配子串,需要使用全局标记)或字符串(如果是字符串,则只会匹配第一个符合的)的替换为第二个参数的字符串或函数的返回值.  
对于第二个参数传入函数的情况,如果不存在捕获时,函数收到3个参数:`匹配的字符串`,`匹配项开始的位置`,`整个字符串`.  
更多细节详见:[MDN-JS-String-replace](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/replace#%E6%8C%87%E5%AE%9A%E5%87%BD%E6%95%B0%E4%BD%9C%E4%B8%BA%E6%9B%BF%E6%8D%A2%E9%A1%B9).

`split`:依据传入的分隔符将字符串拆分为数组.分隔符可以是字符串,也可以是`RegExp`.可选的第二参数确保分隔后的数组不会超过指定大小.

`localeCompare`:依据所在地区(国家和语言)决定字符串的比较,大于返回大于0的值,小于返回小于0的值,等于返回0.

## 单例内置对象
单例内置对象指的是由ES提供,与宿主环境无关,在ES程序开始执行时就存在的对象.
### Global
全局作用域中定义的变量和函数都会变成`Global`对象的属性.例如:`isNaN()`,`isFinite()`,`parseInt()`和`parseFloat()`.

还有其他函数:
#### URI编码方法
`encodeURI()`和`encodeURIComponent()`用于编码统一资源标识符(URI),以便传给浏览器.URI不得包含例如空格等字符,此时就可以使用URI编码方法.

`encodeURI()`用于对整个URI编码(例如:`www.example.com/illegal value.js`),但不会替换属于`URL`组件的特殊字符.

`encodeURIComponent()`用于编码URI中单独的组件(例如:`illegal value.js`),且会编码所有非标准字符.

例如:
````JS
let uri = "https://www.example.com/illegal value.js#start";
// https://www.example.com/illegal%20value.js#start
console.log(encodeURI(uri));
// https%3A%2F%2Fwww.example.com%2Fillegal%20value.js%23start
console.log(encodeURIComponent(uri));
````

`decodeURI()`只对`encodeURI()`编码的字符解码.  
`decodeURIComponent()`只对`encodeURIComponent()`编码的字符解码.  
例如:
````JS
let uri = "https%3A%2F%2Fwww.example.com%2Fillegal%20value.js%23start"
// https%3A%2F%2Fwww.example.com%2Fillegal value.js%23start
console.log(decodeURI(uri));
// https://www.example.com/illegal value.js#start
console.log(decodeURIComponent(uri));
````

#### eval()方法
`eval()`方法接收一个字符串,会将其作为ES语句解释.

例如:
````JS
eval("console.log('hello')");   // hello
````

在非严格模式下,传入`eval()`内的字符串会作为ES语句插入代码当中,且拥有相同的作用域.  
例如:
````JS
let msg = "hello world";
eval("console.log(msg);");  // hello world

eval("function sayHi() {console.log('Hi')}");
sayHi();    // Hi
````

*在严格模式下,`eval()`执行的语句拥有独立的作用域.*  
例如:
````JS
"use strict";
let msg = "hello world";
eval("console.log(msg);");  // hello world
eval("function sayHi() {console.log('Hi')}");
sayHi();    // ReferenceError
````

*严格模式下,不允许定义名为`eval`的变量*

`eval()`功能强大,但也很危险,因为这个方法会对XSS利用暴露出很大的攻击面.

#### 对象属性
- `undefined`:特殊值`undefined`.
- `NaN`:特殊值`NaN`.
- `Infinity`:特殊值`Infinity`.
- `Object`:`Object`的构造函数.
- `Array`:`Array`的构造函数.
- `Function`:`Function`的构造函数.
- `Boolean`:`Boolean`的构造函数.
- `String`:`String`的构造函数.
- `Number`:`Number`的构造函数.
- `Date`:`Date`的构造函数.
- `RegExp`:`RegExp`的构造函数.
- `Symbol`:`Symbol`的构造函数.
- `Error`:`Error`的构造函数.
- `EvalError`:`EvalError`的构造函数.
- `RangeError`:`RangeError`的构造函数.
- `ReferenceError`:`ReferenceError`的构造函数.
- `SyntaxError`:`SyntaxError`的构造函数.
- `TypeError`:`TypeError`的构造函数.
- `URIError`:`URIError`的构造函数.

#### window对象与Global
浏览器将`window`对象实现为`Global`对象的代理.因此,所有全局作用域中声明的变量和函数都变成了`window`的属性.

例如:
````JS
var color = "red";
function sayColor() {
    console.log(window.color);
}
window.sayColor();  // red
````

另一种获取Global对象的方式为:
````JS
let global = function() {
    return this;
}();
````
当`this`没有明确是哪个对象的方法也不是通过`call()`或`apply()`调用时,`this`值等于`Global`对象.

### Math
`Math`对象提供了一些辅助计算的属性和方法.

#### 属性
- `Math.E`:自然对数的基数e的值.
- `Math.LN10`:ln10.
- `Math.LN2`:ln2.
- `Math.LOG2E`:log(2,e).
- `Math.LOG10E`:log(10,e).
- `Math.PI`:π.
- `Math.SQRT1_2`:根号下1/2.
- `Math.SQRT2`:根号下2.

#### max()和min()
`max()`和`min()`静态方法接收任意多个参数,返回其最大值或最小值.

例如:
````JS
let min = Math.min(3, 54, 32, 16);
console.log(min);   // 3
let values = [1,2,3,4,5,6,7,8];
let max = Math.max(...values);
console.log(max);   // 8
````

#### 舍入方法(静态)
`Math.floor()`:向下取整.
`Math.round()`:四舍五入.
`Math.ceil()`:向上取整.
`Math.fround()`:返回数值最接近的单精度浮点数.

#### random()静态方法
`Math.random()`方法返回一个`[0,1)`区间的随机数.

但如果是为了加密而需要生成随机数,建议使用`window.crypto.getRandomValues()`.

#### 其他静态方法
- `Math.abs(x)`:x的绝对值.
- `Math.exp(x)`:e的x次幂.
- `Math.expm1(x)`:Math.exp(x) - 1.
- `Math.log(x)`:x的自然对数.
- `Math.log1p(x)`:1 + Math.log(x).
- `Math.pow(x,p)`:x的p次幂.
- `Math.hypot(num...)`:若干num平方和的平方根.
- `Math.clz32(x)`:32位整数x的前置0的数量.
- `Math.sign(x)`:返回表示x符号的`1`,`0`,`-0`或`-1`.
- `Math.trunc(x)`:x的整数部分.
- `Math.sqrt(x)`:x的平方根.
- `Math.cbrt(x)`:x的立方根.
- `Math.acos(x)`:x的反余弦.
- `Math.acosh(x)`:x的反双曲余弦.
- `Math.asin(x)`:x的反正弦.
- `Math.asinh(x)`:x的反双曲正弦.
- `Math.atan(x)`:x的反正切.
- `Math.atanh(x)`:x的反双曲正切.
- `Math.atan2(y,x)`:y/x的反正切.
- `Math.cos(x)`:x的余弦.
- `Math.sin(x)`:x的正弦.
- `Math.tan(x)`:x的正切.

# 集合引用类型
## Object
`Object`实例适合存储和在应用程序间交换数据.

创建`Object`实例:
````JS
// 使用new操作符和Object构造函数
let person = new Object();  // 等价于let person = {};
person.name = "aaa";
person.age = 18;
````
````JS
// 使用对象字面量
let person = {
    name: "aaa",
    age: 29
}
````
在使用对象字面量表示法定义对象时,并不会实际调用`Object`构造函数.

允许使用中括号语法读写属性:
````JS
let property = "name";
let o = {
    [property]: "aaa"
}
console.log(o.name);        // aaa
console.log(o[property]);   // aaa
console.log(o["name"]);     // aaa
o["whitespace between words"] = "vaild";
````

## Array
ES中的`Array`允许动态调整大小,允许存储不同类型的数据.

### 创建数组
创建数组的基本方法:
````JS
let colors = new Array();   // 默认构造
let colors = new Array(20); // 创建length为20的数组
let colors = new Array("red", 'blue', `green`); // 创建包含3个字符串的数组
// 向Array构造函数中传入一个参数时,如果该参数是数组,当该数值为整数,则会创建一个长度为指定数值的数组,当该数值为小数,则会抛出错误.如果是其他类型的,则会创建一个包含该特定值的数组.
let arr1 = new Array(3.4);  // RangeError
let arr2 = new Array(3);    // length: 3
let arr3 = new Array("12"); // length: 1
console.log(arr2);  // [空 ×3]
console.log(arr3);  // ['12']
````
使用`Array`构造函数时,也可以省略`new`,效果是一样的.

也可以使用数组字面量创建:
````JS
let colors = ['red', 'blue', 'green', 0];   // 创建包含4个元素的数组
let names = []; // 创建一个空数组
let values = [1,2,];    // 创建一个包含2个元素的数组,末尾的逗号会被省略,length为2
````
注意,在使用数组字面量表示法创建数组不会调用`Array`的构造函数.


# 迭代器与生成器

# 对象,类,面向对象编程
ES中对象是一组属性无序的集合.对象的每个属性或方法都由一个名称来标识,名称映射到一个值.因此,可以把ES对象当作一个`unordered_map`.

## 对象
创建自定义对象的通常方法是创建`Object`的一个新实例,然后再给它添加属性和方法.  
例如:
````JS
let person = new Object();
person.name = "aaa";
person.age = 18;
person.job = "CS";
person.sayName = function() {
    console.log(this.name);
};
````
其中`sayName()`方法中的`this.name`会被解析为`person.name`.

还可以通过对象字面量的形式创建对象.  
例如:
````JS
let person = {
    name: "aaa",
    age: 18,
    job: "CS",
    sayName() {
        console.log(this.name);
    }
};
````

能够作为对象名的有`字符串`,`数值`和`符号`:
````JS
let s = Symbol('foo');
let o = {
    "key": "value", // 字符串属性
    1.2: "aaa",     // 虽然写的是数值,但会被解析为字符串属性"1.2"
    1: "bbb",       // 数值属性
    [s]: "ccc"      // 符号属性
};
````

### 属性的类型
ES使用内部特性来描述属性.它是由JS实现定义的,因此不能直接访问这些特性.为了标识内部特性,以下使用两个中括号把特性的名称括出来,例如:`[[Enumerable]]`.即特性是ES内置的私有属性.

属性分两种:`数据属性`和`访问器属性`.

#### 数据属性
数据属性包含一个保存数据值的位置.值会从这个位置读取,也会写入到这个位置.数据属性有以下特性描述它们的行为.
- `[[Configurable]]`:表示属性是否可以通过`delete`删除并重新定义,是否可以修改它们的特性,以及是否可以把它改为访问器属性.默认情况下,所有直接定义在对象上的属性的这个特性都是`true`.
- `[[Enumerable]]`:表示属性是否可以通过`for-in`循环访问.默认情况下,所有直接定义对象上的属性的这个特性都为`true`.
- `[[Writable]]`:表示属性的值是否可以被修改.默认情况下,所有直接定义在对象上的属性的这个特性都是`true`.
- `[[Value]]`:包含属性实际的值.这就是读取和写入属性值的位置.默认为`undefined`.

例如:
````JS
let person = {
    name: "aaa"
};
````
`[[Configurable]]`,`[[Enumerable]]`,`[[Writable]]`为`true`,`[[Value]]`为`"aaa"`.

要修改属性的默认特性,就必须使用`Object.defineProperty()`静态方法.这个方法接收3个参数:要给其添加属性的对象,属性的名称和一个描述符对象.标识符对象可以包含`configurable`,`enumerable`,`writable`和`value`.  
例如:
````JS
let person = {};
Object.defineProperty(person, "name", {
    writable: false;
    value: "aaa"
});
console.log(person.name);   // aaa
person.name = "bbb";
console.log(person.name);   // aaa
````
上例创建了只读的`name`属性,其值为`"aaa"`.

*在非严格模式下给只读属性赋值会被忽略,在严格模式下会报错.对不可配置的属性也是如此.*

````JS
let person = {};
Object.defineProperty(person, "name", {
    configurable: false,
    value: "aaa"
});
console.log(person.name);   // "aaa"
delete person.name; // 严格模式下报错
console.log(person.name);   // "aaa"
Object.defineProperty(person, "name", {
    configurable: true, // 任何情况下都会报错
});
````
不可配置的属性再次调用`Object.defineProperty()`并修改任何非`writable`属性会导致错误.

在调用`Object.defineProperty()`时,`configurable`,`enumerable`,`writable`的值如果不指定,则**默认为`false`**.

#### 访问器属性
访问器属性不包含数据值.相反,它们包含一个获取函数和一个设置函数(`C#`里的那种).不过这两个函数不是必需的.读取访问器属性时,会调用获取函数,得到其返回值.写入访问器属性时,会调用设置函数,对数据做出修改.访问器属性有以下特性:
- `[[Configurable]]`:表示属性是否可以通过`delete`删除并重新定义,是否可以修改它们的特性,以及是否可以把它改为数据属性.默认情况下,所有直接定义在对象上的属性的这个特性都是`true`.
- `[[Enumerable]]`:表示属性是否可以通过`for-in`循环访问.默认情况下,所有直接定义对象上的属性的这个特性都为`true`.
- `[[Get]]`:获取函数,在读取属性时调用.默认为`undefined`.
- `[[Set]]`:设置函数,在写入属性时调用.默认为`undefined`.

访问器属性不能直接定义,必须使用`Object.defineProperty()`.  
例如:
````JS
let book = {
    year_: 2022,    // 伪私有成员,下划线表示该属性并不希望在对象方法的外部被访问
    edition: 1
};
Object.defineProperty(book, "year", {
    get() {
        return this.year_;
    },
    set(newValue) {
        if (newValue > 2022) {
            this.year_ = newValue;
            this.edition = newValue - 2021;
        }
    }
});
book.year = 2024;
console.log(book.edition);  // 2
````
获取函数和设置函数不一定都要定义.只定义获取函数意味着属性是只读的,*在非严格模式下,尝试修改属性会被忽略.在严格模式下,则会抛出错误*.只定义设置函数的属性是不能读取的,*在非严格模式下读取会返回`undefined`,在严格模式下会抛出错误*.

### 定义多个属性
`Object.defineProperties()`静态方法用于同时定义多个属性.其参数为要添加或修改属性的对象和描述符对象.  
例如:
````JS
let book = {};
Object.defineProperties(book, {
    year_: {
        writable: true, // necessary
        value: 2017
    },
    edition: {
        writable: true,
        value: 1
    },
    year: {
        get() {
            return this.year_;
        },
        set(newValue) {
            if (newValue > 2017) {
                this.year_ = newValue;  // 即使是对象内部,也不能对只读属性修改
                this.edition += newValue - 2017;
            }
        }
    }
});
````
在调用`Object.defineProperties()`时,`configurable`,`enumerable`,`writable`的值如果不指定,则**默认为`false`**.

### 读取属性的特性
使用静态方法`Object.getOwnPropertyDescriptor()`可以取得指定属性的属性描述符.这个方法接收两个参数:属性所在的对象和要取得其描述符的属性名.返回的是一个对象,对于访问器属性,包含`configurable`,`enumerable`,`get`和`value`属性,对于数据属性包含`configurable`,`enumerable`,`writable`和`value`属性.  
例如:
````JS
let book = {};
Object.defineProperties(book, {
    year_: {
        writable: true,
        value: 2024
    },
    year: {
        get() {
            return this.year_;
        },
        set(newValue) {
            this.year_ = newValue;
        }
    }
});
let descriptor = Object.getOwnPropertyDescriptor(book, "year_");
console.log(descriptor.value);          // 2024
console.log(descriptor.configurable);   // false
console.log(typeof descriptor.get);     // "undefined"
descriptor = Object.getOwnPropertyDescriptor(book, "year");
console.log(descriptor.value);      // undefined
console.log(descriptor.enumerable); // false
console.log(typeof descriptor.get); // "function"
````

`Object.getOwnPropertyDescriptors()`静态方法传入一个对象,对该对象的每个属性都获取其描述符.  
例如:
````JS
let book = {};
Object.defineProperties(book, {
    year_: {
        writable: true,
        value: 2024
    },
    year: {
        get() {
            return this.year_;
        },
        set(newValue) {
            this.year_ = newValue;
        }
    }
});
console.log(Object.getOwnPropertyDescriptors(book));
// {
//     year: {
//         configurable: false,
//         enumerable: false,
//         get: f(),
//         set: f(newValue)
//     },
//     year_: {
//         configurable: false,
//         enumerable: false,
//         value: 2024,
//         writable: true
//     }
// }
````
### 合并对象
`Object.assign()`静态方法接收一个目标对象和一个或多个源对象作为参数,然后将每个对象中可枚举(`Object.propertyIsEnumerable()`返回`true`)和自有(`Object.hasOwnProperty()`返回`true`.自有属性,即非静态的类成员)属性复制到目标对象.以字符串和符号为键的属性会被复制.对于每个符合条件的属性,这个方法会使用源对象上的`[[Get]]`取得属性的值,然后使用目标对象上的`[[Set]]`设置属性的值.  
例如:
````JS
let dest = {}
let src = { id: 'src' };
let result = Object.assign(dest, src);
// Object.assign修改目标对象也会返回修改完后的目标
console.log(dest === result);   // true, 两者引用同一实例
console.log(dest !== src);      // true, 两者不是同一实例
console.log(result);            // { id: src }
console.log(dest);              // { id: src }

dest = {};
Object.assign(dest, { a: 'foo' }, { b: 'bar' });
console.log(dest);  // { a: 'foo', b: 'bar' }

dest = {
    a_: "a",
    set a(val) {    // 设置函数,这是简写的形式
        console.log(`set`);
        this.a_ = val;
    }
};
src = {
    get a() {
        console.log(`get`);
        return "b";
    }
};
Object.assign(dest, src);
// get
// set
console.log(dest);  // { a_: 'b' }
````
`Object.assign()`执行的是浅复制.如果多个源对象有相同的属性,则使用最后一个复制的值.此外,获取函数和设置函数不能在两个对象之间转移.

````JS
dest = {};
src = { a: {} };
Object.assign(dest, src);
console.log(dest);              // { a: {} }
console.log(dest.a === src.a);  // true
````
如果`Object.assign()`赋值的期间抛出错误,则操作会终止并退出,之后的操作不会执行,之前的操作也不会回滚.

### 对象标识及相等判定
对于`===`操作符,由于具有特殊规则,导致全等判断并不精确.  
例如:
````JS
// expected
true === 1;     // false
{} === {};      // false
"2" === 2;      // false
// unexpected
+0 === -0;      // true
+0 === 0;       // true
-0 === 0;       // true
NaN === NaN;    // false
````
使用静态方法`Object.is()`:
````JS
Object.is(true, 1);     // false
Object.is({}, {});      // false
Object.is("2", 2);      // false
Object.is(+0, -0);      // false
Object.is(+0, 0);       // true
Object.is(-0, 0);       // false
Object.is(NaN, NaN);    // true
````

### 增强的对象语法
#### 属性值简写
在给对象添加变量时,若属性名和变量名是一样的:
````JS
let name = 'a';
let person = {
    name: name
};
console.log(person);    // { name: 'a' }
````
则可以简写为:
````JS
let name = 'a';
let person = {
    name        // 只要使用变量名,不写冒号,就会自动被解释为变量和属性同名
};
console.log(person);    // { name: 'a' }
````
#### 可计算属性
如果想要使用变量的值作为属性名,曾经就必须使用中括号语法来添加属性,也就是不能在对象字面量中直接动态命名属性.例如:
````JS
const nameKey = 'name';
const ageKey = 'age';
const jobKey = 'job';

let person = {};
person[nameKey] = 'aaa';
person[ageKey] = 18;
person[jobKey] = 'CS';

console.log(person);    // { name: 'aaa', age: 18, job: 'CS' }
````
使用ES6中的可计算属性,可以在对象字面量中完成动态属性赋值.中括号包围的对象属性键表明其为JS表达式而不是字符串:
````JS
const nameKey = 'name';
const ageKey = 'age';
const jobKey = 'job';

let person = {
    [nameKey]: 'aaa',
    [ageKey + "_value"]: 18,
    [function f(value) { return value + "_now"; }(jobKey)]: 'CS'
};
console.log(person);    // {name: 'aaa', age_value: 18, job_now: 'CS'}
````
注意:可计算属性表达式中抛出的任何错误都会中断对象创建,而且之前完成的计算是不会回滚的,这导致如果表达式存在副作用是会有影响的.

#### 简写对象名
在给对象定义一个方法时,通常要写一个方法名,冒号,再引用一个(匿名)函数表达式.  
例如:
````JS
let person = {
    sayName: function(name) {
        console.log(name);
    }
};
person.sayName('a');    // a
````
简写方法的语法允许写成这样:
````JS
let person = {
    sayName(name) {
        console.log(name);
    }
};
person.sayName('a');    // a
````
允许对获取函数和设置函数简写:
````JS
let person = {
    name_: '',
    get name() {
        return this.name_;
    },
    set name(name) {
        this.name_ = name;
    },
    sayName() {
        console.log(this.name_);
    }
};
````
简写方法名与可计算属性键相互兼容:
````JS
const methodKey = 'sayName';
let person = {
    [methodKey](name) {
        console.log(name);
    }
};
````
### 对象解构
通过对象解构,能够将对象中的属性绑定到变量上:
````JS
let person = {
    name: 'a',
    age: 18
};
let { name: personName, age: personAge } = person;
console.log(personName);    // a
console.log(personAge);     // 18
````
简写成属性名能够创建一个同名变量:
````JS
let person = {
    name: 'a',
    age: 18
};
let { name, age } = person;
console.log(name);  // a
console.log(age);   // 18
````
解构赋值不一定与对象属性匹配,可以忽略一些属性.如果属性不存在,那么变量就是`undefined`:
````JS
let person = {
    name: 'a',
    age: 18
};
let { name, job } = person;
console.log(name);  // a
console.log(job);   // undefined
````
也可以给解构赋值的同时定义默认值:
````JS
let person = {
    name: 'a',
    age: 18
};
let { name = "b", job = "CS" } = person;
console.log(name);  // a
console.log(job);   // CS
````

解构在内部使用方法`ToObject()`(不能在运行时环境中直接访问)把源数据结构转换为对象.这意味着原始值允许被解构,因为对象解构上下文中,原始值会被当成对象.这也意味着`null`和`undefined`不能被解构,否则会抛出错误.  
例如:
````JS
let { length } = 'foobar';
console.log(length);    // 6
let { constructor: c } = 4;
console.log(c === Number);  // true
let { _ } = null;       // TypeError
let { _ } = undefined;  // TypeError
````

解构并不要求变量必须在解构表达式中声明,但如果是给事先声明的变量赋值,则赋值表达式必须包含在一对括号中:
````JS
let personName, personAge;
let person = {
    name: 'a',
    age: 18
};
({name: personName, age: personAge} = person);
console.log(personName, personAge); // a 18
````

#### 嵌套解构
对于以下例子:
````JS
let person = {
    name: 'a',
    age: 18,
    job: {
        title: 'CS'
    }
};
let personCopy = {};
({
    name: personCopy.name,
    age: personCopy.age,
    job: personCopy.job     // job是一个对象,所以此处personCopy.job和person.job指向同一个内存块
} = person);
person.job.title = 'Hacker';    // 对person.job.title的修改也会影响到personCopy
console.log(person);        // {name: 'a', age: 18, job: {title: 'Hacker'}}
console.log(personCopy);    // {name: 'a', age: 18, job: {title: 'Hacker'}}
````
解构赋值可以使用嵌套结构,以匹配嵌套属性:
````JS
let person = {
    job: {
        title: 'CS'
    }
};
let { job: {title} } = person;
console.log(title); // CS
````
在外层属性没有定义的情况下不能使用嵌套解构,无论是源对象还是目标对象:
````JS
let person = {
    job: {
        title: 'CS'
    }
};
let personCopy = {};
({
    foo: {
        bar: personCopy.bar     // TypeError,原对象上名为foo的外层属性是undefined.
    }
} = person);

({
    job: {
        title: personCopy.job.title // TypeError,目标对象上名为job的外层属性是undefined.
    }
} = person);
````

#### 部分解构
多个属性的解构是一个输出无关的顺序化操作.如果一个解构表达式涉及多个赋值,开始的赋值成功而后面的赋值出错,则整个解构赋值只会完成一部分.

#### 参数上下文匹配
在函数参数列表中也可以进行解构赋值.对参数的解构赋值不会影响`arguments`对象,但可以在函数签名中声明在函数体内使用的局部变量:
````JS
let person = {
    name: 'a',
    age: 18
};
function printPerson(foo, {name: personName, age: personAge}, bar) {
    console.log(arguments);
    console.log(personName, personAge);
}
printPerson(1, person, 2);
// Arguments(3) [1, {name: 'a', age: 18}, 2, callee: (...), Symbol(Symbol.iterator): ƒ]
// a 18
````
也支持简写成属性名(省略冒号和变量名)以作为局部变量名.

## 创建对象
ES5.1并不支持面向对象的结构,但是可以通过巧妙的运用原型式继承模拟相同的行为.

ES6开始正式支持类和继承.ES6的类仅仅是封装了ES5.1构造函数加原型继承的语法糖而已.

### 构造函数
对于普通函数,创建一个对象可以这么写:
````JS
function createPerson(name, age, job) {
    let o = new Object();
    o.name = name;
    o.age = age;
    o.job = job;
    o.sayName = function() {
        console.log(this.name);
    };
    return o;
}
let person1 = createPerson("a", 18, "CS");
let person2 = createPerson("b", 20, "DC");
````
可以使用构造函数的方式写成:
````JS
function Person(name, age, job) {
    this.name = name;
    this.age = age;
    this.job = job;
    this.sayName = function() {
        console.log(this.name);
    };
}
let person1 = new Person("a", 18, "CS");
let person2 = new Person("b", 20, "DC");
````
构造函数与普通函数创建对象有以下区别:
- 没有显式地创建对象.
- 属性和方法直接赋值给了`this`.
- 没有`return`.

按照惯例,构造函数名称的首字母都是要大写的,非构造函数则以小写字母开头.

要创建`Person`的实例,应使用`new`操作符.这种方式调用构造函数会执行如下操作:
1. 在内存中创建一个新对象.
2. 在这个新对象内部的`[[Prototype]]`特性被赋值为构造函数的`prototype`属性.
3. 构造函数内部的`this`被赋值为这个新对象.(即`this`指向新对象).
4. 执行构造函数内部的代码.
5. 如果构造函数返回非空对象,则返回该对象;否则,返回刚创建的新对象.

此外,通过构造函数创建的对象都有一个`constructor`属性指向其构造函数,也会被标识为特定类型:
````JS
console.log(person1.constructor == Person); // true
console.log(person1 instanceof Object);     // true
console.log(person2 instanceof Person);     // true
````

构造函数不一定要写成函数声明的形式.赋值给变量的函数表达式也可以表示构造函数:
````JS
let Person = function(name, age, job) {
    this.name = name;
    this.age = age;
    this.job = job;
    this.sayName = function() {
        console.log(this.name);
    };
}
````

如果没有要传的参数,那么构造函数后面的`()`可加可不加.只要有`new`操作符,就可以调用相应的构造函数:
````JS
let person1 = new Person();
let person2 = new Person;
````

#### 构造函数也是函数
构造函数与普通函数的唯一区别就是调用方式的不同.任何函数只要使用`new`操作符调用,就是构造函数.而不使用`new`操作符调用的函数就是普通函数.  
例如:
````JS
// 作为普通函数调用
Person("a", 18, "CS");
window.sayName();   // "a"

// 在另一个对象的作用域中调用
let o = new Object();
Person.call(o, "b", 20, "DC");
o.sayName();    // "b"
````
注意:没有明确设置`this`值或者没有使用`call()`或`apply()`调用时,`this`始终指向`Global`对象(在浏览器中就是`window`对象).

#### 构造函数的问题
构造函数的问题在于,其定义的方法会在每个实例上都创建一遍.因此对于前面的例子而言,`person1`和`person2`都有名为`sayName()`的方法,但这两个方法不是同一个`Function`实例.  
即逻辑上与下例等价:
````JS
function Person(name, age, job) {
    this.name = name;
    this.age = age;
    this.job = job;
    this.sayName = new Function("console.log(this.name);");
}
````
这将会带来不同实例上的同名方法不相等的问题:
````JS
console.log(person1.sayName == person2.sayName);    // false
````
为了解决这个问题,可以使用原型模式.

### 原型模式
每个函数都会创建一个`prototype`属性,这个属性是一个对象包含特定引用类型的实例共享的属性和方法.`prototype`其实是使用构造函数所创建的对象的原型.  
例如:
````JS
function Person() {}    // let Person = function() {}; 等价
Person.prototype.name = "aaa";
Person.prototype.age = 18;
Person.prototype.job = "CS";
Person.prototype.sayName = function() {
    console.log(this.name);
};
let person1 = new Person();
person1.sayName();  // aaa
let person2 = new Person();
person2.sayName();  // aaa
console.log(person1.sayName == person2.sayName);    // true
````
`prototype`属性是不可枚举的.

#### 原型原理
> **<b class="red_font">`__proto__`属性已被弃用,请使用方法`Object.getPrototypeOf()`代替</b>**

只要创建一个函数,就会按照特定的规则为这个函数创建一个`prototype`属性(指向原型对象).默认情况下,所以原型对象自动获得一个名为`constructor`的属性,指向与之关联的构造函数.对前面的例子而言,`Person.prototype.constructor`指向`Person`.

在自定义构造函数时,原型对象默认只会获得`constructor`属性,其他的所有方法都继承自`Object`.每次调用构造函数创建一个新实例,这个实例内部`[[Prototype]]`指针就会被赋值为构造函数的原型对象.脚本中无访问`[[Prototype]]`特性的标准方式,但`Firefox`,`Safari`,`Chrome`会在每个对象上暴露`__proto__`属性,可通过该属性访问对象的原型.

`[[Prototype]]`保存了对象的继承数据,即对象能够访问其父类方法和静态成员变量就是通过原型访问的.用该方法访问时,无需指出`__proto__`.见[本笔记-原型层级](#原型层级).

例如:
````JS
function Person() {}    // let Person = function() {}; 等价
Person.prototype.name = "aaa";
Person.prototype.age = 18;
Person.prototype.job = "CS";
Person.prototype.sayName = function() {
    console.log(this.name);
};
let person1 = new Person();
let person2 = new Person();

console.log(typeof Person.prototype);   // object
console.log(Person.prototype);
// {
//     age: 18,
//     job: "CS",
//     name: "aaa",
//     sayName: ƒ (),
//     constructor: ƒ Person(),
//     [[Prototype]]: Object
// }
console.log(Person.prototype.constructor === Person);           // true
console.log(Person.prototype.__proto__ === Object.prototype);   // true
console.log(Person.prototype.__proto__.constructor === Object); // true
console.log(Person.prototype.__proto__.__proto__ === null);     // true
console.log(Person.prototype.__proto__);
// {
//     constructor: ƒ Object(),
//     hasOwnProperty: ƒ hasOwnProperty(),
//     isPrototypeOf: ƒ isPrototypeOf(),
//     ...
// }
console.log(person1 !== Person);            // true
console.log(person1 !== Person.prototype);  // true
console.log(Person.prototype !== Person);   // true

console.log(person1.__proto__ === Person.prototype);    // true
console.log(person1.__proto__.constructor === Person);  // true
console.log(person1.__proto__.__proto__ === Person.prototype.__proto__);    // true
console.log(person1.__proto__ === person2.__proto__);   // true
console.log(Person.prototype instanceof Object);        // true

console.log(person1.__proto__);
// {
//     age: 18,
//     job: "CS",
//     name: "aaa",
//     sayName: ƒ (),
//     constructor: ƒ Person(),
//     [[Prototype]]: Object
// }
````
因此,各个对象的之间的关系如下:
- `(Function)Person`:
  - `prototype`: `Person.prototype`
- `(Person)person1`:
  - `[[Prototype]]`: `Person.prototype`
- `(Person)person2`:
  - `[[Prototype]]`: `Person.prototype`
- `(Object)Person.Prototype`:
  - `constructor`: `(Function)Person`
  - `name`: "aaa"
  - `age`: 18
  - `job`: "CS"
  - `sayName`: `(Function)`
  - `[[Prototype]]`: `Object.Prototype`

也可以通过`isPrototypeOf()`方法确定两个对象之间的`[[Prototype]]`关系,即`原型.isPrototypeOf(实例)`返回true.  
使用`Object`的静态方法`Object.getPrototypeOf()`返回参数的内部特性`[[Prototype]]`的值.
例如:
````JS
console.log(Person.prototypr.isPrototypeOf(person1));   // true
console.log(Object.getPrototypeOf(person1) == Person.prototype);    // true
console.log(Obejct.getPrototypeOf(person1).name);   // "aaa"
````

使用静态方法`Object.setPrototypeOf()`可以向实例的私有特性`[[Prototype]]`写入一个新值.由于`[[Prototype]]`包含了类的继承信息,因此可以重写一个对象的原型的继承关系.  
例如:
````JS
let biped = {
    numLegs: 2
};
let person = {
    name: 'aaa'
};
Object.setPrototypeOf(person, biped);
console.log(Object.getPrototypeOf(person) === biped);   // true
console.log(person.numLegs);    // 2
console.log(person);
// {
//     name: "aaa",
//     [[Prototype]]: {
//         numLegs: 2,
//         [[Prototype]]: {
//             constructor: ƒ Object(),
//             ...
//         }
//     }
// }
````
*警告: `Object.setPrototypeOf()`可能会严重影响代码性能.因为该函数会涉及所有访问该`[[Prototype]]`的对象.*

通过使用`Object.create()`静态方法来创建一个新对象并指定原型以避免使用`Object.setPrototypeOf()`:
````JS
let biped = {
    numLegs: 2
};
let person = Object.create(biped);
person.name = 'aaa';
console.log(person.numLegs);    // 2
console.log(Object.getPrototypeOf(person) === biped);   // true
console.log(person);
// {
//     name: "aaa",
//     [[Prototype]]: {
//         numLegs: 2,
//         [[Prototype]]: {
//             constructor: ƒ Object(),
//             ...
//         }
//     }
// }
````

#### 原型层级
在通过对象访问属性时,会按照这个属性的名字开始搜索,搜索开始于对象实例本身.如果在这个实例上发现了给定的名称,则返回该名称对应的值.如果没有,则搜索会沿着`[[Prototype]]`进入原型对象,并在原型对象上搜索.

当实例上添加了一个与原型对象中同名的属性,则会在实例上创建这个属性,这个属性会遮住原型对象上的属性,而不会修改原型内的属性.  
例如:
````JS
function Person() {}
Person.prototype.name = "aaa";
let person1 = new Person();
let person2 = new Person();
person1.name = "bbb";
console.log(person1.name);  // "bbb", 来自实例
console.log(person2.name);  // "aaa", 来自原型
delete person1.name;
console.log(person1.name);  // "aaa", 来自原型
````

`hasOwnProperty()`方法用于确定某个属性是在实例上还是在原型对象(是否是自有属性,即非静态成员)上.这个方法继承自`Object`,会在属性存在于调用它的对象实例上时返回`true`.  
例如:
````JS
function Person() {}
Person.prototype.name = "aaa";
let person = new Person();
console.log(person.hasOwnProperty("name")); // false
person.name = "bbb";
console.log(person.hasOwnProperty("name")); // true
````

#### 原型和in操作符
单独使用`in`操作符可以判断对象是否拥有指定属性,无论属性在原型上,还是在实例上.

例如:
````JS
function Person() {}
Person.prototype.name = "aaa";
let person = new Person();
console.log("name" in person);  // true
person.name = "bbb";
console.log("name" in person);  // true
console.log("age" in person);   // false
````

`for-in`循环能够访问所有可枚举的属性的键,包括原型中的和实例中的.  
例如:
````JS
function Person() {
    Object.defineProperty(this, "name", {value:"bbb", enumerable: true});   // 可枚举的name
    this.nameLength = 3;    // 该语句不会创建一个nameLength,具体细节详见下文链接
    this.other = 0; // 可枚举
}
Object.defineProperty(Person.prototype, "name", { value: "aaa" });      // 不可枚举
Object.defineProperty(Person.prototype, "age", { value: 18 });          // 不可枚举
Object.defineProperty(Person.prototype, "nameLength", { value: 3 });    // 不可枚举
Person.prototype.job = "CS";    // 可枚举
let p = new Person();
for (keys in p) {
    console.log(keys);
}
// name
// other
// job
````
关于上面`nameLength`实例属性不会创建的问题,详见[本笔记-原生属性覆盖问题](#原生属性覆盖问题).

如果只想获取实例的可枚举属性的键,可以使用静态方法`Object.keys()`:
````JS
function Person() {
    Object.defineProperty(this, "name", {value:"bbb", enumerable: true});
    this.nameLength = 3;
    this.other = 0;
}
Object.defineProperty(Person.prototype, "name", { value: "aaa" });
Object.defineProperty(Person.prototype, "age", { value: 18 });
Object.defineProperty(Person.prototype, "nameLength", { value: 3 });
Person.prototype.job = "CS";
let p = new Person();
let keys = Object.keys(p);
console.log(keys);  // ['name', 'other']
````
使用静态方法`Object.getOwnPropertyNames()`获取所有实例属性,无论是否是可枚举的.
````JS
function Person() {
    Object.defineProperty(this, "name", {value:"bbb", enumerable: true});
    Object.defineProperty(this, "add", {value:"bbb", enumerable: false});
    this.nameLength = 3;    // 该实例属性是不存在的
    this.other = 0;
}
Object.defineProperty(Person.prototype, "name", { value: "aaa" });
Object.defineProperty(Person.prototype, "age", { value: 18 });
Object.defineProperty(Person.prototype, "nameLength", { value: 3 });
Person.prototype.job = "CS";
let p = new Person();
let keys = Object.getOwnPropertyNames(p);
console.log(keys);  // ['name', 'add', 'other']
````
使用静态方法`Object.getOwnPropertySymbols()`获取所有实例符号.
````JS
let k1 = Symbol('k1'),
    k2 = Symbol('k2');
let o = {
    [k1]: 'k1',
    [k2]: 'k2',
    name: 1
};
console.log(Object.getOwnPropertyNames(o));     // ['name']
console.log(Object.getOwnPropertySymbols(o));   // [Symbol(k1), Symbol(k2)]
````
#### 属性枚举顺序
`for-in`和`Object.keys()`的枚举顺序是不确定的,取决于JS引擎.`Object.getOwnPropertyNames()`,`Object.getOwnPropertySymbols()`和`Object.assign()`的枚举顺序是确定性的.先以升序枚举数值键,然后以插入顺序枚举字符串和符号键.在对象字面量中定义的键以它们逗号分隔的顺序插入.

例如:
````JS
let k1 = Symbol('k1'),
    k2 = Symbol('k2');
let o = {
    1: 1,
    first: 'first',
    [k1]: 'sym1',
    second: 'second',
    0: 0
};
o[k2] = 'sym2';
o[3] = 3;
o.third = 'third';
o[2.5] = 2; // 2.5被认为是字符串,即使定义在对象中
console.log(Object.getOwnPropertyNames(o));
// ["0", "1", "3", "first", "second", "third", "2.5"]
console.log(Object.getOwnPropertySymbols(o));
// [Symbol(k1), Symbol(k2)]
````

### 对象迭代
静态方法`Object.values()`和`Object.entries()`接收一个对象,返回它们内容的数组.`Object.values()`返回对象值的数组,`Object.entrie()`返回键值对的数组.

例如:
````JS
const o = {
    foo: 'bar',
    baz: 1,
    qux: {}
};
console.log(Object.values(o));
// ["bar", 1, {}]
console.log(Object.entries(o));
// [["foo", "bar"], ["baz", 1], ["qux", {}]]
````
注意,非字符串属性会被转换为字符串输出.另外,这两个方法执行对象的浅复制:
````JS
const o = {
    qux: {}
};
console.log(Object.values(o)[0] === o.qux);     // true
console.log(Object.entries(o)[0][1] === q.qux); // true
````
符号属性会被忽略:
````JS
const sym = Symbol();
const o = {
    [sym]: 'foo'
};
console.log(Object.values(o));  // []
console.log(Obkect.entries(o)); // []
````
#### 其他原型语法
为了减少代码的冗余,可以直接通过一个包含所有属性和方法的对象字面量来重写原型.
````JS
function Person() {}
Person.prototype = {
    name: "aaa",
    age: 18,
    job: "CS",
    sayName() {
        console.log(this.name);
    }
};
let p = new Person();
console.log(p);
// {
//     [[Prototype]]: {
//         age: 18,
//         job: "CS",
//         name: "aaa",
//         sayName: f sayName(),
//         [[Prototype]]: {
//             constructor: f Object,
//             ...
//         }
//     }
// }
````
上述例子的结果与分别使用`Person.prototype`设置属性结果相似,但是,虽然原型中自动补全了其`[[Prototype]]`为`Object`,但却没有补齐构造函数`constructor`.因此:
````JS
let p = new Person();
console.log(friend instanceof Person);  // true
console.log(friend instanceof Person);  // false
console.log(friend instanceof Object);  // true
````
如果构造函数`constructor`的值很重要,则需要在专门设置它的值:
````JS
function Person() {}
Person.prototype = {
    name: "aaa",
    age: 18,
    job: "CS",
    sayName() {
        console.log(this.name);
    }
};
Object.defineProperty(Person.prototype, "constructor", {
    enumerable: false,  // constructor属性是不可枚举的
    value: Person
})
````
#### 原型的动态性
因为从原型上搜索值的过程是动态的,所以任何时候对原型所做的修改也会在实例上反映出来:
````JS
let friend = new Person();  // 先创建对象
Person.prototype.sayHi = function() {   // 后修改原型
    console.log("Hi");
};
friend.sayHi(); // "Hi", 没问题
````
但修改整个原型,实际上是修改原型的引用,由于原型的引用是构造函数赋值的,因此并不会导致先前创建的对象的原型的指针发生修改.
````JS
function Person() {}
let p = new Person();
Person.prototype = {
    sayHi() {
        console.log("Hi");
    }
};
p.sayHi();  // TypeError
````
#### 原生对象原型
所有原生引用类型(例如`Object`,`Array`,`String`)都在原型上定义了实例方法.比如,数组实例的`sort()`方法就是`Array.prototype`上定义的.

通过原生原型的原型可以取得所有默认方法的引用,也可以给原生类型的实例定义新的方法.例如:
````JS
String.prototype.sayHi = function(text) {
    console.log("Hi");
}
let str = "";
str.sayHi();    // Hi
````
*不推荐修改原生对象原型,推荐的做法是创建一个自定义的类,继承原生类型.*

#### 原生属性覆盖问题
原生属性通常可以被对象属性通过赋值同名属性的方式所覆盖
````JS
function Person() {
    this.name = "aaa";
}
Person.prototype.name = "bbb";
let p = Person();
console.log(p.name);
````
但当原生属性的`writable`是`false`时,尝试通过赋值的同名实例属性的手段对原生属性的覆盖会被忽略:
````JS
function Person() {
    this.name = "aaa";
}
Object.defineProperty(Person.prototype, "name", {
    value: "bbb",
    writable: false,
    configurable: true,
    enumerable: true
})
let p = new Person();
console.log(p.name);    // bbb
````
上例中,不存在实例属性`name`,只存在原生属性`prototype.name`.

覆盖原生属性的实例属性不会继承原生属性的特性(属性描述符):
````JS
function Person() {
    this.name = "aaa";
}
Object.defineProperty(Person.prototype, "name", {
    value: "bbb",
    writable: true,
    configurable: false,
    enumerable: false
})
let p = new Person();
console.log(p.name);    // aaa
console.log(Object.getOwnPropertyDescriptor(p, "name"));
// {value: 'aaa', writable: true, enumerable: true, configurable: true}
console.log(Object.getOwnPropertyDescriptor(Object.getPrototypeOf(p), "name"));
// {value: 'bbb', writable: true, enumerable: false, configurable: false}
````

## 继承
ES中无法做到接口继承,但是可以做到实现继承.

### 原型链
ES中主要继承方式为原型链,其基本思想就是通过原型继承多个引用类型的属性和方法.  
例如:
````JS
function ParentType() {
    this.property = true;
}

ParentType.prototype.getSuperValue = function() {
    return this.property;
};

function ChildType() {
    this.subProperty = false;
}

ChildType.prototype = new ParentType();

ChildType.prototype.getSubValue = function() {
    return this.subProperty;
}

let instance = new ChildType();
console.log(instance.getSuperValue());  // true
console.log(instance);
// {
//     subProperty: false;
//     [[Prototype]]: {
//         getSubValue: f(),
//         property: true,
//         [[Prototype]]: {
//             getSuperValue: f(),
//             constructor: f ParentType(),
//             [[Prototype]]: {
//                 constructor: f Object();
//             }
//         }
//     }
// }
````
上述关系为:
- `ParentType`:
  - `prototype`: `ParentType.prototype`
- `ChildType`:
  - `prototype`: `ChildType.prototype`
- `ParentType.prototype`:
  - `constructor`: `ParentType`
  - `getSuperValue`: `Function`
  - `[[Prototype]]`: `Object`
- `ChildType.prototype`:
  - `property`: true
  - `getSubValue`: `Function`
  - `[[Prototype]]`: `ParentType.prototype`
- `instance`:
  - `[[Prototype]]`: `ChildType.prototype`
  - `subProperty`: false

注意,`ChildType.prototype`的`constructor`属性被重写为指向`ParentType`,所以`instance.constuctor`也指向`SuperType`.

在搜索`instance.getSuperValue()`时,会搜索`instance`,`ChildType.prototype`,`ParentType.prototype`.对属性和方法的搜索会沿着原型链一直持续到原型链末端.

#### 默认原型
默认情况下,所以引用类型都继承自`Object`,这也是通过原型链实现的.任何函数的默认原型都是一个`Object`的实例,这个实例有一个内部指针指向`Object.prototype`.因此自定义类型能够继承`toString()`,`valueOf()`等方法.

#### 原型与继承关系
使用`instanceof`操作符在原型链中出现对应引用类型时返回`true`:
````JS
console.log(instance instanceof Object);        // true
console.log(instance instanceof ParentType);    // true
console.log(instance instanceof ChildType);     // true
````

使用`isPrototypeOf()`方法,只要原型当中包含该原型,这个方法就返回`true`:
````JS
console.log(Object.prototype.isPrototypeOf(instance));      // true
console.log(ParentType.prototype.isPrototypeOf(instance));  // true
console.log(ChildType.prototype.isPrototypeOf(instance));   // true
````

#### 关于方法
子类有时需要覆盖父类方法,或者增加父类没有的方法.为此,这些方法必须在原型赋值之后再添加到原型上:
````JS
function ParentType() {
    this.property = true;
}

ParentType.prototype.getSuperValue = function() {
    return this.property;
};

function ChildType() {
    this.subProperty = false;
}
// 继承
ChildType.prototype = new ParentType();
// 新方法,需要在继承之后定义
ChildType.prototype.getSubValue = function() {
    return this.subProperty;
}
// 覆盖已有方法,需要在继承之后定义
ChildType.prototype.getSuperValue = function() {
    return false;
}
let instance = new ChildType();
console.log(instance.getSuperValue());  // false
````

以字面量的形式创建原型方法会破坏之前的原型链,因为这相当于重写了原型链:
````JS
function ParentType() {
    this.property = true;
}
ParentType.prototype.getSuperValue = function() {
    return this.property;
};
function ChildType() {
    this.subProperty = false;
}
// 继承
ChildType.prototype = new ParentType();
// 通过对象字面量添加新方法,这会导致上一行无效
ChildType.prototype = {
    getSubValue() {
        return this.subProperty;
    }
};
````

#### 原型链的问题
由于父类的实例属性成为了子类的原型属性,因此属性会在各子类实例之间共享:
````JS
function ParentType() {
    this.property = true;
}
ParentType.prototype.getSuperValue = function() {
    return this.property;
};
function ChildType() {
    this.subProperty = false;
}
ChildType.prototype = new ParentType();
ChildType.prototype.getSubValue = function() {
    return this.subProperty;
}
let instance = new ChildType();
let i2 = new ChildType();
console.log(instance.getSuperValue());  // true
// instance.property = false;会导致创建一个新的property实例属性覆盖原来的原型属性,结果是instance.getSuperValue()为false,而i2.getSuperValue()为true
Object.getPrototypeOf(instance).property = false;
console.log(i2.getSuperValue());    // false
````
此外,原型链的另一个问题是,子类型在实例化时不能给父类的构造函数传参.**因此,原型链基本上不会使用.**

### 盗用构造函数
类似于C++中的委托构造.

盗用构造函数的思路是:在子类构造函数中调用父类构造函数:
````JS
function SuperType() {
    this.colors = ["red", "blue", "green"];
}
function SubType() {
    // 继承SuperType
    SuperType.call(this);
}
let i1 = new SubType();
let i2 = new SubType();
i1.colors.push("black");
console.log(i1.colors); // ['red', 'blue', 'green', 'black']
console.log(i2.colors); // ['red', 'blue', 'green']
console.log(i1);
// {
//     colors: ['red', 'blue', 'green', 'black'],
//     [[Prototype]]: {
//         constructor: ƒ SubType(),
//         [[Prototype]]: {
//             constructor: ƒ Object(),
//             ...
//         }
//     }
// }
````
通过使用`call()`(或`apply()`)方法,`SuperType`构造函数在位`SubType`实例创建的新对象的上下文中执行了.这相当于新的`SubType`对象上运行了`SuperType()`函数中的所有初始化代码.结果就是每个实例都会有自己的`colors`属性.

`call()`是函数的一个方法,例如上例中,`call()`指的是`constructor: ƒ SuperType()`中的方法.

`Function.prototype.call()`:  
`Function`实例的`call()`方法会以给定的`this值`和逐个提供的参数调用该函数.

参数:
- `thisArg`:在调用`func`时要使用的`this`值.如果函数不在严格模式下,`null`和`undefined`将被替换为全局对象,并且原始值将被转换为对象.
- `arg1, …, argN`:可选,函数的参数.

返回值:
- 使用指定的`this`值和参数调用函数后的结果.

备注:这个函数几乎与`apply()`相同,只是函数的参数以列表的形式逐个传递给`call()`,而在`apply()`中它们被组合在一个对象中,通常是一个数组.例如,`func.call(this, "eat", "bananas")`与`func.apply(this, ["eat", "bananas"])`.

#### 传递参数
相比原型链,盗用构造函数可以在子类构造函数中向父类构造函数传参:
````JS
function SuperType(name) {
    this.name = name;
}
function SubType(name, age) {
    this.age = age;
    SuperType.call(this);
}
let i = new SubType("aaa", 18);
console.log(i.name);    // aaa
console.log(i.age);     // 18
````

#### 盗用构造函数的问题
盗用构造函数的主要缺点是不能获得父类中原型的属性和类方法,因为父类的原型属性和类方法不会在其构造函数中定义.

### 组合继承
组合继承(伪经典继承)综合了原型链和盗用构造函数.基本思路是使用原型链继承原型上的属性和方法,而通过盗用构造函数继承实例属性:
````JS
function SuperType(name) {
    this.name = name;
    this.colors = ["red", "blue", "green"];
}
SuperType.prototype.sayName = function() {
    console.log(this.name);
};
function SubType(name, age) {
    // 继承属性
    SuperType.call(this, name);
    this.age = age;
}
// 继承方法
SubType.prototype = new SuperType();
SubType.prototype.sayAge = function() {
    console.log(this.age);
};
let i1 = new SubType("aaa", 18);
i1.colors.push("black");
console.log(i1.colors); // ['red', 'blue', 'green', 'black']
i1.sayName();   // aaa
i1.sayAge();    // 18

let i2 = new SubType("bbb", 20);
console.log(i2.colors); // ['red', 'blue', 'green']
i2.sayName();   // bbb
i2.sayAge();    // 20

console.log(i1);
// {
//     age: 18,
//     colors: ['red', 'blue', 'green', 'black'],
//     name: "aaa",
//     [[Prototype]]: {
//         colors: ['red', 'blue', 'green'],
//         name: undefined,
//         sayAge: ƒ (),
//         [[Prototype]]: {
//             sayName: ƒ (),
//             constructor: ƒ SuperType(name),
//             [[Prototype]]: {
//                 constructor: ƒ Object(),
//                 ...
//             }
//         }
//     }
// }
````
该方法中实例属性将原型属性覆盖,因此无法直接访问到原型属性,就好像继承类对象中只有实例属性一样.

### 原型式继承
`《JavaScript中的原型式继承》`给出了一个函数:
````JS
function object(o) {
    function F() {}
    F.prototype = o;
    return new F();
}
````
`object()`函数会创建一个临时构造函数,将传入的对象赋值给这个构造函数的原型,然后返回这个临时类型的一个实例.本质上,`object()`是对传入的对象执行了一次浅复制:
````JS
function object(o) {
    function F() {}
    F.prototype = o;
    return new F();
}
let person = {
    name: "aaa",
    friends: ["bbb", "ccc"]
};
let anotherPerson = object(person);
anotherPerson.name = "fff";
anotherPerson.friends.push("ddd");
let yetAnotherPerson = object(person);
yetAnotherPerson.name = "hhh";
yetAnotherPerson.friends.push("ggg");
console.log(person.friends);    // ['bbb', 'ccc', 'ddd', 'ggg']
````

ES5中增加了`Object.create()`方法将原型式继承的概念规范化了.对于`Object.create()`如果只传入一个参数(作为新对象原型的对象),则效果与上面的`object()`函数效果相同.第二个参数(可选)表示给新对象定义的额外属性组成的对象.  
例如:
````JS
let person = {
    name: "aaa",
    friends: ["bbb", "ccc"]
};
let anotherPerson = Object.create(person, {
    name: {     // 必须以这种格式
        value: "ddd"
    }
});
console.log(anotherPerson.name);    // ddd
````
这种继承方式适合不需要单独创建构造函数,但需要在对象间共享信息的场合.*注意:被继承属性位于原型当中,是被共享的.*

### 寄生式继承
寄生式继承与原型式继承比较接近.基本思路是创建一个实现继承的函数,以某种方式增强对象,然后返回这个对象:
````JS
function createAnother(origin) {
    let clone = Object.create(origin);    // Object.create不是必要的,只要返回对象的函数都可以使用,返回的对象即为要继承的对象
    clone.sayHi = function() {
        console.log("hi");
    };
    return clone;
}
let person = {
    name: "aaa",
    friends: ["bbb", "ccc"]
};
let anotherPerson = createAnother(person);
anotherPerson.sayHi();  // Hi
````
这种继承方式适合不需要单独创建构造函数的场合.*注意:新创建的函数是无法重用的.*

### 寄生式组合继承
为了解决组合继承中,继承类的原型和实例中重复包含父类的实例属性的问题,可以通过寄生式继承的方式仅继承父类的原型属性,而使用盗用构造函数的方式继承父类的实例属性.  
例如:
````JS
function inheritPrototype(subType, superType) {
    let prototype = Object.create(superType.prototype); // 创建对象
    prototype.constructor = subType;                    // 增强对象,也可以用设置属性的方式,因为构造函数是不可枚举的属性
    subType.prototype = prototype;                      // 赋值对象
}
function SuperType(name) {
    this.name = name;
    this.colors = ['red', 'blue', 'green'];
}
SuperType.prototype.sayName = function() {
    console.log(this.name);
}
function SubType(name, age) {
    SuperType.call(this, name);
    this.age = age;
}
inheritPrototype(SubType, SuperType);   // 继承
SubType.prototype.sayAge = function() {
    console.log(this.age);
};
let i = new SubType("aaa", 18);
console.log(i);
// {
//     age: 18,
//     colors: ['red', 'blue', 'green'],
//     name: "aaa",
//     [[Prototype]]: {
//         constructor: ƒ SubType(name, age),
//         sayAge: ƒ (),
//         [[Prototype]]: {
//             constructor: ƒ SuperType(name),
//             sayName: ƒ (),
//             [[Prototype]]: {
//                 constructor: ƒ Object(),
//                 ...
//             }
//         }
//     }
// }
````
这个方法避免了`SubType.prototype`的冗余.此外`instanceof`操作符和`isPrototypeOf()`方法正常有效.寄生式组合继承是引用类型继承的最佳模式.

## 类
ES6加入的`class`关键字具有正式定义类的能力.类其实是前面所提及的原型和构造函数的语法糖,背后仍使用原型和构造函数的概念.
### 类定义
定义类有两种方式:`类声明`和`类表达式`.
````JS
// 类声明
class Person {}

// 类表达式
const Animal = {}
````
与函数表达式类似,类表达式在它们被求值前不能被引用.不过,与函数定义不同的是,函数声明可以提升,但类定义不能:
````JS
console.log(FuncExpr);  // undefined
var FuncExpr = function() {};
console.log(FuncExpr);  // function() {}

console.log(FuncDecl);  // FuncDecl() {}
function FuncDecl() {}
console.log(FuncDecl);  // FuncDecl() {}

console.log(ClassExpr); // undefined
var ClassExpr = class {};
console.log(ClassExpr); // class {}

console.log(ClassDecl); // ReferenceError: ClassDecl is not defined
class ClassDecl {}
console.log(ClassDecl); // class ClassDecl {}
````
此外,函数受函数作用域限制,而类受块作用域限制:
````JS
{
    function FuncDecl() {}
    class ClassDecl {}
}
console.log(FuncDecl);  // FuncDecl() {}
console.log(ClassDecl); // ReferenceError
````
类可以包含构造函数,实例方法,获取函数,设置函数和静态类方法,但这些都不是必须的.默认情况下,类定义中的代码都在严格模式下执行.

多数编程风格都建议类名的首字母要大写,以区别于通过它创建的实例:
````JS
// 空类定义,有效
class Foo {}

class Bar {
    // 构造函数
    constructor() {}

    // 获取函数
    get Baz() {}

    // 静态方法
    static Qux() {}
}
````
类表达式的名称是可选的.把类表达式赋值给变量后,可以通过`name`属性获取类表达式的名称的字符串.但不能在类外部访问该名称:
````JS
let Person = class PersonName {
    sayInfo() {
        console.log(Person.name, PersonName.name);  // OK
    }
}
let p = new Person();
p.sayInfo();    // PersonName PersonName
console.log(Person.name);   // PersonName
console.log(PersonName);    // ReferenceError
````

### 类构造函数
`constructor`关键字用于在类定义块内部创建类的构造函数.在使用`new`操作符创建类的新实例时,会调用该函数.构造函数不是必须的,无构造函数相当于无参数的空构造.

#### 实例化
使用`new`调用类的构造函数会执行如下操作:
1. 在内存中创建一个新对象.
2. 这个新对象内部的`[[Prototype]]`指针被赋值为构造函数的`prototype`属性.
3. 构造函数内部的`this`被赋值为这个新对象(即`this`指向新对象).
4. 执行构造函数内部的代码.
5. 如果构造函数返回非空对象,则返回该对象;否则,返回刚创建的新对象.

类实例化时传入的参数会用作构造函数的参数.如果不需要参数,则类名后面的括号也是可选的.

如果返回的对象不是构造函数中的`this`,则如果对象的原型指针没有被修改,`instanceof`操作符就不会检测出跟类有关联.

调用类构造函数时如果忘了使用`new`则会抛出错误:
````JS
function Person() {}
class Animal {}
let p = Person();   // 把全局对象(通常是window)作为内部对象
let a = Animal();   // TypeError: class constructor Animal cannot be invoked without 'new'
````
类构造函数就是普通的函数,可以被实例化:
````JS
class Person {}
let f = new Person.constructor();
console.log(f);     // ƒ anonymous() {}
let p = new f();
console.log(p);     // {}
````
#### 把类当成特殊函数
ES中类就是一种特殊函数.声明一个类之后,通过`typeof`操作符检测类标识符,表明它是一个函数:
````JS
class Person {}
console.log(Person);        // class Person {}
console.log(typeof Person); // function
````
类标识符有`prototype`属性,而这个原型也有一个`constructor`属性指向类自身:
````JS
class Person {}
console.log(Person.prototype);                          // { constructor: f() }
console.log(Person === Person.prototype.constructor);   // true
````
可以使用`instanceof`操作符检测构造函数原型是否存在于实例的原型链中:
````JS
class Person {}
let p = new Person();
console.log(p instanceof Person);   // true
````
类定义中的`constructor`方法不会被当作构造函数,对它使用`instanceof`操作符时会返回`false`.如果在创建实例时直接将类构造函数当成普通函数使用,那么`instanceof`操作符的返回值会反转:
````JS
class Person {}
let p1 = new Person();
console.log(p1.constructor === Person);         // true
console.log(p1 instanceof Person);              // true
console.log(p1 instanceof Person.constructor);  // false
console.log(p1);
// {
//     [[Prototype]]: {
//         constructor: class Person,
//         [[Prototype]]: {
//             constructor: ƒ Object(),
//             ...
//         }
//     }
// }
let p2 = new Person.constructor();
console.log(p2.constructor === Person);         // false
console.log(p2 instanceof Person);              // false
console.log(p2 instanceof Person.constructor);  // true
console.log(p2);
// ƒ anonymous() {}
````
类可以像其他对象或函数引用一样把类作为参数传递:
````JS
let classList = [
    class {
        constructor(id) {
            this.id_ = id;
            console.log(`instance ${this.id_}`);
        }
    }
];
function createInstance(classDef, id) {
    return new classDef(id);
}
let foo = createInstance(classList[0], 3141);   // instance 3141
````
与立即调用表达式类似,类也可以立即实例化,但此时类就无法再次实例化:
````JS
let p = new class Foo {
    constructor(x) {
        console.log(x);
    }
}('bar');
console.log(p); // Foo {}
let q = new Foo('baz'); // ReferenceError
````

### 实例,原型和类成员
#### 实例成员
每次通过`new`调用类标识符时,都会执行类构造函数.在这个构造函数内部,可以为新创建的实例(`this`)添加`自有属性`(实例属性).在构造函数执行完毕后,仍然可以给实例动态添加新成员.

每个实例的成员对象都是唯一且不共享的:
````JS
class Person {
    constructor() {
        this.name = new String('aaa');
        this.sayName = () => console.log(this.name);
        this.nicknames = ['bbb', 'ccc'];
    }
}
let p1 = new Person(),
    p2 = new Person();
p1.sayName();   // aaa
p2.sayName();   // aaa
console.log(p1.name === p2.name);           // false
console.log(p1.sayName === p2.sayName);     // false
console.log(p1.nicknames === p2.nicknames); // false
````

#### 原型方法与访问器
为了在实例间共享方法,类方法语法把在类块中定义的方法作为原型方法:
````JS
class Person {
    constructor() {
        // 添加到实例上
        this.locate = () => console.log('instance');
    }
    // 在类块中定义的所有内容都会定义在类的原型上
    locate() {
        console.log('prototype');
    }
}
let p = new Person();
p.locate();                 // instance
Person.prototype.locate();  // prototype
````
可以把方法定义在类构造函数中或者类块中,但不能在类块中给原型添加原始值或对象作为成员数据:
````JS
class Person {
    name: 'aaa'
}
// Uncaught SyntaxError: Unexpected token
class Animal {
    name = 'aaa';   // 实例属性name的值为'aaa'
}
````
类方法等同于对象属性,因此可以使用字符串,符号,或计算的值作为键:
````JS
const symbolKey = Symbol('symbolKey');
class Person {
    stringKey() {
        console.log('invoke stringKey');
    }
    [symbolKey]() {
        console.log('invoke symbolKey');
    }
    ['computed' + 'Key']() {
        console.log('invoke computedKey');
    }
}
let  p = new Person();
p.stringKey();      // invoked stringKey
p[symbolKey]();     // invoked symbolKey
p.computedKey();    // invoked computedKey
````
类定义也支持获取和设置访问器.语法与行为跟普通对象一样:
````JS
class Person {
    set name(newName) {
        this.name_ = newName;
    }
    get name() {
        return this.name_;
    }
}
let p = new Person();
p.name = 'aaa';
console.log(p.name);    // aaa
````
#### 静态类方法
可以在类上定义静态方法.这些方法通常用于执行不特定于实例的操作,也不要求存在类的实例.与原型成员类似,静态成员每个类上只能有一个.静态类成员在类定义中使用`static`关键字作为前缀.在静态成员中,`this`引用类自身.其他所有约定与原型成员一样:
````JS
class Person {
    constructor() {
        // 定义在实例上
        this.locate = () => console.log('instance', this);
    }
    // 定义在原型上
    locate() {
        console.log('prototype', this);
    }
    // 定义在类本身上
    static locate() {
        console.log('class', this);
    }
}
let p = new Person();
p.locate(); // instance, Person {Locate: ƒ}
Person.prototype.locate();  // prototype {Locate: ƒ}
Person.locate();    // class class Person { ... }
console.log(p);
// Person {
//     locate: () => console.log('instance', this),
//     [[Prototype]]: {
//         constructor: class Person,
//         locate: ƒ locate(),
//         [[Prototype]]: {
//             constructor: ƒ Object(),
//             ...
//         }
//     }
// }
console.log(Person);
// class Person { ... } 类定义本身
````
#### 非函数原型和类成员
虽然类定义并不显式支持在原型或类上添加数据成员,但在类定义外部,可以手动添加:
````JS
class Person {
    sayName() {
        console.log(`${Person.greeting} ${this.name}`);
    }
}
// 在类上定义数据成员
Person.greeting = 'My name is';
// 在原型上定义数据成员
Person.prototype.name = 'aaa';

let p = new Person();
p.sayName();
````
*注:之所以没有显式支持添加数据成员,是因为共享可变数据成员是一种反模式.*

#### 迭代器和生成器方法
类定义语法支持在原型和类本身上定义生成器方法:
````JS
class Person {
    // 在原型上定义生成器方法
    *createNicknameIterator() {
        yield 'Jack';
        yield 'Jake';
        yield 'J-Dog';
    }

    // 在类上定义生成器方法
    static *createJobIterator() {
        yield 'Butcher';
        yield 'Baker';
        yield 'Candlestick maker';
    }
}
let jobIter = Person.createJobIterator();
console.log(jobIter.next().value);  // Butcher
console.log(jobIter.next().value);  // Baker
console.log(jobIter.next().value);  // Candlestick maker

let p = new Person();
let nicknameIter = p.createNicknameIterator();
console.log(nicknameIter.next().value); // Jack
console.log(nicknameIter.next().value); // Jake
console.log(nicknameIter.next().value); // J-Dog
````
可以通过添加一个默认的迭代器,把类实例变成可迭代对象:
````JS
class Person {
    constructor() {
        this.nicknames = ['Jack', 'Jake', 'J-Dog'];
    }

    *[Symbol.iterator]() {
        yield *this.nicknames.entries();
    }
}

let p = new Person();
for (let [idx, nickname] of p) {
    console.log(nickname);
}
// Jack
// Jake
// J-Dog
````
也可以只返回迭代器实例:
````JS
class Person {
    constructor() {
        this.nicknames = ['Jack', 'Jake', 'J-Dog'];
    }

    [Symbol.iterator]() {
        yield this.nicknames.entries();
    }
}

let p = new Person();
for (let [idx, nickname] of p) {
    console.log(nickname);
}
// Jack
// Jake
// J-Dog
````

### 继承
继承背后仍旧使用的是原型链.

#### 继承
ES6的类支持单继承.使用`extends`关键字,就可以继承任何拥有`[[Construct]]`和原型的对象.很大程度上,这意味着不仅可以继承一个类,也可以继承普通的构造函数(保持向后兼容):
````JS
class Vehicle {}
class Bus extends Vehicle {}        // 继承类
let b = new Bus();
console.log(b instanceof Bus);      // true
console.log(b instanceof Vehicle);  // true

function Person() {}
class Engineer extends Person {}    // 继承普通构造函数
let e = new Engineer();
console.log(e instanceof Engineer); // true
console.log(e instanceof Person);   // true
````
表达式继承也是合法的:
````JS
let Bar = class extends Foo {}
````
派生类都会通过原型链访问到类和原型上定义的方法.`this`的值会反映调用对应方法的实例或者类:
````JS
class Vehicle {
    identifyPrototype(id) {
        console.log(id, this);
    }
    static identifyClass(id) {
        console.log(id, this);
    }
}
class Bus extends Vehicle {}
let v = new Vehicle();
let b = new Bus();
b.identifyPrototype('bus'); // bus, Bus {}
v.identifyPrototype('vehicle'); // vehicle, Vehicle {}
Bus.identifyClass('bus');   // bus, class Bus {}
Vehicle.identifyClass('vehicle');   // vehicle, class Vehicle {}
````

#### 构造函数, HomeObject和super()
派生类的方法可以通过`super`关键字引用它们的原型.这个关键字只能在派生类中使用,而且仅限于类构造函数,实例方法和静态方法内部.在类构造函数中使用`super`可以调用父类构造函数.
````JS
class Vehicle {
    constructor() {
        this.hasEngine = true;
    }
}
class Bus extends Vehicle {
    constructor() {
        // 不要在调用super()之前引用this,否则会抛出ReferenceError
        super();    // 相当于super.constructor()
        console.log(this instanceof Vehicle);   // true
        console.log(this);                      // Bus { hasEngine: true }
    }
}
new Bus();
````
在静态方法中可以通过`super`调用继承的类上定义的静态方法:
````JS
class Vehicle {
    static identify() {
        console.log('vehicle');
    }
}
class Bus extends Vehicle {
    static identify() {
        super.identify();
    }
}
Bus.identify(); // vehicle
````
ES6给类构造函数和静态方法添加了内部特性`[[HomeObject]]`,这个特性是一个指针,指向定义该方法的对象.这个指针是自动赋值的,而且只能在JS引擎内部访问.`super`始终会定义为`[[HomeObject]]`的原型.

在使用`super`时要注意:
- `super`只能在派生类构造函数和静态方法中使用:
````JS
class Vehicle {
    constructor() {
        super();    // SyntaxError: 'super' keyword unexpected
    }
}
````
- 不能单独引用`super`关键字,要么用它调用构造函数,要么用它引用静态方法:
````JS
class Vehicle {}
class Bus extends Vehicle {
    constructor() {
        console.log(super); // SyntaxError: 'super' keyword unexpected here
    }
}
````
- 调用`super()`会调用父类构造函数,并将返回的实例赋值给`this`.
````JS
class Vehicle {}
class Bus extends Vehicle {
    constructor() {
        super();
        console.log(this instanceof Vehicle);
    }
}
new Bus();  // true
````
- `super()`的行为如同调用构造函数,如果需要给父类构造函数传参,则需要手动传入.
- 如果没有定义类构造函数,在实例化派生类时会调用`super()`,而且会传入所有传给派生类的参数:
````JS
class Vehicle {
    constructor(a) {
        this.a = a;
    }
}
class Bus extends Vehicle {}
console.log(new Bus(123));  // Bus { a: 123 }
````
- 在类构造函数中,不能在调用`super()`之前引用`this`.
- 如果在派生类中显式定义了构造函数,则要么必须在其中调用`super()`,要么必须在其中返回一个对象:
````JS
class Vehicle {}
class Car extends Vehicle {}
class Bus extends Vehicle {
    constructor() {
        super();
    }
}
class Van extends Vehicle {
    constructor() {
        return {};
    }
}
console.log(new Car()); // Car {}
console.log(new Bus()); // Bus {}
console.log(new Van()); // {}
````

#### 抽象基类
抽象基类可供其他类继承,但本身不会被实例化.ES没有专门支持这种类的语法,但通过`new.target`可以实现.`new.target`保存通过`new`关键字调用的类或函数.通过在实例化时检测`new.target`是不是抽象基类,可以阻止对抽象基类的实例化:
````JS
class Vehicle { // 抽象基类
    constructor() {
        console.log(new.target);
        if (new.target === Vehicle) {
            throw new Error('Vehicle cannot be directly instantiated');
        }
    }
}
class Bus extends Vehicle {}
new Bus();      // class Bus {}
new Vehicle();  // class Vehicle {}
// Error: Vehicle cannot be directly instantiated
````
另外,通过在抽象基类构造函数中进行检查,可以要求派生类必须定义某个方法.因为原型方法在调用类构造函数之前就已经存在了,所以可以通过`this`关键字来检查相应的方法:
````JS
class Vehicle {
    constructor() {
        if (new.target === Vehicle) {
            throw new Error('Vehicle cannot be directly instantiated');
        }
        if (!this.foo) {
            throw new Error('Inheriting class must define foo()');
        }
        console.log('success!');
    }
}
class Bus extends Vehicle {
    foo() {}
}
class Van extends Vehicle {}
new Bus();  // success!
new Van();  // Error: Inheriting class must define foo()
````

#### 继承内置类型
ES6类为继承内置引用类型提供了顺畅的机制,开发者可以方便地扩展内置类型:
````JS
class SuperArray extends Array {
    shuffle() {
        for (let i = this.length - 1; i > 0; i--) {
            const j = Math.floor(Math.random() * (i + 1));
            [this[i], this[j]] = [this[j], this[i]];
        }
    }
}
let a = new SuperArray(1,2,3,4,5);
console.log(a instanceof Array);        // true
console.log(a instanceof SuperArray);   // true
console.log(a);     // [1,2,3,4,5]
a.shuffle();
console.log(a);     // [3,1,4,5,2]
````
有些内置类型的方法会返回新实例.默认情况下,返回实例的类型与原始实例的类型是一致的:
````JS
class SuperArray extends Array {}
let a1 = new SuperArray(1,2,3,4,5);
let a2 = a1.filter(x => !!(x % 2))

console.log(a1);    // [1,2,3,4,5]
console.log(a2);    // [1,3,5]
console.log(a1 instanceof SuperArray);  // true
console.log(a2 instanceof SuperArray);  // true
````
如果想要覆盖这个默认行为,则可以覆盖`Symbol.species`访问器,这个访问器决定在创建返回的实例时使用的类:
````JS
class SuperArray extends Array {
    static get [Symbol.species]() {
        return Array;
    }
}
let a1 = new SuperArray(1,2,3,4,5);
let a2 = a1.filter(x => !!(x % 2))

console.log(a1);    // [1,2,3,4,5]
console.log(a2);    // [1,3,5]
console.log(a1 instanceof SuperArray);  // true
console.log(a2 instanceof SuperArray);  // false
````

#### 类混入
把不同类的行为集中到一个类是一种常见的JS模式,虽然ES6没有显式支持多类继承,但通过现有特性可以轻松地模拟这种行为.

*注:`Object.assign()`方法就是为了混入对象行为而设计的.如果只是需要混入多个对象的属性,那么使用`Object.assign()`就可以了.否则,需要实现自己的混入表达式.*

`extends`关键字后面是一个JS表达式时,任何可以被解析为一个类或一个构造函数的表达式都是有效的.这个表达式会在求值类定义时被求值:
````JS
class Vehicle {}
function getParentClass() {
    console.log('evaluated expression');
    return Vehicle;
}
class Bus extends getParentClass() {}
````
混入模式可以通过在一个表达式中连缀多个混入元素来实现,这个表达式最终会解析为一个可以被继承的类.如果`Person`类需要组合A,B,C,则需要某种机制实现B继承A,C继承B,而`Person`再继承C,从而把A,B,C组合到这个超类中.实现这种模式有不同的策略.
- 定义一组"可嵌套"的函数,每个函数分别接收一个超类作为参数,而将混入类定义为这个参数的子类,并返回这个类.这些组合函数可以连缀调用,最终组合成超类表达式:
````JS
class Vehicle {}
let FooMixin = (Superclass) => class extends Superclass {
    foo() {
        console.log('foo');
    }
};
let BarMixin = (Superclass) => class extends Superclass {
    bar() {
        console.log('bar');
    }
};
let BazMixin = (Superclass) => class extends Superclass {
    baz() {
        console.log('baz');
    }
};
function mix(BaseClass, ...Mixins) {
    return Mixins.reduce((accumulator, current) => current(accumulator), BaseClass);
}
class Bus extends mix(Vehicle, FooMixin, BarMixin, BazMixin) {}
// class Bus extends FooMixin(BarMixin(BazMixin(Vehicle))) {}
let b = new Bus();
b.foo();    // foo
b.bar();    // bar
b.baz();    // baz
````
*注意:很多JS框架已经抛弃混入模式,转向了组合模式(把方法提取到独立的类和辅助对象中,然后把它们组合起来,但不使用继承).这反映了`组合胜过继承(composition over inheritance)`软件设计原则*.这个设计原则被很多人遵循,在代码设计中能提供极大的灵活性.

### 新增特性
#### 私有属性(ES2022)(*待补充*)
详见:[MDN-JavaScript-类-私有属性](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Classes/Private_properties)

# 代理和反射
代理和反射为开发这提供了拦截并向基本操作嵌入额外行为的能力.具体地说,可以给目标对象定义一个关联的代理对象,而这个代理对象可以作为抽象的目标对象来使用.在对象的各种操作影响目标对象之前,可以在代理对象中对这些操作加以控制.

代理是ES6添加的,且是无可替代的,因此代理和反射只在完全支持它们的平台上才有用.

## 代理基础
代理是目标对象的抽象.代理类似C++指针(但有重大区别),因为它可以用作目标对象的替身,但又完全独立于目标对象.对象既可以直接被操作,又可以通过代理来操作.但直接操作会绕过代理施予的行为.

### 创建空代理
空代理是最简单的代理.默认情况下,在代理对象上执行的所以操作都会无障碍地传播到目标对象,因此,在任何可以使用目标对象的地方,都可以通过同样的方式来使用与之关联的代理对象.

代理使用`Proxy`构造函数创建的.这个构造函数接收两个参数:目标对象和处理程序对象.缺少任何一个参数都会抛出`TypeError`.要创建空代理,可以传一个简单的对象字面量作为处理程序对象,从而让所有操作畅通无阻地抵达操作对象:
````JS
const target = { id: 'target' };
const handler = {};
const proxy = new Proxy(target, handler);   // 空代理
// target和proxy访问同一个对象
console.log(target.id); // target
console.log(proxy.id);  // target

target.id = 'foo';
console.log(target.id); // foo
console.log(proxy.id);  // foo

proxy.id = 'bar';
console.log(target.id); // bar
console.log(proxy.id);  // bar

console.log(target.hasOwnProperty('id'));   // true
console.log(proxy.hasOwnProperty('id'));    // true
// Proxy.prototype是undefined,因此不能使用instanceof操作符
console.log(target instanceof Proxy);   // TypeError
console.log(proxy instanceof Proxy);    // TypeError
// 严格相等可以用来区分代理和目标
console.log(target === proxy);  // false
console.log(target == proxy);   // false
````

### 定义捕获器
捕获器(trap)就是在处理程序对象中定义的"基本操作的拦截器".每个处理程序对象可以包含零个或多个捕获器,每个捕获器都对应一种基本操作,可以直接或间接在代理对象上调用.每次在代理对象上调用这些基本操作时,代理可以在这些操作传播到对象之前先调用捕获器函数,从而拦截并修改相应的行为.

*捕获器(trap)是从操作系统中借用的概念.*

例如,可以定义一个`get()`捕获器,当通过代理对象执行`get()`操作时,就会触发定义的`get()`捕获器.此处的`get()`在JS代码中可以通过多种形式触发并被`get()`捕获器拦截到,例如:`proxy[property]`,`proxy.property`,`Object.create(proxy)[property]`.但是在目标对象上直接执行这些操作仍然会产生正常的行为.  
例如:
````JS
const target = {
    foo: 'bar'
};
const handler = {
    get() {
        return 'handler override';
    }
};
const proxy = new Proxy(target, handler);
console.log(target.foo);                    // bar
console.log(proxy.foo);                     // handler override
console.log(target['foo']);                 // bar
console.log(proxy['foo']);                  // handler override
console.log(Object.create(target)['foo']);  // bar
console.log(Object.create(proxy)['foo']);   // handler override
````
### 捕获器参数和反射API
所有捕获器都可以访问相应的参数,基于这些参数可以重建被捕获方法的原始行为.

例如,`get()`捕获器会接收到目标对象,要查询的属性和代理对象三个参数:
````JS
const target = {
    foo: 'bar'
};
const handler = {
    get(trapTarget, property, receiver) {
        console.log(trapTarget);
        console.log(property);
        console.log(receiver);
        console.log(receiver === proxy);
        return trapTarget[property] + ' baz';
    }
};
const proxy = new Proxy(target, handler);
console.log(proxy.foo);
// {foo: 'bar'}
// foo
// Proxy(Object) {foo: 'bar'}
// true
// bar baz
console.log(target.foo);
// bar
````
但对于更加复杂的捕获器，可以通过调用全局`Reflect`对象上(封装了原始行为)的同名方法来轻松重建.处理程序对象中所有可以捕获的方法都有对应的`反射(Reflect)API`方法.这些方法与捕获器拦截的方法具有相同的名称和函数签名,而且也具有与被拦截方法相同的行为.因此,使用反射API也可以定义出空代理:
````JS
const target = {
    foo: 'bar'
};
const handler = {
    get() {
        console.log(...arguments);
        // {foo: "bar"} 'foo' Proxy(Object)
        return Reflect.get(...arguments);
    }
}
const proxy = new Proxy(target, handler);
console.log(proxy.foo);     // bar
console.log(target.foo);    // bar
````
甚至可以将代理写得更加简洁:
````JS
const handler = {
    get: Reflect.get
}
const proxy = new Proxy(target, handler);
````
如果想创建一个可以捕获所有方法,然后将每个方法转发给对应反射API的空代理,那么甚至不需要定义处理程序对象:
````JS
const target = {
    foo: 'bar'
};
const proxy = new Proxy(target, Reflect);
console.log(proxy.foo);     // bar
console.log(target.foo);    // bar
console.log(Reflect);
// {
//     apply: ƒ apply(),
//     construct: ƒ construct(),
//     defineProperty: ƒ defineProperty(),
//     deleteProperty: ƒ deleteProperty(),
//     get: ƒ (),
//     getOwnPropertyDescriptor: ƒ getOwnPropertyDescriptor(),
//     getPrototypeOf: ƒ getPrototypeOf(),
//     has: ƒ has(),
//     isExtensible: ƒ isExtensible(),
//     ownKeys: ƒ ownKeys(),
//     preventExtensions: ƒ preventExtensions(),
//     set: ƒ (),
//     setPrototypeOf: ƒ setPrototypeOf(),
//     Symbol(Symbol.toStringTag): "Reflect",
//     [[Prototype]]: Object
// }
````
反射API为开发者准备好了样板代码,在此基础上开发者可以使用最少的代码修改捕获的方法.

### 捕获器不变式
捕获器可以改变所有的基本方法的行为,但其必须遵循`"捕获器不变式"`.捕获器不定式因方法不同而异,但通常会防止捕获器定义出现过于反常的行为.

例如,当尝试获得目标对象不可配置且不可写的数据属性,若捕获器返回一个与该属性不同的值时,会抛出`TypeError`:
````JS
const target = {};
Object.defineProperty(target, 'foo', {
    configurable: false,
    writable: false,
    value: 'bar'
});
const handler = {
    get() {
        return 'qux';
    }
};
const proxy = new Proxy(target, handler);
console.log(proxy.foo); // TypeError
````

### 可撤销代理
有时候需要中断代理对象与目标对象之间的联系,使用`revocable()`方法可以撤销代理对象与目标对象的关联.撤销代理的操作是不可逆的.而且,撤销函数(`revoke()`)是幂等的(即调用多少次都一样,不会抛出错误).

撤销函数和代理对象是在实例化时同时生成的:
````JS
const target = {
    foo: 'bar'
};
const handler = {
    get() {
        return 'intercepted';
    }
};
const { proxy, revoke } = Proxy.revocable(target, handler);
console.log(proxy.foo);     // intercepted
console.log(target.foo);    // foo
revoke();
console.log(proxy.foo);     // TypeError
````

### 使用反射API
某些情况下应该优先使用反射API.
#### 反射API与对象API
在使用反射API时:
- 反射API并不限于捕获处理程序.
- 大多数反射API方法在`Object`类型上有对应的方法.  
通常,`Object`上的方法适用于通用程序,而反射方法适用于细粒度的对象控制与操作.

#### 状态标记
很多反射API返回称作`状态标记`的布尔值,表示意图执行的操作是否成功.有时候,状态标记比那些返回修改后的对象或者抛出错误的反射API方法更有用.例如对以下代码进行重构:
````JS
// 初始代码
const o = {};
try {
    Object.defineProperty(o, 'foo', 'bar');
    console.log('success');
} catch(e) {
    console.log('failure');
}
````
在定义新属性时如果发生问题,`Reflect.defineProperty()`会返回`false`,而不是抛出错误.因此使用这个反射方法可以这样重构上述代码:
````JS
// 重构后的代码
const o = {};
if (Reflect.defineProperty(o, 'foo', { value: 'bar' })) {
    console.log('success');
} else {
    console.log('failure');
}
````
以下反射方法都会提供状态标记:
- `Reflect.defineProperty()`
- `Reflect.preventExtensions()`
- `Reflect.setPrototypeOf()`
- `Reflect.set()`
- `Reflect.deleteProperty()`

#### 等价函数替代操作符
以下反射函数提供只有通过操作符才能完成的操作:
- `Reflect.get()`: 可以替代对象属性访问操作符
- `Reflect.set()`: 可以替代`=`赋值操作符
- `Reflect.has()`: 可以替代`in`操作符或`with()`
- `Reflect.deleteProperty()`: 可以替代`delete`操作符
- `Reflect.construct()`: 可以替代`new`操作符

#### 安全地应用函数
在通过`apply`方法调用函数时,被调用的函数可能也定义了自己的`apply`属性(虽然可能性很小).为了绕过这个问题,可以使用定义在`Function`原型上的`apply`方法,例如:
````JS
Function.prototype.apply.call(myFunc, thisVal. argumentsList);
````
但可以通过使用`Reflect.apply`简化上述代码:
````JS
Reflect.apply(myFunc, thisVal, argumentsList);
````

### 代理另一个代理
代理可以拦截反射API的操作,这意味着可以创建一个代理,通过它去代理另一个代理.这样可以在一个目标对象之上构建多层拦截网:
````JS
const target = {
    foo: 'bar'
};
const firstProxy = new Proxy(target, {
    get() {
        console.log('first proxy');
        return Reflect.get(...arguments);
    }
});
const secondProxy = new Proxy(firstProxy, {
    get() {
        console.log('second proxy');
        return Reflect.get(...arguments);
    }
});
console.log(secondProxy.foo);
// second proxy
// first proxy
// bar
````

### 代理的问题与不足
代理在某些情况下不能和现在的ES机制很好的协同.

#### 代理中的this
````JS
const target = {
    thisValEqualsProxy() {
        return this === proxy;
    }
}
const proxy = new Proxy(target, {});
console.log(target.thisValEqualsProxy());   // false
console.log(proxy.thisValEqualsProxy());    // true
````
通过代理`proxy`使用`this.Method()`实际上会调用`proxy.Method()`:
````JS
const target = {
    sayThis() {
        console.log(this);
    }
}
const proxy = new Proxy(target, {});
target.sayThis();
// {
//     sayThis: ƒ sayThis(),
//     [[Prototype]]: Object
// }
proxy.sayThis();
// Proxy(Object) {
//     [[Handler]]: Object,
//     [[Target]]: {
//         sayThis: ƒ sayThis(),
//         [[Prototype]]: Object,
//     }
//     [[IsRevoked]]: false
// }
````
通常情况下会符合预期的行为,但如果目标对象依赖于对象标识,那可能会出现意料之外的结果:
````JS
const wm = new WeakMap();
class User {
    constructor(userId) {
        wm.set(this, userId);
    }
    set id(userId) {
        wm.set(this, userId);
    }
    get id() {
        return wm.get(this);
    }
}
const user = new User(123);
console.log(user.id);   // 123
const userInstanceProxy = new Proxy(user, {});
console.log(userInstanceProxy.id);  // undefined
````
上面代码从`WeakMap`中查询值依赖于`User`实例的对象标识,因此该实例被代理时会出现问题.

要解决这个问题,需要重新配置代理,把代理`User`实例改为代理`User`类本身.之后再创建代理的实例就会以代理实例作为`WeakMap`的键:
````JS
const UserClassProxy = new Proxy(User, {});
const proxyUser = new UserClassProxy(456);
console.log(proxyUser.id);
````

#### 代理与内部插槽
代理与内置引用类型的实例通常可以很好地协同,但有些ES内置类型可能会依赖代理无法控制的机制,结果导致在代理上调用某些方法会出错.

例如`Date`类型.根据ES规范,`Date`类型方法的执行依赖`this`值上的内部插槽`[[NumberDate]]`.代理对象上不存在这个内部插槽,而且这个内部插槽的值也不能通过普通的`get()`和`set()`操作访问到.于是代理拦截后本应转发给目标对象的方法会抛出`TypeError`:
````JS
const target = new Date();
const proxy = new Proxy(target, {});
console.log(proxy instanceof Date); // true
proxy.getDate();    // TypeError: 'this' is not a Date object
````

## 代理捕获器与反射方法
代理可以捕获13种不同的基本操作.这些操作有各自不同的反射API方法,参数,关联ES操作和不变式.

正如前面示例所展示的,有几种不同的JS操作会调用同一个捕获器处理程序.不过,对于在代理上执行的任何一种操作,只会有一个捕获处理程序被调用.不会存在重复捕获的情况.

只要在代理上调用,所有捕获器都会拦截它们对应的反射API操作.

### 必要说明
对象的可扩展性(即是否可以在它上面添加新的属性)可以使用静态方法`Object.isExtensible()`来判断.

`Object.preventExtensions()`静态方法可以防止新属性被添加到对象中(即防止该对象被扩展).它还可以防止对象的原型被重新指定.

`Object.seal()`静态方法密封一个对象.密封一个对象会阻止其扩展并且使得现有属性不可配置.但只要属性是可写的,就可以修改属性的值.

`Object.freeze()`静态方法可以使一个对象被冻结.冻结对象可以防止扩展,并使现有的属性不可写入和不可配置.

### get()
`get()`捕获器会在获取属性值的操作中被调用.对应的反射API方法为`Reflect.get()`:
````JS
const myTarget = {};
const proxy = new Proxy(myTarget, {
    get(target, property, receiver) {
        console.log('get()');
        return Reflect.get(...arguments);
    }
});
proxy.foo;
// get()
````

#### 返回值
无限制.

#### 拦截的操作
- `proxy.property`
- `proxy[property]`
- `Object.create(proxy)[property]`
- `Reflect.get(proxy, property, receiver)`

#### 捕获器处理程序参数
- `target`: 目标对象
- `property`: 引用的目标对象上的字符串键属性或符号
- `receiver`: 代理对象或继承代理对象的对象

#### 捕获器不变式
- 如果`target.property`不可写且不可配置,则处理程序返回的值也必须与`target.property`匹配.
- 如果`target.property`不可配置且`[[Get]]`特性为`undefined`,处理程序的返回值也必须是`undefined`.

### set()
`set()`捕获器会在设置属性值的操作中被调用.对应的反射API方法为`Reflect.set()`.
````JS
const myTarget = {};
const proxy = new Proxy(myTarget, {
    set(target, property, value, receiver) {
        console.log('set()');
        return Reflect.set(...arguments);
    }
});
proxy.foo = 'bar';
// set()
````

#### 返回值
返回`true`表示成功;返回`false`表示失败,严格模式下会抛出`TypeError`.

#### 拦截的操作
- `proxy.property = value`
- `proxy[property] = value`
- `Object.create(proxy)[property] = value`
- `Reflect.set(proxy, property, value, receiver)`

#### 捕获器处理程序参数
- `target`: 目标对象
- `property`: 引用的目标对象上的字符串键属性或符号
- `value`: 要赋给属性(或符号,不再赘述)的值
- `receiver`: 接收最初赋值的对象.

#### 捕获器不变式
- 如果`target.property`不可写且不可配置,则不能修改目标属性的值.
- 如果`target.property`不可写且[[Set]]特性为`undefined`,则不能修改目标属性的值
- 在严格模式下,处理程序中返回`false`会抛出`TypeError`.

### has()
`has()`捕获器会在`in`操作符中调用.对应的反射API方法为`Reflect.has()`:
````JS
const myTarget = {};
const proxy = new Proxy(myTarget, {
    has(target, property) {
        console.log('has()');
        return Reflect.has(...arguments);
    }
});
'foo' in proxy;
// has()
````

#### 返回值
`has()`必须返回布尔值,表示属性是否存在.返回非布尔值会被转型为布尔值.

#### 拦截的操作
- `property in proxy`
- `property in Object.create(proxy)`
- `with(proxy) {(property);}`
- `Reflect.has(proxy, property)`

#### 捕获器处理程序参数
- `target`: 目标对象
- `property`: 引用目标对象上的字符串键属性或符号

#### 捕获器不变式
- 如果`target.property`存在且不可配置,则处理程序必须返回`true`.
- 如果`target.property`存在且目标对象不可扩展,则处理程序必须返回`true`.

### defineProperty()
`defineProperty()`捕获器会在`Object.defineProperty()`中被调用.对应的反射API方法为`Reflect.defineProperty()`.
````JS
const myTarget = {};
const proxy = new Proxy(myTarget, {
    defineProperty(target, property, descriptor) {
        console.log('defineProperty()');
        return Reflect.defineProperty(...arguments);
    }
});
Object.defineProperty(proxy, 'foo', { value: 'bar' });
// defineProperty()
````

#### 返回值
`defineProperty()`必须返回布尔值,表示属性是否成功定义.返回非布尔值会被转型为布尔值.

#### 拦截的操作
- `Object.defineProperty(proxy, property, descriptor)`
- `Reflect.defineProperty(proxy, property, descriptor)`

#### 捕获器处理程序参数
- `target`: 目标对象
- `property`: 引用的目标对象上的字符串键属性或符号
- `descriptor`: 包含可选的`enumerable`,`configurable`,`writable`,`value`,`get`,`set`定义的对象

#### 捕获器不变式
- 如果目标对象不可扩展,则无法定义属性.
- 如果目标对象有一个可配置的属性,则不能添加同名的不可配置属性.
- 如果目标对象有一个不可配置的属性,则不能添加同名的可配置属性.

### getOwnPropertyDescriptor()
`getOwnPropertyDescriptor()`捕获器会在`Object.getOwnPropertyDescriptor()`中被调用.对应的反射API方法为`Reflect.getOwnPropertyDescriptor()`.
````JS
const myTarget = {};
const proxy = new Proxy(myTarget, {
    getOwnPropertyDescriptor(target, property) {
        console.log('getOwnPropertyDescriptor()');
        return Reflect.getOwnPropertyDescriptor(...arguments);
    }
});
Object.getOwnPropertyDescriptor(proxy, 'foo');
// getOwnPropertyDescriptor()
````

#### 返回值
`getOwnPropertyDescriptor()`必须返回对象,或者在属性不存在时返回`undefined`.

#### 拦截的操作
- `Object.getOwnPropertyDescriptor(proxy, property)`
- `Reflect.getOwnPropertyDescriptor(proxy, property)`

#### 捕获器处理程序参数
- `target`: 目标对象
- `property`: 引用的目标对象上的字符串键或符号操作

#### 捕获器不变式
- 如果自有的`target.property`存在且不可配置,则处理程序必须返回一个表示该属性存在的对象.
- 如果自有的`target.property`存在且可配置,则处理程序必须返回表示该属性可配置的对象.
- 如果自有的`target.property`存在且`target`不可扩展,则处理程序必须返回一个表示该属性存在的对象.
- 如果`target.property`不存在且`target`不可扩展,则处理程序必须返回`undefined`表示该属性不存在.
- 如果`target.property`不存在,则处理程序不能返回表示该属性可配置的对象.

### deleteProperty()
`deleteProperty()`捕获器会在使用`delete`操作符中被调用.对应的反射API方法为`Reflect.deleteProperty()`.
````JS
const myTarget = {};
const proxy = new Proxy(myTarget, {
    deleteProperty(target, property) {
        console.log('deleteProperty()');
        return Reflect.deleteProperty(...arguments);
    }
});
delete proxy.foo;
// deleteProperty()
````

#### 返回值
`deleteProperty()`必须返回布尔值,表示删除属性是否成功.返回非布尔值会被转型为布尔值.

#### 拦截的操作
- `delete proxy.property`
- `delete proxy[property]`
- `Reflect.deleteProperty(proxy, property)`

#### 捕获器处理程序参数
- `target`:目标对象.
- `property`:引用的目标对象上的字符串键属性或符号.

#### 捕获器不变式
- 如果自有的`target.property`存在且不可配置,则处理程序不能删除这个属性.

#### ownKeys()
`ownKeys()`捕获器会在`Object.keys()`及类似方法中被调用.对应的反射API方法为`Reflect.ownKeys()`.
````JS
const myTarget = {};
const proxy = new Proxy(myTarget, {
    ownKeys(target) {
        console.log('ownKeys()');
        return Reflect.ownKeys(...arguments);
    }
});
Object.keys(proxy);
// ownKeys()
````

#### 返回值
`ownKeys()`必须返回包含字符串或符号的可枚举对象.

#### 拦截的操作
- `Object.getOwnPropertyNames(proxy)`
- `Object.getOwnPropertySymbols(proxy)`
- `Object.keys(proxy)`
- `Object.ownKeys(proxy)`

#### 捕获器处理程序参数
- `target`: 目标对象.

#### 捕获器不变式
- 返回的可枚举对象必须包含`target`的所有不可配置的自有属性.
- 如果`target`不可扩展,则返回可枚举对象必须精确地包含自有属性键.

### getPrototypeOf()
`getPrototypeOf()`捕获器会在`Object.getPrototypeOf()`中被调用.对应的反射API方法为`Reflect.getPrototypeOf()`.
````JS
const myTarget = {};
const proxy = new Proxy(myTarget, {
    getPrototypeOf(target) {
        console.log('getPrototypeOf()');
        return Reflect.getPrototypeOf(...arguments);
    }
});
Object.getPrototypeOf(proxy);
// getPrototypeOf()
````

#### 返回值
`getPrototypeOf()`必须返回对象或`null`.

#### 拦截的操作
- `Object.getPrototypeOf(proxy)`
- `Reflect.getPrototypeOf(proxy)`
- `proxy.__proto__`
- `Object.prototype.isPrototypeOf(proxy)`
- `proxy instanceof Object`

#### 捕获器处理程序参数
- `target`:目标对象.

#### 捕获器不变式
- 如果`target`不可扩展,则`Object.getProptotypeOf(proxy)`唯一有效的返回值就是`Object.getProptotypeOf(target)`的返回值.

### setPrototypeOf()
`setPrototypeOf()`捕获器会在`Object.setPrototypeOf()`中被调用.对应的反射API方法为`Reflect.setPrototypeOf()`.
````JS
const myTarget = {};
const proxy = new Proxy(myTarget, {
    setPrototypeOf(target, prototype) {
        console.log('setPrototypeOf()');
        return Reflect.setPrototypeOf(...arguments);
    }
});
Object.setPrototypeOf(proxy, Object);
// setPrototypeOf()
````

#### 返回值
`setPrototypeOf()`必须返回布尔值,表示原型赋值是否成功.返回非布尔值会被转型为布尔值.

#### 拦截的操作
- `Object.setPrototypeOf(proxy)`
- `Reflect.setPrototypeOf(proxy)`

#### 捕获器处理程序参数
`target`:目标对象.
`prototype`:`target`的替代原型,如果是顶级原型则为`null`.

#### 捕获器不变式
- 如果`target`不可扩展,则唯一有效的`prototype`参数就是`Object.getPrototypeOf(target)`的返回值.

### isExtensible()
`isExtensible()`捕获器会在`Object.isExtensible()`中被调用.对应的反射API方法为`Reflect.isExtensible()`.
````JS
const myTarget = {};
const proxy = new Proxy(myTarget, {
    isExtensible(target) {
        console.log('isExtensible()');
        return Reflect.isExtensible(...arguments);
    }
});
Object.isExtensible(proxy);
// isExtensible()
````

#### 返回值
`isExtensible()`必须返回布尔值,表示`target`是否可扩展.返回非布尔值会被转型为布尔值.

#### 拦截的操作
- `Object.isExtensible(proxy)`
- `Reflect.isExtensible(proxy)`

#### 捕获器处理程序参数
- `target`:目标对象.

#### 捕获器不变式
- 如果`target`可扩展,则处理程序必须返回`true`.
- 如果`target`不可扩展,则处理程序必须返回`false`.

### preventExtensions()
`preventExtensions()`捕获器会在`Object.preventExtensions()`中被调用.对应的反射API方法为`Reflect.preventExtensions()`.
````JS
const myTarget = {};
const proxy = new Proxy(myTarget, {
    preventExtensions(target) {
        console.log('preventExtensions()');
        return Reflect.preventExtensions(...arguments);
    }
});
Object.preventExtensions(proxy);
// preventExtensions()
````

#### 返回值
`preventExtensions()`必须返回布尔值,表示`target`是否已经不可扩展.返回非布尔值会被转型为布尔值.

#### 拦截的操作
- `Object.preventExtensions(proxy)`
- `Reflect.preventExtensions(proxy)`

#### 捕获器处理程序参数
- `target`:目标对象.

#### 捕获器不变式
- 如果`Object.isExtensible(proxy)`是`false`,则处理程序必须返回`true`.

### apply()
`apply()`捕获器会在调用函数时被调用.对应的反射API方法为`Reflect.apply()`.
````JS
const myTarget = () => {}
const proxy = new Proxy(myTarget, {
    apply(target, thisArg, ...argumentsList) {
        console.log('apply()');
        return Reflect.apply(...arguments);
    }
});
proxy();
// apply
````

#### 返回值
无限制.

#### 拦截的操作
- `proxy(...argumentsList)`
- `Function.prototype.apply(thisArg, argumentsList)`
- `Function.prototype.call(thisArg, ...argumentsList)`
- `Reflect.apply(target, thisArgument, argumentsList)`

#### 捕获器处理程序参数
- `target`:目标对象.
- `thisArg`:调用函数时的`this`参数.
- `argumentsList`:调用函数时的参数列表.

#### 捕获器不变式
- `target`必须是一个函数对象.

### construct()
`construct()`捕获器会在`new`操作符中被调用.对应的反射API方法为`Reflect.construct()`.
````JS
const myTarget = function() {};
const proxy = new Proxy(myTarget, {
    construct(target, argumentsList, newTarget) {
        console.log('construct()');
        return Reflect.construct(...arguments);
    }
});
new proxy;
// construct()
````

#### 返回值
`construct()`必须返回一个对象.

#### 拦截的操作
- `new proxy(...argumentsList)`
- `Reflect.construct(target, argumentsList, newTarget)`

#### 捕获器处理程序参数
- `target`:目标构造函数.
- `argumentsList`:传给目标构造函数的参数列表.
- `newTarget`:最初被调用的构造函数.

#### 捕获器不变式
- `target`必须可以用作构造函数.

## 代理模式
### 跟踪属性访问
通过捕获`get`,`set`和`has`等操作,可以知道对象属性什么时候被访问,被查询.把实现相应捕获器的某个对象代理放到应用中,可以监测这个对象何时在何处被访问过:
````JS
const user = {
    name: 'aaa'
};
const proxy = new Proxy(user, {
    get(target, property, receiver) {
        console.log(`Getting ${property}`);
        return Reflect.get(...arguments);
    },
    set(target, property, value, receiver) {
        console.log(`Setting ${property} = ${value}`);
        return Reflect.set(...arguments);
    }
});
proxy.name;     // Getting name
proxy.age = 27; // Setting age = 27
````

### 隐藏属性
代理的内部实现对外部代码是不可见的,因此要隐藏目标对象上的属性也是轻而易举:
````JS
const hiddenProperties = ['foo', 'bar'];
const targetObject = {
    foo: 1,
    bar: 2,
    baz: 3
};
const proxy = new Proxy(targetObject, {
    get(target, property) {
        if (hiddenProperties.includes(property)) {
            return undefined;
        } else {
            return Reflect.get(...arguments);
        }
    },
    has(target, property) {
        if (hiddenProperties.includes(property)) {
            return false;
        } else {
            return Reflect.has(...arguments);
        }
    }
});
console.log(proxy.foo); // undefined
console.log(proxy.bar); // undefined
console.log(proxy.baz); // 3
console.log('foo' in proxy);    // false
console.log('bar' in proxy);    // false
console.log('baz' in proxy);    // true
````

### 属性验证
因为所有赋值操作都会触发`set()`捕获器,所以可以根据所赋的值决定是允许还是拒绝赋值:
````JS
const target = {
    onlyNumbersGoHere: 0
};
const proxy = new Proxy(target, {
    set(target, property, value) {
        if (typeof value !== 'number') {
            return false;
        } else {
            return Reflect.set(...arguments);
        }
    }
});
proxy.onlyNumbersGoHere = 1;
console.log(proxy.onlyNumbersGoHere);   // 1
proxy.onlyNumbersGoHere = '2';
console.log(proxy.onlyNumbersGoHere);   // 1
````

### 函数与构造函数参数验证
跟保护和验证对象属性类似,也可对函数和构造函数参数进行审查:
````JS
function median(...nums) {
    return nums.sort()[Math.floor(nums.length / 2)];
}
const proxy = new Proxy(median, {
    apply(target, thisArg, argumentsList) {
        for (const arg of argumentsList) {
            if (typeof arg !== 'number') {
                throw 'Non-number argument provided';
            }
        }
        return Reflect.apply(...arguments);
    }
});
console.log(proxy(4, 7, 1));    // 4
console.log(proxy(4, '7', '1'));    // Error: Non-number argument provided
````
````JS
class User {
    constructor(id) {
        this.id_ = id;
    }
}
const proxy = new Proxy(User, {
    construct(target, argumentsList, newTarget) {
        if (argumentsList[0] === undefined) {
            throw 'User cannot be instantiated without id';
        } else {
            return Reflect.construct(...arguments);
        }
    }
});
new proxy(1);
new proxy();    // Error: User cannot be instantiated without id
````

### 数据绑定与可观察对象
通过代理可以把运行时中原本不相关的部分联系到一起.这样就可以实现各种模式,从而让不同的代码互相操作.

比如,可以将被代理的类绑定到一个全局实例集合,让所有创建的实例都被添加到这个集合中:
````JS
const userList = [];
class User {
    constructor(name) {
        this.name_ = name;
    }
}
const proxy = new Proxy(User, {
    construct() {
        const newUser = Reflect.construct(...arguments);
        userList.push(newUser);
        return newUser;
    }
});
new proxy('John');
new proxy('Jacob');
new proxy('Jingleheimerschmidt');
console.log(userList);  // [User {}, User {}, User {}]
````
还可以把集合绑定到一个事件分派程序,每次插入新实例时都会发送消息:
````JS
const userList = [];
function emit(newValue) {
    console.log(newValue);
}
const proxy = new Proxy(userList, {
    set(target, property, value, receiver) {
        const result = Reflect.set(...arguments);
        if (result) {
            emit(Reflect.get(target, property, receiver));
        }
        return result;
    }
});
proxy.push('John');
// John
proxy.push('Jacob');
// Jacob
````

# 函数
函数实际上是对象.每个函数都是`Function`类型的实例,而`Function`也有属性和方法,跟其他引用类型一样.因为函数是对象,所以函数名就是指向函数对象的指针,而且不一定与函数本身紧密绑定.函数通常以函数声明的方式定义:
````JS
function sum(num1, num2) {
    return num1 + num2;
}   // 此处无分号
````
````JS
let sum = function(num1, num2) {
    return num1 + num2;
};  // 此处有分号
````
可以使用`箭头函数`定义函数:
````JS
let sum = (num1, num2) => {
    return num1 + num2;
};
````
还可以使用`Function`构造函数,构造函数接收任意多个字符串参数,最后一个参数始终会被当成函数体,而之前的参数都是新函数的参数:
````JS
let sum = new Function("num1", "num2", "return num1 + num2;");  // 不推荐
````
不推荐使用`Function`构造函数来创建函数,因为该代码会被解析两次,第一次当成常规代码,第二次将字符串解析为函数.这会影响性能.

## 箭头函数
ES6新增了使用`=>`(箭头)语法定义函数表达式的能力.任何可以使用函数表达式的地方,都可以使用箭头函数:
````JS
let arrowSum = (a, b) => {
    return a + b;
};
let functionExpressionSum = function(a, b) {
    return a + b;
};
console.log(arrowSum(5, 8));    // 13
console.log(functionExpressionSum(5, 8));   // 13
````
箭头函数简洁的语法非常适合嵌入函数的场景:
````JS
let ints = [1, 2, 3];
console.log(ints.map(function(i) {return i + 1;})); // [2, 3, 4]
console.log(ints.map((i) => {return i + 1;}))       // [2, 3, 4]
````
如果只有一个参数,那也可以不用括号.只有没有参数,或者多个参数的情况下,才需要使用括号:
````JS
let double = (x) => {return 2 * x;};    // OK
let triple = x => {return 3 * x;};      // OK
let getRandom = () => {return Math.random();}   // ()是必需的
let sum = (a, b) => {return a + b;};    // ()是必需的
````
箭头函数可以不用大括号,但是这样箭头后面就只能有一行代码,比如一个赋值操作,或者一个表达式.而且,省略大括号会隐式返回这行代码的值:
````JS
let double = (x) => {return 2 * x;};    // OK
let triple = (x) => 3 * x;  // OK

let value = {};
let setName = x => x.name = "aaa";  // OK
setName(value);
console.log(value.name);    // aaa

let multiply = (a, b) => return a * b;  // Error
````
但箭头函数不能使用`arguments`,`super`和`new.target`,也不能用作构造函数.此外箭头函数也没有`prototype`属性.

## 函数名
函数名就是指针,因此一个函数可以有多个名称.
````JS
function sum(num1, num2) {
    return num1 + num2;
}
console.log(sum(10, 10));           // 20
let anotherSum = sum;
console.log(anotherSum(10, 10));    // 20
sum = null;
console.log(anotherSum(10, 10));    // 20
````
ES的所有函数对象都只会暴露一个只读的`name`属性,其中包含关于函数的信息.多数情况下,这个属性中保存的就是一个函数标识符(字符串化的变量名).如果函数没有名称,则会显示为空字符串.如果函数使用`Function`构造函数创建,则会标识为`"anonymous"`:
````JS
function foo() {}
let bar = function() {};
let baz = () => {};
console.log(foo.name);              // foo
console.log(bar.name);              // bar
console.log(baz.name);              // baz
console.log((() => {}).name);       // (空字符串)
console.log((new Function()).name); // anonymous
let qux = baz;
baz = null;
console.log(qux.name);              // baz
````
如果函数是一个获取函数,设置函数,或者使用`bind()`实例化,那么标识符前面会加上一个前缀:
````JS
function foo() {}
console.log(foo.bind(null).name);   // bound foo
let dog = {
    years: 1,
    get age() {
        return this.years;
    },
    set age(newAge) {
        this.years = newAge;
    }
};
let propertyDescriptor = Object.getOwnPrrpertyDescriptor(dog, 'age');
console.log(propertyDescriptor.get.name);   // get age
console.log(propertyDescriptor.set.name);   // set age
````

## 理解参数
ES中传入函数的参数数量不需要和函数接收的数量匹配,多于或少于其数量都是合法的.

其原因是所有函数的参数在内部表现为一个数组,函数被调用时总会接收一个数组,但函数并不关心这个数组里面包含什么.

在使用`function`关键字定义(非箭头)函数时,可以在函数内部访问`arguments`对象,从中取得传进来的每个参数值.

`arguments`对象是一个类数组对象(但不是一个`Array`实例),因此可以使用中括号语法访问其中的元素(第一个参数为`arguments[0]`,第二个参数为`arguments[1]`).要确定传进来多少个参数,可以访问`arguments.length`属性:
````JS
function countArgs() {
    console.log(arguments.length);
}
countArgs("string", 42);    // 2
countArgs();                // 0
countArgs(12);              // 1

function doAdd(num1, num2) {
    if (arguments.length === 1) {
        console.log(num1 + 10);
    } else if (arguments.length === 2) {
        console.log(arguments[0] + num2);
    }
}
````

ES中的函数参数只不过是为了方便才写出来的,不写出来依然可以使用:
````JS
function sayHi() {
    console.log("Hello " + arguments[0] + ", " + "hello " + arguments[1]);
}
sayHi("world", "JS!");
// Hello world, hello JS!
````

`arguments`的值始终会与对应的命名参数同步(注意,并不是说两者一定共享相同的地址,对于原始值而言,两者只是保持同步而已):
````JS
function doAdd(num1, num2) {
    arguments[1] = 10;
    console.log(arguments[0] + num2);
}
doAdd(12, 13);  // 22
doAdd(12);      // NaN
````
注意,上例中如果只传入一个参数,此时`arguments[1]`并不存在,因此对`arguments[1]`的赋值不会映射到`num2`,对`num2`的赋值也不会映射到`arguments[1]`.因此,`doAdd(12)`执行`12 + undefined`.

对于没有传参的命名变量,其值为`undefined`.

严格模式下,对`arguments`的值不会映射到命名参数(对于原始值而言,两者是不同的值,对于引用值而言,两者仍然指向同一块内存).尝试在函数中重写`arguments`对象会导致语法错误:
````JS
"use strict";
function doAdd(num1, num2) {
    arguments[1] = 10;
    console.log(arguments[0] + num2);
}
doAdd(12, 13);  // 25
doAdd(12);      // NaN
function addArray(arr) {
    arguments[0].push(1);
    console.log(arr);
}
addArray([-1,0]);   // [-1,0,1]
````

### 箭头函数中的参数
如果函数是使用箭头语法定义的,那么传给函数的参数将不能使用`arguments`关键字访问,而只能通过定义的命名参数访问:
````JS
let bar = () => {
    console.log(arguments[0]);
};
bar(5); // ReferenceError: arguments is not defined
````
但箭头函数允许调用包装函数的`arguments`:
````JS
function foo() {
    let bar = () => {
        console.log(arguments[0]);
    }
}
foo(5); // 5
````

## 没有重载
ES不能重载函数.后定义的同名函数会覆盖先定义的:
````JS
function add(num) {
    return num + 100;
}
function add(num) {
    return num + 200;
}
console.log(add(100));  // 300
````

## 默认参数值
ES6支持显示定义默认参数:
````JS
function sayName(name = "aaa") {
    console.log(name);
}
sayName("bbb");     // bbb
sayName();          // aaa
sayName(undefined); // aaa
````
`arguments`不反应参数的默认值,只反映传给函数的参数.此外,对于含有默认值的命名参数,修改命名参数不会影响`arguments`对象:
````JS
function sayName(name = "aaa") {
    name = "bbb";
    console.log(arguments[0]);
}
sayName();          // undefined
sayName("ccc");     // ccc
sayName(undefined, "ddd");  // undefined
````
默认值可以是一个表达式,而非仅仅是字面量:
````JS
function getArr() {
    return [1,2,3,4,5];
}
function say(arr = getArr()) {
    console.log(arr);
}
say(1); // 1
say();  // [1,2,3,4,5]
````
默认值只有在函数被调用时才会求值,不会在函数定义时求值.且只有在调用函数但未传相应参数时才会被调用.

箭头函数同样也可以这样使用默认参数,只不过在只有一个参数且包含默认值时,就必须使用括号而不能省略了:
````JS
let func = (name = "aaa") => console.log(name);
func("bbb");    // bbb
func();         // aaa
````

### 默认参数作用域与暂时性死区
因为在求值默认参数时可以定义对象,也可以动态调用函数,所有函数参数肯定是在某个作用域中求值的.

给多个参数定义默认值实际上跟使用`let`关键字顺序声明变量一样:
````JS
function say1(name = "aaa", other = name) {
    console.log(name + ' ' + other);
}
function say2(name = other, other = "aaa") {}    // 调用时不传第一个参数会报错,因为对于name来说,other变量并不存在
function say3(name = "aaa", other = tmp) {  // 调用时不传第二个参数会报错,因为对于other来说,函数体内的tmp变量未定义
    let tmp = "bbb";
}
````

## 参数扩展与收集
ES6新增了扩展操作符,使用它可以非常简洁地操作和组合集合数据.扩展操作符既可以用于调用函数时传参,也可以用于定义函数参数.

### 扩展参数
如果要将数组中的元素作为参数传入函数当中,可以使用`apply`方法,也可以使用`扩展操作符...`:
````JS
let values = [1,2,3,4];
function getSum() {
    let sum = 0;
    for (let i = 0; i < arguments.length; ++i) {
        sum += arguments[i];
    }
    return sum;
}
console.log(getSum(null, values));  // 10
console.log(getSum(...values));     // 10
````
扩展操作符能将可迭代对象拆分,并将迭代返回的每个值单独传入:
````JS
console.log(getSum(-1, ...values));         // 9
console.log(getSum(...values, 5));          // 15
console.log(getSum(...values, ...[5,6,7])); // 28
````
函数中`arguments`会计算拆分后的实参的长度:
````JS
function countArgs() {
    console.log(arguments.length);
}
countArgs(-1, ...[5,6,7]);  // 4
````
也允许使用命名参数接收扩展操作符拆分的实参:
````JS
function getSum(a, b, c = 1) {
    return a + b + c;
}
console.log(getSum(...[0,1]));      // 2
console.log(getSum(...[0,1,2]));    // 3
console.log(getSum(...[0,1,2,3]));  // 3
````

### 收集参数
可以使用扩展操作符把超出命名参数的接收范围的实参组合为一个数组:
````JS
function say(firstValue, ...values) {
    console.log(firstValue, values);
}
say(1,2,3,4,5);         // 1 [2,3,4,5]
say(...[0,9,8,7,6]);    // 0 [9,8,7,6]
say();                  // undefined []
````
收集参数的结果可变,所以只能把它作为最后一个参数:
````JS
function errorFunc(...values, lastValue) {} // 不可以
````
箭头函数也支持收集参数的定义方式:
````JS
let getSum = (...values) => {
    return values.reduce((x, y) => x + y, 0);
}
console.log(getSum(1,2,3)); // 6
````
使用收集参数并不影响`arguments`对象,它仍然反映调用时传给函数的参数:
````JS
function getSum(...values) {
    console.log(arguments.length);  // 3
    console.log(arguments[1]);      // 2
    console.log(values);            // [1,2,3]
}
console.log(getSum(1,2,3));
````

## 函数声明与函数表达式
对于函数声明,JS引擎会在代码执行之前先扫描一遍,并将函数声明提升到源代码树的顶部,这个过程叫做`函数声明提升`:
````JS
console.log(sum(10, 10));   // 没问题
function sum(num1, num2) {
    return num1 + num2;
}
````
而函数表达式则是在代码执行到那一行时,才会生成函数定义(即使是使用`var`定义也是如此):
````JS
console.log(sum(10, 10));   // 出错
var sum = function(num1, num2) {
    return num1 + num2;
};
````
除了上述区别以外,函数声明和函数表达式等价.

此外,对于代码
````JS
if (condition) {
    function sayHi() {
        console.log('Hi');
    }
} else {
    function sayHi() {
        console.log('Hello');
    }
}
````
不是有效的语法,会导致在不同的浏览器上出现不同的行为.应该修改为:
````JS
let sayHi;
if (condition) {
    sayHi = function() {
        console.log('Hi');
    }
} else {
    function sayHi() {
        console.log('Hello');
    }
}
````

## 函数作为值
函数名就是变量,所以函数可以用在任何可以使用变量的地方,比如作为函数的参数或者函数的返回值:
````JS
function callFunc(Func, Argument) {
    return Func(Argument);
}
function add10(num) {
    return num + 10;
}
console.log(callFunc(add10, 10));   // 20
````
````JS
function comp(property) {
    return function(obj1, obj2) {
        let value1 = obj1[property];
        let value2 = obj2[property];
        if (value1 < value2) return -1;
        else if (value1 > value2) return 1;
        else return 0;
    };
}
let data = [{name: "aaa", age: 28}, {name: "bbb", age: 27}];
data.sort(comp("name"));
console.log(data);      // [{name: 'aaa', age: 28}, {name: 'bbb', age: 27}]
data.sort(comp("age"));
console.log(data);      // [{name: 'bbb', age: 27}, {name: 'aaa', age: 28}]
````

## 函数内部
### arguments

**已弃用.请不要在新的网站中使用.**

`arguments`是一个类数组对象,包含调用函数时传入的所有参数.这个对象只有以`function`关键字定义函数时才会有.主要包含调用函数时传入的所有参数以及一个`callee`属性,指向`arguments`对象所在函数的指针:
````JS
function factorial(num) {
    if (num <= 1) {
        return 1;
    } else {
        return num * arguments.callee(num - 1);
    }
}
````
这样做,使得函数逻辑与函数名解耦.

*在严格模式下访问`arguments.callee`会报错.*

### this
`this`在标准函数和箭头函数中有不同的行为.

标准函数中,`this`引用的时把函数当成方法调用的上下文对象(在全局上下文中`this`指向全局上下文对象,网页中是`window`):
````JS
window.color = 'red';   // window是网页全局上下文
let o = {
    color: 'blue'
};
function sayColor() {
    console.log(this.color);
}
sayColor();     // red
// this指向window
o.sayColor = sayColor;
o.sayColor();   // blue
// this指向o
````
在箭头函数中,`this`引用的是定义箭头函数的上下文:
````JS
window.color = 'red';
let o = {
    color: 'blue'
};
let sayColor = () => console.log(this.color);
sayColor();     // red
// sayColor在全局定义,this指向window
o.sayColor = sayColor;
o.sayColor();   // red
// o的方法sayColor在全局定义,this也指向window
````
这种特性常用于保留定义函数时的上下文.

### caller

**已弃用.请不要在新的网站中使用.**

`caller`是函数对象的属性,这个属性引用的是调用当前函数的函数,如果是在全局作用域中调用的则为`null`:
````JS
function outer() {
    inner();
}
function inner() {
    console.log(inner.caller);
}
outer();    // ƒ outer()
````
ES5也定义了`arguments.caller`,但在严格模式下访问它会报错,在非严格模式下始终是`undefined`.这是为了分清`arguments.caller`和函数的`caller`而故意为之.

*严格模式下尝试给函数的`caller`属性赋值会导致错误.*

### new.target
ES6增加了检测函数是否使用`new`关键字调用的`new.target`属性.如果函数是正常调用的,则`new.target`的值是`undefined`,否则`new.target`引用被调用的构造函数:
````JS
function A() {
    if (!new.target) {
        throw "Error";
    }
    console.log('Using new');
}
new A();    // Using new
A();        // Error: Error
````

## 函数属性与方法
ES中函数是对象,因此有属性和方法.每个函数都有两个属性:`length`和`prototype`.

`length`属性保存函数定义的命名参数的个数:
````JS
function sayName(name) {}
function sum(num1, num2) {}
function sayHi() {}
console.log(sayName.length);    // 1
console.log(sum.length);        // 2
console.log(sayHi.length);      // 0
````

其`prototype`内存储了两个属性`constructor`和`[[Prototype]]`.

`[[Prototype]]`就是`Object`,因此函数允许调用`toString()`和`valueOf()`等方法.  
`toLocaleString()`和`toString()`始终返回函数的代码,但返回代码的格式因浏览器而异,因此只应在调试中使用它们.  
`valueOf`返回函数本身.

而`constructor`内包含`arguments`,`caller`,`name`等属性,除此以外还有`[[Prototype]]`属性,其中包含与函数相关的方法.

`apply()`和`call()`这两个方法以指定的`this`值来调用函数,即会设置调用函数时函数体内`this`对象的值.  
`apply()`定义为`func.apply(thisArg, argArray)`,相当于使用`thisArg.func(...argArray)`.其中`argArray`可以是一个`Array`的实例,也可以是`arguments`对象.  
`call()`定义为`func.call(thisArg, ...argArray)`,与`apply()`相同,只不过需要逐个传递参数,而非将参数打包为一个数组.

`apply()`和`call()`可用于控制函数上下文即函数体内`this`值的能力:
````JS
window.color = 'red';
let o = {
    color: 'blue'
};
function sayColor() {
    console.log(this.color);
}
sayColor();             // red
sayColor.call(this);    // red
sayColor.call(window);  // red
sayColor.call(o);       // blue
````
上面这样操作就可以省略`o.sayColor = sayColor;`.

`bind()`方法会创建一个新的函数实例,其`this`值会被绑定到传给`bind()`的对象:
````JS
window.color = 'red';
let o = {
    color: 'blue'
};
function sayColor() {
    console.log(this.color);
}
let objSayColor = sayColor.bind(o);
objSayColor();  // blue
````

## 函数表达式
````JS
let functionName = function(arg0, arg1) {}
console.log(functionName);  // ƒ (arg0, arg1) {}
let AnotherFunc = functionName;
console.log(AnotherFunc);   // ƒ (arg0, arg1) {}
````
上面函数表达式会创建一个`匿名函数`(或`lambda表达式`),这种函数的`name`属性是空字符串.

但允许给函数表达式中的函数一个名称:
````JS
let functionName = function myFunc(arg0, arg1) {}
console.log(functionName);  // ƒ myFunc(arg0, arg1) {}
````

## 递归
一个函数直接或间接调用自身就是`递归`.

使用`arguments.callee`来调用自身可以使调用与函数名解耦合,但*严格模式下不能访问`arguments.callee`*,可以使用命名函数表达式替代:
````JS
const factorial = (function f(num) {
    if (num <= 1) {
        return 1;
    } else {
        return num * f(num - 1);
    }
});
````

## 尾调用优化
ES6允许JS引擎在满足条件时可以重用栈帧.  
此优化非常适合`尾调用`:
````JS
function outerFunc() {
    // some codes here
    return innerFunc(); // 尾调用
}
````
ES6前,上述例子在内存中的操作如下:
1. 执行到`outerFunc`函数体,第一个栈帧被推到栈上.
2. 执行`outerFunc`函数体,到`return`语句,必须先计算`innerFunc`.
3. 执行到`innerFunc`函数体,第二个栈帧被推到栈上.
4. 执行`innerFunc`函数体,计算其返回值.
5. 将返回值传回`outerFunc`,然后`outerFunc`再返回.
6. 将栈帧弹出栈外.

ES6之后,上述例子再内存中的操作如下:
1. 执行到`outerFunc`函数体,第一个栈帧被推到栈上.
2. 执行`outerFunc`函数体,到`return`语句,必须先计算`innerFunc`.
3. 引擎发现把第一个栈帧弹出栈外也没问题,因为`innerFunc`的返回值也是`outerFunc`的返回值.
4. 弹出`outerFunc`的栈帧
5. 执行到`innerFunc`函数体,栈帧被推到栈上.
6. 执行`innerFunc`函数体,计算其返回值.
7. 将`innerFunc`的栈帧弹出栈外.

### 尾调用优化条件
尾调用优化的条件就是确定外部栈帧真的没有必要存在了.涉及的条件如下:
- 代码再严格模式下执行
- 外部函数的返回值时对尾调用函数的调用.
- 尾调用函数返回后不需要执行额外的逻辑.
- 尾调用函数不是引用外部函数作用域中自由变量的闭包.

例如:
````JS
"use strict";
// 无优化,尾调用返回后转型为字符串
function outerFunc() {
    return innerFunc().toString();
}
// 有优化: 初始返回值不涉及栈帧
function outerFunc(a, b) {
    if (a < b) {
        return a;
    }
    return innerFunc(a + b);
}
// 有优化
function outerFunc(condition) {
    return condition ? innerFuncA() : innerFuncB();
}
````
尾调用优化在递归代码中效果是最明显的

### 使用尾调用优化
例如对于递归求斐波那契数列:
````JS
function fib(n) {
    if (n < 2) {
        return n;
    }
    return fib(n - 1) + fib(n - 2);
}
````
上述代码不会被优化.  
而为了能够优化,可以使用如下代码:
````JS
"use strict"
function fib(n) {
    return fibImpl(0, 1, n);
}
function fibImpl(a, b, n) {
    if (n === 0) {
        return a;
    }
    return fibImpl(b, a + b, n - 1);
}
````

## 闭包
`闭包`指的是那些引用了另一个函数作用域中变量的函数,通常是在嵌套函数中实现的.

对于普通函数而言,例如:
````JS
function compare(value1, value2) {
    if (value1 < value2) {
        return -1;
    } else if (value1 > value2) {
        return 1;
    } else {
        return 0;
    }
}
let before = 1;
let result = compare(5, 10);
````
在定义时,对沿着作用域链将函数能够访问的作用域保存在内部的`[[Scope]]`中.此处是函数内部以及全局,其中`[[Scope]]`位于`prototype`中的`constructor`中,其值为:
````JS
Scopes: [Global: {window: Window, ...}]
````
当函数调用时,除了函数本身的活动对象,上例为`value1`,`value2`,`arguments`等,还会搜寻`[[Scope]]`当中的变量.由于此处`[[Scope]]`中的`global`已经定义了`before`,因此可以正常访问该变量,对于`result`,虽然已经定义,但其未被赋值,因此不能使用.

但对于闭包而言,例如:
````JS
function createCompFunc(propertyName) {
    return function(obj1, obj2) {
        let value1 = obj1[propertyName];
        let value2 = obj2[propertyName];
        ...
    };
}
````
其中内部的匿名函数是闭包,闭包即使被`return`并离开了函数的作用域,却仍然能够访问`createCompFunc`函数内的`propertyName`.这是因为在闭包定义时,其`[[Scope]]`包含`createCompFunc`和全局,因此能够访问`propertyName`.此外,闭包还导致了其一直引用`propertyName`导致外函数在执行完毕后不能销毁`propertyName`.*外部函数的活动对象会一直保留直到闭包被销毁*.

上面闭包的`[[Scope]]`包含内容如下:
````JS
Scopes: [Closure (createCompFunc): {propertyName: 'name'}, Global: {window: Window, ...}]
````

### this对象
对于闭包中的`this`,如果使用的不是箭头表达式,则`this`对象会在运行时绑定到执行函数的上下文:
````JS
window.identity = 'The Window';
let o = {
    identity: 'My Object',
    getIdentityFunc() {
        return function() {
            return this.identity;
        };
    }
};
console.log(o.getIdentityFunc()()); // The Window
// 严格模式下全局作用域中的this是undefined
````
````JS
window.identity = 'The Window';
let o = {
    identity: 'My Object',
    getIdentity() {
        return this.identity;
    }
};
o.getIdentity();    // My Object
(o.getIdentity)();  // My Object (规范规定,(o.getIdentity)等价于o.getIdentity)
(o.getIdentity = o.getIdentity)();  // The Window, 赋值后的表达式返回的是函数本身,this不与任何对象绑定
````

### 内存泄漏
> **<b class="red_font">已过时</b>**

对于引用计数来清理内存的JS引擎,闭包可能会导致内存泄漏.可以在使用完闭包后将变量设置为`null`来避免.

## 立即调用的函数表达式
`立即调用的匿名函数`又被称作`立即调用的函数表达式`(IIFE, Immediately Invoked Function Expression).其语法如下:
````JS
(function() {
    // code
})();
````
函数声明被包含在一个括号内,因此会被解释为一个函数表达式,后面的括号会调用该函数.

## 私有变量
> **<b class="yellow_font">注:`私有属性`已在ES2022加入,详见[本笔记-私有属性](#私有属性es2022待补充)</b>**

可以通过局部变量来模拟私有变量,而特权方法是能够访问函数私有变量(及私有函数)的公有方法:
````JS
function MyObject() {   // 或在构造函数中
    let privateVar = 10;
    function privateFunc() {
        return false;
    }
    this.publicMethod = function() {
        ++privateVar;
        return privateFunction();
    }
}
````
````JS
let MyObj;
(function() {
    let privateVar = 10;
    function privateFunc() {
        return false;
    }
    // 构造函数
    MyObject = function() {};
    MyObject.prototype.publicMethod = function() {
        privateVar++;
        return privateFunc();
    };
})();
````
模块模式:
````JS
let singleton = function() {
    let privateVar = 10;
    function privateFunc() {
        return false;
    }
    // 特权/公有方法和属性
    return {
        publicProperty: true,
        publicMethod() {
            privateVar++;
            return privateFunc();
        }
    };
}();
````
模块增强模式:
````JS
let singleton = function() {
    let privateVar = 10;
    function privateFunc() {
        return false;
    }
    let obj = new CustomType();
    obj.publicVar = true;
    obj.publicMethod = function() {
        privateVar++;
        return privateFunc();
    }
    return obj;
}();
````

# 期约与异步函数



