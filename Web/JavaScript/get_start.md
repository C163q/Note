<title>This is a JavaScript note.</title>
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
    - [数组空位](#数组空位)
    - [数组索引](#数组索引)
    - [检测数组](#检测数组)
    - [迭代器方法](#迭代器方法)
    - [复制和填充方法](#复制和填充方法)
    - [转换方法](#转换方法)
    - [栈方法与队列方法](#栈方法与队列方法)
    - [排序方法](#排序方法)
    - [操作方法](#操作方法)
    - [搜索和位置方法](#搜索和位置方法)
      - [严格相等](#严格相等)
      - [断言比较](#断言比较)
    - [迭代方法](#迭代方法)
    - [归并方法](#归并方法)
  - [定型数组](#定型数组)
    - [ArrayBuffer](#arraybuffer)
    - [DataView](#dataview)
      - [ElementType](#elementtype)
      - [字节序](#字节序)
      - [其他](#其他)
    - [定型数组](#定型数组-1)
      - [定型数组行为](#定型数组行为)
      - [合并,复制和修改定型数组](#合并复制和修改定型数组)
      - [上溢和下溢](#上溢和下溢)
  - [Map](#map)
    - [基本API](#基本api)
    - [顺序与迭代](#顺序与迭代)
    - [选择Object还是Map](#选择object还是map)
  - [WeakMap](#weakmap)
    - [基本API](#基本api-1)
    - [弱键](#弱键)
    - [不可迭代键](#不可迭代键)
  - [Set](#set)
    - [基本API](#基本api-2)
    - [顺序与迭代](#顺序与迭代-1)
    - [自定义集合操作](#自定义集合操作)
  - [WeakSet](#weakset)
    - [基本API](#基本api-3)
    - [弱值](#弱值)
    - [不可迭代键](#不可迭代键-1)
  - [迭代与扩展操作](#迭代与扩展操作)
- [迭代器与生成器](#迭代器与生成器)
  - [理解迭代](#理解迭代)
  - [迭代器模式](#迭代器模式)
    - [可迭代协议](#可迭代协议)
    - [迭代器协议](#迭代器协议)
    - [自定义迭代器](#自定义迭代器)
    - [提前终止迭代器](#提前终止迭代器)
  - [生成器](#生成器)
    - [生成器基础](#生成器基础)
    - [通过yield中断执行](#通过yield中断执行)
      - [生成器对象作为可迭代对象](#生成器对象作为可迭代对象)
      - [yield实现输入输出](#yield实现输入输出)
      - [产生可迭代对象](#产生可迭代对象)
      - [yield\*实现递归](#yield实现递归)
    - [生成器作为默认迭代器](#生成器作为默认迭代器)
    - [提前终止生成器](#提前终止生成器)
      - [return()](#return)
      - [throw()](#throw)
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
    - [set()](#set-1)
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
  - [异步编程](#异步编程)
    - [同步与异步](#同步与异步)
    - [以往的异步编程模式](#以往的异步编程模式)
  - [期约](#期约)
    - [Promise/A+规范](#promisea规范)
    - [期约基础](#期约基础)
      - [期约状态机](#期约状态机)
      - [解决值,拒绝理由及期约用例](#解决值拒绝理由及期约用例)
      - [通过执行函数控制期约状态](#通过执行函数控制期约状态)
      - [Promise.resolve()](#promiseresolve)
      - [Promise.reject()](#promisereject)
      - [同步/异步执行的二元性](#同步异步执行的二元性)
    - [期约的实例方法](#期约的实例方法)
      - [实现Thenable接口](#实现thenable接口)
      - [Promise.prototype.then()](#promiseprototypethen)
      - [Promise.prototype.catch()](#promiseprototypecatch)
      - [Promise.prototype.finally()](#promiseprototypefinally)
      - [非重入期约方法](#非重入期约方法)
      - [邻近处理程序的执行顺序](#邻近处理程序的执行顺序)
      - [传递解决值和拒绝理由](#传递解决值和拒绝理由)
      - [拒绝期约与拒绝错误处理](#拒绝期约与拒绝错误处理)
    - [期约连锁与期约合成](#期约连锁与期约合成)
      - [期约连锁](#期约连锁)
      - [期约图](#期约图)
      - [Promise.all()和Promise.race()](#promiseall和promiserace)
      - [串行期约合成](#串行期约合成)
    - [期约扩展](#期约扩展)
      - [期约取消](#期约取消)
      - [期约进度通知](#期约进度通知)
  - [异步函数](#异步函数)
    - [异步函数](#异步函数-1)
      - [async](#async)
      - [await](#await)
      - [await的限制](#await的限制)
    - [停止和恢复执行](#停止和恢复执行)
    - [异步函数策略](#异步函数策略)
      - [实现sleep()](#实现sleep)
      - [利用平行执行](#利用平行执行)
      - [串行执行期约](#串行执行期约)
      - [栈追踪与内存管理](#栈追踪与内存管理)
- [BOM](#bom-1)
  - [window对象](#window对象)
    - [Global作用域](#global作用域)
    - [窗口关系](#窗口关系)
    - [窗口位置与像素比](#窗口位置与像素比)
      - [像素比](#像素比)
    - [窗口大小](#窗口大小)
    - [视口位置](#视口位置)
    - [导航与打开新窗口](#导航与打开新窗口)
      - [弹窗屏蔽程序](#弹窗屏蔽程序)
    - [定时器](#定时器)
    - [系统对话框](#系统对话框)
  - [location对象](#location对象)
    - [查询字符串](#查询字符串)
      - [URLSearchParams](#urlsearchparams)
    - [操作地址](#操作地址)
  - [navigator对象](#navigator对象)
    - [检测插件](#检测插件)
    - [注册处理程序](#注册处理程序)
  - [screen对象](#screen对象)
  - [history对象](#history对象)
    - [导航](#导航)
    - [历史状态管理](#历史状态管理)
- [客户端检测](#客户端检测)
  - [能力检测](#能力检测)
    - [安全能力检测](#安全能力检测)
    - [基于能力检测进行浏览器分析](#基于能力检测进行浏览器分析)
      - [检测特性](#检测特性)
      - [检测浏览器](#检测浏览器)
      - [能力检测的局限](#能力检测的局限)
  - [用户代理检测](#用户代理检测)
    - [浏览器分析](#浏览器分析)
      - [伪造用户代理](#伪造用户代理)
      - [分析浏览器](#分析浏览器)
  - [软件与硬件检测](#软件与硬件检测)
    - [识别浏览器与操作系统](#识别浏览器与操作系统)
    - [浏览器元数据](#浏览器元数据)
      - [Geolocation API](#geolocation-api)
      - [Connection State和NetworkInformation API](#connection-state和networkinformation-api)
      - [Battery Status API](#battery-status-api)
    - [硬件](#硬件)
- [DOM](#dom-1)
  - [节点层级](#节点层级)
    - [Node类型](#node类型)
      - [nodeName于nodeValue](#nodename于nodevalue)
      - [节点关系](#节点关系)
      - [操纵节点](#操纵节点)
      - [其他方法](#其他方法-1)
    - [Document类型](#document类型)
      - [文档子节点](#文档子节点)
      - [文档信息](#文档信息)
      - [定位元素](#定位元素)
      - [特殊集合](#特殊集合)
      - [DOM兼容性检测](#dom兼容性检测)
      - [文档写入](#文档写入)
    - [Element类型](#element类型)
      - [HTML元素](#html元素)
      - [取得属性](#取得属性)
      - [设置属性](#设置属性)
      - [attributes属性](#attributes属性)
      - [创建元素](#创建元素)
      - [元素后代](#元素后代)
    - [Text类型](#text类型)
      - [创建文本节点](#创建文本节点)
      - [规范化文本节点](#规范化文本节点)
      - [拆分文本节点](#拆分文本节点)
    - [Comment类型](#comment类型)
    - [CDATASection](#cdatasection)
    - [DocumentType类型](#documenttype类型)
    - [DocumentFragment类型](#documentfragment类型)
    - [Attr类型](#attr类型)
  - [DOM编程](#dom编程)
    - [动态脚本](#动态脚本)
    - [动态样式](#动态样式)
    - [操作表格](#操作表格)
    - [使用NodeList](#使用nodelist)
  - [MutationObserver接口](#mutationobserver接口)
    - [基本用法](#基本用法-1)
      - [observe()方法](#observe方法)
      - [回调与MutationRecord](#回调与mutationrecord)
      - [disconnect()](#disconnect)
      - [复用MutationObserver](#复用mutationobserver)
      - [重用MutationObserver](#重用mutationobserver)
    - [MutationObserverInit与观察返回](#mutationobserverinit与观察返回)
      - [观察属性](#观察属性)
      - [观察字符数据](#观察字符数据)
      - [观察子节点](#观察子节点)
      - [观察子树](#观察子树)
    - [异步回调与记录队列](#异步回调与记录队列)
      - [记录队列](#记录队列)
      - [takeRecords()方法](#takerecords方法)
    - [性能,内存与垃圾回收](#性能内存与垃圾回收)
      - [MutationObserver的引用](#mutationobserver的引用)
      - [MutationRecord的引用](#mutationrecord的引用)
- [DOM扩展](#dom扩展)
  - [Selectors API](#selectors-api)
    - [querySelector()](#queryselector)
    - [querySelectorAll()](#queryselectorall)
    - [matches()](#matches)
  - [元素遍历](#元素遍历)
  - [HTML5](#html5)
    - [CSS类扩展](#css类扩展)
      - [getElementsByClassName()](#getelementsbyclassname)
      - [classList属性](#classlist属性)
    - [焦点管理](#焦点管理)
    - [HTMLDocument扩展](#htmldocument扩展)
      - [readyState属性](#readystate属性)
      - [compatMode属性](#compatmode属性)
      - [head属性](#head属性)
    - [字符集属性](#字符集属性)
    - [自定义数据属性](#自定义数据属性)
    - [插入标记](#插入标记)
      - [innerHTML属性](#innerhtml属性)
      - [outerHTML](#outerhtml)
      - [insertAdjacentHTML()与insertAdjacentText()](#insertadjacenthtml与insertadjacenttext)
      - [内存与性能问题](#内存与性能问题)
      - [跨站点脚本](#跨站点脚本)
    - [scrollIntoView()](#scrollintoview)
  - [专有扩展](#专有扩展)

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
*本章所给出的类型只需要知道其存在,具体API可以查看文档.*

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

使用`from()`静态方法将类数组结构转换为数组实例.其第一个参数可以是任何可迭代的结构,或者由有一个`length`属性和可索引元素的结构:
````JS
console.log(Array.from("Matt"));    // ['M', 'a', 't', 't']
console.log(Array.from(new Map().set(1,2)
                                .set(3,4)));    // [[1,2],[3,4]]
console.log(Array.from(new Set().add(1)
                                .add(2)
                                .add(3)
                                .add(4)));  // [1,2,3,4]
// Array.from()对现有数组执行浅复制
const a1 = [1,2,3,4];
const a2 = Array.from(a1);
console.log(a2);    // [1,2,3,4]
console.log(a1 === a2); // false

const iter = {
    *[Symbol.iterator]() {
        yield 1;
        yield 2;
        yield 3;
        yield 4;
    }
};
console.log(Array.from(iter));  // [1,2,3,4]
const arrayLikeObj = {
    0: 1,
    1: 2,
    2: 3,
    3: 4,
    length: 4
};
console.log(Array.from(arrayLikeObj));  // [1,2,3,4]
````
`Array.from()`接受第二个可选的映射函数参数,该映射函数会应用于数组中的每一项数据.还可以接收第三个可选参数,用于指定映射函数中`this`的值.但这个重写的`this`值在箭头函数中不适用.
````JS
const a1 = [1,2,3,4];
const a2 = Array.from(a1, x => x**2);
const a3 = Array.from(a1, function(x) { return x**this.exponent }, {exponent: 2});
console.log(a2);    // [1,4,9,16]
console.log(a3);    // [1,4,9,16]
````

`Array.of()`将一组参数转换为数组:
````JS
console.log(Array.of(1,2,3,4)); // [1,2,3,4]
console.log(Array.of(undefined));   // [undefined]
````

### 数组空位
使用字面量初始化数组时,可以使用一串逗号来创建空位.ES6新增的方法和迭代器几乎都把空位当成存在的元素,且为`undefined`;而ES6之前的方法则会忽略空位.**因此建议避免使用数组空位,或者显式地使用undefined值代替**.
````JS
const a1 = [,,,,,];
console.log(a1.length); // 5
console.log(a1);    // [空 ×5]
const a2 = [,,,,1,];
console.log(a2.length); // 5
const a3 = [1,,,,2];
console.log(a3.length); // 5
const a4 = [,1,,2,3,];
console.log(a4.length); // 5
console.log(a4);    // [空, 1, 空, 2, 3]
````
````JS
// 迭代
const options = [1,,,,5];
for (const option of options) {
    console.log(option === undefined);
}
// false
// true
// true
// true
// false

// ES6之后的方法
const a = Array.from([,,,]);
console.log(Array.of(...[,,,]));    // [undefined, undefined, undefined]
// ES6之前的方法
const arr = [1,,,,5];
// map()会跳过空位置而不将其设置为6
console.log(arr.map(() => 6));  // [6, 空 ×3, 6]
````

### 数组索引
使用中括号来提供数字索引:
````JS
let colors = ['red', 'blue', 'green'];
console.log(colors[0]);     // 显式第一项,red
colors[2] = 'black';        // 修改'green'为'black'
colors[3] = 'brown';        // 第四项不存在,因此添加第四项
console.log(colors);        // ['red', 'blue', 'black', 'brown']
````

`length`表示数组长度:
````JS
let colors = ['red', 'blue', 'green'];
let names = [];
console.log(colors.length); // 3
console.log(names.length);  // 0
````

可以修改`length`来删除或扩充元素:
````JS
let arr = [1,2,3,4];
arr.length = 3; // 删除了末尾的4
console.log(arr[3]);    // undefined
arr.length = 4; // 将数组从3个元素扩充到了4个
console.log(arr);       // [1, 2, 3, 空]
arr[arr.length] = arr.length;
console.log(arr);       // [1, 2, 3, 空, 4]
console.log(arr.length);    // 5
arr[100] = 5;
console.log(arr[99]);   // undefined
console.log(arr.length);    // 101
````

数组最多可以包含`2^32-1`个元素.

### 检测数组
单个网页中,使用`value instanceof Array`可以判断一个对象是不是数组.

但如果网页中有多个框架,则可能涉及两个不同的全局执行上下文,因此就会有两个不同版本的`Array`构造函数.使用`isArray()`静态方法可以忽略执行上下文确定一个值是否为数组:
````JS
if (Array.isArray(value)) {}
````

### 迭代器方法
`Array`的原型上暴露了3个用于检索数组内容的方法:`keys()`,`values()`和`entries()`.

`keys()`返回数组索引的迭代器,`values()`返回数组元素的迭代器,`entries()`返回索引/值对的迭代器:
````JS
const a = ['foo', 'bar', 'baz', 'qux'];
const aKeys = Array.from(a.keys());
const aValues = Array.from(a.values());
const aEntries = Array.from(a.entries());
console.log(aKeys);     // [0, 1, 2, 3]
console.log(aValues);   // ['foo', 'bar', 'baz', 'qux']
console.log(aEntries);  // [[0, 'foo'], [1, 'bar'], [2, 'baz'], [3, 'qux']]
console.log(a.keys());  // Array Iterator {...}
for (const [idx, element] of a.entries()) {
    console.log(idx);
}
// 0
// 1
// 2
// 3
````

### 复制和填充方法
批量复制方法`copyWithin()`和填充数组方法`fill()`都需要指定一个左闭右开的区间.这两个方法不会改变数组的大小.

`fill()`方法项一个已有的数组中插入全部或部分相同的值.第一个参数是填充值.第二个参数是开始索引,默认值是`0`.第三个参数是结束索引(不包括),默认值是`length`.索引为负值表示从末尾开始计算.超出数组边界,零长度,方向相反的索引范围都会被忽略:
````JS
const arr = [0,0,0,0,0];
arr.fill(5, 2, -1);
console.log(arr);   // [0, 0, 5, 5, 0]
arr.fill(0);
arr.fill(1, 2, 10); // [2,5)没有超出索引范围
console.log(arr);   // [0, 0, 1, 1, 1]
arr.fill(3, -10, 0);    // 忽略
````

`copyWithin()`会按照指定范围浅复制数组中的部分内容,然后替换(插入)指定开始索引的位置.索引的计算方法同`fill()`:
````JS
let ints,
    reset = () => ints = [0,1,2,3,4,5,6,7,8,9];
reset();
// 第一个参数是插入的索引
ints.copyWithin(5);
console.log(ints);  // [0,1,2,3,4,0,1,2,3,4]
reset();

// 第二个参数是复制索引开始的位置.默认为0
ints.copyWithin(0, 5);
console.log(ints);  // [5,6,7,8,9,5,6,7,8,9]
reset();

// 第三个参数是复制索引结束的位置.默认为length
ints.copyWithin(4, 0, 3);
console.log(ints);  // [0,1,2,3,0,1,2,7,8,9]
````

### 转换方法
`valueOf()`返回数组本身.`toString()`返回数组中每个元素调用`toString()`的返回值并用`,`拼接返回的字符串.`toLocaleString()`则是调用每个元素的`toLocaleString()`方法.若数组中某一项为`null`或`undefined`,则上述3个方法和`join()`方法调用后,该项的位置为空字符串.
````JS
let colors = ["red", "blue", "green"];
console.log(colors.toString()); // red,blue,green
console.log(colors.valueOf());  // ["red", "blue", "green"]
console.log(colors);            // ["red", "blue", "green"]
````

使用`join()`方法传入一个分隔的字符串(默认为`,`),返回数组中每个元素调用`toString()`的返回值并用所给值拼接:
````JS
let colors = ["red", "blue", "green"];
console.log(colors.join("||")); // red||blue||green
````

### 栈方法与队列方法
数组提供了`push()`(在数组末尾添加任意多个元素,返回数组长度)和`pop()`(弹出并返回最后一个元素)方法,以实现类似栈的行为.

使用`push()`和`shift()`(弹出并返回第一个元素)方法,以实现类似队列的行为.

`unshift()`方法允许在数组开头添加任意多个值,然后返回新的数组长度:
````JS
let colors = ["red", "blue", "green"];
let count = colors.push("black", "yellow");
console.log(count);             // 5
console.log(colors.pop());      // yellow
console.log(colors.shift());    // red
count = colors.unshift("grey", "white");
console.log(count);             // 5
console.log(colors);            // ['grey', 'white', 'blue', 'green', 'black']
````

### 排序方法
`reverse()`方法将数组元素逆序:
````JS
let nums = [2,5,1,7,3];
nums.reverse();
console.log(nums);  // [3, 7, 1, 5, 2]
````

`sort()`方法默认将数组元素**调用String()转型函数之后**,按照升序排列.
````JS
let values = [0,1,5,10,15];
values.sort();
console.log(values);
````
`sort()`方法可以接收一个比较函数,该情况下`sort()`不使用`String()`方法.比较函数中,传入两个参数,`负值`表示小于,`0`表示相等,`正值`表示大于.(也可以不遵循这种条件以实现降序排列)
````JS
function compare(value1, value2) {
    // return value1 - value2;
    if (value1 < value2) {
        return -1;
    } else if (value1 > value2) {
        return 1;
    } else {
        return 0;
    }
}
let values = [10,5,1,15,0];
values.sort(compare);
console.log(values);    // [0, 1, 5, 10, 15]
````

`reverse()`和`sort()`都返回调用它们的数组的引用.

### 操作方法
`concat()`方法创建一个原数组的拷贝(元素浅复制)并将实参拼接到其末尾(如果是数组),或添加到其末尾(如果不是数组):
````JS
let colors = ["red", "green", "blue"];
let colors2 = colors.concat("yellow", ["black", "brown"]);
console.log(colors);    // ["red", "green", "blue"]
console.log(colors2);   // ["red", "green", "blue", "yellow", "black", "brown"]
````
详见[符号-Symbol.isConcatSpreadable](#symbolisconcatspreadable)

`slice()`用于创建一个包含原有数组中一个或多个元素的新数组.该操作不影响原始数组.

第一个参数是开始索引,第二个参数是结束索引(默认为`length`)(不包含).索引为负值表示从末尾开始计算.超出数组边界,零长度,方向相反索引返回空数组.
````JS
let colors = ["red", "green", "blue", "yellow", "black", "brown"];
let colors2 = colors.slice(1, 4);
console.log(colors2);   // ['green', 'blue', 'yellow']
````

`splice()`:
- 删除.传入两个参数表示要删除的元素索引开始的位置和要删除的元素数量.
- 替换.传入多于2个参数时,前两个参数表示要删除的元素索引开始的位置和要删除的元素数量.后面的参数表示要再删除处重新插入的元素.

该方法返回一个数组,包含从数组中删除的元素.如果没有删除元素,则返回空数组.
````JS
let colors = ["red", "green", "blue"];
let removed = colors.splice(0, 1);
console.log(colors);    // ['green', 'blue']
console.log(removed);   // ['red']

removed = colors.splice(1, 0, "yellow", "orange");
console.log(colors);    // ['green', 'yellow', 'orange', 'blue']
console.log(removed);   // []

removed = colors.splice(1, 1, "red", "purple");
console.log(colors);    // ['green', 'red', 'purple', 'orange', 'blue']
console.log(removed);   // ['yellow']
````

### 搜索和位置方法
ES有两类搜索数组的方法:
- 按严格相等搜索
- 按断言函数搜索

#### 严格相等
`indexOf`接收两个参数:要查找的元素和可选的起始搜索位置.

`indexOf`从前向后搜索,返回要查找的元素在数组中的位置.如果没找到则返回`-1`.

`lastIndexOf()`接收两个参数:要查找的元素和可选的起始搜索位置.

`lastIndexOf()`从后向前搜索,返回要查找的元素在数组中的位置.如果没找到则返回`-1`.

`includes()`接收两个参数:要查找的元素和可选的起始搜索位置.

`includes()`从前向后搜索,返回布尔值,表示是否至少找到一个与指定元素匹配的项.

上面三个方法在比较每一项时,都会使用全等(`===`)比较.

#### 断言比较
断言函数接收3个参数:元素(数组中当前元素),索引(数组的当前索引)和数组本身.断言函数返回布尔值,表示是否匹配.

`find()`和`findIndex()`方法使用了断言函数作为第一个参数.这两个方法都从数组的最小索引开始.`find()`返回第一个匹配的元素,`findIndex()`返回第一个匹配元素的索引.可选的第二个参数用于指定断言函数内部`this`的值.

````JS
const people = [10, 20, 50, 25, 80];
console.log(people.find((element, index, array) => element >= 25 && element <= 35));    // 25
````

### 迭代方法
ES为数组定义了5个迭代方法.每个方法接收两个参数:以每一项为参数运行的函数和可选的作为函数运行上下文的作用域对象(this).传给方法的函数接收3个参数:数组元素,元素索引和数组本身.

- `every()`:对数组每一项都运行传入的函数,如果对每一项函数都返回`true`,则这个方法返回`true`.
- `filter()`:对数组每一项都运行传入的函数,函数返回`true`的项会组成数组之后返回.
- `forEach()`:对数组每一项都运行传入的函数,没有返回值.
- `map()`:对数组每一项都运行传入的函数,返回由每次函数调用的结构构成的数组.
- `some()`:对数组每一项都运行传入的函数,如果有一项函数返回`true`,则这个方法返回`true`.

这些方法都不改变调用它们的数组.

### 归并方法
`reduce()`和`reduceRight()`方法会迭代数组的所有项,并在此基础上构建一个最终返回值.`reduce()`方法从数组第一项开始遍历到最后一项.`reduceRight()`从最后一项开始遍历至第一项.

这两个方法接收两个参数:对每一项都会运行的归并函数,以及可选的以之为归并起点的初始值.

归并函数接收4个参数:上一个归并值,当前项,当前索引,数组本身.函数的返回值会作为下一次调用该函数的第一个参数.若调用方法时没有传入第二个参数,则迭代从第二个元素开始,且将第一个元素作为调用归并函数的第一实参.否则,迭代从第一个元素开始,且将方法的第二实参作为归并函数的第一实参.

## 定型数组
为了让JavaScript提高向底层API(如WebGL)传输数据的效率(不是JS原生的`number`类型(底层是double),而是整型),产生了定型数组.

### ArrayBuffer
`ArrayBuffer`是所有定型数组及视图引用的基本单位,用于管理底层内存.

`SharedArrayBuffer`是`ArrayBuffer`的变体,允许传递`SharedArrayBuffer`的引用而非像`ArrayBuffer`一样需要复制.

构造函数`new ArrayBuffer(size)`在内存中分配`size`字节的空间:
````JS
const buf = new ArrayBuffer(16);    // 在内存中分配16字节的空间
console.log(buf.byteLength);    // 16
````
`ArrayBuffer`一经创建就不能再调整大小.不过可以使用`slice()`复制其全部或部分到一个新实例中:
````JS
const buf1 = new ArrayBuffer(16);
const buf2 = buf1.slice(4, 12);
console.log(buf2.byteLength);   // 8
````

`ArrayBuffer`类似于C++的`::operator new(size)`,但也有不同之处,其行为包括:
- `ArrayBuffer`分配失败时会抛出错误.
- 后者可利用虚拟内存,因此只受可寻址系统内存限制.而`ArrayBuffer`分配的内存不能超过`Number.MAX_SAFE_INTEGER`(2^53-1)字节.
- `ArrayBuffer`会将所有二进制位初始化为0.
- `ArrayBuffer`可以被垃圾回收,不需要手动释放.
- 为了对`ArrayBuffer`的引用读取或写入,就必须通过视图.

**视图**将`ArrayBuffer`中的二进制数据解析为不同类型进行读写.

### DataView
`DataView`视图专为文件IO和网络IO设计,其API支持对缓冲数据的高度控制,但相比于其他类型的视图性能也差一些.`DataView`对缓冲的类型没有任何预设,也不能迭代.

创建实例时需要指定对特定`ArrayBuffer`的引用.
````JS
const buf = new ArrayBuffer(16);
// 第一个参数表示引用的ArrayBuffer
const fullDataView = new DataView(buf);
console.log(fullDataView.byteOffset);       // 0
console.log(fullDataView.byteLength);       // 16
console.log(fullDataView.buffer === buf);   // true
// 第二个参数表示视图的字节偏移量,默认为0
// 第三个参数表示限制视图的字节长度,默认为剩余缓冲
const halfDataView = new DataView(buf, 0, 8);
console.log(halfDataView.byteOffset);       // 0
console.log(halfDataView.byteLength);       // 8
console.log(halfDataView.buffer === buf);   // true
````

使用`byteOffset`属性获得视图相对于引用的`ArrayBuffer`的开始位置.使用`byteLength`属性获取视图可读写的缓冲区的字节数.使用`buffer`属性获取所引用的`ArrayBuffer`.

#### ElementType
由于`DataView`对存储在缓冲内的元素的类型没有预设,因此其强制要求开发者在读写时指定一个`ElementType`.

ES支持的`ElementType`包含:
- `ElemType`    `Byte`  `equivalent type in C++(LLP64)`     `range`
-   `Int8`        1              signed char                -128~127
-  `Uint8`        1             unsigned char                0~255
-  `Int16`        2                 short                 -32768~32767
-  `Uint16`       2             unsigned short              0~65535
-  `Int32`        4                  int             -2147483648~2147483647
-  `Uint32`       4                unsigned               0~4294967295
- `Float32`       4                 float               -3.4e+38~+3.4e+38
- `Float64`       8                 double             -1.7e+308~+1.7e+308

使用`get`和`set`方法并与上述类型组合,以实现对`DataView`的读写.

`set`族方法的第一个参数为字节位移量(考虑元素类型本身字节),第二个参数为写入值,可选的第三个参数为布尔值,用于控制大小端字节序.

`get`族方法的第一个参数为字节位移量(考虑元素类型本身字节),可选的第二个参数为布尔值,用于控制大小端字节序.

例如:
````JS
const buf = new ArrayBuffer(2);
const view = new DataView(buf);
// 获取后8个字节
console.log(view.getInt8(1));   // 0
// 获取整个缓冲(16字节)
console.log(view.getInt16(0));  // 0
view.setUint8(1, 255);  // 0x00FF
// 大端字节序读取16字节
console.log(view.getInt16(0));  // 255
````

#### 字节序
`字节序`指的是计算系统维护的一种字节顺序的约定.`DataView`支持两种约定:`大端字节序`和`小端字节序`.大端字节序将高位放在低地址处.小端字节序将低位放在低地址处.

`DataView`不遵循原生系统的大小端存储规则,而约定:`get`和`set`族方法允许传入一个布尔值(分别为第二个参数和第三个参数)用于控制大小端字节序的读写.默认值为`false`,即大端字节序.传入`true`即可启用小端字节序.
````JS
const buf = new ArrayBuffer(2);
const view = new DataView(buf);
view.setUint8(0, 0x80);
view.setUint8(1, 0x01);
// 0b1000'0000'0000'0001
console.log(view.getUint16(0));         // 32769  0x8001
console.log(view.getUint16(0, true));   // 384    0x0180

view.setUint16(0, 0x0004);
// 0x  0    0    0    4
// 0b 0000 0000 0000 0100
view.setUint16(0, 0x0002, true);
// 0x  0    2    0    0
// 0b 0000 0010 0000 0000
````

#### 其他
`DataView`尝试读写超出或部分超出缓冲区范围的内存时会抛出`RangeError`异常.

对于写入缓冲区内的值,会尽可能转换为适当的类型,后备为`0`.如果无法转换,则抛出错误`TypeError`:
````JS
const buf = new ArrayBuffer(1);
const view = new DataView(buf);

view.setInt8(0, 1.5);   // 1
view.setInt8(0, [4]);   // 4
view.setInt8(0, 'f');   // 0
view.setInt8(0, Symbol());  // TypeError
````

### 定型数组
定型数组也是一种视图,与`DataView`相近,但是它特定于一种`ElementType`且**遵循系统原生的字节序**.定型数组提供了适用面更广的API和更高的性能.JS引擎能够优化其算数运算,按位运算和其他对定型数组的常见操作,因此使用它们速度极快.

定型数组继承于`TypedArray`.

创建定型数组的方法包括读取已有缓冲,填充可迭代结构,填充(基于任意类型的)定型数组,`from()`静态方法和`of()`静态方法:
````JS
const buf = new ArrayBuffer(12);
const ints = new Int32Array(buf, 4, 2); // 第二和第三个参数分别为传入字节偏移量和元素数量(不是字节,而是可容纳元素数)
console.log(ints.length);       // 2
console.log(ints.byteLength);   // 8
console.log(ints.byteOffset);   // 4
console.log(ints.buffer === buf);   // true

const ints2 = new Int32Array(6);    // 会自动创建一个24字节的缓冲
console.log(ints2.buffer instanceof ArrayBuffer);   // true

const ints3 = new Int32Array([2,4,6,8]);    // 会自动创建一个16字节的缓冲
console.log(ints3[2]);  // 6
const ints4 = new Int16Array(ints3);    // 分配8字节的缓冲并将ints3的数据复制给ints4
const ints5 = Int16Array.from([3,5,7,9]);
const floats = Float32Array.of(3.14, 2.718, 1.618);
````

`length`属性返回可容纳元素数,`byteLength`属性返回可容纳字节数,`byteOffset`属性返回可读写的缓冲区的字节数,`buffer`属性返回引用的缓冲.`BYTES_PER_ELEMENT`静态属性返回某类型数组中每个元素占用的字节数.

#### 定型数组行为
定型数组的行为类似普通数组,其支持如下操作符,方法和属性:
- `[]`
- `copyWithin()`
- `entries()`
- `every()`
- `fill()`
- `filter()`
- `find()`
- `findIndex()`
- `forEach()`
- `indexOf()`
- `join()`
- `keys()`
- `lastIndexOf()`
- `length`
- `map()`
- `reduce()`
- `reduceRight()`
- `reverse()`
- `slice()`
- `some()`
- `sort()`
- `toLocaleString()`
- `toString()`
- `values()`

其中,返回新数组的方法也会返回包含同样元素类型的新定型数组:
````JS
const ints = new Int16Array([1,2,3]);
const doubleInts = ints.map(x => 2*x);
console.log(doubleInts instanceof Int16Array);  // true
````

定型数组拥有`Symbol.iterator`符号属性:
````JS
const ints = new Int16Array([1,2,3]);
for (const num of ints) {
    console.log(num);
}
// 1
// 2
// 3
````

#### 合并,复制和修改定型数组
定型数组使用数组缓冲来存储数据,因此无法调整大小.

以下方法不适用于定型数组:
- `concat()`
- `pop()`
- `push()`
- `shift()`
- `splice()`
- `unshift()`

使用`set()`方法将提供的数组或定型数组中的值复制到当前定型数组的指定索引位置:
````JS
const container = new Int16Array(8);
container.set(Int8Array.of(1,2,3,4));
console.log(container); // [1, 2, 3, 4, 0, 0, 0, 0]
container.set([5,6,7,8], 4);
console.log(container); // [1, 2, 3, 4, 5, 6, 7, 8]
// 超过或部分超过索引范围会抛出错误
container.set([5,6,7,8], 7);    // RangeError
````

`subarray()`基于原始定型数组中复制的值返回一个新的定型数组.复制时开始索引和结束索引是可选的,左闭右开:
````JS
const source = Int16Array.of(2,4,6,8);
const fullCopy = source.subarray();
console.log(fullCopy);  // [2, 4, 6, 8]
const partialCopy = source.subarray(1, 3);
console.log(partialCopy);   // [4, 6]
````

定型数组没有原生的拼接能力,但可以手动构建:
````JS
// 第一个参数是应该返回的数组类型
// 其余参数是应该拼接在一起的定型数组
function typedArrayConcat(typedArrayConstructor, ...typedArrays) {
    const numElements = typedArrays.reduce((x, y) => (x.length || x) + y.length);
    const resultArray = new typedArrayConstructor(numElements);
    let currentOffset = 0;
    typedArray.map(x => {
        resultArray.set(x, currentOffset);
        currentOffset += x.length;
    });
    return resultArray;
}
const concatArray = typedArrayConcat(Int32Array,
                                     Int8Array.of(1,2,3),
                                     Int16Array.of(4,5,6),
                                     Float32Array.of(7,8,9));
console.log(concatArray);   // [1, 2, 3, 4, 5, 6, 7, 8, 9]
console.log(concatArray instanceof Int32Array); // true
````

#### 上溢和下溢
定型数组会有类似于C语言数组中元素的上溢和下溢行为:
````JS
const ints = new Int8Array(2);
ints[1] = 255;
console.log(ints);  // [0, -1]
````

`Uint8ClampedArray`不允许任何方向溢出.超出最大值255的值会向下舍入为255,而小于最小值0的值会被向上舍入为0.

> `Uint8ClampedArray`完全是HTML5`canvas`元素的历史留存.除非真的做跟`canvas`相关的开发,否则不要使用它.
> <p style="text-align: right"> -- Brendan Eich</p>

## Map
`Object`也可以作为键值对的存储容器,但`Map`的特性实现了真正的键值存储机制.

### 基本API
默认构造可以创建一个空映射:
````JS
const m = new Map();
````
传入可迭代对象,并将包含键值对的数组作为元素可以在构造时将可迭代对象中的每个键值对依次插入到新映射中:
````JS
const m1 = new Map([
    ["key1", "value1"],
    ["key2", "value2"],
    ["key3", "value3"]
]);
console.log(m1.size);   // 3
const m2 = new Map({
    [Symbol.iterator]: function*() {
        yield ["key1", "value1"],
        yield ["key2", "value2"],
        yield ["key3", "value3"],
    }
});
console.log(m2.size);   // 3
// 若可迭代元素内的包含键值对的数组是空,仍然会被解析为undefined: undefined
const m3 = new Map([ [] ]);
console.log(m3.has(undefined)); // true
````

- `set()`方法可以添加或更新一个指定的键值对.
- `get()`方法可以获取对应键的值(若为对象,则为其引用).如果无所给键,返回`undefined`.
- `has()`方法查询是否存在指定键.
- `delete()`方法删除指定键(与值).
- `clear()`方法删除所有键值对.

````JS
const m = new Map();
console.log(m.has("fn"));   // false
console.log(m.get("fn"));   // undefined
console.log(m.size);        // 0
m.set("fn", "aaa").
  set("ln", "bbb")          // set()方法返回实例本身,因此支持这种写法
console.log(m.has("fn"));   // true
console.log(m.get("fn"));   // aaa
console.log(m.size);        // 2
m.delete("fn");
console.log(m.has("fn"));   // false
console.log(m.has("ln"));   // true
console.log(m.size);        // 1
m.clear();
console.log(m.size);        // 0
````

`Object`只能使用数值,字符串或符号作为键,但`Map`可以使用任何JS数据类型作为键.`Map`内部使用`SameValueZero`比较操作(ES内部定义,语言中不能使用),大体相当于使用严格对象相等的标准检查键的匹配性.映射的值也没有限制.

集合的键若是对象,则其依然是引用,外部对其的修改并不会影响键值对的映射关系:
````JS
const m = new Map();
const objKey = {},
      objVal = {},
      arrKey = [],
      arrVal = [];
m.set(objKey, objVal);
m.set(arrKey, arrVal);
objKey.foo = "foo";
objVal.bar = "bar";
arrKey.push("foo");
arrVal.push("bar");
console.log(m.get(objKey)); // {bar: "bar"}
console.log(m.get(arrKey)); // ["bar"]
console.log(m.has([]));     // false
console.log(m.has(["foo"]));// false
````

`SameValueZero`中`NaN`和`NaN`,`+0`和`-0`被认为是相等的.

详见[MDN-JavaScript 中的相等性判断](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Equality_comparisons_and_sameness)

### 顺序与迭代
`Map`实例会维护键值对的插入顺序,因此可以根据插入顺序执行迭代操作.

使用`Symbol.iterator`属性或者`entries()`方法(前者引用后者)可以获取`Map`的迭代器,迭代器会以插入的顺序输出`[key, value]`形式的数组:
````JS
const m = new Map([
    ["key1", "val1"],
    ["key2", "val2"],
    ["key3", "val3"]
]);
console.log(m.entries === m[Symbol.iterator]);  // true
for (let pair of m.entries()) {
    console.log(pair);
}
// [key1, val1]
// [key2, val2]
// [key3, val3]
````

扩展操作符`...`能把`Map`转换为数组:
````JS
const m = new Map([
    ["key1", "val1"],
    ["key2", "val2"],
    ["key3", "val3"]
]);
console.log([...m]);    // [[key1, val1], [key2, val2], [key3, val3]]
````

`forEach(callback, opt_thisArg)`的回调函数接收两个参数`val`和`key`(`forEach`可选的第二参数为回调函数的`this`值):
````JS
const m = new Map([
    ["key1", "val1"],
    ["key2", "val2"],
    ["key3", "val3"]
]);
m.forEach((val, key) => console.log(`${key} -> ${val}`));
// key1 -> val1
// key2 -> val2
// key3 -> val3
````

`keys()`和`values()`分别返回以插入顺序生成键和值的迭代器.

键和值在迭代器遍历时是可以修改的,但无法将键绑定为其他对象,只能修改其属性.

### 选择Object还是Map
1. 内存占用: `Object`和`Map`对内存的分配取决于实现,但`Map`所占内存小于`Object`.
2. 插入性能: `Map`一般会比`Object`稍快一些.
3. 查找速度: 大型的`Object`和`Map`中查找键值对的性能差异极小,但如果只包含少量键值对,则`Object`有时速度更快,因为浏览器可以对作为数组使用的`Object`进行布局优化,而`Map`不行.
4. 删除性能: `Map`的`delete()`操作远快于对`Object`属性的`delete`.

## WeakMap
`WeakMap`的API是`Map`的子集.

### 基本API
默认构造创建一个空的`WeakMap`:
````JS
const wm = new WeakMap();
````
弱映射中的键只能是`Object`或者继承自`Object`的类型,尝试使用非对象设置键会抛出`TypeError`.值的类型没有限制.

类似`Map`,传入可迭代对象,并将包含键值对的数组作为元素可以在构造时将可迭代对象中的每个键值对依次插入到新实例中:
````JS
const key1 = {id: 1},
      key2 = {id: 2},
      key3 = {id: 3};
const wm1 = new WeakMap([
    [key1, "val1"],
    [key2, "val2"],
    [key3, "val3"]
]);
console.log(wm1.get(key1)); // val1
console.log(wm1.get(key2)); // val2
console.log(wm1.get(key3)); // val3
// 初始化是全有或全无的操作,只要有一个键无效就会抛出错误,导致整个初始化失败
const wm2 = new WeakMap([
    [key1, "val1"],
    ["BADKEY", "val2"],
    [key3, "val3"]
]);
// TypeError: Invalid value used as WeakMap key
typeof wm2; // ReferenceError: wm2 is not defined
const stringKey = new String("key1");   // 原始值可以先包装成对象再用作键
const wm3 = new WeakMap([
    [stringKey, "val"]
]);
console.log(wm3.get(stringKey));
````

- `set()`方法可以添加或更新一个指定的键值对.
- `get()`方法可以获取对应键的值(若为对象,则为其引用).如果无所给键,返回`undefined`.
- `has()`方法查询是否存在指定键.
- `delete()`方法删除指定键(与值).

### 弱键
所谓弱键,描述的是引用而不拥有,即虽然键引用了一个对象,但不会影响其垃圾回收.值则是引用且拥有.

对于弱键,一旦失去其它对对象的引用,则该键会被垃圾回收:
````JS
const wm = new WeakMap();
wm.set({}, "val");  // {}会被垃圾回收
````

### 不可迭代键
`WeakMap`无法迭代其键值对.

## Set
Set对象允许你存储任何类型的**唯一值**.

### 基本API
默认构造可以创建一个空集合:
````JS
const s = new Set();
````
要在创建的同时初始化实例,可以给Set构造函数传入一个可迭代对象,其中包含插入到新集合实例中的元素:
````JS
const s1 = new Set(["val1", "val2", "val3"]);
console.log(s1.size);   // 3
const s2 = new Set({
    [Symbol.iterator]: function*() {
        yield "val1";
        yield "val2";
        yield "val3";
    }
});
console.log(s2.size);   // 3
````

- `add()`方法用于插入一个新元素.
- `has()`方法用于查询是否存在某一元素.
- `size`属性取得元素数量.
- `delete()`删除指定元素.成功删除返回`true`,否则返回`false`.
- `clear()`删除所有元素.

````JS
const s = new Set().add("ccc");     // 构造函数返回对象本身,add()也返回集合本身,因此可以这么做
console.log(s.has("aaa"));  // false
console.log(s.size);        // 1
s.add("aaa").
  add("bbb");   // add()返回集合本身,所有可以将多个添加操作连缀起来
console.log(s.has("aaa"));  // true
console.log(s.size);        // 3
s.delete("aaa");
console.log(s.has("aaa"));  // false
console.log(s.has("bbb"));  // true
console.log(s.size);        // 2
s.clear();
console.log(s.size);        // 0
````

`Set`可以包含任何JS数据类型作为值.集合也使用`SameValueZero`操作(ES内部定义,无法在语言中使用).

若元素为对象,则其在`Set`持有其引用.外部的修改能影响其内部,但不会影响对其的查找.

### 顺序与迭代
`Set`会维护值插入时的顺序,因此按插入顺序迭代.

可以使用`value()`或`keys()`或`Symbol.iterator`(其引用`values()`)来获取迭代器:
````JS
const s = new Set(["val1", "val2", "val3"]);
console.log(s.value === s[Symbol.iterator]);    // true
console.log(s.keys === s[Symbol.iterator]);     // true
for (let value of s.values()) {
    console.log(value);
}
// val1
// val2
// val3
````

可以对集合使用`...`(扩展操作符),把集合转换为数组:
````JS
const s = new Set(["val1", "val2", "val3"]);
console.log([...s]);    // ["val1", "val2", "val3"]
````

集合的`entries()`方法返回一个迭代器,可以按照插入顺序返回包含键值对的数组,对于集合来说,键和值相同.
````JS
const s = new Set(["val1", "val2", "val3"]);
for (let pair of s.entries()) {
    console.log(pair);
}
// ["val1", "val1"]
// ["val2", "val2"]
// ["val3", "val3"]
````

`forEach(callback, opt_thisArg)`的回调函数接收两个参数`val`和`dupVal`,这两个参数值相同(`forEach`可选的第二参数为回调函数的`this`值):
````JS
const s = new Set(["val1", "val2", "val3"]);
s.forEach((val, dupVal) => console.log(`${val} -> ${dupVal}`));
// val1 -> val1
// val2 -> val2
// val3 -> val3
````

### 自定义集合操作
`Set`的很多与集合相关的操作需要手动去实现,实现时,要考虑到:
- 某些`Set`操作是可交换的,这些方法最好能支持处理任意多个集合实例.
- `Set`保留插入顺序,所有方法返回的集合必须保证顺序.
- 尽可能高效地使用内存.扩展操作符语法简洁,但应尽可能避免集合和数组间的相互转换能够节省对象初始化成本.
- 不要修改已有的集合实例.`union(a,b)`或`a.union(b)`应该返回包含结果的新集合实例.
- 在定义集合相关的函数库时,可以考虑定义为集合的静态方法.

````JS
class XSet extends Set {
    union(...sets) {
        return XSet.union(this, ...sets);
    }
    intersection(...sets) {
        return XSet.intersection(this, ...sets);
    }
    difference(set) {
        return XSet.difference(this, set);
    }
    symmetricDifference(set) {
        return XSet.symmetricDifference(this, set);
    }
    cartesianProduct(set) {
        return XSet.cartesianProduct(this, set);
    }
    powerSet() {
        return XSet.powerSet(this);
    }
    // 并集
    static union(a, ...bSets) {
        const unionSet = new XSet(a);
        for (const b of bSets) {
            for (const b of bSets) {
                for (const bValue of b) {
                    unionSet.add(bValue);
                }
            }
        }
    }
    // 交集
    static intersection(a, ...bSets) {
        const intersectionSet = new XSet(a);
        for (const aValue of intersectionSet) {
            for (const b of bSets) {
                if (!b.has(aValue)) {
                    intersectionSet.delete(aValue);
                }
            }
        }
        return intersectionSet;
    }
    // 差集
    static difference(a, b) {
        const differenceSet = new XSet(a);
        for (const bValue of b) {
            if (a.has(bValue)) {
                differenceSet.delete(bValue);
            }
        }
        return differenceSet;
    }
    // 对称差
    static symmetricDifference(a, b) {
        return a.union(b).difference(a.intersection(b));
    }
    // 笛卡尔积
    static cartesianProduct(a, b) {
        const cartesianProductSet = new XSet();
        for (const aValue of a) {
            for (const bValue of b) {
                cartesianProductSet.add([aValue, bValue]);
            }
        }
        return cartesianProductSet;
    }
    // 幂集
    static powerSet(a) {
        const powerSet = new XSet().add(new XSet());
        for (const aValue of a) {
            for (const set of new XSet(powerSet)) {
                powerSet.add(new XSet(set).add(aValue));
            }
        }
        return powerSet;
    }
}
````

## WeakSet
`WeakSet`的API是`Set`的子集.

### 基本API
默认构造创建一个空的`WeakSet`:
````JS
const ws = new WeakSet();
````

弱集合只能存储`Object`或者继承自`Object`的类型,尝试使用非对象值会抛出`TypeError`.

要在初始化时填充弱集合,则给构造函数传入一个可迭代对象:
````JS
const val1 = {id: 1},
      val2 = {id: 2},
      val3 = {id: 3};
const ws1 = new WeakSet([val1, val2, val3]);
console.log(ws1.has(val1)); // true
console.log(ws1.has(val2)); // true
console.log(ws1.has(val3)); // true
// 初始化只要有一个值无效就会抛出错误,整个初始化无效
const ws2 = new WeakSet([val1, "BADVAL", val3]);    // TypeError
typeof ws2; // ReferenceError
````

- `add()`方法用于插入一个新元素.
- `has()`方法用于查询是否存在某一元素.
- `delete()`删除指定元素.成功删除返回`true`,否则返回`false`.

### 弱值
`WeakSet`的弱值,描述的是引用而不拥有,即虽然值引用了一个对象,但不会影响其垃圾回收.一旦失去其他引用该值的引用,则会执行垃圾回收.

### 不可迭代键
`WeakSet`的值在任何时候都可能被销毁,因此无法迭代其值.

## 迭代与扩展操作
`Array`,`Map`,`Set`,`定型数组`都支持静态方法`of()`和`from()`来创建.

# 迭代器与生成器
## 理解迭代
通过循环遍历有时并不如迭代器遍历理想,原因如下:
- 循环需要事先知道如何使用数据结构.例如对于数组,必须知道使用`[]`才能通过循环遍历.
- 循环顺序并不是数据结构固有的.对于隐式顺序结构,不适合使用循环的方式访问.

## 迭代器模式
迭代器模式描述了一个方案,即可以把有些结构称为"可迭代对象",因为它们实现了正式的`Iterable`接口,而且可以通过迭代器`Iterator`消费.

`迭代器(iterator)`是按需创建的一次性对象,每个迭代器都会关联一个`可迭代对象`,而迭代器会暴露迭代其关联可迭代对象的API.迭代器无序了解与其关联的可迭代对象的结构,只需要知道如何取得连续的值.

### 可迭代协议
实现`Iterable`接口(可迭代接口)要求同时具备两种能力:支持迭代的自我识别能力和创建实现`Iterator`接口对象的能力.对于ES,则意味着必须暴露一个属性作为默认迭代器,且这个属性必须以`Symbol.iterator`作为键.

很多内置类型都实现了`Iterable`接口:
````JS
// Object没有实现迭代器工厂函数
let obj = {};
console.log(obj[Symbol.iterator]);  // undefined
// String实现了迭代器工厂函数
let str = 'abc';
console.log(str[Symbol.iterator]);  // f values() { [native code] }
console.log(str[Symbol.iterator]);  // StringIterator {...}
````

在实际代码中,无序显式调用工厂函数,原生语言特性能够自动兼容接收可迭代对象的任何语言特性:
- `for-of`循环
- 数组解构
- 扩展操作符
- `Array.from()`
- 创建集合
- 创建映射
- `Promise.all()`接收由期约组成的可迭代对象
- `Promise.race()`接收由期约组成的可迭代对象
- `yield*`操作符,在生成器中使用

例如:
````JS
let arr = ['foo', 'bar', 'baz'];
let [a, b, c] = arr;    // 数组解构
let arr2 = [...arr];    // 扩展操作符
````

### 迭代器协议
迭代器API使用`next()`方法在可迭代对象中遍历数据.每次成功调用`next()`,都会返回一个`IteratorResult`对象,其中包含迭代器返回的当前值.`IteratorResult`包含两个属性:`done`和`value`.`done`是一个布尔值,表示是否还可以再次调用`next()`取得下一个值;`value`包含可迭代对象的当前值(`done`为`false`)或者`undefined`(`done`为`true`):
````JS
let arr = ['foo', 'bar'];
console.log(arr[Symbol.iterator]);  // ƒ values() { [native code] }
let iter = arr[Symbol.iterator]();
console.log(iter);          // Array Iterator { ... }
console.log(iter.next());   // { done: false, value: "foo" }
console.log(iter.next());   // { done: false, value: "bar" }
console.log(iter.next());   // { done: true, value: undefined }
// 只要迭代器到达done: true状态,后续调用next()就一直返回同样的值了
console.log(iter.next());   // { done: true, value: undefined }
console.log(iter.next());   // { done: true, value: undefined }
````

不同迭代器之间是独立的.若可迭代对象在迭代器迭代期间被修改了,那么迭代器也可能会发生变化:
````JS
let arr = ['foo', 'bar'];
let iter = arr[Symbol.iterator]();
console.log(iter.next());   // { done: false, value: 'foo' }
arr.splice(1, 0, 'bar');    // 在数组中间插入值
console.log(iter.next());   // { done: false, value: 'bar' }
console.log(iter.next());   // { done: false, value: 'baz' }
console.log(iter.next());   // { done: true, value: undefined }
````

*注意:迭代器维护一个指向可迭代对象的引用,因此迭代器会阻止垃圾回收程序回收可迭代对象.*

### 自定义迭代器
实例:
````JS
class Counter {
    // Counter的实例应该迭代limit次
    constructor(limit) {
        this.count = 1;
        this.limit = limit;
    }
    next() {
        if (this.count <= this.limit) {
            return { done: false, value: this.count++ };
        }
        else {
            return { done: true, value: undefined };
        }
    }
    [Symbol.iterator]() {
        return this;
    }
}
let counter = new Counter(3);
for (let i of counter) {
    console.log(i);
}
// 1
// 2
// 3
for (let i of counter) {
    console.log(i);
}
// <nothing logged>
````
上述`Counter`类本身就是迭代器,因此在迭代一次之后,其就失效了.

使用闭包返回迭代器使`Counter`类与迭代器相分离:  
**(注:我认为现在可以使用含有私有属性的类会更加好一点)**
````JS
class Counter {
    constructor(limit) {
        this.limit = limit;
    }
    [Symbol.iterator]() {
        let count = 1,
            limit = this.limit;
        return {
            next() {
                if (count <= limit) {
                    return { done: false, value: count++ };
                }
                else {
                    return { done: true, value: undefined };
                }
            }
        };
    }
}
let counter = new Counter(3);
for (let i of counter) { console.log(i); }
// 1
// 2
// 3
for (let i of counter) { console.log(i); }
// 1
// 2
// 3
````

以工厂函数创建的迭代器的`Symbol.iterator`属性会返回自身的引用,因此可以被迭代:
````JS
let arr = ['foo', 'bar', 'baz'];
let iter1 = arr[Symbol.iterator]();
console.log(iter1[Symbol.iterator]);    // ƒ [Symbol.iterator]() { [native code] }
let iter2 = iter1[Symbol.iterator]();
console.log(iter1 === iter2);           // true
for (let item of iter1) { console.log(item); }  // 迭代器被迭代
// foo
// bar
// baz
````

### 提前终止迭代器
可选的`return()`方法用于指定在迭代器提前关闭时执行的逻辑.可能执行的情况包括:
- `for-of`循环通过`break`,`continue`?,`return`或`throw`提前退出.
- 解构操作并未消费所有值.

`return()`方法必须返回一个有效的`IteratorResult`对象.简单情况下,可以只返回`{ done: true }`,因为这个返回值只会用在生成器上下文中.

````JS
class Counter {
    constructor(limit) {
        this.limit = limit;
    }
    [Symbol.iterator]() {
        let count = 1,
            limit = this.limit;
        return {
            next() {
                if (count <= limit) {
                    return { done: false, value: count++ };
                } else {
                    return { done: true };
                }
            },
            return() {
                count = limit + 1;  // 关闭迭代器
                console.log('Exit');
                return { done: true };
            },
            [Symbol.iterator]() {
                return this;
            }
        };
    }
}
let counter1 = new Counter(5);
for (let i of counter1) {
    if (i > 2) {
        continue;
    }
    console.log(i);
}
// 1
// 2
for (let i of counter1) {
    if (i > 2) {
        break;
    }
    console.log(i);
}
// 1
// 2
// Exit
let [a, b] = counter1;
// Exit
````

`return()`方法是可选的,所有并非所有迭代器都是可关闭的(例如数组的迭代器).只是增加一个`return()`并不代表迭代器就会被关闭,需要显式地写出迭代器被关闭的代码.

## 生成器
生成器能够在一个函数块内暂停和恢复代码执行的能力.可用于自定义迭代器和实现协程.

### 生成器基础
生成器的形式是一个函数,函数名称前面加一个`*`(星号)表示它是一个生成器.只要是可以定义函数的地方,就可以定义生成器:
````JS
function* generatorFn1() {}
let generatorFn = function* () {}
let foo = {
    * generatorFn() {}
}
class Foo {
    * generatorFn() {}
}
class Bar {
    static * generatorFn() {}
}
````

箭头函数不能用来定义生成器函数.

标识生成器函数的星号不受两侧空格的影响:
````JS
function* generatorFnA() {}
function *generatorFnB() {}
function * generatorFnC() {}
function*generatorFnD() {}
````

调用生成器函数会产生一个生成器对象.生成器对象一开始处于暂停执行(挂起)的状态.与迭代器类似,生成器对象也实现了`Iterator`接口,因此具有`next()`方法.调用这个方法会让生成器开始或恢复执行.
````JS
function* generatorFn() {}
const g = generatorFn();
console.log(g);         // generatorFn {<suspended>}
console.log(g.next);    // ƒ next() { [native code] }
````

`value`属性是生成器函数的返回值,默认为`undefined`,可以通过生成器函数的返回值指定:
````JS
function* generatorFn() {
    return 'foo';
}
let g = generatorFn();
console.log(g);         // generatorFn {<suspended>}
console.log(g.next());  // {value: 'foo', done: true}
````

生成器初次调用后会立即挂起,只有调用`next()`才会往下执行.

生成器对象内部实现了`Iterable`接口,它们默认的迭代器是自引用的:
````JS
function* gFn() { return 'foo'; }
console.log(gFn);   // ƒ* gFn() { return 'foo'; }
let g = gFn();
let iterFn = g[Symbol.iterator];
console.log(iterFn);    // ƒ [Symbol.iterator]() { [native code] }
console.log(iterFn());      // undefined
console.log(g[Symbol.iterator]());  // gFn {<suspended>}
console.log(g === iterFn());    // false
console.log(g === g[Symbol.iterator]());    // true
````
*这里不知道什么原因,对`g[Symbol.iterator]`引用后调用与直接调用结果不同.*

### 通过yield中断执行
`yield`能让生成器暂停并产生一个值,函数作用域的状态会被保留.使用`next()`方法来恢复执行:
````JS
function* gFn() {
    yield 'foo';
    yield 'bar';
    yield 'baz';
}
let g = gFn();
console.log(gFn.next());    // { done: false, value: 'foo' }
console.log(gFn.next());    // { done: false, value: 'bar' }
console.log(gFn.next());    // { done: true, value: 'baz' }
````
通过`yield`挂起的函数返回的对象`done`为`false`,`value`为`yield`后面的值.通过`return`退出的生成器函数会处于`done`为`true`的状态.

不同生成器的生命周期是独立的.

不是直接定义在生成器内部的`yield`会抛出语法错误.
````JS
// 无效
function* invalidGFn() {
    function a() {
        yield;
    }
}
````

#### 生成器对象作为可迭代对象
可以将生成器对象当成可迭代对象:
````JS
function* gFn() {
    yield 1;
    yield 2;
    yield 3;
}
for (const x of gFn()) {
    console.log(x);
}
// 1
// 2
// 3
````

#### yield实现输入输出
`next()`函数允许传入一个参数,使得挂起的生成器恢复时能够通过`yield`返回传入值:
````JS
function* gFn(initial) {
    console.log(initial);
    console.log(yield 1);
    console.log(yield 2);
}
let g = gFn('foo');
g.next('bar');  // foo
// 在该次调用next()前,生成器并未执行,未曾涉及yield,因此'bar'不会被传入生成器
console.log(g.next('baz')); // baz
// {value: 2, done: false}
console.log(g.next('qux')); // qux
// {value: undefined, done: true}
````
示例:
````JS
function* range(start, end) {
    while (end > start) {
        yield start++;
    }
}
for (const x of range(4, 7)) {
    console.log(x);
}
// 4
// 5
// 6
````

#### 产生可迭代对象
可以用星号增强`yield`行为,让它能够迭代一个可迭代对象,从而一次产出一个值:
````JS
function* gFn() {
    yield* [1, 2, 3];
}
// 等价于:
// function* gFn() {
//     for (const x of [1, 2, 3]) {
//         yield x;
//     }
// }
let g = gFn();
for (const x of g) {
    console.log(x);
}
// 1
// 2
// 3
````
`yield`星号两侧的空格不影响其行为.

对于`yield*`来说,若可迭代对象(参数)为普通迭代器(且迭代最后一个元素时未给`next()`传入参数),则恢复后的返回值为`undefined`:
````JS
function* gFn() {
    console.log(yield* [1, 2, 3]);
}
for (const x of gFn());
// undefined
````
若可迭代对象为生成器函数,则恢复后的返回值为生成器的返回值:
````JS
function* innerGFn() {
    yield 'foo';
    return 'bar';
}
function* outerGFn() {
    console.log(yield* innerGFn());
}
for (const x of outerGFn());
// bar
````

#### yield*实现递归
````JS
function* nTimes(n) {
    if (n > 0) {
        yield* nTimes(n - 1);
        yield n - 1;
    }
}
for (const x of nTimes(3)) {
    console.log(x);
}
// 0
// 1
// 2
````

### 生成器作为默认迭代器
生成器对象实现了`Iterable`接口,而且生成器函数和默认迭代器被调用之后都生成迭代器,所以生成器格外适合作为默认迭代器.  
例如:
````JS
class Foo {
    constructor() {
        this.values = [1, 2, 3];
    }
    * [Symbol.iterator]() {
        yield* this.values;
    }
}
const f = new Foo();
for (const x of f) {
    console.log(x);
}
// 1
// 2
// 3
````

### 提前终止生成器
与迭代器类似,生成器也支持`可关闭`概念.除了`next()`,生成器还拥有`return()`方法和`throw()`方法:
````JS
function* gFn() {}
const g = gFn();
console.log(g);         // gFn {<suspended>}
console.log(g.next);    // ƒ next() { [native code] }
console.log(g.return);  // ƒ return() { [native code] }
console.log(g.throw);   // ƒ throw() { [native code] }
````

#### return()
`return()`方法会强制生成器进入关闭状态.提供给`return()`方法的值,就是终止迭代器对象的值:
````JS
function* gFn() {
    for (const x of [1, 2, 3]) {
        yield x;
    }
}
const g = gFn();
console.log(g);             // gFn {<suspended>}
console.log(g.return(4));   // {value: 4, done: true}
console.log(g);             // gFn {<closed>}
````
所有生成器对象都有`return()`方法,只要通过它进入关闭状态,就无法恢复了.后续调用`next()`会显式`done: true`状态,而提供的任何返回值都不会被存储或传播.

`for-of`循环等内置语言结构会忽略状态为`done: true`的`IteratorObject`内部返回的值:
````JS
function* gFn() {
    for (const x of [1, 2, 3]) {
        yield x;
    }
}
const g = gFn();
for (const x of g) {
    if (x > 1) {
        g.return(4);
    }
}
// 1
// 2
````

#### throw()
`throw()`方法会在暂停的时候将一个提供的错误注入到生成器对象中.如果错误未被处理,生成器就会关闭,错误向外传播:
````JS
function* gFn() {
    for (const x of [1, 2, 3]) {
        yield x;
    }
}
const g = gFn();
console.log(g);     // // gFn {<suspended>}
try {
    g.throw('foo');
} catch (e) {
    console.log(e); // foo
}
console.log(g);     // gFn {<closed>}
````
如果生成器内部处理了这个错误,那么生成器就不会关闭,而且还可以恢复执行:
````JS
function* gFn() {
    for (const x of [1, 2, 3]) {
        try {
            yield x;
        } catch (e) {}
    }
}
const g = gFn();
console.log(g.next());          // {value: 1, done: false}
console.log(g.throw('foo'));    // {value: 2, done: false}
console.log(g.next());          // {value: 3, done: false}
````

*注意:如果生成器对象还没有开始执行,那么调用`throw()`抛出的错误不会在函数内部被捕获,因为这相当于在函数块外部抛出了错误.*
````JS
function* gFn() {   // line 1
    try {
        for (const x of [1, 2, 3]) {
            yield x;
        }
    } catch (_) {}
}
const g = gFn();
g.throw('foo');
// Uncaught foo [xxx.js:1]
````

# 对象,类,面向对象编程
ES中对象是一组属性无序的集合.对象的每个属性或方法都由一个名称来标识,名称映射到一个值.因此,可以把ES对象当作一个`unordered_map`.

*本章可以只看[对象](#对象)的内容,然后跳过[创建对象](#创建对象)和[继承](#继承)的内容,直接看[类](#类)的相关内容,因为后者是前两者的语法糖.*

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
    sayHi = function sayHi() {
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
> 示例中会大量使用异步日志输出的方式`setTimeout(console.log, 0, ...params)`,旨在演示执行顺序及其他异步行为.这样可以让期约等返回的值达到其最终状态.
>
> 此外,浏览器控制台的输出经常能打印出JS运行中无法获取的对象信息

## 异步编程
### 同步与异步
同步行为对应内存中顺序执行的处理器指令.每条指令都会严格按照它们出现的顺序来执行,而每条指令执行后也能立即获得存储在系统本地(如寄存器或系统内存)的信息.

异步行为类似于系统中断,即当前进程外部的实体可以触发代码执行.异步操作经常是必要的,因为强制进程等待一个长时间的操作通常是不可行的.

**注意:**
> JS的异步**不代表**多线程,而是内部存在一个执行顺序队列.  
> 对于同步来说,执行顺序队列是按照代码所在行依次排下去.  
> 对于异步来说,执行顺序队列是不确定的,某些代码可能会插队进入,但仍然是单线程的.在异步环境下,先出现的代码处于的执行顺序队列位置*不一定*在后出现的代码处于的执行顺序队列位置的前面.

### 以往的异步编程模式
在早期JS中,只支持回调函数来表明异步操作完成:
````JS
function double(num) {
    setTimeout(() => setTimeout(console.log, 0, num.value * 2), 1000);  // 不要写成num,否则会使用传入num的原始值副本,导致不会发生改变
    // 也可以使用 setTimeout(() => console.log(num.value * 2), 1000)
}
let a = new Number(10); // 使用Number包装为对象,以传入引用
double(a);
a.value = 20;
// 40 (大约1000ms后)
````
将上述被调函数作为`callback`传入,即形成了通过回调函数来执行异步操作.实际操作中通常需要深度嵌套回调函数,导致代码维护困难.

## 期约
期约是对尚不存在结果的一个替身.

### Promise/A+规范
`Promise/A+`组织分叉(fork)了`CommonJS`的`Promise/A`建议,并以相同的名字制定了`Promise/A+`规范.

ES6增加了对`Promise/A+`规范的完善支持,即`Promise`类型.

### 期约基础
`Promise`可以通过`new`操作符来实例化.创建新期约时,需要传入一个执行器(executor)函数作为参数:
````JS
let p = new Promise(() => {});
setTimeout(console.log, 0, p);  // Promise {<pending>}
````
未传入函数作为参数会抛出`SyntaxError`.

#### 期约状态机
期约是一个有状态的对象,可能处于如下3种状态之一:
- `待定(pending)`
- `兑现(fulfilled, 或"解决"resolved)`
- `拒绝(rejected)`

**待定**是期约的最初始状态.在待定状态下,期约可以**落定(settled)**为代表成功的**兑现**状态,或者代表失败的**拒绝**状态.无论落定为哪种状态都是不可逆的.只要从待定转换为兑现或者拒绝,期约的状态就不再改变.而且,不能保证期约必然会脱离待定状态,永远处于待定状态也是具有恰当的行为.

期约的状态是私有的,不能直接通过JS检测到.期约的状态也不能被外部JS代码修改.期约故意将异步行为封装起来,从而隔离外部的同步代码.

#### 解决值,拒绝理由及期约用例
期约主要有两大用途.首先是抽象地表示一个异步操作.期约的状态代表期约是否完成."待定"表示尚未开始或者正在执行中."兑现"表示已经成功完成."拒绝"表示没有成功完成.利于期约要向服务器发送一个`HTTP`请求,请求返回`200~299`范围内的状态码就足以让期约的状态变为"兑现".如果不在`200~299`范围内,那么就会把期约状态切换为"拒绝".

在另外一些情况下,期约封装的异步操作会实际生成某个值,而程序期约状态改变时可以访问这个值.相应地,如果期约被拒绝,程序就会期待期约状态改变时可以拿到拒绝的理由.

为了支持这两种用例,每个期约只有状态切换为兑现,就会有一个私有的内部`值(value)`.类似地,每个期约只要状态切换为拒绝,就会有一个私有的内部`理由(reason)`.无论是值还是理由,都是包含原始值或对象的不可修改的引用.二者都是可选的,而且默认值为`undefined`.在期约到达某个落定状态时执行的异步代码始终会收到这个值或理由.

#### 通过执行函数控制期约状态
期约状态是私有的,所以只能在内部进行操作.内部状态在期约的执行器函数中完成.执行器函数主要有两项职责:初始化期约的异步行为和控制状态的最终转换.其中,控制期约状态的转换是通过调用它的两个**函数参数**实现的.这两个函数参数通常都命名为`resolve()`和`reject()`.调用`resolve()`会把状态切换为`兑现`,调用`reject()`会把状态切换为拒绝,并抛出错误(在执行函数内).

````JS
function func(resolve, reject) {
    resolve();  // resolve是函数形参
}
let p1 = new Promise(func);
let p2 = new Promise((resolve, reject) => reject());    // line 5
setTimeout(console.log, 0, p1); // Promise {<fulfilled>: undefined}
setTimeout(console.log, 0, p2); // Promise {<rejected>: undefined}
// Uncaught (in promise) undefined [xxx.js:5]
````
上述的操作是同步的.

一旦调用了`resolve()`或`rejected()`再次调用两者之一都是无效的:
````JS
let p = new Promise((resolve, reject) => {
    resolve();
    reject();
});
setTimeout(console.log, 0, p);  // Promise {<fulfilled>: undefined}
````
为避免期约卡在待定状态,可以添加一个定时退出功能.比如,可以通过`setTimeout`设置一个10秒钟后无论如何都会拒绝期约的回调:
````JS
let  p = new Promise((resolve, reject) => {
    setTimeout(reject, 10000);
});
setTimeout(console.log, 0, p);
// Promise {<pending>}
setTimeout(console.log, 11000, p);
// (after 10 sec) Uncaught (in promise) undefined
// (after 11 sec) Promise {<rejected>: undefined}
````
因为期约状态只能改变一次,因此上述操作没有副作用.

#### Promise.resolve()
使用静态方法`Promise.resolve()`可以实例化一个解决的期约:
````JS
setTimeout(console.log, 0, Promise.resolve());  // Promise {<fulfilled>: undefined}
// 传入一个参数以作为结果
setTimeout(console.log, 0, Promise.resolve(3)); // Promise {<fulfilled>: 3}
// 多余的参数会被忽略
setTimeout(console.log, 0, Promise.resolve(4, 5, 6));   // Promise {<fulfilled>: 4}
````

`Promise.resolve()`是幂等的:
````JS
let p = Promise.resolve(7);
setTimeout(console.log, 0, p === Promise.resolve(p));   // true
setTimeout(console.log, 0, Promise.resolve(Promise.resolve(p)));    // Promise {<fulfilled>: 7}
setTimeout(console.log, 0, Promise.resolve(new Promise(() => {}))); // Promise {<pending>}
````

这个静态方法可以包装任何值,包括错误对象,并将其转换为解决的期约.因此,可能会导致不符合预期的行为:
````JS
let p = Promise.resolve(new Error('foo'));
setTimeout(console.log, 0, p);  // Promise {<fulfilled>: Error: foo at xxx.js:1:25}
````

#### Promise.reject()
`Promise.reject()`会实例化一个拒绝的期约并抛出一个异步错误(这个错误只能通过拒绝处理程序捕获):
````JS
let p = Promise.reject();
setTimeout(console.log, 0, p);  // Promise {<rejected>: undefined}
// Uncaught (in promise) undefined [xxx.js:1]
````

该方法的第一个参数是拒绝的理由.这个参数也会传给后续的拒绝处理程序:
````JS
let p = Promise.reject(3);
setTimeout(console.log, 0, p);  // Promise {<rejected>: 3}
p.then(null, (e) => setTimeout(console.log, 0, e)); // 3
// 拒绝处理程序
````

`Promise.reject()`**不是**幂等的:
````JS
setTimeout(console.log, 0, Promise.reject(Promise.reject()));   // Promise {<rejected>: Promise {<rejected>: undefined}}
// Uncaught (in promise) undefined
// Uncaught (in promise) Promise {<rejected>: undefined}
````

#### 同步/异步执行的二元性
`Promise`是与异步模式交互的唯一方法,它是同步对象,也是异步执行模式的媒介.异步代码当中抛出的错误,必须通过异步模式捕获.

### 期约的实例方法
#### 实现Thenable接口
在ES暴露的异步结构中,任何对象都有一个`then()`方法.这个方法被认为实现了`Thenable`接口:
````JS
class MyThenable {
    then() {}
}
````
`Promise`实现了`Thenable`接口.

#### Promise.prototype.then()
`Promise.prototype.then()`是为期约实例添加处理程序的主要方法.这个`then()`方法接收最多两个参数:`onResolved`处理程序和`onRejected`处理程序.这两个参数都是可选的,如果提供的话,则会在期约分别进入`兑现`和`拒绝`状态时执行.
````JS
function onResolved(id) {
    setTimeout(console.log, 0, id, 'resolved');
}
function onRejected(id) {
    setTimeout(console.log, 0, id, 'rejected');
}
let p1 = new Promise((resolve, reject) => setTimeout(resolve, 3000));
let p2 = new Promise((resolve, reject) => setTimeout(reject, 3000));
p1.then(() => onResolved('p1'),
        () => onRejected('p1'));
p2.then(() => onResolved('p2'),
        () => onRejected('p2'));
// (3秒后)
// p1 resolved
// p2 rejected
````

因为期约只能转化为最终状态一次,所以这两个操作一定是互斥的.

对同一个`Promise`多次调用`then()`是合法的.

`onRejected`或者`onResolved`参数都是可选的,且传入非函数类型的参数都会被静默忽略.因此如果只想要提供`onRejected`,可以给`onResolved`参数传入`undefined`或`null`.

`Promise.prototype.then()`方法返回一个新的期约实例:
````JS
let p1 = new Promise(() => {});
let p2 = p1.then();
setTimeout(console.log, 0, p1);         // Promise {<pending>}
setTimeout(console.log, 0, p2);         // Promise {<pending>}
setTimeout(console.log, 0, p1 === p2);  // false
````
返回的实例始终处于待定状态,无论当前`Promise`对象的状态如何.

返回的`Promise`对象(称之为`p`)的行为取决于处理函数的执行结果,遵循一组特定的规则.如果处理函数：
- 返回一个值:`p`以该返回值作为其兑现值.
- 没有返回任何值:`p`以`undefined`作为其兑现值.
- 抛出一个错误:`p`抛出的错误作为其拒绝值.
- 返回一个已兑现的`Promise`对象:`p`以该`Promise`的值作为其兑现值.
- 返回一个已拒绝的`Promise`对象:`p`以该`Promise`的值作为其拒绝值.
- 返回另一个待定的`Promise`对象:`p`保持待定状态,并在该`Promise`对象被兑现/拒绝后立即以该`Promise`的值作为其兑现/拒绝值.

例如:
````JS
let p1 = new Promise((resolve, reject) => reject());
let p11 = p1.then(null, null);
// Uncaught (in promise) undefined
setTimeout(console.log, 0, p11);    // Promise {<rejected>: undefined}
let p12 = p1.then(null, () => 1);
setTimeout(console.log, 0, p12);    // Promise {<fulfilled>: 1}
let p13 = p1.then(null, () => Promise.resolve('p13'));
setTimeout(console.log, 0, p13);    // Promise {<fulfilled>: 'p13'}
let p2 = new Promise((resolve, reject) => resolve());
let p21 = p2.then(null, null);
setTimeout(console.log, 0, p21);    // Promise {<fulfilled>: undefined}
let p22 = p2.then(() => { throw 'p22'; });
// Uncaught (in promise) p22
setTimeout(console.log, 0, p22);    // Promise {<rejected>: 'p22'}
let p23 = p2.then(() => Promise.reject('p23'));
// Uncaught (in promise) p23
setTimeout(console.log, 0, p23);    // Promise {<rejected>: 'p23'}
let p3 = new Promise((resolve) => setTimeout(resolve, 1000));
let p31 = p3.then();
setTimeout(console.log, 0, p31);    // Promise {<pending>}
setTimeout(console.log, 1000, p31);
// (1秒后) Promise {<fulfilled>: undefined}
````
返回错误对象而非抛出错误不会触发拒绝行为.

调用`then()`,表明错误已经处理中,因此无需写`try/catch`,若最终`then()`的返回值(无论是否被接收)`Promise`的状态为`rejected`,则会再次在异步模式中抛出错误.

这种行为可以做到链式调用.

#### Promise.prototype.catch()
`Promise.prototype.catch()`方法用于给期约添加拒绝处理程序.这个方法只接收一个参数:`onRejected`处理程序.这其实是`Promise.prototype.then(undefined, onRejected)`的语法糖.

其返回值同`Promise.prototype.then()`.

#### Promise.prototype.finally()
`Promise.prototype.finally()`方法用于给期约添加`onFinally`处理程序(唯一参数).这个处理程序在期约转换为解决或拒绝状态时都会执行.但该方法**并不**等同于`then(onFinally, onFinally)`,它的处理程序不接受任何参数.
````JS
let p1 = new Promise((resolve, reject) => reject(3));
// Uncaught (in promise) 3
let p11 = p1.finally((id) => {
        setTimeout(console.log, 0, id); // undefined
        return 4;
    } );
setTimeout(console.log, 5, p11);
// Promise {<rejected>: 3}
````

该方法立即返回一个新的`Promise`.无论当前`promise`的状态如何,此新的`promise`在返回时始终处于待定(pending)状态.如果`onFinally`抛出错误或返回被拒绝的`Promise`，则新的`Promise`将使用该值进行拒绝.否则,新的`promise`将以与当前`promise`相同的状态敲定(settled).

#### 非重入期约方法
当期约进入落定状态时,与该状态相关的处理程序仅仅会被`排期`,而非立即执行.跟在添加这个处理程序(例如`then()`)的代码之后的同步代码(当前线程的代码)一定会在处理程序之前先执行.即使期约一开始就是与附加处理程序关联的状态,执行顺序也是这样的.这个特性由JS运行时保证,被称为`非重入(non-reentrancy)`特性:
````JS
let p = Promise.resolve();
p.then(() => console.log('onResolved handler'));    // then()是p的处理程序,一定会在同步代码之后运行
console.log('then() returns');  // 当前线程的代码先执行
````
其输出为:
```
then() returns
onResolved handler
```

即使先添加处理程序,后改变期约状态,其结果也是一样的:
````JS
let synchronousResolve;
let p = new Promise((resolve) => {
    synchronousResolve = function() {
        console.log('1: invoking resolve()');
        resolve()l
        console.log('2: resolve() returns');
    };
});
p.then(() => console.log('4: then() handler executes'));
synchronousResolve();
console.log('3: synchronousResolve() returns');
````
实际的输出:
```
1: invoking resolve()
2: resolve() returns
3: synchronousResolve() returns
4: then() handler executes
```

非重入适用于`onResolved/onRejected`(`then()`)处理程序,`catch()`处理程序和`finally()`处理程序.

#### 邻近处理程序的执行顺序
如果给期约添加了多个处理程序,当期约状态变化时,相关处理程序会添加它们的顺序依次执行.无论是`then()`,`catch()`还是`finally()`:
````JS
let p1 = Promise.resolve();
let p2 = Promise.reject();
p1.then(() => setTimeout(console.log, 0, 1));
p1.then(() => setTimeout(console.log, 0, 2));
// 1
// 2
p2.then(null, () => setTimeout(console.log, 0, 3));
p2.then(null, () => setTimeout(console.log, 0, 4));
// 3
// 4
p2.catch(() => setTimeout(console.log, 0, 5));
p2.catch(() => setTimeout(console.log, 0, 5));
// 5
// 6
p1.finally(() => setTimeout(console.log, 0, 7));
p1.finally(() => setTimeout(console.log, 0, 8));
// 7
// 8
````

#### 传递解决值和拒绝理由
到了落定状态后,期约会提供其解决值(如果兑现)或其拒绝理由(如果拒绝)给相关状态的处理程序.拿到返回值后,就可以进一步对这个值进行操作.

在执行函数中,解决的值和拒绝的理由是分别作为`resolve()`和`reject()`的第一个参数往后传的.这些值会传给它们各自的处理程序,作为`onResolved`或`onRejected`处理程序的**唯一**参数:
````JS
let p1 = Promise.resolve('foo');
p1.then((value) => console.log(value));     // foo
let p2 = Promise.reject('bar');
p2.catch((reason) => console.log(reason));  // bar
let p3 = new Promise((resolve, reject) => resolve('foo'));
p3.then((value) => console.log(value));     // foo
let p4 = new Promise((resolve, reject) => reject('bar'));
p4.catch((reason) => console.log(reason));  // bar
````

#### 拒绝期约与拒绝错误处理
拒绝期约表明程序需要中断或特殊处理.在期约的执行函数或处理程序中抛出错误会导致拒绝,对应的错误对象会成为拒绝的理由.

以下期约都会以一个错误对象为由被拒绝:
````JS
let p1 = new Promise((resolve, reject) => reject(Error('foo')));
let p2 = new Promise((resolve, reject) => { throw Error('foo'); });
let p3 = Promise.resolve().then(() => { throw Error('foo'); });
let p4 = Promise.reject(Error('foo'));
setTimeout(console.log, 0, p1); // Promise <rejected>: Error: foo
setTimeout(console.log, 0, p2); // Promise <rejected>: Error: foo
setTimeout(console.log, 0, p3); // Promise <rejected>: Error: foo
setTimeout(console.log, 0, p4); // Promise <rejected>: Error: foo
// [4个未捕获异常]
````

期约可以以任何理由拒绝,包括`undefined`,但最好统一使用错误对象.因为创建错误对象可以让浏览器捕获错误对象中的栈追踪信息,而这些信息对调试是非常关键的.

在同步执行过程中,`throw`关键字抛出错误会停止执行错误之后的任何指令.但是,在异步抛出错误的情况下不会阻止同步指令的继续执行.

异步错误只能通过异步的`onRejected`处理程序捕获:
````JS
// 正确
Promise.reject(Error('foo')).catch((e) => {});

// 错误
try {
    Promise.reject(Error('foo'));
} catch (e) {}
````

但若是期约内显式使用`throw`而非`reject()`,则仍然可以用`try/catch`块捕获,仅当错误未被捕获时,其行为与`reject()`相同(不能使用上述错误的捕获).

`onRejected`处理程序的任务应该是在捕获异步错误之后返回一个解决的期约(或者再次传递一个拒绝的期约待下一个处理程序解决):
````JS
// 同步时的try/catch
console.log('begin synchronous execution');
try {
    throw Error('foo');
} catch (e) {
    console.log('caught error', e);
}
console.log('continue synchronous execution')
// begin synchronous execution
// caught error Error: foo
// coutinue synchronous execution

// 异步的错误处理与try/catch处理类似
new Promise((resolve, reject) => {
    console.log('begin asynchronous execution');
    reject(Error('bar'));
}).catch((e) => {
    console.log('caught error', e);
}).then(() => {
    console.log('continue asynchronous execution');
});
// begin asynchronous execution
// caught error Error: bar
// continue asynchronous execution
````

### 期约连锁与期约合成
多个期约组合在一起可以构成强大的逻辑.这种组合可以通过两种方式实现:期约连锁与期约合成.前者就是一个期约接一个期约地拼接,后者则是将多个期约组合为一个期约.

#### 期约连锁
期约连锁举例:
````JS
let p = new Promise((resolve, reject) => {
    console.log('first');
    setTimeout(resolve, 1000);
});
let pr = p.then(() => new Promise((resolve, reject) => {
    console.log('second');
    setTimeout(resolve, 1000);
}))
 .then(() => new Promise((resolve, reject) => {
    console.log('third');
    setTimeout(resolve, 1000);
}))
 .then(() => new Promise((resolve, reject) => {
    console.log('fourth');
    setTimeout(resolve, 1000);
}));
setTimeout(console.log, 5000, pr);
// (0秒后) first
// (1秒后) second
// (2秒后) third
// (3秒后) fourth
// (5秒后) Promise {<fulfilled>: undefined}
````
可以使用工厂函数简写:
````JS
function delayedResolve(str) {
    return new Promise((resolve, reject) => {
        console.log(str);
        setTimeout(resolve, 1000);
    });
}
delayedResolve('first')
  .then(() => delayedResolve('second'))
  .then(() => delayedResolve('third'))
  .then(() => delayedResolve('fourth'));
````

#### 期约图
因为一个期约可以有任意多个处理程序,所以期约连锁可以构建*有向非循环图*的结构,每个期约都是图中的一个结点,图的方向是期约解决或拒绝的顺序:
````JS
// 二叉树,属于有向非循环结构的特殊情况
//      A
//    /   \
//   B     C
//  / \   / \
// D   E F   G
let A = new Promise((resolve, reject) => {
    console.log('A');
    resolve();
});
let B = A.then(() => console.log('B'));
let C = A.then(() => console.log('C'));

B.then(() => console.log('D'));
B.then(() => console.log('E'));
C.then(() => console.log('F'));
C.then(() => console.log('G'));
// A
// B
// C
// D
// E
// F
// G
````

由于期约是按照添加顺序执行的,因此上述写法必定会出现层序遍历的结果.

允许使用`Promise.all()`和`Promise.race()`将多个期约组合为一个,因此使用*有向非循环图*而非树状结构描述最为准确.

#### Promise.all()和Promise.race()
`Promise.all()`和`Promise.race()`能将多个期约组合为一个.

- 对于`Promise.all()`:

该静态方法创建的期约会在一组期约全部解决之后再解决.如果存在期约处于待定状态,则合成的期约处于待定.如果存在期约拒绝,则合成的期约也会拒绝.

该静态方法接收一个可迭代对象,返回一个新期约:
````JS
let p1 = Promise.all([
    Promise.resolve(),
    Promise.resolve()
]);
setTimeout(console.log, 0, p1); // Promise {<fulfilled>: [undefined, undefined]}

// 可迭代对象中的非Promise元素会使用Promise.resolve()转换为期约
let p2 = Promise.all([3,4]);
setTimeout(console.log, 0, p2); // Promise {<fulfilled>: [3, 4]}

// 空的可迭代对象等价于Promise.resolve()
let p3 = Promise.all([]);
setTimeout(console.log, 0, p3); // Promise {<fulfilled>: []}

// 无效的语法
let p4 = Promise.all(); // TypeError

// 待定
let p5 = Promise.all([
    Promise.resolve(),
    new Promise((resolve) => setTimeout(resolve, 1000))
]);
setTimeout(console.log, 0, p5); // Promise {<pending>}

// 一次拒绝导致最终拒绝,即使其他期约待定
let p6 = Promise.all([
    new Promise(() => {}),
    Promise.reject()
]);
setTimeout(console.log, 0, p6); // Promise {<rejected>: undefined}
// Uncaught (in promise) undefined

setTimeout(console.log, 1000, p5);  // (1秒后) Promise {<fulfilled>: [undefined, undefined]}
````

如果所有期约都成功解决,则合成的期约的解决值就是包含所有期约解决值(包括`undefined`)的数组,按照迭代器顺序.

如果有期约拒绝,则第一个拒绝的期约就是作为合成期约的拒绝理由.对于所有拒绝的期约,`Promise.all()`会静默处理所有错误(拒绝),但只有第一个错误理由不会被忽略,其返回的合成期约由于是拒绝的,因此也会抛出一个错误(异步):
````JS
let p1 = Promise.all([
    Promise.reject(3),
    new Promise((resolve, reject) => setTimeout(reject, 1000, 4))
]);
p1.catch((reason) => setTimeout(console.log, 0, reason));    // 3
// 没有未处理的错误

let p2 = Promise.all([
    Promise.resolve(5),
    Promise.resolve(6),
    Promise.resolve(7)
]);
p2.then((value) => setTimeout(console.log, 0, value));  // [5, 6, 7]
````

- 对于`Promise.race()`:

`Promise.race()`静态方法返回一个包装期约,是一组集合中**最先**解决或拒绝的期约的镜像.这个方法接收一个可迭代对象,返回一个新期约:
````JS
let p1 = Promise.race([
    Promise.resolve(),
    Promise.resolve()
]);
setTimeout(console.log, 0, p1); // Promise {<fulfilled>: undefined}

// 可迭代对象中的非Promise元素会使用Promise.resolve()转换为期约
let p2 = Promise.race([3,4]);
setTimeout(console.log, 0, p2); // Promise {<fulfilled>: 3}

// 空的可迭代对象等价于new Promise(() => {})
let p3 = Promise.race([]);
setTimeout(console.log, 0, p3); // Promise {<pending>}

// 无效的语法
let p4 = Promise.race(); // TypeError

// 谁先发生,就返回谁
let p5 = Promise.race([
    Promise.reject(4),
    new Promise((resolve) => setTimeout(resolve, 10)),
    new Promise(() => {})
]);
// Uncaught (in promise) 4
setTimeout(console.log, 0, p5); // Promise {<rejected>: 4}
setTimeout(console.log, 20, p5);    // Promise {<rejected>: 4}
````

合成的期约会静默处理所有的拒绝的操作,但如果返回值为*拒绝的期约*,则仍然会异步抛出错误:
````JS
let p = Promise.race([
    Promise.resolve(3),
    new Promise((resolve, reject) => setTimeout(reject, 1000, 4)),
    new Promise((resolve, reject) => setTimeout(reject, 1000, 5)),
    new Promise((resolve, reject) => setTimeout(reject, 1000, 6)),
    new Promise((resolve, reject) => setTimeout(reject, 1000, 7))
]);
// 没有未处理的错误
````

#### 串行期约合成

可以通过之前期约的返回值来串联期约.这很像函数参数是函数返回值的情况:
````JS
function addTwo(x) { return x + 2; }
function addThree(x) { return x + 3; }
function addFive(x) { return x + 5; }

function addTen(x) {
    return Promise.resolve(x)
      .then(addTwo)
      .then(addThree)
      .then(addFive);
}
addTen(8).then(console.log);    // 18
// vvv 简化
function addTen(x) {
    return [addTwo, addThree, addFive]
        .reduce((promise, fn) => promise.then(fn), Promise.resolve(x));
}
addTen(8).then(console.log);    // 18
````
由上可以提取出一个通用函数,可以把任意多个函数作为处理程序合成一个连续传值的期约连锁:
````JS
function addTwo(x) { return x + 2; }
function addThree(x) { return x + 3; }
function addFive(x) { return x + 5; }

function compose(...fns) {
    return (x) => fns.reduce((promise, fn) => promise.then(fn), Promise.resolve(x));
}
let addTen = compose(addTwo, addThree, addFive);
addTen(8).then(console.log);    // 18
````

### 期约扩展
ES期约有不足之处.它缺少了期约取消和进度追踪发功能.

#### 期约取消
期约处理过程中,程序不再需要其结果.这时候需要能够期约取消.但ES6没有办法阻止它执行到完成.可以在现有实现基础上提供一种临时性的封装,使用`取消令牌`来实现取消期约的功能.

/// TODO

#### 期约进度通知
执行中的期约可能会有不少离散的阶段,在最终解决之前必须依次经过.某些情况下,监控期约的执行进度会很有用.ES6并不支持进度追踪,但是可以通过扩展(继承)来实现.

/// TODO

## 异步函数
异步函数,也称为`async/await`,是ES8规范新增的.ES6期约模式在ES函数中的应用.

### 异步函数
#### async
使用`async`关键字可以让函数具有异步特征,但没有`await`辅助,该函数总体上来说仍然是同步求值的:
````JS
async function foo() {
    console.log(1);
}
let ret = foo();
console.log(ret);
// 1
// Promise {<fulfilled>: undefined}
````

如果函数返回值(无显式返回则返回`undefined`)未实现`thenable`接口,则会被`Promise.resolve()`包装为一个期约对象.如果返回值实现了`thenable`接口的对象,则直接返回该对象(以供`then()`处理程序"解包"):
````JS
async function foo() {
    console.log(1);
    return 3;
}
foo().then(console.log);
console.log(2);
// 1
// 2
// 3

async function bar() {
    const thenable = {
        then(callback) { callback('bar'); }
    };
    return thenable;
}
bar().then(console.log);
// bar

async function baz() {
    return Promise.resolve('baz');
}
baz().then(console.log);
// baz
````

异步函数抛出的错误会返回拒绝的期约:
````JS
async function foo() {
    console.log(1);
    throw 3;
}
setTimeout(console.log, 0, foo());
// 1
// Promise {<rejected>: 3}
// Uncaught (in promise) 3
````

异步函数中的嵌套异步错误不会被异步函数捕获:
````JS
async function foo() {
    console.log(1);
    Promise.reject(3);
    throw 2;
}
foo().catch(console.log);
// 1
// 2
// Uncaught (in promise) 3
````

#### await
`await`关键字可以暂停异步函数代码的执行,等待期约解决:
````JS
let p = new Promise((resolve, reject) => setTimeout(resolve, 1000, 3));
p.then((x) => console.log(x));  // 3
// ^^^ 之前的方法 | 使用async/await vvv
async function foo() {
    let p = new Promise((resolve, reject) => setTimeout(resolve, 1000, 3));
    console.log(await p);
}
foo();
// 3
````

`await`类似一元操作符,可以作为表达式使用.若`await`后的表达式是原生的`Promise`(或其派生类),且其构造函数为`Promise`构造函数或其引用,则返回`Promise`对象要传给`then()`方法的值;否则,如果结果实现了`thenable`接口,`await`就会构造一个新的`Promise`用于等待,并使用表达式结果的`then()`方法作为其处理函数;否则,将该值作为已经解决的期约的值并返回:
````JS
async function foo() {
    console.log(await 'foo');
}
foo();
// foo
async function bar() {
    console.log(await ['bar']);
}
bar();
// ['bar']
async function baz() {
    const thenable = {
        then(callback) { callback('baz'); }
    };
    console.log(await thenable);
    // 不是原生的Promise或其派生,构造一个新的Promise,使用new Promise(thenable.then);
    // thenable.then()作为处理函数,其第一个形参callback接收了resolve,因此,使用callback('baz');相当于resolve('bar');,其使得Promise解决且值为baz.
}
baz();
// baz
async function qux() {
    console.log(await Promise.resolve('qux'));
}
qux();
// qux
````

等待的表达式抛出错误会导致`await`不被计算并使异步函数立即返回拒绝的期约:
````JS
async function foo() {
    console.log(1); // 1
    console.log(await (() => { throw 3; })());  // <不输出>
}
console.log(foo()); // Promise {<rejected>: 3}
// Uncaught (in promise) 3
````

当`await`后的表达式结果为拒绝的期约,会导致`await`不被计算并使异步函数立即返回该拒绝的期约:
````JS
async function foo() {
    console.log(1); // 1
    console.log(await Promise.reject(3));   // <不输出>
    console.log(2); // <不执行>
}
setTimeout(console.log, 0, foo());  // Promise {<rejected>: 3}
// Uncaught (in promise) 3
````

#### await的限制
`await`仅能在异步函数中使用,且在异步函数嵌套的同步函数中使用也是非法的.

允许立即定义并调用异步函数:
````JS
(async function() {
    console.log(await Promise.resolve(3));
})();
// 3
````

### 停止和恢复执行
JS在碰到`await`关键字时,会记录在哪里暂停执行,等到`await`右边的值可用了,JS会向任务队列中推送一个任务(即使是一个立即可用的值),这个任务会恢复异步函数的执行:
````JS
async function foo() {
    console.log(2);
    await null;
    console.log(4);
}
console.log(1);
foo();
console.log(3);

// 1
// 2
// 3
// 4
````
其过程为:
1. 打印`1`
2. 调用异步函数`foo()`
3. (在`foo()`中)打印`2`
4. (在`foo()`中)`await`关键字暂停执行,为立即可用的值`null`向消息队列中添加一个任务
5. `foo()`退出
6. 打印`3`
7. 同步线程的代码执行完毕
8. JS运行时从消息队列中取出任务,恢复异步函数执行
9. (在`foo()`中)恢复执行,`await`取得`null`值
10. (在`foo()`中)打印4
11. `foo()`返回

对于表达式`await Promise.resolve(value)`,在`TC39`后对该行为做出了修改.在此前,`Promise.resolve(value)`会异步(立即)落定并在消息队列中添加一个结果(其本身),`await`会获取其`value`并再次在消息队列中添加一个任务以恢复函数.而在`TC39`后,`await`中的`Promise.resolve(value)`会立即落定,`await`会获取其`value`并在消息队列中添加一个任务以恢复函数,即只会生成一个异步任务而非前后两个.

### 异步函数策略
#### 实现sleep()
````JS
async function sleep(delay) {
    return new Promise((resolve) => setTimeout(resolve, delay));
}
async function foo() {
    const t0 = Date.now();
    await sleep(1500);  // 暂停约1500毫秒
    console.log(Date.now() - t0);
}
foo();
// 1508
````

#### 利用平行执行
以下例子中各函数会顺序执行:
````JS
async function randomDelay(id) {
    const delay = Math.random() * 1000;
    return new Promise((resolve) => setTimeout(() => {
        console.log(`${id} finished`);
        resolve();
    }, delay));
}
async function foo() {
    const t0 = Date.now();
    await randomDelay(0);
    await randomDelay(1);
    await randomDelay(2);
    await randomDelay(3);
    await randomDelay(4);
    console.log(`${Date.now() - t0}ms elapsed`);
}
foo();
// 0 finished
// 1 finished
// 2 finished
// 3 finished
// 4 finished
// 1656ms elapsed
````

如果顺序不是必需保证的,那么可以先一次性初始化所有期约,然后再分别等待它们的结果.比如:
````JS
async function randomDelay(id) {
    const delay = Math.random() * 1000;
    return new Promise((resolve) => setTimeout(() => {
        console.log(`${id} finished`);
        resolve();
    }, delay));
}
async function foo() {
    const t0 = Date.now();
    const p0 = randomDelay(0);
    const p1 = randomDelay(1);
    const p2 = randomDelay(2);
    const p3 = randomDelay(3);
    const p4 = randomDelay(4);
    // const promises = Array(5).fill(null).map((_, i) => randomDelay(i));
    await p0;
    await p1;
    await p2;
    await p3;
    await p4;
    // for (const p of promises) {
    //     await p;
    // }
    setTimeout(console.log, 0, `${Date.now() - t0}ms elapsed`);
}
foo();
// 4 finished
// 3 finished
// 0 finished
// 1 finished
// 2 finished
// 663ms elapsed
````
由于异步执行不是多线程的,所以可能会出现时间没有明显缩短的情况.上述期约没有按照顺序执行,但`await`按顺序收到了每个期约的值.

#### 串行执行期约
使用`async/await`可以更加简单地连锁期约:
````JS
function addTwo(x) { return x + 2; }
function addThree(x) { return x + 3; }
function addFive(x) { return x + 5; }
async function addTen(x) {
    for (const fn of [addTwo, addThree, addFive]) {
        x = await fn(x);
    }
    return x;
}
addTen(9).then(console.log);    // 19
````

#### 栈追踪与内存管理
期约和异步函数的功能虽然有相当程度的重叠,但它们在内存中的表示则差别很大.例如:
````JS
function fooPromiseExecutor(resolve, reject) {
    setTimeout(reject, 1000, 'bar');
}
function foo() {
    new Promise(fooPromiseExecutor);
}
foo();
// Uncaught (in promise) bar
// setTimeout
// fooPromiseExecutor
// foo
// (匿名)
````
上述调用栈中,`fooPromiseExecutor`应当已经返回,但其仍然出现在异步错误显式的调用栈中.这表明JS会在创建期约时尽可能保留完整的调用栈.在抛出错误时,调用栈可以由运行时错误处理逻辑获取,因而就会出现在栈追踪信息中.这也意味着站追踪信息会占用内存,从而带来一些计算和存储成本.

````JS
function fooPromiseExecutor(resolve, reject) {
    setTimeout(reject, 1000, 'bar');
}
async function foo() {
    await new Promise(fooPromiseExecutor);
}
foo();
// foo
// await in foo
// (匿名)
````
`await in foo`表明此时`foo()`被挂起了,并没有退出.上述调用栈表明异步函数并不会保留完整的调用栈,因而不会带来额外的性能消耗.

# BOM
ES把浏览器对象模型(BOM)描述为JS的核心.BOM的发展缺乏规范,最终,浏览器实现之间共通的部分成为了事实标准,为Web开发提供了浏览器之间互操作的基础.HTML5规范中有一部分涵盖了BOM的主要内容.

## window对象
BOM的核心是`window`对象,表示浏览器的实例.`window`对象在浏览器中有两重身份,一个是ES中的Global对象,另一个就是浏览器窗口的JS接口.这意味着在全局范围内定义的对象,(用`var`定义的)变量和函数都以`window`作为其`Global`对象.

### Global作用域
`window`对象被复用为ES的Global对象,所以通过`var`声明的所有全局变量和函数都会变成`window`对象的属性和方法:
````JS
var age = 29;
var sayAge = () => console.log(this.age);
console.log(window.age);    // 29
sayAge();   // 29
window.sayAge();    // 29
````

使用`let`或`const`替代`var`,则不会把变量添加给全局对象:
````JS
let age = 29;
const sayAge = () => console.log(this.age);
console.log(window.age);    // undefined
sayAge();   // undefined
window.sayAge();    // TypeError
````

很多对象都暴露在全局作用域中,例如`location`和`navigator`,因而它们也是`window`对象的属性.

### 窗口关系
所谓窗口包含浏览器窗口(最外层的`window`对象)以及窗格`<frame>`等.

(以下的`window`表示任意窗口)

`window.top`属性始终指向最上层(最外层)窗口,即浏览器窗口本身.`window.parent`则始终指向当前窗口的父窗口,如果没有父窗口,则其`parent`属性为自身引用.`window.self`属性始终指向自身.

### 窗口位置与像素比
`screenLeft`和`screenTop`分别表示窗口相对于屏幕左侧和顶部的位置,返回值的单位是CSS像素.

`moveTo()`和`moveBy()`方法移动窗口.这两个方法都接收两个参数,其中`moveTo()`接收要移动到的新位置的绝对坐标`x`和`y`;`moveBy()`则接收相对当前位置在两个方向上移动的像素数:
````JS
// 把窗口移动到左上角
window.moveTo(0, 0);
// 把窗口向下移动100像素
window.moveBy(0, 100);
````

移动窗口的方法可能被浏览器禁用.

#### 像素比
一CSS像素约为1/96英寸.定义为屏幕距离人眼一臂长时,0.0213°在屏幕上的长度为一CSS像素.相同分辨率的不同设备可能会有不同的CSS像素.物理像素与CSS像素的比率由`window.devicePixelRatio`属性提供.例如物理分辨率为`1920×1080`,CSS像素分辨率为`640×320`的设备的`window.devicePixelRatio`为`3`.

### 窗口大小
布局视口:浏览器中不包含框架的页面部分.除非调整浏览器整体大小或者修改框架布局,否则它是不变的.

视觉视口:浏览器中可见的部分,相对于布局视口.当使用双指缩放,或键盘在手机上弹出的时候,或者之前隐藏的地址栏变得可见的时候,视觉视口缩小了,但是布局视口却保持不变.

`outerWidth`,`outerHeight`返回浏览器窗口自身的大小,不论是在哪个窗口上使用该属性.

`innerWidth`,`innerHeight`返回浏览器窗口中页面视口的大小(不包括浏览器边框和工具栏).(这两个属性通常被认为是布局视口的大小)

`document.documentElement.clientWidth`和`document.documentElement.clientHeight`返回页面视口的宽度和高度.

由于兼容性问题,浏览器窗口自身的精确尺寸不好确定,但可以确定页面视口的大小:
````JS
let pageWidth = window.innerWidth,
    pageHeight = window.innerHeight;
if (typeof pageWidth != "number") {
    if (document.compatMode == "CSS1Compat") {
        pageWidth = document.documentElement.clientWidth;
        pageHeight = document.documentElement.clientHeight;
    } else {
        pageWidth = document.body.clientWidth;
        pageHeight = document.body.clientHeight;
    }
}
````

而在移动设备上,不同浏览器确定布局视口和视觉视口会有所差异.详见:[A Tale of Two Viewports--Part Two](https://www.quirksmode.org/mobile/viewports2.html)

`resizeTo()`和`resizeBy()`方法可以调整窗口的大小.这两个方法都接收两个参数,`resizeTo()`接收新的宽度和高度值,`resizeBy()`接收宽度和豪赌各要缩放多少:
````JS
// 缩放到100×100
window.resizeTo(100, 100);
// (在上述方法执行成功的条件下)缩放到200×150
window.resizeBy(100, 50);
// 缩放到300×300
window.resizeTo(300, 300);
````

缩放窗口的方法在浏览器可能被禁用.

### 视口位置
一般浏览器可以通过右侧或者下方滚轮来在有限的视口中查看完整的文档.

`window.scrollX`返回文档/页面水平方向滚动的像素值.`window.scrollY`返回文档/页面垂直方向滚动的像素值.

`window.pageXoffset`或`window.pageYoffset`虽然分别与上述值相同,但**已弃用**.

`scroll()`和`scrollTo()`和`scrollBy()`方法可以滚动页面.`scroll()`与`scrollTo()`是相同的,接收x和y坐标,表示要滚动到的坐标.`scrollBy()`接收两个参数,表示要横向和纵向滚动的距离:
````JS
// 向下滚动100像素
window.scrollBy(0, 100);
// 相对于当前视口向右滚动40像素
window.scrollBy(40, 0);
// 滚动到左上角
window.scrollTo(0, 0);
// 滚动到距离屏幕左边和顶边个100像素的位置
window.scrollTo(100, 100);
````

这三个方法也接收一个`ScrollToOptions`字典,除了提供偏移量,还可以通过`behavior`属性告诉浏览器是否平滑滚动:
````JS
window.scrollTo({
    left: 100,
    top: 100,   // 这两个属性相当于之前的x和y
    behavior: 'auto'    // 依据CSS属性scroll-behavior来确定
});
window.scrollBy({
    left: 100,
    top: 100,   // 这两个属性相当于之前的x和y
    behavior: 'smooth'    // 平滑滚动
});
// behavior还可以选择值为`instant`,表示立即跳转
````

### 导航与打开新窗口
`window.open()`方法可以用于导航到指定URL,也可以用于打开新浏览器窗口.其接收四个参数:要加载的URL,目标窗口,特性字符串,浏览器历史记录相关的布尔值.

第一个参数URL是要加载的链接,类似于`<a>`标签的`src`属性.

第二个参数是目标窗口,类似于`<a>`标签的`target`属性,默认值为`_self`.给定字符串时,它会根据字符串找到拥有该名字的窗口,并在此窗口上打开URL.如果未找到该名字的窗口,则建立一个该名字的新窗口,并打开URL.该参数也可以是特殊的窗口名:`_self`(自身),`_parent`(父窗口),`_top`(顶级窗口),`_blank`(新窗口)

第三个参数是特性字符串,用于包含指定特性,特性是一个字符串,书写方法例如:`"height=400,width=400,top=10,left=10,resizable=yes"`.  
可用的特性包括:
- `height`或`innerHeight`:数值.表示新窗口的高度.这个值不能小于100.
- `left`或`screenX`:数值.表示新窗口的x轴坐标.这个值不能是负值.
- `top`或`screenY`:数值.表示新窗口的y轴坐标.这个值不能是负值.
- `width`或`innerWidth`:数值.表示新窗口的宽度.这个值不能小于100.
- 其他特性详见[MDN-window.open()](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/open)
- 部分特性已被弃用

该方法返回一个对新建窗口的引用.这个对象和普通的`window`对象没有区别.但部分浏览器可能会允许缩放或移动通过`window.open()`创建的窗口:
````JS
let newWin = window.open("https://www.mozilla.org/", "_blank", "height=400, width=400, top=10, left=10, resizable=yes");
newWin.resizeTo(500, 500);
newWin.moveTo(100, 100);
````

新创建的窗口的`top`为其自身.

使用`close()`方法关闭使用`window.open()`创建的窗口.关闭窗口后,窗口的引用虽然还在,但只能用于检查其`closed`属性:
````JS
newWin.close();
console.log(newWin.closed);
````

通过其他窗口打开的`window`对象有一个属性`opener`,指向打开它的窗口.这个属性只在弹出窗口的最上层`window`对象有定义,其余皆为`null`:
````JS
let newWin = window.open("https://www.example.com/", "_blank");
console.log(newWin.opener === window);  // true
````

窗口不会记录自己打开的窗口.

某些浏览器中不同标签页运行在独立进程中,使用`open()`打开新窗口(表示两者需要通信)将导致两者运行在同一进程中.将新打开的标签页的`opener`属性设置为`null`,表示新打开的标签页可以运行在独立的进程中(表示两者无需通信).

由于弹出窗口被在线广告滥用,浏览器针对弹窗施加了限制.

#### 弹窗屏蔽程序
许多浏览器内置了弹窗屏蔽程序.此时`window.open()`很可能就会返回`null`.而针对浏览器扩展或其他程序屏蔽弹窗时,`window.open()`通常会抛出错误.因此:
````JS
let blocked = false;
try {
    let newWin = window.open("https://www.example.com/", "_blank");
    if (newWin == null) {
        blocked = true;
    }
} catch (ex) {
    blocked = true;
}
if (blocked) {
    alert("The popup was blocked!");
}
````

### 定时器
JS在浏览器中是单线程执行的,但允许使用定时器指定在某个时间后或每隔一段时间就执行相应的代码.`setTimeout()`用于指定在一段时间后执行某些代码,而`setInterval()`用于指定每隔一段时间执行某些代码.

`setTimeout`接收任意长的参数,其中,第一个参数是要执行的函数,第二个参数是调用函数前要等待的时间(毫秒),后面的参数是要调用执行函数的参数:
````JS
setTimeout(console.log, 1000, 1);   // (1秒后) 1
````

第二个参数不是执行代码的确切时间,因为`setTimeout`在指定毫秒数之后会把任务添加到任务队列中(详见[期约与异步函数](#期约与异步函数)),而不是立即执行代码.

上述函数返回一个表示该超时排期的数值ID.这个超时ID是被排期执行代码的唯一标识符,用于取消该任务.要取消等待中的排期任务,可以调用`clearTimeout()`方法并传入超时ID:
````JS
let timeoutId = setTimeout(console.log, 1000, 1);
clearTimeout(timeoutId);
// <无输出>
````

注意:传入`setTimeout`函数始终会在全局作用域中的一个匿名函数中运行,因此函数中的`this`在非严格模式下始终指向`window`,而在严格模式下是`undefined`.如果函数是箭头函数,则`this`保留为定义它时所在的作用域.

`setInterval()`的参数与`setTimeout()`相同,但指定的任务会每隔指定时间就执行一次,直到取消循环定时或者页面卸载:
````JS
setInterval(console.log, 1000, 1);
// (1秒后) 1
// (2秒后) 1
// (3秒后) 1
// (4秒后) 1
// ...
````

注意:浏览器并不关心`setInterval()`中上一个排期的任务是否执行或者执行完成,只要间隔时间一到,就会向任务队列中添加下一个任务,此时,上一个循环任务可能会因此跳过,因此该函数很少使用.要实现类似的效果,可以使用`setTimeout()`配合循环.

`setInterval()`方法返回一个循环定时ID,用于在未来某个时间点上使用`clearInterval()`并传入定时ID来取消循环定时:
````JS
let num = 0, intervalId = null;
let max = 10;
let incrementNumber = function() {
    console.log(++num);
    if (num == max) {
        clearInterval(intervalId);
        console.log("Done");
    }
}
intervalId = setInterval(incrementNumber, 100);
````

### 系统对话框
`alert()`,`confirm()`和`prompt()`方法可以让浏览器调用系统对话框向用户显示消息.这些对话框与网页无关(即不包括HTML和CSS,外观由操作系统或者浏览器决定).这些对话框都是同步的模态对话框,即在它们显示的时候,代码会停止运行,消失之后,代码才会恢复执行.

`alert()`方法只接收一个要显示给用户的字符串.调用后会显示一个对话框,其中只有一个确定按钮.传入任何不是字符串的参数都会调用`toString()`方法将其转换为字符串.警告框(alert)通常用于向用户显示一些他们无法控制的消息,比如报错.
````JS
alert("Hello world");
````
![alert()](img/get_start/alert.png)

确认对话框使用`confirm()`方法来显示.其参数与`alert()`相同.确认框有两个按钮:"取消"和"确定",用户通过单击不同的按钮表明希望接下来执行什么操作.该方法返回`true`(当单击"确定"时)或`false`(当单击"取消"或者关闭确认框时):
````JS
if (confirm("Are you sure?")) {
    alert("I'm so glad you're sure!");
} else {
    alert("I'm sorry to hear you're not sure.");
}
````
![confirm()](img/get_start/comfirm.png)

提示框通过调用`prompt()`方法来显示.提示框的用途是提示用户输入消息.除了"确定"和"取消"按钮,提示框还会显示一个文本框,让用户输入内容.其接收两个参数:要显示给用户的文本和文本框的默认值.如果用户单击了"确定"按钮,则返回文本框中的值.如果用户单击了"取消"按钮,或者关闭了对话框,则返回`null`:
````JS
let result = prompt("What is your name?", "ABC");
if (result !== null) {
    alert("Welcome, " + result);
}
````
![prompt()](img/get_start/prompt.png)

很多浏览器会在脚本产生两个或更多对话框时,在除第一个以外的对话框上显示一个复选框,让用户选择是否禁用后续的弹框,直到页面刷新.开发者无法获悉这些弹窗是否显示了.上述的对话框计数器会在浏览器空闲时重置,即非连续地独立显示两个警告框不会显示复选框.

`find()`和`print()`对话框是非模态的.用户在浏览器菜单上选择"查找"(find)和"打印"(print)时显示的就是这两种对话框:
````JS
window.print();
window.find();
````
这两个方法不会返回任何有关用户的信息.此外,浏览器的对话框计数器不会涉及它们,而且用户选择禁用对话框对它们也没有影响:

## location对象
`location`是最有用的BOM对象之一,提供了当前窗口中加载文档的信息,以及通常的导航功能.这个对象既是`window`的属性,也是`document`的属性,也就是说,`window.location`和`document.location`指向同一个对象.`location`对象不仅保存着当前加载文档的信息,也保存着把URL解析为离散片段后能够通过属性访问的信息.  
假设浏览器当前加载的URL为`http://foouser:barpassword@www.example.com:80/myPath/?q=javascript#contents`,则:

- `属性`
  - `值` 
  - `说明`
- location.hash
  - "#contents"
  - URL散列值(#后跟零或多个字符),如果没有则为空字符串
- location.host
  - "www.example.com:80"
  - 服务器名及端口号
- location.hostname
  - "www.example.com"
  - 服务器名
- location.href
  - "http://www.example.com:80/myPath/?q=javascript#contents"
  - 当前加载页面的完整URL.`location`的`toString()`方法返回这个值
- location.pathname
  - "/myPath/"
  - URL中的路径和(或)文件名
- location.port
  - "80"
  - 请求的端口.如果URL中没有端口,则返回空字符串
- location.protocol
  - "http:"
  - 页面使用的协议.通常是`http:`或`https:`
- location.search
  - "?q=javascript"
  - URL的查询字符串.这个字符串以问号开头
- location.username
  - "foouser"
  - 域名前指定的用户名
- location.password
  - "barpassword"
  - 域名前指定的密码
- location.origin
  - "http://www.example.com"
  - URL的源地址.只读

### 查询字符串
为了要解析URL中`?`后面的每一个参数(即查询字符串,`location.search`返回值),可以使用以下函数:
````JS
let getQueryStringArgs = function() {
    let qs = (location.search.length > 0 ? location.search.substring(1) : "").
        args = {};
    for (let item of qs.split("&").map(kv => kv.split("="))) {
        let name = decodeURIComponent(item[0]), // 查询字符串通常是被编码后的格式
            value = decodeURIComponent(item[1]);
        if (name.length) {
            args[name] = value;
        }
    }
    return args;
}
let args = getQueryStringArgs();    // 假设查询字符串为?q=javascript&num=10
console.log(args["q"]);     // "javascript"
console.log(args["num"]);   // "10"
````

#### URLSearchParams
`URLSearchParams`提供了一组标准API方法,通过它们可以检查和修改查询字符串.给`URLSearchParams`构造函数传入一个查询字符串,就可以创建一个实例.这个实例暴露了`get()`,`set()`和`delete()`等方法,可以对查询字符串执行相应的操作:
````JS
let qs = "?q=javascript&num=10";
let searchParams = new URLSearchParams(qs);
console.log(searchParams.toString());   // " q=javascript&num=10"
searchParams.has("num");    // true
searchParams.get("num");    // 10
searchParams.set("page", "3");
console.log(searchParams.toString());   // " q=javascript&num=10&page=3"
searchParams.delete("q");
console.log(searchParams.toString());   // " num=10&page=3"
````

大多数支持`URLSearchParams`的浏览器也支持将`URLSearchParams`的实例用作可迭代对象:
````JS
let qs = "?q=javascript&num=10";
let searchParams = new URLSearchParams(qs);
for (let param of searchParams) {
    console.log(param);
}
// ["q", "javascript"]
// ["num", "10"]
````

### 操作地址
可以通过修改`location`对象修改浏览器的地址.

使用`assign()`方法并传入一个URL来修改浏览器地址:
````JS
location.assign("https://www.example.com");
````
这行代码会立即启动导航到新URL的操作,同时在浏览器历史记录中增加一条记录.如果给`location.href`或`window.location`设置一个URL,也会以同一个URL值调用`assign()`方法.比如下面两行代码都会显式调用`assign()`一样的操作:
````JS
window.location = "https://www.example.com";
location.href = "https://www.example.com";
````
这三种方法中设置`location.href`是最常见的.

修改`location`对象的属性也会修改当前加载的页面.其中,`hash`,`search`,`hostname`,`pathname`,`port`属性被设置为新值之后都会修改当前URL,如:
````JS
// 假设当前URL为https://www.example.com/ABC/
location.hash = "#section1";    // https://www.example.com/ABC/#section1
location.search = "?q=javascript";  // https://www.example.com/ABC/?q=javascript#section1
location.hostname = "www.somewhere.com";    // https://www.somewhere.com/ABC/?q=javascript#section1
location.pathname = "mydir";    // https://www.somewhere.com/mydir/?q=javascript#section1
location.port = 8080;   // https://www.somewhere.com:8080/mydir/?q=javascript#section1
````
除了`hash`以外,只要修改`location`的一个属性,就会导致页面重新加载新URL.但修改`hash`的值仍然会在浏览器历史中增加一条新记录.

通过上面的方法,都是会在浏览器中增加相应的记录的,也可以在用户单击"后退"按钮时,导航到前一个页面.

使用`replace()`方法可以既不增加历史记录,也不能回到前一个.其接收一个URL参数:
````JS
location.replace("https://www.example.com");
````

`reload()`方法能够重新加载当前显示的页面.如果不传参数,页面会以最有效的方式重新加载(有可能从缓存中加载页面).传入`true`作为参数会强制从服务器重新加载:
````JS
location.reload();      // 可能是从缓存中加载
location.reload(true);  // 从服务器加载
````

脚本中位于`reload()`调用之后的代码可能执行也可能不执行,这取决于网络延迟和系统资源等因素.调用`reload()`将会导致浏览器重新执行JS代码,因此不在分支中使用`reload()`可能会导致反复重新加载.

## navigator对象
浏览器一定存在`navigator`对象,但每个浏览器都支持自己的属性.

`navigator`对象实现了`NavigatorID`,`NavigatorLanguage`,`NavigatorOnLine`,`NavigatorContentUtils`,`NavigatorStorage`,`NavigatorStorageUtils`,`NavigatorConcurrentHandware`,`NavigatorPlugins`和`NavigatorUserMedia`接口定义的属性和方法:
- `属性方法`:`说明`
- `activeVrDisplays`:返回数组,包含`ispresenting`属性为`true`的`VRDisplay`实例.
- `appCodeName`:即使在非Mozilla浏览器中也会返回`"Mozilla"`.
- `appName`:浏览器全名.
- `appVersion`:浏览器版本.通常比实际的浏览器版本不一致.
- `battery`:返回暴露`Battery Status API`的`BatteryManager`对象.
- `bulidId`:浏览器的构建编号.
- `connection`:返回暴露`Network Information API`的`NetworkInformation`对象.
- `cookieEnabled`:返回布尔值,表示是否启用了cookie.
- `credentials`:返回暴露`Credentials Management API`的`CredentialsContainer`对象.
- `deviceMemory`:返回单位为GB的设备内存容量.
- `doNotTrack`:返回用户的"不追踪"(do-not-track)设置.
- `geolocation`:返回暴露`GeolocationAPI`的`Geolocation`对象.
- `getVRDisplays()`:返回数组,包含可以的每个`VRDisplay`实例.
- `getUserMedia()`:返回与可用媒体设备硬件关联的流.
- `handwareConcurrency`:返回设备的处理器核心数量.
- `javaEnabled`:返回布尔值,表示浏览器是否启用了Java.
- `language`:返回浏览器的主语言.
- `languages`:返回浏览器偏好的语言数组.
- `locks`:返回暴露`Web Locks API`的`LockManager`对象
- `mediaCapabilities`:返回暴露`Media Capabilities API`的`MediaCapabilities`对象
- `mediaDevices`:返回可用的媒体设备.
- `maxTouchPoints`:返回设备触摸屏支持的最大触点数.
- `mimeTypes`:返回浏览器中注册的MIME类型数组.
- `onLine`:返回布尔值,表示浏览器是否联网.
- `oscpu`:返回浏览器运行设备的操作系统和(或)CPU.
- `permissions`:返回暴露`Permission API`的`Permissions`对象.
- `platform`:返回浏览器运行的系统平台.
- `plugins`:返回浏览器安装的插件数组.在IE中,这个数组包含页面中所有`<embed>`元素.
- `product`:返回产品名称(通常是`"Gecko"`).
- `productSub`:返回产品的额外信息(通常是`Gecko`的版本).
- `registerProtocolHandler()`:将一个网站注册为特定协议的处理程序.
- `requestMediaKeySystemAccess()`:返回一个期约,解决为`MediaKeySystemAccess`对象.
- `sendBeacon()`:异步传输一些小数据.
- `serviceWorker`:返回用来与`ServiceWorker`实例交互的`ServiceWorkerContianer`.
- `share()`:返回当前平台的原生共享机制.
- `storage`:返回暴露`Storage API`的`StorageManager`对象.
- `userAgent`:返回浏览器的用户代理字符串.
- `vendor`:返回浏览器的厂商名称.
- `venderSub`:返回浏览器厂商的更多信息.
- `vibrate()`:触发设备振动.
- `webdriver`:返回浏览器当前是否被自动化程序控制.

### 检测插件
可以通过`plugins`数组来检测浏览器的插件(IE10及以下不行).这个数组中的每一项都包含如下属性:
- `name`:插件名称.
- `description`:插件介绍.
- `filename`:插件的文件名.
- `length`:由当前插件处理的MIME类型数量.
- `MimeType对象`:(需要通过中括号访问)包含4个属性:
  - `description`:描述MIME类型.
  - `enabledPlugin`:指向插件对象的指针.
  - `suffixes`:该MIME类型对应扩展名的逗号分隔的字符串.
  - `type`:完整的MIME类型字符串.

所谓检测插件,就是遍历浏览器中可用的插件,并逐个比较插件的名称,如下:
````JS
// 插件检测,IE10及更低版本无效
let hasPlugin = function(name) {
    name = name.toLowerCase();
    for (let plugin of window.navigator.plugins) {
        if (plugin.name.toLowerCase().indexOf(name) > -1) {
            return true;
        }
    }
    return false;
}
// 检测Flesh
console.log(hasPlugin("Flash"));
````

对于IE10及以下版本,不支持`Netscape`式的插件,需要使用专有的`ActiveXObject`,并尝试实例化特定的插件.IE中的插件是实现为COM对象的,由唯一字符串标识.例如:
````JS
// 在旧版本IE中检测插件
function hasIEPlugin(name) {
    try {
        new ActiveXObject(name);
        return true;
    } catch (ex) {
        return false;
    }
}
// 检测Flash
console.log(hasIEPlugin("ShockwaveFlash.ShockwaveFlash"));
````

将两种方式整合,用于检测特定插件的方法如下:
````JS
// 在所有浏览器中检测Flash
function hasFlash() {
    var result = hasPlugin("Flash");
    if (!result) {
        result = hasIEPlugin("ShockwaveFlash.ShockwaveFlash");
    }
    return result;
}
console.log(hasFlash());
````

`plugins`有一个`refresh()`方法,用于刷新`plugins`属性以反映新安装的插件.这个方法接收一个布尔值参数,表示刷新时是否重新加载页面.如果传入`true`,则所有包含插件的页面都会重新加载.否则,只有`plugins`会更新,但页面不会重新加载.

### 注册处理程序
`navigator`支持`registerProtocolHandler()`方法.这个方法可以把一个网站注册为处理某种特定类型信息应用程序.可以借助这个方法将Web应用程序注册为像桌面软件一样的默认应用程序.

要使用`registerProtocolHandler()`方法,必须传入3个参数:要处理的协议(如"mailto"或"ftp"),处理该协议的URL,以及应用名称.例如,要把一个Web应用程序注册为默认邮件客户端,可以这样做:
````JS
navigator.registerProtocolHandler("mailto",
    "http://www.somemailclient.com?cmd=%s",
    "Some Mail Client");
````
这个例子为`"mailto"`协议注册了一个处理程序,这样邮件地址就可以通过指定的Web应用程序打开.第二个参数是负责处理请求的URL,`%s`表示原始的请求.

## screen对象
`window`的另一个属性`screen`对象,在编程中很少使用.这个对象保存的纯粹是客户端能力的信息,即显示器的信息:
- `属性`:`说明`
- `availHeight`:屏幕像素高度减去系统组件高度(只读).
- `availLeft`:没有被系统组件占用的屏幕的最左侧像素(只读).
- `availTop`:没有被系统组件占用的屏幕的最顶端像素(只读).
- `availWidth`:屏幕像素高度减去系统组件宽度(只读).
- `colorDepth`:表示屏幕颜色的位数,多数系统是32(只读).
- `height`:屏幕像素高度.
- `left`:当前屏幕左边的像素距离.
- `pixelDepth`:屏幕的位深(只读).
- `top`:当前屏幕顶端的像素距离.
- `width`:屏幕像素宽度.
- `orientation`:返回`Screen Orientation API`中屏幕的朝向.

## history对象
`history`对象表示当前窗口首次使用以来用户的导航历史记录.每个`window`都有自己的`history`对象.出于安全考虑,这个对象不会暴露用户访问过的URL,但可以通过它在不知道实际URL的情况下前进和后退.

### 导航
`go()`方法可以在用户历史记录中沿任何方向导航,可以前进也可以后退.这个方法只接受一个参数,这个参数可以是一个整数(在旧版浏览器还允许传入字符串),表示前进或后退多少步.负值表示在历史记录中后退(类似点击浏览器的"后退"按钮),而正值表示在历史记录中前进(类似点击浏览器的"前进"按钮):
````JS
// 后退一页
history.go(-1);
// 前进一页
history.go(1);
// 前进两页
history.go(2);
````

`go()`还有两个简写方法:`back()`和`forword()`.这两个方法模拟了浏览器的后退和前进按钮.

`history`对象还有一个`length`属性,表示历史记录中有多个条目.这个属性反映了历史记录的数量.对于窗口或标签页中加载的第一个页面,`history.length`等于1.

### 历史状态管理
`hashchange`会在页面URL的散列变化是被触发,开发者可以在此时执行某些操作.而状态管理API则可以让开发者改变浏览器URL而不会加载新页面.为此,可以使用`history.pushState()`方法.这个方法接收3个参数:一个state对象,一个新状态的标题和一个(可选的)相对URL.例如:
````JS
let stateObject = {foo: "bar"};
history.pushState(stateObject, "my title", "baz.html");
````

`pushState()`方法执行后,状态信息就会被推到历史记录中,浏览器地址栏也会改变以反映新的相对URL.除了这些变化以外,即使`location.href`返回的是地址栏中的内容,浏览器页不会向服务器发送请求.第二个参数并未被当前实现所使用.第一个参数应该包含正确初始化页面状态所必需的信息.这个状态对象的大小是有限制的,通常在500KB~1MB之间(为防止滥用).

`pushState()`会创建新的历史记录,此时单击"后退"按钮,就会触发`window`对象上的`popstate`事件.该事件对象有一个`state`属性,其中包含通过`pushState()`第一个参数传入的`state`对象:
````JS
window.addEventListListener("popstate", (event) => {
    let state = event.state;
    if (state) {    // 第一个页面加载时状态是null
        processState(state);
    }
});
````

基于这个状态,应该把页面重置为状态对象所表示的状态.可以通过`history.state`获取当前的状态对象,也可以使用`replaceState()`并传入与`pushState()`同样的前两个参数来更新状态对象.更新状态不会创建新历史记录,只会覆盖当前状态:
````JS
history.replaceState({newFoo: "newBar"}, "New title");
````

传给`pushState()`和`replaceState()`的`state`对象应该只包含可以被序列化的信息.因此DOM元素之类并不适合放到状态对象里保存.

状态管理时,应当确保`pushState()`创建URL背后都对应一个真实的物理URL,即使不会被使用.否则,单击"刷新"按钮会导致404错误.

# 客户端检测
由于现实中,浏览器之间总会有莫名的差异,客户端检测成为了一种补救措施以及开发策略的重要一环.

## 能力检测
能力检测,即在JS运行时测试浏览器是否持某种特性.这种方式不要求事先知道浏览器的信息,只需要检测自己关心的能力是否存在即可.能力检测的基本模式如下:
````JS
if (object.propertyInQuestion) {
    // 使用object.propertyInQuestion
}
````

例如:
````JS
function getElement(id) {
    if (document.getElementById) {
        return document.getElementById(id);
    } else if (document.all) {
        return document.all[id];
    } else {
        throw new Error("No way to retrieve element!");
    }
}
````

应当先检测最有可能的方式.不能通过检测一个属性或方法从而假定另一个属性或方法的存在(或确定用户所使用的浏览器).

### 安全能力检测
能力检测应当验证存在的同时,确保其能够展现出预期的行为.  
例如,要前侧是否存在排序函数不应该检测:
````JS
function isSortable(object) {
    return !!object.sort;
}
````
应为上述`sort`可能是一个属性而非方法,使用`()`可能会抛出错误.应当使用:
````JS
function isSortable(object) {
    return typeof object.sort == "function";
}
````

有些时候这种方法可能会失效,要深入理解JS能力检测,详见:[Feature Detection: State of the Art Browser Scripting](http://peter.michaux.ca/articles/feature-detection-state-of-the-art-browser-scripting)

### 基于能力检测进行浏览器分析
#### 检测特性
可以按照能力将浏览器归类:
````JS
// 检测浏览器是否支持Netscape式插件
let hasNSPlugins = !!(navigator.plugins && navigator.plugins.length);
````

#### 检测浏览器
根据对浏览器特性的检测并与已知特性对比,可以确认用户使用的是什么浏览器.但对于符合标准的浏览器,可能不会适用.  
例如:
````JS
class BrowserDetector {
    constructor() {
        // 测试条件编译;IE6~10支持
        this.isIE_Gte6Lte10 = /*@cc_on!@*/false;

        // 测试documentMode;IE7~11支持
        this.isIE_Gte7Lte11 = !!document.documentMode;

        // 测试StyleMedia构造函数;Edge20及以上支持
        this.isEdge_Gte20 = !!window.styleMedia;

        // 测试Firebox专有扩展安装API;所有版本的Firebox都支持
        this.isFirefox_Gte1 = typeof InstanllTrigger !== 'undefined';

        // 测试chrome对象及其webstore属性;Opera的某些版本有window.chrome,但没有window.chrome.webstore;所有版本的Chrome都支持
        this.isChrome_Gte1 = !!window.chrome && !!window.chrome.webstore;

        // Safari早期版本会给构造函数的标签符追加"Constructor"字样;Safari 3~9.1支持
        this.isSafari_Gte3Lte9_1 = /constructor/i.test(window.Element);

        // 推送通知API暴露在window对象上,适用默认参数值以避免对undefined调用toString();Safari 7.1及以上版本支持
        this.isSafari_Gte7_1 = 
            (({pushNotification = {}} = {}) =>
              pushNotification.toString() == '[object SafariRemoteNotification]'
            )(window.safari);

        // 测试addons属性;Opera 20及以上版本支持
        this.isOpera_Gte20 = !!window.opr && !!window.opr.addons;
    }
    isIE() { return this.isIE_Gte6Lte10 || this.isIE_Gte7Lte11; }
    isEdge() { return this.isEdge_Gte20 && !this.isIE(); }
    isFirefox() { return this.isFirefox_Gte1; }
    isChrome() { return this.isChrome_Gte1; }
    isSafari() { return this.isSafari_Gte3Lte9_1 || this.isSafari_Gte7_1; }
    isOpera() { return this.isOpera_Gte20; }
}
// 随着浏览器变迁和发展,可以不断调整上述底层检测逻辑
````

#### 能力检测的局限
通过检测一种或一组能力,并不总能确定使用的是哪种浏览器.
````JS
let isFirefox = !!(navigator.vendor && navigator.vendorSub);    // 不够特殊,Safari后来也实现了同样的属性
let isIE = !!(document.all && document.uniqueID);   // 假设太多
````

## 用户代理检测
用户代理检测通过浏览器用户代理字符串确定使用的是什么浏览器.用户代理字符串包含在每个HTTP请求的头部,在JS中可以通过`navigator.userAgent`访问.在服务器段,可以根据用户代理字符串确定浏览器并执行相应操作.而在客户端,用户代理检测被认为是不可靠的,只应该在没有其他选项时再考虑.

> 基于用户代理字符串来识别浏览器是**不可靠**的且**不推荐**,因为用户代理字符串是可以由用户配置的.

在很长一段时间里,浏览器都通过在用户代理字符串包含错误或误导性信息来欺骗服务器:
- `Mosaic`(早期浏览器)的代理字符串类似于:`Mosaic/0.9`
- `Netscape Navigator`(Mozilla)浏览器的代理字符串格式为:`Mozilla/Version [Language] (Platform; Encryption)`
- 微软为了让`IE`能打开检测是否为`Netscape Navigator`的浏览器,使其代理字符串格式为:`Mozilla/Version (Platform; Encryption [; OS-or-CPU description])`
- `Firebox`的渲染引擎`Gecko`使用的代理字符串格式为:`Mozilla/MozillaVersion (...)`
- `Safari`浏览器的渲染引擎为`WebKit`,为了让浏览器不被排除在流行站点以外,其代理字符串格式为:`Mozilla/5.0 (...) AppleWebKit/AppleWebKitVersion (...) Safari/SafariVersion`
- `Konqueror`浏览器的渲染引擎为`KHTML`.为了实现最大化兼容,其采用的代理字符串格式为:`Mozilla/5.0 (...; Konqueror/Version; ...)`
- `Chrome`使用`Blink`作为渲染引擎,使用`V8`作为JS引擎.其用户代理字符串包含所有`WebKit`信息:`Mozilla/5.0 (...) AppleWebKit/AppleWebKitVersion (...) Chrome/ChromeVersion Safari/SafariVersion`
- `Opera`在`Opera 8`及以前的格式为:`Opera/Version (...)`;但在`Opera 9`时,会在不同网站伪装成`Firebox`或`IE`且不通知用户;而在`Opera 10`时,其用户代理字符串变成了:`Opera/9.80 (OS-or-CPU; Encryption; Language) Presto/PrestoVersion Version/Version`
- 对于`iOS`与`Android`,系统默认的浏览器都是基于`WebKit`的,因此与`Safari`相似,但会加上`like Mac OS X`来表示这是和`Mobile`相关的.

### 浏览器分析
#### 伪造用户代理
用户代理是可以造假的,即使`window.navigator.userAgent`是只读的.

在某些浏览器,可以使用浏览器私有的`__defineGetter__`方法来篡改用户代理字符串:
````JS
console.log(window.navigator.userAgent);
// Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/130.0.0.0 Safari/537.36 Edg/130.0.0.0
window.navigator.__defineGetter__('userAgent', () => 'foobar');
console.log(window.navigator.userAgent);    // foobar
````
在`Firefox`中,可以通过`about:config`修改`general.useragent.override`偏好设置来更改用户代理.

`Opera 6`及更高版本允许用户通过菜单设置浏览器标识字符串.

#### 分析浏览器
通过解析浏览器返回的用户代理字符串,可以推断出下列相关的环境信息:
- 浏览器
- 浏览器版本
- 浏览器渲染引擎
- 设备类型(桌面/移动)
- 设备生产商
- 设备型号
- 操作系统
- 操作系统版本

但新浏览器,新操作系统,新硬件设备随时可能出现,因此,用户代理解析程序需要与时俱进,频繁更新.可以使用以下第三方用户代理解析程序:
- [Bowser](https://github.com/bowser-js/bowser)
- [UAParser.js](https://github.com/faisalman/ua-parser-js)
- [Platform.js](https://github.com/bestiejs/platform.js)(archived)
- [CURRENT-DEVICE](https://github.com/matthewhudson/current-device)
- [Google Closure](https://github.com/google/closure-library)(archived)
- [Mootools](https://github.com/mootools/mootools-core)

[Mozilla wiki - Compatibility/UADetectionLibraries](https://wiki.mozilla.org/Compatibility/UADetectionLibraries)提供了用户代理解析程序的列表(JS部分包含客户端库和`Node.js`库).

## 软件与硬件检测
通过暴露在`window.navigator`上的一组API,可以获得一组与页面执行环境相关的信息,包括浏览器,操作系统,硬件和周边设备信息.

*注意:其中很多API不是强制性的,且很多浏览器没有支持,有些特性也不一定可靠.*

### 识别浏览器与操作系统
- `navigator.oscpu`:其标准要求返回空字符串或者表示浏览器所在平台的字符串,比如:`"Windows NT 10.0; Win64; x64"`或`"Linux x86_64"`.
- `navigator.vendor`:通常包含浏览器开发商信息.返回这个字符串是浏览器`navigator`兼容模式的一个功能.其标准要求返回一个空字符串,也可能返回字符串`"Apple Computer, Inc."`或字符串`"Google Inc."`.
- `navigator.platform`:其标准要求返回一个空字符串或表示浏览器所在平台的字符串,例如`"MacIntel"`,`"Win32"`,`"FreeBSD i386"`或`"WebTV OS"`.
- `screen.colorDepth`和`screen.pixelDepth`:其标准要求返回输出设备中每像素用于显示颜色的位数,不包含`alpha`通道.
- `screen.orientation`:返回一个`ScreenOrientation`对象,其中包含`Screen Orientation API`定义的屏幕信息:
  - `angle`:返回相对于默认状态下屏幕的角度(不能假设`0`始终是初始值).
  - `type`:返回以下4中枚举值之一(不能假设`portrait-primary`始终是初始值):
    - `portrait-primary`
    - `portrait-secondary`
    - `landscape-primary`
    - `landscape-secondary`

### 浏览器元数据
`navigator`对象暴露出一些API,可以提供浏览器和操作系统的状态信息.

#### Geolocation API
`navigator.geolocation`属性暴露了`Geolocation API`,可以让浏览器脚本感知当前设备的地理位置.这个API只在安全执行环境(通过HTTPS获取的脚本)中可用.根据不同的配置,返回结果的精度可能不一样.

`Geoloaction API`规范规定:地理位置信息的主要来源是GPS和IP地址,射频识别(RFID),`Wi-Fi`及蓝牙Mac地址,`GSM/CDMA`蜂窝ID以及用户输入等信息.

*注意:有时候并没有GPS,此时浏览器会收集所有可用的无线网络,包括`Wi-Fi`和蜂窝信号.拿到这些信号后,再去查询网络数据库.这样就可以精确地报告出你的设备位置.*

`getCurrentPosition()`方法返回一个`Coordinates`对象:
````JS
let p;
navigator.geolocation.getCurrentPosition((position) => p = position);
console.log(p.timestamp);   // 1525364883361
console.log(p.coords);      // Coordinates {...}
````
上述代码中,`timestamp`表示查询时间的时间戳.浏览器可能会不允许访问这些数据(或者等待用户选择允许/拒绝该权限),因此见下文对第二个参数的描述.

`Coordinates`对象包含:
- `latitude`:经度,例如`37.4854409`.
- `longitude`:纬度,例如`-122.2325506`.
- `accuracy`:精度,单位为米,例如:`58`.
- `altitude`:海拔高度,相对于1984世界大地坐标系地球表面以米为单位的距离(可能为空).
- `altitudeAccuracy`:海拔高度的精度,单位为米(可能为空).
- `speed`:表示设备每秒移动的速度.
- `heading`:朝向,表示相对于正北方向移动的角度(0<=`heading`<360).

`getCurrentPosition()`方法的接收第二个参数(回调函数)作为获取失败时调用的函数,这个函数会收到一个`PositionError`对象,其中包含:
- `code`:一个整数,表示以下3中错误:
  - `PERMISSION_DENIED`:浏览器未被允许访问设备位置.页面第一次尝试访问`Geolocation API`时,浏览器会弹出确认对话框取得用户授权(每个域分别获取).如果返回了这个错误码,则要么是用户不同意授权,要么是在不安全的环境下访问了`Geolocation API`.`message`属性还会提供额外信息.
  - `POSITION_UNAVAILABLE`:系统无法返回任何位置信息.这个错误码可能代表各种失败原因,但相对来说并不常见,因为只要设备能上网,就至少可以根据IP地址返回一个低精度的坐标.
  - `TIMEOUT`:系统不能在超时时间内返回位置信息,例如用户在超时前未选择是否授权,见下文.
- `message`:包含对错误的简短描述.

例如:
````JS
navigator.geolocation.getCurrentPosition(
    () => {},
    (e) => {
        console.log(e.code);
        console.log(e.message);
    }
);
````

`Geolocation API`可以使用`PositionOptions`对象来配置,作为第三个参数提供.这个对象支持以下3个属性:
- `enableHighAccuracy`:布尔值,`true`表示返回的值应该尽可能精确,默认值为`false`.默认情况下,设备通常会选择最快,最省电的方式返回坐标.在`true`时,则会使用设备的GPS确定设备位置,并返回与其他方式获取值的混合效果,这种方式更加耗时耗电.
- `timeout`:毫秒,表示在以`TIMEOUT`状态调用错误回调函数之前等待的最长时间.默认值是`0xFFFFFFFF`.`0`表示完全跳过系统调用而立即以`TIMEOUT`调用错误回调函数.
- `maximunAge`:毫秒,表示返回坐标的最长有效期,默认值为`0`.因为查询设备位置会消耗资源,所以系统通常会缓存坐标并在下次返回缓存的值(遵从位置缓存失效策略).系统会计算缓存期,如果`Geolocation API`请求的配置要求比缓存的结果更新,则系统才会重新查询并返回值.`0`表示强制系统忽略缓存的值,每次都重新查询.`Infinity`会阻止系统重新查询,只会返回缓存的值.JS通过检查`Position`对象的`timestamp`属性是否重复来判断返回的是否是缓存值.

#### Connection State和NetworkInformation API
浏览器会跟踪网络连接状态并以两种方式暴露这些信息:连接事件和`navigator.onLine`属性.在设备连接网络时,浏览器会记录并在`window`对象上触发`online`事件,断开连接会在`window`对象上触发`offline`事件.任何时候,都可以通过`navigator.onLine`属性来确定浏览器的联网状态.这个属性返回一个布尔值,表示浏览器是否联网(由浏览器与系统定义,有些连接到局域网就算"在线",即使没有连接到互联网).

`navigator.connection`返回暴露了`NetworkInformation API`的对象,这个API提供了一些只读属性,并为连接属性变化事件处理程序定义了一个事件对象:
- `downlink`:整数,表示当前设备的带宽(以`Mbit/s`为单位),舍入到最接近的`25kbit/s`.
- `downlinkMax`:整数,表示当前设备最大的下行带宽(以`Mbit/s`为单位),根据网络的第一跳来确定.
- `effectiveType`:字符串枚举值,表示连接速度和质量.这些值对应不同的蜂窝数据网络连接技术,但也用于分类无线网络.这个值有以下4种可能:
  - `slow-2g`:往返时间不小于`2000ms`,下行带宽小于`50kbit/s`.
  - `2g`:往返时间小于`2000ms`但不小于`1400ms`,下行带宽小于`70kbit/s`但不小于`50kbit/s`.
  - `3g`:往返时间小于`1400ms`但不小于`270ms`,下行带宽小于`700kbit/s`但不小于`70kbit/s`.
  - `4g`:往返时间小于`270ms`,下行带宽不小于`700kbit/s`.
- `rrt`:毫秒,表示当前网络实际的往返时间,舍入为最接近的25毫秒.
- `type`:字符串枚举值,表示网络连接技术.这个值可能为下列值之一:
  - `bluetooth`:蓝牙.
  - `cellular`:蜂窝.
  - `ethernet`:以太网.
  - `none`:无网络连接.相当于`navigator.onLine === false`.
  - `mixed`:多种网络混合.
  - `other`:其他.
  - `unknown`:不确定.
  - `wifi`:Wi-Fi.
  - `wimax`:WiMAX.
- `saveData`:布尔值,表示用户设备是否启用了"节流"模式.
- `onchange`:事件处理程序,会在任何连接状态变化时激发一个`change`事件.可以通过`navigator.connection.addEventListener('change',changeHandler)`或`navigator.connection.onchange = changeHandler`等方式使用.

#### Battery Status API
浏览器可以访问设备电池及充电状态的信息.`navigator.getBattery()`方法会返回一个期约实例,解决为一个`BatteryManager`对象.
````JS
navigator.getBattery().then((b) => console.log(b));
// BatteryManager { ... }
````

`BatteryManager`包含4个只读属性,提供设备电池的相关信息:
- `charging`:布尔值,表示设备当前是否正接入电源充电.如果设备没有电池,则返回`true`.
- `chargingTime`:整数,表示预计离电池充满还有多少秒.如果电池已充满或设备没有电池,则返回`0`.
- `dischargingTime`:整数,表示预计离电池耗尽还有多少秒.如果设备没有电池或正在充电,则返回`Infinity`.
- `level`:浮点数,表示电量百分比.电量完全耗尽返回`0.0`,电池充满返回`1.0`.如果设备没有电池,则返回`1.0`.

这个API还提供了4个事件属性,可用于设置在相应的电池事件发生时调用的回调函数.可以通过给`BatteryManager`添加事件监听器,也可以通过给事件属性赋值来使用这些属性:
- `onchargingchange`:充电状态变化时.
- `onchargingtimechange`:充电时间变化时.
- `ondischargingtimechange`:放电时间变化时.
- `onlevelchange`:电量百分比变化时.

### 硬件
浏览器检测硬件的能力相当有限.

- `navigator.handwareConcurrency`属性返回浏览器支持的逻辑处理器核心数量,包含表示核心数的一个整数值(如果核心数无法确定,这个值就是`1`).这个值表示浏览器可以并行执行的最大工作线程数量,不一定是实际的CPU核心数.
- `navigator.deviceMemory`属性返回设备大致的系统内存大小,包含单位为`GB`的浮点数(舍入为最接近的`2`的幂:512MB->0.5,4GB->4).
- `navigator.maxTouchPoints`属性返回触摸屏支持的最大关联触点数量,包含一个整数值.

# DOM
文档对象模型是`HTML`和`XML`文档的编程接口.`DOM`表示由多个节点构成的文档,通过它开发者可以添加,删除和修改页面的各个部分.`DOM`是跨平台,语言无关的表示和操作页面的方法.

`JS`中提供了`DOM API`并且它与浏览器中的`HTML`网页相关.

*注:IE8以下的DOM是由COM对象实现的,因此与原生的JS对象会有不同的行为和功能.*

DOM操作在JS代码中是代价比较高的,`NodeList`对象尤其需要注意.因此,实践中要尽量减少DOM操作的数量.

## 节点层级
任何HTML和XML都可以用DOM表示为一个由节点构成的层级结构.  
例如:
````HTML
<html>
    <head>
        <title>Sample Page</title>
    </head>
    <body>
        <p>Hello World!</p>
    </body>
</html>
````

其DOM层级结构可以表示为:
```
Document
 └-Element (html)
    ├-Element (head)
    |  └-Element (title)
    |     └-Text (Sample Page)
    └-Element (body)
       └-Element (p)
          └-Text (Hello world!)
```
上例中,`document`节点表示每个文档的根节点(文档节点).根节点的唯一子节点是`<html>`元素,叫做`文档元素`.文档元素是文档最外层的元素,所有其他元素都存在于这个元素之内.每个文档只能有**一个文档元素**.在HTML页面中,文档元素始终是`<html>`元素(`<!DOCTYPE>`不属于文档元素,即使它也处于最外层且属于`document`子节点).在XML中,则没有这样的预定义元素.

`HTML`中的每段标记都可以表示为这个属性结构中的一个节点.元素节点表示HTML元素,属性节点表示属性,文档类型节点表示文档类型,注释节点表示注释.`DOM`中总共有12种节点类型,这些类型都继承一种基本类型.

### Node类型
`DOM Level 1`描述了名为`Node`的接口,所有DOM节点类型都必须实现这个接口.`Node`接口在JS中实现为`Node`类型.`IE`除外的所有浏览器都可以直接访问这个类型.JS中,所有节点类型都继承`Node`类型,因此所有类型都共享相同的基本属性和方法.

每个节点都有`nodeType`属性,表示该节点的类型,其通过定义在`Node`类型上的12个数值常量表示:
- `Node.ELEMENT_NODE`(1)
- `Node.ATTRIBUTE_NODE`(2)
- `Node.TEXT_NODE`(3)
- `Node.CDATA_SECTION_NODE`(4)
- `Node.ENTITY_REFERENCE_NODE`(5)
- `Node.ENTITY_NODE`(6)
- `Node.PROCESSING_INSTRUCTION_NODE`(7)
- `Node.COMMENT_NODE`(8)
- `Node.DOCUMENT_NODE`(9)
- `Node.DOCUMENT_TYPE_NODE`(10)
- `Node.DOCUMENT_FRAGMENT_NODE`(11)
- `Node.NOTATION_NODE`(12)

例如:
````JS
if (someNode.nodetype == Node.ELEMENT_NODE) {
    console.log("Node is an element.");
}
````

浏览器并不支持所有节点类型.

#### nodeName于nodeValue
`nodeName`和`nodeValue`保存着有关节点的信息.这两个属性的值完全取决于节点类型,因此最好事先检测节点类型.

#### 节点关系
文档中的所有节点都与其他节点有关系.

每个节点都有一个`childNodes`属性,其中包含一个`NodeList`的实例,存放了其所有的子节点(DOM树).

`NodeList`是一个类数组对象,用于存储可以按位置存取的有序节点.它可以用中括号访问下标,也有`length`属性.`NodeList`独特在于,DOM结构的变化会自动地在`NodeList`中反映出来,所以它是实时的活动对象.

例如:
````JS
let firstChild = someNode.childNodes[0];
let secondChild = someNode.childNodes.item(1);
let count = someNode.childNodes.length;
````

使用中括号和使用`item()`方法是等价的.`length`返回的值不会随DOM结构变化而变化,因为它是原始值.

使用`Array.prototype.slice()`,`Array.from()`等方法可以将`NodeList`转换为数组:
````JS
let arr1 = Array.prototype.slice.call(someNode.childNodes, 0);
let arr2 = Array.from(someNode.childNodes);
````

每个节点都有一个`parentNode`属性,指向其DOM树中的父元素.`childNodes`中的所有节点都指向同一个父元素(节点).`childNodes`列表中的每一个节点都是同一个列表中其他节点的同胞节点.`previousSibling`和`nextSibling`分别指向前驱和后继的同胞节点.列表中第一个节点的`previousSibling`为`null`,最后一个节点的`nextSibling`为`null`.

`firstChild`和`lastChild`分别指向`childNodes`中的第一个和最后一个子节点.如果`childNodes`内没有节点,则这两个属性都是`null`.

`hasChildNodes()`方法返回布尔值,表示是否存在子节点.

`ownerDocument`属性指向代表整个文档的文档节点的指针.所有节点都被创建它们(或自己所在)的文档所拥有.

![节点关系](img/get_start/node_relationship.jpg)

*注:不是所有节点都存在子节点的概念*

#### 操纵节点
所有关系指针都是只读的.但DOM提供了操纵节点的方法.

`appendChild()`用于在`childNodes`列表末尾添加节点(作为唯一的参数).添加新节点会更新相关的关系指针.该方法返回新添加的节点.**一个节点不会在文档中同时出现在两个或更多个地方.因此,传入文档中已经存在的节点会将节点移动到该位置.**对于此函数,会移动为最后一个子节点.
````JS
let returnedNode = someNode.appendChild(newNode);
console.log(returnedNode == newNode);       // true
console.log(someNode.lastChild == newNode); // true
returnedNode = someNode.appendChild(someNode.firstChild);
console.log(returnedNode == someNode.firstChild);   // false
console.log(returnedNode == someNode.lastChild);    // true
````

使用`insertBefore()`方法将节点插入到`childNodes`的特定位置.该方法接收两个参数:要插入的节点和参照节点.调用这个方法后,要插入的节点会变成参照节点的前一个同胞节点.如果参照节点是`null`,则`insertBefore()`的效果同`appendChild()`.该方法返回插入的节点.

`replaceChild()`方法接收两个参数:要插入的节点和要替换的节点.要替换的节点会被返回并从文档中完全移除,要插入的节点会取而代之.但从技术上来讲,被移除的节点仍然被同一个文档所拥有,即使文档中已经没有它的位置.

`removeChild()`接收一个参数,表示要移除的节点.被移除的节点会被返回.被移除的节点仍然被同一个文档所拥有,即使文档中已经没有它的位置.

对于不支持子节点的节点上调用上述方法,会导致抛出错误.

#### 其他方法
`cloneNode()`返回与调用它的节点一模一样但不是同一实例的节点.该方法接收一个布尔值参数,如果传入的是`true`,则会复制节点及其子DOM树.如果传入`false`,则只会复制节点本身.返回的节点属于文档所有,但尚未指定父节点,所以可称为孤儿节点(orphan).

例如:
````HTML
<ul>
    <li>item 1</li>
    <li>item 2</li>
    <li>item 3</li>
</ul>
````
对上述HTML片段使用`cloneNode()`:
````JS
let deepList = myList.cloneNode(true);
console.log(deepList.childNodes.length);    // 3 (IE9之前的版本) 或 7 (其他浏览器)
let shallowList = myList.cloneNode(false);
console.log(shallowList.childNodes.length); // 0
````

*注意:`cloneNode()`方法不会复制添加到DOM节点的JS属性,比如事件处理程序.这个方法只复制HTML属性以及可选的复制子节点,除此以外一概不会复制.IE在很长时间内会复制事件处理程序,这是一个bug.*

`normalize()`用于处理文档子树中的文本节点.它会检测这个节点的所有后代,从中搜索上述两种情形.如果发现空文本节点,则将其删除;如果两个同胞节点是相邻的,则将其合并为一个文本节点.[*见下文*](#规范化文本节点)

### Document类型
`Document`类型是JS中表示文档节点的类型.在浏览器中,文档对象`document`是`HTMLDocument`的实例(`HTMLDocument`继承`Document`),表示整个HTML页面.`document`是`window`对象的属性,因此是一个全局对象.`Document`类型的节点有以下特征:
- `nodeType`等于`9`(`Node.DOCUMENT_NODE`)
- `nodeName`值为`#document`
- `nodeValue`值为`null`
- `parentNode`值为`null`
- `ownerDocument`值为`null`
- 子节点可以是`DocumentType`(最多一个),`Element`(最多一个),`ProcessingInstruction`或`Comment`类型.

`Document`类型可以表示`HTML`页面或其他`XML`文档,但最常用的还是通过`HTMLDocument`的实例取得`document`对象.

#### 文档子节点
`Document`提供了几个访问子节点(不一定是直接子节点)的快捷方式.

(这里使用`document`对象,但是`Document`类型的实例对象也可以使用)  
`document.documentElement`属性始终指向`HTML`页面中的`<html>`元素.

`document.body`属性始终指向`<body>`元素.

`document.doctype`用于访问`<!doctype>`标签(属于`DocumentType`).

出现在`<html>`元素外面的注释也是文档的子节点,它们的类型是`Comment`.不过,针对不同的浏览器,这些注释可能会不被识别.

一般来说,`appendChild()`,`removeChild()`和`replaceChild()`方法一般不会用在`document`对象上.因为文档类型是只读的,而且只能有一个`Element`类型的子节点.

#### 文档信息
`HTMLDocument`上还增加了一些属性.

`title`属性指向`<title>`元素中的文本(不是标签本身).
````JS
// 读取文档标题
let originalTitle = document.title;
// 修改文档标题
document.title = "New page title"
````

`URL`属性包含当前页面的完整URL.`domain`属性包含页面的域名.`referrer`属性包含链接到当前页面的那个页面的URL,如果当前页面没有来源,则`referrer`属性包含空字符串.所有这些信息都可以在请求的HTTP头部信息中获取,只是JS中通过这几个属性暴露出来而已.

例如:
````JS
// 当前URL为https://www.example.com/page/
console.log(document.URL);  // https://www.example.com/page/
console.log(document.domain);   // www.example.com
console.log(document.referrer); // <从哪个网站导航到这个网站的>
````

只有`domain`属性是可以设置的,但条件是页面只能放松,不能收紧,不能重定义向其他服务器:
```
p2p.example.com -> example.com  // OK
www.example.com -> example.com  // OK
example.com -> p2p.example.com  // Error
www.example.com -> p2p.example.com  // Error
example.com -> anothersite.com  // Error
```

这可以用于对不同子域的窗格(`<frame>`)或内嵌窗格(`<iframe>`)(用于在网页中嵌套其他网页),使用`domain`将每个页面设置为相同的域,多个子域之间就可以通信了.

#### 定位元素
`Document`上的方法`getElementById()`接收一个参数,即要获取元素的ID,如果找到了则返回这个元素,如果没找到则返回`null`,区分大小写.

例如:
````HTML
<div id="myDiv">Some text</div>
````
可以使用:
````JS
let div = document.getElementId("myDiv");   // 取得对这个<div>元素的引用
let div2 = document.getElementId("mydiv");  // null
````

如果页面中存在多个具有相同ID的元素,则`getElementById()`返回文档中出现的第一个元素.

`Document`上的方法`getElementsByTagName()`接收一个参数,即要获取元素的标签名,返回包含0个或多个元素的`NodeList`.在`HTML`文档中(使用`HTMLDocument`实例),这个方法返回一个`HTMLCollection`对象.两者很相似,都是"实时"列表.

````JS
let images = document.getElementsByTagName("img");  // 取得包含所有<img>元素的HTMLCollection
````

`HTMLCollection`可以使用中括号或者`item()`方法索引,也可以用`length`属性获取元素数量.

其上还有一个额外的方法`namedItem()`,可通过标签的`name`属性取得某一项的引用.
````HTML
<img src="myimage.jpg" name="myImage">
````
则可以使用以下方法获取对这个`<img>`元素的引用:
````JS
let images = document.getElementsByTagName("img");
let myImage = images.namedItem("myImage");
````
使用中括号接收字符串索引的方式也可以与`namedItem()`方法等价:`images["myImage"]`.

给`getElementsByTagName()`传入`"*"`可以取得文档中的所有元素:
````JS
let allElements = document.getElementsByTagName("*");   // 返回包含页面中所有元素的HTMLCollection对象,顺序是它们在页面中出现的顺序.因此第一项是<html>元素
````

*注意:虽然规范要求`getElementsByTagName()`区分标签的大小写,但为了最大限度兼容原有HTML页面,实际上是不区分大小写的.如果是在`XML`页面(例如`XHTML`)中使用,那么`getElementsByTagName()`就是区分大小写的.*

`HTMLDocument`类型上还定义了`getElementsByName()`方法,这个方法会返回具有给定`name`属性的所有元素.该方法最常用于单选按钮,因为同一字段的单选按钮必须具有相同的`name`属性才能确保把正确的值发送给服务器:
````HTML
<fieldset>
    <legend>Which color do you prefer?</legend>
    <ul>
        <li>
            <input type="radio" value="red" name="color" id="colorRed">
            <label for="colorRed">Red</label>
        </li>
        <li>
            <input type="radio" value="green" name="color" id="colorGreen">
            <label for="colorGreen">Green</label>
        </li>
        <li>
            <input type="radio" value="blue" name="color" id="colorBlue">
            <label for="colorBlue">Blue</label>
        </li>
    </ul>
</fieldset>
````
上例中所有单选按钮都有名为`"color"`的`name`属性,但它们的ID都不一样.这是因为ID是为了匹配相应的`<label>`元素,而`name`相同时为了保证只将三个中的一个值发送给服务器.  
可以通过下面的方法取得所有单选按钮:
````JS
let radios = document.getElementsByName("color");
````

`getElementsByName()`方法返回`HTMLCollection`.不过在这种情况下,`namedItem()`方法只会取得第一项(因为所有项的`name`属性都一样).

#### 特殊集合
`HTMLDocument`的实例对象上还暴露了几个特殊属性,它们是`HTMLCollection`的实例:
- `document.anchors`:包含文档中所有带`name`属性的`<a>`元素.
- `document.applets`*(已废弃)*:包含文档中所有`<applet>`*(已废弃)*元素.
- `document.forms`:包含文档中所有`<form>`元素(与`document.getElementsByTagName("form")`返回结果相同).
- `document.images`:包含文档中所有`<img>`元素(与`document.getElementsByTagName("img")`返回结果相同).
- `document.links`:包含文档中所有带`href`属性的`<a>`元素.

上述属性的内容也会实时更新以符合当前文档的内容.

#### DOM兼容性检测

> **<b class="red_font">已弃用,请不要在新的网站中使用</b>**

`DOM`有多个Level和多个部分,因此确定浏览器实现了DOM的那些部分是很必要的.

`document.implementation`上定义了一个方法,即`hasFeature()`(已弃用),这个方法接收两个参数:特性名称和DOM版本.如果浏览器支持指定的特性和版本,则`hasFeature()`方法返回`true`:`let hasXmlDom = document.implementation.hasFeature("XML", "1.0")`;

#### 文档写入
`Document`类型的对象有4个方法:`write()`,`writeln()`,`open()`,`close()`.

**<p class="yellow_font">注意:强烈不建议使用`write()`和`writeln()`方法.XHTML文档也不支持文档写入.对于内容类型为`application/xml+xhtml`的页面,这些方法不起作用.</p>**

`write()`和`writeln()`方法都接收一个字符串参数,可以将这个字符串写入网页中.`write()`简单地写入文本,而`writeln()`会在字符串末尾追加一个换行符(`\n`).

例如:
````HTML
<html>
<head>
    <title>example<title>
</head>
<body>
    <script type="text/javascript">
        document.write("<script type=\"text/javascript\" src=\"test.js\">" + "<\/script>"); // 不能直接写成/script,因为这会导致被解析为脚本块的结尾.
        // 此文字会写在该JS脚本的后面
    </script>
</body>
</html>
````
如果是在页面加载结束之后用`write()`向文档输出内容,则输出内容会重写整个页面(整个HTML的内容都变成了`write()`的字符串参数值).
````JS
window.onload = function() {
    document.write("Hello world");
};
````

`open()`和`close()`方法用于打开和关闭网页输出流.在调用`write()`和`writeln()`时,这两个方法都不是必需的.

### Element类型
`Element`类型表示`XML`或`HTML`元素,对外暴露出访问元素标签名,子节点和属性的能力.其特征如下:
- `nodeType`等于`1`(`Node.ELEMENT_NODE`)
- `nodeName`值为元素的标签名
- `nodeValue`值为`null`
- `parentNode`值为`Document`或`Element`对象
- 子节点可以是`Element`,`Text`,`Comment`,`ProcessingInstruction`,`CDATASection`,`EntityReference`类型.

使用`nodeName`或`tagName`属性来获取元素的标签名,这两个属性的返回值相同:
````HTML
<div id="myDiv"></div>
````
````JS
let div = document.getElementById("myDiv");
console.log(div.tagName);   // DIV
console.log(div.tagName === div.nodeName);  // true
````

在HTML中,元素标签名始终以全大写表示,在XML(包括XHTML)中,标签名始终与源代码的大小写一致.因此,最好将标签名转换为小写形式,以便于比较:
````JS
if (element.tagName.toLowerCase() == "div") {   // 推荐
    // do something
}
````

#### HTML元素
所有HTML元素都通过`HTMLElement`类型(直接继承自`Element`)标识,包括其直接实例或间接实例.

所有`HTMLElement`都有以下属性:
- `id`:id属性
- `title`:title属性
- `lang`:lang属性
- `dir`:dir属性
- `className`:class属性

例如:
````HTML
<div id="myDiv" class="bd" title="Body text" lang="en" dir="ltr"></div>
````
可以使用JS代码读取或修改上述元素的属性:
````JS
let div = document.getElementById("myDiv");
console.log(div.id);        // myDiv
console.log(div.className); // bd
console.log(div.title);     // Body text
console.log(div.lang);      // en
console.log(div.dir);       // ltr
div.id = "someOtherId";     // 可以修改,会实时更新
````

所有HTML元素都是`HTMLElement`或其子类型的实例,以下是所有HTML元素及其对应的类型(删除线表示已经废弃的元素):
- `元素(小写表示)`:`类型`
- `a`:`HTMLAnchorElement`
- `abbr`:`HTMLElement`
- <s>`acronym`:`HTMLElement`</s>
- <s>`applet`:`HTMLAppletElement`</s>
- `area`:`HTMLAreaElement`
- `b`:`HTMLElement`
- `base`:`HTMLBaseElement`
- <s>`basefont`:`HTMLBaseFontElement`</s>
- `bdo`:`HTMLElement`
- <s>`big`:`HTMLElement`</s>
- `blockquote`:`HTMLQuoteElement`
- `body`:`HTMLBodyElement`
- `br`:`HTMLBRElement`
- `button`:`HTMLButtonElement`
- `caption`:`HTMLTableCaptionElement`
- <s>`center`:`HTMLElement`</s>
- `cite`:`HTMLElement`
- `code`:`HTMLElement`
- `col`:`HTMLTableColElement`
- `colgroup`:`HTMLTableColElement`
- `dd`:`HTMLElement`
- `del`:`HTMLModElement`
- `dfn`:`HTMLElement`
- <s>`dir`:`HTMLDirectoryElement`</s>
- `div`:`HTMLDivElement`
- `dl`:`HTMLDListElement`
- `dt`:`HTMLElement`
- `em`:`HTMLElement`
- `fieldset`:`HTMLFieldSetElement`
- <s>`font`:`HTMLFontElement`</s>
- `form`:`HTMLFormElement`
- <s>`frame`:`HTMLFrameElement`</s>
- <s>`frameset`:`HTMLFrameSetElement`</s>
- `h1`:`HTMLHeadingElement`
- `h2`:`HTMLHeadingElement`
- `h3`:`HTMLHeadingElement`
- `h4`:`HTMLHeadingElement`
- `h5`:`HTMLHeadingElement`
- `h6`:`HTMLHeadingElement`
- `head`:`HTMLHeadElement`
- `hr`:`HTMLHRElement`
- `html`:`HTMLHtmlElement`
- `i`:`HTMLElement`
- `iframe`:`HTMLIFrameElement`
- `img`:`HTMLImageElement`
- `imput`:`HTMLInputElement`
- `ins`:`HTMLModElement`
- <s>`isindex`:`HTMLIsIndexElement`</s>
- `kbd`:`HTMLElement`
- `label`:`HTMLLabelElement`
- `legend`:`HTMLLegendElement`
- `li`:`HTMLLIElement`
- `link`:`HTMLLinkElement`
- `map`:`HTMLMapElement`
- <s>`menu`:`HTMLMenuElement`</s>
- `meta`:`HTMLMetaElement`
- <s>`noframes`:`HTMLElement`</s>
- `noscript`:`HTMLElement`
- `object`:`HTMLObjectElement`
- `ol`:`HTMLOListElement`
- `optgroup`:`HTMLOptGroupElement`
- `option`:`HTMLOptionElement`
- `p`:`HTMLParagraphElement`
- <s>`param`:`HTMLParamElement`</s>
- `pre`:`HTMLPreElement`
- `q`:`HTMLQuoteElement`
- `s`:`HTMLElement`
- `samp`:`HTMLElement`
- `script`:`HTMLScriptElement`
- `select`:`HTMLSelectElement`
- `small`:`HTMLElement`
- `span`:`HTMLElement`
- <s>`strike`:`HTMLElement`</s>
- `strong`:`HTMLElement`
- `style`:`HTMLStyleElement`
- `sub`:`HTMLElement`
- `sup`:`HTMLElement`
- `table`:`HTMLTableElement`
- `tbody`:`HTMLTableSectionElement`
- `td`:`HTMLTableCellElement`
- `textarea`:`HTMLTextAreaElement`
- `tfoot`:`HTMLTableSectionElement`
- `th`:`HTMLTableSectionElement`
- `thead`:`HTMLTableSectionElement`
- `title`:`HTMLTitleElement`
- `tr`:`HTMLTableRowElement`
- <s>`tt`:`HTMLElement`</s>
- `u`:`HTMLElement`
- `ul`:`HTMLUListElement`
- `var`:`HTMLElement`

#### 取得属性
与属性相关的DOM方法有三个`getAttribute()`,`setAttribute()`,`removeAttribute()`.

`getAttribute()`方法接收一个字符串,表示要获取的属性的.属性名不区分大小写,如果给定的属性不存在,则`getAttribute()`返回`null`.`HTML`中的布尔属性如果其后没有值,则返回`""`.获取的属性不一定要求是HTML属性.
````HTML
<div id="myDiv" class="myClass" not_html_attribute="hello world" html_boolean_attribute></div>
````
````JS
let div = document.getElementById("myDiv");
console.log(div.getAttribute("cLAss"));                     // "myClass"
console.log(div.getAttribute("not_html_attribute"));        // "hello world"
console.log(div.getAttribute("html_boolean_attribute"));    // ""
console.log(div.getAttribute("not_exsit"));                 // null
````

***HTML5规范要求,自定义属性名应该前缀为`data-`以方便验证.***

元素的公认(非自定义)属性也会被添加到DOM对象的属性.

通过DOM对象访问的属性中,有两个属性与`getAttribute()`的返回值不一样:
- `style`属性:对于`getAttribute()`返回CSS字符串;对于DOM对象属性返回`CSSStyleDeclaration`对象.
- 事件处理程序(事件属性,这种属性的值是一段JS代码):对于`getAttribute()`返回字符串形式的源代码;对于DOM对象属性返回JS函数(未指定该属性则返回`null`).

因此,通常使用DOM对象属性而非`getAttribute()`(自定义属性除外).

#### 设置属性
`setAttribute()`用于给属性设置(或替换)属性值.该方法接收两个参数:要设置的属性名和属性的值.第一个参数传入的字符串会自动转换为小写形式.

直接给DOM对象属性赋值与`setAttribute()`是等价的:
````JS
let div = document.getElementById("myDiv");
div.setAttribute("Id", "someOtherId");  // 等价于div.id = "someOtherId";
div.setAttribute("cLass", "myClass");   // 等价于div.className = "myClass";
div.setAttribute("title", "aaa");       // 等价于div.title = "aaa";
````

但在DOM上添加自定义属性,不会自动让它变成元素的属性.

`removeAttribute()`用于从元素中删除属性:
````JS
div.removeAttribute("class");
````

#### attributes属性
`Element`类型是唯一使用`attributes`属性的DOM节点类型.`attributes`属性包含一个`NamedNodeMap`实例,是一个"实时"集合.元素的每个属性都表示为一个`Attr`节点,并保存在这个`NamedNodeMap`对象中.

`NamedNodeMap`对象包含下列方法:
- `getNamedItem(name)`:返回`nodeName`属性等于`name`的节点
- `removeNamedItem(name)`:删除`nodeName`属性等于`name`的节点
- `setNamedItem(name)`:向列表中添加`node`节点,以其`nodeName`为索引
- `item(pos)`:返回索引位置`pos`处的节点

`attributes`属性中的每个节点的`nodeName`是对应属性的名字,`nodeValue`是属性的值:
````JS
let id = element.attributes.getNamedItem("id").nodeValue;   // 获取属性id的属性值
````
也可以使用中括号访问来简写:
````JS
let id = element.attributes["id"].nodeValue;
element.attributes["id"].nodeValue = "someOtherId";
````

`removedNamedItem()`方法与元素上的`removeAttribute()`方法类似.

`setNamedItem()`接收一个[属性节点](#attr类型),然后给元素添加一个新属性:
````JS
element.attributes.setNamedItem(newAttr);   // newAttr是Attr类型的
````

`attributes`属性一般用于迭代元素上的所有属性,这可以用于将DOM结构序列化为XML或HTML字符串.迭代顺序取决于浏览器实现.

#### 创建元素
使用`document.createElement()`方法创建新元素并将其`ownerDocument`属性设置为`document`(即使它不存在于DOM树中).这个方法接收一个参数,即要创建元素的标签名.`HTML`中,标签名不区分大小写,`XML`(包括`XHTML`)中是区分大小写的.该方法返回对元素节点的引用:
````JS
let div = document.createElement("div");    // 此时`ownerDocument`已经是`document`
div.id = "myNewDiv";
div.className = "box";
document.body.appendChild(div);
````

#### 元素后代
`childNodes`属性包含元素所有的子节点:其他元素,文本节点,注释或处理指令.

对于:
````HTML
<ul id="myList">
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
</ul>
````
`<ul>`元素会包含7个子元素,其中3个是`<li>`元素,还有4个`Text`节点(表示`<li>`元素周围的空白符(换行符,制表符)).(不同浏览器可能会有所不同,例如:认为只包含3个子元素)

若为:
````HTML
<ul id="myList"><li>Item 1</li><li>Item 2</li><li>Item 3</li></ul>
````
此时`<ul>`元素会包含3个子元素.

对某个元素调用[定位元素](定位元素)中提及的方法,则只会在子节点中搜索:
````JS
let ul = document.getElementById("myList");
let items = ul.getElementsByTagName("li");
````

### Text类型
`Text`节点由`Text`类型表示,包含按字面解释的纯文本,也可能包含转义后的HTML字符,但不含HTML代码.`Text`类型的节点具有以下特征:
- `nodeType`为`3`(`Node.TEXT_NODE`)
- `nodeName`值为`#text`
- `nodeValue`值为节点中包含的文本
- `parentNode`值为`Element`对象
- 不支持子节点

`Text`节点中包含的文本可以通过`nodeValue`属性访问,也可以通过`data`属性访问,这两个属性包含相同的值.修改`nodeValue`或`data`的值,也会在另一个属性反映出来.文本节点暴露了以下操作文本的方法:
- `appendData(text)`:向节点末尾添加文本`text`
- `deleteData(offset, count)`:从位置`offset`开始删除`count`个字符
- `insertData(offset, text)`:在位置`offset`插入`text`.
- `replaceData(offset, count, text)`:用`text`替换从位置`offset`到`offset+count`的文本.
- `splitText(offset)`:在位置`offset`将当前文本节点拆分为两个文本节点
- `substringData(offset, count)`:提取从位置`offset`到`offset+count`的文本
- `length`:该属性获取文本节点中包含的字符数量.这个值等于`nodeValue.length`和`data.length`.

默认情况下,包含文本内容的每个元素最多只能有一个文本节点:
````HTML
<div></div> <!-- 没有内容,因此没有文本节点 -->
<div> </div>    <!-- 有空格,因此有一个文本节点 -->
<div>Hello World!</div> <!-- 有且仅有文本内容,因此有一个文本节点 -->
````

如果文本中有字符实体,则在JS字符串中会变成正常字符.如果JS字符串中有大小于号,则会自动转换为字符实体(应用HTML或XML编码):
````JS
div.firstChild.nodeValue = "Some <strong>other</strong> message";
// HTML中div元素内的文本为Some &lt;strong&gt;other&lt;/strong&gt; message
````

#### 创建文本节点
`document.createTextNode()`可以用来创建新文本节点(其`ownerDocument`属性会被设置为`document`),它接收一个参数,即要插入节点的文本,这些插入的文本也会应用HTML或XML编码.
````JS
let element = document.createElement("div");
element.className = "message";
let textNode = document.createTextNode("Hello world!");
element.appendChild(textNode);
document.body.appendChild(element);
````
两个相邻的文本节点不会导致文本之间出现空格.

#### 规范化文本节点
DOM文档中经常出现两个相邻的文本节点,因此,可以使用`Node`类型中的`normalize()`方法,将子节点中相邻的同胞文本节点合并为一个文本节点,这个文本节点的`nodeValue`就等于之前所有同胞节点`nodeValue`拼接在一起的字符串.
````JS
// element的子节点是两个文本节点"Hello "和"world!"
console.log(element.childNodes.length); // 2
element.normalize();
console.log(element.childNodes.length); // 1
console.log(element.firstChild.nodeValue);  // Hello world!
````

浏览器解析文档时,永远不会创建同胞文本节点.同胞文本节点只会出现在DOM脚本生成的文档树中.

#### 拆分文本节点
如上所说,存在`splitText()`方法可用于拆分`nodeValue`:
````JS
// element包含一个文本节点"Hello world!"
let newNode = element.firstChild.splitText(5);
console.log(element.firstChild.nodeValue);  // "Hello"
console.log(newNode.nodeValue);             // " world!"
console.log(element.childNodes.length);     // 2
````

拆分文本节点常用于从文本节点中提取数据的DOM解析技术.

### Comment类型
`DOM`中的注释通过`Comment`类型表示.`Comment`类型的节点具有以下特征:
- `nodeType`等于`8`(`Node.COMMENT_NODE`)
- `nodeName`值为`"#comment"`
- `nodeValue`值为注释的内容
- `parentNode`值为`Document`或`Element`对象
- 不支持子节点

`Comment`类型与`Text`类型继承同一个基类`CharacterData`,因此拥有除`splitText()`之外`Text`节点所有的字符串操作方法.其注释的实际内容(指的是不包含`<!-- -->`的文字部分)可以通过`nodeValue`或`data`属性获得.

例如:
````HTML
<div id="myDiv"><!-- A comment --></div>
````
此处的注释是`<div>`元素的子节点,因此可以用如下的代码访问:
````JS
let div = document.getElementById("myDiv");
let comment = div.firstChild;
console.log(comment.data);  // " A comment "
````

可以使用`document.createComment()`方法创建注释节点,参数为注释文本(不包括`<!-- -->`).

浏览器不承认`</html>`标签后的注释,因此这部分不会出现在DOM树上.

### CDATASection
`CDATASection`类型表示`XML`中特有的`CDATA`区块.`CDATASection`类型继承`Text`类型,因此拥有包括`splitText()`在内的所有字符串操作方法.`CDATASection`类型的节点具有以下特征:
- `nodeType`等于`4`(`Node.CDATA_SECTION_NODE`)
- `nodeName`值为`#cdata-section`
- `nodeValue`值为CDATA区块的内容
- `parentNode`值为`Document`或`Element`对象
- 不支持子节点

`CDATA`区块只在XML文档中有效.但对于代码:
````XHTML
<div id="myDiv"><![CDATA[This is some content.]]></div>
````
主流的浏览器都没有将其识别为`CDATASection`.

在真正的XML文档中,可以使用`document.createCDataSection()`并传入节点内容来创建CDATA区块.

### DocumentType类型
`DocumentType`类型的节点包含文档的类型(`doctype`)信息,具有以下特征:
- `nodeType`等于`10`(`Node.DOCUMENT_TYPE_NODE`)
- `nodeName`值为文档类型的名称
- `nodeValue`值为`null`
- `parentNode`值为`Document`对象
- 不支持子节点

`DocumentType`在`DOM Level1`中不支持动态创建.`DocumentType`对象保存在`document.doctype`属性中.  
`DocumentType`还有几个属性:
- `name`:文档类型的名称
- `entities`:文档类型描述的实体的`NamedNodeMap`
- `notations`:文档类型描述的表示法的`NamedNodeMap`

对于`HTML`和`XHTML`,`entities`和`notations`列表为空.

对于`name`(文档类型名称),是`<!DOCTYPE`后面的那个字符串:
````HTML
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN"
  "http://www.w3.org/TR/html4/strict.dtd">
````
````JS
console.log(document.doctype.name); // html
````

### DocumentFragment类型
在所有节点类型中,`DocuemntFragment`类型是唯一一个在标记中没有对应表示的类型.`DOM`将文档片段定义为"轻量级"文档,能够包含和操作节点,却没有完整文档那样的额外的消耗.  
`DocumentFragment`节点具有以下特征:
- `nodeType`等于`11`(`Node.DOCUMENT_FRAGMENT_NODE`)
- `nodeName`值为`"#document-fragment"`
- `nodeValue`值为`null`
- `parentNode`值为`null`
- 子节点可以是`Element`,`ProcessingInstruction`,`Comment`,`Text`,`CDATASection`或`EntityReference`.

不能直接把文档片段添加到文档.相反,文档片段的作用是充当其他要被添加到文档的节点的仓库.

可以使用`document.createDocumentFargment()`方法创建文档片段.

文档片段从`Node`类型继承了所有文档类型具备的可以执行DOM操作的方法.

使用例:要将`<ul>`和许多`<li>`元素添加到文档中,为了避免多次渲染,将`<ul>`和`<li>`在文档片段中创建,并将其移到文档中.


### Attr类型
元素数据(属性)在DOM中通过`Attr`类型表示.`Attr`类型的构造函数和原型在所有浏览器中都可以访问.技术上讲,属性是存在于元素`attributes`属性中的节点(而非DOM文档树中).`Attr`节点具有以下特征:
- `nodeType`等于`2`(`Node.ATTRIBUTE_NODE`)
- `nodeName`值为属性名
- `nodeValue`值为属性值
- `parentNode`值为`null`
- 在HTML中不支持子节点
- 在XML中子节点可以是`Text`或`EntityReference`.

属性节点尽管是节点,却不认为是DOM文档树的一部分.`Attr`节点很少直接被引用,而是通常使用`getAttribute()`,`removeAttribute()`和`setAttribute()`方法操作属性.

`Attr`对象上还有几个属性:
- `name`:属性名(同`nodeName`)
- `value`:属性值(同`nodeValue`)
- `specified`:布尔值,表示属性使用的是默认值还是被指定的值.

可以使用`document.createAttribute()`方法创建新的`Attr`节点,参数为属性名:
````JS
let attr = document.createAttribute("align");
attr.value = "left";
element.setAttributeNode(attr);
````

元素的`setAttributeNode()`方法传入一个`Attr`节点,以赋值一个属性.元素的`getAttributeNode()`方法返回属性对应的`Attr`节点.

*注:推荐使用`getAttribute()`,`removeAttribute()`和`setAttribute()`方法操作属性,而不是直接操作属性节点,因为将属性作为节点来访问多数情况下并无必要.*

## DOM编程
### 动态脚本
动态脚本就是在页面初始加载时不存在,之后又通过DOM包含的脚本.与对应的HTML元素一样,有两种方式通过`<script>`动态为网页添加脚本:引入外部文件和直接插入源代码.

**动态加载外部文件:**

例如要添加这样的节点:
````HTML
<script src="foo.js"></script>
````
可以这样写:
````JS
function loadScript(url) {
    let script = document.createElement("script");
    script.src = url;
    document.body.appendChild(script);
}
loadScript("foo.js");
````

如何确定动态脚本加载完*见下文*.

**直接插入源代码:**

例如要添加这样的节点:
````HTML
<script>
    function sayHi() {
        console.log("hi");
    }
</script>
````
可以这样写:
````JS
let script = document.createElement("script");
script.appendChild(document.createTextNode("function sayHi() { console.log('hi'); }"));
document.body.appendChild(script);
````

*注:为了兼容IE和Safari 3之前的版本,上述代码需要做修改.*

以这种方法加载的代码会在全局作用域中执行,并在加入DOM树后立即生效.基本上,这就相当于在全局作用域中把源代码传给`eval()`方法.

注意,通过`innerHTML`属性创建的`<script>`元素永远不会执行.浏览器会创建该元素,但是会打上永不执行的标签.

`innerHTML`属性:对于元素节点,拥有`innerHTML`属性,对其赋值可以将其子节点变成一个文本节点,且其内容为所赋值:
````JS
let div = document.getElementById("myDiv");
div.innerHTML = "abc"
````
则:
````HTML
<div id="myDiv">abc</div>
````

### 动态样式
`CSS`样式在`HTML`页面中可以通过两个元素加载.`<link>`元素用于包含CSS外部文件,而`<style>`元素用于添加嵌入样式.动态样式在页面初始加载时并不存在,而是在之后才添加到页面中的.

**`<link>`加载CSS外部文件:**

若想要添加以下元素:
````HTML
<link rel="stylesheet" type="text/css" href="styles.css">
````
则:
````JS
function loadStyles(url) {
    let link = document.createElement("link");
    link.rel = "stylesheet";
    link.type = "text/css";
    link.href = url;
    let head = document.getElementsByTagName("head")[0];
    head.appendChild(link);
}
loadStyles("styles.css");
````

通过外部文件加载样式是一个异步过程.因此,样式的加载和正执行的JS代码并没有先后顺序.

**使用`<style>`元素包含嵌入的CSS规则**

若想要添加以下元素:
````JS
<style type="text/css">
body {
    background-color: red;
}
</style>
````
则:
````JS
let style = document.createElement("style");
style.type = "text/css";
style.appendChild(document.createTextNode("body { background-color: red; }"));
let head = document.getElementsByTagName("head")[0];
head.appendChild(style);
````

*注:为了兼容IE,上述代码需要做修改.*

### 操作表格
使用DOM来创建`<table>`元素时,通常要涉及大量标签.  
例如对于:
````HTML
<table border="1" width="100%">
    <tbody>
        <tr>
            <td>Cell 1,1</td>
            <td>Cell 2,1</td>
        </tr>
        <tr>
            <td>Cell 1,2</td>
            <td>Cell 2,2</td>
        </tr>
    </tbody>
</table>
````
使用以下代码重建这个表格:
````JS
// 创建表格
let table = document.createElement("table");
table.border = 1;
table.width = "100%";

// 创建表体
let tbody = document.createElement("tbody");
table.appendChild(tbody);

// 创建第一行
let row1 = document.createElement("tr");
tbody.appendChild(row1);
let cell1_1 = document.createElement("td");
cell1_1.appendChild(document.createTextNode("Cell 1,1"));
row1.appendChild(cell1_1);
let cell2_1 = document.createElement("td");
cell2_1.appendChild(document.createTextNode("Cell 2,1"));
row1.appendChild(cell2_1);

// 创建第二行
let row2 = document.createElement("tr");
tbody.appendChild(row2);
let cell1_2 = document.createElement("td");
cell1_2.appendChild(document.createTextNode("Cell 1,2"));
row2.appendChild(cell1_2);
let cell2_2 = document.createElement("td");
cell2_2.appendChild(document.createTextNode("Cell 2,2"));
row2.appendChild(cell2_2);

// 把表格添加到文档主体
document.body.appendChild(table);
````

为了方便创建表格,`HTML DOM`给`<table>`,`<tbody>`和`<tr>`元素添加了一些属性和方法.

`<table>`元素添加了以下属性和方法:
- `caption`:指向`<caption>`元素的指针(如果存在)
- `tBody`:包含`<tbody>`元素的`HTMLCollection`
- `tFoot`:指向`<tfoot>`元素(如果存在)
- `tHead`:指向`<thead>`元素(如果存在)
- `rows`:包含表示所有行的`HTMLCollection`
- `createTHead()`:创建`<thead>`元素,放到表格中,返回引用
- `createTFoot()`:创建`<tfoot>`元素,放到表格中,返回引用
- `createCaption()`:创建`<caption>`元素,放到表格中,返回引用
- `deleteTHead()`:删除`<thead>`元素
- `deleteTFoot()`:删除`<tfoot>`元素
- `deleteCaption()`:删除`<caption>`元素
- `deleteRow(pos)`:删除给定位置的行
- `insertRow(pos)`:在行集合中给定位置插入一行

`<tbody>`元素添加了以下属性和方法:
- `rows`:包含`<tbody>`元素中所有行的`HTMLCollection`
- `deleteRow(pos)`:删除给定位置的行
- `insertRow(pos)`:在行集合中给定位置插入一行,返回该行的引用.

`<tr>`元素添加了以下属性和方法:
- `cells`:包含`<tr>`元素所有表元的`HTMLCollection`
- `deleteCell(pos)`:删除给定位置的表元
- `insertCell(pos)`:在表元集合给定位置插入一个表元,返回该表元的引用

利用上面的方法,简化后的代码为:
````JS
// 创建表格
let table = document.createElement("table");
table.border = 1;
table.width = "100%";

// 创建表体
let tbody = document.createElement("tbody");
table.appendChild(tbody);

// 创建第一行
tbody.insertRow(0);
tbody.rows[0].insertCell(0);
tbody.rows[0].cells[0].appendChild(document.createTextNode("Cell 1,1"));
tbody.rows[0].insertCell(1);
tbody.rows[0].cells[1].appendChild(document.createTextNode("Cell 2,1"));

// 创建第二行
tbody.insertRow(1);
tbody.rows[1].insertCell(0);
tbody.rows[1].cells[0].appendChild(document.createTextNode("Cell 1,2"));
tbody.rows[1].insertCell(1);
tbody.rows[1].cells[1].appendChild(document.createTextNode("Cell 2,2"));

// 把表格添加到文档主体
document.body.appendChild(table);
````

### 使用NodeList
`NodeList`对象和相关的`NamedNodeMap`,`HTMLCollection`这3个集合类型都是"实时的".任何文档结构的变化都会实时地在它们身上反映出来.

`NodeList`就是基于DOM文档的实时查询.例如,下面的代码会导致无限循环:
````JS
let divs = document.getElementsByTagName("div");
for (let i = 0; i < divs.length; ++i) {
    let div = document.createElement("div");
    document.body.appendChild(div);
}
````

使用迭代器(`for-of`包括在内)也不会解决这个问题.

为了避免这种问题发生,可以创建一个临时变量来记录遍历前的长度:
````JS
let divs = document.getElementsByTagName("div");
for (let i = 0, len = divs.length; i < len; ++i) {
    let div = document.createElement("div");
    document.body.appendChild(div);
}
````
或者反向迭代集合:
````JS
let divs = document.getElementsByTagName("div");
for (let i = divs.length - 1; i >= 0; --i) {
    let div = document.createElement("div");
    document.body.appendChild(div);
}
````
最好可以限制操作`NodeList`的次数,或者将查询到的`NodeList`缓存起来.

## MutationObserver接口
`MutationObserver`接口可以在DOM修改时异步执行回调.使用`MutationObserver`可以观察整个文档,DOM树的一部分,或某个元素.此外还可以观察元素属性,子节点,文本,或者前三者任意组合的变化.

*注:`MutationObserver`接口是为了取代废弃的`MutationEvent`.*

### 基本用法
`MutationObserver`的实例要通过调用`MutationObserver`构造函数并传入一个回调函数来创建:
````JS
let observer = new MutationObserver(() => console.log('DOM was mutated.'));
````

#### observe()方法
新创建的`MutationObserver`实例不会关联DOM的任何部分.使用`observe()`方法将实例与DOM关联.这个方法接收两个必需的参数:要观察其变化的DOM节点,以及一个`MutationObserverInit`对象.

`MutationObserverInit`对象用于控制观察哪些方面的变化,是一个键值对形式配置选项的字典.  
例如,下面的代码会创建一个`observer`并配置它观察`<body>`元素上的属性变化:
````JS
let observer = new MutationObserver(() => console.log('<body> attributes changed'));
observer.observe(document.body, { attributes: true });
// 此后,<body>元素(不包括其子元素)上任何属性发生变化都会被observer发现,然后就会异步执行注册的回调函数.
document.body.className = 'foo';
console.log('Changed body class');
// Changed body class
// <body> attributes changed
````
由于是异步执行的,所以`<body> attributes changed`最后才打印.

#### 回调与MutationRecord
每个回调都会收到一个`MutationRecord`实例数组.`MutationRecord`实例包含的信息包括发生了什么变化,以及DOM的哪一部分受到了影响.因为回调函数执行之前可能同时发生多个满足观察条件的事件,所以每次执行回调都会传入一个包含按顺序入队的`MutationRecord`实例的数组.

````JS
let observer = new MutationObserver(
    (mutationRecords) => console.log(mutationRecords));
observer.observe(document.body, { attributes: true });
document.body.setAttribute('foo', 'bar');
// [
//     MutationRecord {
//         addedNodes: NodeList [],
//         attributeName: "foo",
//         attributeNamespace: null,
//         nextSibling: null,
//         oldValue: null,
//         previousSibling: null,
//         removeNodes: NodeList [],
//         target: body,
//         type: "attributes",
//         [[Prototype]]: MutationRecord
//     }
// ]
````
连续修改会生成多个`MutationRecord`实例,下次回调执行时就会收到包含所有这些实例的数组,顺序为变化事件发生的顺序:
````JS
let observer = new MutationObserver(
    (mutationRecords) => console.log(mutationRecords));
observer.observe(document.body, { attribute: true });
document.body.className = 'foo';
document.body.className = 'bar';
document.body.className = 'baz';
// [MutationRecord, MutationRecord, MutationRecord]
````

下面列出了`MutationRecord`实例的属性:
- `属性`:`说明`
- `target`:被修改的目标结点
- `type`:字符串,表示变化的类型:`"attributes"`,`"characterData"`,`"childList"`
- `oldValue`:如果在`MutationObserverInit`对象中启用(`attributeOldValue`或`characterData OldValue`为`true`),`"attributes"`或`characterData`的变化事件会设置这个属性为被替代的值,`"childList"`类型的变化始终将这个属性设置为`null`.
- `attributeName`:对于`"attributes"`类型的变化,这里保存被修改属性的名称(即使原来不存在),其他变化事件会将这个属性设置为`null`.
- `attributeNamespace`:对于使用了命名空间的`"attributes"`类型的变化,这里保存被修改属性的命名空间的名字(即使原来不存在),其他变化事件会将这个属性设置为`null`.
- `addedNodes`:对于`"childList"`类型的变化,返回包含变化中添加节点的`NodeList`.默认为空`NodeList`.
- `removedNodes`:对于`"childList"`类型的变化,返回包含变化中删除节点的`NodeList`.默认为空`NodeList`.
- `previousSibling`:对于`"childList"`类型的变化,返回变化节点的前一个同胞`Node`,默认为`null`.
- `nextSibling`:对于`"childList"`类型的变化,返回变化节点的后一个同胞`Node`,默认为`null`.

传给回调函数的第二个参数时观察变化的`MutationObserver`的实例:
````JS
let observer = new MutationObserver(
    (mutationRecords, mutationObserver) => console.log(mutationObserver === observer));
observer.observe(document.body, { attributes: true });
document.body.setAttribute('foo', 'bar');
setTimeout(() => { document.body.setAttribute('baz', 'qux') }, 1000);
// true
// (1秒后)true
````

回调函数允许被调用多次.

#### disconnect()
默认情况下,只要被观察的元素不被垃圾回收,`MutationObserver`的回调就会相应DOM变化事件.要提前终止执行回调,可以调用`disconnect()`方法.该方法也会抛弃已经加入任务队列要异步执行的回调(对于正在执行或已经执行的无效).

使用:`observer.disconnect();`

#### 复用MutationObserver
多次调用`observer()`方法,可以复用一个`MutationObserver`对象观察多个不同的目标节点.此时,`MutationRecord`的`target`属性可以标识发生变化事件的目标节点:
````JS
let observer = new MutationObserver(
    (mutationRecords) => console.log(mutationRecords.map((x) => x.target)));
let childA = document.createElement('div');
let childB = document.createElement('span');
observer.observe(childA, { attributes: true });
observer.observe(childB, { attributes: true });
childA.setAttribute('foo', 'bar');
childB.setAttribute('foo', 'bar');
// [div, span]
````

`disconnect()`方法会停止观察所有目标.

#### 重用MutationObserver
调用`disconnect()`并不会结束`MutationObserver`的生命,还可以继续调用`observe()`等方法将他关联到新的目标节点.

### MutationObserverInit与观察返回
`MutationObserverInit`对象用于控制对目标节点的观察范围.粗略地讲,观察者可以观察的事件包括属性变化,文本变化和子节点变化.

以下为`MutationObserverInit`对象的属性:
- `属性`:`说明`
- `subtree`:布尔值,表示除了目标节点,是否观察目标节点的子树(后代).如果是`false`,则只观察目标节点的变化;如果是`true`,则观察目标节点及其整个子树.默认为`false`.
- `attributes`:布尔值,表示是否观察目标节点的属性变化.默认值为`false`.
- `attributeFilter`:字符串数组,表示要观察哪些属性的变化.把这个值设置为`true`也会将`attributes`的值转换为`true`,默认为观察所有属性.
- `attributeOldValue`:布尔值,表示`MutationRecord`是否记录变化之前的属性值.把这个值设置为`true`也会将`attributes`的值转换为`true`.默认为`false`.
- `characterData`:布尔值,表示修改字符数据是否触发变化事件.默认为`false`.
- `characterDataOldValue`:布尔值,表示`MutationRecord`是否记录变化之前的字符数据.把这个值设置为`true`也会将`characterData`的值转换为`true`.默认为`false`.
- `childList`:布尔值,表示修改目标节点的子节点是否触发变化事件.默认为`false`.

*注:在调用`observe()`时,`MutationObserverInit`对象中的`attributes`,`characterData`,`childList`属性必须至少有一项为`true`.否则会抛出错误,因为没有任何变化事件可能触发回调.*

#### 观察属性
`attributes`设置为`true`时,默认观察所有属性:
````JS
document.observe(document.body, { attributes: true });
````

使用`attributeFilter`属性来设置白名单:
````JS
let observer = new MutationObserver(
    (mutationRecords) => console.log(mutationRecords));
observer.observe(document.body, { attributeFilter: ['foo'] });
document.body.setAttribute('foo', 'bar');
document.body.setAttribute('baz', 'qux');
// [MutationRecords]
// ↑只有foo属性的变化被记录了
````

如果想在变化记录中保存原来的值,可以将`attributeOldValue`属性设置为`true`:
````JS
let observer = new MutationObserver(
    (mutationRecords) => console.log(mutationRecords.map((x) => x.oldValue)));
observer.observe(document.body, { attributeOldValue: true });
document.body.setAttribute('foo', 'bar');
document.body.setAttribute('foo', 'baz');
document.body.setAttribute('foo', 'qux');
// [null, 'bar', 'baz']
````

#### 观察字符数据
`MutationObserver`可以观察文本节点(如`Text`,`Comment`,`ProcessingInstruction`节点)中字符的添加,删除,修改.这需要将`characterData`属性设置为`true`:
````JS
let observer = new MutationObserver(
    (mutationRecords) => console.log(mutationRecords));
document.body.appendChild(document.createTextNode("foo"));
observer.observe(document.body.lastChild, { characterData: true });
document.body.lastChild.textContent = 'foo';    // 赋值为相同字符串
document.body.lastChild.textContent = 'bar';    // 赋值为新字符串
document.body.lastChild.textContent = 'baz';
// [MutationRecord, MutationRecord, MutationRecord]
// ↑以上变化都被记录下来了
// [MutationRecord, MutationRecord]
// ↑这些可能是浏览器格式化HTML导致的
````

将`characterDataOldValue`属性设置为`true`以记录原来的字符数据:
````JS
let observer = new MutationObserver(
    (mutationRecords) => console.log(mutationRecords.map((x) => x.oldValue)));
document.body.appendChild(document.createTextNode("foo"));
observer.observe(document.body.lastChild, { characterDataOldValue: true });
document.body.lastChild.textContent = 'foo';
document.body.lastChild.textContent = 'bar';
document.body.lastChild.textContent = 'baz';
// ['foo', 'foo', 'bar']
// ['baz', 'baz\n'] ←这些可能是浏览器格式化HTML导致的
````

#### 观察子节点
`MutationObserver`可以观察目标节点子节点的添加和移除.要观察子节点,需要在`MutationObserverInit`对象中将`ChildList`属性设置为`true`:
````JS
let observer = new MutationObserver(
    (mutationRecords) => console.log(mutationRecords));
observer.observe(document.body, { childList: true });
document.body.appendChild(document.createElement('div'));
// [
//     MutationRecord {
//         addedNodes: NodeList [div],
//         attributeName: null,
//         attributeNamespace: null,
//         nextSibling: null,
//         oldValue: null,
//         previousSibling: script,
//         removeNodes: NodeList [],
//         target: body,
//         type: "childList",
//         [[Prototype]]: MutationRecord
//     }
// ]

// 可能还会有一个addedNodes: NodeList [text]的记录,是浏览器格式化HTML产生的.
````
对子节点的重新排序会报告两次变化事件,因为这涉及先移除再添加:
````JS
document.body.appendChild(document.createElement('div'));
document.body.appendChild(document.createElement('span'));
let observer = new MutationObserver(
    (mutationRecords) => console.log(mutationRecords));
observer.observe(document.body, { childList: true });
document.body.insertBefore(document.body.lastChild, document.body.firstChild);
// [
//     MutationRecord {
//         addedNodes: NodeList [],
//         attributeName: null,
//         attributeNamespace: null,
//         nextSibling: null,
//         oldValue: null,
//         previousSibling: div,
//         removeNodes: NodeList [span],
//         target: body,
//         type: "childList",
//         [[Prototype]]: MutationRecord
//     },
//     MutationRecord {
//         addedNodes: NodeList [span],
//         attributeName: null,
//         attributeNamespace: null,
//         nextSibling: text,
//         oldValue: null,
//         previousSibling: null,
//         removeNodes: NodeList [],
//         target: body,
//         type: "childList",
//         [[Prototype]]: MutationRecord
//     }
// ]

// 可能还会有一个addedNodes: NodeList [text]的记录,是浏览器格式化HTML产生的.
````

#### 观察子树
可以把观察的范围扩展到这个元素的子树(所有后代节点),这需要在`MutationObserverInit`对象中将`subtree`属性设置为`true`:
````JS
document.body.appendChild(document.createElement('div'));
let observer = new MutationObserver(
    (mutationRecords) => console.log(mutationRecords));
observer.observe(document.body, { attributes: true, subtree: true });
document.body.lastChild.setAttribute('foo', 'bar');
// [
//     MutationRecord {
//         addedNodes: NodeList [],
//         attributeName: "foo",
//         attributeNamespace: null,
//         nextSibling: null,
//         oldValue: null,
//         previousSibling: null,
//         removeNodes: NodeList [],
//         target: div,
//         type: "attributes",
//         [[Prototype]]: MutationRecord
//     }
// ]
````
被观察子树中的节点被移出子树之后仍然能够触发变化事件.这意味着在子树中的节点离开该子树后,即使严格来讲该节点已经脱离了原来的子树,但它仍然会触发变化事件:
````JS
document.body.appendChild(document.createElement('div'));
let observer = new MutationObserver(
    (mutationRecords) => console.log(mutationRecords));
observer.observe(document.body, { attributes: true, subtree: true });
let removedNode = document.body.removeChild(document.body.lastChild);
removedNode.setAttribute('foo', 'bar');
// 移出的节点仍然触发变化事件
// [MutationRecord]
````

### 异步回调与记录队列
`MutationObserver`接口出于性能考虑,每次变化的信息会保存在`MutationRecord`中,然后添加到记录队列.这个队列对每个`MutationObserver`实例都是唯一的,是所有`DOM`变化事件的有序列表.

#### 记录队列
每次`MutationRecord`被添加到`MutationObserver`的记录队列时,仅当之前没有已排期的微任务回调时(队列中微任务的长度为`0`),才会将观察者注册的回调作为微任务调度到任务队列中.*(即每个`MutationObserver`的回调函数调用只会在异步任务队列中最多同时出现一次)*

在回调函数未被执行前,如果有更多变化的事件,则会放入存储`MutationRecord`实例的数组,顺序为它们进入记录队列的顺序.回调函数所接收的,就是这个数组.回调执行后,`MutationRecord`的数组会被清空,等待下一次被调度到任务队列.

#### takeRecords()方法
`MutationObserver`的`takeRecords()`方法可以清空队列记录,取出并返回其中的所有`MutationRecord`实例:
````JS
let observer = new MutationObserver(
    (mutationRecords) => console.log(mutationRecords.map((x) => x.oldValue)));
document.body.appendChild(document.createTextNode("foo"));
observer.observe(document.body.lastChild, { characterDataOldValue: true });
document.body.lastChild.textContent = 'foo';
document.body.lastChild.textContent = 'bar';
document.body.lastChild.textContent = 'baz';
console.log(observer.takeRecords());
console.log(observer.takeRecords());
// [MutationRecord, MutationRecord, MutationRecord]
// []
````

### 性能,内存与垃圾回收
`MutationObserver`让变化事件即使被爆发式地触发,也不会显著地拖慢浏览器.但这是*有代价的*.

#### MutationObserver的引用
`MutationObserver`实例对目标节点的引用关系是弱引用,即不会妨碍垃圾回收程序回收目标节点.但目标节点却拥有对`MutationObserver`的强引用,如果目标节点从DOM中被移除,随后被垃圾回收,则关联的`MutationObserver`才会被垃圾回收.

#### MutationRecord的引用
记录队列中的每个`MutationRecord`实例至少包含对已有DOM节点的一个引用.如果是变化是`childList`类型,则会包含多个节点的引用.记录队列和回调处理的默认行为是耗尽这个队列,处理每个`MutationRecord`,然后让它们超出作用域并被垃圾回收.
这些`MutationRecord`实例会妨碍节点的回收.如果需要尽快地释放内存,并且要保存`MutationRecord`实例,建议从中取出最有用的信息,然后保存到一个新对象中,最后抛弃`MutationRecord`.

# DOM扩展
由于不断出现的专有扩展的出现,W3C将已成为事实标准的专有扩展编制成正式规范.DOM扩展包括:`Selectors API`,`HTML5`以及`Element Traversal`规范.这些扩展已经得到了所有主流浏览器的支持.

## Selectors API
`Selectors API`是W3C推荐标准,规定了浏览器原生支持的CSS查询API(也就是使用CSS的选择器的方式来筛选元素).

`Selectors API Level 1`的核心是两个方法:`querySelector()`和`querySelectorAll()`.在兼容浏览器中,`Document`类型和`Element`类型的实例上都会暴露这两个方法.

`Selectors API Level 2`规范在`Element`类型上新增了更多方法,比如`matches()`,`find()`和`findAll()`.不过,目前还没有浏览器实现或宣称实现`find()`和`findAll()`.

### querySelector()
`querySelector()`方法接收CSS选择符参数,返回匹配该模式的第一个后代元素,如果没有匹配项则返回`null`:
````JS
// 取得<body>元素
let body = document.querySelector('body');
// 取得ID为"myDiv"的元素
let myDiv = document.querySelector('#myDiv');
// 取得类名为"selected"的第一个元素
let selected = document.querySelector(".selected");
// 取得类名为"button"的<img>,且为<body>的后代(可以非直接)
let img = document.body.querySelector("img.button");
````

在`Document`上使用`querySelector()`方法时,会从文档元素开始搜索(即搜索所有节点);在`Element`上使用`querySelector()`方法时,则只会从当前元素的后代(可以非直接)中查询.也可以在`DocumentFragment`上使用.

如果选择符有语法错误或碰到不支持的选择符,则`querySelector()`方法会抛出错误.

### querySelectorAll()
`querySelectorAll()`方法跟`querySelector()`方法一样,但它会返回所有匹配的节点,这些节点放置在一个`NodeList`的*静态*(不是动态,为了防止性能问题)实例中.如果没有匹配项,则返回空的`NodeList`实例.

返回的`NodeList`对象的详细操作见[节点关系](#节点关系)和[使用NodeList](#使用nodelist).

其余性质与`querySelector()`方法相同.

### matches()
`matches()`方法(在规范草案中称为`matchesSelector()`)接收一个CSS选择符参数,如果存在匹配的元素,则返回`true`,否则返回`false`:
````JS
if (document.body.matches("body.page1")) { /*...*/ }
````

## 元素遍历
IE9之前的版本会把元素间的空白符忽略,而其他浏览器会将其当作空白节点.这就导致了`childNodes`等属性上的差异.为了弥补这个差异,同时不影响DOM规范,W3C通过新的`Element Traversal`规范定义了一组新属性.

`Element Traversal API`为DOM元素添加了5个属性:
- `childElementCount`:返回子元素的数量(不包含文本节点和注释)
- `firstElementChild`:指向第一个`Element`类型的子元素
- `lastElementChild`:指向最后一个`Element`类型的子元素
- `previousElementSibling`:指向前一个`Element`类型的同胞元素
- `nextElementSibling`:指向后一个`Element`类型的同胞元素

在支持的浏览器中,所有DOM元素都会有这些属性,为遍历DOM元素提供便利:
````JS
let parentElement = document.getElementById('parent');
let currentChildElement = parentElement.firstElementChild;
// 遍历所有子元素
while (currentChildElement) {
    processChild(currentChildElement);
    if (currentChildElement === parentElement.lastElementChild) {
        break;
    }
    currentChildElement = currentChildElement.nextElementSibling;
}
````

在IE9及以上版本,以及所有现代浏览器都支持`Element Traversal`属性.

## HTML5
`HTML5`规范包含了与标记相关的大量`JavaScript API`定义.其中有的API与DOM重合,定义了浏览器应该提供的DOM扩展.

### CSS类扩展
#### getElementsByClassName()
`getElementsByClassName()`暴露在`document`对象和所有HTML元素上.该方法接收一个参数,即包含一个或多个类名的字符串,返回类名中包含相应类的元素的`NodeList`.如果提供了多个类名,则顺序无关紧要,但类名需要全部满足:
````JS
// 取得所有元素中既包含类名"username"的,也包含类名"current"的元素
// 这两个类名的顺序无关紧要
let allCurrentUsernames = document.getElementsByClassName("username current");
// 取得ID为"myDiv"的元素子树中所有包含"selected"类的元素
let selected = document.getElementById("myDiv").getElementsByClassName("selected");
````

这个方法只会返回以调用它的对象为根元素的子树中所有匹配的元素.在`document`上调用`getElementsByClassName()`返回文档中所有匹配的元素,而在特定元素上调用`getElementsByClassName()`则返回该元素后代中匹配的元素.

该方法返回的`NodeList`是动态的.

IE9及以上版本,以及所有现代浏览器都支持`getElementsByClassName()`方法.

#### classList属性
要操作类名,可以通过`className`实现,但`className`是一个字符串.

HTML5通过给所有元素增加`classList`属性为操作类名提供了更简单也更安全的实现方式.`classList`是一个新的集合类型`DOMTokenList`的实例.`DOMTokenList`有`length`属性表示包含的项,可以通过`item()`或中括号取得个别的元素,可以迭代.此外,该类型还有以下方法:
- `add(value)`:向类名列表中添加指定的字符串值`value`.如果这个值已经存在,则什么也不做.
- `contains(value)`:返回布尔值,表示给定的`value`是否存在.
- `remove(value)`:从类名列表中删除指定的的字符串值`value`.
- `toggle(value)`:如果类名列表中已经存在指定的`value`,则删除;如果不存在,则添加.

使用例:
````JS
// 删除"disabled"类
div.classList.remove("disabled");
// 添加"current"类
div.classList.add("current");
````

有了`classList`属性之后,除非是完全删除或完全重写元素的`class`属性,否则`className`属性就用不到了.IE10及以上版本(部分)和其他主流浏览器(完全)实现了`classList`属性.

### 焦点管理
`document.activeElement`始终包含当前拥有焦点的DOM元素.页面加载时,可以通过用户输入(按下Tab键或代码中使用`focus()`方法)让某个元素自动获得焦点.例如:
````JS
let button = document.getElementById("myButton");
button.focus();
console.log(document.activeElement === button); // true
````
默认情况下,`document.activeElement`在页面刚加载完之后会设置为`document.body`.而在页面完全加载之前,`document.activeElement`的值为`null`.

`document.hasFocus()`方法,该方法返回布尔值,表示文档是否拥有焦点:
````JS
let button = document.getElementById("myButton");
button.focus();
console.log(document.hasFocus());   // true
````

确定文档是否获得了焦点,就可以帮助确定用户是否在操作页面.

焦点管理对于保证Web应用程序的无障碍使用是非常重要的.

### HTMLDocument扩展
#### readyState属性
`readyState`属性位于`document`上,该属性有两个可能的值:
- `"loading"`:表示文档正在加载
- `"complete"`:表示文档加载完成

例如:
````JS
if (document.readyState == "complete") { /*...*/ }
````

#### compatMode属性
`document`上的`compatMode`属性指示浏览器当前处于什么渲染模式,其可能值为:
- `"CSS1Compat"`:文档处于标准模式或接近标准模式
- `"BackCompat"`:文档处于混杂模式

*由于所有模式现在都已经标准化了,因此这些名称都不再在标准中使用了.*

#### head属性
作为对`document.body`的补充,HTML5添加了`document.head`属性,指向文档的`<head>`元素.

### 字符集属性
HTML5增加了几个与文档字符集有关的新属性.

`characterSet`属性表示文档实际使用的字符集,也可以用来指定新字符集.这个属性的默认值是`"UTF-16"`,但可以通过`<meta>`元素或响应头,或者直接修改自身来修改:
````JS
console.log(document.characterSet); // "UTF-16"
document.characterSet = "UTF-8";
````

### 自定义数据属性
`HTML5`允许给元素指定非标准的属性,但要使用前缀`data-`以告诉浏览器,这些属性既不包含与渲染有关的信息,也不包含元素的语义信息.除了前缀,自定义属性对命名是没有限制的:
````HTML
<div id="myDiv" data-appId="12345" data-myname="aaa"></div>
````

元素的`dataset`属性可以用来访问这些以`data-`开头的自定义属性.`dataset`属性是一个`DOMStringMap`的实例,包含一组键值对映射.元素可以通过`data-`后面的字符串作为键访问.  
例如针对上面的HTML:
````JS
let div = document.getElementById("myDiv");
// 读取自定义数据属性的值
let appId = div.dataset.appId;  // 虽然浏览器可能会把appId标准化为app-id,但这仍然可行
let myName = div.dataset.myname;
// 设置自定义数据属性的值
div.dataset.appId = 23456;  // 会被类型转换为"23456"
div.dataset.myname = "bbb";
// 存在"myname"吗?
if (div.dataset.myname !== undefined) {
    console.log(`Hello, ${div.dataset.myname}`);
}
````

注意:如果HTML属性为`data-my-name`,则JS中键名为`myName`,因为`-`不是一个合法的命名变量的字符.如果书写HTML是使用`data-myName`,则浏览器会自动将其转换为`data-my-name`,使用键名`myName`访问仍然有效.

自定义数据类型非常适合需要给元素附加某些数据的场景,比如链接追踪和在聚合应用程序中识别页面的不同部分.另外,单页应用程序框架也非常多地使用了自定义数据属性.

### 插入标记
#### innerHTML属性
在读取元素的`innerHTML`属性时,会返回该元素所有后代的HTML字符串,包括元素,注释,文本节点.而在写入`innerHTML`时,则会根据提供的字符串以新的DOM子树代替元素中原来包含的所有结点.

例如:
````HTML
<div id="content">
    <p>This is a <strong>paragraph</strong> with a list following it.</p>
    <ul>
        <li>Item 1</li>
        <li>Item 2</li>
        <li>Item 3</li>
    </ul>
</div>
````
对于`<div>`元素,其`innerHTML`属性将有以下字符串:
````JS
`<p>This is a <strong>paragraph</strong> with a list following it.</p>
<ul>
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
</ul>`
````
实际返回的文本内容可能会因浏览器而不同.

在写入时,赋给`innerHTML`属性的值会被解析为DOM子树,并替换该元素之前的所有子节点.所附的值默认以HTML的形式解析,所以其中的所有标签都会以浏览器处理HTML的方式转换为元素.如果赋值中不包含任何HTML标签,则直接生成一个文本节点.
````JS
div.innerHTML = "Hello & welcome, <b>\"reader\"!</b>";
````
则HTML会转换为:
````HTML
<div id="content">Hello &amp; welcome, <b>&quot;reader&quot;!</b></div>
````

在将HTML字符串解析为DOM树时,浏览器会自动序列化,所以设置`innerHTML`属性后马上再读出来会得到不同的字符串(不是指字符实体).

在现代浏览器中,通过`innerHTML`插入的`<script>`标签是不会执行的.而`<style>`元素可以正常加载.

在IE8及之前的版本中,`<script>`和`<style>`被认为是"非受控元素"(其他的则是"受控元素"),如果给`<script>`指定了`defer`属性,且在该元素前的元素是"受控元素"(该元素需要和`<script>`同时插入),则插入的`<script>`是可以执行的,否则不能执行.同理,如果`<style>`元素前的元素是"受控元素"(该元素需要和`<style>`同时插入),则插入的`<style>`也是可以生效的,否则不能生效.

*注意:`Firefox`在内容类型为`application/xhtml+xml`的XHTML文档中对`innerHTML`更加严格.在XHTML文档中使用`innerHTML`,必须使用格式良好的XHTML代码.否则,在`Firefox`中会静默失败.*

#### outerHTML
读取`outerHTML`属性时,会返回调用它的元素(及所有后代元素)的HTML字符串.在写入`outerHTML`属性时,调用它的元素会被传入的HTML字符串经解释之后生成的DOM子树取代.比如:
````HTML
<div id="content">
    <p>This is a <strong>paragraph</strong> with a list following it.</p>
    <ul>
        <li>Item 1</li>
        <li>Item 2</li>
        <li>Item 3</li>
    </ul>
</div>
````
在`<div>`元素上访问`outerHTML`会返回相同的字符串,包括`<div>`本身.不同浏览器可能会返回不同的字符串(和`innerHTML`情况相同).

如果使用`outerHTML`设置HTML:
````JS
div.outerHTML = "<p>This is a paragraph</p>";
````
则会将上面的字符串(会经过解析)整个替代`<div>`.

#### insertAdjacentHTML()与insertAdjacentText()
关于插入标签的另外两个新增方法是:`insertAdjacentHTML()`和`insertAdjacentText()`.它们都接收两个参数:要插入的标记的位置和要插入的HTML或文本.

第一个参数必须是下列值的一个:
- `"beforebegin"`:插入当前元素前面,作为前一个同胞节点
- `"afterbegin"`:插入当前元素内部,作为新的子节点或放在第一个子节点前面
- `"beforeend"`:插入当前元素内部,作为新的子节点或放在最后一个子节点后面
- `"afterend"`:插入当前元素后面,作为下一个同胞节点.

这几个值是不区分大小写的.第二个参数会作为HTML字符串解析(与`innerHTML`和`outerHTML`相同)或者作为纯文本解析(与`innerText`和`outerText`相同).如果是HTML,则会在解析出错时抛出错误:
````JS
element.insertAdjacentHTML("beforebegin", "<p>Hello world!</p>");
element.insertAdjacentText("beforebegin", "Hello world!");
````

#### 内存与性能问题
使用本节介绍的方法替换子节点可能会在浏览器(特别是IE)中导致内存问题.例如,被移除的子树元素中之前有关联的事件处理程序或其他JS对象指向它,那么元素就不会被垃圾回收.因此在使用这些方法前,最好手动删除要被替换的元素上关联的事件处理程序和JS对象.

当大量插入HTML元素时,使用HTML解析器会比用JS多次创建并插入节点快的多.但是,频繁使用HTML解析器反而会降低性能.因此最好限制使用`innerHTML`和`outerHTML`的次数.

例如,不要这么写:
````JS
for (let value of values) {
    ul.innerHTML += `<li>${value}</li>`;    // 别这样做!
}
````
而应该这么写以降低`innerHTML`的赋值次数:
````JS
let itemsHtml = "";
for (let value of values) {
    itemsHtml += `<li>${value}</li>`;
}
ul.innerHTML = itemsHtml;
// 或 ul.innerHTML = values.map(value => `<li>${value}</li>`).join('');
````

#### 跨站点脚本
尽管`innerHTML`不会执行自己创建的`<script>`标签,但仍然向恶意用户暴露了很大的攻击面,因为可以利用将输入信息赋值给`innerHTML`(如果JS中有这样逻辑的代码)等方法来执行`onclick`之类的属性.

所以,如果页面中要使用用户提供的信息,则不建议使用`innerHTML`.与使用`innerHTML`获得的方便相比,防止XSS攻击更让人头疼.此时一定要隔离要插入的数据,在插入页面前必须毫不犹豫地使用相关的库对它们进行转义.

### scrollIntoView()
`HTML5`标准化了`scrollIntoView()`,该方法存在于所以HTML元素上,可以滚动浏览器窗口或容器元素以便包含元素进入视口.这个方法的参数如下:
- `alignToTop`:是一个布尔值.
  - `true`:窗口滚动后元素的顶部与视口顶部对齐.
  - `false`:窗口滚动后元素的底部与视口底部对齐.
- `scrollIntoViewOptions`:是一个选项对象.
  - `behavior`:定义过渡动画,可取的值为`"smooth"`,`"auto"`,默认为`"auto"`.
  - `block`:定义垂直方向的对齐,可取的值为`"start"`,`"center"`,`"end"`和`"nearest"`,默认为`start`.
  - `inline`:定义水平方向的对齐,可取的值为`"start"`,`"center"`,`"end"`和`"nearest"`,默认为`"nearest"`.

不传参数等同于`alignToTop`为`true`.上面`alignToTop`和`scrollIntoViewOptions`是二选一的.

例如:
````JS
document.forms[0].scrollIntoView({behavior: 'smooth', block: 'start'});
document.forms[0].scrollIntoView(true);
````

这个方法可以用来在页面上发生某个事件时引起用户关注.把焦点设置到一个元素上也会导致浏览器将元素滚动到可见位置.

## 专有扩展

