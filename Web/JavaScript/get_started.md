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

本笔记是《JavaScript高级程序设计（第4版）》(Professional JavaScript for Web Developers, 4th Edition)的阅读笔记.

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
    - [children属性](#children属性)
    - [contains()方法](#contains方法)
    - [插入标记](#插入标记-1)
      - [innerText属性](#innertext属性)
      - [outerText](#outertext)
      - [滚动](#滚动)
- [DOM2 和 DOM3](#dom2-和-dom3)
  - [DOM的演进](#dom的演进)
    - [XML命名空间](#xml命名空间)
      - [Node的变化](#node的变化)
      - [Document的变化](#document的变化)
      - [Element的变化](#element的变化)
      - [NamedNodeMap的变化](#namednodemap的变化)
    - [其他变化](#其他变化)
      - [DocumentType的变化](#documenttype的变化)
      - [Document的变化](#document的变化-1)
      - [Node的变化](#node的变化-1)
      - [内嵌窗格的变化](#内嵌窗格的变化)
  - [样式](#样式)
    - [存储元素样式](#存储元素样式)
      - [DOM](#dom-2)
      - [计算样式](#计算样式)
    - [操作样式表](#操作样式表)
      - [CSS规则](#css规则)
      - [创建规则](#创建规则)
    - [元素尺寸](#元素尺寸)
      - [偏移尺寸](#偏移尺寸)
      - [客户端尺寸](#客户端尺寸)
      - [滚动尺寸](#滚动尺寸)
      - [确定元素尺寸](#确定元素尺寸)
  - [遍历](#遍历)
    - [NodeIterator](#nodeiterator)
    - [TreeWalker](#treewalker)
  - [范围](#范围)
    - [DOM范围](#dom范围)
    - [简单选择](#简单选择)
    - [复杂选择](#复杂选择)
    - [操作范围](#操作范围)
    - [范围插入](#范围插入)
    - [范围折叠](#范围折叠)
    - [范围比较](#范围比较)
    - [复制范围](#复制范围)
    - [清理](#清理)
- [事件](#事件)
  - [事件流](#事件流)
    - [事件冒泡](#事件冒泡)
    - [事件捕获](#事件捕获)
    - [DOM事件流](#dom事件流)
  - [事件处理程序](#事件处理程序)
    - [HTML事件处理程序](#html事件处理程序)
    - [DOM0事件处理程序](#dom0事件处理程序)
    - [DOM2事件处理程序](#dom2事件处理程序)
    - [IE事件处理程序](#ie事件处理程序)
    - [跨浏览器事件处理程序](#跨浏览器事件处理程序)
  - [事件(Event)对象](#事件event对象)
    - [DOM事件对象](#dom事件对象)
    - [IE事件对象](#ie事件对象)
    - [跨浏览器事件对象](#跨浏览器事件对象)
  - [事件类型](#事件类型)
    - [用户界面事件(UIEvent)](#用户界面事件uievent)
      - [load事件](#load事件)
      - [unload事件(已弃用)](#unload事件已弃用)
      - [resize事件](#resize事件)
      - [scroll事件](#scroll事件)
    - [焦点事件(FocusEvent)](#焦点事件focusevent)
    - [鼠标(MouseEvent)和滚轮事件(WheelEvent)](#鼠标mouseevent和滚轮事件wheelevent)
      - [客户端坐标](#客户端坐标)
      - [页面坐标](#页面坐标)
      - [屏幕坐标](#屏幕坐标)
      - [修饰键](#修饰键)
      - [相关元素](#相关元素)
      - [鼠标按键](#鼠标按键)
      - [额外事件信息](#额外事件信息)
      - [mousewheel事件](#mousewheel事件)
      - [触摸屏设备](#触摸屏设备)
      - [无障碍问题](#无障碍问题)
    - [键盘(KeyboardEvent)与输入事件(TextEvent)](#键盘keyboardevent与输入事件textevent)
      - [键码](#键码)
      - [字符编码](#字符编码)
      - [DOM3的变化](#dom3的变化)
      - [textInput事件(已废弃)](#textinput事件已废弃)
    - [合成事件(CompositionEvent)](#合成事件compositionevent)
    - [变化事件(MutationEvent)](#变化事件mutationevent)
    - [HTML5事件](#html5事件)
      - [contextmenu事件](#contextmenu事件)
      - [beforeunload事件](#beforeunload事件)
      - [DOMContentLoaded事件](#domcontentloaded事件)
      - [readystatechange事件](#readystatechange事件)
      - [pageshow与pagehide事件](#pageshow与pagehide事件)
      - [hashchange事件](#hashchange事件)
    - [设备事件](#设备事件)
      - [orientationchange事件(已废弃)](#orientationchange事件已废弃)
      - [deviceorientation事件](#deviceorientation事件)
      - [devicemotion事件](#devicemotion事件)
    - [触摸及手势事件](#触摸及手势事件)
      - [触摸事件(TouchEvent)](#触摸事件touchevent)
      - [手势事件(GestureEvent)](#手势事件gestureevent)
    - [事件参考](#事件参考)
  - [内存和性能](#内存和性能)
    - [事件委托](#事件委托)
    - [删除事件处理程序](#删除事件处理程序)
  - [模拟事件](#模拟事件)
    - [DOM模拟事件](#dom模拟事件)
      - [模拟鼠标事件](#模拟鼠标事件)
      - [模拟键盘事件](#模拟键盘事件)
      - [模拟其他事件](#模拟其他事件)
      - [自定义DOM事件](#自定义dom事件)
    - [IE事件模拟](#ie事件模拟)
    - [使用事件构造器](#使用事件构造器)
- [动画与Canvas图形](#动画与canvas图形)
  - [使用requestAnimationFrame](#使用requestanimationframe)
    - [早期定时动画和问题](#早期定时动画和问题)
    - [requestAnimationFrame](#requestanimationframe)
    - [cancelAnimationFrame](#cancelanimationframe)
    - [通过requestAnimationFrame节流](#通过requestanimationframe节流)
  - [基本的画布功能](#基本的画布功能)
  - [2D绘图上下文](#2d绘图上下文)
    - [填充和描边](#填充和描边)
    - [绘制矩形](#绘制矩形)
    - [绘制路径](#绘制路径)
    - [绘制文本](#绘制文本)
    - [变换](#变换)
    - [绘制图像](#绘制图像)
    - [阴影](#阴影)
    - [渐变](#渐变)
    - [图案](#图案)
    - [图像数据](#图像数据)
    - [合成](#合成)
  - [WebGL](#webgl)
    - [WebGL上下文](#webgl上下文)
    - [WebGL基础](#webgl基础)
    - [WebGL1与WebGL2](#webgl1与webgl2)
- [表单脚本](#表单脚本)
  - [表单基础](#表单基础)
    - [提交表单](#提交表单)
    - [重置表单](#重置表单)
    - [表单字段](#表单字段)
      - [表单字段的公共属性](#表单字段的公共属性)
      - [表单字段的公共方法](#表单字段的公共方法)
      - [表单字段的公共事件](#表单字段的公共事件)
  - [文本框编程](#文本框编程)
    - [选择文本](#选择文本)
      - [select事件](#select事件)
      - [取得选中的文本](#取得选中的文本)
      - [部分选中的文本](#部分选中的文本)
    - [输入过滤](#输入过滤)
      - [屏蔽字符](#屏蔽字符)
      - [处理剪贴板](#处理剪贴板)
    - [自动切换](#自动切换)
    - [HTML5约束验证API](#html5约束验证api)
      - [必填字段](#必填字段)
      - [更多输入类型](#更多输入类型)
      - [输入模式](#输入模式)
      - [检测有效性](#检测有效性)
      - [禁用验证](#禁用验证)
  - [选择框编程](#选择框编程)
    - [选项处理](#选项处理)
    - [添加选项](#添加选项)
    - [移除选项](#移除选项)
    - [移动和重排选项](#移动和重排选项)
  - [表单序列化](#表单序列化)
  - [富文本编辑](#富文本编辑)
    - [使用contenteditable](#使用contenteditable)
    - [与富文本交互](#与富文本交互)
    - [富文本选择](#富文本选择)
    - [通过表单提交富文本](#通过表单提交富文本)
- [JavaScript API](#javascript-api)
  - [Atomics与SharedArrayBuffer](#atomics与sharedarraybuffer)
    - [SharedArrayBuffer](#sharedarraybuffer)
    - [原子操作基础](#原子操作基础)
  - [跨上下文消息](#跨上下文消息)
  - [Encoding API](#encoding-api)
    - [文本编码](#文本编码)
      - [批量编码](#批量编码)
      - [流编码](#流编码)
    - [文本编码](#文本编码-1)
      - [批量解码](#批量解码)
      - [流解码](#流解码)
  - [File API与Blob API](#file-api与blob-api)
    - [File类型](#file类型)
    - [FileReader类型](#filereader类型)
    - [FileReaderSync类型](#filereadersync类型)
    - [Blob与部分读取](#blob与部分读取)
      - [对象URL与Blob](#对象url与blob)
    - [读取拖放文件](#读取拖放文件)
  - [媒体元素](#媒体元素)
    - [属性](#属性-2)
    - [事件](#事件-1)
    - [自定义媒体播放器](#自定义媒体播放器)
    - [检测编解码器](#检测编解码器)
    - [音频类型](#音频类型)
  - [原生拖放](#原生拖放)
    - [可拖动能力](#可拖动能力)
    - [拖动事件](#拖动事件)
    - [自定义放置目标](#自定义放置目标)
    - [dataTransfer对象](#datatransfer对象)
    - [dropEffect与effectAllowed](#dropeffect与effectallowed)
    - [其他成员](#其他成员)
  - [Notifications API](#notifications-api)
    - [通知权限](#通知权限)
    - [显示和隐藏通知](#显示和隐藏通知)
    - [通知生命周期回调](#通知生命周期回调)
  - [Page Visibility API](#page-visibility-api)
  - [Stream API](#stream-api)
    - [理解流](#理解流)
      - [块,内部队列和反压](#块内部队列和反压)
    - [可读流](#可读流)
      - [ReadableStreamDefaultController](#readablestreamdefaultcontroller)
      - [ReadableStreamDefaultReader](#readablestreamdefaultreader)
    - [可写流](#可写流)
      - [创建WritableStream](#创建writablestream)
      - [WritableStreamDefaultWriter](#writablestreamdefaultwriter)
    - [转换流](#转换流)
    - [通过管道连接流](#通过管道连接流)
  - [计时API](#计时api)
    - [High Resolution Time API](#high-resolution-time-api)
    - [Performance Timeline API](#performance-timeline-api)
      - [User Timing API](#user-timing-api)
      - [Navigation Timing API](#navigation-timing-api)
      - [Resource Timing API](#resource-timing-api)
  - [Web组件](#web组件)
    - [HTML模板](#html模板)
      - [使用DocumentFragment](#使用documentfragment)
      - [使用`<template>`标签](#使用template标签)
      - [模板脚本](#模板脚本)
    - [影子DOM](#影子dom)
      - [理解影子DOM](#理解影子dom)
      - [创建影子DOM](#创建影子dom)
      - [使用影子DOM](#使用影子dom)
      - [合成与影子DOM槽位](#合成与影子dom槽位)
      - [事件重定向](#事件重定向)
    - [自定义元素](#自定义元素)
      - [创建自定义元素](#创建自定义元素)
      - [使用自定义元素生命周期方法](#使用自定义元素生命周期方法)
      - [升级自定义元素](#升级自定义元素)
  - [Web Cryptography API](#web-cryptography-api)
    - [生成随机数](#生成随机数)
    - [使用SubtleCrypto对象](#使用subtlecrypto对象)
      - [生成密码学摘要](#生成密码学摘要)
      - [CryptoKey与算法](#cryptokey与算法)
      - [生成CryptoKey](#生成cryptokey)
- [错误处理与调试](#错误处理与调试)
  - [浏览器错误报告](#浏览器错误报告)
    - [桌面控制台](#桌面控制台)
    - [移动控制台](#移动控制台)
  - [错误处理](#错误处理)
    - [try/catch语句](#trycatch语句)
      - [finally子句](#finally子句)
      - [错误类型](#错误类型)
    - [抛出错误](#抛出错误)
    - [error事件](#error事件)
    - [识别错误](#识别错误)
      - [静态代码分析器](#静态代码分析器)
      - [类型转换错误](#类型转换错误)
      - [数据类型错误](#数据类型错误)
      - [通信错误](#通信错误)
    - [区分重大与非重大错误](#区分重大与非重大错误)
    - [把错误记录到服务器中](#把错误记录到服务器中)
  - [调试技术](#调试技术)
    - [把消息记录到控制台](#把消息记录到控制台)
    - [理解控制台运行时](#理解控制台运行时)
    - [使用JS调试器](#使用js调试器)
    - [在页面中打印消息](#在页面中打印消息)
    - [补充控制台方法](#补充控制台方法)
    - [抛出错误](#抛出错误-1)
  - [旧版IE的常见错误](#旧版ie的常见错误)
- [处理XML](#处理xml)
  - [浏览器对XML DOM的支持](#浏览器对xml-dom的支持)
    - [DOM Level2 Core](#dom-level2-core)
    - [DOMParser类型](#domparser类型)
    - [XMLSerializer](#xmlserializer)
  - [浏览器对XPath的支持](#浏览器对xpath的支持)
    - [DOM Level 3 XPath](#dom-level-3-xpath)
    - [单个节点结果](#单个节点结果)
    - [简单类型结果](#简单类型结果)
    - [默认类型结果](#默认类型结果)
    - [命名空间支持](#命名空间支持)
  - [浏览器对XSLT的支持](#浏览器对xslt的支持)
    - [XSLTProcessor类型](#xsltprocessor类型)
    - [使用参数](#使用参数)
    - [重置处理器](#重置处理器)
- [JSON](#json)
  - [语法](#语法)
    - [简单值](#简单值)
    - [对象](#对象-1)
    - [数组](#数组)
  - [解析与序列化](#解析与序列化)
    - [JSON对象](#json对象)
    - [序列化选项](#序列化选项)
      - [过滤结果](#过滤结果)
      - [字符串缩进](#字符串缩进)
    - [toJSON()方法](#tojson方法)
    - [解析选项](#解析选项)
- [网络请求与远程资源](#网络请求与远程资源)
  - [XMLHttpRequest](#xmlhttprequest)
    - [使用XHR](#使用xhr)
    - [HTTP头部](#http头部)
    - [GET请求](#get请求)
    - [POST请求](#post请求)
    - [XMLHttpRequest Level2](#xmlhttprequest-level2)
      - [FormData类型](#formdata类型)
      - [超时](#超时)
      - [overrideMimeType()方法](#overridemimetype方法)
  - [进度事件](#进度事件)
    - [progress事件](#progress事件)
  - [跨源资源共享](#跨源资源共享)
    - [预检请求](#预检请求)
    - [凭据请求](#凭据请求)
  - [替代性跨源技术](#替代性跨源技术)
  - [Fetch API](#fetch-api)
    - [基本用法](#基本用法-2)
      - [分派请求](#分派请求)
      - [读取响应](#读取响应)
      - [处理状态码和请求失败](#处理状态码和请求失败)
      - [自定义选项](#自定义选项)
    - [常见Fetch请求模式](#常见fetch请求模式)
      - [发送JSON数据](#发送json数据)
      - [在请求体中发送参数](#在请求体中发送参数)
      - [发送文件](#发送文件)
      - [加载Blob文件](#加载blob文件)
      - [发送跨源请求](#发送跨源请求)
      - [中断请求](#中断请求)
    - [Headers对象](#headers对象)
      - [Headers与Map的相似之处](#headers与map的相似之处)
      - [Headers独有的特性](#headers独有的特性)
      - [头部护卫](#头部护卫)
    - [Request对象](#request对象)
      - [创建Request对象](#创建request对象)
      - [克隆Request对象](#克隆request对象)
      - [在fetch()中使用Request对象](#在fetch中使用request对象)
    - [Response对象](#response对象)
      - [创建Response对象](#创建response对象)
      - [读取响应状态信息](#读取响应状态信息)
      - [克隆Response对象](#克隆response对象)
    - [Request,Response及Body混入](#requestresponse及body混入)
      - [Body.text()](#bodytext)
      - [Body.json()](#bodyjson)
      - [Body.formData()](#bodyformdata)
      - [Body.arrayBuffer()](#bodyarraybuffer)
      - [Body.blob()](#bodyblob)
      - [一次性流](#一次性流)
      - [使用ReadableStream主体](#使用readablestream主体)
  - [Beacon API](#beacon-api)
  - [Web Socket](#web-socket)
    - [API](#api)
    - [发送和接收数据](#发送和接收数据)
    - [其他事件](#其他事件)
  - [安全](#安全)
- [客户端存储](#客户端存储)
  - [cookie](#cookie)
    - [限制](#限制)
    - [cookie的构成](#cookie的构成)
    - [JS中的cookie](#js中的cookie)
    - [子cookie](#子cookie)
    - [使用cookie的注意事项](#使用cookie的注意事项)
  - [Web Storage](#web-storage)
    - [Storage类型](#storage类型)
    - [sessionStorage对象](#sessionstorage对象)
    - [localStorage对象](#localstorage对象)
    - [存储事件](#存储事件)
    - [限制](#限制-1)
  - [IndexedDB](#indexeddb)
    - [数据库](#数据库)
    - [对象存储](#对象存储)
    - [事务](#事务)
    - [插入对象](#插入对象)
    - [通过游标查询](#通过游标查询)
    - [键范围](#键范围)
    - [设置游标的方向](#设置游标的方向)
    - [索引](#索引)
    - [并发问题](#并发问题)
    - [限制](#限制-2)
- [模块](#模块)
  - [理解模块模式](#理解模块模式)
    - [模块标识符](#模块标识符)
    - [模块依赖](#模块依赖)
    - [模块加载](#模块加载)
    - [入口](#入口)
    - [异步依赖](#异步依赖)
    - [动态依赖](#动态依赖)
    - [静态分析](#静态分析)
    - [循环依赖](#循环依赖)
  - [凑合的模块模式](#凑合的模块模式)
  - [使用ES6之前的模块加载器](#使用es6之前的模块加载器)
  - [使用ES6模块](#使用es6模块)
    - [模块标签及定义](#模块标签及定义)
    - [模块加载](#模块加载-1)
    - [模块行为](#模块行为)
    - [模块导出](#模块导出)
    - [模块导入](#模块导入)
    - [模块转移导出](#模块转移导出)
    - [工作者模块](#工作者模块)
    - [向后兼容](#向后兼容)
- [工作者线程](#工作者线程)
  - [工作者线程简介](#工作者线程简介)
    - [工作者线程与线程](#工作者线程与线程)
    - [工作者线程的类型](#工作者线程的类型)
    - [WorkerGlobalScope](#workerglobalscope)
      - [WorkerGlobalScope属性和方法](#workerglobalscope属性和方法)
      - [WorkerGlobalScope的子类](#workerglobalscope的子类)
  - [专用工作者线程](#专用工作者线程)

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
`arguments`不反映参数的默认值,只反映传给函数的参数.此外,对于含有默认值的命名参数,修改命名参数不会影响`arguments`对象:
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

`try/catch`表达式能捕获`await`表达式抛出的错误:
````JS
async function foo() {
    console.log(1); // 1
    try {
        console.log(await (() => { throw 2; })());  // <不输出>
    } catch (e) {
        console.log(e); // 2
    }
    console.log(3); // 3
}
console.log(foo()); // Promise {<fulfilled>: undefined}
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
各家浏览器还有很多未被标准化的专有扩展.

### children属性
`children`属性是一个`HTMLCollection`,只包含元素的`Element`类型的子节点.如果元素的子节点类型全部是元素类型,那`children`和`childNodes`中包含的节点应该是一样的.

### contains()方法
`contains()`方法在要搜索的祖先元素上调用,参数是待确定的目标节点.如果目标节点是被搜索节点的后代,`contains()`返回`true`,否则返回`false`:
````JS
console.log(document.documentElement.contains(document.body));  // true
````

另外,使用`DOM level 3`的`compareDocumentPosition()`方法也可以确定节点间的关系.这个方法会返回表示两个节点关系的位掩码:
- `0x1`:断开(传入的节点不在文档中)
- `0x2`:领先(传入的节点在DOM树中位于参考节点之前)
- `0x4`:随后(传入的节点在DOM树中位于参考节点之后)
- `0x8`:包含(传入的节点是参考节点的祖先)
- `0x10`:被包含(传入的节点是参考节点的后代)

因此上面的代码等价于:
````JS
let result = document.documentElement.compareDocumentPosition(document.body);   // 0x14
console.log(!!(result & 0x10));
````

IE9及之后的版本,以及所有现代浏览器都支持`contains()`和`compareDocumentPosition()`方法.

### 插入标记
`HTML5`将`innerHTML`和`outerHTML`纳入了标准,但`innerText`和`outerText`没有入选.

#### innerText属性
`innerText`属性对应元素中包含的所有文本内容,无论文本在子树中哪个层级.在读取值时,`innerText`会按照深度优先的顺序将子树中所有文本节点拼接起来.在用于写入值时,`innerText`会移除元素所有后代并插入一个包含该值的文本节点.

例如对于:
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
`innerText`属性会返回以下字符串:
```
This is a paragraph with a list following it.
Item 1
Item 2
Item 3
```

若使用
````JS
div.innerText = "Hello & welcome, <b>\"reader\"!</b>";
````
则执行这行代码后,HTML页面中的`<div>`元素就会变成这样:
````HTML
<div id="content">Hello &amp; welcome, &lt;b&gt;&quot;reader&quot;!&lt;/b&gt;</div>
````

`innerText`已经得到所有浏览器支持.

#### outerText
`outerText`与`innerText`是类似的,只不过作用范围包含调用它的节点.要读取文本值时,`outerText`与`innerText`实际上会返回同样的内容.但在写入文本值时,`outerText`会用新的文本节点替换掉`outerText`所在的整个元素.

`outerText`未被所有主流浏览器支持,不推荐使用这个属性.

#### 滚动
不同浏览器仍然有除了`scrollIntoView()`以外的滚动相关的专有方法.例如:`scrollIntoViewIfNeeded()`仅仅在元素不可见的情况下,将其滚动到窗口中或包含窗口中,使其可见;如果已经在视口中可见,则这个方法什么也不做.

但`scrollIntoView()`是唯一一个所有浏览器都支持的方法,所以只用它就可以了.

# DOM2 和 DOM3
## DOM的演进
`DOM2 Core`和`DOM3 Core`模块的目标是扩展`DOM API`,满足`XML`的所有需要并提供更好的错误处理和特性检测.很大程度上,这意味着支持XML命名空间的概念.`DOM2 Core`没有新增任何类型,仅仅在`DOM1 Core`基础上增加了一些方法和属性.`DOM3 Core`除了增强原有类型,也新增了一些新类型.

`DOM View`和`HTML`模块也丰富了`DOM`接口,定义了新的属性和方法.

### XML命名空间
XML命名空间可以实现在一个格式规范的文档中混用不同的XML语言,而不必担心元素命名冲突.XML命名空间在XHTML中才支持,HTML并不支持.

命名空间是使用`xmlns`指定的.XHTML的命名空间是`"http://www.w3.org/1999/xhtml"`,应该包含在任何格式规范的XHTML页面的`<html>`元素中:
````XHTML
<html xmln="http://www.w3.org/1999/xhtml">
    <head>
        <!-- ... -->
    </head>
    <body>
        <!-- ... -->
    </body>
</html>
````
上述例子中,所有元素都默认属于XHTML命名空间.可以使用`xmlns`给命名空间创建一个前缀,格式未`xmlns:前缀`,如下所示:
````JS
<xhtml:html xmlns:xhtml="http://www.w3.org/1999/xhtml">
    <xhtml:head>
        <!-- ... -->
    </xhtml:head>
    <xhtml:body xhtml:class="home">
        <!-- ... -->
    </xhtml:body>
</xhtml:html>
````
上例中为XHTML命名空间定义了一个前缀`xhtml`,同时所有XHTML元素都必须加上这个前缀.为了避免混淆,属性也可以加上命名空间前缀.

对于一个文档混合使用多种XML语言时,命名空间就有必要了.  
例如,下面这个文档就使用了`XHTML`和`SVG`两种语言:
````XML
<html xmlns="http://www.w3.org/1999/xhtml">
    <head>
        <!-- ... -->
    </head>
    <body>
        <s:svg xmlns:s="http://www.w3.org/2000/svg" version="1.1"
            viewBox="0 0 100 100" style="width:100%; height:100%">
            <s:rect x="0" y="0" width="100" height="100" style="fill:red" />
        </s:svg>
    </body>
</html>
````
在上述例子中,通过给`<svg>`元素设置自己的命名空间,将其标识为当前文档的外来元素.因此,这个文档虽然是XHTML文档,但由于使用了命名空间,其中包含的SVG代码也是有效的.

#### Node的变化
为了与节点交互,并获取其命名空间,`DOM2`中,`Node`类型新增了以下特定于命名空间的属性:
- `localName`:不包含命名空间前缀的节点名
- `namespaceURI`:节点的命名空间URL,如果没有指定则为`null`;
- `prefix`:命名空间前缀,如果未指定则为`null`.

在节点使用命名空间前缀的情况下,`nodeName`等于`prefix + ":" + localName`.

例如对于上例使用了`XHTML`和`SVG`两种语言的文档,`<html>`元素的`localName`和`tagName`都是`"html"`,`namespaceURL`是`"http://www.w3.org/1999/xhtml"`,而`prefix`是`null`.对于`<s:svg>元素`,`localName`是`"svg"`,`tagName`是`"s:svg"`,`namespaceURI`是`"https://www.w3.org/2000/svg"`,而`prefix`是`"s"`.

`DOM3`进一步增加了如下与命名空间相关的方法:
- `isDefaultNamespace(namespaceURI)`:返回布尔值,表示`namespaceURI`是否为节点的默认命名空间
- `lookupNamespaceURI(prefix)`:返回给定`prefix`的命名空间URI
- `lookupPrefix(namespaceURI)`:返回给定的`namespaceURI`的前缀

对前面的例子,使用如下代码:
````JS
console.log(document.body.isDefaultNamespace("http://www.w3.org/1999/xhtml"));  // true
// 假设svg包含对<s:svg>元素的引用
console.log(svg.lookupPrefix("http://www.w3.org/2000/svg"));    // "s"
console.log(svg.lookupNamespaceURI("s"));   // "http://www.w3.org/2000/svg"
````

#### Document的变化
`DOM2`在`Document`上新增了如下命名空间特定的方法:
- `createElementNS(namespaceURI, tagName)`:以给定的标签名`tagName`创建指定命名空间`namespaceURI`的一个新元素
- `createAttributeNS(namespaceURI, attributeName)`:以给定的属性名`attributeName`创建指定命名空间`namespaceURI`的一个新属性
- `getElementsByTagNameNS(namespaceURI, tagName)`:返回指定命名空间`namespaceURI`中所有标签名为`tagName`的元素的`NodeList`.

所有这些方法传入的是相应命名空间URI(不是命名空间前缀):
````JS
let svg = document.createElementNS("http://www.w3.org/2000/svg", "svg");
let att = document.createAttributeNS("http://www.somewhere.com", "random");
let elems = document.getElementsByTagNameNS("http://www.w3.org/1999/xhtml", "*");    // 获取所有XHTML元素
````

#### Element的变化
`DOM2 Core`对`Element`类型的更新主要集中在对属性的操作上.下面是新增的方法:
- `getAttributeNS(namespaceURI, localName)`:取得指定命名空间`namespaceURI`中名为`localName`的属性
- `getAttributeNodeNS(namespaceURI, localName)`:取得指定命名空间`namespaceURI`中名为`localName`的属性节点
- `getElementsByTagNameNS(namespaceURI, tagName)`:取得指定命名空间`namespaceURI`中标签名为`tagName`的元素的`NodeList`
- `hasAttributeNS(namespaceURI, localName)`:返回布尔值,表示元素中是否有命名空间`namespaceURI`下名为`localName`的属性(注意,`DOM2 Core`也添加了不带命名空间的`hasAttribute()`方法)
- `removeAttributeNS(namespaceURI, localName)`:删除指定命名空间`namespaceURI`中名为`localName`的属性
- `setAttributeNS(namespaceURI, qualifiedName, value)`:设置指定命名空间`namespaceURI`中名为`qualifiedName`的属性为`value`
- `setAttributeNodeNS(attNode)`:为元素设置(添加)包含命名空间信息的属性节点`attNode`

#### NamedNodeMap的变化
`NamedNodeMap`也增加了处理命名空间的方法.因为`NamedNodeMap`主要表示属性,所以这些方法大都适用于属性:
- `getNamedItemNS(namespaceURI, localName)`:取得指定命名空间`namespaceURI`中名为`localName`的项
- `removeNamedItemNS(namespaceURI, localName)`:删除指定命名空间`namespaceURI`中名为`localName`的项
- `setNamedItemNS(node)`:为元素设置(添加)包含命名空间信息的节点

### 其他变化
`DOM2 Core`还对DOM的其他部分做了一些更新.这些变化与XML命名空间无关,主要关注DOM API的完整性与可靠性.

#### DocumentType的变化
`DocumentType`新增了3个属性:`publicId`,`systemId`和`internalSubset`.`publicId`,`systemId`属性表示文档类型声明中有效但无法使用`DOM1 API`访问的数据.`internalSubset`用于访问文档声明中可能包含的额外定义.比如下面这个HTML文档类型声明:
````HTML
<!DOCTYPE HTML PUBLIC "-// W3C// DTD HTML 4.01// EN"
"http://www.w3.org/TR/html4/strict.dtd"
[<!ELEMENT name (#PCDATA)>] >
````

其`publicId`是`"-// W3C// DTD HTML 4.01// EN"`,而`systemId`是`"http://www.w3.org/TR/html4/strict.dtd"`.`internalSubset`返回`"<!ELEMENT name (#PCDATA)>"`,HTML文档中几乎不会涉及文档类型的内部子集,XML文档中稍微常用一些.

#### Document的变化
`Document`类型的更新中唯一与命名空间无关的方法是`importNode()`.这个方法的目的是从其他文档获取一个节点并导入到新文档,以便将其插入新文档.每个节点都有一个`ownerDocument`属性,表示所属文档,如果调用`appendChild()`方法时传入节点的`ownerDocument`不是指向当前文档,则会发生错误.而调用`importNode()`导入其他文档的节点会返回一个新节点,这个新节点的`ownerDocument`属性是正确的.

`importNode()`方法接收两个参数:要复制的节点和表示是否同时复制子树的布尔值,返回结果是适合在当前文档中使用的新节点.(参数类似于`cloneNode()`)

这个方法在`XML`文档中使用会更多一点.

`DOM2 View`给`Document`类型增加了新属性`defaultView`,是一个指向拥有当前文档的窗口(或窗格`<frame>`的指针).

`DOM2 Core`还针对`document.implementation`对象增加了两个新方法:`createDocumentType()`和`createDocument()`.前者用于创建`DocumentType`类型的新节点,接收3个参数:文档类型名称,`publicId`和`systemId`.比如:
````JS
let doctype = document.implementation.createDocumentType("html",
            "-// W3C// DTD HTML 4.01// EN",
            "http://www.w3.org/TR/html4/strict.dtd");
````

已有文档的文档类型不可更改,因此`createDocumentType()`只在创建新文档时才会用到,而创建新文档要使用`createDocument()`方法.`createDocument()`接收3个参数:文档元素的`namespaceURI`,文档元素的标签名和文档类型.  
例如,使用以下代码创建一个XHTML文档:
````JS
let doctype = document.implementation.createDocumentType("html",
            "-// W3C// DTD XHTML 1.0 Strict// EN",
            "http://www.w3.org/TR/xhtml/DTD/xhtml1-strict.dtd");
let doc = document.implementation.createDocument("http://www.w3.org/1999/xhtml",
        "html", doctype);
````
上述文档只有一个文档元素`<html>`(当然也有`<!DOCTYPE>`),其他一切都需要另行添加.

`DOM2 HTML`模块也为`document.implamentation`对象添加了`createHTMLDocument()`方法.这个方法可以创建一个完整的HTML文档,包含`<html>`,`<head>`,`<title>`,`<body>`元素.这个方法只接收一个参数,即新创建文档的标题(放到`<title>`元素中).返回一个新的HTML文档(`HTMLDocument`类型的实例).

#### Node的变化
`DOM3`新增了两个用于比较节点的方法:`isSameNode()`和`isEqualNode()`.这两个方法都接收一个节点参数,如果这个节点与参考节点相同或相等,则返回`true`.节点相同,意味着引用同一个对象;节点相等,意味着节点类型相同,拥有相等的属性(`nodeName`,`nodeValue`等),而且`attributes`和`childNodes`也相等(即相同的位置包含相等的值).

`DOM3`也增加了给DOM节点附加额外数据的方法.`setUserData()`方法接收3个参数:键,值,处理函数,用于给节点追加数据.

**<p class="red_font">无论是`setUserData()`还是`getUserData()`,都已经在`DOM4`弃用了,因此多数浏览器不支持它们</p>**

例如:
````JS
document.body.setUserData("name", "aaa", function() {});
````
然后,可以通过相同的键在取得这个信息:
````JS
let value = document.body.getUserData("name");
````
处理函数接收5个参数:表示操作类型的数值(1表示复制,2表示导入,3表示删除,4表示重命名),数据的键,数据的值,源节点,目标节点.删除节点时,源节点为`null`;除复制外,目标节点都为`null`.

#### 内嵌窗格的变化
`DOM2 HTML`给`HTMLIFrameElement`(即`<iframe>`,内嵌窗格)类型新增了一个属性,叫`contentDocument`.这个属性包含代表子内嵌窗格中的内容的`document`对象的指针:
````JS
let iframe = document.getElementById("myIfrane");
let iframeDoc = iframe.contentDocument;
````

`contentDocument`属性是`Document`的实例.

还有一个属性`contentWindow`,返回对应窗格的`window`对象,这个对象上有一个`document`属性.

*注:跨源访问子内嵌窗格的`document`对象会受到安全限制.*

## 样式
HTML中的样式有3中定义方式:外部样式表(`<link>`),文档样式表(`<style>`)和元素特定样式(`style`属性).`DOM2 Style`为这3种应用样式的机制都提供了API.

### 存储元素样式
任何支持`style`属性的HTML元素在JS种都会有一个对应的`style`元素.这个`style`属性是`CSSStyleDeclaration`类型的实例,其中包含通过HTML `style`属性为元素设置的所有样式信息,但不包含通过层叠机制从文档样式和外部样式中继承来的样式.HTML `style`属性中的CSS属性在JS `style`对象中都有相应的属性.因为CSS属性名使用连字符表示法,所以在JS中,这些属性名都必须转换为驼峰大小写形式.  
例如:
- `CSS属性` -- `JS属性`
- `background-image` -- `style.backgroundImage`
- `color` -- `style.color`

CSS属性名`float`是个例外,它是JS保留字,所以`DOM2 Style`规定它在`style`中对应属性为`cssFloat`.

可以读取或修改这些CSS属性:
````JS
let color = div.style.backgroundColor;
div.style.width = "100px";
````

*在标准模式下,所以尺寸都必须包含单位.否则会被忽略.*

如果元素上没有相应的`style`属性,则`style`读一下包含所有可能的CSS属性的空值:
````JS
console.log(document.body.style.animationName); // ""
console.log(document.body.style.alignContent);  // ""
````

对CSS属性赋值`""`或`null`来重置属性.

#### DOM
`DOM2 Style`在`style`对象(`CSSStyleDeclaration`类型)上定义了一些属性和方法.这些属性和方法提供了元素`style`属性的信息并支持修改:
- `cssText`:包含`style`属性中的CSS代码
- `length`:应用给元素CSS属性的数量
- `parentRule`:表示CSS信息的`CSSRule`对象
- `getPropertyPriority(propertyName)`:如果CSS属性`propertyName`使用了`!important`,则返回`"important"`,否则返回空字符串.
- `getPropertyValue(propertyName)`:返回属性`propertyName`的字符串值
- `item(index)`:返回索引为`index`的CSS属性名
- `removeProperty(propertyName)`:从样式中删除CSS属性`propertyName`(删除后,CSS会使用默认值,即使JS访问该属性时返回`""`)
- `setProperty(propertyName, value, priority)`:设置CSS属性`propertyName`的值为`value`,`property`是`"important"`或空字符串.

可以读写`cssText`属性,其返回整个HTML`style`属性字符串.给其赋值则用所给值覆盖原来的`style`属性.

除了使用`item()`方法,也可以使用中括号,也可以使用迭代.其返回的属性名是原始的CSS名称("background-color",不是"backgroundColor").传入的`propertyName`也使用的是原始的CSS名称.

`getPropertyValue()`方法返回CSS属性的字符串表示.

而其对应已经**废弃**的`getPropertyCSSValue(propertyName)`返回包含CSS属性`propertyName`值的`CSSValue`对象,该对象包含`cssText`和`cssValueType`,前者等同于`getPropertyValue()`的返回值,后者是一个数值常数,表示当前值的类型(0表示继承的值,1表示原始值,2表示列表,3表示自定义值).

#### 计算样式
`style`属性不好好从其他样式表层叠继承的同样影响该元素的样式信息(即只显示元素特定样式(`style`属性)所指定的样式).

`DOM2 Style`在`document.defaultView`上增加了`getComputedStyle()`方法,用于获取元素计算后的样式(即实际显示的样式).这个方法接收两个参数:要取得计算样式的元素和伪元素字符串(如`"::after"`).如果不需要查询伪元素,则第二个参数可以传`null`.`getComputedStyle()`方法返回一个`CSSStyleDeclaration`对象,包含元素的计算样式.

例如:
````HTML
<html>
<head>
    <!-- ... -->
    <style type="text/css">
        #myDiv {
            background-color: blue;
            width: 100px;
            height: 200px;
        }
    </style>
</head>
<body>
    <div id="myDiv" style="background-color: red; border: 1px solid black"></div>
</body>
</html>
````
````JS
let div = document.getElementById("myDiv");
// style中只包括元素特定样式
console.log(div.style.width);   // ""

let computedStyle = document.defaultView.getComputedStyle(div, null);
console.log(computedStyle.backgroundColor); // rgb(255, 0, 0)
console.log(computedStyle.width);   // 100px
console.log(computedStyle.height);  // 200px
console.log(computedStyle.border);  // 0.8px solid rgb(0, 0, 0)
````

不同浏览器返回样式值不一定相同.

所有浏览器中计算样式都是只读的.计算样式还包含浏览器内部样式表中的信息,因此`style`属性中的样式不会返回默认值,而计算样式会.但默认值可能会因浏览器而异.

### 操作样式表
`CSSStyleSheet`类型可以表示使用`<link>`(`HTMLLinkElement`)或`<style>`(`HTMLStyleElement`)定义的样式表.

`CSSStyleSheet`继承`StyleSheet`,后者可用作非CSS样式表的基类.以下是`CSSStyleSheet`从`StyleSheet`继承的属性:
- `disabled`:布尔值,表示样式表是否被禁用了(这个属性可以读写,设置为`true`会禁用样式表)
- `href`:如果是使用`<link>`包含的样式表,则返回样式表的URL,否则返回`null`
- `media`:样式表支持的媒体类型的集合`MediaList`,这个集合有一个`length`属性和一个`item()`方法,也可以使用中括号访问集合中特定的项.如果样式表不可用于任何媒体,则返回空列表.
- `ownerNode`:指向拥有当前样式表的节点,在HTML中要么是`<link>`元素,要么是`<style>`元素(在XML中可以是处理指令).如果当前样式表是通过`@import`被包含在另一个样式表中,则这个属性值伪`null`.
- `parentStyleSheet`:如果当前样式表是通过`@import`被包含在另一个样式表中,则这个属性指向导入它的样式表.
- `title`:`ownerNode`的`title`属性.
- `type`:字符串,表示样式表的类型.对于`CSS`样式表来说,就是`"text/css"`.

`CSSStyleSheet`类型的实例是一个只读对象(只有`disable`属性例外).

`CSSStyleSheet`类型还支持以下属性和方法:
- `cssRules`:当前样式表包含的样式规则的实时的`CSSRuleList`集合.
- `ownerRule`:如果样式表是使用`@import`导入的,则指向导入样式表的样式规则;否则为`null`.
- `deleteRule(index)`:在指定位置删除`cssRules`中的规则.
- `insertRule(rule, index)`:在指定位置向`cssRules`中插入规则.

`document.styleSheets`表示文档中可用的样式表集合,即`StyleSheetList`对象.这个集合的`length`属性保存着文档中样式表的数量,而每个样式表都可以使用中括号或`item()`方法获取:
````JS
let sheet = null;
for (let i = 0, len = document.styleSheets.length; i < len; ++i) {
    sheet = document.styleSheets[i];
    console.log(sheet.href);
}
````

其返回的样式表可能会因浏览器而异,但所有浏览器都会包含`<style>`元素和`rel`属性设置为`stylesheet`的`<link>`元素.

通过`<link>`或`<style>`元素也可以直接获取`CSSStyleSheet`对象.DOM在这两个元素上暴露了`sheet`属性,其中包含对应的`CSSStyleSheet`对象.

#### CSS规则
`CSSRule`类型表示样式表中的一条规则.这个类型是一个通用基类.`CSSStyleRule`继承于它(每个对象都包含一个样式信息或者`at-rule`(例如`@font-face`)等).

以下是`CSSStyleRule`对象上可用的属性:
- `cssText`:返回整条规则的文本.这里的文本可能与样式表中实际的文本不一样,因为浏览器内部处理样式表的方式不一样.
- `parentRule`:如果这条规则被其他规则(如`@media`)包含,则指向包含规则,否则是`null`.
- `parentStyleSheet`:包含当前规则的样式表.
- `selectorText`:返回规则的选择符(选择器)文本.这里的文本可能与样式表中实际的文本不一样,因为浏览器内部处理样式表的方式不一样.一般是只读的.
- `style`:返回`CSSStyleDeclaration`对象,可以设置和获取当前规则中的样式.
- `type`**(已弃用)**:数值常量,表示规则类型.对于样式规则,它始终为`1`.

上面的`cssText`属性和`style.cssText`类似,但前者包含选择符文本和环绕声明的大括号,后则会只包括样式声明.此外,`cssText`是只读的,而`style.cssText`可以被读写.

例如:
````CSS
div.box {
    background-color: blue;
    width: 100px;
    height: 200px;
}
div {
    background-color: red;
}
````
上面有两个`CSSStyleRule`对象,即`CSSStyleSheet.cssText`返回的列表的长度为`2`(只要它们在同一个`<style>`内或者由同一个`<link>`引用).

使用以下代码:
````JS
let sheet = document.styleSheets[0];
let rules = sheet.cssRules; // 其等价方法sheet.rules已经被废弃
let rule = rules[0];
console.log(rule.selectorText);         // div.box
console.log(rule.style.cssText);        // background-color: blue; width: 100px; height: 200px;
console.log(rule.cssText);              // div.box { background-color: blue; width: 100px; height: 200px; }
console.log(rule.style.backgroundColor);// blue
console.log(rule.style.width);          // 100px
console.log(rule.style.height);         // 200px
rule.style.backgroundColor = "red"      // 可以修改样式信息
````

#### 创建规则
如上所述,使用`insertRule()`方法向样式表中添加新规则:
````JS
sheet.insertRule("body {background-color: silver}", 0); // 顺序对于CSS非常重要,这里是将样式表作为第一条规则
````

如果要维护的规则增多,最好使用[动态样式加载技术](#动态样式).

### 元素尺寸
#### 偏移尺寸
偏移尺寸,包含元素在屏幕上占用的所有视觉空间.以下4个属性用于取得元素的偏移尺寸:
- `offsetHeight`:元素在垂直方向上占用的像素尺寸,包括它的高度,水平滚动条高度(如果可见)和上,下边框的高度.
- `offsetLeft`:元素左边框外侧距离*包含元素*左边框内侧的像素数.
- `offsetTop`:元素上边框外侧距离*包含元素*上边框内侧的像素数.
- `offsetWidth`:元素在水平方向上占用的像素尺寸,包括它的宽度,垂直滚动条宽度(如果可见)和左,右边框的宽度.
- `offsetParent`:上面所言的*包含元素*,即将被调元素包含在内的元素.`offsetParent`不一定是`parentNode`.

所谓元素,指的是包括内容,内边距,边框,但不包括外边距的部分.所谓像素,如果不特殊说明,表示CSS像素.

![偏移尺寸](img/get_start/offsetFunc.png)

由于所计算的是包含元素,所以由`offsetLeft`和`offsetTop`想推出元素相对于网页的位移,可以不断向上访问并将位移相加,直至根节点:
````JS
function getElementLeft(element) {
    let actualLeft = element.offsetLeft;
    let current = element.offsetParent;
    while (current !== null) {
        actualLeft += current.offsetLeft;
        current = current.offsetParent;
    }
    return actualLeft;
}
````

用该方法得到的实际偏移量是很精确的.但对于使用表格和内嵌窗格的页面布局,它们返回的值会因浏览器不同而有所差异.

*注意:上述的值都是只读的,每次访问都会重写计算,因此,应该尽量减少查询它们的次数.*

#### 客户端尺寸
元素的客户端尺寸包含元素内容及其内边距所占用的空间,但不包括边框,外边距和滚动条.其相关属性有:
- `clientWidth`:客户端的宽度
- `clientHeight`:客户端的高度

![客户端尺寸](img/get_start/clientFunc.png)

这两个属性最常用与确定浏览器视口尺寸,即检测`document.documentElement`(`<html>`或`<body>`元素)的`clientWidth`和`clientHeight`.

*注:客户端尺寸是只读的,每次访问都会重新计算.若内容超出元素边框导致需要滚动时,也只会计算边框内的内容.*

#### 滚动尺寸
滚动尺寸提供了元素内容滚动距离的信息.有些元素,比如`<html>`无须任何代码就可以自动滚动,而其他元素则需要使用CSS的`overflow`属性令其滚动.滚动尺寸相关的属性有如下4个:
- `scrollHeight`:没有滚动条出现时,元素内容的总高度
- `scrollLeft`:内容区左侧隐藏的像素数,设置这个属性可以改变元素的滚动位置.
- `scrollTop`:内容区顶部隐藏的像素数,设置这个属性可以改变元素的滚动位置.
- `scrollWidth`:没有滚动条出现时,元素内容的总宽度.

`scrollLeft`和`scrollTop`是可读写的.

![滚动尺寸](img/get_start/scrollFunc.png)

#### 确定元素尺寸
浏览器在每个元素上都暴露了`getBoundingClientRect()`方法,返回一个`DOMRect`对象,包含6个属性:`left`,`top`,`right`,`bottom`,`height`和`width`.这些属性给出了元素在页面中相对于视口的位置.注意,此处元素表示包含内容,内边距,边框,但不包含外边距的部分.

![确定元素尺寸](img/get_start/getBoundingClientRect.png)

## 遍历
`DOM2 Traversal and Range`模块定义了两个类型用于辅助顺序遍历DOM结构:`NodeIterator`和`TreeWalker`.

这两个类型对DOM进行深度优先遍历,至少允许朝两个方向移动(取决于类型).遍历以给定节点为根,且不会再DOM中超越这个根节点.

例如:
````HTML
<!DOCTYPE html>
<html>
    <head>
        <title>Example</title>
    </head>
    <body>
        <p><b>Hello</b> world!</p>
    </body>
</html>
````

下面是HTML构成的DOM数,序号为其深度优先遍历的顺序.

![遍历顺序](img/get_start/Iterator.png)

如果以`<body>`元素作为根节点遍历,那么绝对不会访问`<html>`元素,`<head>`元素及其子元素.

### NodeIterator
`NodeIterator`可以通过`document.createNodeIterator()`方法创建其实例.这个方法接收以下4个参数:
- `root`:作为遍历根节点的节点.
- `whatToShow`:数值代码,表示应该访问哪些节点.
- `filter`:`NodeFilter`对象或函数,表示是否接受或跳过特定节点.
- `entityReferenceExpansion`:布尔值,表示是否扩展实体引用.这个参数在HTML文档中没有效果,因为实体引用永不扩展.

`whatToShow`参数是一个位掩码,通过应用一个或多个过滤器来指定访问哪些节点.这个参数对应的常量是在`NodeFilter`类型中定义的:
- `NodeFilter.SHOW_ALL`:所有节点
- `NodeFilter.SHOW_ELEMENT`:元素节点
- `NodeFilter.SHOW_ATTRIBUTE`:属性节点.由于DOM的结构,因此实际上用不上.
- `NodeFilter.SHOW_TEXT`:文本节点
- `NodeFilter.SHOW_CDATA_SECTION`:CData区块节点.不是在HTML页面中使用的.
- `NodeFilter.SHOW_ENTITY_REFERENCE`:实体引用节点.不是在HTML页面中使用的.
- `NodeFilter.SHOW_ENTITY`:实体节点.不是在HTML页面中使用的.
- `NodeFilter.SHOW_PROCESSING_INSTRUCTION`:处理指令节点.不是在HTML页面中使用的.
- `NodeFilter.SHOW_COMMENT`:注释节点
- `NodeFilter.SHOW_DOCUMENT`:文档节点
- `NodeFilter.SHOW_DOCUMENT_TYPE`:文档类型节点
- `NodeFilter.SHOW_DOCUMENT_FRAGMENT`:文档片段节点.不是在HTML页面中使用的.
- `NodeFilter.SHOW_NOTATION`:记号节点.不是在HTML页面中使用的.

这些值除了`NodeFilter.SHOW_ALL`之外,都可以组合使用:`NodeFilter.SHOW_ELEMENT | NodeFilter.SHOW_TEXT`

`filter`参数可以用来指定自定义`NodeFilter`对象,或者一个作为节点过滤器的函数.`NodeFilter`对象只有一个方法`acceptNode()`,如果给定节点应该访问,就返回`NodeFilter.FILTER_ACCEPT`,否则返回`NodeFilter.FILTER_SKIP`.创建`NodeFilter`对象,只需要创建一个包含`acceptNode()`方法的对象就可以了:
````JS
let filter = {
    acceptNode(node) {
        return node.tagNode.toLowerCase() == "p" ?
                NodeFilter.FILTER_ACCEPT :
                NodeFilter.FILTER_SKIP;
    }
};
let iterator = document.createNodeIterator(root, NodeFilter.SHOW_ELEMENT,
                                           filter, false);
````

`filter`参数还可以是一个函数,与`acceptNode()`的形式一样:
````JS
let filter = function(node) {
    return node.tagName.toLowerCase() == "p" ?
         NodeFilter.FILTER_ACCEPT :
         NodeFilter.FILTER_SKIP
};
let iterator = document.createNodeIterator(root, NodeFilter.SHOW_ELEMENT,
                                           filter, false);
````

如果不需要指定过滤器,则可以给这个参数传入`null`.

`NodeIterator`的两个主要方法是`nextNode()`和`previousNode()`,分别代表前进一步和后退一步.当到达最后一个节点之后,调用`nextNode()`返回`null`.在根节点处调用`previousNode()`返回`null`.这两个方法都返回指向的节点的引用.当第一次执行`nextNode()`,返回的是根节点.

修改DOM结构也会体现在遍历中.

### TreeWalker
`TreeWalker`是`NodeIterator`的高级版.除了包含同样的`nextNode()`和`previousNode()`方法,`TreeWalker`还添加了如下在DOM结构中向不同方向遍历的方法:
- `parentNode()`:遍历到当前节点的父节点.
- `firstChild()`:遍历到当前节点的第一个子节点.
- `lastChild()`:遍历到当前节点的最后一个子节点.
- `nextSibling()`:遍历到当前节点的下一个同胞节点.
- `previousSibling()`:遍历到当前节点的上一个同胞节点.

`TreeWalker`对象要调用`document.createTreeWalker()`方法来创建,这个方法接收与`document.createNodeIterator()`同样的参数.

不同的是,节点过滤器除了可以返回`NodeFilter.FILTER_ACCEPT`和`NodeFilter.FILTER_SKIP`,还可以返回`NodeFilter.FILTER_REJECT`.在使用`NodeIterator`时,`NodeFilter.FILTER_SKIP`和`NodeFilter.FILTER_REJECT`是一样的.但对于`TreeWalker`,`NodeFilter.FILTER_SKIP`表示跳过节点,访问子树中的下一个节点,而`NodeFilter.FILTER_REJECT`则表示跳过该节点以及该节点的整个子树.

`TreeWalker`类型也有一个名为`currentNode`的属性,表示遍历过程中上一次返回的节点(无论使用的是哪个遍历方法).可以通过修改这个属性来影响接下来遍历的起点.

相比`NodeIterator`,`TreeWalker`类型为遍历DOM提供了更大的灵活性.

## 范围
`DOM2 Traversal and Range`模块定义了范围接口.范围可用于在文档中选择内容,而不用考虑节点之间的界限.(选择在后台发生,用户看不见.)

### DOM范围
`DOM2`在`Document`类型上定义了一个`createRange()`方法,暴露在`document`对象上.使用这个方法可以创建一个`DOM`范围对象(`Range`类型):
````JS
let range = document.createRange();
````

范围对象是与创建它的文档关联的,不能再其他文档中使用.然后可以使用这个范围在后台选择文档的特定部分.创建范围并指定它的位置之后,可以对范围的内容执行一些操作,从而实现对底层DOM树更精细的控制.

`Range`类型的实例拥有以下属性:
- `startContainer`:范围起点所在的节点(选区中第一个子节点的父节点).
- `startOffset`:范围起点在`startContainer`中的偏移量.如果`startContainer`是文本节点,注释节点或CData区块节点,则`startOffset`指范围起点之前跳过的字符数;否则,表示范围中第一个节点的索引.
- `endContainer`:范围终点所在的节点(选区中最后一个子节点的父节点).
- `endOffset`:范围终点在`endContainer`中的偏移量(不包括).
- `commonAncestorContainer`:文档中以`startContainer`和`endContainer`为后代的最深的节点.

这些属性会在范围被放到文档中特定位置时获得对应的值.

### 简单选择
`selectNode()`或`selectNodeContents()`方法都接收一个节点作为参数,并将该节点的信息添加到调用它的范围.`selectNode()`方法选择整个节点,包括其后代节点,而`selectNodeContents()`只选择节点的后代:
````HTML
<!DOCTYPE html>
<html>
    <body>
        <p id="p1"><b>Hello</b> world!</p>
    </body>
</html>
````
````JS
let range1 = document.createRange(),
    range2 = document.createRange(),
    p1 = document.getElementById("p1");
range1.selectNode(p1);          // 选择 <p id="p1"><b>Hello</b> world!</p>
range2.selectNodeContents(p1);  // 选择 <b>Hello</b> world!
````

调用`selectNode()`时,`startContainer`,`endContainer`和`commonAncestorContainer`都等于传入节点的父节点(上例中,为`document.body`).`startOffset`属性等于传入节点在其父节点`childNodes`集合中的索引(上例中,`startOffset`等于`1`,因为`<p>`元素前存在一个文本节点).`endOffset`等于`startOffset`加`1`(左闭右开).

在调用`selectNodeContents()`时,`startContainer`,`endContainer`和`commonAncestorContainer`属性就是传入的节点(在这个例子中是`<p>`元素).`startOffset`属性始终为`0`,而`endOffset`等于传入节点的子节点数量(上例中为`2`).

还可以在范围上调用相应的方法,实现对范围中选区的更精细的控制:
- `setStartBefore(refNode)`:把范围的起点设置为`refNode`,从而让`refNode`成为选区的第一个子节点.`startContainer`属性被设置到`refNode.parentNode`,而`startOffset`属性被设置为`refNode`在其父节点`childNodes`集合中的索引.
- `setStartAfter(refNode)`:把范围的起点设置到`refNode`之后,从而将`refNode`排除在选区之外,让其下一个同胞节点成为选区的第一个子节点.`startContainer`属性被设置为`refNode.parentNode`,`startOffset`属性被设置为`refNode`在其父节点`childNodes`集合中的索引加1.
- `setEndBefore(refNode)`:把范围的终点设置到`refNode`之前,从而将`refNode`排除在选区之外,让其上一个同胞节点成为选区的最后一个子节点.`endContainer`属性被设置为`refNode.parentNode`,`endOffset`属性被设置为`refNode`在其父节点`childNodes`集合中的索引.
- `setEndAfter(refNode)`:把范围的终点设置为`refNode`,从而让`refNode`成为选区的最后一个子节点.`endContainer`属性被设置为`refNode.parentNode`,`endOffset`属性被设置为`refNode`在其父节点`childNodes`集合中的索引加1.

为了实现复杂的选区,也可以直接修改`startContainer`,`startOffset`,`endContainer`,`endOffset`的值.

### 复杂选择
`setStart()`和`setEnd()`方法都接收两个参数:参照节点和偏移量.对于`setStart()`来说,参照节点会成为`startContainer`,而偏移量会赋值给`startOffset`.对`setEnd()`而言,参照节点会成为`endContainer`,而偏移量会赋值给`endOffset`.

假设想要选择上例中`"Hello"`中`"llo"`到`" world!"`中的`" wo"`的部分.则可以这么设置:
````JS
let p1 = document.getElementById("p1");
    helloNode = p1.firstChild.firstChild,
    worldNode = p1.lastChild;
let range = document.createRange();
range.setStart(helloNode, 2);
range.setEnd(worldNode, 3);
````
因为`helloNode`和`worldNode`是文本节点,所以它们会成为范围内的`startContainer`和`endContainer`,这样`startOffset`和`endOffset`实际上表示每个节点中文字字符的位置,而不是子节点的位置.而`commonAncestorContainer`是`<p>`元素,即包含这两个节点的第一个祖先节点.

### 操作范围
创建范围之后,浏览器会在内部创建一个文档片段节点,用于包含范围选区中的节点.为操作选区范围的内容,选区中的内容必须格式完好.上例中,`"Hello"`中`"llo"`到`" world!"`中的`" wo"`的部分的范围不是完好的DOM结构,因为范围的起点和重点都在文本节点内部,所以无法在DOM中表示.不过,范围能够确定缺失的开始标签和结束标签,从而可以重构出有效的DOM结构,以便后续操作.

重构是后台发生的,不会影响实际HTML,除非在删除操作之后无法形成正确的HTML结构.

例如上例在后台会被修改成这样:
````HTML
<p><b>He</b><b>llo</b> world!<p>
````
其中,单独的`" world!"`文本节点被拆成了`" wo"`和`"rld!"`

`deleteContents()`方法会从文档中删除范围包含的节点:`range.deleteContents()`.

`extractContents()`会从文档中移除范围选区,并将其放入`DocumentFragment`对象并返回.

`cloneContents()`方法创建一个副本,并将其放入`DocumentFragment`对象并返回.

### 范围插入
`insertNode()`方法可以在选区的开始位置插入一个节点.插入的节点也会被`Range`对象包含在内.  
例如:
````JS
let p1 = document.getElementById("p1");
    helloNode = p1.firstChild.firstChild,
    worldNode = p1.lastChild;
let range = document.createRange();
range.setStart(helloNode, 2);
range.setEnd(worldNode, 3);

let span = document.createElement("span");
span.style.color = "red";
span.appendChild(document.createTextNode("Inserted text"));
range.insertNode(span);
````
此时,HTML代码会变成:
````HTML
<p id="p1"><b>He<span style="color: red;">Inserted text</span>llo</b> world!</p>
````

`surroundContents()`方法将`Range`的内容移动到一个新节点作为其最后一个子节点,并将该新节点放置在范围所指定的起始位置.  
例如:
````JS
let p1 = document.getElementById("p1");
    helloNode = p1.firstChild.firstChild;
let range = document.createRange();
range.selectNode(helloNode);
let span = document.createElement("span");
span.style.backgroundColor = "yellow";
range.surroundContents(span);
````
此操作会得到如下HTML:
````HTML
<p id="p1"><b><span style="background-color: yellow;">Hello</span></b> world!</p>
````

如果范围内不包含完整的DOM结构,则会失败并抛出错误.如果给定的节点是`Document`,`DocumentType`或`DocumentFragment`类型,也会导致抛出错误.

### 范围折叠
如果范围并没有选择文档的任何部分,则称为折叠.折叠类似于鼠标光标,起点和终点相同.

使用`collapse()`方法可以折叠范围.这个方法接收一个参数:布尔值,表示折叠到范围的哪一端.`true`表示折叠到起点,`false`表示折叠到终点.

`collapsed`属性返回一个布尔值,表示范围是否已经被折叠.

测试范围是否被折叠,能够帮助确定范围中的两个节点是否相邻:
````HTML
<p id="p1">Paragraph 1</p><p id="p2">Paragraph 2</p>
````
````JS
let p1 = document.getElementById("p1"),
    p2 = document.getElementById("p2"),
    range = document.createRange();
range.setStartAfter(p1);
range.setEndBefore(p2);
console.log(range.collapsed);   // true
````

### 范围比较
如果有多个范围,则可以使用`compareBoundaryPoints()`方法确定范围之间是否存在公共的边界(起点或终点).这个方法接收两个参数:要比较的范围和一个常量值,表示比较的方式.这个常量参数包括:
- `Range.START_TO_START`(0):比较两个范围的起点
- `Range.START_TO_END`(1):比较第一个范围的起点和第二个范围的终点
- `Range.END_TO_END`(2):比较两个范围的终点
- `Range.END_TO_START`(3):比较第一个范围的终点和第二个范围的起点

`compareBoundaryPoints()`方法在第一个范围的边界点位于第二个范围的边界点前时返回`-1`,在两个范围的边界点相等时返回`0`,在第一个范围的边界点位于第二个范围的边界点之后返回`1`.

### 复制范围
调用范围的`cloneRange()`方法可以复制范围.这个方法会创建调用它的范围的副本.新属性包含与原始范围一样的属性,修改其边界点不会影响原始范围.

### 清理
在使用完范围之后,最好调用`detach()`方法把范围从创建它的文档中剥离.调用`detach()`之后,就可以放心解除对范围的引用,以便垃圾回收程序释放它所占用的内存:
````JS
range.detach();
range = null;
````
剥离之后的范围就不能再使用了.

# 事件
JS与HTML的交互是通过*事件*实现的,事件代表文档或浏览器窗口中某个有意义的时刻.可以使用仅再事件发生时执行的*监视器*(也叫处理程序)订阅事件.在传统软件工程领域,这个模型叫"观察者模式",其能够做到页面行为与页面展示的分离.

即使所有主流浏览器都实现了`DOM2 Events`,规范也没有涵盖所有的事件类型.BOM也支持事件,但缺乏文档.而DOM3新增的事件API又让这些问题复杂化了.

以下所有IE的专有事件都指的是IE8及以下版本的事件系统.

可在[MDN-Element](https://developer.mozilla.org/zh-CN/docs/Web/API/Element)的事件栏找到元素支持的事件.

可在[MDN-Document](https://developer.mozilla.org/zh-CN/docs/Web/API/Document)的事件栏找到元素支持的事件.

## 事件流
事件流描述了页面接收事件的顺序.例如,一个按钮被点击,实际上不光按钮,其他包含按钮的容器也会收到事件.

### 事件冒泡
IE(IE8前)的事件流被称为事件冒泡,因为事件被定义为从最具体的元素(文档树中最深的节点)开始触发,然后向上传播至没有那么具体的元素.

所有现代浏览器都支持事件冒泡,只是在实现方式上会有一些变化.

### 事件捕获
`Netscape Communicator`提出了名为事件捕获的事件流.事件捕获的意思是最不具体的节点应该最先收到事件,而最具体的节点应该最后收到事件.事件捕获实际上是为了在事件到达最终目标前拦截事件.

事件捕获得到了所有现代浏览器的支持.实际上,所有浏览器都是从`window`对象开始捕获事件,而`DOM2 Events`规范规定的是从`document`开始.

由于旧版本浏览器不支持,因此实际当中几乎不会使用事件捕获.

### DOM事件流
`DOM2 Events`规范规定事件流分为3个阶段:事件捕获,到达目标和事件冒泡.事件捕获最先发生,为提前拦截事件提供了可能.然后,实际的目标元素接收到事件(通常也被认为是冒泡阶段的一部分).最后一个阶段是冒泡,最迟要在这个阶段相应事件.

![DOM事件流](img/get_start/DOMEvent.png)

注意:在捕获阶段实际的目标(上图为`<div>`)不会接收到事件.这是因为捕获阶段从`document`到`<html>`再到`<body>`就结束了.在`<div>`元素上触发事件是下一阶段的事.

大多数支持DOM事件流的浏览器实现了一个拓展,虽然`DOM2 Events`规范明确捕获阶段不命中事件目标,但现代浏览器都会在捕获阶段在事件目标上触发事件.最终结果是在事件目标上有两个机会来处理事件.

注意:所有现代浏览器都支持DOM事件流,只有`IE8`及更早版本不支持.

## 事件处理程序
事件意味着用户或浏览器执行的某种动作.比如,单击,加载,鼠标悬停.为相应事件而调用的函数被称为*事件处理程序*(或*事件监听器*).事件处理程序的名字以`"on"`开头,因此`click`事件的处理程序叫作`onclick`,而`load`事件的处理程序叫做`onload`.有很多方式可以指定事件处理程序.

### HTML事件处理程序
特定元素支持的每个事件都可以使用事件处理程序的名字以HTML属性的形式来指定.此时属性的值必须是能够执行的JS代码:
````HTML
<input type="button" value="Click Me" onclick="console.log('Clicked')">
````
转义字符在内嵌于HTML属性的JS代码中并非总是有效,使用字符实体属于语法错误:
````HTML
<input type="button" value="Click Me" onclick="console.log(&quto;Clicked&quto;)">   <!-- ERROR -->
<input type="button" value="Click Me" onclick="console.log('Clicked\"')">           <!-- ERROR -->
````
内嵌的代码允许访问先前在全局作用域中的一切:
````HTML
<input type="button" value="Click Me" onclick="showMessage();">
<script>
    function showMessage() {
        console.log("Hello world!")
    }
</script>
<!-- 注意,由于此时是先加载的HTML按钮,后加载的函数定义,因此可能会导致用户在未加载完时点击按钮导致发生错误.
 可以使用try/catch块封装以便在这种情况下静默失败 -->
````
以这种方法指定的事件处理程序会创建一个函数来封装属性的值,因此以该方式定义的变量或函数均不可在外部使用.这个函数包含一个特殊的局部变量`event`,其中保存的就是`event`对象.
````HTML
<input type="button" value="Click Me" onclick="console.log(event.type)">    <!-- 输出"click" -->
````
在这个函数中,`this`值相当于事件的目标元素:
````HTML
<input type="button" value="Click Me" onclick="console.log(this.value)">    <!-- 输出"Click Me" -->
````
这个函数的作用域链被扩展了.在这个函数中,`document`和元素自身的成员都可以被当成局部变量来访问,类似于使用如下方法来包装:
````JS
function() {
    with(document) {
        with(this) {
            // ...
        }
    }
}
````
因此,可以这样访问属性:
````HTML
<input type="button" value="Click Me" onclick="console.log(value)"> <!-- 输出"Click Me" -->
````
如果这个元素是一个表单输入框,则作用域链中还会包含表单元素,类似于使用如下方法来包装:
````JS
function() {
    with(document) {
        with(this.form) {
            with(this) {
                // ...
            }
        }
    }
}
````

### DOM0事件处理程序
JS中指定事件处理程序的传统方法是把一个函数赋值给(DOM元素的)一个事件处理程序属性.

每个元素(包括`window`和`document`)都有通常小写的事件处理程序属性,比如`onclick`.只要把这个属性赋值为一个函数即可:
````JS
let btn = document.getElementById("myBtn");
btn.onclick = function() {
    console.log("Clicked");
}
````

只有在代码运行到此处时,才会给事件处理程序赋值.因此可能出现用户点击按钮没有反应的情况.

向这样使用DOM0方式为事件处理程序赋值时,所赋函数被视为元素的方法.因此,事件处理程序会在元素的作用域中运行,即`this`等于元素:
````JS
let btn = document.getElementById("myBtn");
btn.onclick = function() {
    console.log(this.id);   // "myBtn"
}
````

以这种方式添加事件处理程序是注册在事件流的冒泡阶段的.

将事件处理程序属性的值设置为`null`,可以移除通过DOM0方式添加的事件处理程序.

*注:如果事件处理程序是在HTML中指定的,则`onclick`属性的值是一个包装相应HTML事件处理程序属性值的函数.这些事件处理程序也可以通过在JS中将相应属性设置为`null`来移除.*

### DOM2事件处理程序
`DOM2 Events`为事件处理程序的赋值和移除定义浏览两个方法:`addEventListener()`和`removeEventListener()`.这两个方法暴露在所有DOM节点上,它们接收3个参数:事件名,事件处理程序和一个布尔值,`true`表示在捕获阶段调用事件处理程序,`false`(默认值)表示在冒泡阶段调用事件处理程序.

**注:事实上`addEventListener()`,`removeEventListener`和`dispatchEvent()`都是`EventTarget`中定义的方法,所有DOM节点都继承了该类.**

例如:
````JS
let btn = document.getElementById("myBtn");
btn.addEventListener("click", function() {
    console.log(this.id);   // myBtn
}, false);
````
由于箭头函数的特性,其中的`this`指的是定义时的上下文,因此:
````JS
let btn = document.getElementById("myBtn");
btn.addEventListener("click", () => {
    console.log(this.id);   // undefined
}, false);
````

`DOM2`方式的主要优势是可以添加多个事件处理程序:
````JS
let btn = document.getElementById("myBtn");
btn.addEventListener("click", function() {
    console.log(this.id);   // myBtn
}, false);
btn.addEventListener("click", function() {
    console.log("Hello world!");    // Hello world!
}, false);
````

事件处理程序会以添加顺序来触发.

通过`addEventListener()`添加的事件处理程序只能使用`removeEventListener()`并传入与添加时同样的参数来移除,这意味着使用`addEventListener()`添加的匿名函数无法移除:
````JS
let btn = document.getElementById("myBtn");
btn.addEventListener("click", function() {
    console.log(this.id);   // myBtn
}, false);
btn.removeEventListener("click", function() {
    console.log(this.id);
}, false);  // 没有作用!
````

必须保证两者指向的是同一个函数:
````JS
let btn = document.getElementById("myBtn");
let handler = function() {
    console.log(this.id);
};
btn.addEventListener("click", handler, false);
btn.removeEventListener("click", handler, false);   // 有效果
````

### IE事件处理程序
IE使用`attachEvent()`和`detachEvent()`来为事件处理程序的赋值和移除.这两个方法接收两个参数:事件处理程序的名字和事件处理函数.因为`IE8`及更早的版本只支持事件冒泡,所以其添加到冒泡阶段.此外,事件名称应当加上`"on"`,例如`"onclick"`而非`"click"`.

IE中,事件处理程序是在全局作用域中运行的,而非作为元素的作用域中,因此,`this`为`window`.此外,事件处理函数会以添加顺序*反向*触发.

### 跨浏览器事件处理程序
以下`EventUtil`能够保证在所有浏览器中都能进行事件处理,尽管无法保证一致性问题:
````JS
var EventUtil = {
    addHandler: function(element, type, handler) {
        if (element.addEventListener) {
            element.addEventListener(type, hander, false);
        } else if (element.attachEvent) {
            element.attachEvent("on" + type, handler);
        } else {
            element["on" + type] = handler;
        }
    },
    removeHandler: function(element, type, handler) {
        if (element.removeEventListener) {
            element.removeEventListener(type, handler, false);
        } else if (element.detachEvent) {
            element.detachEvent("on" + type, handler);
        } else {
            element["on" + type] = null;
        }
    }
};
````

不过IE已经死了,所以其实使用DOM2的事件处理程序问题不大.

## 事件(Event)对象
在DOM中发生事件时,所有相关信息都会被收集并存储在一个名为`event`的对象中.这个对象包含了一些基本信息,比如导致事件的元素,发生的事件类型,以及可能与特定事件相关的任何其他数据.所有浏览器都支持这个`event`对象,尽管支持的方式不同.

### DOM事件对象
在`DOM`合规的浏览器中,`event`对象时传给事件处理程序的唯一参数.不管以哪种方式(DOM0或DOM2)指定事件处理程序,都会传入这个`event`对象:
````JS
let btn = document.getElementById("myBtn");
btn.onclick = function(thisShouldBeTheEventObject) {
    console.log(thisShouldBeTheEventObject.type);   // "click"
}
btn.addEventListener("click", (event) => {
    console.log(event.type);    // "click"
}, false);
````

通过HTML属性指定的事件处理程序中,同样可以使用变量`event`(但不能够自己命名)引用事件对象:
````HTML
<input type="button" value="Click Me" onclick="console.log(event.type)">
````

事件对象包含与特定事件相关的属性和方法.不同的事件生成的事件对象也会包含不同的属性和方法.不过,所有事件对象都会包含以下公共属性和方法:
- `bubbles`:布尔值.只读.表示事件是否冒泡.
- `cancelable`:布尔值.只读.表示是否可以取消事件的默认行为.
- `currentTarget`:元素.只读.当前事件处理程序所在的元素.
- `defaultPrevented`:布尔值.只读.`true`表示已经调用`preventDefault()`方法.(`DOM3 Events`中新增)
- `detail`*(UIEvent)*:整数.只读.事件相关的其他信息.
- `eventPhase`:整数.只读.表示调用事件处理程序的阶段:`1`代表捕获阶段,`2`代表到达目标,`3`代表冒泡阶段.
- `preventDefault()`:函数.只读.用于取消事件的默认行为.只有`cancelable`为`true`才可以调用这个方法.
- `stopImmediatePropagation()`:函数.只读.用于取消所有后续事件捕获或事件冒泡,并阻止调用任何后续事件处理程序.(`DOM3 Events`中新增)
- `stopPropagation()`:函数.只读.用于取消所有后续事件捕获或事件冒泡.只有`bubbles`为`true`才可以调用这个方法.
- `target`:元素.只读.事件目标.
- `isTrusted`:布尔值.只读.`true`表示事件是由浏览器生成的.`false`表示事件是开发者通过JS创建的.(`DOM3 Events`中新增)
- `type`:字符串.只读.被触发的事件类型.
- `view`*(UIEvent)*:`AbstractView`.只读.与事件相关的抽象视图.等于事件所发生的`window`对象.

在事件处理程序内部,非箭头函数的`this`对象始终等于`currentTarget`的值,而`target`只包含事件的实际目标:
````JS
let btn = document.getElementById("myBtn");
document.body.onclick = function(event) {
    console.log(event.currentTarget === this);  // true
    console.log(event.target === btn);          // true
    console.log(event.target === event.currentTarget);  // false
}
````

上述事件处理程序中,`btn`本身没有注册事件处理程序,但是由于`click`事件冒泡到`document.body`,从而触发了在它上面注册的处理程序.

`type`属性在一个处理程序处理多个事件时很有用.例如:
````JS
let btn = document.getElementById("myBtn");
let handler = function(event) {
    switch(event.type) {
        case "click":
            console.log("Clicked");
            break;
        case "mouseover":
            event.target.style.backgroundColor = "red";
            break;
        case "mouseout":
            event.target.style.backgroundColor = "";
            break;
    }
};
btn.onclick = handler;
btn.onmouseover = handler;
btn.onmouseout = handler;
````

`preventDefault()`方法用于阻止特定事件的默认动作.比如,链接的默认行为就是在被单击时导航到`href`属性指定的URL.如果想阻止这个导航行为,可以在`onclick`事件处理程序中取消:
````JS
let link = document.getElementById("myLink");
link.onclick = function(event) {
    event.preventDefault();
};
````

可以通过`preventDefault()`取消默认行为的事件,其事件对象的`cancelable`属性都会设置为`true`.

`stopPropagation()`方法用于立即阻止事件流在DOM结构中传播,取消后续事件捕获或冒泡(实际上就是阻止冒泡,因为只有在冒泡阶段才能调用).例如,直接添加到按钮的事件处理程序中调用`stopPropagation()`,可以阻止`document.body`上注册的事件处理程序执行:
````JS
let btn = document.getElementById("myBtn");
btn.onclick = function(event) {
    console.log("Clicked");
    event.stopPropagation();
};
document.body.onclick = function(event) {
    console.log("Body clicked");    // 不会执行
}
````

`eventPhase`属性用于确定事件流当前所处的阶段:
````JS
let btn = document.getElementById("myBtn");
btn.onclick = function(event) {
    console.log(event.eventPhase);  // 2
}
document.body.addEventListener("click", (event) => {
    console.log(event.eventPhase);  // 1
}, true);
document.body.addEventListener("click", (event) => {
    console.log(event.eventPhase);  // 3
}, false);
````

*注:`event`对象只在事件处理程序执行期间存在,一旦执行完毕,就会被销毁.*

### IE事件对象
IE事件对象可以基于事件处理程序被指定的方式以不同方式来访问.如果事件处理程序是使用`DOM0`方式指定的,则`event`对象只是`window`对象的一个属性.如果事件处理程序是使用`attachEvent()`指定的,则`event`对象会作为唯一的参数传给处理函数.使用`attachEvent()`时,`event`对象仍然是`window`对象的属性,只是处于方便也将其作为参数传入.

如果是`HTML`属性方式指定的事件处理程序,则`event`对象同样可以通过变量`event`访问.

IE事件对象也包含与其创建的特定事件相关的属性和方法,但所有的IE事件对象都会包含下表所列的公共属性和方法:
- `cancelBubble`:布尔值.读/写.默认为`false`,设置为`true`可以取消冒泡(与`stopPropagation()`方法相同)
- `returnValue`:布尔值.读/写.默认为`true`,设置为`false`可以取消事件默认行为(与`preventDefault()`方法相同)
- `srcElement`:元素.只读.事件目标(与`target`属性相同)
- `type`:字符串.只读.触发的事件类型

IE中,以DOM0方式指定的事件处理程序中,`this`当前元素,而在`attachEvent()`设置的情况下,`this`是`window`对象.

### 跨浏览器事件对象
基于前面的`EventUtil`对象,可以像这样再添加一些方法,以实现让两种事件模型之间的映射称为可能:
````JS
var EventUtil = {
    addHandler: function(element, type, handler) {
        // (见上文)
    },
    getEvent: function(event) {
        return event ? event : window.event;
    },
    getTarget: function(event) {
        return event.target || event.srcElement;
    },
    PreventDefault: function(event) {
        if (event.preventDefault) {
            event.preventDefault();
        } else {
            event.returnValue = false;
        }
    },
    removeHandler: function(element, type, handler) {
        // (见上文)
    },
    stopPropagation: function(event) {
        if (event.stopPropagation) {
            event.stopPropagation();
        } else {
            event.cancelBubble = true;
        }
    }
};
````

## 事件类型
所发生事件的类型决定了事件对象中会保存什么信息.`DOM3 Events`定义了如下事件类型:
- `UIEvent`(用户界面事件):涉及与BOM交互的通用浏览器事件
- `FocusEvent`(焦点事件):在元素获得和失去焦点时触发
- `MouseEvent`(鼠标事件):使用鼠标在页面上执行某些操作时触发
- `WheelEvent`(滚轮事件):使用鼠标滚轮(或类似设备)时触发
- `InputEvent`(输入事件)(**已废弃**):向文档中输入文本时触发
- `KeyboardEvent`(键盘事件):使用键盘在页面上执行某些操作时触发
- `CompositionEvent`(合成事件):在使用某种IME(Input Method Editor,输入法编辑器)输入字符时触发

除了这些事件类型之外,HTML5还定义了另一组事件,而浏览器通常在`DOM`和`BOM`上实现专有事件.这些专有事件并没有统一规范,因此不同浏览器会有所不同.

`DOM3 Events`在`DOM2 Events`基础上重新定义了事件,并增加了新的事件类型.所有主流浏览器都支持`DOM2 Events`和`DOM3 Events`.

### 用户界面事件(UIEvent)
用户界面事件或UI事件不一定跟用户操作有关.这类事件在DOM规范出现之前就已经以某种形式存在了,保留它们是为了向后兼容.UI事件主要有以下几种:
- `DOMActivate`**(已废弃)**:元素被用户通过鼠标或键盘操作激活时触发(比`click`或`keydown`更通用).此事件已废弃,因为浏览器的实现之间存在差异.
- `load`:在`window`上当页面加载完成后触发,在窗套(`<frameset>`)上当所有窗格(`<frame>`)都加载完成后触发,在`<img>`元素上当图片加载完成后触发,在`<object>`元素上当相应对象加载完成后触发.
- `unload`**(已弃用)**:在`window`上当页面完全卸载后触发,在窗套上当所有窗格都卸载完成后触发,在`<object>`元素上当对应对象卸载完成后触发.
- `abort`:在`<object>`元素上当相应对象加载完成前被用户提前终止下载时触发.
- `error`:在`window`上当JS报错时触发,在`<img>`元素上当无法加载指定图片时触发,在`<object>`元素上当无法加载相应对象时触发,在窗套上当一个或多个窗格无法加载时触发.
- `select`:在文本框(`<input>`或`textarea`)上当用户选择了一个或多个字符时触发.
- `resize`:在`window`或窗格上当窗口或窗格被缩放时触发.
- `scroll`:当用户滚动包含滚动条的元素时在元素上触发.`<body>`元素包含已加载页面的滚动条.

除了`DOMActivate`,这些事件在`DOM2 Events`中都被归为`HTML Events`.

#### load事件
`load`事件在`window`上当整个页面加载完成后触发.
````JS
window.addEventListener("load", (event) => {
    console.log("Loaded!");     // Loaded!
    console.log(event.target);  // #document
    console.log(event.currentTarget);   // Window { ... }
});
````
上面使用了`addEventListener()`方法来指定事件处理程序.虽然是在`window`对象上设置的,但DOM合规的浏览器中,`event.target`会被设置为`document`.

如果要在HTML上指定`window`对象的`load`事件处理程序,则可以给`<body>`元素上`onload`属性赋值:
````HTML
<!DOCTYPE html>
<html>
<head>
    <!-- ... -->
</head>
<body onload="console.log('Loaded!')">
    <!-- ... -->
</body>
</html>
````

一般来说,任何在`window`上发生的事件,都可以通过给`<body>`元素上对应的属性赋值来指定,这是因为HTML中没有`window`元素.这实际上是为了保证向后兼容的一个策略,但在所有浏览器中都能得到很好的支持.实际开发中要尽量使用JS方式.

*注:根据`DOM2 Events`,`load`事件应该在`document`而非`window`上触发.(不过MDN上也是给`window`设置`load`事件的)*

图片上也会触发`load`事件,包括DOM中的图片和非DOM中的图片.可以在HTML中直接给`<img>`元素的`onload`属性指定事件处理程序.

如果要用JS创建一个新的`<img>`元素,并给这个元素指定一个加载完成后执行的事件处理程序.需要在赋值`src`属性之前指定事件处理程序:
````JS
window.addEventListener("load", () => { // 由于向DOM中添加新元素,所以必须确保页面已经加载完成
    let image = document.createElement("img");
    image.addEventListener("load", (event) => { // 需要事先添加事件处理程序,防止错过
        console.log(event.target.src);
    });
    document.body.appendChild(image);
    image.src = "smile.gif";
});
````

还有一些元素也支持`load`事件,但这是**非标准的**.
- `<script>`元素会在JS文件加载完成后触发`load`事件,从而可以动态检测.
- `<link>`元素会触发`load`事件,因而支持动态检测样式表是否加载完成.

#### unload事件(已弃用)

**已弃用**

`unload`事件会在文档卸载完成后触发.`unload`事件一般是在从一个页面导航到另一个页面时触发,最常用于清理引用,以避免内存泄漏.

同样可以在`window`对象上使用`addEventListener()`并传入`"unload"`来指定事件处理程序.也可以给`<body>`元素添加`onunload`属性.

事件生成的`event`对象在DOM合规的浏览器中只有`target`属性,且值为`document`.

因为`unload`事件是在页面卸载完成后触发的,所以不能使用页面加载后才有的对象.此时要访问DOM或修改页面外观都会导致错误.

*注:根据`DOM2 Events`,`unload`事件应该在`<body>`而非`window`上触发.*

#### resize事件
当浏览器窗口被缩放到新高度或宽度时,会触发`resize`事件.这个事件在`window`上触发,因此可以通过JS在`window`上使用`addEventListener()`并传入`"resize"`,或者为`<body>`元素添加`onresize`属性指定事件处理程序.

生成的`event`对象的`target`属性在DOM合规的浏览器中是`document`.

用户在缩放浏览器的过程中会持续触发`resize`事件.应当避免在这个事件处理程序中执行过多计算或对其限流.

*注:浏览器窗口在最大化和最小化时也会触发`resize`事件.*

#### scroll事件
当文档视图或元素滚动后,`scroll`事件就会触发.

可滚动的元素可以查看其`scrollTop`和`scrollLeft`属性来查看两个方向上滚动的距离.

用户在滚动时会持续触发`scroll`事件.应当避免在这个事件处理程序中执行过多的计算或对其限流.

详见:
- [MDN-Document：scroll 事件](https://developer.mozilla.org/zh-CN/docs/Web/API/Document/scroll_event)
- [MDN-GlobalEventHandlers.onscroll](https://developer.mozilla.org/zh-CN/docs/Web/API/Element/scroll_event)

示例:
````HTML
<body>
    <textarea style="overflow: scroll; font-size: 50px" id="myText">222222222</textarea>
</body>
````
````JS
let textArea = document.getElementById("myText");
textArea.addEventListener("scroll", (event) => {
    console.log("Scroll!");
    console.log(event.target.scrollTop);
    console.log(event.target.scrollLeft);
});
````

### 焦点事件(FocusEvent)
焦点事件在页面元素获得或失去焦点时触发.这些事件可以与`document.hasFocus()`和`document.activeElement`一起为开发者提供用户在页面中导航的信息.焦点事件有以下6种:
- `blur`:当元素失去焦点时触发.这个事件不冒泡.
- `DOMFocusIn`**(已弃用)**
- `DOMFocusOut`**(已弃用)**
- `focus`:当元素获得焦点时触发.这个事件不冒泡.
- `focusin`:当元素获得焦点时触发.这个事件相比`focus`支持冒泡.
- `focusout`:当元素失去焦点时触发.这个事件相比`blur`支持冒泡.

当焦点从页面中的一个元素移到另一个元素上时,会依次发生如下事件:
- `focusout`在失去焦点的元素上触发
- `focusin`在获得焦点的元素上触发
- `blur`在失去焦点的元素上触发
- `DOMFocusOut`在失去焦点的元素上触发
- `focus`在获得焦点的元素上触发
- `DOMFocusIn`在获得焦点的元素上触发

### 鼠标(MouseEvent)和滚轮事件(WheelEvent)
*鼠标事件*是Web开发中最常用的一组事件.`DOM3 Events`定义了9种鼠标事件:
- `click`:在用户单击鼠标主键(通常是左键)或按键盘回车键时触发.这主要是基于无障碍的考虑,让键盘和鼠标都可以触发`onclick`事件处理程序.
- `dblclick`:在用户双击鼠标主键(通常是左键)时触发.
- `mousedown`:在用户按下任意鼠标键时触发.这个事件不能通过键盘触发.
- `mouseenter`:在用户把鼠标光标从元素外部移到元素内部时触发.这个事件不冒泡,也不会在光标经过后代元素时触发.
- `mouseleave`:在用户把鼠标光标从元素内部移到元素外部时触发.这个事件不冒泡,也不会再光标经过后代元素时触发.
- `mousemove`:在鼠标光标在元素上移到时反复触发.这个元素不能通过键盘触发.
- `mouseout`:在用户把鼠标光标从一个元素移到另一个元素上时触发.移到的元素可以是原始元素的外部元素,也可以是原始元素的子元素.这个事件不能通过键盘触发.
- `mouseover`:在用户把鼠标光标从元素外部移到元素内部时触发.这个事件不能通过键盘触发.
- `mouseup`:在用户释放鼠标键时触发.这个事件不能通过键盘触发.

页面中的所有元素都支持鼠标事件,除了`mouseenter`和`mouseleave`,所有鼠标事件都会冒泡,都可以被取消,而这会影响浏览器的默认行为,也会影响其他事件.

一个双击事件永远以如下顺序触发:
1. `mousedown`
2. `mouseup`
3. `click`
4. `mousedown`
5. `mouseup`
6. `click`
7. `dblclick`

不在同一个元素上触发`mouseup`或`mousedown`或其一事件被取消,那么`click`事件就不会触发.两个连续的`click`事件中任意一个不触发则`dblclick`不会被触发.

鼠标事件还有一个名为滚轮事件的子类别.滚轮事件只有一个事件`mousewheel`,反映的是鼠标滚轮或带滚轮的类似设备上滚轮的交互.

#### 客户端坐标
鼠标事件都是在浏览器视口中的某个位置上发生的.这些信息被保存在`event`对象的`clientX`和`clientY`属性中.这两个属性表示事件发生时鼠标光标在视口中的坐标.

![客户端坐标](img/get_start/clientPosition.png)

客户端坐标不考虑页面滚动,因此这两个值并不代表鼠标在页面上的位置.

#### 页面坐标
页面坐标是事件发生时,鼠标光标在页面上的坐标,通过`event`对象的`pageX`和`pageY`可以获取.这两个属性表示鼠标光标在页面上的位置,因此可以反映的是光标到页面而非视口左边与上边的距离.

`pageX`和`pageY`也可以通过`clientX`和`clientY`以及`document.document.Element`的`scrollLeft`和`scrollTop`属性计算获得.(用于IE8及以前的版本)

#### 屏幕坐标

屏幕事件不仅是在浏览器窗口中发生的,也是在整个屏幕上发生的.可以通过`event`对象的`screenX`和`screenY`属性获取鼠标光标在屏幕上的坐标.

![屏幕坐标](img/get_start/screenPosition.png)

#### 修饰键
有时候要确定用户想实现的操作,还要考虑键盘按键的状态.键盘上的修饰键`Shift`,`Ctrl`,`Alt`,`Meta`经常用户修改鼠标事件的行为.DOM规定了4个属性来表示这几个修饰键的状态:`shiftKey`,`ctrlKey`,`altKey`和`metaKey`.这些属性会在各自对应的修饰键被按下时包含布尔值`true`,没有被按下时包含`false`.在鼠标事件发生的,可以通过这几个属性来检测修饰键是否被按下:
````JS
let div = document.getElementById("myDiv");
div.addEventListener("click", (event) => {
    let keys = new Array();
    if (event.shiftKey) {
        keys.push("shift");
    }
    if (event.ctrlKey) {
        keys.push("ctrl");
    }
    if (event.altKey) {
        keys.push("alt");
    }
    if (event.metaKey) {
        keys.push("meta");
    }
    console.log("Keys: " + keys.join(","));
});
````

*注:IE8及更早版本不支持`metaKey`属性.*

#### 相关元素
对`mouseover`和`mouseout`事件而言,这两个事件都涉及从一个元素边界之内把光标移到另一个元素的边界之内.对`mouseover`事件来说,事件的主要目标时获得光标的元素,相关元素时失去光标的元素.类似的,对`mouseout`事件来说,事件的主要目标是失去光标的元素,而相关元素是获得光标的元素.

DOM通过`event`对象的`relatedTarget`属性提供了相关元素的信息(指向相关元素的引用).这个属性只有在`mouseover`和`mouseout`事件发生时才包含值,其他所有事件的这个属性的值都是`null`.对于IE8及更早版本,这个属性分别用`fromElement`和`toElement`表示.

#### 鼠标按键
对`mousedown`和`mouseup`事件来说,`event`对象上会有一个`button`属性,表示按下或释放的是哪个按键.DOM为这个`button`属性定义了几个值:
- `0`表示鼠标主键(通常为左键或默认值)(如`document.getElementById('a').click()`这样触发就会是默认值)
- `1`表示鼠标中键
- `2`表示鼠标副键(通常为右键).
- `3`表示鼠标第四个按钮,通常指浏览器后退按钮
- `4`表示鼠标第五个按钮，通常指浏览器的前进按钮

`MouseEvent.button`仅能指示最后一个被按下/释放的鼠标按键.

`MouseEvent.buttons`则可以指示多个鼠标按键被按下的情形.
- `0`:没有按键或者是没有初始化
- `1`:鼠标左键
- `2`:鼠标右键
- `4`:鼠标滚轮或者是中键
- `8`:第四按键(通常是“浏览器后退”按键)
- `16`:第五按键(通常是“浏览器前进”)

其值为按下按键数值之或.

#### 额外事件信息
对于鼠标事件来说,`detail`包含一个数值,表示在给定位置上发生了多少次单击.一次单击相当于在同一像素上发生一次`mousedown`紧跟一次`mouseup`.每次单击会加`1`.如果鼠标在`mousedown`和`mouseup`之间移动了或在单击之间移动了,则`detail`会重置为`0`.

#### mousewheel事件
`mousewheel`事件会在用户使用鼠标滚轮时触发,包括在垂直方向上任意滚动.这个事件会在任何元素上触发,并冒泡到`document`和`window`.`mousewheel`事件的`event`对象包含鼠标事件的所有标准信息,此外还有一个名为`wheelDelta`的新属性.当鼠标滚轮向前滚动时,`wheelDalta`每次值都为`+120`;而当鼠标滚轮向后滚动时,`wheelDelta`每次值都为`-120`.

#### 触摸屏设备
触摸屏通常不支持鼠标操作.在为触摸屏设备开发时,要记住以下事项:
- 不支持`dblclick`事件.双击浏览器窗口可以方法,但没有办法覆盖这个行为.
- 单指点触屏幕上的可点击元素会触发`mousemove`事件.如果操作会导致内容变化,则不会再触发其他事件.如果屏幕上没有变化,则会相继触发`mousedown`,`mouseup`和`click`事件.点触不可点击的元素不会触发事件.可点击元素是指点击时有默认动作的元素(如链接)或制定了`onclick`事件处理程序的元素.
- `mousemove`事件也会触发`mouseover`和`mouseout`事件.
- 双指点触屏幕并滑动导致页面滚动时会触发`mousewheel`和`scroll`事件.

#### 无障碍问题
如果Web应用或网站必须考虑残障人士,特别是使用屏幕阅读器的用户,那么必须小心使用鼠标事件.因为除了`click`事件之外的其他鼠标事件都不能用键盘触发,会严重妨碍盲人或视障用户使用.以下是使用鼠标事件时应该遵循的无障碍建议:
- 使用`click`事件执行代码.
- 不要使用`mouseover`向用户显示新选项.
- 不要使用`dblclick`执行重要的操作.

详见:[WebAIM](https://webaim.org)

### 键盘(KeyboardEvent)与输入事件(TextEvent)
键盘事件是用户操作键盘时触发的.`DOM2 Events`最初定义了键盘事件,但该规范再最终发布前删除了相应内容.`DOM3 Events`为键盘事件提供了一个首先在`IE9`中完全实现的规范.其他浏览器也开始实现该规范,但仍然存在很多遗留问题的实现.

键盘事件包含3个事件:
- `keydown`:用户按下键盘上某个键时触发,而且持续按住会重复触发.
- `keypress`**(已废弃,推荐使用`textInput`事件)**:用户按下键盘上某个键并产生字符时触发,而且会持续按住并重复触发.`Esc`键也会触发这个事件.
- `keyup`:用户释放键盘上某个键时触发.

输入事件只有一个,即`textInput`(**已废弃**).这个事件用于在文本显示给用户之前更方便地截获文本输入.`textInput`会在文本被插入到文本框之前触发.

键盘事件支持与鼠标事件相同的修饰键.`shiftKey`,`ctrlKey`,`altKey`和`metaKey`属性在键盘事件中都是可用的.

#### 键码

**keyCode属性已过时,请使用code属性代替**

对于`keydown`和`keyup`事件,`event`对象的`keyCode`属性中会保存一个键码,对应键盘上特定的一个键.

对于字母和数字键,`keyCode`的值与小写字母和数字的ASCII编码一致,而且跟是否按了`Shift`无关.`A`为`65`,`0`为`48`.

关于键盘上所有非字符键的键码,详见[MDN-keyCode](https://developer.mozilla.org/zh-CN/docs/Web/API/KeyboardEvent/keyCode#%E9%94%AE%E7%A0%81%E5%80%BC)

`KeyboardEvent.code`属性用于替代**过时的**`keyCode`属性,关于其键码,详见:[MDN-code](https://developer.mozilla.org/zh-CN/docs/Web/API/KeyboardEvent/code#code_values)

#### 字符编码

**charCode属性已过时,请使用key属性代替**

`event`对象上支持`charCode`属性 **(已废弃)**,只有在`keypress`事件时这个属性才会被设置值,包含的是按键字符对应的ASCII编码.

`KeyboardEvent.key`属性能够返回按下键的字符串名称,例如`"k"`或`"Shift"`或`"ArrowDown"`,关于具体名称,见[MDN-code](https://developer.mozilla.org/zh-CN/docs/Web/API/KeyboardEvent/code#code_values)

#### DOM3的变化
`DOM3 Events`也支持一个名为`location1`的属性,该属性是一个数值,表示是在哪里按的键.可能的值为:`0`是默认值,`1`是左边(如左边的`Alt`键),`2`是右边(如右边的`Shift`键),`3`是数字键盘,`4`是移动设备(**已废弃**),`5`是游戏手柄(**已废弃**).

`getModifierState()`接收一个参数,这个参数是一个等于`"Shift"`,`"Control"`,`"Alt"`,`"AltGraph"`或`"Meta"`的字符串,表示要检测的修饰符.如果给定的修饰键处于激活状态(键被按住),则方法返回`true`,否则返回`false`.

不过,`event`对象已经通过`shiftKey`,`altKey`,`ctrlKey`和`metaKey`属性暴露了这些信息.

#### textInput事件(已废弃)

*已废弃,请使用`input`,`beforeinput`,`keyup`,`keydown`事件来替代*

`textInput`事件在字符被输入到可编辑区域时触发.`textInput`只在可编辑区域上触发,且只有新字符被插入时才会触发(因此不包含退格键等).

`textInput`在`event`上提供了一个`data`属性,包含要插入的字符.

还有一个名为`inputMethod`的属性,表示向控件中输入文本的手段:
- 0表示浏览器不能确定
- 1表示键盘
- 2表示粘贴
- 3表示拖放
- 4表示IME
- 5表示表单选项
- 6表示手写
- 7表示语音
- 8表示组合方式
- 9表示脚本

### 合成事件(CompositionEvent)
合成事件用于处理通常使用IME输入时的复杂输入序列.IME可以让用户输入物理键盘上没有的字符(输入法).合成事件用于检测和控制这种输入.合成事件有以下3种:
- `compositionstart`:在IME的文本合成系统打开时触发,表示输入即将开始.
- `compositionupdate`:在新字符插入输入字段时触发.
- `compositionend`:在IME的文本合成系统关闭时触发,表示恢复正常键盘输入.

该事件继承了`Event`和`UIEvent`的属性,唯一增加的事件属性就是`data`:
- 在`compositionstart`种,包含正在编辑的文本
- 在`compositionupdate`中,包含要插入的新字符
- 在`compositionend`中,包含本次合成过程中输入的全部内容

### 变化事件(MutationEvent)

**已弃用**

### HTML5事件
这些事件不是DOM规范涵盖的,但在HTML5规范中列出,并在浏览器中有较好的支持.

#### contextmenu事件
`contextmenu`事件属于`MouseEvent`.

Window95最先提出通过单击鼠标右键呼出上下文菜单的概念(Mac上是`Ctrl+单击`),这个功能在Web上也得以实现.`contextmenu`事件专门用于表示何时该显示上下文菜单,从而允许开发者取消默认的上下文菜单并提供自定义菜单.

`contextmenu`事件冒泡,因此只要给`document`指定一个事件处理程序就可以处理页面上所有的同类事件.事件目标是触发操作的元素.这个事件在所有浏览器中都可以取消.

例如:
````HTML
<!DOCTYPE html>
<html>
<head>
        <!-- ... -->
</head>
<body>
    <div id="myDiv" style="height: 100px; width: 100px; background-color: blue;">Right click or Ctrl+click me to get a custom context menu.
        Click anywhere else to get the default context menu.</div>
    <ul id="myMenu" style="position: absolute; visibility: hidden; background-color: silver">
        <li><a href="https://www.example.com">example1</a></li>
        <li><a href="https://www.example.com">example2</a></li>
        <li><a href="https://www.example.com">example3</a></li>
    </ul>
</body>
</html>
````
````JS
window.addEventListener("load", (event) => {
    let div = document.getElementById("myDiv");
    div.addEventListener("contextmenu", (event) => {
        event.preventDefault();
        let menu = document.getElementById("myMenu");
        menu.style.left = event.clientX + "px";
        menu.style.top = event.clientY + "px";
        menu.style.visibility = "visible";
    });
    document.addEventListener("click", (event) => {
        document.getElementById("myMenu").style.visibility = "hidden";
    });
});
````

#### beforeunload事件
`beforeunload`事件会在`window`上触发,用意是给开发者提供阻止页面被卸载的机会.这个事件会在页面即将从浏览器中卸载时触发,如果页面需要继续使用,则可以不被卸载.这个事件不能取消,也不支持冒泡,不然就可以把用户拦在一个页面上.相反,这个事件会向用户显示一个确认框,其中的消息表明浏览器即将卸载页面,并请用户确认是否希望关闭页面.

详见:[MDN-BeforeUnloadEvent](https://developer.mozilla.org/zh-CN/docs/Web/API/BeforeUnloadEvent)

#### DOMContentLoaded事件
`window`的`load`事件会在页面完全加载后触发,而`DOMContentLoaded`事件会在DOM树构建完成后立即触发,而不用等待图片,JS文件,CSS文件或其他资源加载完成.相对于`load`事件`DOMContentLoaded`可以让开发者在外部资源下载的同时就能指定事件处理程序,从而让用户能够更快地与页面交互.

例如:
````JS
document.addEventListener("DOMContentLoaded", (event) => {
  console.log("DOM 完全加载和解析");
});
````

需要给`document`或`window`添加事件处理程序(实际的事件目标是`document`,但会冒泡到`window`).

该事件属于通用的`Event`类型.

如果浏览器不支持`DOMContentLoaded`事件,可以使用:
````JS
setTimeout(() => {
    // "事件处理程序",不保证执行时间
}, 0);
````

#### readystatechange事件
该事件属于`Event`类型

该事件旨在提供文档或元素加载状态的信息,当文档或元素的`readyState`属性发生改变时,就会触发.

支持`readystatechange`事件的对象要求其存在`readyState`属性,该属性具有一个以下列出的可能的字符串值:
- `uninitialized`:对象存在并尚未初始化.
- `loading`:对象正在加载数据.
- `loaded`:对象已经加载完数据.
- `interactive`:对象可以交互,但尚未加载完成.
- `complete`:对象加载完成.

并非所有对象都会经历所有`readyState`阶段,某些对象会跳过某个阶段,但并未说明哪些阶段适用于哪些对象.

`load`和`readystatechange`在实际中并没有严格的先后顺序的关系.

#### pageshow与pagehide事件
*往返缓存*的功能旨在使用浏览器的"前进"和"后退"按钮时加快网页之间的切换.这个缓存(存储在内存中)不仅存储页面的数据,也存储DOM和JS状态.如果页面存储在缓存中,那么导航到这个页面时就不会触发`load`事件.

`pageshow`和`pagehide`事件属于`PageTransitionEvent`,该类(接口)继承自`Event`,多出了示例属性`persisted`.

`pageshow`事件在页面显示时触发,无论是否来自往返缓存.在新加载的页面上,`pageshow`会在`load`事件之后触发;在来自往返缓存的页面上,`pageshow`会在页面状态完全恢复后触发.注意,虽然这个事件的目标是`document`,但事件处理程序必须添加到`window`上.

`persisted`属性是一个布尔值,对于`pageshow`来说,如果页面在存储在了往返缓存中就是`true`,否则就是`false`,第一次触发时,`pageshow`的`persisted`始终是`false`.

`pagehide`会在页面从浏览器中卸载后,在`unload`事件之前触发或者在浏览器中被隐藏时触发.对于`pagehide`的`persisted`,`true`表示页面在卸载以后会保存在往返缓存中,其值始终为`true`,除非不符合使用往返缓存的条件.

`pagehide`事件同样是在`document`上触发,但事件处理程序必须被添加到`window`.

*注意:注册了`onunload`事件处理程序(即使是空函数)的页面会自动排除在往返缓存之外.这是因为`onunload`事件典型的使用场景是撤销`onload`事件发生时所做的事情,如果使用往返缓存,则下一次页面显示时就不会触发`onload`事件,而这可能导致页面无法使用.*

#### hashchange事件
`hashchange`事件用于在`URL`散列值(URL最后#后面的部分)发生变化时触发事件.

该事件属于`HashChangeEvent`,继承自`Event`.

该事件处理程序必须添加给`window`.`event`对象有两个新属性:`oldURL`和`newURL`,表示变化前后的URL,而且是包含散列值的完整`URL`.

### 设备事件
设备事件可以用于确定用户使用设备的方式.用于定义新设备及设备相关的事件

#### orientationchange事件(已废弃)

**已废弃**

#### deviceorientation事件
*Baseline 2023 Newly available*

`deviceorientation`属于`DeviceOrientationEvent`,继承于`Event`.

该事件不可取消也不会冒泡.

如果可以获取设备的加速计信息,而且数据发生了变化,这个事件就会在`window`上触发.`deviceorientation`事件只反映设备在空间中的朝向,而不涉及移动相关的信息.

设备本身处于3D空间,即拥有x轴,y轴和z轴坐标系中.如果把设备静止放在水平的表明上,那么三轴的值均为0,其中,x轴方向为设备左侧到右侧,y轴方向为设备从底部到上部,z轴方向为从设备背面到正面.

当`deviceorientation`触发时,`event`对象中会包含各个轴相对于设备静置时坐标值的变化,主要是以下5个属性:
- `alpha`:0~360范围的浮点数,表示围绕z轴旋转时y轴的度数(左右转).
- `beta`:-180~180范围内的浮点数,表示围绕x轴旋转时z轴的度数(前后转).
- `gamma`:-90~90范围内的浮点数,表示围绕y轴旋转时z轴的度数(扭转).
- `absolute`:布尔值,表示设备是否返回绝对值.
- `compassCailbrated`:布尔值,表示设备的指南针是否正确校准.

![deviceorientation](img/get_start/deviceorientation.png)

![alpha-beta-gamma](img/get_start/orientation_abg.png)

#### devicemotion事件
仅在仅在一些支持的浏览器的安全上下文(HTTPS)中可用.

该事件属于`DeviceMotionEvent`,继承于`Event`.

这个事件用于提示设备实际上在移动,而不仅仅时改变了朝向.当该事件被触发时,`event`对象包含如下属性:
- `acceleration`:对象,包含x,y和z属性,包含不考虑重力的情况下各个维度的加速度信息.
- `accelerateIncludingGravity`:对象,包含x,y和z属性,反映各个维度的加速度信息,包含z轴自然重力加速度.
- `interval`:毫秒,距离下次触发`devicemotion`事件的时间.此值在时间之间应为常量.
- `rotationRate`:对象,包含`alpha`,`beta`,`gamma`属性,表示设备朝向.

如果上述值无法提供,则属性值为`null`.

### 触摸及手势事件
#### 触摸事件(TouchEvent)

`TouchEvent`继承自`UIEvent`.

当手指放在屏幕上,在屏幕上滑动或从屏幕移开时,*触摸事件*即会触发.触摸事件有如下几种:
- `touchstart`:手指放到屏幕上时触发(即使有一个手指已经放在了屏幕上)
- `touchmove`:手指在屏幕上滑动时连续触发.在这个事件中调用`preventDefault()`可以阻止滚动.
- `touchend`:手指从屏幕上移开时触发.
- `touchcancel`:系统停止追踪触摸时触发.

这些事件都会冒泡,都可以被取消.每个触摸事件提供了鼠标事件的公共属性:`bubbles`,`cancelable`,`view`,`clientX`,`clientY`,`screenX`,`screenY`,`detail`,`altKey`,`shiftKey`,`ctrlKey`和`metaKey`.(理论上后面的这4个属性不是继承的,而是自有的)

触摸事件还提供了以下3个属性用于追踪触点:
- `touches`:`Touch`对象的数组,表示当前屏幕上的每个触点
- `targetTouches`:`Touch`对象的数组,表示特定于事件目标的触点
- `changedTouches`:`Touch`对象的数组,表示自上次用户动作之后变化的触点

每个`Touch`对象都包含下列属性:
- `clientX`:触点在视口中的x坐标
- `clientY`:触点在视口中的y坐标
- `identifier`:触点ID
- `pageX`:触点在页面上的x坐标
- `pageY`:触点在页面上的y坐标
- `screenX`:触点在屏幕上的x坐标
- `screenY`:触点在屏幕上的y坐标
- `target`:触摸事件的事件目标
- `rotation`:手指变化旋转的角度(两个以上触点时)
- `scale`:两指之间距离变化(对捏)的程度(两个以上触点时)

#### 手势事件(GestureEvent)

**非标准**

*手势事件*会在两个手指触碰屏幕且相对距离或旋转角度变化时触发.手势事件有以下3种:
- `gesturestart`:一个手指已经放到屏幕上,再把另一个手指放到屏幕上时触发.
- `gesturechange`:任何一个手指在屏幕上的位置发生变化时触发.
- `gustureend`:其中一个手指离开屏幕时触发.

触摸事件和手势事件存在一定关系.当一个手指放在屏幕上时,会触发`touchstart`事件.当另一个手指放到屏幕上时,`gesturestart`事件会首先触发,然后紧接着触发这个手指的`touchstart`事件.如果两个手指或其中一个手指移动,则会触发`gesturechange`事件.只要其中一个手指离开屏幕,就会触发`gustureend`事件,紧接着触发该手指的`touchend`事件.

手势事件的`event`包含`bubbles`,`cancelable`,`view`,`clientX`,`clientY`,`screenX`,`screenY`,`detail`,`altKey`,`shiftKey`,`ctrlKey`,`metaKey`以及`rotation`和`scale`.`rotation`属性表示手指变化旋转的度数,负值表示逆时针旋转,正值表示顺时针旋转.`scale`表示两指之间的距离变化(对捏)的程度,开始时为1,然后随着距离增大或缩小相应地增大或缩小.

### 事件参考
参见:
- [事件参考](https://developer.mozilla.org/zh-CN/docs/Web/Events)
- [Web-API-Event](https://developer.mozilla.org/zh-CN/docs/Web/API/Event)

## 内存和性能
在JS中,页面中事件处理程序的数量与页面整体性能直接相关.原因包括:每个函数都是对象,都占用内存空间,对象很多,性能很差;其次,为指定事件处理程序所需访问DOM的次数会先期造成整个页面交互的延迟.只要在使用事件处理程序时多注意一些方法,就可以改善页面性能.

### 事件委托
*事件委托*利用事件冒泡,可以只使用一个事件处理程序来管理一种类型的事件.例如,`click`事件冒泡到`document`.这意味着可以为整个页面指定一个`onclick`事件处理程序,而不用为每个可点击元素分别指定事件处理程序.

例如:
````HTML
<ul id="myLinks">
    <li id="goSomewhere">Go somewhere</li>
    <li id="doSomething">Do something</li>
    <li id="sayHi">Say hi</li>
</ul>
````
````JS
let list = document.getElementById("myLinks");
list.addEventListener("click", (event) => {
    let target = event.target;
    switch(target.id) {
        case "doSomething":
            document.title = "I changed the document's title";
            break;
        case "goSomewhere":
            location.href = "https://www.example.com";
            break;
        case "sayHi":
            console.log("hi");
            break;
    }
});
````

只要可行,就应该考虑只给`document`添加一个事件处理程序,通过它处理页面中所有某种类型的事件.相对于之前的技术,事件委托具有如下优点:
- `document`对象随时可用,任何时候都可以给它添加事件处理程序(不用等待`DOMContentLoaded`或`load`事件).这意味着只要页面渲染出可点击元素,就可以无延迟地起作用.
- 节省花在设置页面事件处理程序上的事件.只指定一个事件处理程序既可以节省DOM引用,也可以节省时间.
- 减少整个页面所需的内存,提升整体性能.

最适合使用事件委托的事件包括:`click`,`mousedown`,`mouseup`,`keydown`,`keypress`.

### 删除事件处理程序
应该及时删除不用的事件处理程序.很多Web应用性能不佳都是由于无用的事件处理程序长驻内存导致的.

导致这个问题的主要原因有两个.第一个时删除带有事件处理程序的元素.比如通过`removeChild()`或`replaceChild()`删除节点或者使用`innerHTML`整体替换页面的某一部分.这时候,被删除的元素上有事件处理程序,就不会被垃圾收集程序正常清理.

在事件处理程序中删除事件目标元素会阻止事件冒泡.只有事件目标仍然存在于文档中时,事件才会冒泡.

## 模拟事件

### DOM模拟事件
可以使用`document.createEvent()`方法创建一个`event`对象.这个方法接收一个参数,此参数是一个表示要创建事件类型的字符串.

**警告:与`createEvent`一起使用的许多方法(例如`initCustomEvent`)已被弃用.大多数事件对象现在都有构造函数,这是创建事件对象实例的现代推荐方法**

可以作为创建事件类型的字符串见[DOM 标准—步骤2中的表格](https://dom.spec.whatwg.org/#dom-document-createevent)

创建`event`对象之后,需要使用事件相关的信息来初始化.每种类型的`event`对象都有特定的方法,可以使用相应数据来完成初始化.方法的名字并不相同,这取决于调用`createEvent()`时传入的参数.

模拟事件的最后一步是触发事件.为此要使用`dispatchEvent()`方法,这个方法存在于所有支持事件的DOM节点之上.`dispatchEvent()`方法接收一个参数,即表示要触发事件的`event`对象.

#### 模拟鼠标事件

**已弃用**

模拟鼠标事件需要先创建一个新的鼠标`event`对象,然后再使用必要的信息对其进行初始化.要创建鼠标`event`对象,可以调用`createEvent()`方法并传入`"mouseEvents"`参数.这样就会返回一个`event`对象,这个对象有一个`initMouseEvent()`方法(**已弃用**)(接收15个参数),用于为新对象指定鼠标的特定信息.

由于`initMouseEvent()`方法已弃用,可以查看[MDN-initMouseEvent](https://developer.mozilla.org/zh-CN/docs/Web/API/MouseEvent/initMouseEvent),不作赘述.也可以查看[使用事件构造器](#使用事件构造器)以了解替代的方法.

#### 模拟键盘事件
创建键盘事件的方式是给`createEvent()`方法传入参数`"keyboardEvent"`,并将返回的`event`对象使用`initKeyboardEvent`方法(**已弃用,请不要使用**).

由于`initKeyboardEvent()`方法已弃用,可以查看[MDN-initKeyboardEvent](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/initKeyboardEvent),不作赘述.也可以查看[使用事件构造器](#使用事件构造器)以了解替代的方法.

#### 模拟其他事件
要模拟HTML事件,也是为`createEvent()`传入`"HTMLEvents"`,然后再使用返回对象的`initEvent()`(**已弃用**)方法来初始化.

#### 自定义DOM事件
DOM3增加了自定义事件的类型.自定义事件不会触发原生DOM事件,但可以让开发者定义自己的事件.要创建自定义事件,需要调用`createEvent("CustomEvent")`.返回的对象包含`initCustomEvent()`(**已弃用**)方法.

由于`initCustomEvent()`方法已弃用,可以查看[MDN-initCustomEvent](https://developer.mozilla.org/zh-CN/docs/Web/API/CustomEvent/initCustomEvent),不作赘述.也可以查看[使用事件构造器](#使用事件构造器)以了解替代的方法.

### IE事件模拟
IE8及以下版本的事件系统与DOM不同,模拟事件也就不同.

其是通过`document`对象的`createEventObject()`方法(不接受参数)来创建`event`对象,返回的是一个通用的`event`对象.然后可以手工给返回的对象指定希望该对象具备的所有属性(可以指定任何属性).最后一步是在事件目标上调用`fireEvent()`方法,这个方法接收两个参数:事件处理程序的名称(例如`"onclick"`)和`event`对象.调用`fireEvent()`时,`srcElement`和`type`属性会自动指派到`event`对象.

### 使用事件构造器
详见[MDN-创建和触发事件](https://developer.mozilla.org/zh-CN/docs/Web/Events/Creating_and_triggering_events).

任何事件都可以通过构造函数来创建,而非`createEvent()`方法.

# 动画与Canvas图形
`<canvas>`元素会占据一块页面区域,让JS可以动态在上面绘制图片.`<canvas>`自身提供了一些API,包括基础绘画能力的2D上下文和被称为WebGL的3D上下文.

## 使用requestAnimationFrame
浏览器通过使用`requestAnimationFrame()`方法告诉浏览器要执行的动画.

### 早期定时动画和问题
早期定时动画都是通过`setInterval()`来控制动画执行的.但这不能保证事件精度,不能保证任务添加到队列里就会立即执行.此外,浏览器本身计时器精度就不准确.

### requestAnimationFrame
`window`上的`requestAnimationFrame()`方法优于上述方式的原因是,这个方法能够通知浏览器JS代码要执行动画了,这样浏览器就可以在运行某些代码后进行适当的优化.

该方法接收一个参数,此参数时一个要在重绘屏幕前调用的函数.这个函数就是修改DOM样式以反映下一次重绘有什么变化的地方.为了实现动画循环,可以把多个`requestAnimationFrame()`调用传来你起来:
````JS
function updateProgress() {
    let div = document.getElementById("status");
    div.style.width = (parseInt(div.style.width, 10) + 5) + "%";
    if (div.style.left != "100%") {
        requestAnimationFrame(updateProgress);
    }
}
requestAnimationFrame(updateProgress);
````

传给`requestAnimationFrame()`的回调函数可以接收一个参数,此参数是一个`DOMHighResTimeStamp`的实例(一个双精度浮点数),表示下次重绘的时间(误差约为5微秒),这一点非常重要,`requestAnimationFrame()`实际上把重绘任务安排在了未来一个已知的时间点上,而且通过这个参数告诉了开发者.要知道现在的时间,可以使用`performance.now()`,该方法也返回一个`DOMHighResTimeStamp`.

**警告：请确保总是使用(回调函数的)第一个参数(或其他一些获取当前时间的方法)来计算动画在一帧中的进度,否则动画在高刷新率的屏幕中会运行得更快**

### cancelAnimationFrame
`requestAnimationFrame()`也返回一个请求ID,可以用于通过另一个方法`cancelAnimationFrame()`来取消重绘任务:
````JS
let requestID = window.requestAnimationFrame(() => {
    console.log('Repaint');
});
window.cancelAnimationFrame(requestID);
````

### 通过requestAnimationFrame节流
`requestAnimationFrame`方法跟排期任务有关,浏览器会暴露出作为钩子的回调队列.所谓钩子,就是浏览器在执行下一次重绘之前的一个点.这个回调队列是一个可修改的函数列表,包含应该在重绘之前调用的函数.每次调用`requestAnimationFrame()`都会在队列上推入一个回调函数,队列长度没有限制.

这个回调队列的行为不一定跟动画有关,通过`requestAnimationFrame()`递归地向队列中加入回调函数,可以保证每次重绘最多只调用一次回调函数(虽然下次重绘已经在队列中).

````JS
let i = 0;
function sayHi() {
    console.log("hi");
    ++i;
    if (i < 60) requestAnimationFrame(sayHi);
}
requestAnimationFrame(sayHi);

console.log("aaa");
setTimeout(() => { console.log("bbb") }, 40);
setTimeout(() => { console.log("ccc") }, 100);
// aaa
// hi × 2
// bbb
// hi × 4
// ccc
// hi × 54
// "hi"不会像直接递归调用一样一下子全部出现
````

为了让任务不会反复添加到队列中,可以限制重绘的调用:
````JS
let enabled = true;
function expensiveOperation() { // 一个会耗费大量时间的函数
    console.log('Invoked at', Date.now());
    // ...
}
window.addEventListener('scroll', () => {   // 滑动事件会产生大量消息
    if (enabled) {    // 节流
        enabled = false;
        window.requestAnimationFrame(expensiveOperation);   // 控制浏览器在哪个渲染周期中执行
        window.setTimeout(() => enabled = true, 50);
    }
});
````

## 基本的画布功能
创建`<canvas>`元素时至少要设置其`width`和`height`属性,这样才能告诉浏览器在多大面积上绘图.出现在开始和结束标签之间的内容是后备数据,会在浏览器不支持`<canvas>`元素时显示.比如:
````HTML
<canvas id="drawing" width="200" height="200"> A drawing of something.</canvas>
````

`width`和`height`属性也可以在DOM节点上设置,因此可以随时修改.整个元素还可以通过CSS添加样式,并且元素在添加样式或实际绘制内容前是不可见的.

要在画布上绘制图形,首先要取得绘图上下文.使用`getContext()`方法可以获取对绘图上下文的引用.对于平面图形,需要给这个方法传入参数`"2d"`,表示要获取2D上下文对象:
````JS
let drawing = document.getElementById("drawing");
if (drawing.getContext) {   // 测试getContext()是否存在,确保浏览器支持<canvas>,部分浏览器即使不支持<canvas>,上面的表达式依然能够返回结果
    let context = drawing.getContext("2d");
}
````

可以使用`toDataURL()`方法导出`<canvas>`元素上的图像.这个方法接收一个参数:要生成图像的MIME类型(与用来创建图形的上下文无关).例如,要从画布上导出一张PNG格式的图片,可以这样做:
````JS
let drawing = document.getElementBy("drawing");
let imgURI = drawing.toDataURL("image/png");
let image = document.createElement("img");
image.src = imgURI;
document.body.appendChild(image);
````
浏览器默认将图像编码为PNG格式,除非另行指定.

如果画布中的图像是其他域绘制过来的,`toDataURL()`方法就会抛出错误.

## 2D绘图上下文
2D绘图上下文提供了绘制2D图形的方法,包括矩形,弧形和路径.2D上下文的坐标原点`(0,0)`在`<canvas>`元素的左上角.所有坐标值都相对于该点计算,因此x坐标向右增长,y坐标向下增长.默认情况下,`width`和`height`表示两个方向上像素的最大值.

### 填充和描边
2D上下文有两个基本绘制操作:填充和描边.填充以指定样式(颜色,渐变和图像)自动填充形状,而描边值为图形边界着色.大多数2D上下文操作有填充和描边的变体,显示效果取决于两个属性:`fillStyle`和`strokeStyle`.

这两个属性可以是字符串,渐变对象或图案对象,默认值都为`"#000000"`.字符串表示颜色值,可以是CSS支持的任意格式:名称,十六进制代码,rgb,rgba,hsl或hsla.比如:
````JS
let drawing = document.getElementById("drawing");
let context = drawing.getContext("2d");
context.strokeStyle = "red";
context.fillStyle = "#0000ff";
````
这两个属性也可以是渐变或图案.

### 绘制矩形
矩形是唯一一个可以直接在2D绘图上下文中绘制的形状.域绘制矩形相关的方法有3个:`fillRect()`,`strokeRect()`和`clearRect()`.这些方法都接收4个参数:矩形x坐标,矩形y坐标,矩形宽度和矩形高度.这几个参数的单位都是像素.

`fillRect()`方法用于指定颜色在画布上绘制并填充矩形.填充的颜色使用`fillStyle`颜色指定:
````JS
let drawing = document.getElementById("drawing");
let context = drawing.getContext("2d");
context.fillStyle = "#ff0000";
context.fillRect(10, 10, 50, 50);
context.fillStyle = "rgba(0, 0, 255, 0.5)";
context.fillRect(30, 30, 50, 50);
````

![fillRect](img/get_start/canvasFillRect.png)

`strokeRect()`方法使用通过`strokeStyle`属性指定的颜色绘制矩形轮廓.例如:
````JS
let drawing = document.getElementById("drawing");
let context = drawing.getContext("2d");
context.strokeStyle = "#ff0000";
context.strokeRect(10, 10, 50, 50);
context.strokeStyle = "rgba(0,0,255,0.5)";
context.strokeRect(30, 30, 50, 50);
````

![strokeRect](img/get_start/canvasStrokeRect.png)

描线宽度由`lineWidth`属性控制,它可以是任意整数值.类似地,`lineCap`属性控制线条端点的形状:`"butt"`(平头),`"round"`(圆头)或`"square"`(出方头),而`lineJoin`属性控制线条交点的形状:`"round"`(圆转),`"bevel"`(取平)或`"miter"`(出尖).

使用`clearRect()`方法可以擦除画布中某个区域.该方法用于把绘画上下文的某个区域变透明:
````JS
let drawing = document.getElementById("drawing");
let context = drawing.getContext("2d");
context.fillStyle = "#ff0000";
context.fillRect(10, 10, 50, 50);
context.fillStyle = "rgba(0,0,255,0.5)";
context.fillRect(30, 30, 50, 50);
context.clearRect(40, 40, 10, 10);
````

![clearRect](img/get_start/canvasClearRect.png)

### 绘制路径
2D绘图上下文支持很多在画布上绘制路径的方法.通过路径可以创建复杂的形状和线条.要绘制路径,必须首先调用`beginPath()`方法以表示要开始绘制新路径.然后,在调用下列方法来绘制路径:
- `arc(x, y, radius, startAngle, endAngle, counterclockwise)`:以坐标`(x, y)`为圆心,以`radius`为半径绘制一条弧线,起始角度为`startAngle`,结束角度为`endAngle`(都是弧度).最后一个参数`counterclockwise`表示是否逆时针计算起始角度和结束角度(默认为顺时针).
- `arcTo(x1, y1, x2, y2, radius)`:以给定半径`radius`,经由`(x1, y1)`绘制一条从上一点到`(x2, y2)`的弧线.
- `bezierCurveTo(c1x, c1y, c2x, c2y, x, y)`:以`(c1x, c1y)`和`(c2x, c2y)`为控制点,绘制一条从上一点到`(x, y)`的弧线(三次贝塞尔曲线).
- `lineTo(x, y)`:绘制一条从上一点到`(x, y)`的直线.
- `moveTo(x, y)`:不绘制线条,只把绘制光标移动到`(x, y)`.
- `quadraticCurveTo(cx, cy, x, y)`:以`(cx, cy)`为控制点,绘制一条从上一点到`(x, y)`的弧线(二次贝塞尔曲线).
- `rect(x, y, width, height)`:以给定宽度和高度在坐标点`(x, y)`绘制一个矩形.这个方法与`strokeRect()`和`fillRect()`区别在于,它创建的是一条路径,而不是独立的图形.

创建路径之后,可以使用`closePath()`方法绘制一条返回起点的线.如果路径已经完成,则既可以指定`fillStyle`属性并调用`fill()`方法来填充路径,也可以指定`strokeStyle`属性并调用`stroke()`方法来描画路径,还可以调用`clip()`方法基于已有路径创建一个新剪切区域.

例如:
````JS
let drawing = document.getElementById("drawing");
let context = drawing.getContext("2d");
context.beginPath();
context.arc(100, 100, 99, 0, 2 * Math.PI, false);
context.moveTo(194, 100);
context.arc(100, 100, 94, 0, 2 * Math.PI, false);
context.moveTo(100, 100);
context.lineTo(100, 15);
context.moveTo(100, 100);
context.lineTo(35, 100);
context.stroke();
````

![canvasPath](img/get_start/canvasPath.png)

`isPointInPath()`方法接收x轴和y轴坐标作为参数.这个方法用于确定指定的点是否在路径上,可以在关闭路径前随时调用:
````JS
if (isPointInPath(100, 100)) {
    console.log("Point (100, 100) is in the path.");
}
````

### 绘制文本
文本和图像混合也是常见的绘制需求,因此2D绘图上下文还提供了绘制文本的方法,即`fillText()`和`strokeText()`.这两个方法都接收4个参数:要绘制的字符串,x坐标,y坐标和可选的最大像素宽度.而且,这两个方法最终绘制的结果都却决于以下三个属性:
- `font`:以CSS语法指定的字体样式,大小,字体族等,比如`"10px Arial"`.
- `textAlign`:指定文本的对齐方式,可能的值包括`"start"`,`"end"`,`"left"`,`"right"`和`center`.推荐使用`"start"`和`"end"`,不使用`"left"`和`"right"`,因为前者无论在从左到右书写的语言还是从右向左书写的语言中含义都更明确.
- `textBaseLine`:指定文本的基线,可能的值包括`"top"`,`"hanging"`,`"middle"`,`"alphabetic"`,`"ideographic"`和`"bottom"`.

这些属性都有相应的默认值,因此没必要每次绘制文本时都设置它们.`fillText()`方法使用`fillStyle`属性绘制文本,而`strokeText()`方法使用`strokeStyle`属性.通常`fillText()`方法是使用最多的,因为它模拟了在网页中渲染文本.

例如:
````JS
let drawing = document.getElementById("drawing");
let context = drawing.getContext("2d");
context.beginPath();
context.arc(100, 100, 99, 0, 2 * Math.PI, false);
context.moveTo(194, 100);
context.arc(100, 100, 94, 0, 2 * Math.PI, false);
context.moveTo(100, 100);
context.lineTo(100, 15);
context.moveTo(100, 100);
context.lineTo(35, 100);
context.stroke();
context.font = "bold 14px Arial";
context.textAlign = "center";
context.textBaseline = "middle";
context.fillText("12", 100, 12);
````

![canvasText](img/get_start/canvasText.png)

使用`"center"`表示x坐标是文本的中心,使用`"start"`表示在从左到右书写的语言中,x坐标是文本的左侧.同样,`"top"`意味着y坐标是文本的顶部,`"bottom"`表示y坐标是文本的底部,`"hanging"`,`alphabetic`和`ideographic`分别引用字体中特定的基准点.

由于绘制文本很复杂,因此2D上下文提供了用于辅助确定文本大小的`measureText()`方法.这个方法接收一个参数,即要绘制的文本,然后返回一个`TextMetrics`对象,这个对象包含文本的尺寸的属性.[MDN-TextMetrics](https://developer.mozilla.org/zh-CN/docs/Web/API/TextMetrics)

`measureText()`方法使用`font`,`textAlign`和`textBaseline`属性当前的值计算绘制指定文本后的大小.

例如,假设要把文本`"Hello world!"`放到一个140像素宽的矩形中,可以使用以下代码,从100像素的字体大小开始计算,不断递减,知道文本大小合适:
````JS
let drawing = document.getElementById("drawing");
let context = drawing.getContext("2d");
let fontSize = 100;
context.font = fontSize + "px Arial";   // measureText()需要依赖font属性来计算
while (context.measureText("Hello world!").width > 140) {
    fontSize--;
    context.font = fontSize + "px Arial";
}
context.fillText("Hello world!", 10, 30);
context.fillText("Font size is " + fontSize + "px", 10, 70);
````

![canvasHelloWorld](img/get_start/canvasHelloWorld.png)

`fillText()`和`strokeText()`还有第四个参数,即文本的最大宽度.这个参数是可选的.如果调用`fillText()`和`strokeText()`时提供了此参数,但要绘制的字符串超出了最大宽度限制,则文本会以正确的字符高度绘制,但水平会被压缩,以达到限定宽度:

![canvasTextParam4](img/get_start/canvasTextParam4.png)

### 变换
上下文变换可以操作绘制在画布上的图像.2D绘图上下文支持所有常见的绘制变换.在创建绘制上下文时,会以默认值初始化变换矩阵.从而让绘制操作如实应用到绘制结果上.对绘制上下文应用变换,可以导致以不同的变化矩阵应用绘制操作,从而产生不同的结果.

以下方法可用于变换绘制上下文的变换矩阵:
- `rotate(angle)`:围绕原点把图像旋转`angle`弧度.
- `scale(scaleX, scaleY)`:通过在x轴乘以`scaleX`,在y轴乘以`scaleY`来缩放图像.`scaleX`和`scaleY`的默认值都是`1.0`.
- `translate(x, y)`:把原点移动到`(x, y)`.执行这个操作后,坐标`(0, 0)`就会变成`(x, y)`.
- `tranform(m1_1, m1_2, m2_1, m2_2, dx, dy)`:通过矩阵乘法直接修改矩阵:
$$
\begin{bmatrix}
m_{_{11} } & m_{_{12} } & dx \\
m_{_{21} } & m_{_{22} } & dy \\
0          & 0          & 1  \\
\end{bmatrix}
$$
- `setTransform(m1_1, m1_2, m2_1, m2_2, dx, dy)`:把矩阵重置为默认值,再以传入的参数调用`transform()`.

例如:
````JS
let drawing = document.getElementById("drawing");
let context = drawing.getContext("2d");
context.beginPath();
context.arc(100, 100, 99, 0, 2 * Math.PI, false);
context.moveTo(194, 100);
context.arc(100, 100, 94, 0, 2 * Math.PI, false);
context.translate(100, 100);    // 将原点移动到表盘中心
context.rotate(1);      // 旋转1rad
context.moveTo(0, 0);
context.lineTo(0, -85);
context.moveTo(0, 0);
context.lineTo(-65, 0);
context.stroke();
````

![canvasTransform](img/get_start/canvasTransform.png)

所有这些变换,以及`fillStyle`和`strokeStyle`属性,会一直在上下文中保留,直到再次修改它们.并没有办法能够将它们重置为默认值.但可以通过`save()`方法将这一时刻的设置存放到一个暂存栈中.调用`restore()`方法可以从暂存栈中取出并恢复之前保存的设置:
````JS
context.fillStyle = "#ff0000";  // 红色
context.save();

context.fillStyle = "#00ff00";  // 绿色
context.translate(100, 100);
context.save();

context.fillStyle = "#0000ff";  // 蓝色
context.fillRect(0, 0, 100, 200);   // 在(100, 100)绘制蓝色矩形

context.restore();
context.fillRect(10, 10, 100, 200); // 在(100, 100)绘制绿色矩形

context.restore();
context.fillRect(0, 0, 100, 200);   // 在(0, 0)绘制红色矩形
````

![canvasSaveRestore](img/get_start/canvasSaveRestore.png)

`save()`方法不保存绘图上下文的内容.

### 绘制图像
2D绘图上下文内置支持操作图像.如果想把现有图像绘制到画布上,可以使用`drawImage()`方法.这个方法接收5族不同的参数,并产生不同的结果.最简单的调用是传入一个HTML的`<img>`元素,以及表示绘制目标的x和y坐标,结果是把图像绘制到指定位置.

如果想改变所绘制图像的大小,可以再传入另外两个参数:目标宽度和目标高度.这只会缩放绘制的图像.

还可以只把图像绘制到上下文中的一个区域.此时,需要给`drawImage()`提供9个参数:要绘制的图像,源图像x坐标,源图像y坐标,源图像宽度,源图像高度,目标区域x坐标,目标区域y坐标,目标区域宽度和目标区域高度.

除了可以是`<img>`元素,还可以是另一个`<canvas>`元素,这样就会把另一个画布的内容绘制到当前画布上.

但如果绘制的图像来自其他域而非当前页面,则不能获取其数据.

### 阴影
2D上下文可以根据以下属性的值自动为已有形状或路径生成阴影:
- `shadowColor`:CSS颜色值,表示要绘制的阴影颜色,默认为黑色.
- `shadowOffsetX`:阴影相对于形状或路径的x坐标偏移量,默认为`0`.
- `shadowOffsetY`:阴影相对于形状或路径的y坐标偏移量,默认为`0`.
- `shadowBlur`:像素,表示阴影的模糊量.默认值为`0`,表示不模糊.

例如:
````JS
let context = drawing.getContext("2d");
context.shadowOffsetX = 5;
context.shadowOffsetY = 5;
context.shadowBlur = 4;
context.shadowColor = "rgba(0, 0, 0, 0.5)";
context.fillStyle = "#ff0000";
context.fillRect(10, 10, 50, 50);
context.fillStyle = "rgba(0, 0, 255, 1)";
context.fillRect(30, 30, 50, 50);
````

![canvasShadow](img/get_start/canvasShadow.png)

### 渐变
渐变通过`CanvasGradient`的实例表示.

要创建一个新的线性渐变,可以调用上下文的`createLinearGradient()`方法.这个方法接收4个参数:起点x坐标,起点y坐标,终点x坐标和终点y坐标.调用之后,该方法会以指定大小创建一个新的`CanvasGradient`对象并返回实例.

`gradient`(`CanvasGradient`实例)使用`addColorStop()`方法为渐变指定色标.这个方法接收两个参数:色标位置和CSS颜色字符串.色标位置通过0-1范围的值表示,0是第一种颜色,1是最后一种颜色.

最后,把`gradient`赋值给`fillStyle`或`strokeStyle`属性,从而以渐变填充或描绘绘制的图形:
````JS
let drawing = document.getElementById("drawing");
let context = drawing.getContext("2d");
let gradient = context.createLinearGradient(30, 30, 70, 70);
gradient.addColorStop(0, "white");
gradient.addColorStop(1, "black");
context.fillStyle = gradient;
context.fillRect(30, 30, 50, 50);
````

![canvasCreateLinearGradient](img/get_start/canvasCreateLinearGradient.png)

注意,在调用`createLinearGradient()`时,给出了渐变的范围,因此,如果矩阵没有绘制在给出的渐变范围,则只会显示部分渐变:
````JS
context.fillStyle = gradient;
context.fillRect(50, 50, 50, 50);
````

![canvasCreateLinearGradientWarn](img/get_start/canvasCreateLinearGradientWarn.png)

径向渐变(或放射性渐变)要使用`createRadialGradient()`方法来创建.这个方法接收6个参数,分别对应两个圆形圆心的坐标和半径.前3个参数指定起点圆形中心的x,y坐标和半径,后3个参数指定终点圆形中心的x,y坐标和半径:
````JS
let drawing = document.getElementById("drawing");
let context = drawing.getContext("2d");
let gradient = context.createRadialGradient(55, 55, 10, 55, 55, 30);
gradient.addColorStop(0, "black");
gradient.addColorStop(1, "white");
context.fillStyle = gradient;
context.fillRect(25, 25, 60, 60);
````

![canvasCreateRadialGradient](img/get_start/canvasCreateRadialGradient.png)

### 图案
图案是用于填充和描画重复图像.要创建新图案,可以调用`createPattern()`方法并传入两个参数:一个HTML`<img>`元素(或`<video>`元素或另一个`<canvas>`元素)和一个表示该如何重复图像的字符串.第二个参数的值与CSS的`background-repeat`属性是一样的,包括`"repeat"`,`"repeat-x"`,`"repeat-y"`和`"no-repeat"`:
````JS
let image = document.images[0],
    pattern = context.createPattern(image, "repeat");
context.fillStyle = pattern;
context.fillRect(10, 10, 150, 150);
````

![canvasCreatePattern](img/get_start/canvasCreatePattern.png)

### 图像数据
使用`getImageData()`方法获取原始图像数据.这个方法接收4个参数:要取得数据中第一个像素的左上角坐标和要取得的像素宽度和高度.

返回的对象是一个`ImageData`的实例.每个`ImageData`对象都包含3个属性:`width`,`height`和`data`,其中,`data`属性是包含图像的原始像素信息的数组.每个像素在`data`数组中都由4个值表示,分别代表红,绿,蓝和透明度值.因此,第一个像素的信息包含在第0到第3个值中,第二个像素的信息包含在第4到第7个值中:
````JS
let data = imageData.data,
    red = data[0],
    green = data[1],
    blue = data[2],
    alpha = data[3];
````
数组中的每个值都在`0-255`范围内(包括边界).

对原始图像数据进行访问可以更灵活地操作图像,可以见:[How to apply filters in javascript](https://img.ly/blog/how-to-apply-filters-in-javascript/)

注意,如果画布上绘制的是跨域内容,则尝试获取图像数据会导致JS报错.

### 合成
2D上下文中绘制的所有内容都会应用两个属性:`globalAlpha`和`globalCompositionOperation`,其中,`globalAlpha`属性是一个范围在`[0, 1]`的值,用于指定所有绘制内容的透明度,默认值为0.

`globalCompositionOperation`属性表示新绘制的形状如何与上下文中已有的形状融合.这个属性是一个字符串,可以取下列值:
- `source-over`:默认值,新图形绘制在原有图形上面.
- `source-in`:新图形值绘制出与原有图形重叠的部分,画布上其余部分全部透明.
- `source-out`:新图形值绘制出不与原有图形重叠的部分,画布上其余部分全部透明.
- `source-atop`:新图形只绘制出与原有图形重叠的部分,原有图形不受影响.
- `destination-over`:新图形绘制在原有图形下面,重叠部分只有原图形透明像素下的部分可见.
- `destination-in`:新图形绘制在原有图形下面,画布上只剩下两者重叠部分,其余部分完全透明.
- `destination-out`:新图形与原有图形重叠的部分完全透明,原图形其余部分不受影响.
- `destination-atop`:新图形绘制在原有图形下面,原有图形与新图形不重叠的部分完全透明.
- `lighter`:新图形与原有图形重叠部分的像素值相加,使该部分变亮.
- `copy`:新图形将擦除并完全取代原有图形.
- `xor`:新图形与原有图形重叠部分的像素执行异或计算.

详见[MDN-globalCompositeOperation](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/globalCompositeOperation)

## WebGL
`WebGL`是画布的3D上下文.与其他Web技术不同,`WebGL`不是W3C制定的标准,而是`Khronos Group`的标准.

要使用`WebGL`最好熟悉`OpenGL ES 2.0`,因为很多概念可以照搬过来.

### WebGL上下文
`WebGL 2.0`上下文的名字叫`"webgl2"`,`WebGL 1.0`上下文的名字叫`"webgl1"`.如果浏览器不支持WebGL,则尝试访问WebGL上下文会返回`null`.
````JS
let drawing = document.getElementById("drawing");
let gl = drawing.getContext("webgl");
````

### WebGL基础
- 常量:常量在`OpenGL`中的名字以`GL_`开头.在WebGL中,`context`对象上的常量则不包含`GL_`前缀.例如,`GL_COLOR_BUFFER_BIT`常量在WebGL中要这样访问`gl.COLOR_BUFFER_BIT`.WebGL以这种方式支持大部分OpenGL常量(少数常量不支持).
- 方法命名:OpenGL中的很多方法会包含相关的数据类型信息.接收不同类型和不同数量参数的方法,会通过方法名的后缀体现这些信息.表示参数数量的数字在先,表示数据类型的字符串(`f`表示浮点数,`i`表示整数)在后.比如,`gl.uniform4f()`的意思是需要4个浮点数值参数,`gl.uniform3i()`表示需要3个整数值参数.还有很多方法接收数组,这类方法用字母`v`来表示.因此,`gl.uniform3iv()`就是要接收一个包含3个值的数组参数.在编写WebGL代码时,要记住这些约定.

/// TODO

### WebGL1与WebGL2
`WebGL1`代码几乎完全与`WebGL2`兼容.在使用`WebGL2`上下文时,唯一可能涉及修改代码以保证兼容性的就是扩展.在`WebGL2`中,很多扩展都变成了默认功能.

# 表单脚本
## 表单基础
`Web`表单在HTML中以`<form>`元素表示,在JS中则以`HTMLFormElement`类型表示.`HTMLFormElement`类型继承自`HTMLElement`类型,因此拥有与其他HTML元素一样的默认属性.不过,`HTMLFormElement`也有自己的属性和方法:
- `acceptCharset`:服务器可以接收的字符集,等价于HTML的`accept-charset`属性.
- `action`:请求的URL,等价于HTML的`action`属性.
- `elements`:表单中所有控件的`HTMLFormControlsCollection`(不会包含文本等节点,但包括所有的属于控件的子节点,即使是非直接的)(继承自`HTMLCollection`).
- `enctype`:请求的编码类型,等价于HTML的`enctype`属性.
- `length`:表单中控件的数量.
- `method`:HTTP请求的方法类型,通常是`"get"`或`"post"`,等价于HTML的`method`属性.
- `name`:表单的名字,等价于HTML的`name`属性.
- `reset()`:把表单字段重置为各自的默认值.
- `submit()`:提交表单.
- `target`:用于发送请求和接收响应的窗口的名字,等价于HTML的`target`属性.

有几个方式可以取得`<form>`元素的引用:
- `getElementById()`并把表单元素当作一个普通元素给`<form>`指定一个`id`.
- `document.forms`集合(`HTMLCollection`类型)可以获取页面上所有的表单元素.例如:`let myForm = document.forms["form2"]; // 取得名字为"form2"的表单`

### 提交表单
表单是通过用户点击提交按钮或图片按钮的方式提交的.提交按钮可以使用`type`属性为`"submit"`的`<input>`或`"<button>"`元素来定义,图片按钮可以使用`type`属性为`"image"`的`<image>`元素来定义:
````HTML
<!-- 以下按钮都可以提交它们所在的表单: -->

<!-- 通用提交按钮 -->
<input type="submit" value="Submit Form">

<!-- 自定义提交按钮 -->
<button type="submit">Submit Form</button>

<!-- 图片按钮 -->
<input type="image" src="graphic.gif">
````

如果表单中有上述任何一个按钮,且焦点在表单中某个控件上,则按回车键也可以提交表单.(`textarea`控件是个例外,当焦点在它上面时,按回车键会换行.)

以这种方式提交表单会在向浏览器发送请求之前触发`submit`事件.这样就提供了一个验证表单数据的机会,可以根据验证结果决定是否真的要提交.阻止这个事件的默认行为可以取消提交表单:
````JS
let form = document.getElementById("myForm");
form.addEventListener("submit", (event) => {
    event.preventDefault();
});
````

调用`preventDefault()`方法可以阻止表单提交.通常,在表单数据无效以及不应该发送到服务器时可以这样处理.

当然,也可以通过编程的方式在JS中调用`submit()`方法来提交表单.可以在任何时候调用这个方法来提交表单,而且表单中不存在提交按钮也不影响表单提交.

通过`submit()`提交表单时,`submit`事件不会触发.

表单提交的一个最大问题时可能会提交两次表单.如果提交表单之后没有什么反映,那么用户可能会多次点击提交按钮.解决这个问题主要有两种方式:在表单提交之后禁用提交按钮,或者通过`submit`事件处理程序取消之后的表单提交.

### 重置表单
用户单击重置按钮可以重置表单.重置按钮可以使用`type`属性为`"reset"`的`<input>`或`<button>`元素来创建:
````HTML
<!-- 通用重置按钮 -->
<input type="reset" value="Reset Form">

<!-- 自定义重置按钮 -->
<button type="reset">Reset Form</button>
````
这两种按钮都可以重置表单.表单重置后,所有表单字段都会重置回页面第一次渲染时各自拥有的值.如果字段原来是空的,就会变成空的;如果字段有默认值,则恢复为默认值.

用户单击重置按钮重置表单就会触发`reset`事件.这个事件为取消重置提供了机会.例如:
````JS
let form = document.getElementById("myForm");
form.addEventListener("reset", (event) => {
    event.preventDefault();
});
````

重置表单可以通过JS调用`reset()`方法来完成:`form.reset();`

*注意:表单设计中通常不提倡重置表单.实践中几乎没有重置表单的需求.一般来说,提供一个取消按钮,让用户点击返回前一个页面会比恢复表单中所有的默认值来得更直观.*

### 表单字段
表单元素可以像页面中的其他元素一样使用原生DOM方法来访问.此外,所有表单元素都是表单`elements`属性(元素集合)(不会包含文本等节点)中包含的一个值.这个`elements`集合是一个有序列表,包含对表中所有字段的引用,包括所有`<input>`,`<textarea>`,`<select>`和`<fieldset>`元素.`elements`集合中的每个字段都以它们在HTML标记中出现的次序保存,可以通过索引位置的`name`属性来访问:
````JS
let form = document.getElementById("form1");
// 取得表单中的第一个字段
let field1 = form.elements[0];
// 取得表单中名为(或id为)"textbox1"的字段
let field2 = form.elements["textbox1"];
// 取得字段的数量
let fieldCount = form.elements.length;
````

即使控件是非直接子节点,`elements`属性仍然会将其包含在内:
````HTML
<form id="myForm">
    <fieldset>
        <input type="text" value="bbb">
    </fieldset>
    <input type="text" value="aaa" required pattern="\d+">
</form>
````
````JS
let form = document.getElementById("myForm");
for (let field of form.elements) {
    console.log(field);
}
// <fieldset>...</fieldset>
// <input type="text" value="bbb">
// <input type="text" value="aaa" required="" pattern="\d+">
````

如果多个表单控件使用了同一个`name`(很常见,因为存在像单选按钮那样的元素),则会返回包含所有同名元素的`HTMLCollection`.

*注意:可以直接通过`form[0]`而非`form.elements[0]`来索引.只不过这种方式是为了向后兼容旧浏览器而提供的,实际开发中应该避免这样使用.*

#### 表单字段的公共属性
除`<fieldset>`元素以外,所有表单字段都有一组同样的属性.由于`<input>`类型可以表示多种表单字段,因此这些属性只适用于特定类型的字段,除此以外的属性可以在任何表单字段上使用.以下为这些表单字段的公共属性和方法:
- `disabled`:布尔值,表示表单字段是否禁用.
- `form`:指针,指向表单字段所属的表单.这个属性是只读的.
- `name`:字符串,这个字段的名字.
- `readOnly`:布尔值,表示这个字段是否只读.
- `tabIndex`:数值,表示这个字段在按`Tab`键时的切换顺序.
- `type`:字符串,表示字段类型,如`"checkbox"`,`"radio"`等.
- `value`:要提交给服务器的字段值.对文件输入字段来说,这个属性是只读的,仅包含计算机上某个文件的路径.

这里面除了`form`属性之外,JS可以动态修改任何属性:
````JS
let form = document.getElementById("myForm");
let field = form.elements[0];
field.value = "Another value";
console.log(field.form === form);
field.focus();
field.disabled = true;
field.type = "checkbox";    // 改变字段的类型(不推荐,但对<input>来说是可能的)
````

这种能力的用例为在用户多次点击表单点,禁用表单的提交按钮.可以通过监听`submit`事件来实现:
````JS
let form = document.getElementById("myForm");
form.addEventListener("submit", (event) => {
    let target = event.target;
    let btn = target.elements["submit-btn"];
    btn.disabled = true;
});
// 注意:不能使用click事件,原因是不同浏览器的click事件和submit事件先后顺序不同,如果先触发click事件,然后禁用了提交按钮,那么表单就不会提交了.
````

`type`属性可以用于除了`<fieldset>`之外的任何表单字段.对于`<input>`元素,这个值等于`HTML`的`type`属性值.对于其他元素,这个`type`属性的值按照下面设置:
- 描述:`值`.`示例HTML`
- 单选列表:`"select-one"`.`<select>...</select>`
- 多选列表:`"select-multiple"`.`<select multiple>...</select>`
- 自定义按钮:`"submit"`.`<button>...</button>`
- 自定义非提交按钮:`"button"`.`<button type="button">...</button>`
- 自定义重置按钮:`"reset"`.`<button type="reset">...</button>`
- 自定义提交按钮:`"submit"`.`<button type="submit">...</button>`

对于`<input>`和`<button>`元素,可以动态修改其`type`属性.但`<select>`元素的`type`属性是只读的.

#### 表单字段的公共方法
每个表单字段都有两个公共方法:`focus()`和`blur()`.

`focus()`方法把浏览器焦点设置到表单字段,这意味着该字段会变成活动字段并可以响应键盘事件.在页面加载后把焦点定位到表单中第一个字段就是很常见的做法:
````JS
window.addEventListener("load", (event) => {
    document.forms[0].elements[0].focus();
});
````
注意,如果表单中第一个字段是`type`为`"hidden"`的`<input>`元素,或者该字段被CSS属性`display`或`visibility`隐藏了,以上代码就会出错.

HTML5为表单字段增加了`autofocus`布尔属性,支持的浏览器会自动为带有该属性的元素设置焦点,而无须使用JS:
````HTML
<input type="text" autofocus>
````
在JS中访问表单字段的`autofocus`属性会返回`true`(如果设置了`autofocus`).在不支持的浏览器中,该属性是空字符串(如果设置了`autofocus`).

`blur()`是`focus()`的反向操作,用于从元素上移除焦点.调用`blur()`时,焦点不会转移到任何特定元素,仅仅只是从调用这个方法的元素上移除了.

#### 表单字段的公共事件
除了鼠标,键盘,变化和HTML事件外,所有字段还支持以下3个事件:
- `blur`:在字段失去焦点时触发.
- `change`:在`<input>`和`<textarea>`元素的`value`发生变化且失去焦点时触发,或者在`<select>`元素中选中项发生变化时触发.
- `focus`:在字段获得焦点时触发.

`blur()`或`focus()`方法被调用也会触发上述的事件.

`blur`和`change`事件的触发先后顺序没有明确的规定,因此不能依赖这两个事件触发的顺序.

例如:
````JS
let textbox = document.forms[0].elements[0];
textbox.addEventListener("focus", (event) => {
    let target = event.target;
    if (target.style.backgroundColor != "red") {
        target.style.backgroundColor = "yellow";
    }
});
textbox.addEventListener("blur", (event) => {
    let target = event.target;
    target.style.backgroundColor = /[^\d]/.test(target.value) ? "red" : "";
});
textbox.addEventListener("change", (event) => {
    let target = event.target;
    target.style.backgroundColor = /[^\d]/.test(target.value) ? "red" : "";
});
````

## 文本框编程
在HTML中有两种表示文本框的方式:单行使用`<input>`元素,多行使用`<textarea>`元素.这两个控件非常相似,大多数时候行为也一样.不过,它们也有非常重要的区别.

默认情况下,`<input>`元素显示为文本框,省略`type`属性会以`"text"`作为默认值.然后可以通过`size`属性指定文本框的宽度,这个宽度是以字符数来计量的.而`value`属性用于指定文本框的初始值,`maxLength`属性用于指定文本框允许的最多字符数:
````HTML
<input type="text" size="25" maxlength="50" value="initial value">
````

`<textarea>`元素总是会创建多行文本框.可以使用`rows`属性指定这个文本框的高度,以字符数计量;以`cols`属性指定以字符数计量的文本框宽度,类似于`<input>`元素的`size`属性.与`<input>`不同的是,`<textarea>`的初始值必须包含在`<textarea>`和`</textarea>`之间且不允许在HTML中指定最大的允许字符数:
````HTML
<textarea rows="25" cols="5">initial value</textarea>
````

但是这两种类型的文本框都会在`value`属性中保存自己的内容.通过这个属性,可以读取也可以设置文本模式的值:
````JS
console.log(textbox.value);
textbox.value = "some new value";
````

最好使用上述`value`属性来读写文本框的属性,而非修改文本节点.

### 选择文本
两种文本框都支持名为`select()`的方法,此方法用于全部选中文本框中的文本.大多数浏览器在调用`select()`方法后自动将焦点设置到文本框.这个方法不接受参数,可以在任何时候调用:`textbox.select();`

#### select事件
`select`事件在选中文本框中的文本时,会触发`select`事件.事件的触发时机因浏览器而异.调用`select()`方法也会触发`select`事件.

#### 取得选中的文本
`selectionStart`和`selectionEnd`这两个属性包含基于0的数值,分别表示文本选区的起点和终点(文本选区起点的偏移量和文本终区的偏移量).可用以下代码取得文本框中选中的文本:
````JS
function getSelectedText(textbox) {
    return textbox.value.substring(textbox.selectionStart,
                                   textbox.selectionEnd);
}
````

#### 部分选中的文本
`setSelectionRange()`方法接收两个参数:要选择的第一个字符的索引和停止选择的字符的索引:
````JS
textbox.value = "Hello world!";
textbox.setSelectionRange(0, textbox.value.length); // "Hello world!"
textbox.setSelectionRange(0, 3);    // "Hel"
````

不过,要是想要看到选择,则必须在调用`setSelectionRange()`之前或之后给文本框设置焦点.

### 输入过滤
由于文本框默认并未提供什么验证功能,因此必须通过JS来实现这种输入过滤.

#### 屏蔽字符
可以通过`keypress`事件来屏蔽字符,例如:
````JS
// 只允许输入数字
textbox.addEventListener("keypress", (event) => {
    if (!/\d/.test(String.fromCharCode(event.charCode)) &&
        event.charCode > 9 && /* 某些低版本的浏览器可能也会屏蔽像↑这样的方向键等,因此添加 */
        !event.ctrlKey /* 防止按下Ctrl+C,Ctrl+V等按键时被屏蔽 */ ) {
        event.preventDefault();
    }
});
````

#### 处理剪贴板
与剪贴板相关的事件(属于`ClipboardEvent`,继承自`Event`)包括:
- `beforecopy`**(已弃用)**:复制操作发生前触发.
- `copy`:复制操作发生时触发.
- `beforecut`**(已弃用)**:剪切操作发生前触发.
- `cut`:剪切操作发生时触发.
- `beforepaste`**(已弃用)**:粘贴操作发生前触发.
- `paste`:粘贴操作发生时触发.

*注意:`beforecopy`,`beforecut`,`beforepaste`是非标准的,在不同浏览器触发的时机不同.取消这三个事件并不会阻止复制,剪切和粘贴行为.*

要阻止剪贴板行为,必须取消`copy`,`cut`,`paste`事件.

可以在`document`,`window`或者元素上使用剪贴板事件.

该`event`存在`clipboardData`对象,可以获取剪贴板数据.该方法上存在3个方法:
- `getData()`:从剪贴板检索字符串数据,并接收一个参数,该参数是要检索的数据的格式(是一个`MIME`类型,不过会将`"text"`视为等价于`"text/plain"`).
- `setData()`:其第一个参数用于指定数据类型(是一个`MIME`类型,但不认可`"text"`类型,需要写成`"text/plain"`),第二个参数是要放到剪贴板上的文本.
- `clearData()`:删除数据,其第一个参数用于指定删除的数据类型(是一个`MIME`类型,不指定或`""`表示所有数据类型).

例如:
````JS
// 确保只有数字才能粘贴到文本框中
textbox.addEventListener("paste", (event) => {
    let text = getClipboardText(event);
    if (!/^\d*$/.test(text)) {
        event.preventDefault();
    }
});
````

### 自动切换
JS可以通过很多方式来增强表单字段的易用性.最常用的是在当前字段完成时自动切换到下一个字段.例如收集数据长度已知(比如电话号码)的字段.

例如:
````HTML
<!-- 分三段输入电话号码 -->
<input type="text" name="tel1" id="txtTel1" maxlength="3">
<input type="text" name="tel2" id="txtTel2" maxlength="3">
<input type="text" name="tel3" id="txtTel3" maxlength="4">
````

可以在每个文本框输入到最大允许字符数时自动把焦点切换到下一个文本框:
````JS
function tabForward(event) {
    let target = event.target;
    if (target.value.length == target.maxLength) {
        let form = target.form;
        for (let i = 0, len = form.elements.length; i < len; ++i) {
            if (form.elements[i] == target) {
                if (form.elements[i + 1]) {
                    form.elements[i + 1].focus();
                }
                return;
            }
        }
    }
}
let inputIds = ["txtTel1", "txtTel2", "txtTel3"];
for (let id of inputIds) {
    let id of document.getElementById(id);
    textbox.addEventListener("keyup", tabForward);
}
let textbox1 = document.getElementById("txtTel1");
let textbox2 = document.getElementById("txtTel2");
let textbox3 = document.getElementById("txtTel3");
````

### HTML5约束验证API
HTML5为浏览器新增了在提交表单前验证数据的能力.这些能力实现了基本的验证,即使JS不可用或加载失败也没关系.这是因为浏览器自身会基于指定的规则进行验证,并在出错时显示适当的错误消息(无须JS).

验证会根据某些条件应用到表单字段.可以使用HTML标记指定对特定字段的约束,然后浏览器会根据这些约束自动执行表单验证.

#### 必填字段
HTML的`require`属性表示该字段必须有值,否则无法提交表单.这个属性适用于`<input>`,`<textarea>`和`<select>`字段:
````HTML
<input type="text" name="username" required>
````

可以通过JS检测对于元素的`required`属性来判断表单字段是否为必填:
````JS
let form = document.getElementById("myForm");
let field = form.elements["username"];
console.log(field.required);    // true
````

还可以使用下面的代码检测浏览器是否支持`required`属性:
````JS
console.log("required" in document.createElement("input"));
````

#### 更多输入类型
`HTML5`为`<input>`元素增加了几个新的`type`值.这些类型属性不仅表明了字段期待的数据类型,而且也提供了一些默认验证,详见[HTML-type属性](../HTML/get_start.md#type属性).

老版本浏览器会自动将未知类型值设置为`"text"`,因此,如果想要检查浏览器是否支持新的`type`值,可以:
````JS
let input = document.createElement("input");
input.type = "email";
let isEmailSupported = (input.type == "email");
````

对于`"number"`,`"range"`,`"datetime"`,`"datetime-local"`,`"date"`,`"month"`,`"week"`和`"time"`这些数值类型,都可以指定`min`属性(最小可能值),`max`属性(最大可能值),`step`属性(步长).
````HTML
<!-- 只允许输入0到100中5的倍数 -->
<input type="number" min="0" max="100" step="5" name="count">
````

上述属性也可以在JS中通过对应元素的DOM属性来访问和修改.此外,还有两个方法`stepUp()`和`stepDown()`分别接收一个可选的参数:要从当前值加上或减去的数值(不填则为表单类型对应的默认值).

#### 输入模式
`HTML`的`pattern`属性用于指定一个正则表达式,用户输入的文本必须与之匹配.例如:
````HTML
<!-- 限制只能在文本字段中输入数字 -->
<input type="text" pattern="\d+" name="count">
````

注意,模式的开头和末尾分别假设有`^`和`$`.这意味着输入内容必须从头到尾都严格与模式匹配.

指定`pattern`属性不会阻止用户输入无效内容.模式会应用到值,然后浏览器会知道值是否有效.

通过元素的`pattern`属性可以读取模式,返回字符串(不是正则表达式类型).

可以使用下面的代码检测浏览器是否支持`pattern`属性:
````JS
console.log("pattern" in document.createElement("input"));
````

#### 检测有效性
由于上面的约束都不能直接阻止用户的输入,因此必须使用`checkValidity()`方法检测表单中任意给定字段是否有效.有效返回`true`,否则返回`false`,判断条件就是上述的HTML约束.

例如:
````JS
if (document.forms[0].elements[0].checkValidity()) {
    // 字段有效
} else {
    // 字段无效
}
````

要检测这个表单是否有效,可以直接在表单上调用`checkValidity()`方法.这个方法会在所有字段都有效时返回`true`,有任何字段无效时返回`false`:
````JS
if (document.forms[0].checkValidity()) {
    // 表单有效
} else {
    // 表单无效
}
````

`validity`属性能够告诉字段为什么有效或无效,其返回`ValidityState`对象,这个对象包含一系列布尔值属性:
- `customError`:如果设置了`setCustomValidity()`就返回`true`,否则返回`false`.
- `patternMismatch`:如果字段值不匹配指定的`pattern`属性则返回`true`.
- `rangeOverflow`:如果字段值大于`max`的值则返回`true`.
- `rangeUnderflow`:如果字段值小于`min`的值则返回`true`.
- `stepMisMatch`:如果字段值与`min`,`max`和`step`的值不符合则返回`true`.
- `tooLong`:如果字段值的长度超过了`maxLength`属性指定的值则返回`true`.
- `typeMismatch`:如果字段值不是`"email"`或`"url"`要求的格式则返回`true`.
- `vaild`:如果其他所有属性的值都为`false`则返回`true`.与`checkValidity()`的条件一致.
- `valueMissing`:如果字段是必填的但没有值则返回`true`.

例如;
````JS
if (input.validity /* 检查浏览器是否支持validity属性 */
    && !input.validity.valid) {
    if (input.validity.valueMissing) {
        console.log("Please specify a value.");
    } else if (input.validity.typeMismatch) {
        console.log("Please enter an email address.");
    } else {
        console.log("Value is invalid.");
    }
}
````

#### 禁用验证
指定`novalidate`属性可以禁止对表单进行任何验证:
````HTML
<form method="post" action="/signup" novalidate>
    <!-- 表单元素 -->
</form>
````
这个值也可以通过JS属性`noValidate`检索或设置,设置为`true`表示属性存在,设置为`false`表示属性不存在:
````JS
document.forms[0].noValidate = true;    // 关闭验证
````

如果一个表单中有多个提交按钮,那么可以给特定的提交按钮添加`formnovalidate`属性,指定通过该按钮无效验证即可提交表单:
````HTML
<form method="post" action="/foo">
    <!-- 表单元素 -->
    <input type="submit" value="Regular Submit">
    <input type="submit" formnovalidate name="btnNoValidate"
           value="Non-validating Submit">
</form>
````

可以使用JS来设置这个值:
````JS
document.forms[0].elements["btnNoValidate"].formNoValidate = true;
````

## 选择框编程
选择框是使用`<select>`和`<option>`元素创建的.

为方便交互,`HTMLSelectElement`类型在所有表单字段的公共能力之外又提供了以下属性和方法:
- `add(newOption, relOption)`:在`relOption`之前向控件中添加新的`<option>`.
- `multiple`:布尔值,表示是否允许多选,等价于HTML的`multiple`属性.
- `options`:控件中所有`<option>`元素的`HTMLCollection`.
- `remove(index)`:移除给定位置的选项.
- `selectedIndex`:选中项基于0的索引值,如果没有选中项则为-1.对于允许多选的列表,始终是第一个选项的索引.
- `size`:选择框中可见的行数,等价于`HTML`的`size`属性.

选择框的`type`属性可能是`"select-one"`或`"select-multiple"`.

当前选中项根据以下规则决定选择框的`value`属性:
- 如果没有选择项,则选择框的值是空字符串.
- 如果有一个选中项,且其`value`属性有值,则选择框的值就是选中项`value`属性的值.即使`value`属性的值是空字符串也是如此.
- 如果有一个选中项,且其`value`属性没有指定值,则选择框的值是该项的文本内容.
- 如果有多个选中值,则选择框的值根据前两条规则取得第一个选中项的值.

````HTML
<select name="location" id="selLocation">
    <option value="JS">j</option>   <!-- "JS" -->
    <option value="">a</option>     <!-- "" -->
    <option>b</option>              <!-- "b" -->
</select>
````

每个`<option>`元素在DOM中都由一个`HTMLOptionElement`对象表示.`HTMLOptionElement`类型又拥有以下属性:
- `index`:选项在`options`集合中的索引.
- `label`:选项的标签,等价于HTML的`label`属性.
- `selected`:布尔值,表示是否选中了当前选项.把这个属性设置为`true`会选中当前选项.
- `text`:选项的文本.
- `value`:选项的值(等价于HTML的`value`属性).当不存在时,返回`text`的值(IE8之前会返回空字符串).

这只是为了方便而存在这些属性,使用常规的DOM也可以实现读取这些信息,但是效率更低,因此能使用上面的属性就不要使用DOM方法.也不推荐使用DOM的方法修改`<option>`的文本和值.

此外,选择框会在选中一项是立即触发`change`事件,而非在字段失去焦点时触发.

### 选项处理

对于只允许选择一项的选择框,获取选项最简单的方式是选择框的`selectedIndex`属性:
````JS
let selectedOption = selectbox.options[selectbox.selectedIndex];
````

而多选选择框,`selectedIndex`只会返回第一项,且修改`selectedIndex`会移除其他所有选项,只选择指定的项.

可以通过访问每个选项的`selected`来判断该项是否被选中.此外,在多选选择框中,修改`selected`不会影响其他选项.在单选选择框中,将一项设定为`true`会将其他项移除,设定为`false`则对其他项没有影响.

### 添加选项
可以使用JS动态创建选项并将它们添加到选择框.

可以使用DOM方法:
````JS
let newOption = document.createElement("option");
newOption.appendChild(document.createTextNode("Option text"));
newOption.setAttribute("value", "Option value");
// 上面的三行代码也可以使用Option的构造函数创建,其接收两个参数:text和value.其中,value是可选的.
// let newOption = new Option("Option text", "Option value");
selectbox.appendChild(newOption);
````

除了使用`appendChild()`,还可以使用选择框的`add()`方法.该方法接收两个参数:要添加的新选项和要添加到其前面的参考选项.如果想添加选项到选择框末尾,那么第二个参数应该是`null`.由于IE8中想要添加到选择框末尾,必须不传入参数,所以为了兼容,可以向第二个参数传递`undefined`.

例如:
````JS
let newOption = new Option("Option text", "Option value");
selectbox.add(newOption, null);
````

### 移除选项
可以使用DOM的`removeChild()`方法并传入要移除的选项:
````JS
selectbox.removeChild(selectbox.options[0]);    // 移除第一项
````

第二种方式是使用选择框的`remove()`方法.这个方法接收一个参数,即要移除选项的索引:
````JS
selectbox.remove(0);
````

也可以直接将选项设置为等于`null`:
````JS
selectbox.options[0] = null;
````

要清除所有选项,可以这么写:
````JS
function clearSelectbox(selectbox) {
    for (let option of selectbox.options) {
        selectbox.remove(0);    // 因为移除第一项会自动将所有选项向前移一位,所以这样就可以移除所有选项
    }
}
````

### 移动和重排选项
使用DOM从一个选择框将一个选项移动到另一个选择框时,只要对相应的选项使用`appendChild()`(或`insertBefore()`)方法即可.因为对于已经存在于DOM树的结点,调用`appendChild()`会将结点先移出DOM树,然后再插入指定位置:
````JS
let selectbox1 = document.getElementById("selLocations1");
let selectbox2 = document.getElementById("selLocations2");
selectbox2.appendChild(selectbox1.options[0]);
````

重排也是一样:
````JS
let optionToMove = selectbox.options[1];
selectbox.insertBefore(optionToMove,
                       selectbox.options[optionToMove.index - 1]);
// 将一个选项在选择框中前移一个位置
// options超出索引范围会返回null,所以如果是第一个选项会导致insertBefore()的第二参数为null,会插入到最后一个
````

## 表单序列化
表单在JS中可以使用表单字段的`type`属性连同其`name`属性和`value`属性来进行序列化.

浏览器如何确定在提交表单时要把什么发送到服务器:
- 字段名和值是URL编码的并以和号(&)分隔.
- 禁用字段不会发送.
- 复选框或单选按钮只在被选中时才发送.
- 类型为`"reset"`或`"button"`的按钮不会发送.
- 多选字段的每个选中项都有一个值.
- 通过点击提交按钮提交表单时,会发送该提交按钮;否则,不会发送提交按钮.类型为`"image"`的`<input>`元素视同提交按钮.
- `<select>`元素的值是被选中`<option>`元素的`value`属性.如果`<option>`元素没有`value`属性,则该值是它的文本.

所谓序列化,就是使用JS模拟浏览器发送到服务器的内容.表单序列化通常不包含任何按钮,因为序列化得到的字符串很可能以其他方式提交.除此以外其他规则都应该遵循.

表单序列化代码如下:
````JS
// 返回查询字符串格式
function serialize(form) {
    let parts = [];
    let optValue;
    for (let field of form.elements) {
        switch (field.type) {
            case "select-one":
            case "select-multiple":
                if (field.name.length) {    // 排除没有名字的字段
                    for (let option of field.options) {
                        if (option.selected) {
                            if (option.hasAttribute) {
                                optValue = (option.hasAttribute("value") ?
                                            option.value : option.text);
                            } else {    // 兼容IE8
                                optValue = (option.attributes["value"].specified ?
                                            option.value : option.text);
                            }
                            parts.push(`${encodeURIComponent(field.name)}` + "=" +
                                       `${encodeURIComponent(optValue)}`);
                        }
                    }
                }
                break;
            case undefined: // 字段集`<fieldset>`元素
            case "file":    // 文件输入
            case "submit":  // 提交按钮
            case "reset":   // 重置按钮
            case "button":  // 自定义按钮
                break;
            case "radio":   // 单选按钮
            case "checkbox":    // 复选框
                if (!field.checked) {
                    break;
                }
            default:
                if (field.name.length) {    // 排除没有名字的表单字段
                    parts.push(`${encodeURIComponent(field.name)}=` +
                               `${encodeURIComponent(field.value)}`);
                }
        }
    }
    return parts.join("&");
}
````

## 富文本编辑
`<iframe>`允许将另一个HTML文件嵌入其中.通过其JS属性`designMode`,可以让这个嵌入页面(`<body>`)可编辑.`designMode`属性有两个可能的值:`"off"`(默认值)和`"on"`.设置为`"on"`时,整个文档都会变成可以编辑的(显示插入光标).也可以像使用文字处理程序一样编辑文本,通过键盘将文本标记为粗体,斜体等.

例如:
````HTML
<iframe name="richedit" style="height: 100px; width: 100px;"></iframe>
<!-- 可以使用src属性指定显示的URL -->
````
````JS
// window.frames返回所有的直接子窗口
frames["richedit"].document.designMode = "on";
````

### 使用contenteditable
给元素指定HTML枚举属性`contenteditable`,可以让元素可以被用户编辑,即使没有`<iframe>`和JavaScript.

其属性值必须为下面值之一:
- `true`或空字符串,表示元素是可编辑的.
- `false`表示元素不是可编辑的.
- `plaintext-only`表示元素的原始文本是可编辑的,但富文本格式会被禁用.

例如:
````HTML
<div class="editable" id="richedit" contenteditable></div>
<!-- contenteditable后面什么也没有,所以被视作是空字符串 -->
````

也可以使用元素的JS属性`contentEditable`来设置元素的可编辑状态:
````JS
div.contentEditable = "true";
````

*访问伪URL`data:text/html,<html contenteditable>`可以把浏览器窗口转换为一个记事本.*

### 与富文本交互
**`document.execCommend()`已弃用**

与富文本编辑器交互的主要方法是使用`document.execCommand()`.这个方法在文档上执行既定的命令,可以实现大多数格式化任务.`document.execCommand()`可以接收3个参数:要执行的命令,表示浏览器是否为命令提供用户界面的布尔值和执行命令必需的值(如果不需要则为`null`).

可用的命令详见:[MDN-execCommand](https://developer.mozilla.org/zh-CN/docs/Web/API/Document/execCommand#%E5%91%BD%E4%BB%A4)

例如:
````JS
// 在内嵌窗格中为内容添加<h1>标签
frames["richedit"].document.execCommand("formatblock", false, "<h1>");
// 为页面中添加了contenteditable属性的元素创建指向www.example.com的链接
document.execCommand("createlink", false, "https://www.example.com");
````

**`queryCommandEnabled()`已弃用**

使用`document.queryCommandEnabled()`可以确定对当前选中文本或光标所在位置是否可以执行相关命令.它只接受一个参数,即要检查的命令名.如果可编辑区可以执行该命令就返回`true`,否则返回`false`.

**`queryCommandState()`已弃用**

使用`document.queryCommandState()`可以确定相关命令是否应用到了当前文本选区.例如,要确定当前选区的文本是否为粗体:
````JS
let isBold = frames["richedit"].document.queryCommandState("bold");
````

**`queryCommandValue()`为非标准**
使用`document.queryCommandValue()`可以返回执行命令时使用的值,即`execCommand()`中的第三个参数.

### 富文本选择
*`getSelection()`也可以不使用在富文本当中.*

在内嵌窗格中使用`getSelection()`方法,可以获得富文本编辑器的选区.这个方法暴露在`document`和`window`对象上,返回表示当前选中文本的`Selection`对象.每个`Selection`对象都拥有以下属性:
- `anchorNode`:选区开始的节点.
- `anchorOffset`:在`anchorNode`中,从开头到选区开始跳过的字符数.
- `focusNode`:选区结束的节点.
- `focusOffset`:`focusNode`中包含在选区内的字符数.
- `isCollapsed`:布尔值,表示选区起点和终点是否在同一个地方.
- `rangeCount`:选区中包含的DOM范围数量.

`Selection`提供了以下方法来操作选区:
- `addRange(range)`:把给定的DOM范围添加到选区.
- `collapse(node, offset)`:将选区折叠到给定节点中给定的文本偏移处.
- `collapseToEnd()`:将选区折叠到终点.
- `collapseToStart()`:将选区折叠到起点.
- `containsNode(node)`:确定给定节点是否包含在选区中.
- `deleteFromDocument()`:从文档中删除选区文本.
- `extend(node, offset)`:通过将`focusNode`和`focusOffset`移动到指定值来扩展选区.
- `getRangeAt(index)`:返回选区中指定索引处的DOM范围.
- `removeAllRanges()`:从选区中移除所有DOM范围.这实际上会移除选区,因为选区中至少要包含一个范围.
- `removeRange(range)`:从选区中移除指定的DOM范围.
- `selectAllChildren(node)`:清除选区并选择给定节点的所有子节点.
- `toString()`:返回选区中的文本内容.

使用例:
````JS
let selection = frames["richedit"].getSelection();
let range = getRangeAt(0);
let span = frames["richedit"].document.createElement("span");
span.style.backgroundColor = "yellow";
range.surroundContents(span);
````

### 通过表单提交富文本
因为富文本编辑是在内嵌窗格中或通过为元素指定`contenteditable`属性实现的,而不是在表单控件中实现,所以富文本编辑技术上与表单没有关系.这意味着要把富文本编辑的结果提交给服务器,必须手动提取HTML并自己提交.通常的解决方案是在表单中添加一个隐藏字段,使用内嵌窗格或`contenteditable`元素的HTML更新它的值:
````JS
form.addEventListener("submit", (event) => {
    let target = event.target;
    target.elements["comments"].value = frames["richedit"].document.body.innerHTML;
});
````

# JavaScript API
## Atomics与SharedArrayBuffer
多个上下文访问`SharedArrayBuffer`时,如果同时对缓冲区执行操作,就可能出现资源争用问题.`Atomics API`通过强制同一时刻只能对缓冲区执行一个操作,可以让多个上下文安全地读写一个`SharedArrayBuffer`.

### SharedArrayBuffer
`SharedArrayBuffer`与`ArrayBuffer`具有相同的API,两者的主要区别是`ArrayBuffer`必须在不同执行的上下文间切换,`SharedArrayBuffer`则可以被任意多个执行上下文同时使用.

多个执行上下文间共享内容意味着并发线程操作成为了可能,但会导致资源竞争:
````JS
const workerScript = `
self.onmessage = ({data}) => {
    const view = new Uint32Array(data);
    for (let i = 0; i < 1E6; ++i) {
        // 线程不安全加操作会导致资源竞争
        view[0] += 1;
    }
    self.postMessage(null);
};
`;
const workerScriptBlobUrl = URL.createObjectURL(new Blob([workerScript]));
const workers = [];
for (let i = 0; i < 4; ++i) {
    workers.push(new Worker(workerScriptBlobUrl));
}
let responeCount = 0;
for (const worker of workers) {
    workers.onmessage = () => {
        if (++responseCount == workers.length) {
            console.log(`Final buffer value: ${view[0]}`);
        }
    };
}
const sharedArrayBuffer = new SharedArrayBuffer(4);
const view = new Uint32Array(sharedArrayBuffer);
view[0] = 1;
for (const worker of workers) {
    worker.postMessage(sharedArrayBuffer);
}
// (期待结果为4000001)
// 可能的结果:
// Final buffer value: 2145106
````

### 原子操作基础

/// TODO

## 跨上下文消息
跨文档消息,有时候也简称为XDM(cross-document messaging),是一种在不同执行上下文(如不同工作线程或不同源的页面)间传递信息的能力.

XDM的核心是`postMessage()`方法,处理XDM,这个方法名还在HTML5中存在,但目的都一样,都是把数据传送到另一个位置.

`postMessage()`方法接收3个参数:消息,表示目标接收源的字符串(非常重要,用于限制浏览器交付数据的目标)和可选的可传输对象的数组(只与工作线程相关):
````JS
let iframeWindow = document.getElementById("myframe").contentWindow;
iframeWindow.postMessage("A secret", "https://www.example.com");
````

上面的第二个代码向内嵌窗格中发送一条信息,而且指定了源必须是`"https://www.example.com"`.如果源匹配,那么信息将会交付到窗格;否则,`postMessage()`什么也不做.这个限制可以保护消息不会因地址改变而泄露.如果不想限制接收的目标,则第二个参数可以传递`"*"`.

接收到XMD消息后,`window`对象上会触发`message`事件,这个事件是异步触发的,因此从消息发出到消息接收(接收窗口触发`message`事件)可能有延迟.传给`onmessage`事件处理程序的`event`对象(`MessageEvent`类型)包含以下额外属性:
- `data`:作为第一个参数传递给`postMessage()`的字符串数据.
- `origin`:发送消息的文档源,例如`"https://www.example.com"`
- `source`:发送消息的文档中`window`对象的代理.这个代理对象主要用于发送上一条消息的窗口中执行`postMessage`.如果发送窗口有相同的源,那么这个对象应该就是`window`对象.

借助`origin`,可以保证数据来自正确的地方:
````JS
window.addEventListener("message", (event) => {
    if (event.origin == "https://www.example.com") {
        processMessage(event.data);
        event.source.postMessage("Received", "https://somewhere.com");
    }
});
````

大多数情况下,`source`是某个`window`对象的代理,而非实际的`window`对象.因此不能通过它访问窗口下的信息.最好只使用`postMessage()`,这个方法永远存在且可以调用.

第一个参数如果不是字符串,会被[结构化克隆算法](https://developer.mozilla.org/zh-CN/docs/Web/API/Web_Workers_API/Structured_clone_algorithm)序列化.也可以使用`JSON.stringify()`类型转换为字符串,然后在`onmessage`事件处理程序中调用`JSON.parse()`.

## Encoding API
`Encoding API`主要用于实现字符串与定型数组之间的转换.规范新增了4个用于执行转换的全局类:`TextEncoder`,`TextEncoderStream`,`TextDecoder`和`TextDecoderStream`.

### 文本编码
`Encoding API`提供了两种将字符串转换为定型二进制格式的方法:批量编码和流编码.把字符串转换为定型数组,编码器始终使用`UTF-8`.

#### 批量编码
所谓批量,指的是JS引擎会同步编码整个字符串.对于比较长的字符串,可能会花较长时间.批量编码是通过`TextEncoder`的实例完成的.

该实例上有一个`encode()`方法,该方法接收一个字符串参数,并以`Uint8Array`格式返回每个字符的UTF-8编码:
````JS
const textEncoder = new TextEncoder();
const decodedText = 'foo';
const encodedText = textEncoder.encode(decodedText);
// f的UTF-8编码是0x66(102)
// o的UTF-8编码是0x6F(111)
console.log(encodedText);   // Uint8Array(3) [102, 111, 111]
````

编码器实例还有一个`encodeInto()`方法,该方法接收一个字符串和目标`Uint8Array`(传入其他类型会抛出错误),返回一个字典(普通的`Object`),该字典包含`read`和`written`属性,分别表示成功从源字符串读取了多少字符和向目标数组写入了多少字符.如果空间不够,编码就会提前终止,返回的字典就会体现这个结果,该方法比`encode()`更加高效:
````JS
const textEncoder = new TextEncoder();
const fooArr = new Uint8Array(3);
const barArr = new Uint8Array(2);
const fooRes = textEncoder.encodeInto('foo', fooArr);
const barRes = textEncoder.encodeInto('bar', barArr);
console.log(fooArr);    // UintArray(3) [102, 111, 111]
console.log(fooRes);    // { read: 3, written: 3 }
console.log(barArr);    // UintArray(2) [98, 97]
console.log(barRes);    // { read: 2, written: 2 }
````

#### 流编码
`TextEncoderStream`其实就是`TransformStream`形式的`TextEncoder`.将解码后的文本流通过管道输入流编码器会得到编码后文本块的流:
````JS
async function* chars() {
    const decodedText = 'foo';
    for (let char of decodedText) {
        yield await new Promise((resolve) => setTimeout(resolve, 1000, char));
    }
}

const decodedTextStream = new ReadableStream({
    async start(controller) {
        for await (let chunk of chars()) {
            controller.enqueue(chunk);
        }
        controller.close();
    }
});

const encodedTextStream = decodedTextStream.pipeThrough(new TextEncoderStream());
const readableStreamDefaultReader = encodeTextStream.getReader();

(async function() {
    while (true) {
        const { done, value } = await readableStreamDefaultReader.read();
        if (done) {
            break;
        } else {
            console.log(value);
        }
    }
})();
// Uint8Array[102]
// Uint8Array[111]
// Uint8Array[111]
````

### 文本编码
`Encoding API`提供了两种将定型数组转换为字符串的方式:批量解码和流解码.与编码器类不同,在将定性数组转换为字符串是,编码器支持非常多的字符串编码.默认字符编码是UTF-8.

#### 批量解码
批量解码是通过`TextDecoder`的实例完成的:

这个实例上有一个`decode()`方法,该方法接收一个定型数组参数,返回解码后的字符串:
````JS
const textDecoder = new TextDecoder();
const encodedText = Uint8Array.of(102, 111, 111);
const decodedText = textDecoder.decode(encodedText);
console.log(decodedText);   // foo
````

即使传入的不是`Uint8Array`也没有关系,解码只会关心整个二进制表示.

想要使用其他解码可以在构造函数中传入编码格式:
````JS
const textDecoder = new TextDecoder('utf-16');
````

#### 流解码
`TextDecoderStream`是`TransformStream`形式的`TextDecoder`.将编码后的文本流通过管道输入流解码器会得到解码后的文本块的流:
````JS
async function* chars() {
    const encodedText = [102, 111, 111].map((x) => Uint8Array.of(x));
    for (let char of encodedText) {
        yield await new Promise((resolve) => setTimeout(resolve, 1000, char));
    }
}
const encodedTextStream = new ReadableStream({
    async start(controller) {
        controller.enqueue(chunk);
    }
    controller.close();
});

const decodedTextStream = encodedTextStream.pipeThrough(new TextDecoderStream());
const readableStreamDefaultReader = decodedTextStream.getReader();

(async function() {
    while (true) {
        const { done, value } = await readableStreamDefaultReader.read();

        if (done) {
            break;
        } else {
            console.log(value);
        }
    }
})();
// f
// o
// o
````

文本编码器能够识别可能分散在不同块上的代理对.解码器流会保持块片段直到取得完整的字符.

文本解码器流经常与`fetch()`一起使用,因为响应体可以作为`ReadableStream`来处理:
````JS
const response = await fetch(url);
const stream = response.body.pipeThrough(new TextDecoderStream());
const decodedStream = stream.getReader();
for await (let decodedChunk of decodedStream) {
    console.log(decodedChunk);
}
````

## File API与Blob API
`File API`与`Blob API`是为了让Web开发者能以安全的方式访问客户端机器上的文件,从而更好地与这些文件交互而设计.

### File类型
`File API`仍然以表单中的文件输入字段为基础,但是增加了直接访问文件信息的能力.HTML5在DOM上为文件输入元素添加了`files`集合.当用户在文件字段中选择一个或多个文件时,这个`files`集合中会包含一组`File`(继承自`Blob`)对象,表示选中的文件.每个`File`对象都有一些只读属性:
- `name`:本地系统中的文件名
- `size`:以字节计的文件大小
- `type`:包含文件MIME类型的字符串
- `lastModifiedDate`:表示文件最后修改时间的字符串

可以监听`change`事件然后遍历`files`集合可以取得每个选中文件的信息:
````JS
let filesList = document.getElementById("files-list");
filesList.addEventListener("change", (event) => {
    let files = event.target.files,
        i = 0,
        len = files.length;
    while (i < len) {
        const f = files[i];
        console.log(`${f.name}, ${f.size} bytes`);
        i++;
    }
});
````

### FileReader类型
`FileReader`类型表示一种异步文件读取机制.`FileReader`类型提供了几个读取文件数据的方法:
- `readAsText(file, encoding)`:从文件中读取纯文本内容并保存在对象的`result`属性中.第二个参数表示编码,是可选的.
- `readAsDataURL(file)`:读取文件并将内容的数据URI保存在`result`属性中.
- `readAsBinaryString(file)`:读取文件并将二进制数据保存在`result`属性中.
- `readAsArrayBuffer(file)`:读取文件并将文件内容以`ArrayBuffer`形式保存在`result`属性中.

例如,为了向用户显示图片,可以将图片读取为数据URI,而为了解析文本内容,可以将文件读取为文本.

这些方法是异步的,每个`FileReader`会发布几个事件,包括:`progress`,`error`和`load`.

`progress`事件(`ProgressEvent`类型)在文件读取时每50毫秒触发一次,其包含`lengthComputable`,`loaded`和`total`属性.此外,也可以读取未完成的`FileReader`的`result`属性,即使其中尚未包含全部数据.

`error`事件会在由于某种原因无法读取文件时触发.触发`error`事件时,`FileReader`的`error`属性会包含错误信息.这个属性是一个对象,只包含一个属性:`code`.这个错误码的值可能是`1`(未找到文件),`2`(安全错误),`3`(读取被中断),`4`(文件不可读),`5`(编码错误).

`load`事件会在文件成功加载后触发.如果`error`事件被触发,则不会再触发`load`事件.

如果想提前结束文件读取,则可以在过程中调用`abort()`方法,从而触发`abort`事件.在`load`,`error`或`abort`事件触发后,还会触发`loadend`事件.该事件表示在上述3种情况下,所有读取操作都已经结束.

### FileReaderSync类型
`FileReaderSync`类型是`FileReader`的同步版本.这个类型拥有与`FileReader`相同的方法,只有在整个文件加载到内存之后才会继续执行.`FileReaderSync`只在工作线程中可用,因为如果读取整个文件耗时太长则会影响全局.

### Blob与部分读取
某些情况下,可能需要读取部分文件而不是整个文件,为此,需要使用`File`对象的`slice()`方法,这个方法接收两个参数,起始的字节和要读取的字节数.这个方法返回一个`Blob`实例.

`Blob`表示二进制大对象,是JS对不可修改二进制数据的封装类型.包含字符串的数组,`ArrayBuffers`,`ArrayBufferViews`,甚至其他`Blob`都可以用来创建`Blob`实例.`Blob`构造函数可以接收一个`options`参数,并在其中指定`MIME`类型:
````JS
console.log(new Blob(['foo']));
// Blob {size: 3, type: ""}
console.log(new Blob(['{"a": "b"}'], {type: 'application/json'}));
// Blob {size: 10, type: "application/json"}
console.log(new Blob(['<p>Foo</p>', '<p>Bar</p>'], {type: "text/html"}));
// Blob {size: 20, type: "text/html"}
````

`Blob`对象有一个`size`属性和一个`type`属性,还有一个`slice()`方法用于进一步切分数据.另外也可以使用`FileReader`从`Blob`中读取数据:
````JS
let filesList = document.getElementById("files-list");
fileList.addEventListener("change", (event) => {
    let files = event.target.files,
        reader = new FileReader(),
        blob = blobSlice(files[0], 0, 32);
    if (blob) {
        reader.readAsText(blob);
        reader.onload = function() {
            output.innerHTML = reader.result;
        }
    }
})
````

#### 对象URL与Blob
对象URL有时候也称作Blob URL,是指引用存储在`File`或`Blob`中数据的URL.对象URL的优点是不用把文件内容读取到JS也可以使用文件.只要在适当位置提供对象URL即可.要创建对象URL,可以使用`window.URL.createObjectURL()`方法并传入`File`或`Blob`对象.这个函数返回的值是一个指向内存中地址的字符串.因为这个字符串是URL,所以可以在DOM中直接使用:
````JS
let files = document.getElementById("files-list").files,
    url = window.URL.createObjectURL(files[0]);
if (url && /image/.test(files[0].type)) {
    output.innerHTML = `<img src=${url}>`;
}
````

使用完数据之后,最好能释放与之关联的内存.只要对象URL在使用中,就不能释放内存.如果想表明不再使用某个对象URL,则可以把它传给`window.URL.revokeObjectURL()`以释放与之关联的内存.页面卸载时会自动释放对象URL占用的内存.

### 读取拖放文件
在页面上创建放置目标后,可以从桌面上把文件拖放并放到放置目标.这样会像拖放图片或链接一样触发`drop`事件.被放置的文件可以通过事件的`event.dataTransfer.files`属性读到,这个属性保存着一组`File`对象:
````JS
let droptarget = document.getElementById("droptarget");
function handleEvent(event) {
    let files, i, len;
    event.preventDefault();
    if (event.type == "drop") {
        files = event.dataTransfer.files;
        i = 0;
        len = files.length;
        while (i < len) {
            console.log(`${files[i].name}  ${files[i].type}, ${files[i].size} bytes`);
            i++;
        }
    }
}
droptarget.addEventListener("dropenter", handleEvent);
droptarget.addEventListener("dropover", handleEvent);
droptarget.addEventListener("drop", handleEvent);
````

## 媒体元素
`<audio>`和`<video>`为浏览器提供了嵌入音频和视频的统一解决方案.

详见[HTML-audio](../HTML/get_start.md#audio)和[HTML-video](../HTML/get_start.md#video)

### 属性
`<video>`和`<audio>`元素提供了JS接口.这两个元素有很多共有属性(`HTMLMediaElement`实例,`HTMLVideoElement`和`HTMLAudioElement`都继承它),可以用于确定媒体的当前状态:
- `autoplay`:`Boolean`.取得或设置HTML`autoplay`标签.
- `buffered`:`TimeRanges`对象.表示已下载缓冲的时间范围.
- `bufferedBytes`**(未查到)**:`ByteRanges`对象.表示已下载缓冲的字节范围.
- `bufferingRate`**(未查到)**:`Integer`:平均每秒下载的位数.
- `bufferingThrottled`**(未查到)**:`Boolean`.表示缓冲是否被浏览器截流.
- `controls`:`Boolean`.取得或设置HTML`controls`属性.
- `currentLoop`:`Integer`.媒体已经播放的循环次数.
- `currentSrc`:`String`.当前播放媒体的URL.
- `currentTime`:`Float`.已经播放的秒数.
- `defaultPlaybackRate`:`Float`.取得或设置默认播放速率.默认为`1.0`秒.
- `duration`:`Float`.媒体的总秒数.
- `ended`:`Boolean`.表示媒体是否播放完成.
- `loop`:`Boolean`.取得或设置媒体是否应该在播放完成再循环开始.
- `muted`:`Boolean`.取得或设置媒体是否静音.
- `networkState`:`Integer`.表示媒体当前网络状态.`0`表示空,`1`表示加载中,`2`表示加载元数据,`3`表示加载了第一帧,`4`表示加载完成.
- `paused`:`Boolean`.表示播放器是否暂停.
- `playbackRate`:`Float`.取得或设置当前播放速率.将`playbackRate`设为负值**不可以**实现倒播.用户可以调整该属性而无法调整`defaultPlaybackRate`.
- `played`:`TimeRanges`.到目前为止已经播放的时间范围.
- `readyState`:`Integer`.表示媒体是否已经准备就绪.`0`表示媒体不可用,`1`表示可以显示当前帧,`2`表示媒体可以开始播放,`3`表示媒体可以从头播到尾.
- `seekable`:`TimeRanges`.可以跳转的时间范围.
- `seeking`:`Boolean`.表示播放器正在移动到媒体文件的新位置.
- `src`:`String`.媒体文件源.可以在任何时候重写.
- `start`:`Float`.取得或设置媒体文件中的位置,以秒为单位,从该处开始播放
- `totalBytes`:`Integer`.资源需要的字节总数(如果知道的话).
- `videoHeight`(`HTMLVideoElement`):`Integer`.返回视频(不一定是元素)的高度.
- `videoWidth`(`HTMLVideoElement`):`Integer`.返回视频(不一定是元素)的宽度.
- `volume`:`Float`.取得或设置当前音量,值为`0.0`到`1.0`.

### 事件
媒体元素包含以下事件:
- `abort`:下载被中断.
- `canplay`:播放可以开始,但未完全缓冲,`readyState`为`2`.
- `canplaythrough`:播放可以开始,且已经完全缓冲,`readyState`为`3`.
- `canshowcurrentframe`**(未查到)**:已经下载当前帧,`readyState`为`1`.
- `dataunavailable`**(未查到)**:不能播放,因为没有数据,`readyState`为`0`.
- `durationchange`:`duration`属性的值发生变化.
- `emptied`:网络连接关闭了.
- `empty`:发生了错误,阻止媒体下载.
- `ended`:媒体已经播放完,且停止了.
- `error`:下载期间发生了网络错误.
- `loadeddata`:媒体的第一帧已经下载.
- `loadedmetadata`:媒体的元数据已经下载.
- `loadstart`:下载已经开始.
- `pause`:播放已经暂停
- `play`:媒体已经收到开始播放的请求.
- `playing`:媒体已经实际开始播放了.
- `progress`:下载中.
- `ratechange`:媒体播放速率发生变化.
- `seeked`:跳转已结束.
- `seeking`:播放已移动到新位置.
- `stalled`:浏览器尝试下载,但尚未收到数据.
- `timeupdate`:`currentTime`被非常规或意外地更改了.
- `volumechange`:`volume`或`muted`属性值发生了变化.
- `waiting`:播放暂停,以下载更多数据.

### 自定义媒体播放器
使用`<audio>`和`<video>`的`play()`和`pause()`方法,可以手动控制媒体文件的播放.综合使用属性,事件和这些方法,可以方便地创建自定义的媒体播放器.

(不过还是建议从现成的代码直接修改)

### 检测编解码器
不是所有浏览器都支持`<video>`和`<audio>`的所有编解码器,这通常意味着必须提供多个媒体源.为此,也有JS API可以用来检测浏览器是否支持给定格式和编解码器.这两个媒体元素都有一个名为`canPlayType()`的方法,该方法接收一个格式/编解码器字符串,返回一个字符串值:`"probably"`,`"maybe"`或`""`,其中空字符串就是假值,因此可以在条件判断中直接使用:
````JS
if (audio.canPlayType("audio/mpeg")) {
    // ...
}
````
最有可能返回的值是`"maybe"`和`""`.这是因为文件实际上只是一个包装音频和视频的容器,而真正决定文件是否可以播放的是编码.在同时提供MIME类型和编解码器的情况下,返回值的可能性会提高到`"probably"`:
````JS
if (audio.canPlayType("audio/ogg; codecs=\"vorbis\"")) {
    // ...
}
````
注意:编解码器必须放到引号中.

### 音频类型
`<audio>`元素还有一个名为`Audio`的原生JS构造函数,支持在任何时候播放音频.`Audio`实例不需要插入文档即可工作.

可选的`url`参数传入指定的音频源文件的URL:
````JS
let audio = new Audio("sound.mp3");
audio.addEventListener("canplaythrough", (event) => {
    event.target.play();
});
````

## 原生拖放
- [MDN-HTML 拖放 API](https://developer.mozilla.org/zh-CN/docs/Web/API/HTML_Drag_and_Drop_API)
- [MDN-拖拽操作](https://developer.mozilla.org/zh-CN/docs/Web/API/HTML_Drag_and_Drop_API/Drag_operations)

拖放可以跨窗格,跨浏览器容器,甚至跨应用程序拖动元素.

### 可拖动能力
默认情况下,图片,链接和文本是可拖动的,这意味着无须额外代码用户就可以拖动它们.文本只有在被选中后才可以拖动,而图片和链接在任意时候都是可以拖动的.

也可以使用`HTML`的*枚举*属性(**不是**布尔属性)`draggable`让其他元素变得可以拖动.设置为`"true"`表示可以拖动,`"false"`表示不能拖动.图片和链接的`draggable`属性默认为`"true"`,而其他元素默认为`"false"`.

````HTML
<img src="smile.gif" draggable="false">
<div draggable="true">...</div>
````

### 拖动事件
在某个事件被拖动时,会(按顺序)触发以下事件:
- `dragstart`
- `drag`
- `dragend`

在按住鼠标键不放并开始移动鼠标的那一刻,被拖动元素上会触发`dragstart`事件.此时光标会变成非放置符号(圆环中间一条斜杠),表示元素不能放到自身上.`dragstart`事件触发后,只要目标还被拖动就会持续触发`drag`事件(即使鼠标不移动也会不断触发).当拖动停止时(把元素放到有效或无效放置目标上),会触发`dragend`事件.

上述3个事件的目标都是被拖动的元素.默认情况下,浏览器在拖动开始后不会改变被拖动元素的外观.不过,大多数浏览器此时会创建元素的一个半透明副本,始终跟随在光标下方.

在把元素拖动到一个有效的放置目标上时,放置目标会依次触发以下事件:
- `dragenter`
- `dragover`
- `dragleave`或`drop`

只要一把元素拖动到放置目标上,`dragenter`事件就会触发.`dragenter`事件触发后,会立即触发`dragover`事件,并且在元素在放置目标范围内被拖动期间此事件会持续触发.当元素被拖动到放置目标之外,`dragover`停止触发,`dragleave`事件触发.如果被拖动元素被放到目标上,则会触发`drop`事件而不是`dragleave`事件.这些事件的目标时放置目标元素.

### 自定义放置目标
在把某个元素拖动到无效放置目标上时,光标会显示为禁止.即使所有元素都支持放置目标事件,这些元素默认也是不允许放置的.但可以通过覆盖`dragenter`和`dragover`事件的默认行为,可以把任何元素转换为有效的放置目标.此时,元素上就可以触发`drop`事件.

无效放置目标的放置事件的默认行为是导航到放在放置目标上的URL.要阻止这个行为,需要取消`drop`事件的默认行为.

````HTML
<p id="dragfrom" draggable="true">This text <strong>may</strong> be dragged.</p>
<div id="myDiv" style="height: 100px; width: 100px; background-color: blue;"></div>
````

````JS
let dragfrom = document.getElementById("dragfrom");
let dragto = document.getElementById("myDiv");
dragto.addEventListener("dragover", (event) => {
    event.preventDefault();
});
dragto.addEventListener("dragenter", (event) => {
    event.preventDefault();
});
dragto.addEventListener("drop", (event) => {
    event.preventDefault();
})
````

### dataTransfer对象
除非数据受影响,否则简单的拖放并没有实际意义.为实现拖放操作中的数据传输,可以使用`event`对象(属于`DragEvent`,继承自`MouseEvent`)的`dataTransfer`属性(`DataTransfer`类型).该属性是一个对象,包含两个主要方法:`getData()`和`setData()`.`getData()`用于获取`setData()`存储的值.`setData()`的第一个参数以及`getData()`的唯一参数是一个字符串,表示要设置的数据类型:`"text/plain"`(`"text"`以兼容旧版)或`"text/uri-list"`(`"URL"`以兼容旧版)(也可以是其他MIME类型?).`setData()`的第二个参数是一个字符串,表示要存储的数据.

可以同时存储`text`和`URL`(和其他MIME类型),不会相互覆盖.如果没有在`drop`事件中获取这些数据,`dataTransfer`对象就会被销毁,数据也会丢失.

在从文本框拖动文本时,浏览器会自动调用`setData()`并将文本以`text`格式存储起来.当拖动链接或图片时,浏览器会调用`setData()`并以`URL`的形式储存起来.

以`URL`形式存储时,放在浏览器空白处可能会导航到该URL.

`getData()`读取失败会返回一个空字符串.
````JS
let url = event.dataTransfer.getData("url");
````

### dropEffect与effectAllowed
`dataTransfer`对象不仅可以用于实现简单的数据传输,还可以用于确定能够对被拖放元素和放置目标执行什么操作.为此,可以使用`dropEffect`和`effectAllowed`.

`dropEffect`属性可以告诉浏览器允许哪种放置行为,这是拖动(放置)目标的限制(结果).这个属性有以下4种可能的值:
- `"none"`:被拖动元素可能不能放到这里.这是除文本框以外所有元素的默认值.(真正是否可以拖放还与`effectAllowed`有关)
- `"move"`:被拖放元素应该移动到放置目标.
- `"copy"`:被拖放元素应该复制到放置目标.
- `"link"`:表示放置目标会导航到被拖动元素(仅在它是URL的情况下).

为了使用`dropEffect`属性,必须在放置目标的`dragenter`事件处理程序中设置它.

`effectAllowed`属性表示对被拖放元素是否允许`dropEffect`,这是拖动元素的限制.这个属性有如下几个可能的值:
- `uninitialized`:没有给被拖放元素设置动作.
- `none`:被拖放元素上没有允许的动作.
- `copy`:只允许`"copy"`这种`dropEffect`.
- `link`:只允许`"link"`这种`dropEffect`.
- `move`:只允许`"move"`这种`dropEffect`.
- `copyLink`:只允许`"copy"`和`"link"`两种`dropEffect`.
- `copyMove`:只允许`"copy"`和`"move"`两种`dropEffect`.
- `linkMove`:只允许`"link"`和`"move"`两种`dropEffect`.
- `all`:允许所有`dropEffect`.

必须在`dragstart`事件处理程序中设置这个属性.

`DataTransfer`还拥有`files`等属性.

### 其他成员
`DataTransfer`还有以下方法:
- `clearData(format)`:清除以特定格式存储的数据.
- `setDragImage(element, x, y)`:允许指定拖动发生时显示在光标下面的图片.这个方法接收3个参数:要显示的HTML元素以及标识光标位置的图片上的x和y坐标.这里的HTML元素可以是一张图片,也可以是其他任何元素,此时显示渲染后的元素.
- `type`:当前存储的数据类型列表.这个集合类似数组,以字符串形式保存数据类型,比如`"text"`.

## Notifications API
`Notifications API`用于向用户显示通知.通知使用JS API触发页面外部的浏览器行为,允许页面处理用户与对话框或弹层的交互.其在`Service Worker`中非常有用.渐进Web应用通过触发通知可以在页面不活跃时向用户显示消息,看起来就像原生应用.

### 通知权限
`Notifications API`有被滥用的可能,因此默认会开启两项安全措施:
- 通知只能在运行安全上下文代码中被触发.
- 通知必须按照每个源的原则明确得到用户允许.

用户授权显示通知是通过浏览器内部的一个对话框完成的.除非用户没有明确给出允许或拒绝的答案,否则这个权限请求对每个域只会出现一次.浏览器会记住用户的选择.

页面可以使用全局对象`Notification`向用户请求通知权限.这个对象有一个`requestPermission()`方法,该方法返回一个期约,用户在授权对话框上执行操作后这个期约会解决.

````JS
Notification.requestPermission().then((permission) => {
    console.log('User responded to permission request:', permission);
});
````

`"granted"`值意味着用户明确授权了显示通知的权限.除此以外的其他值意味着显示通知会静默失败.如果用户拒绝授权,这个值就是`"denied"`.一旦拒绝,就无法通过编程方式挽回,因为不可能再触发授权提示.

### 显示和隐藏通知
`Notification`构造函数用于创建和显示通知.最简单的通知形式是只显示一个标题,这个标题内容可以作为第一个参数传给`Notification`构造函数.可以通过`options`参数(一个`Object`对象)对通知进行自定义,包括设置通知的主体,图片和振动等:
````JS
const n = new Notification('Title text!', {
    body: 'Body text!', // 通知主体
    image: 'path/to/image.png', // 通知图片
    vibrate: true   // 是否振动
});
setTimeout(() => n.close(), 1000);  // 1秒后关闭显示的通知
````
可以使用对象的`close()`方法关闭显示的通知.

### 通知生命周期回调
通知(`Notification`)拥有以下4个事件:
- `show`:在通知显示时触发
- `click`:在通知点击时触发
- `close`:在通知消失或通过`close()`关闭时触发
- `error`:在发生错误阻止通知显示时触发

## Page Visibility API
`Page Visibility API`旨在为开发者提供页面对用户是否可见的信息(页面是否被最小化或隐藏在其他标签后面).

- `document.visibilityState`值,表示以下3种状态之一:
  - `"visible"`:此时页面内容至少是部分可见.即此页面在前景标签页中,并且窗口没有最小化.
  - `"hidden"`:此时页面对用户不可见.即文档处于背景标签页或者窗口处于最小化状态,或者操作系统正处于锁屏状态.
  - `"prerender"`:页面此时正在渲染中,因此是不可见的.文档只能从此状态开始,永远不能从其他值变为此状态.
- `visibilitychange`事件,该事件会在文档从隐藏变可见(或反之)时触发.
- `document.hidden`布尔值 **(后向兼容)**,表示页面是否被隐藏.这意味着页面在后台标签页或浏览器被最小化了.

## Stream API
深入了解流,详见[数据流-权威指南](https://web.dev/articles/streams)

`Stream API`用于消费有序的小信息块.

这种能力主要有两种应用场景:
- 大块信息可能不会一次性都可用.网络请求就是一个典型的例子.流式处理可以让应用在数据已到达就能使用,而不必等到所有数据都加载完毕.
- 大块数据可能需要小部分处理.视频处理,数据压缩,图像编码和JSON解析都是可以分成小部分进行处理,而不必等到所有数据都在内存中时再处理.

### 理解流
提到流,可以把数据想象成某种通过管道输送的液体.JS中的流借用了管道相关的概念,因为原理是相通的.

`Stream API`定义了3种流:
- 可读流:可以通过某个公共接口读取数据块的流.数据在内部从底层源进入流,然后由消费者进行处理.
- 可写流:可以通过某个公共接口写入数据块的流.生产者将数据写入流,数据在内部传入底层数据槽.
- 转换流:由两种流组成,可写流用于接收数据(可写端),可读流用于输出数据(可读流).这两个流之间是转换程序,可以根据需要检查和修改流的内容.

**注意:不是说是可读流接收后传入可写流并处理.可读流和可写流是可以独立存在的.**

#### 块,内部队列和反压
流的基本单位是**块**.块可以是任意数据类型,但通常是定型数组.每个块都是离散的流片段,可以作为一个整体来处理.块不是固定大小的,也不一定按固定间隔到达.在理想的流中,块的大小近似相同,到达间隔近似相等.流可能需要考虑边界情况.

各种类型的流都有入口和出口的概念.有时候,由于进出速率不同,可能会出现不匹配的情况.有以下三种情况:
- 流出口处理数据的速度比入口提供数据的速度快.流出口经常空闲,但只会浪费一点内存或计算资源,因此这是可以接受的.
- 流入和流出均衡.这是理想状态.
- 流入口提供数据的速度比出口处理数据速度快.这种流不平衡是固有的问题.此时一定会在某个地方出现数据积压,流必须响应做出处理.

流为上述第三种情况提供了解决的工具.所有流都会为已进入流但尚未离开流的块提供一个内部队列,用于均衡流.但如果内部队列不断增大,它会使用**反压**,通知流入口停止发送数据,知道队列大小降到某个既定的阈值之下.这个阈值由排列策略决定,这个策略定义了内部队列可以占用的最大内存,即高水位线.

### 可读流
可读流是对底层数据源的封装.底层数据源可以将数据填充到流中,允许消费者通过流的公共接口读取数据.

#### ReadableStreamDefaultController
要让值通过可读流的控制器传入可读流,需要创建一个`ReadableStream`实例,并在构造函数的`underlyingSource`参数(第一个参数)中定义`start()`方法,然后在这个方法中使用作为参数传入的`controller`.默认情况下,这个控制器参数是`ReadableStreamDefaultController`的一个实例,其包含`enqueue()`方法可以把值传入控制器.所有值都传完之后,调用其`close()`关闭流.

示例见下.

#### ReadableStreamDefaultReader
要从队列中读出值,需要`ReadableStreamDefaultReader`的实例,该实例可以通过流的`getReader()`方法获取.调用这个方法会获得流的锁(带锁的`ReadableStreamDefaultReader`实例),保证只有这个读取器可以从流中读取值.然后消费者使用这个读取器实例的`read()`方法可以读出值.

其中`read()`方法返回一个`Promise`,其可能状态如下:
- 如果有分块可用,则`promise`将使用`{ value: theChunk, done: false }`形式的对象来兑现.
- 如果流已经关闭,则`promise`将使用`{ value: undefined, done: true }`形式的对象来兑现.
- 如果流发生错误,`promise`将因相关错误被拒绝.

示例:
````JS
async function* ints() {
    // 每1秒生成一个递增的整数
    for (let i = 0; i < 5; ++i) {
        yield await new Promise((resolve) => setTimeout(resolve, 1000, i));
    }
}
const readableStream = new ReadableStream({
    async start(controller) {
        for await (let chunk of ints()) {
            controller.enqueue(chunk);
        }
        controller.close();
    }
});
console.log(readableStream.locked); // false
const readableStreamDefaultReader = readableStream.getReader(); // 返回的是ReadableStreamDefaultReader的实例
console.log(readableStream.locked); // true

// 消费者
(async function() {
    while (true) {
        const { done, value } = await readableStreamDefaultReader.read();   // 使用对象解构,如果流发生错误,await会立刻结束异步函数
        if (done) {
            break;
        } else {
            console.log(value);
        }
    }
})();
// 0
// 1
// 2
// 3
// 4
````

### 可写流
可写流是底层数据槽的封装.底层数据槽处理通过流的公共接口写入的数据.

#### 创建WritableStream
将值通过可写流的公共接口可以写入流.在传给`WritableStream`构造函数的`underlyingSink`参数(第一个参数)中,通过实现`write()`方法可以获得写入的数据.

示例见下.

#### WritableStreamDefaultWriter
要把获得的数据写入流,可以通过流的`getWriter()`方法获取`WritableStreamDefaultWriter`的实例.这样会获得流的锁,确保只有一个写入器可以向流中写入数据.

在向流中写入数据前,生产者必须确保写入器可以接收值.`writableStreamDefaultWriter.ready`返回一个期约,此期约会在能够向流中写入数据时解决.然后,就可以把值传给`WritableStreamDefaultWriter.write()`方法.写入数据后,调用其`close()`方法将流关闭.

示例:
````JS
async function* ints() {
    for (let i = 0; i < 5; ++i) {
        yield await new Promise((resolve) => setTimeout(resolve, 1000, i));
    }
}
const writableStream = new WritableStream({
    write(value) {
        console.log(value);
    }
});
console.log(writableStream.locked); // false
const writableStreamDefaultWriter = writableStream.getWriter();
console.log(writableStream.locked); // true

// 生产者
(async function() {
    for await (let chunk of ints()) {
        await writableStreamDefaultWriter.ready;
        writableStreamDefaultWriter.write(chunk);
    }
    writableStreamDefaultWriter.close();
})();
````

### 转换流
转换流用于组合可读流和可写流.数据块在两个流之间的转换是通过`transform()`方法完成的.数据进入`TransformStream`对象的可写流写入对象,然后通过可读流从对象中读出.

示例:
````JS
async function* ints() {
    // 每1秒生成一个递增的整数
    for (let i = 0; i < 5; ++i) {
        yield await new Promise((resolve) => setTimeout(resolve, 1000, i));
    }
}
// 通过transform()方法将每个值翻倍
// 返回的TransformStream包含writable和readable,分别表示由TransformStream控制的ReadableStream和WritableStream
const { writable, readable } = new TransformStream({
    transform(chunk, controller) {
        controller.enqueue(chunk * 2);
    }
});
const readableStreamDefaultReader = readable.getReader();
const writableStreamDefaultWriter = writable.getWriter();

// 消费者
(async function() {
    while (true) {
        const { done, value } = await readableStreamDefaultReader.read();   // 使用对象解构,如果流发生错误,await会立刻结束异步函数
        if (done) {
            break;
        } else {
            console.log(value);
        }
    }
})();
// 生产者
(async function() {
    for await (let chunk of ints()) {
        await writableStreamDefaultWriter.ready;
        writableStreamDefaultWriter.write(chunk);
    }
    writableStreamDefaultWriter.close();
})();
````

### 通过管道连接流
流可以通过管道连接成一串.最常见的用例是使用`pipeThrough()`方法把`ReadableStream`接入`TransformStream`.从内部看,`ReadableStream`先把自己的值传给`TransformStream`内部的`WritableStream`,然后执行转换,接着转换后的值又在新的`ReadableStream`上出现.

例如:
````JS
async function* ints() {
    // 每1秒生成一个递增的整数
    for (let i = 0; i < 5; ++i) {
        yield await new Promise((resolve) => setTimeout(resolve, 1000, i));
    }
}
const integerStream = new ReadableStream({
    async start(controller) {
        controller.enqueue(chunk);
    }
    controller.close();
});
const doublingStream = new TransformStream({
    transform(chunk, controller) {
        controller.enqueue(chunk * 2);
    }
});

// 通过管道连接流
const pipedStream = integerStream.pipeThrough(doublingStream);
// 从连接流的输出获得读取器
const pipedStreamDefaultReader = pipedStream.getReader();

// 消费者
(async function() {
    while (true) {
        const { done, value } = await pipedStreamDefaultReader.read();  // 使用对象解构,如果流发生错误,await会立刻结束异步函数
        if (done) {
            break;
        } else {
            console.log(value);
        }
    }
})();
// 0
// 2
// 4
// 6
// 8
````

使用`pipeTo()`方法可以将`ReadableStream`连接到`WritableStream`:
````JS
async function* ints() {
    // 每1秒生成一个递增的整数
    for (let i = 0; i < 5; ++i) {
        yield await new Promise((resolve) => setTimeout(resolve, 1000, i));
    }
}
const integerStream = new ReadableStream({
    async start(controller) {
        controller.enqueue(chunk);
    }
    controller.close();
});
const writableStream = new WritableStream({
    write(value) {
        console.log(value);
    }
});
const pipedStream = integerStream.pipeTo(writableStream);
// 0
// 1
// 2
// 3
// 4
````
这里的管道连接操作隐式从`ReadableStream`获得了一个读取器,并把产生的值填充到`WritableStream`.

## 计时API
`Performance`接口通过JS API暴露了浏览器内部的度量指标(性能).这个接口暴露在`window.performance`对象上.所有与页面相关的指标,包括已经定义和将来会定义的,都会存在于这个对象上.

`Performance`接口由多个API构成:
- `High Resolution Time API`
- `Performance Timeline API`
- `Navigation Timing API`
- `User Timing API`
- `Resource Timing API`
- `Paint Timing API`

### High Resolution Time API
对于`Date`的时间,其精度并不高,而且受系统时间调整的影响.

`High Resolution Time API`定义了`window.performance.now()`,该方法返回一个微秒精度的浮点数.而且这个方法可以保证时间戳单调增长.
````JS
const t0 = performance.now();
const t1 = performance.now();
console.log(t0);    // 1768.625000026077
console.log(t1);    // 1768.6300000059418
const duration = t1 - t0;
console.log(duration);  // 0.004999979864805937
````

该计数器使用相对度量.会在上下文创建时从0开始计时.例如,打开页面或创建工作线程时,`performance.now()`就会从0开始计时.不同上下文之间会存在初始时间差,不能直接比较,但可以使用`performance.timeOrigin`属性返回计时器初始化时全局系统时钟的值.
````JS
const relativeTimestamp = performance.now();
const absoluteTimestamp = performance.timeOrigin + relativeTimestamp;
console.log(relativeTimestamp); // 294.40000000596046
console.log(absoluteTimestamp); // 1732254247472.5
````

*注:通过使用`performance.now()`测量L1缓存与主内存的延迟差,幽灵漏洞(Spectre)可以执行缓存推断攻击.因此主浏览器会选择降到其精度或在时间戳内混入一些随机性.详见[WebKit-What Spectre and Meltdown Mean For WebKit](https://webkit.org/blog/8048/what-spectre-and-meltdown-mean-for-webkit/)*

### Performance Timeline API
`Performance Timeline API`使用一套用于度量客户端延迟的工具.性能度量将会采用计算结束和开始时间差的形式.这些开始和结束时间会被记录为`DOMHighResTimeStamp`值,而封装这个时间戳的对象时`PerformanceEntry`的实例.

浏览器会自动记录各种`PerformanceEntry`对象,而使用`Performance.mark()`也可以记录自定义`PerformanceEntry`对象.在一个执行上下文中被记录的所有性能条目可以通过`performance.getEntries()`获取:
````JS
setTimeout(() => { console.log(performance.getEntries()); }, 1000);
// [PerformanceNavigationTiming, VisibilityStateEntry, PerformancePaintTiming, PerformancePaintTiming]
// 注意:上面的输出列表会随着时间推移而变长
````

这个返回的集合代表浏览器的性能时间线.每个`PerformanceEntry`对象都有`name`,`entryType`,`startTime`和`duration`属性:
````JS
const entry = performance.getEntries()[0];
console.log(entry.name);        // "https://www.example.com"
console.log(entry.entryType);   // navigation
console.log(entry.startTime);   // 0
console.log(entry.duration);    // 182.365000015122468
````

`performance.getEntriesByName(name)`根据`name`属性来返回`PerformanceEntry`对象的集合.  
`performance.getEntriesByType(type)`根据`entryType`属性来返回`PerformanceEntry`对象的集合.

`PerformanceEntry`是一个抽象基类.所有记录条目都继承`PerformanceEntry`,包含以下具体类:
- `PerformanceMark`
- `PerformanceMeasure`
- `PerformanceFrameTiming`
- `PerformanceNavigationTiming`
- `PerformanceResourceTiming`
- `PerformancePaintTiming`

上面的每个类都会增加大量属性,用于描述与相应条目有关的元数据.每个实例的`name`和`entryType`属性会因为各自的类不同而不同.

#### User Timing API
`User Timing API`用于记录和分析自定义性能条目.记录自定义性能条目要使用`performance.mark()`方法:
````JS
performance.mark('foo');
console.log(performance.getEntriesByType('mark')[0]);
// PerformanceMark {
//     "name": "foo",
//     "entryType": "mark",
//     "startTime": 24,
//     "duration": 0
// }
for (let i = 0; i < 1E6; ++i) {}
performance.mark('bar');
const [endMark, startMark] = performance.getEntriesByType('mark');
console.log(startMark.startTime - endMark.startTime);   // 2.300000011920929
````

还可以生成`PerformanceMeasure`条目,对应由名字作为标识的两个标记之间的持续时间.`PerformanceMeasure`的实例由`performance.measure()`方法生成:
````JS
performance.mark('foo');
for (let i = 0; i < 1E6; ++i) {}
performance.mark('bar');
performance.measure('baz', 'foo', 'bar');
const [differenceMark] = performance.getEntriesByType('measure');
console.log(differenceMark);
// PerformanceMeasure {
//     "name": "baz",
//     "entryType": "measure",
//     "startTime": 49.599999994039536,
//     "duration": 3.0999999940395355
// }
````

#### Navigation Timing API
`Navigation Timing API`提供了高精度时间戳,用于度量当前页面加载速度.浏览器会在导航事件发生时自动记录`PerformanceNavigationTiming`条目.这个对象会捕获大量事件戳,用于描述页面是何时以及如何加载的.

详见[MDN-PerformanceNavigationTiming](https://developer.mozilla.org/zh-CN/docs/Web/API/PerformanceNavigationTiming)

#### Resource Timing API
`Resource Timing API`提供了高精度事件戳,用于度量当前页面加载时请求资源的速度.浏览器会在加载资源时自动记录`PerformanceResourceTiming`.这个对象会捕获大量时间戳,用于描述资源加载速度.

详见[MDN-PerformanceResourceTiming](https://developer.mozilla.org/zh-CN/docs/Web/API/PerformanceResourceTiming)

## Web组件
这里所说的Web组件指的是一套用于增强DOM行为的工具,包括影子DOM,自定义元素和HTML模板.

*注意:这部分API可能没有统一的规范*

### HTML模板
HTML模板的核心思想是提前在页面中写好,让浏览器自动将其解析为DOM子树,但不进行渲染.这可以避免使用`innerHTML`的安全隐患和`document.createElement()`的性能损失和麻烦.

HTML元素`<template>`用于创建一个HTML模板:
````JS
<template id="foo">
    <p>A template</p>
</template>
````

#### 使用DocumentFragment
浏览器在渲染时,`<template>`的内容不会被显示,也不属于活动文档,所以`document.querySelector()`等DOM查询方法不会发现其中的`<p>`标签(但仍然能发现外围的`<template>`).`<p>`存在于一个包含在HTML模板中的`DocumentFragment`节点内:
````HTML
<!-- 开发者工具 -->
<template id="foo">
  #document-fragment
    <p>A template</p>
</template>
````
通过`<template>`元素的`content`属性可以取得这个`DocumentFragment`的引用:
````JS
console.log(document.querySelector('#foo').content);    // #document-fragment
````

对于该`DocumentFragment`,使用其DOM方法可以发现`<p>`标签.利用该`DocumentFragment`,可以一次性添加所有子节点,且比连续调用`document.appendChild()`更加高效,前者最多只需要一次布局重排.

允许使用该`DocumentFragment`对`<template>`的内容进行修改,且不会影响网页渲染.

将`DocumentFragment`作为子节点插入实际上是将`DocumentFragment`的子节点转移为另一个节点的子节点:
````JS
const fragment = new DocumentFragment();
fragment.appendChild(document.createElement('p'));
fragment.appendChild(document.createElement('p'));
fragment.appendChild(document.createElement('p'));
console.log(fragment.children.length);  // 3
document.body.appendChild(fragment);
console.log(fragment.children.length);  // 0
````

#### 使用`<template>`标签
同样,可以用上面的方法把`<template>`的内容移动:
````HTML
<body>
    <template id="foo">
        <ul>
            <li>abc</li>
            <li>abc</li>
            <li>abc</li>
        </ul>
    </template>
</body>
````
````JS
const foo = document.getElementById('foo').content;
document.body.appendChild(foo);
````
执行后`<template>`的内容变为空,此时的HTML为:
````HTML
<body>
    <template id="foo"></template>
    <ul>
        <li>abc</li>
        <li>abc</li>
        <li>abc</li>
    </ul>
</body>
````

如果想要复制模板,可以使用`importNode()`方法克隆`DocumentFragment`(或者`cloneNode()`方法?):
````JS
const foo = document.getElementById('foo').content;
document.body.appendChild(document.importNode(foo, true));
````

#### 模板脚本
脚本执行可以推迟到将`DocumentFragment`的内容实际添加到DOM树:
````HTML
<body>
    <template id="foo">
        <script>console.log('Template script executed');</script>
    </template>
    <script src="script.js"></script>
</body>
````
````JS
const foo = document.getElementById('foo').content;
console.log('About to add template');
document.body.appendChild(foo);
console.log('Added template');
// About to add template
// Template script executed
// Added template
````
执行后的HTML:
````HTML
<body>
    <template id="foo"></template>
    <script src="try.js"></script>
    <script>console.log('Template script executed');</script>
</body>
````

注意:即使`<script>`插入到了暂时未执行到的地方,其也会立即执行.

### 影子DOM
使用影子DOM可以将完整的DOM树作为节点添加到DOM树.这样可以实现DOM的封装.即使是CSS样式也可以限制在影子DOM子树而不是整个顶级DOM树中.

DOM与HTML模板很类似,但是影子DOM的内容会实际渲染到页面上.

#### 理解影子DOM
例如,对于:
````HTML
<div class="red-text">
    <p>Make me red!</p>
</div>
<div class="green-text">
    <p>Make me green!</p>
</div>
<div class="blue-text">
    <p>Make me blue!</p>
</div>

<style>
    .red-text {
        color: red;
    }
    .green-text {
        color: green;
    }
    .blue-text {
        color: blue;
    }
</style>
````
我希望这些CSS样式仅仅应用于这3个`<div>`,而不渗透到其他地方.解决方法就是使CSS选择符足够特别,或者使用影子DOM.

#### 创建影子DOM
考虑到安全以及避免影子DOM冲突,并非所有元素都可以包含影子DOM.尝试给无效元素或者已经有了影子DOM的元素添加影子DOM会导致抛出错误.

可以容纳影子DOM的元素包括:
- 任何带有有效的名称且可独立存在的(autonomous)自定义元素
- `<article>`
- `<aside>`
- `<blockquote>`
- `<body>`
- `<div>`
- `<footer>`
- `<h1>`
- `<h2>`
- `<h3>`
- `<h4>`
- `<h5>`
- `<h6>`
- `<header>`
- `<main>`
- `<nav>`
- `<p>`
- `<section>`
- `<span>`

影子DOM使通过元素的`attachShadow()`方法创建并添加给有效HTML元素的.容纳影子DOM的元素被称为*影子宿主*.影子DOM的根节点被称为*影子根*.

`attachShadow()`方法需要一个`shadowRootInit`对象,返回影子DOM的实例.`shadowRootInit`对象必须包含一个`mode`属性,值为`"open"`或`"closed"`.对`open`影子DOM的引用可以通过`shadowRoot`属性在HTML元素上获得,而对`closed`影子DOM的引用无法这样获得.

````JS
const foo = document.getElementById('foo');
const bar = document.getElementById('bar');
const openShadowDOM = foo.attachShadow({ mode: 'open' });
const closeShadowDOM = bar.attachShadow({ mode: 'closed' });
console.log(openShadowDOM);     // #shadow-root (open)
console.log(closeShadowDOM);    // #shadow-root (closed)
console.log(foo.shadowRoot);    // #shadow-root (open)
console.log(bar.shadowRoot);    // null
````

注意:恶意代码可以绕过`closed`影子DOM的限制,从而恢复对影子DOM的访问.因此不能为了安全创建保密(closed)影子DOM,需要创建保密影子DOM的场景也很少.如果想保护独立的DOM树不受未信任代码影响,对`<iframe>`施加的跨源限制更可靠.

#### 使用影子DOM
把影子DOM添加到元素之后,可以像使用常规DOM一样使用影子DOM:
````JS
const foo = document.getElementById('foo');
const shadowDOM = foo.attachShadow({ mode: 'open' });
shadowDOM.innerHTML = `<p style="red-text" id="in-shadow">Hello world</p>`
console.log(document.getElementById("in-shadow"));
console.log(shadowDOM.getElementById("in-shadow"));
````
对应的HTML(修改后):
````HTML
<div id="foo">
  #shadow-root (open)
    <p style="red-text" id="in-shadow">Hello world</p>
</div>
<div id="bar"></div>
````

HTML元素可以在影子DOM内外之间无限制移动,即使它们属于不同的DOM树.

#### 合成与影子DOM槽位
对于影子DOM,其一旦添加到元素中,浏览器就会赋予其最高的渲染优先级(因为影子DOM不属于原有的DOM树,却又需要渲染).例如:
````JS
document.body.innerHTML = `
<div>
    <p>Foo</p>
</div>
`;
setTimeout(() => document.querySelector('div').attachShadow({ mode: 'open' }), 1000);
````
上述代码中,空的影子DOM渲染优先级会高于`<p>`,因此`<div>`内的文本会在1000毫秒后被隐藏.

为了显示文本内容,需要使用`<slot>`标签指示浏览器在哪里放置原来的HTML:
````JS
document.body.innerHTML = `
<div>
    <p>Foo</p>
</div>
`;
document.querySelector('div').attachShadow({ mode: 'open' })
        .innerHTML = `<div id="bar">
                        <slot></slot>
                     </div>`
````
最终的HTML为:
````HTML
<div>
  #shadow-root (open)
    <div id="bar">
        <slot>
            #reveal <!-- 浏览器会在这里显示一个灰色的<p> -->
        </slot>
    </div>
    <p>Foo</p> #slot    <!--这里的#slot 和 #reveal其实都是按钮,分别表示导航到对应的<slot>和真实存在的位置-->
</div>
````

除了默认槽位,还可以使用*命名槽位*实现多个投射.这是通过匹配的`slot`/`name`属性对实现的.带有`slot="foo"`属性的元素会被投射到带有`name="foo"`的`<slot>`上:
````JS
document.body.innerHTML = `
<div>
    <p slot="foo">Foo</p>
    <p slot="bar">Bar</p>
</div>
`;

document.querySelector('div')
    .attachShadow({ mode: 'open' })
    .innerHTML = `
    <slot name="bar"></slot>
    <slot name="foo"></slot>
    `
````

#### 事件重定向
如果影子DOM中发生了浏览器事件(如`click`),那么浏览器需要一种方式让父DOM处理事件.不过,实现也必须考虑影子DOM的边界.为此,事件会逃出(冒泡)影子DOM并经过*事件重定义向*在外部能被处理.逃出后,事件就好像是由影子宿主本身而非真正的包装元素触发的一样.

````JS
document.body.innerHTML = `
<div onclick="console.log('Handled outside:', event.target)"></div>
`;
document.querySelector('div')
    .attachShadow({ mode: 'open' })
    .innerHTML = `
<button onclick="console.log('Handled inside:', event.target)">Foo</button>
`;
// 点击按钮时:
// Handled inside: <button onclick="..."></button>
// Handled outside: <div onclick="..."></div>
````
事件重定向只会发生在影子DOM中实际存在的元素上.使用`<slot>`标签从外部投射进来的元素不会发生事件重定向,因为这些元素仍然存在于影子DOM外部.

### 自定义元素
自定义元素为HTML元素引入了面向对象编程风格.

#### 创建自定义元素
浏览器会尝试将无法识别的元素作为通用元素整合进DOM.当然,这些元素默认会做任何通用HTML元素做的事,即显示其中的文本:
````HTML
<x-foo>I'm inside a nonsense element.</x-foo>
````
````JS
let foo = document.getElementsByTagName('x-foo')[0];
console.log(foo instanceof HTMLElement);    // true
````
自定义元素默认会被标识为`HTMLElement`.

为了实现更加复杂的行为,自定义元素要使用全局属性`customElements`,这个属性会返回`CustomElementRegistry`对象.

调用`customElements.define()`方法可以创建自定义元素:
````JS
class FooElement extends HTMLElement {  // 很少有创建自定义元素而不继承HTMLElement的.
    constructor() {
        super();    // 自定义元素的构造函数中必须始终先调用super().如果没有定义构造函数,会默认调用super().
        console.log('x-foo');
    }
}
customElements.define('x-foo', FooElement);
// x-foo
console.log(document.querySelector('x-foo') instanceof FooElement); // true
console.log(customElements);    // CustomElementRegistry { ... }
````

注意:自定义元素名必须至少包含一个不在名称开头和末尾的连字符,而且元素标签不能自关闭.

如果自定义元素继承了一个元素类,那么可以使用`is`属性和`extends`选项将标签指定为该自定义元素的实例:
````HTML
<div is="x-foo"></div>
````
````JS
class FooElement extends HTMLDivElement {
    constructor() {
        super();
        console.log('x-foo');
    }
}
customElements.define('x-foo', FooElement, { extends: 'div' });
// x-foo
````

自定义元素可以添加子DOM内容,也可以为自定义元素添加影子DOM并将内容添加到这个影子DOM中.

#### 使用自定义元素生命周期方法
可以在自定义元素的不同生命周期执行代码.带有相应名称的自定义元素类的实例方法会在不同生命周期阶段被调用.自定义元素有以下5个生命周期方法:
- `constructor()`:在创建元素实例或将已有DOM元素升级为自定义元素时调用.
- `connectedCallback()`:每当元素添加到文档中时调用.规范建议开发人员尽可能在此回调中实现自定义元素的设定,而不是在构造函数中实现.
- `disconnectedCallback()`:每当元素从文档中移除时调用.
- `adoptedCallback()`:每当元素通过`document.adoptNode()`而被移动到新文档中时调用.
- `attributeChangedCallback()`:在每次可观察属性更改,添加,移除或替换时调用.在元素实例初始化时,初始值的定义也算一次变化.

````JS
class FooElement extends HTMLElement {
    constructor() {
        super();
        console.log('ctor');
        // 设置属性不要在构造函数中,因为使用document.createElement()创建的元素不能拥有属性
    }
    get bar() {
        return this.getAttribute('bar');
    }
    set bar(value) {
        this.setAttribute('bar', value);
    }
    connectedCallback() {
        console.log('connected');
        this.bar = true;    // 这个会映射到DOM属性上,因为定义了相应的set和get函数
        this.baz = true;    // 这个不会映射到DOM属性上
    }
    disconnectedCallback() {
        console.log('disconnect');
    }
}
customElements.define('x-foo', FooElement);
const fooElement = document.createElement('x-foo');
// ctor
document.body.appendChild(fooElement);
// connected
console.log(fooElement);    // <x-foo bar="true"></x-foo>
setTimeout(() => {
    document.body.removeChild(fooElement);
    // disconnected
}, 100);
````

对于`attributeChangedCallback()`,需要一个静态属性`observedAttributes`来表示哪些属性在被修改之后需要回调:
````JS
class FooElement extends HTMLElement {
    static observedAttributes = ["bar"];    // 指示应该触发attributeChangedCallback()的属性名的数组
    get bar() {
        return this.getAttribute('bar');
    }
    set bar(value) {
        this.setAttribute('bar', value);
    }
    connectedCallback() {
        this.bar = true;
    }
    attributeChangedCallback(name, oldValue, newValue) {
        console.log(`${name}: ${oldValue} -> ${newValue}`);
    }
}
customElements.define('x-foo', FooElement);
const fooElement = document.createElement('x-foo');
document.body.appendChild(fooElement);
// bar: null -> true
fooElement.bar = false;
// bar: true -> false
````

#### 升级自定义元素
`CustomElementRegistry`上额外暴露了一些方法,这些方法可以检测自定义元素是否定义完成,然后可以用它来升级已有元素.

`CustomElementRegistry.get()`方法会返回相应自定义元素的类.

`CustomElementRegistry.whenDefined()`方法会返回一个期约,当相应自定义元素有定义之后解决.

连接到DOM的元素在自定义元素有定义时会*自动升级*.如果想在元素连接到DOM之前强制升级,可以使用`CustomElementRegistry.upgrade()`方法.

````JS
class FooElement extends HTMLElement {}
let foo = document.querySelector('x-foo');
customElements.whenDefined('x-foo').then((value) => console.log('defined:',value));
console.log(customElements.get('x-foo'));   // undefined
customElements.upgrade(foo); // 强制升级
customElements.define('x-foo', FooElement);
console.log(customElements.get('x-foo'));   // class FooElement extends HTMLElement {}
// defined: class FooElement extends HTMLElement {}
````

## Web Cryptography API
### 生成随机数
`Math.random()`方法是伪随机数生成器(PRNG)实现的,攻击者只要知道PRNG的内部状态,就可以预测后续生成的伪随机值.

PRNG不适和用于加密计算.为解决这个问题,`Web Cryptography API`引入了密码学安全伪随机数生成器(CSPRNG),这个CSPRNG可以通过`crypto.getRandomValues()`在全局`Crypto`对象上访问.`getRandomValues()`会把随机值写入作为参数传给它的定型数组.定型数组的类不重要,因为底层缓冲区会被随机的二进制位填充:
````JS
const array = new Uint8Array(2);
for (let i = 0; i < 5; ++i) {
    console.log(crypto.getRandomValues(array));
}
// Uint8Array [11, 222]
// Uint8Array [242, 213]
// Uint8Array [30, 212]
// Uint8Array [232, 88]
// Uint8Array [115, 64]
````

`getRandomValues()`最多可以生成`2^16`字节,超出则会抛出错误.

### 使用SubtleCrypto对象
`SubtleCrypto`对象可以通过`window.crypto.subtle`访问.

这个对象包含一组方法,用于执行常见的密码学功能,如加密,散列,签名和生成密钥.因为所有密码学操作都在原始二进制数据上执行,所以`SubtleCrypto`的每个方法都要用到`ArrayBuffer`和`ArrayBufferView`类型.由于字符串是密码学操作的重要应用场景,因此`TextEncoder`和`TextDecoder`是经常与`SubtleCrypto`一起使用的类,用于实现二进制数据与字符串之间的相互转换.

*`SubtleCrypto`对象只能在安全上下文(https)中使用.否则`subtle`属性为`undefined`.*

#### 生成密码学摘要
计算数据的密码学摘要是非常常用的密码学操作.这个规范支持4种摘要算法:`SHA-1`和3种`SHA-2`.
- `SHA-1`(Secure Hash Algorithm 1):架构类似MD5的散列函数.接收任意大小的输入,生成160位消息散列.由于容易受到碰撞攻击,这个算法已经不再安全.
- `SHA-2`(Secure Hash Algorithm 2):构建于相同耐碰撞单向压缩函数之上的一套散列函数.规范支持其中3种:`SHA-256`,`SHA-384`,`SHA-512`.生成的消息摘要可以是256位(SHA-256),384位(SHA-384)或512位(SHA-512).这个算法被认为是安全的,广泛应用于很多领域和协议,包括TLS,PGP和加密货币(如比特币).

`SubtleCrypto.digest()`方法用于生成信息摘要.要使用的散列算法通过字符串`"SHA-1"`,`"SHA-256"`,`"SHA-384"`,`"SHA-512"`指定.返回一个`Promise`,解决一个包含摘要值的`ArrayBuffer`.
````JS
const message = new TextEncoder().encode('foo');    // 转换为二进制
const messageDigest = crypto.subtle.digest('SHA-256', message);
messageDigest.then((value) => {
    console.log(value); // ArrayBuffer(32)
    const arr = new Uint32Array(value);
    console.log(arr);   // Uint32Array(8) [1806968364, 2412183400, 1011194873, 876687389, 1882014227, 2696905572, 2287897337, 2934400610]
    return Promise.resolve(new Uint8Array(value));
}).then((value) => console.log(
    Array.from(value)   // 这里的value需要以8位进行分隔,否则会出现大小端的问题
         .map((x) => x.toString(16).padStart(2, '0'))
         .join("")
));
````

#### CryptoKey与算法
`SubtleCrypto`对象使用`CryptoKey`类的实例来生成密钥.`CryptoKey`类支持多种加密算法,允许终止密钥的抽取和使用.

`CryptoKey`类支持以下算法,按各自的父密码系统归类:
- `RSA`:公钥密码系统,使用两个大素数获得一对公钥和私钥,可用于签名/验证或加密/解密消息.`RSA`的陷门函数被称为`分解难题`.
- `RSASSA-PKCS1-v1_5`:RSA的一个应用,用于使用私钥给消息签名,允许使用公钥验证签名.
  - `SSA`:表示算法支持签名生成和验证操作.
  - `PKCS1`表示算法展示出的RSA密钥必需的数学特征.
  - `RSASSA-PKCS1-v1_5`:是确定性的,意味着同样的消息和密钥每次都会生成相同的签名.
- `RSA-PSS`:RSA的另一个应用,用于签名和验证消息.
  - `PSS`表示生成签名时会加盐以得到随机签名.
  - 与`RSASSA-PKCS1-v1_5`不同,同样的消息和密钥每次都会生成不同的签名.
  - 与`RSASSA-PKCS1-v1_5`不同,`RSA-PSS`有可能简约到`RSA`分解难题的难度.
  - 通常,虽然`RSASSA-PKCS1-v1_5`仍被认为是安全的,但`RSA-PSS`应该用于代替`RSASSA-PKCS1-v1_5`.
- `RSA-OAEP`:RSA的一个应用,用于使用公钥加密信息,用私钥来解密.
  - `OAEP`表示算法利用了`Feistel`网络在加密前处理未加密的消息.
  - `OAEP`只要将确定性RSA加密模式转换为概率性加密模式.
- `ECC`:公钥密码系统,使用一个素数和一个椭圆曲线获得一对公钥和私钥,可用于签名/验证消息.ECC的陷门系统被称为`椭圆曲线离散对数问题`.ECC被认为优于RSA.虽然RSA和ECC在密码学意义上都很强,但ECC密钥比RSA密钥短,而且ECC密码学操作比RSA操作快.
- `ECDSA`:ECC的一个应用,用于签名和验证消息.这个算法是`数字签名算法(DSA)`的一个椭圆曲线风格的变体.
- `ECDH`:ECC的密钥生成和密钥协议应用,允许两方通过公开通信渠道建立共享的机密.这个算法是`Diffie-Hellman密钥交换`协议的一个椭圆曲线风格的变体.
- `AES`:对称密钥密码系统,使用派生自置换组合网络的分组密码加密和解密数据.AES在不同模式下使用,不同模式算法的特性也不同.
- `AES-CTR`:AES的`计数器模式`.这个模式使用递增计数器生成器密钥流,其行为类似密文流.使用时必需为其提供一个随机数,用作初始化向量.`AES-CTR`加密/解密可以并行.
- `AES-CBC`:AES的`密码分组链模式`.在加密纯文本的每个分组之前,先使用之前密文分组求`XOR`,也就是名字中的"链".使用一个初始化向量作为第一个分组的XOR输入.
- `AES-GCM`:AES的`伽罗瓦/计数器模式`.这个模式使用计数器和初始化向量生成一个值,这个值会与每个分组的纯文本计算XOR.与CBC不同,这个模式的XOR输入不依赖之前分组密文.因此GCM模式可以并行.由于其卓越的性能,ASM-GCM在很多网络安全协议中得到了应用.
- `AES-KW`:AES的`密钥包装模式`.这个算法将加密密钥包装为一个可移植且加密的格式,可以在不信任的渠道中传输.传输之后,接收方可以解包密钥.与其他AES模式不同,`AES-KW`不需要初始化向量.
- `HMAC`:用于生成`消息认证码`的算法,用于验证通过不可信网络接收的消息没有被修改过.两方使用散列函数和共享密钥来签名和验证消息.
- `KDF`:可以使用散列函数从主密钥获得一个或多个密钥的算法.`KDF`能够生成不同长度的密钥,也能把密钥转换为不同格式.
- `HKDF`:密钥推导函数,与高熵输入(如已有密钥)一起使用.
- `PBKDF2`:密钥推导函数,与低熵输入(如密钥字符串)一起使用.

详见[W3C-Web Cryptography API-Algorithm Overview](https://w3c.github.io/webcrypto/#algorithms)

#### 生成CryptoKey
使用`SubtleCrypto.generateKey()`方法可以生成随机`CryptoKey`,这个方法可以返回一个期约,解决为一个或多个`CryptoKey`实例.使用时需要给这个方法传入一个指定目标算法的参数对象,一个表示密钥是否可以从`CryptoKey`对象中提取出来的布尔值,以及一个表示这个密钥可以与哪个`SubtleCrypto`方法一起使用的字符串数组.

由于不同的密码系统需要不同的输入来生成密钥,上述参数对象为每种密码系统都规定了必需的输入.

/// TODO

# 错误处理与调试
## 浏览器错误报告
### 桌面控制台
所有现代的桌面浏览器都会通过控制台暴露错误.这些错误可以显示在开发者工具的内嵌控制台中.

### 移动控制台
移动浏览器不会直接在设别上提供控制台界面.不过,还是有一些途径可以在移动设备中检查错误.

详见:
- [Google Developers-Remote debug Android devices](https://developer.chrome.google.cn/docs/devtools/remote-debugging)
- [Apple Developer-Web Inspector](https://developer.apple.com/documentation/safari-developer-tools/web-inspector/)

## 错误处理
### try/catch语句
`try/catch`语句的基本语法如下:
````JS
try {
    // 可能出错的代码
} catch (error) {
    // 出错时要做什么
}
````

如果`try`块中有代码发生错误,代码会立即退出执行,并跳到`catch`块中.`catch`块此时接收到一个对象,该对象包含发生错误的相关信息.即使在`catch`块中不使用错误对象,也必须为它定义名称.错误对象中暴露的实际信息因浏览器而异,但至少包含保存错误消息的`message`属性.规范也指定了定义错误类型的`name`属性:
````JS
try {
    undefined();
} catch (error) {
    console.log(error.message); // undefined is not a function
    console.log(error.name);    // TypeError
}
````

#### finally子句
`try/catch`语句中可选的`finally`子句始终运行.如果`try`块中的代码运行完,则接着执行`finally`块中的代码.如果出错并执行`catch`块中的代码,则`finally`块中的代码仍执行.`try`或`catch`块无法阻止`finally`块执行,`return`语句也无法阻止:
````JS
function testFinally() {
    try {
        return 2;
    } catch (error) {
        return 1;
    } finally {
        return 0;
    }
}
````

这个函数由于`finally`块的存在导致`try`块中的`return`语句被忽略.因此,这个函数永远返回`0`.如果去掉`finally`子句,该函数会返回`2`.如果写出`finally`子句,`catch`块就成了可选的(它们两者中只有一个是必需的).

#### 错误类型
代码执行过程中会发生各种类型的错误.每种类型都会对应一个错误发生时抛出的错误对象:
- `Error`
- `InternalError`
- `EvalError`
- `RangeError`
- `ReferenceError`
- `SyntaxError`
- `TypeError`
- `URIError`

`Error`是基类型,其他错误类型继承该类型.因此,所有错误类型都共享相同的属性(所有错误对象上的方法都是这个默认类型定义的方法).浏览器很少会抛出`Error`类型错误,该类型错误主要用于开发者抛出自定义错误.

`InternalError`类型的错误会在底层JS引擎抛出异常时由浏览器抛出.例如,递归过多导致了栈溢出.这个类型并不是代码中通常要处理的错误,如果真发生了这种错误,很可能代码哪里弄错了或者有危险了.

`EvalError`类型的错误会在使用`eval()`函数发生异常时抛出.其发生在不将`eval()`作为函数直接调用或`eval`被赋值时.

`RangeErrir`错误会在数组越界时抛出.

`ReferenceError`会在找不到对象时发生.这种错误经常是由访问不存在的变量而导致的.

`SyntaxError`经常在给`eval()`传入的字符串包含JS语法错误时发生.

`TypeError`在JS中很常见,主要发生在变量不是预期类型,或者访问不存在的方法时.很多原因可能导致这种错误,尤其是在使用类型特定的操作而变量类型不对时.

`URIError`只会在使用`encodeURI()`或`decodeURI()`但传入了格式错误的URI时发生.

在`try/catch`语句的`catch`块中,可以使用`instanceof`操作符确定错误类型:
````JS
try {
    someFunc();
} catch (error) {
    if (error instanceof TypeError) {
        // ...
    } else if (error instanceof ReferenceError) {
        // ...
    } else {
        // ...
    }
}
````

### 抛出错误
与`try/catch`语句对应的一个机制是`throw`操作符,用于在任何时候抛出自定义错误.`throw`操作符必须有一个值,但值的类型不限:
````JS
throw 12345;
throw "Hello world!";
throw true;
throw { name: "JavaScript" };
````

使用`throw`操作符时,代码立即停止执行,除非`try/catch`语句捕获了抛出的值.

可以通过内置的错误类型来模拟浏览器错误.每种错误类型的构造函数都只接收一个参数,就是错误消息:
````JS
throw new Error("something happened");
throw new SyntaxError("syntax error");
````

也可以通过继承`Error`创建自定义的错误类型.创建自定义错误类型时,需要提供`name`和`message`属性:
````JS
class CustomError extends Error {
    constructor(message) {
        super(message);
        this.name = "CustomError";
        this.message = message;
    }
}
throw new CustomError("My message");
````

使用适当的信息创建自定义错误可以有效提高代码的可维护性:
````JS
function process(values) {
    if (!(value instanceof Array)) {
        throw new Error("process(): Argument must be an array.");
    }
    values.sort();
    for (let value of values) {
        if (value > 100) {
            return value;
        }
    }
    return -1;
}
````

一般来说,错误要在应用程序架构的底层抛出,在这个层面上,人们对正在进行的流程知之甚少,因此无法真正地处理错误.因此,应该认真烤炉抛出带有详细信息的错误.然后捕获和处理错误交给应用程序就行了.

### error事件
**这种事件处理的相关文章已经无法在MDN上找到,取而代之的是符合DOM2规范的`ErrorEvent`.**

任何没有被`try/catch`语句处理的错误都会在`window`对象上触发`error`事件.该事件是浏览器早期支持的事件,为了向后兼容,很多浏览器保持了其格式不变.在`error`事件处理程序中,浏览器会传入3个参数:错误信息,发生错误的URL和行号.这种事件处理程序需要使用`DOM Level0`技术来指定,因为它不遵勖`DOM Level2 Events`规范:
````JS
window.onerror = (message, url, line) => {
    console.log(message);   // Script error.
    return false;   // 返回false表示阻止浏览器默认报告错误的行为
};
throw new Error("");
````

上面这个方法已经不符合规范,建议使用[MDN-ErrorEvent](https://developer.mozilla.org/zh-CN/docs/Web/API/ErrorEvent)

图片也支持`error`事件.任何时候,如果图片`src`属性的URL没有返回可识别的图片格式,就会触发`error`事件.这个事件遵循DOM格式,返回一个以图片为目标的`event`对象:
````JS
const image = new Image();
image.addEventListener("load", (event) => {
    console.log("Image loaded!");
});
image.addEventListener("error", (event) => {
    console.log("Image not loaded!");
});
image.src = "notExist.gif";
````

### 识别错误
错误处理非常重要的部分是首先识别错误可能会在代码中的什么地方发生,因为JS是松散类型的,不会验证函数参数,所以很多错误只有在代码真正运行起来时才会出现.通常,需要注意3类错误:
- 类型转换错误
- 数据类型错误
- 通信错误

#### 静态代码分析器
通过在代码构建流程中添加静态代码分析或代码检查器(linter),可以预先发现非常多的错误.这样的代码分析工具有很多,常用的静态分析工具时`JSHint`,`JSLint`,`Google Closure`,`TypeScript`.

静态代码分析器要求使用类型,函数签名及其他指令来注解JS,以此描述程序如何在基本可执行代码之外运行.分析器会比较注解和JS代码的各个部分,对在实际运行时可能出现的潜在不兼容问题给出提醒.

#### 类型转换错误
类型转换错误的主要原因时使用了会自动改变某个值的数据类型的操作符或语言构建.使用`==`或`!=`操作符,以及在`if`,`for`,`while`等流程控制语句中使用非布尔值,经常会导致类型转换错误.

#### 数据类型错误
因为JS是松散类型的,所以变量和函数参数都不能保证会使用正确的数据类型.开发者需要自己检查数据类型,确保不会发生错误.数据类型错误常发生在将意外值传给函数的时候.

例如:
````JS
function getQueryString(url) {
    if (typeof url === "string") {  // 通过类型检查保证安全
        let pos = url.indexOf("?");
        if (pos > -1) {
            return url.substring(pos + 1);
        }
    }
    return "";
}

function reverseSort(values) {
    if (values instanceof Array) {
        values.sort();
        values.reverse();
    }
}
````

#### 通信错误
随着Ajax编程的出现,Web应用程序在运行期间动态数据和功能成为常见的情形.JS和服务器之间的通信也会出现错误.

第一种错误是URL格式或发送数据的格式不正确.通常,把数据发送到服务器之前没有用`encodeURIComponent()`编码,会导致这种错误.例如,下面的URL格式就不正确:`http://www.yourdomain.com/?redir=http://someotherdomain.com?a=b&c=d`.使用`encodeURIComponent()`修复后,得到的结果如下:`http://www.yourdomain.com/?redir=http%3A%2F%2Fwww.someotherdomain.com%3Fa%3Db%26c%3Dd`

在服务器相应非预期值时也会发生通信错误.在动态加载脚本或样式时,请求的资源有可能不可用.有些浏览器在没有返回预期资源时会静默失败,而其他浏览器则会报告错误.不过,在动态加载资源的情况下出错,是不太好做错误处理的.有时候,使用Ajax通信可能会提供关于错误条件的更多信息.

### 区分重大与非重大错误
任何错误处理策略中一个非常重要的方面就是确定某个错误是否为重大错误.具有以下一个或多个特性的错误属于非重大错误:
- 不会影响用户的主要任务
- 只会影响到页面中某个部分
- 可以恢复
- 重复操作可能成功

对于非重大错误,无须给用户发送消息.可以将受影响的页面区域替换为一条消息,表示该功能暂时不能使用,但不需要中断用户体验.

另一反面,重大错误具备如下特性:
- 应用程序绝对无法继续运行
- 错误严重影响了用户的主要目标
- 会导致其他错误发生

当重大错误发生时,应该立即发送消息让用户知晓自己不能再继续使用应用程序了.如果必须刷新页面才能恢复应用程序,那就应该明确告知用户,并提供一个自动刷新页面的按钮.

代码中则不要区分是不是重大错误.非重大错误和重大错误的区别主要体现在对用户的影响上.好的代码设计意味着应用程序的某个部分的错误不会影响其他部分,实际上根本不应该相关.

### 把错误记录到服务器中
Web应用程序开发中的一个常见做法就是建立中心化的错误日志存储和追踪系统.数据库和服务器错误正常写到日志中并按照API加以分类.对复杂的Web应用程序而言,最好也把JS错误发送回服务器记录下来.这样做可以把错误记录到与服务器相同的系统,只要把它们归类到前端错误即可.使用相同的系统可以进行相同的分析,而不用考虑错误来源.

要建立JS错误日志系统,首先需要在服务器上有页面或入口可以处理错误数据.该页面只要从查询字符串中取得错误数据,然后把它们保存到错误日志中即可.例如:
````JS
function logError(sev, msg) {
    let img = new Image(),
        encodeSev = encodeURIComponent(sev),
        encodeMsg = encodeURIComponent(msg);
    img.src = `log.php?sev=${encodedSev}&msg=${encodedMsg}`;
}

for (let mod of mods) {
    try {
        mod.init();
    } catch (ex) {
        logError(`nonfatal", "Module init failed: ${ex.message}`);
    }
}
````
上面使用`Image`对象发送请求只要是从灵活性方法考虑的:
- 所有浏览器都支持`Image`对象,即使不支持`XMLHttpRequest`对象也一样.
- 不受跨域规则限制.通常,接收错误消息的应该是多个服务器中的一个,而`XMLHttpRequest`此时就比较麻烦.
- 记录错误的过程很少出错.大多数Ajax通信借助JS库的包装来处理.如果这个库本身出错,而你又要利用它记录错误,那么显然错误消息永远不会发给服务器.

## 调试技术
### 把消息记录到控制台
所有主流浏览器都有JS控制台,该控制台可用于查询JS错误.另外,这些浏览器都支持通过`console`对象直接把JS消息写入控制台,这个对象包含如下方法:
- `error(message)`:在控制台中记录错误消息.
- `info(message)`:在控制台中记录消息性内容.
- `log(message)`:在控制台记录常规消息.
- `warn(message)`:在控制台中记录警告消息.

记录消息时使用的方法不同,消息显示的样式也不同.错误消息包含一个红叉图标,而警告消息包含一个黄色叹号图标.

在产品环境下应该删除所有调试相关代码.这可以在部署时使用代码自动完成清理,也可以手动删除.

*注意:相比于使用警告框,打印日志消息是更好的调试方法.这是因为警告框会阻塞代码执行,从而影响对异步操作的计时,进而影响代码的结果.打印日志也可以随意输出任意多个参数并检查对象实例.(警告框只能将对象序列化为一个字符串再展示出来)*

### 理解控制台运行时
浏览器控制台是个读取-求值-打印-循环(REPL,read-eval-print-loop),与页面的JS运行时并发.这个运行时就像浏览器对新出现在DOM中的`<script>`标签求值一样.在控制台中执行的命令可以像页面级JS一样访问全局和各种API.控制台中可以执行任意数量的代码,与它可能会阻塞的任何页面级代码一样.修改,对象和回调都会保留在DOM和运行时中.

JS运行时会限制不同窗口可以访问哪些内容,因而在所有主流浏览器中都可以选择在哪个窗口中执行JS控制台输入.你所执行的代码不会有特权提升,仍会受跨源限制和其他浏览器施加的控制规则约束.

控制台运行时也会集成开发者工具,提供常规JS开发中所没有的上下文调试工具.其中一个非常有用的工具是最后点击选择器.在开发者工具的元素标签内,单击DOM树中一个节点,就可以在控制台标签页中使用`$0`引用该节点的JS实例.它就跟普通的JS实例一样,因此可以读取属性,或者调用成员方法.

### 使用JS调试器
所有主流浏览器都可以使用JS调试器.`debugger`关键字可以调用可能存在的调试功能.如果没有相关的功能,这条语句会被简单地跳过.可以像下面这样使用`debugger`关键字:
````JS
function pauseExecution() {
    console.log("Will print before breakpoint");
    debugger;
    console.log("Will not print until breakpoint continue");
}
````

在运行时碰到这个关键字,所有主流浏览器都会打开开发者工具面板,并在指定位置显示断点.然后,可以通过单独的浏览器控制台在断点所在的特定词法作用域中执行代码.此外,还可以执行标准的浏览器调试器操作(单步进入,单步跳过,继续,等等).

浏览器也支持在开发者工具的源代码标签页中选择希望设置断点的代码行来手动设置断点.这样设置的断点与使用`debugger`关键字设置的一样,只是不会在不同浏览器会话之间保持.

### 在页面中打印消息
另一种常见的打印调试消息的方式是把消息写到页面中指定的区域.这个区域可以是所有页面中都包含的元素,但仅用于调试目的.也可以是在需要时临时创建的元素.例如,可以定义这样`log()`函数:
````JS
function log(message) {
    const console = document.getElementById("debuginfo");
    if (console === null) {
        console = document.createElement("div");
        console.id = "debuginfo";
        console.style.background = "#dedede";
        console.style.border = "1px solid silver";
        console.style.padding = "5px";
        console.style.width = "400px";
        console.style.position = "absolute";
        console.style.right = "0px";
        console.style.top = "0px";
        document.body.appendChild(console);
    }
    console.innerHTML += `<p>${message}</p>`;
}
````

### 补充控制台方法
由于`console`是一个全局对象,所以可以为这个对象添加方法,也可以用自定义函数重写已有的方法.

### 抛出错误
抛出错误是调试代码的很好方式.如果错误消息足够具体,只要看一眼就可以确定原因.好的错误消息包含关于错误原因的确切信息,因此可以减少额外的调试的工作量.比如:
````JS
function assert(condition, message) {
    if (!condition) {
        throw new Error(message);
    }
}
function divide(num1, num2) {
    assert(typeof num1 == "number" && typeof num2 == "number",
           "divide(): Both arguments must be numbers.");
    return num1 / num2;
}
````

## 旧版IE的常见错误
IE已死,所以该部分内容就直接跳过了.

# 处理XML
## 浏览器对XML DOM的支持
### DOM Level2 Core
DOM Level2增加了`document.implementation`的`createDocument()`方法,用于创建空XML文档:
````JS
let xmldom = document.implementation.createDocument(namespaceUri, root, doctype);
````

在JS中处理XML时,`root`参数通常只会使用一次,因为这个参数定义的是XML DOM中`document`元素的标签名.`namespace`参数用得很少,因为在JS中很难管理命名空间.`doctype`参数则是更少用.

要创建一个`document`对象标签名为`<root>`的新XML文档,可以这样写:
````JS
let xmldom = document.implementation.createDocument("", "root", null);
console.log(xmldom.documentElement.tagName);    // "root"
let child = xmldom.createElement("child");
xmldom.documentElement.appendChild(child);
````

注意,即使不指定命名空间和文档类型,参数还是要传的.命名空间传入空字符串表示不应用命名空间,文档类型传入`null`表示没有文档类型.`xmldom`是`Document`类型的实例.

在实践中,更多的时候是把XML文档解析为DOM结构,或者相反.

### DOMParser类型
`DOMParser`用于把XML解析为DOM文档.要使用`DOMParser`,需要先创建它的一个实例,然后再调用`parseFromString()`方法.这个方法接收两个参数:要解析的XML字符串和内容类型(始终应该是`"text/html"`).返回值是`Document`的实例:
````JS
let parser = new DOMParser();
let xmldom = parser.parseFromString("<root><child /></root>", "text/xml");
console.log(xmldom.documentElement.tagName);    // "root"
console.log(xmldom.documentElement.firstChild.tagName); // "child"
let anotherChild = xmldom.createElement("child");
xmldom.documentElement.appendChild(anotherChild);
let children = xmldom.getElementsByTagName("child");
console.log(children.length);   // 2
````

`DOMParser`只能解析格式良好的XML,因此不能把HTML解析为HTML文档.发生解析错误时,`parseFromString()`方法仍会返回一个`Document`对象,只不过其`document`元素是`<parsererror>`(需要通过`getElementsByTagName()`方法查找文档中是否包含`<parsererror>`元素,不要使用`xmldom.documentElement.tagName`判断,因为不同浏览器会嵌入在不同位置,旧版IE还会抛出错误),该元素的内容为解析错误的描述:
````XML
<parsererror xmlns="http://www.mozilla.org/newlayout/xml/parsererror.xml">
(error description)
<sourcetext>(a snippet of the source XML)</sourcetext>
</parsererror>
````

### XMLSerializer
`XMLSerializer`类型用于把DOM文档序列化为XML字符串.要序列化DOM文档,必须创建`XMLSerializer`的实例.然后把文档传给`serializeToString()`方法:
````JS
let serializer = new XMLSerializer();
let xml = serializer.serializeToString(xmldom);
console.log(xml);
````

`serializeToString()`返回的值是打印效果不太好的字符串,因此看起来有点困难.

`XMLSerializer`能够序列化任何有效的DOM对象,包括个别节点和HTML文档.把HTML文档传给`serializeToString()`时,这个文档会被当成XML文档,因此得到的结果是格式良好的.

给`serializeToString()`传入非DOM对象,就会导致抛出错误.

## 浏览器对XPath的支持
`XPath`是为了在DOM文档中定位特定节点而创建的,因此它对XML处理非常重要.很多浏览器实现了`DOM Level3 XPath`标准(IE除外).

### DOM Level 3 XPath
`DOM Level3 XPath`规范定义了接口,用于在DOM中求值XPath表达式.

`XPathEvaluator`用于在特定上下文中求值XPath表达式,包含3个方法:
- `createExpression(expression, nsresolver)`:用于根据XPath表达式及相应的命名空间计算得到一个`XPathExpression`,`XPathExpression`是查询的编译版本.这适合于同样的查询要多次的情况.
- `createNSResolver(node)`:基于`node`的命名空间创建新的`XPathNSResolver`对象.当对使用名称空间的XML文档求值时,需要`XPathNSResolver`对象.
- `evaluate(expression, context, nsresolver, type, result)`:根据给定的上下文和命名空间对XPath进行求值.其他参数表示如何返回结果.

`Document`类型通常是通过`XPathEvaluator`接口实现的,因此可以创建`XPathEvaluator`的实例,或使用`Document`实例上的方法.

`evaluate()`方法接收5个参数:`XPath`表达式,上下文节点,命名空间解析器,返回的结果类型和`XPathResult`对象(用于填充结果,通常是`null`,因为结果也可能是函数值).第三个参数,只在XML代码使用XML命名空间的情况下有必要.如果没有使用命名空间,这个参数也应该是`null`.第四个参数是如下10个常量值之一:
- `XPathResult.ANY_TYPE`:返回适合XPath表达式的数据类型.
- `XPathResult.NUMBER_TYPE`:返回数值.
- `XPathResult.STRING_TYPE`:返回字符串值.
- `XPathResult.BOOLEAN_TYPE`:返回布尔值.
- `XPathResult.UNORDERED_NODE_ITERATOR_TYPE`:返回匹配节点的集合,但集合中的节点的顺序可能与它们在文档中的顺序不一样.
- `XPathResult.ORDERED_NODE_ITERATOR_TYPE`:返回匹配节点的集合,集合中的节点的顺序与它们在文档中的顺序一样.这是非常常用的结果类型.
- `XPathResult.UNORDERED_NODE_SNAPSHOT_TYPE`:返回节点集合的快照,在文档外部捕获节点,因此对文档的进一步修改不会影响这个节点集合.集合中节点的顺序可能与它们在文档中的顺序不一致.
- `XPathResult.ORDERED_NODE_SNAPSHOT_TYPE`:返回节点集合的快照,在文档外部捕获节点,因此对文档的进一步修改不会影响这个节点集合.集合中节点的顺序与它们在文档中的顺序一致.
- `XPathResult.ANY_UNORDERED_NODE_TYPE`:返回匹配节点的集合,但集合中节点的顺序可能与它们在文档的顺序不一致.
- `XPathResult.FIRST_ORDERED_NODE_TYPE`:返回只有一个节点的节点集合,包含文档中第一个匹配的节点.

指定的结果类型决定了如何获取结果的值:
````JS
let result = xmldom.evaluate("employee/name", xmldom.documentElement, null, XPathResult.ORDERED_NODE_ITERATOR_TYPE, null);
if (result !== null) {
    let element = result.iterateNext();
    while (element) {
        console.log(element.tagName);
        node = result.iterateNext();
    }
}
````

这个例子使用了`XPathResult.ORDERED_NODE_ITERATOR_TYPE`结果类型,也是最常用的类型.如果没有节点匹配XPath表达式,`evaluate()`方法返回`null`;否则,返回`XPathResult`对象.返回的`XPathResult`对象上有相应的属性和方法用于获取特定类型的结果.如果结果是节点迭代器,无论是有序还是无序,都必须使用`iterateNext()`方法获取结果中的每个匹配节点.在没有更多匹配节点时,`iterateNext()`返回`null`.

如果指定了快照结果类型(无论有序还是无序),都必须使用`snapshotItem()`方法和`snapshotLength`属性获取结果:
````JS
let result = xmldom.evaluate("employee/name", xmldom.documentElement, null, XPathResult.ORDERED_NODE_SNAPSHOT_TYPE, null);
if (result !== null) {
    for (let i = 0, len = result.snapshotLength; i < len; ++i) {
        console.log(result.snapshotItem(i).tagName);
    }
}
````

### 单个节点结果
`XPathResult.FIRST_ORDERED_NODE_TYPE`结果类型返回匹配的第一个节点,可以通过结果的`singleNodeValue`属性获取.比如:
````JS
let result = xmldom.evaluate("employee/name", xmldom.documentElement, null, XPathResult.FIRST_ORDERED_NODE_TYPE, null);
if (result !== null) {  // 如果没有匹配的节点,evaluate()返回null
    console.log(result.singleNodeValue.tagName);
}
````

### 简单类型结果
使用布尔值,数值,字符串`XPathResult`类型,可以根据XPath获取简单,非节点数据类型.这些结果类型返回的值需要分别使用`booleanValue`,`numberValue`和`stringValue`属性获取.

对于布尔值类型,如果至少有一个节点匹配XPath表达式,`booleanValue`就是`true`;否则,`booleanValue`为`false`.

对于数值类型,XPath表达式必须使用返回数值的XPath函数,如`count()`可以计算匹配给定模式的节点数:
````JS
let result = xmldom.evaluate("count(employee/name)", xmldom.documentElement, null, XPathResult.NUMBER_TYPE, null);
console.log(result.numberValue);
````

如果没有指定XPath函数,`numberValue`就等于`NaN`.

对于字符串类型,`evaluate()`方法查找匹配XPath表达式的第一个节点,然后返回其第一个子节点的值,前提是第一个子节点是文本节点.如果不是,就返回空字符串.

### 默认类型结果
所有XPath表达式都会自动映射到特定类型的结果.设置特定结果类型会限制表达式的输出.不过,可以使用`XPathResult.ANY_TYPE`类型让求值自动返回默认类型结果.通常,默认类型结果式布尔值,数值,字符串或无序节点迭代器.要确定返回的结果类型,可以访问求值结果的`resultType`属性,如下例所示:
````JS
let result = xmldom.evaluate("employee/name", xmldom.documentElement, null, XPathResult.ANY_TYPE, null);
if (result !== null) {
    switch (result.resultType) {
        case XPathResult.STRING_TYPE:
            // ...
            break;
        case XPathResult.NUMBER_TYPE:
            // ...
            break;
        case XPathResult.BOOLEAN_TYPE:
            // ...
            break;
        case XPathResult.UNORDERED_NODE_ITERATOR_TYPE:
            // ...
            break;
        default:
            // ...
    }
}
````

使用`XPathResult.ANY_TYPE`可以让使用XPath变得更自然,但在返回结果后则需要增加额外的判断和处理.

### 命名空间支持
对于使用命名空间的XML文档,必须告诉`XPathEvaluator`命名空间信息,才能进行正确求值.

第一个处理命名空间的方式是通过`createNSResolver()`方法创建`XPathNSResolver`对象.这个方法只接收一个参数,即包含命名空间定义的文档节点,将该节点传给`createNSResolver()`然后得到的结果就可以在`evaluate()`方法中使用:
````JS
let nsresolver = xmldom.createNSResolver(xmldom.documentElement);
let result = xmldom.evaluate("wrox:book/wrox:author", xmldom.documentElement, nsresolver, XPathResult.ORDERED_NODE_SNAPSHOT_TYPE, null);
console.log(result.snapshotLength);
````

如果在包含命名空间的XML中不传入`XPathNSResolver`,则同样的表达式会导致错误.

第二种处理命名空间的方式是定义一个接收命名空间前缀并返回相应URI的函数:
````JS
let nsresolver = function(prefix) {
    switch (prefix) {
        case "wrox": return "http://www.wrox.com/";
        // ...
    }
};
let result = xmldom.evaluate("count(wrox:book/wrox:author)", xmldom.documentElement, nsresolver, XPathResult.NUMBER_TYPE, null);
console.log(result.numberValue);
````

在并不知晓文档的哪个节点包含命名空间定义时,可以采用这种定义命名空间解析函数的方式.只要知道前缀和URI,就可以定义这样一个函数,然后把它作为第三个参数传给`evaluate()`.

## 浏览器对XSLT的支持
可扩展样式表语言转换(XSLT, Extensible Stylesheet Language Transformations)是与XML相伴的一种技术,可以利用XPath将一种文档表示转换为另一种文档表示.XSLT没有正式API,DOM中也没有涵盖它.

### XSLTProcessor类型
`XSLTProcessor`类型可以使用`XSLT`转换`XML`文档.第一步是加载两个DOM文档:XML文档和XSLT文档.然后,创建一个新的`XSLTProcessor`,使用`importStyleSheet()`方法将XSLT指定给它:
````JS
let processor = new XSLTProcessor();
processor.importStylesheet(xsltdom);
````

然后执行转换,有两种方式.如果想返回完整的DOM文档,就调用`transformToDocument()`.如果想得到文档片段,则可以调用`transformToFragment()`.

使用`transfromToDocument()`只要传给它XML DOM,就可以将结果当作另一个完全不同的DOM来使用:
````JS
let result = processor.transformToDocument(xmldom);
console.log(result);
````

`transformToFragment()`方法接收两个参数:要转换的XML DOM和最终会拥有结果片段的文档.这可以确保新文本片段可以在目标文档中使用:
````JS
let fragment = processor.transformToFragment(xmldom, document);
let div = document.getElementById("divResult");
div.appendChild(fragment);
````

注意,拥有文档片段不代表其存在于文档的DOM树中.

如果输出格式为`"text"`,则通常意味着只想得到转换后的文本结果.但没有方法能够直接返回文本.`transfromToDocument()`在不同浏览器中的表现会不同.对于`transformToFragment()`,返回包含此文本的一个节点,因此可以通过以下方式取得文本:
````JS
let fragment = processor.tranformToFragment(xmldom, document);
let text = fragment.firstChild.nodeValue;
console.log(text);
````

### 使用参数
`XSLTProcessor`还允许使用`setParameter()`方法设置XSLT参数.该方法接收三个参数:命名空间URI,参数本地名称和要设置的值.通常,命名空间URI是`null`,本地名称就是参数名称.`setParameter()`方法必须在调用`transfromToDocument()`或`transformToFragment()`之前调用.

还有相关的两个方法是`getParameter()`和`removeParameter()`.它们分别用于取得参数的当前值和移除参数的值.它们都以一个命名空间URI(同样一般是`null`)和参数的本地名称为参数:
````JS
let processor = new XSLTProcessor();
processor.importStylesheet(xsltdom);
processor.setParameter(null, "message", "Hello World!");
console.log(processor.getParameter(null, "message"));   // "Hello World!"
processor.removeParameter(null, "message");
let result = processor.transformToDocument(xmldom);
````

### 重置处理器
每个`XSLTProcessor`实例都可以重用于多个转换,只是要使用不同的XSLT样式表.处理器的`reset()`方法可以删除所有参数和样式表.然后,可以使用`importStylesheet()`方法加载不同的XSLT样式表.

在使用多个样式表执行转换时,重用一个`XSLTProcessor`可以节省内存.

# JSON
JavaScript对象简谱(JSON, JavaScript Object Notation)是JavaScript的严格子集,利用JS中的几个模式来表示结构化数据.其作为代替XML到达一个方案提出,因为JSON可以直接传给`eval()`而不需要创建DOM.

JSON是一种数据格式,而不是编程语言.JSON不属于JavaScript,它们只是拥有相同的语法而已.JSON也不是只能在JS中使用,它是一种通用数据格式.

## 语法
JSON语法支持表示3种类型的值.
- `简单值`:字符串,数值,布尔值,`null`可以在JSON中出现,但`undefined`不可以.
- `对象`:第一种复杂数据类型,对象表示有序的键值对.每个值可以是简单值,也可以是复杂值.
- `数组`:第二种复杂数据类型,数组表示可以通过数值索引访问的值的有序列表.数组的值可以是任意类型,包括简单值,对象,甚至其他数组.

JSON没有变量,函数或对象实例的概念.

### 简单值
- 数值.例如:`5`.
- 字符串,必须使用双引号.例如:`"Hello world!`.
- 布尔值.`true`和`false`.
- `null`

### 对象
JSON表示对象的语法:
````JSON
{
    "name": "aaa",
    "age": 18
}
````
JSON对象的键始终应该是字符串,值可以为任意类型.

### 数组
JSON表示数组的语法:
````JSON
[
    1,
    {
        "name": "aaa",
        "age": 18
    },
    "student"
]
````

## 解析与序列化
### JSON对象
`JSON`全局对象有两个方法:`stringify()`和`parse()`.在简单情况下,这两个方法分别可以将JS序列化为JSON字符串,以及将JSON解析为原生JS值:
````JS
let book = {
    title: "Professional JavaScript",
    authors: [
        "Nicholas C. Zakas",
        "Matt Frisbie"
    ],
    edition: 4,
    year: 2017
};
let jsonText = JSON.stringify(book);
````

默认情况下,`JSON.stringify()`会输出不包含空格或缩进的JSON字符串,因此,`jsonText`的值是这样的:
````JSON
{"title":"Professional JavaScript","authors":["Nicholas C. Zakas","Matt Frisbie"],"edition":4,"year":2017}
````

在序列化JS对象时,所有函数和原型成员都会有意地在结果中省略.此外,值为`undefined`的任何属性也会被跳过.最终得到的就是所有实例属性均为有效JSON数据类型的表示.

`JSON`字符串可以直接传给`JSON.parse()`,然后得到对应的JS值.例如:
````JS
let bookCopy = JSON.parse(jsonText);
````

注意,`book`和`bookCopy`是两个完全不同的对象,没有任何关系.但是它们拥有相同的属性和值.如果给`JSON.parse()`传入的JSON字符串无效,则会导致抛出错误.

### 序列化选项
`JSON.stringify()`方法除了要序列化的对象,还可以接收两个参数.这两个参数可以用于指定其他序列化JS对象的方式.第一个参数是过滤器,可以是数组或函数;第二个参数是用于缩进结果JSON字符串的选项.单独或组合使用这些参数可以更好地控制JSON序列化.

#### 过滤结果
如果第二个参数是一个数组,那么`JSON.stringify()`返回的结果只会包含该数组中列出的对象属性:
````JS
let book = {
    title: "Professional JavaScript",
    authors: [
        "Nicholas C. Zakas",
        "Matt Frisbie"
    ],
    edition: 4,
    year: 2017
};
let jsonText = JSON.stringify(book, ["title", "edition"]);
````
则结果的JSON字符串中只会包含`title`和`edition`两个属性:
````JSON
{"title":"Professional JavaScript","edition":4}
````

如果第二个参数是一个函数,提供的函数接收两个参数:属性名(key)和属性值(value).可以根据这个`key`决定要对相应属性执行什么操作.这个`key`始终是字符串,只是在值不属于某个键值对时会是空字符串.为了改变对象的序列化,返回的值就是相应`key`应该包含的结果,返回`undefined`则表示属性应该被忽略:
````JS
let book = {
    title: "Professional JavaScript",
    authors: [
        "Nicholas C. Zakas",
        "Matt Frisbie"
    ],
    edition: 4,
    year: 2017
};
let jsonText = JSON.stringify(book, (key, value) => {
    switch (key) {
        case "authors":
            return value.join(",");
        case "year":
            return 5000;
        case "edition":
            return undefined;
        default:
            return value;
    }
});
````
第一次调用该函数实际上会传入空字符串`key`,值是`book`对象.  
最终得到的JSON字符串是:
````JSON
{"title":"Professional JavaScript","authors":"Nicholas C. Zakas,Matt Frisbie","year":5000}
````

#### 字符串缩进
`JSON.stringify()`方法的三个参数控制缩进和空格.在这个参数是数值时,表示每一级缩进的空格数:
````JS
let jsonText = JSON.stringify(book, null, 4);
````
得到的`jsonText`格式如下:
````JSON
{
    "title": "Professional JavaScript",
    "authors": [
        "Nicholas C. Zakas",
        "Matt Frisbie"
    ],
    "edition": 4,
    "year": 2017
}
````
除了缩进,`JSON.stringify()`方法还为方便阅读插入了换行符.这个行为对于所有有效的缩进参数都会发生.最大缩进值为10,大于10的值会自动设置为10.

如果缩进参数是一个字符串而非数值,那么JSON字符串中就会使用这个字符串而不是空格来缩进:
````JS
let jsonText = JSON.stringify(book, null, "--");
````
得到的`jsonText`格式如下:
````JSON
{
--"title": "Professional JavaScript",
--"authors": [
----"Nicholas C. Zakas",
----"Matt Frisbie"
--],
--"edition": 4,
--"year": 2017
}
````
使用字符串时同样有10个字符的长度限制.如果字符串的长度超过10,则会在第10个字符处截断.

### toJSON()方法
有时候,对象需要在`JSON.stringify()`之上自定义JSON序列化.此时,可以在要序列化的对象中添加`toJSON()`方法,序列化时会基于这个方法返回适当的JSON表示.事实上,原生`Date`对象就有一个`toJSON()`方法,能够自动将JS的Date对象转换为`ISO 8601`日期字符串(本质上与在Date对象上调用`toISOString()`方法一样).

例如:
````JS
let book = {
    title: "Professional JavaScript",
    authors: [
        "Nicholas C. Zakas",
        "Matt Frisbie"
    ],
    edition: 4,
    year: 2017
    toJSON: function() {
        return this.title;
    }
};
let jsonText = JSON.stringify(book);
````

由于`toJSON()`方法直接返回了`this.title`,因此该对象会被序列化为简单字符串而非对象.

`toJSON()`方法可以返回任意序列化值,都可以起到相应的作用.如果对象被嵌入在另一个对象中,返回`undefined`会导致值变成`null`;如果是顶级对象,则返回`undefined`相当于返回本身.

把对象传给`JSON.stringify()`时会执行如下步骤:
1. 如果可以获取实际的值,则调用`toJOSN()`方法获取实际的值,否则使用默认的序列化.
2. 如果提供了第二个参数,则应用过滤.传入过滤函数的值就是第一步返回的值.
3. 第二步返回的每个值都会相应地进行序列化.
4. 如果提供了第三个参数,则相应地进行缩进.

### 解析选项
`JSON.parse()`方法也可以接收一个额外的参数,这个函数会针对每个键值对都调用一次.为区别于传给`JSON.stringify()`的起过滤作用的*替代函数(replacer)*,这个函数被称为*还原函数(reviver)*.还原函数也接收两个参数,属性名(key)和属性值(value),另外也需要返回值.

如果还原函数返回`undefined`,则结果中就会删除相应的键.如果返回了其他任何值,则该值就会成为相应键的值插入到结果中.例如:
````JS
let book = {
    title: "Professional JavaScript",
    authors: [
        "Nicholas C. Zakas",
        "Matt Frisbie"
    ],
    edition: 4,
    year: 2017,
    releaseDate: new Date(2017, 11, 1)
};
let jsonText = JSON.stringify(book);
let bookCopy = JSON.parse(jsonText,
    (key, value) => key == "releaseDate" ? new Date(value) : value);
console.log(bookCopy.releaseDate.getFullYear());
````

# 网络请求与远程资源
`Ajax`(Asynchronous JavaScript+XML)技术涉及发送服务器请求额外数据而不刷新页面,从而实现更好的用户体验.虽然`Ajax`名字中包含XML,但实际上Ajax通信与数据格式无关.

`XHR`(XMLHttpRequest)对象为开发者提供了原生的浏览器通信能力,而之后诞生的`Fetch API`支持期约和服务线程,用于代替比较难用的`XHR`对象的API.`XMLHttpRequest`实际上是过时Web规范的产物(虽然标准并没有废弃),应该只在旧版本浏览器中使用.实际开发中,应该尽可能使用`fetch()`.

## XMLHttpRequest
*此部分内容会作简化.详细内容,见[MDN-XHR](https://developer.mozilla.org/zh-CN/docs/Glossary/XMLHttpRequest)*

通过使用`XMLHttpRequest`构造函数来创建`XHR`对象:
````JS
let xhr = new XMLHttpRequest();
````

### 使用XHR
使用XHR对象首先要调用`open()`方法,这个方法接收3个参数:请求类型(`"get"`,`"post"`等),请求URL,以及表示请求是否异步的布尔值.  
例如:`xhr.open("get", "example.php", false);`

上面代码中的URL可以使用相对URL,也可以使用绝对URL.调用`open()`不会实际发送请求,只是为发送请求做好准备.

注意:只能访问同源URL,也就是域名相同,端口相同,协议相同.否则会抛出安全错误.

要发送定义好的请求,需要调用`send()`方法.该方法接收一个参数,是作为请求体发送的数据.如果不需要发送请求体,则必须传`null`.调用`send()`之后,请求就会发送到服务器.  
例如:`xhr.send(null);`

收到相应后,XHR对象的以下属性会被填充上数据:
- `responseText`:作为相应体返回的文本.
- `responseXML`:如果相应的内容类型是`"text/xml"`或`"application/xml"`,那就是包含响应数据的XML DOM文档.
- `status`:响应的HTTP状态.
- `statusText`:响应的HTTP状态描述.

收到响应后,第一步要检查`status`属性以确保响应成功返回.一般来说,HTTP状态码为`2XX`表示成功.此时,`responseText`或`responseXML`(如果内容类型正确)属性中会有内容.如果`HTTP`状态码是`304`,则表示资源未修改过,是从浏览器缓存中直接拿取的,当然这也意味着响应有效.

无论是什么响应内容类型,`responseText`属性始终会保存响应体,而`responseXML`则对于非XML数据是`null`.

如果是异步请求,XHR对象有一个`readyState`属性,表示当前处在请求/响应过程的哪个阶段.这个属性有如下可能的值:
- `0`:未初始化(Uninitialized).尚未调用`open()`方法.
- `1`:已打开(Open).已调用`open()`方法,尚未调用`send()`方法.
- `2`:已发送(Sent).已调用`send()`方法,尚未收到响应.
- `3`:接收中(Receiving).已经收到部分响应.
- `4`:完成(Complete).已经收到所有响应,可以使用了.

每次`readyState`从一个值变成另一个值,都会触发`readystatechange`事件.可以借此机会检查`readyState`的值.为确保兼容性,应当在调用`open()`之前设置事件处理程序.该事件处理程序不会收到`event`对象.

在收到响应之前如果想取消异步请求,可以调用`abort()`方法:`xhr.abort();`.调用这个方法后,XHR对象会停止触发事件,并阻止访问这个对象上任何与响应相关的属性.中断请求后,应该取消对XHR对象的引用.

由于内存问题,不推荐重用XHR对象.

### HTTP头部
每个HTTP请求和响应都会携带一些头部字段(*请求标头*和*响应标头*),这些字段可能对开发者有用.XHR对象会通过一些方法暴露与请求和响应相关的头部字段.

默认情况下,`XHR`请求会发送以下头部字段:
- `Accept`:浏览器可以处理的内容类型.
- `Accept-Charset`:浏览器可以显示的字符集.
- `Accept-Encoding`:浏览器可以处理的压缩编码类型.
- `Accept-Language`:浏览器使用的语言.
- `Connection`:浏览器与服务器的连接类型.
- `Cookie`:页面中设置的`Cookie`.
- `Host`:发送请求的页面所在的域.
- `Referer`:发送请求的页面的URI.注意,这个字段在HTTP规范中就拼错了,所以考虑到兼容性也必须将错就错.(正确的拼写应该是`Referrer`)
- `User-Agent`:浏览器的用户代理字符串.

虽然不同浏览器发送的确切头部字段可能各不相同,但这些通常都是会发送的.如果需要发送额外的请求头部,可以使用`setRequestHeader()`方法.这个方法接收两个参数:头部字段的名称和值.为保证请求头部被发送,必须在`open()`之后,`send()`之前调用`setRequestHeader()`:
````JS
xhr.setRequestHeader("MyHeader", "MyValue");
````

服务器通过读取自定义头部可以确定适当的操作.自定义头部一定要区别于浏览器正常发送的头部,否则可能会影响服务器正常响应.有些浏览器不允许重写默认头部.

可以使用`getResponseHeader()`方法从XHR对象获取响应头部,只要传入要获取头部的名称即可.如果想取得所有响应头部,可以使用`getAllResponseHeaders()`方法,这个方法会返回包含所有响应头部的字符串.

以下是`getAllResponseHeaders()`可能返回的值:
```
Date: Sun, 14 Nov 2004 18:04:03 GMT
Server: Apache/1.3.29
Vary: Accept
X-Powered-By: PHP/4.3.8
Connection: close
Content-Type: text/html; charset=iso-8859-1
```

### GET请求
最常用的请求方法是GET请求,用于向服务器查询某些信息.必要时,需要在GET请求的URL后面添加查询字符串参数.对XHR而言,查询字符串必须正确编码后添加到URL后面,然后再传给`open()`方法.

发送GET请求的查询字符串中的每个名和值都必须使用`encodeURIComponent()`编码,所有名值对必须以`&`分隔:
````JS
xhr.open("get", "example.php?name1=value1&name2=value2", true);
````

### POST请求
第二个最常用的请求是`POST`请求,用于向服务器发送应该保存的数据.每个`POST`请求都应该再请求体中携带提交的数据.每个`POST`请求都应该在请求体中携带提交数据,而GET请求则不然.`POST`请求的请求体可以包含非常多的数据,而且数据可以是任意格式.要初始化`POST`请求,`open()`方法的第一个参数要传`"post"`.

接下来就是要给`send()`方法传入要发送的数据.因为XHR最初主要设计用于发送XML,所以可以传入序列化之后的XML DOM文档作为请求体.当然,也可以传入任意字符串.

默认情况下,对服务器而言,POST请求与提交表单是不一样的.服务器逻辑需要读取原始POST数据才能取得浏览器发送的数据.不过,可以使用XHR模拟表单提交.为此,都一部需要把`Content-Type`头部设置为`application/x-www-formurlencoded`,这是提交表单时使用的内容类型.第二步是创建对应格式的字符串.POST数据此时使用与查询字符串相同的格式.如果网页中确实有一个表单需要序列化并通过XHR发送到服务器,可以使用[表单序列化](#表单序列化)中所提及的函数来创建相应的字符串.

*注意:POST请求相比GET请求要占用更多资源.从性能方面来说,发送相同数量的数据,GET请求比POST请求要快两倍.*

### XMLHttpRequest Level2
#### FormData类型
`FormData`类型便于表单序列化,也便于创建与表单类似格式的数据然后通过XHR发送:
````JS
let data = new FormData();
data.append("name", "aaa");
````

`append()`方法接收两个参数:键和值,相当于表单字段和该字段的值.可以像这样添加任意多个键值对数据,此外,通过直接给`FormData`构造函数传入一个表单元素,也可以将表单中的数据作为键值对填充进去:
````JS
let xhr = new XMLHttpRequest();
xhr.open("post", "example.php", true);
let data = new FormData(document.forms[0]);
xhr.send(data);
````

使用`FormData`的另一个方便之处是不再需要给XHR对象显示设置任何请求头部了.XHR对象能够识别作为`FormData`实例传入的数据类型并自动配置相应的头部.

#### 超时
XHR的`timeout`属性用于表示发送请求后等待多少毫秒,如果响应不成功就中断请求.当给`timeout`属性设置了一个时间且在该时间过后没有收到响应时,XHR对象就会触发`timeout`事件,而`readyState`仍然会变成4,但此时访问其`status`属性会抛出错误.为做好防护,可以把`readystatechange`事件处理程序中检查`status`属性的代码封装在`try/catch`语句中.

#### overrideMimeType()方法
`overrideMimeType()`方法用于重写XHR响应的MIME类型.服务器响应返回的MIME类型决定了XHR对象如何处理响应,所以如果有办法覆盖服务器返回的类型,那么是有帮助的.

假设服务器实际发送了XML数据,但响应头设置的MIME类型是`text/plain`.结果就会导致数据是XML,但`responseXML`属性值是`null`.此时调用`overrideMimeType()`可以保证将响应当成XML而不是纯文本来处理:
````JS
let xhr = new XMLHttpRequest();
xhr.open("get", "text.php", true);
xhr.overrideMimeType("text/xml");
xhr.send(null);
````

必须在调用`send()`之前调用`overrideMimeType()`.

## 进度事件
`Progress Events`定义了客户端-服务器端通信.这些事件最初只针对XHR,现在也推广到了其他类似的API.有以下6个进度相关的事件.
- `loadstart`:在接收到响应的第一个字节时触发.
- `progress`:在接收响应期间反复触发.
- `error`:在请求出错时触发.
- `abort`:在调用`abort()`终止连接时触发.
- `load`:在成功接收完响应时触发.
- `loadend`:在通信完成时,且在`error`,`abort`或`load`之后触发.

每次请求都会首先触发`loadstart`事件,之后是一个或多个`progress`事件,接着是`error`,`abort`或`load`中的一个,最后以`loadend`事件结束.

以下是[MDN](https://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest/load_event)上的一个示例:
````JS
const xhrButtonSuccess = document.querySelector(".xhr.success");
const xhrButtonError = document.querySelector(".xhr.error");
const xhrButtonAbort = document.querySelector(".xhr.abort");
const log = document.querySelector(".event-log");

function handleEvent(e) {
  log.textContent =
    log.textContent + `${e.type}: ${e.loaded} bytes transferred\n`;
}

function addListeners(xhr) {
  xhr.addEventListener("loadstart", handleEvent);
  xhr.addEventListener("load", handleEvent);
  xhr.addEventListener("loadend", handleEvent);
  xhr.addEventListener("progress", handleEvent);
  xhr.addEventListener("error", handleEvent);
  xhr.addEventListener("abort", handleEvent);
}

function runXHR(url) {
  log.textContent = "";

  const xhr = new XMLHttpRequest();
  addListeners(xhr);
  xhr.open("GET", url);
  xhr.send();
  return xhr;
}

xhrButtonSuccess.addEventListener("click", () => {
  runXHR("dgszyjnxcaipwzy.jpg");
});

xhrButtonError.addEventListener("click", () => {
  runXHR("https://somewhere.org/i-dont-exist");
});

xhrButtonAbort.addEventListener("click", () => {
  runXHR("dgszyjnxcaipwzy.jpg").abort();
});
````
按下`xhrButtonSuccess`:
```
loadstart: 0 bytes transferred
progress: 1381 bytes transferred
progress: 13891 bytes transferred
progress: 32768 bytes transferred
progress: 35539 bytes transferred
progress: 36929 bytes transferred
progress: 42489 bytes transferred
progress: 48049 bytes transferred
progress: 56380 bytes transferred
progress: 62373 bytes transferred
load: 62373 bytes transferred
loadend: 62373 bytes transferred
```
按下`xhrButtonError`:
```
loadstart: 0 bytes transferred
error: 0 bytes transferred
loadend: 0 bytes transferred
```
按下`xhrButtonAbort`:
```
loadstart: 0 bytes transferred
abort: 0 bytes transferred
loadend: 0 bytes transferred
```

必须在调用`open()`之前添加这些事件处理程序.

### progress事件
`progress`事件的`event`对象包含3个额外属性:
- `lengthComputable`:一个布尔值,表示进度信息是否可用.
- `position`:接收到的字节数.
- `totalSize`:响应的`Content-Length`头部定义的总字节数.

假设响应有`Content-Length`头部,就可以利用这些信息计算出已经收到响应的百分比.

## 跨源资源共享
通过XHR进行Ajax通信的一个主要限制是跨源安全策略.默认情况下,XHR只能访问与发起请求的网页在同一个域内的资源.这个安全限制可以防止某些恶意行为.不过,浏览器也需要支持合法跨源访问的能力.

跨源资源共享(CORS, Cross-Origin Resource Sharing)定义了浏览器域服务器如何实现跨源通信.CORS背后的基本思路就是使用自定义的HTTP头部允许浏览器和服务器相互了解,以确实请求或响应应该成功还是失败.

对于简单的请求,比如GET或POST请求,没有自定义头部,而且请求体是`text/plain`类型,这样的请求在发送是会有一个额外的头部叫`Origin`.`Origin`头部包含发送请求的页面的源(协议,域名和端口),以便服务器确定是否为其提供响应.可能的`Origin`头部:`Origin: https://somewhere.org`

如果服务器决定响应请求,那么应该发送`Access-Control-Allow-Origin`头部,包含相同的源.或者如果资源是公开的,那么就包含`"*"`.一个可能的示例:`Access-Control-Allow-Origin: https://somewhere.org`.

如果没有这个头部,或者有但源不匹配,则表明不会响应浏览器请求.否则,服务器就会处理这个请求.注意,无论请求还是响应都不会包含`cookie`信息.

`XMLHttpRequest`支持`CORS`.在尝试访问不同源的资源时,这个行为会被自动触发.要向不同域发送请求,可以使用标准XHR对象并给`open()`方法传入一个绝对URL(其他域).

跨域XHR对象允许访问`status`和`statusText`属性,也允许同步请求.出于安全考虑,跨域XHR对象也施加了一些额外限制:
- 不能使用`setRequestHeader()`设置自定义头部.
- 不能发送和接收`cookie`.
- `getAllResponseHeaders()`方法始终返回空字符串.

### 预检请求
CORS通过一种叫预检请求的服务器验证机制,允许使用自定义头部,除GET和POST以外的方法,以及不同请求体内容类型.在要发送涉及上述某种高级选项的请求时,会先向服务器发送一个"预检"请求.这个请求使用`OPTIONS`方法发送并包含以下头部:
- `Origin`:与简单请求相同.
- `Access-Control-Request-Method`:请求希望使用的方法.
- `Access-Control-Request-Headers`:(可选)要使用的逗号分隔的自定义头部列表.

下面是一个假设的POST请求,包含自定义的NCZ头部:
```
Origin: https://somewhere.org
Access-Control-Request-Method: POST
Access-Control-Request-Headers: NCZ
```

在这个请求发送后,服务器可以确定是都允许这种类型的请求.服务器会通过在响应中发送如下头部与浏览器沟通这些信息:
- `Access-Control-Allow-Origin`:与简单请求相同.
- `Access-Control-Allow-Methods`:允许的方法(逗号分隔的列表).
- `Access-Control-Allow-Headers`:服务器允许的头部(逗号分隔的列表).
- `Access-Control-Max-Age`:缓存预检请求的秒数.

例如:
```
Access-Control-Allow-Origin: https://somewhere.org
Access-Control-Allow-Methods: POST, GET
Access-Control-Allow-Headers: NCZ
Access-Control-Max-Age: 1728000
```
预检请求返回后,结果会按响应指定的事件缓存一段时间.换句话说,只有第一次发送这种类型请求时才会多发送一次额外的HTTP请求.

### 凭据请求
默认情况下,跨源请求不提供凭据(cookie,HTTP认证和客户端SSL证书).可以通过将`withCredentials`属性设置为`true`来表明请求会发送凭据.如果服务器允许带凭据的请求,那么可以在响应中包含如下HTTP头部:
```
Access-Control-Allow-Credentials: true
```

如果发送了凭据请求而服务器返回的响应中没有这个头部,则浏览器不会把响应交给JS(`responseText`是空字符串,`status`是0,`onerror()`被调用).注意,服务器也可以在预检请求的响应中发送这个HTTP头部,以表明这个源允许发送凭据请求.

## 替代性跨源技术
该部分是有关CORS出现前如何实现跨源Ajax通信的.

使用`<img>`元素可以跨源加载的特性,通过将`src`设置为其他域并设置查询字符串发送,根据`load`和`error`事件来判断何时接收到响应.

`JSONP`(JSON with padding)让服务器收到响应后回调指定函数并传入数据,以达到跨源通信的效果.在请求时,通常使用查询字符串:`callback=func`,其中,`func`指的是服务器应该回调的函数:
````JS
function handleResponse(response) {
    console.log(`IP: ${response.ip}, city: ${response.city}`)
}
let script = document.createElement("script");
script.src = "https://freegeoip.net/json/?callback=handleResponse";
document.body.insertBefore(script, document.body.firstChild);
````

注意:上述两种方法已经过时,而且都有缺陷.

## Fetch API
`Fetch API`能够执行`XMLHttpRequest`对象的所有任务,但更容易使用,接口也更现代化,能够在Web工作线程等现代Web工具中使用.`XMLHttpRequest`可以选择异步,而`Fetch API`则必须是异步.`Fetch API`是WHATWG的一个"活标准"(living standard),用规范原文说,就是"Fetch标准定义请求,响应,以及绑定二者的流程:获取(fetch)".

`Fetch API`本身是使用JS请求资源的优秀工具,同时这个API也能够应用在服务线程中,提供拦截,重定向和修改通过`fetch()`生成的请求接口.

[MDN上的Fetch API](https://developer.mozilla.org/zh-CN/docs/Web/API/Fetch_API)

### 基本用法
`fetch()`方法是暴露在全局作用域中的,包括主页面执行线程,模块和工作线程.调用这个方法,浏览器就会向给定URL发送请求.

#### 分派请求
`fetch()`只有一个必需的参数`input`.多数情况下,这个参数是要获取资源的URL.这个方法返回一个期约:
````JS
let r = fetch('/bar');  // 相对路径
console.log(r); // Promise <pending>
````

请求完成,资源可用时,期约会解决为一个`Response`对象.这个对象是API的封装,可以通过它取得相应资源.获取资源要使用这个对象的属性和方法,掌握响应的情况并将负载转换为有用的形式:
````JS
fetch('bar.txt')
  .then((response) => {
    console.log(response);
  });
// Response { type: "basic", url: ... }
````

#### 读取响应
读取响应内容的最简单方式是取得纯文本格式的内容,这要用到`text()`方法.这个方法返回一个期约,会解决为取得资源的完整内容:
````JS
fetch('bar.txt')
  .then((response) => {
    response.text().then((data) => {
        console.log(data);
    });
  });
// vvv通常写成下面的样子
fetch('bar.txt')
  .then((response) => response.text())
  .then((data) => console.log(data));
// 输出bar.txt的内容
````

#### 处理状态码和请求失败
`Fetch API`支持通过`Response`的`status`(状态码)和`statusText`(状态文本)属性检查响应状态.成功获取响应的请求通常会产生值为`200`的状态码:
````JS
fetch('bar.txt')
  .then((response) => {
    console.log(response.status);       // 200
    console.log(response.statusText);   // OK
  });
````

请求不存在的资源通常会产生值为`404`的状态码:
````JS
fetch('bar.txt')
  .then((response) => {
    console.log(response.status);       // 404
    console.log(response.statusText);   // Not Found
  });
````

请求的URL如果抛出服务器错误会产生值为`500`的状态码.

更多状态码详见[MDN-HTTP 响应状态码](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Status)

可以显式地设置`fetch()`在遇到重定向时的行为([见下文](#自定义选项)),默认行为是跟随重定向并返回状态码不是`300~399`的响应.跟随重定向时,响应对象的`redirected`属性会被设置为`true`,而状态码仍然是`200`(如果请求成功的话).

注意,即使请求是失败的(状态码为404或500等),但期约都算作是**解决**的.事实上,只要服务器返回了响应(即使所指向服务器不存在,但上级服务器仍然返回了服务器不存在的响应),`fetch()`期约都会解决.这个行为是合理的:系统级网络协议已经成功完成消息的一次往返传输.至于真正的"成功"请求,则需要在处理响应时再定义.

`Response`的`ok`只读属性返回一个布尔值,表明响应是否成功(状态码在`200~299`范围内).

当请求失败时(例如浏览器等待超时,URL格式错误,网络错误,违反CORS以及其他浏览器/网络策略问题),都会导致期约被拒绝.

使用`Response`的`url`属性检查通过`fetch()`发送请求时使用的完整URL:
````JS
// 假设foo.com/bar/baz发送的请求
console.log(window.location.href);  // https://foo.com/bar/baz
fetch('qux').then((response) => console.log(response.url));
// https://foo.com/bar/qux
fetch('/qux').then((response) => console.log(response.url));
// https://foo.com/qux
fetch('//qux.com').then((response) => console.log(response.url));
// https://qux.com
fetch('https://qux.com').then((response) => console.log(response.url));
// https://qux.com
````

#### 自定义选项
只使用URL时,`fetch`会发送GET请求,只包含最低限度的请求头.要进一步配置如何发送请求,需要传入可选的第二个参数`init`对象(`RequestInit`类型).详见下文或[MDN-RequestInit(英文)](https://developer.mozilla.org/en-US/docs/Web/API/RequestInit).

`init`对象要按照下表中的键值进行填充:
- 键:
  - 描述
  - 更多描述
- `body`:
  - 指定使用请求体时请求体的内容
  - 必须是`Blob`,`BufferSource`,`FormData`,`URLSearchParams`,`ReadableStream`或`String`的实例
- `cache`:
  - 用于控制浏览器与HTTP缓存的交互.要跟踪缓存的重定向,请求的`redirect`属性值必须是`"follow"`,而且必须符合同源策略限制.必须是下列值之一:
  - `default`
    - `fetch()`返回命中的有效缓存.不发送请求
    - 命中无效(stale)缓存会发送条件式请求.如果响应已经改变,则更新缓存的值.然后`fetch()`返回缓存的值
    - 未命中缓存会发送请求,并缓存响应.然后`fetch()`返回响应
  - `no-store`
    - 浏览器不检查缓存,直接发送请求
    - 不缓存响应,直接通过`fetch()`返回
  - `reload`
    - 浏览器不检查缓存,直接发送请求
    - 缓存响应,再通过`fetch()`返回
  - `no-cache`
    - 无论命中有效缓存还是无效缓存都会发送条件式请求.如果响应已经改变,则更新缓存的值.然后`fetch()`返回缓存的值
    - 未命中缓存会发送请求,并缓存响应.然后`fetch()`返回相应.
  - `force-cache`
    - 无论命中有效缓存还是无效缓存都通过`fetch()`返回.不发送请求
    - 未未命中缓存会发送请求,并缓存响应.然后`fetch()`返回相应
  - `only-if-cached`
    - 只在请求模式为`same-origin`时使用缓存
    - 无论命中有效缓存还是无效缓存都通过`fetch()`返回.不发送请求
    - 未命中缓存返回状态码为`504`(网关超时)的响应
  - 默认为`default`.
- `credentials`:
  - 用于指定在外发请求中如何包含`cookie`.必须是下列字符串之一:
    - `omit`:不发送`cookie`
    - `same-origin`:只在请求URL与发送`fetch()`请求的网页同源时发送`cookie`
    - `include`:无论同源还是跨源都包含`cookie`
  - 在支持`Credential Management API`的浏览器中,也可以是一个`FederatedCredential`或`PasswordCredential`的实例
  - 默认为`same-origin`
- `headers`:
  - 用于指定请求头部
  - 必须是`Headers`对象实例或包含字符串格式键值对的`Object`
  - 默认值为不包含键值对的`Headers`对象.这意味着请求不包含任何头部,浏览器仍然会随请求发送一些头部.虽然这些头部对JS不可见,但浏览器的网络检查器可以观察到
- `integrity`:
  - 用于强制子资源完整性
  - 必须是包含子资源完整性标识符的字符串
  - 默认为空字符串
- `keepalive`:
  - 用于指示浏览器允许请求存在的时间能超出页面生命周期.适合报告事件或分析.设置`keepalive`标志的`fetch()`请求可用于替代`Navigator.sendBeacon()`
  - 必须是布尔值
  - 默认为`false`
- `method`:
  - 用于指定HTTP请求方法
  - 基本上就是如下字符串值:
    - `GET`
    - `POST`
    - `PUT`
    - `PATCH`
    - `DELETE`
    - `HEAD`
    - `OPTIONS`
    - `CONNECT`
    - `TARCE`
  - 默认为`GET`
- `mode`
  - 用于指定请求模式.这个模式决定来自跨源请求的响应是否有效,以及客户端可以读取多少响应.违反这里指定模式的请求会抛出错误
  - 必须是下列字符串值之一:
    - `cors`:允许遵循CORS协议的跨源请求.响应是"CORS过滤的响应",意思是响应中可以访问的浏览器头部是经过浏览器强制白名单过滤的
    - `no-cors`:允许不需要发送预检请求的跨源请求(`HEAD`,`GET`和只带有满足CORS请求头部的`POST`).响应类型是`opaque`,意思是不能读取响应内容
    - `same-origin`:任何跨源请求都不允许发送
    - `navigate`:用于支持HTML导航,只在文档间导航时使用.基本用不到
  - 在通过构造函数手动创建`Request`实例时,默认为`cors`,否则,默认为`no-cors`
- `redirect`
  - 用于指定如果处理重定向响应(状态码为`301`,`302`,`303`,`307`或`308`)
  - 必须是下列字符串值之一:
    - `follow`:跟踪重定向请求,以最终非重定向URL的响应作为最终响应
    - `error`:重定向请求会抛出错误
    - `manual`:不跟踪重定向请求,而是返回`opaqueredirect`类型的响应,同时仍然暴露期望的重定向URL.允许以手动方式跟踪重定向
  - 默认为`follow`
- `referrer`
  - 用于指定HTTP的`Referer`头部
  - 必须是下列字符串值之一:
    - 空字符串或`no-referrer`:以`no-referrer`作为值
    - `about:client`或`client`:以当前URL或`no-referrer`(取决于来源策略`referrerPolicy`)作为值
    - `<URL>`:以伪造URL作为值.伪造URL的源必须与执行脚本的源匹配
  - 默认为`about:client`
- `referrerPolicy`:
  - 用于指定HTTP的`Referer`头部
  - 必须是下列字符串值之一:
    - `no-referrer`:请求中不包括`Referer`头部
    - `no-referrer-when-downgrade`:对于从安全HTTPS上下文发送到HTTP URL的请求,不包含`Referer`头部.对于所有其他请求,将`Referer`设置为完整URL
    - `origin`:对于所有请求,将`Referer`设置为只包含源
    - `same-origin`:对于跨源请求,不包含`Referer`头部.对于同源请求,将`Referer`设置为完整URL
    - `strict-origin`:对于从安全HTTPS上下文发送到HTTP URL的请求,不包含`Referer`头部.对于所有其他请求,将`Referer`设置为只包含源
    - `origin-when-cross-origin`:对于跨源请求,将`Referer`设置为只包含源.对于同源请求,将`Referer`设置为完整URL
    - `strict-origin-when-cross-origin`:对于从安全HTTPS上下文发送到HTTP URL的请求,不包含`Referer`头部.对于所有其他跨源请求,将`Referer`设置为只包含源.对于同源请求,将`Referer`设置为完整URL
    - `unsafe-url`:对于所有请求,将`Referer`设置为完整URL
  - 默认为`no-referrer-when-downgrade`
- `signal`:
  - 用于支持通过`AbortController`中断进行中的`fetch()`请求
  - 必须是`AbortSignal`的实例
  - 默认为未关联控制器的`AbortSignal`实例

### 常见Fetch请求模式
`fetch()`既可以发送数据,也可以接收数据.使用`init`对象(`RequestInit`类型)参数,可以配置`fetch()`在请求体中发送的各种序列化数据.

#### 发送JSON数据
使用例:
````JS
let payload = JSON.stringify({
    foo: 'bar'
});
let jsonHeaders = new Headers({
    'Content-Type': 'application/json'
});
fetch('/send-me-json', {
    method: 'POST',
    body: payload,
    headers: jsonHeaders
})
````

#### 在请求体中发送参数
因为请求体支持任意字符串,所以可以通过它发送请求参数:
````JS
let payload = "foo=bar&baz=qux";
let paramHeaders = new Headers({
    'Content-Type': 'application/x-www-form-urlencoded; charset=UTF-8'
});
fetch('/send-me-params', {
    method: 'POST',
    body: payload,
    headers: paramHeaders
});
````

#### 发送文件
因为请求体支持`FormData`实现,所以`fetch()`也可以序列化并发送文件字段中的文件:
````JS
let imageFormData = new FormData();
let imageInput = document.querySelector("input[type='file']");
imageFormData.append('image', imageInput.files[0]);
fetch('/img-upload', {
    method: 'POST',
    body: imageFormData
});
````

`fetch()`可以支持多个文件:
````JS
let imageFormData = new FormData();
let imageInput = document.querySelector("input[type='file'][multiple]")
for (let i = 0; i < imageInput.files.length; ++i) {
    imageFormData.append('image', imageInput.files[i]);
}
fetch('/img-upload', {
    method: 'POST',
    body: imageFormData
});
````

#### 加载Blob文件
`Fetch API`也能提供`Blob`类型的响应.一种常见的做法是明确将图片文件加载到内存,然后将其添加到HTML图片元素.为此,可以使用响应对象上暴露的`blob()`方法.这个方法返回一个期约,解决为一个`Blob`的实例.然后,可以将这个实例传给`URL.createObjectURL()`以生成可以添加给图片元素src属性的值:
````JS
const imageElement = document.querySelector('img');
fetch('my-image.png')
  .then((response) => response.blob())
  .then((blob) => {
    imageElement.src = URL.createObjectURL(blob);
  });
````

#### 发送跨源请求
从不同源请求资源,响应要包含CORS头部才能保证浏览器收到响应.没有这些头部,跨源请求会失败并抛出错误.
````JS
fetch('//example.org');
// Access to fetch at 'http://example.org/' from origin 'http://127.0.0.1:5500' has been blocked by CORS policy: No 'Access-Control-Allow-Origin' header is present on the requested resource. If an opaque response serves your needs, set the request's mode to 'no-cors' to fetch the resource with CORS disabled.
````

如果代码不需要访问响应,也可以发送`no-cors`请求.此时响应的`type`属性值为`opaque`,因此无法读取响应内容.这种方式适合发送探测请求或者将响应缓存起来供以后使用.
````JS
fetch('//cross-origin.com', { method: 'no-cors' })
  .then((response) => console.log(response.type));
// opaque
````

#### 中断请求
`Fetch API`支持通过`AbortController/AbortSignal`对中断请求.调用`AbortController.abort()`会中断所有网络传输,特别适合希望停止传输大型负载的情况.中断进行中的`fetch()`请求会包含错误的拒绝:
````JS
let abortController = new AbortController();
fetch('wikipedia.zip', { signal: abortController.signal /* neccessary */ })
  .catch(() => console.log('aborted!'));
setTimeout(() => abortController.abort(), 10);
// abort
````

### Headers对象
`Headers`对象是所有外发请求和入站响应头部的容器.每个外发的`Request`实例都包含一个空的`Headers`实例,可以通过`Request.prototype.headers`访问,每个入站的`Response`实例也可以通过`Response.prototype.headers`访问包含响应头部的`Headers`对象.这两个属性都是可修改属性.另外`new Headers()`也可以创建一个新实例.

#### Headers与Map的相似之处
`Headers`对象与`Map`对象极为相似.HTTP头部本质上是序列化后的键值对,它们的JS表示则是中间接口.`Headers`与`Map`类型都有`get()`(由键获取值),`set()`(设置/更新键值),`has()`(检查指定键是否存在),`delete()`(删除键值对)等实例方法.

`Headers`和`Map`也都可以使用一个可迭代对象来初始化:
````JS
let seed = [['foo', 'bar']];
let h = new Headers(seed);
console.log(h.get('foo'));  // bar
````

两者都有相同的`keys()`,`values()`和`entries()`迭代器接口:
````JS
let seed = [['foo', 'bar'], ['baz', 'qux']];
let h = new Headers(seed);
console.log(...h.keys());       // foo, baz
console.log(...h.values());     // bar, qux
console.log(...h.entries());    // ['foo', 'bar'], ['baz', 'qux']
````

#### Headers独有的特性
在初始化`Headers`对象时,也可以使用键值对形式的对象:
````JS
let seed = {foo: "bar"};
let h = new Headers(seed);
console.log(h.get('foo'));  // bar
````

一个HTTP头部字段可以有多个值,而`Headers`对象通过`append()`方法支持添加多个值.在`Headers`实例中还不存在的键上调用`append()`方法相当于调用`set()`.后续调用会以逗号为分隔符拼接多个值:
````JS
let h = new Headers();
h.append('foo', 'bar');
console.log(h.get('foo'));  // "bar"
h.append('foo', 'baz');
console.log(h.get('foo'));  // "bar, baz"
````

#### 头部护卫
某些情况下,并非所有HTTP头部都可以被客户端修改,而`Headers`对象使用护卫来防止不被允许的修改.不同的护卫设置会改变`set()`,`append()`和`delete()`的行为.违反护卫限制会抛出`TypeError`.

`Headers`实例会因来源不同而展现不同的行为,它们的行为由护卫来控制.JS可以决定`Headers`实例的护卫设置.下表列出了不同的护卫设置和每种设置对应的行为.

详见下文或[MDN-Headers-modification_restrictions](https://developer.mozilla.org/en-US/docs/Web/API/Headers#modification_restrictions)

- 护卫
  - 适用情形
  - 限制
- `none`:
  - 适用情形:在通过构造函数创建`Headers`实例时激活
  - 限制:无
- `request`:
  - 适用情形:在通过构造函数初始化`Request`对象(因此此处指的是`Request`对象的标头,下同),且`mode`值为非`no-cors`时激活
  - 限制:不允许修改[禁止修改的头部](https://developer.mozilla.org/zh-CN/docs/Glossary/Forbidden_header_name)
- `request`:
  - 适用情形:在通过构造函数初始化`Request`对象,且`mode`值为`no-cors`时激活
  - 限制:不允许修改非简单头部(简单标头又称[列入CORS白名单的请求标头](https://developer.mozilla.org/zh-CN/docs/Glossary/CORS-safelisted_request_header))
- `response`:
  - 适用情形:在通过构造函数初始化`Response`对象时激活
  - 限制:不允许修改[禁止修改的响应头部](https://developer.mozilla.org/zh-CN/docs/Glossary/Forbidden_response_header_name)
- `immutable`:
  - 适用情形:在通过`error()`或`redirect()`静态方法初始化`Response`对象时激活
  - 限制:不允许修改任何头部

### Request对象
`Request`对象是获取资源请求的接口.这个接口暴露了请求相关信息,也暴露了使用请求体的不同方式.

有关请求体,[详见下文](#requestresponse及body混入)

#### 创建Request对象
可以通过构造函数初始化`Request`对象.为此需要传入一个`input`参数,一般是URL:
````JS
let r = new Request('https://foo.com');
console.log(r);
// Request {
//     bodyUsed: false,
//     cache: "default",
//     credentials: "same-origin",
//     destination: "",
//     headers: Headers {},
//     integrity: "",
//     keepalive: false,
//     method: "GET",
//     mode: "cors",
//     redirect: "follow",
//     referrer: "about:client",
//     referrerPolicy: "",
//     signal: AbortSignal { abort: false, onabort: null },
//     url: "<current URL>"
// }
````

`Request`构造函数也接收第二个参数,即一个`init`对象(`RequestInit`类型).这个对象与前面`fetch()`的`init`对象一样.没有在`init`对象中涉及的值则会使用默认值.

示例:
````JS
let r = new Request('https://foo.com', { method: 'POST' });
````

#### 克隆Request对象
将`Request`实例作为`input`参数传给`Request`构造函数,会得到该请求的一个副本.如果再传入`init`对象,则`init`对象的值会覆盖源对象中同名的值:
````JS
let r1 = new Request('https://foo.com');
let r2 = new Request(r1);
let r3 = new Request(r2, { method: 'POST' });
````

这种克隆方式并不总能得到一模一样的副本.在克隆完之后,被克隆的请求体会被标记为"已使用".如果源对象与创建的新对象不同源,则`referrer`属性会被清除.此外,如果源对象的`mode`为`navigate`,则会被转换为`same-origin`.
````JS
let r1 = new Request('https://foo.com', { method: 'POST', body: 'foobar' });
let r2 = new Request(r1);
console.log(r1.bodyUsed);   // true
console.log(r2.bodyUsed);   // false
````

第二种克隆`Request`对象的方式是使用`clone()`方法,这个方法会创建一模一样的副本,任何值都不会被覆盖.与第一种方式不同,这种方法不会将任何请求的请求体标记为"已使用":
````JS
let r1 = new Request('https://foo.com', { method: 'POST', body: 'foobar' });
let r2 = r1.clone();
console.log(r2.url);    // https://foo.com/
console.log(r1.bodyUsed);   // false
````

如果请求对象的`bodyUsed`属性为`true`(即请求体已被读取),那么上述任何一种方式都不能用来创建这个对象的副本.在请求体被读取之后再克隆会导致抛出`TypeError`.

**注意:`bodyUsed`属性被修改为`true`的前提条件是`Request`存在请求体,也就是说,只有当`init`中传入`body`属性,后续才可以将请求体标记为已使用.例如:**
````JS
let r1 = new Request('tmp');
let r2 = new Request(r1);
let r3 = new Request(r1);   // OK

let r4 = new Request('tmp', { body: "" });
let r5 = new Request(r4);
let r6 = new Request(r4);   // Uncaught TypeError: Failed to construct 'Request': Request with GET/HEAD method cannot have body.
````

#### 在fetch()中使用Request对象
在调用`fetch()`时,可以传入已经创建好的`Request`实例而不是URL.与`Request`构造函数一样,传给`fetch()`的`init`对象会覆盖传入请求对象的值:
````JS
let r = new Request('https://foo.com');
fetch(r);   // 向foo.com发送GET请求
fetch(r, { method: 'POST' });   // 向foo.com发送POST请求
````

与克隆`Request`一样,`fetch()`也不能拿请求体已经用过的`Request`对象来发送请求.

包含请求体的`Request`只能在一次`fetch()`中使用,传入后会被标记为"已使用"(类似于第一种克隆方法,[见上文](#克隆request对象)).

想要基于包含请求体的相同`Request`对象多次调用`fetch()`,必须在第一次发送`fetch()`请求前调用`clone()`.

### Response对象
`Response`对象是获取资源响应的接口.这个接口暴露了响应的相关信息,也暴露了使用响应体的不同方式.

#### 创建Response对象
可以通过构造函数初始化`Response`对象且不需要参数.此时响应实例的属性均为默认值,因为它并不代表实际的HTTP响应:
````JS
let r = new Response();
console.log(r);
// Response {
//     body: { ... },
//     bodyUsed: false,
//     headers: Headers {},
//     ok: true,
//     redirected: false,
//     status: 200,
//     statusText: "OK",
//     type: "default",
//     url: ""
// }
````

`Response`构造函数接收一个可选的`body`参数.这个`body`可以是`null`,等同于`fetch()`参数`init`中的`body`.还可以接收一个可选的`init`对象(`Object`),这个对象包含如下的键和值:
- `headers`:必须是`Headers`对象实例或包含字符串键值对的常规对象实例.默认为没有键值对的`Headers`对象.
- `status`:表示HTTP响应状态码的整数.默认为`200`.
- `statusText`:表示HTTP响应状态的字符串.默认为空字符串.

示例:
````JS
let r = new Response('foobar', {
    status: 418,
    statusText: 'I\'m a teapot'
});
console.log(r);
// Response {
//     body: { ... },
//     bodyUsed: false,
//     headers: Headers {},
//     ok: false,
//     redirected: false,
//     status: 418,
//     statusText: "I'm a teapot",
//     type: "default",
//     url: ""
// }
````

大多数情况下,产生`Response`对象的主要方式是调用`fetch()`,它返回一个最后会解决为`Response`对象的期约,这个`Response`对象代表实际的HTTP响应:
````JS
fetch('https://foo.com')
  .then((response) => {
    console.log(response);
  });
// Response {
//     body: { ... },
//     bodyUsed: false,
//     headers: Headers {},
//     ok: true,
//     redirected: false,
//     status: 200,
//     statusText: "OK",
//     type: "basic",
//     url: "https://foo.com/"
// }
````

`Response`类还有两个用于生成`Response`对象的静态方法:`Response.redirect()`和`Response.error()`.

`Response.redirect()`接收一个URL和一个重定向状态码(301,302,303,307或308),返回重定向的`Response`对象.提供的状态码必须对应重定向,否则会抛出错误.
````JS
console.log(Response.redirect('https://foo.com/', 301));
// Response {
//     body: { ... },
//     bodyUsed: false,
//     headers: Headers {},
//     ok: false,
//     redirected: false,
//     status: 301,
//     statusText: "",
//     type: "default",
//     url: ""
// }
````

`Response.error()`用于产生表示网络错误的`Response`对象(网络错误会导致`fetch()`期约被拒绝).
````JS
console.log(Response.error());
// Response {
//     body: { ... },
//     bodyUsed: false,
//     headers: Headers {},
//     ok: false,
//     redirected: false,
//     status: 0,
//     statusText: "",
//     type: "error",
//     url: ""
// }
````

#### 读取响应状态信息
`Response`对象包含一组只读属性,描述了请求完成后的状态,如下所示:
- `headers`:响应包含的`Headers`对象
- `ok`:布尔值,表示HTTP状态码的含义.`200-299`的状态码返回`true`,其他状态码返回`false`
- `redirected`:布尔值,表示响应是否至少经过一次重定向
- `status`:整数,表示响应的HTTP状态码
- `statusText`:字符串,包含对HTTP状态码的正式描述.这个值派生自可选的`HTTP Reason-Phrase`字段,因此如果服务器已`Reason-Phrase`为由拒绝响应,这个字段可能是空字符串
- `type`:字符串,包含响应类型.可能是下列字符串值之一:
  - `basic`:表示标准的同源响应
  - `cors`:表示标准的跨源响应
  - `error`:表示响应对象是通过`Response.error()`创建的
  - `opaque`:表示`no-cors`的`fetch()`返回的跨源响应
  - `opaqueredirect`:表示对`redirect`设置为`manual`的请求的响应
- `url`:包含响应URL的字符串.对于重定向响应,这是最终的URL,非重定向响应就是它产生的

#### 克隆Response对象

**注意:`bodyUsed`属性被修改为`true`的前提条件是`Response`存在请求体,也就是说,只有当第一个参数传入合法的非`null`或`undefined`参数时,后续才可以将请求体标记为已使用.例如:**
````JS
let r1 = new Response();
r1.text();  // 使用Response
r1.clone(); // OK

let r2 = new Response('foobar');
r2.text();  // 使用Response
r2.clone(); // Uncaught TypeError: Failed to execute 'clone' on 'Response': Response body is already used
````

克隆`Response`对象的主要方式是使用`clone()`方法,这个方法会创建一个一模一样的副本,不会覆盖任何值.这样不会将任何请求的请求体标记为已使用:
````JS
let r1 = new Response('foobar');
let r2 = r1.clone();
console.log(r1.bodyUsed);   // false
console.log(r2.bodyUsed);   // false
````

如果响应对象的`bodyUsed`属性为`true`(即响应体已被读取),则不能再创建这个对象的副本.在响应体被读取之后再克隆会导致抛出`TypeError`.

有响应体的`Response`对象只能读取一次.(不包含响应体的`Response`对象不受此限制.)比如:
````JS
let r = new Response('foobar');
r.text().then(console.log); // foobar
r.text().then(console.log); // Uncaught (in promise) TypeError: Failed to execute 'text' on 'Response': body stream already read
````

要多次读取包含相应体的同一个`Response`对象,必须再第一次读取前调用`clone()`.

此外,通过创建带有原始响应体的`Response`实例,可以执行伪克隆操作.这样不会把第一个`Response`实例标记为已读,而是会在两个响应之间*共享*:
````JS
let r1 = new Response('foobar');
let r2 = new Response(r1.body);

console.log(r1.bodyUsed);   // false
console.log(r2.bodyUsed);   // false

r2.text().then(console.log);    // foobar
r1.text().then(console.log);    // Uncaught (in promise) TypeError: Failed to execute 'text' on 'Response': body stream already read
````

### Request,Response及Body混入
`Request`和`Response`都使用了`Fetch API`的`Body`混入,以实现两者承担有效载荷的能力.这个混入为两个类型提供了只读的`body`属性(实现为`ReadableStream`),只读的`bodyUsed`布尔值(表示`body`流是否已读)和一组方法,用于从流中读取内容并将结果转换为某种JS对象类型.

通过,将`Request`和`Response`主体(body)作为流来使用主要有两个原因.一个原因是有效载荷的大小可能会导致网络延迟,另一个原因是流API本身在处理有效载荷方面是有优势的.除此之外,最好是一次性获取资源主体.

`Body`混入提供了5个方法,用于将`ReadableStream`转存到缓冲区的内存里,将缓冲区转换为某种JS对象类型,以及通过期约来产生结果.在解决之前,期约会等待主体流报告完成及缓冲被解析.这意味着客户端必须等待响应的资源完全加载才能访问其内容.

#### Body.text()
`Body.text()`方法返回期约,解决为将缓冲区转存得到的`UTF-8`格式字符串:
````JS
fetch('https://foo.com')
  .then((response) => response.text())
  .then(console.log);
// <!doctype html><html lang="en">
//  <head>
//   <meta charset="utf-8">
//   ...

let request = new Request('https://foo.com', { method: 'POST', body: 'barbazqux' });
request.text()
  .then(console.log);   
// barbazqux
````

#### Body.json()
`Body.json()`方法返回期约,解决为将缓冲区转存得到的JSON:
````JS
fetch('https://foo.com/foo.json')
  .then((response) => response.json())
  .then(console.log);
// {"foo": "bar"}

let request = new Request('https://foo.com',
                          { method: 'POST', body: JSON.stringify({ bar: 'baz' }) });
request.json()
  .then(console.log);
// {bar: 'baz'}
````

#### Body.formData()
浏览器可以将`FormData`对象序列化/反序列化为主体:
````JS
let myFormData = new FormData();
myFormData.append('foo', 'bar');
````
在通过HTTP传送时,WebKit浏览器会将其序列化为下列内容:
```
------WebKitFormBoundarydR9Q2kOzE6nbN7eR
Content-Disposition: form-data; name="foo"
bar
------WebKitFormBoundarydR9Q2kOzE6nbN7eR--
```

`Body.formData()`方法返回期约,解决为将缓冲区转存得到的`FormData`实例:
````JS
fetch('https://foo.com/form-data')
  .then((response) => response.formData())
  .then((formData) => console.log(formData.get('foo')));
// bar

let myFormData = new FormData();
myFormData.append('foo', 'bar');
let request = new Request('https://foo.com',
                          { method: 'POST', body: myFormData });
request.formData()
  .then((formData) => console.log(formData.get('foo')));
// bar
````

#### Body.arrayBuffer()
有时候,可能需要以原始二进制格式查看和修改主体.为此,可以使用`Body.arrayBuffer()`将主体内容转换为`ArrayBuffer`实例.`Body.arrayBuffer()`方法返回期约,解决为将缓冲区转存得到的`ArrayBuffer`实例:
````JS
fetch('https://foo.com')
  .then((response) => response.arrayBuffer())
  .then(console.log);
// ArrayBuffer(...) {}

let request = new Request('https://foo.com',
                          { method: 'POST', body: 'adcdefg' });
request.arrayBuffer()
  .then((buf) => console.log(new Int8Array(buf)));
// Int8Array(7) [97, 98, 99, 100, 101, 102, 103]
````

#### Body.blob()
有时候,可能需要以原始二进制格式使用主体,不用查看和修改.为此,可以使用`Body.blob()`将主体内容转换为`Blob`实例.`Body.blob()`方法返回期约,解决为将缓冲区转存得到的`Blob`实例:
````JS
fetch('https://foo.com')
  .then((response) => response.blob())
  .then(console.log);
// Blob(...) { size: ..., type: "..." }

let request = new Request('https://foo.com',
                          { method: 'POST', body: 'abcdefg' });
request.blob()
  .then(console.log);
// Blob(7) { size: 7, type: "text/plain;charset=utf-8" }
````

#### 一次性流
因为`Body`混入是构建在`ReadableStream`之上的,所以主体流只能使用一次.这意味着所有主体混入方法都只能调用一次,再次调用就会抛出错误:
````JS
fetch('https://foo.com')
  .then((response) => response.blob().then(() => response.blob()));
// Uncaught (in promise) TypeError: Failed to execute 'blob' on 'Response': body stream already read
````

即使是在读取流的过程中,所有这些方法也会在它们被调用时给`ReadableStream`加锁,以阻止其他读取器访问:
````JS
fetch('https://foo.com')
  .then((response) => {
    response.blob();
    response.blob();
  });
// Uncaught (in promise) TypeError: Failed to execute 'blob' on 'Response': body stream already read
````

作为`Body`混入的一部分,`bodyUsed`布尔值属性表示`ReadableStream`是否已*摄受(disturbed)*,即读取器是否已经在流上加了锁.这不一定表示流已经完全读取.

#### 使用ReadableStream主体
JS编程逻辑很多时候会将访问网络作为原子操作,比如请求是同时创建和发送的,响应数据也是以统一的格式一次性暴露出来的.这种约定隐藏了底层的混乱,让涉及网络的代码变得很清晰.

从TCP/IP角度来看,传输的数据是以分块形式抵达端点的,而且速度受到网速的限制.接收端点会为此分配节点,并将收到的块写入内存.`Fetch API`通过`ReadableStream`支持在这些块到达时就实时读取的操作这些数据.

有关`Stream API`,[详见上](#stream-api).

`ReadableStream`暴露了`getReader()`方法,用于产生`ReadableStreamDefaultReader`,这个读取器可以用于在数据到达时异步获取数据块.数据流的格式是`Uint8Array`.

下面的代码调用了读取器的`read()`方法,把最早可用的块打印了出来:
````JS
fetch('https://fetch.spec.whatwg.org/')
  .then((response) => response.body)
  .then((body) => {
    let reader = body.getReader();
    console.log(reader);    // ReadableStreamDefaultReader {}
    reader.read()
      .then(console.log);
  });
// { value: Uint8Array {}, done: false }
````

可以这样写来不断查看有效载荷:
````JS
fetch('https://fetch.spec.whatwg.org/')
  .then((response) => response.body)
  .then(async function(body) {
    let reader = body.getReader();
    while (true) {
        let { value, done } = await reader.read();  // 注意,每次返回一个分块的内容,如果想获得所有内容,记得将分块合并
        if (done) {
            break;
        }
        console.log(value);
    }
  });
// Uint8Array(65536) [60, 33, 100, ...]
// Uint8Array(85607) [101, 110, 116, ...]
// Uint8Array(49785) [47, 97, 62, ...]
// Uint8Array(232327) [116, 104, 101, ...]
// Uint8Array(65536) [100, 111, 101, ...]
// ...
// Uint8Array(94105) [117, 114, 108, ...]
````
或封装到`Iterable`接口中,并使用`for-await-of`循环:
````JS
fetch('https://fetch.spec.whatwg.org/')
  .then((response) => response.body)
  .then(async fucntion(body) {
    let reader = body.getReader();
    let asyncIterable = {
        [Symbol.asyncIterator]() {
            return {
                next() {
                    return reader.read();
                }
            };
        }
    };
    for await (chunk of asyncIterable) {
        console.log(chunk);
    }
  });
````
或者,更进一步,将异步包装到一个生成器函数中,还可以进一步简化代码.此外,如果流因为耗尽或错误而终止,还可以让读取器释放锁,以允许不同的流读取器继续操作:
````JS
async function* streamGenerator(stream) {
    const reader = stream.getReader();
    try {
        while (true) {
            const { value, done } = await reader.read();
            if (done) {
                break;
            }
            yield value;
        }
    } finally {
        reader.releaseLock();
    }
}

fetch('https://fetch.spec.whatwg.org/')
  .then((response) => response.body)
  .then(async function(body) {
    for await (chunk of streamGenerator(body)) {
        console.log(chunk);
    }
  });
````

缓冲区的大小,以及浏览器是否等待缓冲区被填充后才将其推到流中,要根据JS运行时的实现.浏览器会控制等待分配的缓冲区被填充,同时会尽快将缓冲区数据发送到流.

不同浏览器中分块大小可能不同,这取决于带宽和网络延迟.此外,浏览器如果决定不等待网络,也可以将部分填充的缓冲区发送到流.最终,代码要准备好处理以下情况:
- 不同大小的`Uint8Array`块
- 部分填充的`Uint8Array`块
- 块到达的时间间隔不确定

默认情况下,块是以`Uint8Array`格式抵达的.因为块的分割不会考虑编码,所以会出现某些值作为多字节字符被分散到两个块中的情况.手动处理这些情况非常麻烦,但很多时候可以使用`Encoding API`的可插拔方案.

要将`Uint8Array`转换为可读文本,可以将缓冲区传给`TextDecoder`,返回转换后的值.通过设置`stream: true`,可以将之前的缓冲区保留在内存,从而让跨越两个块的内容能够被正确解码:
````JS
let decoder = new TextDecoder();
async function* streamGenerator(stream) {
    const reader = stream.getReader();
    try {
        while (true) {
            const { value, done } = await reader.read();
            if (done) {
                break;
            }
            yield value;
        }
    } finally {
        reader.releaseLock();
    }
}
fetch('https://fetch.spec.whatwg.org/')
  .then((response) => response.body)
  .then(async function(body) {
    for await (chunk of streamGenerator(body)) {
        console.log(decoder.decode(chunk, { stream: true }));
    }
  });
// <!doctype html><html lang="en">
//  <head>
//   <meta charset="utf-8">
//   <meta content="width=device-width, initial-scale=1, shrink-to-fit=no" name="viewport">
//   <meta content="#3c790a" name="theme-color">
//   <meta content="light dark" name="color-scheme">
//   <title>Fetch Standard</title>
//   <link crossorigin href="https://resources.whatwg.org/standard-shared-with-dev.css" rel="stylesheet">
// ...
````

因为可以使用`ReadableStream`(body)创建`Response`对象,所以就可以在读取流之后,将其通过管道导入另一个流.然后在这个新流上再使用`Body`的方法,如`text()`.这样就可以随着流的到达实时检查和操作流内容.例如:
````JS
fetch('https://fetch.spec.whatwg.org/')
  .then((response) => response.body)
  .then((body) => {
    const reader = body.getReader();
    // 创建第二个流
    return new ReadableStream({
        async start(controller) {
            try {
                while (true) {
                    const { value, done } = await reader.read();
                    if (done) {
                        break;
                    }
                    controller.enqueue(value);
                }
            } finally {
                controller.close();
                reader.releaseLock();
            }
        }
    })
  })
  .then((secondaryStream) => new Response(secondaryStream))
  .then(response => response.text())
  .then(console.log);
// <!doctype html><html lang="en">
//  <head>
//   <meta charset="utf-8">
//   <meta content="width=device-width, initial-scale=1, shrink-to-fit=no" name="viewport">
//   <meta content="#3c790a" name="theme-color">
//   <meta content="light dark" name="color-scheme">
//   <title>Fetch Standard</title>
//   <link crossorigin href="https://resources.whatwg.org/standard-shared-with-dev.css" rel="stylesheet">
// ...
````

## Beacon API
为了把尽量多的页面信息传到服务器,很多分析工具需要在页面生命周期中尽量晚的时候向服务器发送遥测或分析数据.因此,理想的情况下是通过浏览器的`unload`事件发送网络请求.这个事件表示要离开当前页面,不会再生成别的有用信息了.但`unload`事件对浏览器意味着没有理由再发送任何结果未知的网络请求(因为页面都要被销毁了).因此,此时任何异步请求都会被浏览器取消.

为此,W3C引入了`Beacon API`.这个API给`navigator`对象增加了一个`sendBeacon()`方法.这个方法接收一个`URL`和一个数据有效载荷参数,并会发送一个`POST`请求.可选的数据有效载荷参数有:`ArrayBufferView`,`Blob`,`DOMString`,`FormData`实例.如果请求成功进入了最终要发送的任务队列,则这个方法返回`true`,否则返回`false`.

````JS
navigator.sendBeacon('https://example.com/analytics-reporting-url', '{foo: "bar"}');
````

这个方法虽然看起来不过是`POST`请求的一个语法糖,但它有几个重要的特性:
- `sendBeacon()`并不是只能在页面生命周期末尾使用,而是任何时间都可以使用.
- 调用`sendBeacon()`后,浏览器会把请求添加到一个内部的请求队列.浏览器会主动地发送队列中的请求.
- 浏览器保证在原始页面已经关闭的情况下也会发送请求.
- 状态码,超时和其他网络原因造成的失败完全是不透明的,不能通过编程方式处理.
- 信标(`beacon`)请求会携带调用`sendBeacon()`时所有相关的`cookie`.

## Web Socket
`Web Socket`的目标是通过一个长时连接实现与服务器全双工,双向的通信.在JS中创建`Web Socket`时,一个HTTP请求会发送到服务器以初始化连接.服务器响应后,连接使用`HTTP`的`Upgrade`头部从HTTP协议切换到`Web Socket`协议.这意味着`Web Socket`不能通过标准HTTP服务器实现,而必须使用支持该协议的专有服务器.

因为`Web Socket`使用了自定义协议,所以URL方案稍有变化:不能再使用`http://`或`https://`,而要使用`ws://`或`wss://`.前者是不安全的连接,后者是安全连接.在指定`Web Socket URL`时,必须包含`URL`方案,因为将来有可能再支持其他方案.

使用自定义协议而非HTTP协议的好处是,客户端和服务器之间可以发送非常少的数据,不会对`HTTP`造成任何负担.使用更小的数据包让`Web Socket`非常适合带宽和延迟问题比较明显的移动应用.使用自定义协议的缺点是,定义协议的时间比定义`JS API`要长.`Web Socket`得到了所有主流浏览器支持.

### API
要创建一个新的`Web Socket`,就要实例化一个`WebSocket`对象并传入提供连接的URL:
````JS
let socket = new WebSocket("ws://www.example.org/server.php");
````

注意,必须给`WebSocket`构造函数传入一个绝对URL.同源策略不适用于`Web Socket`,因此可以打开到任意站点的连接.至于是否与来自特定源的页面通信,则完全取决于服务器.(在握手阶段就可以确定请求来自哪里.)

浏览器会在初始化`WebSocket`对象之后立即创建连接.`WebSocket`有一个`readyState`属性表示当前状态.其可能值为:
- `WebSocket.OPENING(0)`:连接正在建立.
- `WebSocket.OPEN(1)`:连接已经建立.
- `WebSocket.CLOSING(2)`:连接正在关闭.
- `WebSocket.CLOSE(3)`:连接已经关闭.

`WebSocket`对象没有`readystatechange`事件,而是有与上述不同状态对应的其他事件.`readyState`值从0开始.

任何时候都可以调用`close()`方法关闭`Web Socket`连接:
````JS
socket.close();
````
调用`close()`之后,`readyState`立即变为`2`(连接正在关闭),并会在关闭后变为`3`(连接已经关闭).

### 发送和接收数据
打开`Web Socket`之后,可以通过连接发送和接收数据.要向服务器发送数据,使用`send()`方法并传入一个字符串,`ArrayBuffer`或`Blob`:
````JS
let socket = new WebSocket("ws://www.example.org/server.php");
let stringData = "Hello world!";
let arrayBufferData = Uint8Array.from(['f', 'o', 'o']);
let blobData = new Blob(['f', 'o', 'o']);

socket.send(stringData);
socket.send(arrayBufferData);
socket.send(blobData);
````

服务器向客户端发送信息时,`WebSocket`对象上会触发`message`事件.可以通过`event.data`属性访问到有效载荷:
````JS
socket.addEventListener("message", (event) => {
    let data = event.data;
    // ...
});
````

`event.data`返回的数据可能是`ArrayBuffer`或`Blob`.这由`WebSocket`对象的`binaryType`属性决定,该属性可能是`"blob"`或`"arraybuffer"`.

### 其他事件
`WebSocket`对象在连接生命周期中有可能触发3个其他事件:
- `open`:在连接成功建立时触发.
- `error`:在发生错误时触发.连接无法存续.
- `close`:在连接关闭时触发.

`WebSocket`在比较旧的浏览器中可能不支持`DOM Level 2`事件监听器,需要使用`DOM Level 0`风格的事件处理程序来监听事件.但现代浏览器都支持`WebSocket`使用`addEventListener()`(继承自`EventTarget`类).

在这些事件中,只有`close`事件的`event`对象上有额外信息.这个对象上有3个额外属性:
- `wasClean`:布尔值,表示连接是否干净地关闭
- `code`:一个来自服务器的数值状态码
- `reason`:一个字符串,包含服务器发来的消息

## 安全
大规模Ajax应用程序需要考虑的安全问题非常多,但在通用层面上一般需要考虑以下几个问题.

首先,任何Ajax可以访问的URL,也可以通过浏览器或服务器访问,例如:`/getuserinfo.php?id=23`.请求这个URL,可以假定返回ID为23的用户信息.`getuserinfo.php`文件必须知道访问者是否拥有访问相应数据的权限.否则,服务器就会大门敞开,泄露所有用户的信息.

在未授权系统可以访问某个资源时,可以将其视为跨站点请求伪造(CSRF, cross-site request forgery)攻击.未授权系统会按照处理请求的服务器的要求伪装自己.Ajax应用程序,无论大小,都会受到CSRF攻击的影响,包含无害的漏洞验证攻击和恶意的数据盗窃或数据破坏攻击.

关于安全防护Ajax相关URL的一般理论认为,需要验证请求发送者拥有对资源的访问权限.可以通过如下方式实现:
- 要求通过SSL访问能够被Ajax访问的资源.
- 要求每个请求都发送一个按约定算法计算好的令牌(token).

注意,以下手段对防护CSRF攻击是无效的:
- 要求`POST`而非`GET`请求(很容易修改请求方法).
- 使用来源`URL`验证来源(来源`URL`很容易伪造).
- 基于`cookie`验证(同样很容易伪造).

# 客户端存储
## cookie
`HTTP cookie`通常也叫作`cookie`,最初用于在客户端存储会话信息.这个规范要求服务器在响应`HTTP`请求时,通过发送`Set-Cookie` HTTP头部包含会话信息.

例如,下面是包含这个头部的一个HTTP响应:
```
HTTP/1.1 200 OK
Content-type: text/html
Set-Cookie: name=value
Other-header: other-header-value
```

这个HTTP响应会设置一个名为`"name"`,值为`"value"`的`cookie`.名和值在发送时都会经过URL编码.浏览器会存储这些会话信息,并在之后的每个请求中都会通过HTTP头部`cookie`再将它们发回服务器,比如:
```
GET /index.js1 HTTP/1.1
Cookie: name=value
Other-header: other-header-value
```

这些发送回服务器的额外信息可用于唯一标识发送请求的客户端.

### 限制
`cookie`是与特定域绑定的.设置`cookie`后,它会与请求一起发送到创建它的域.这个限制能保证`cookie`中存储的信息只对被认可的接收者开放,不被其他域访问.

因为`cookie`存储在客户端机器上,所以为保证它不会被恶意利用,浏览器会施加限制.同时,`cookie`也不会占用太多磁盘空间.

通常,只要遵守以下大致的限制,就不会在任何浏览器中碰到问题:
- 不超过300个cookie
- 每个cookie不超过4096字节
- 每个域不超过20个cookie
- 每个域不超过81920字节

每个域能设置的`cookie`总数是受限的,但不同浏览器的限制不同.如果`cookie`总数超过了单个域的上限,浏览器就会删除之前设置的cookie.

浏览器也会限制`cookie`的大小,大多数浏览器对`cookie`的限制是不超过4096字节,上下可以有一个字节的误差.为跨浏览器兼容,最好保证`cookie`的大小不超过4095字节.如果创建的`cookie`超过最大限制,则该`cookie`会被静默删除.

### cookie的构成
`cookie`在浏览器中是由以下参数构成的:
- **名称**:唯一标识`cookie`的名称.`cookie`名不区分大小写,因此`myCookie`和`MyCookie`是同一个名称.不过,实践中最好将`cookie`名当成区分大小写来对待,因为一些服务器软件可能这样对待它们.`cookie`名必须经过URL编码.
- **值**:存储在`cookie`里的字符串值.这个值必须经过URL编码.
- **域**:`cookie`有效的域.发送到这个域的所有请求都会包含对应的`cookie`.这个值可能包含子域(如`www.example.org`),也可以不包含(如`.example.org`表示对`example.org`的所有子域都有效).
- **路径**:请求URL中包含这个路径才会把`cookie`发送到服务器.例如,可以指定`cookie`只能由`http://www.example.org/path/`访问,因此访问`http://www.example.com/`下的页面就不会发送cookie,即使请求的是同一个域.
- **过期时间**:表示何时删除cookie的时间戳(即什么时间之后就不发送到服务器了).默认情况下,浏览器会话结束后会删除所有`cookie`.不过,也可以设置删除`cookie`的具体时间.这样即使关闭浏览器,`cookie`也会保留在用户机器上.把过期时间设置为过去的时间会立即删除`cookie`.
- **安全标志**:设置之后,只在使用SSL安全连接的情况下才会把`cookie`发送到服务器.例如,请求`https://www.example.com`会发送`cookie`,而请求`http://www.example.com`则不会.

这些参数在`Set-Cookie`头部中使用分号加空格隔开:
```
HTTP/1.1 200 OK
Content-type: text/html
Set-Cookie: name=value; expires=Wed, 22-Jan-25 07:08:33 GMT; domain=.example.org; path=/path/; secure
Other-header: other-header-value
```
上面设置的`cookie`名为`name`,这个`cookie`在2025年1月22日7:08:33过期,对`www.example.org`及其他`example.org`的子域有效,但路径必须是`/path/`,只能在SSL上发送,因为设置了`secure`标志.

域,路径,过期时间和`secure`标志用于告诉浏览器什么情况下应该在请求中包含`cookie`.这些参数并不会随请求发送给服务器,实际发送的只有`cookie`的名值对.

### JS中的cookie
[相关链接](https://developer.mozilla.org/zh-CN/docs/Web/API/Document/cookie)

在JS中处理`cookie`比较麻烦,由于接口过于简单,只有BOM的`document.cookie`属性.根据用法不同,该属性的表现迥异.

要使用该属性获取值时,`document.cookie`返回包含页面所有有效`cookie`的字符串(根据域,路径,过期时间和安全设置),以分号分隔:`name1=value1;name2=value2;name3=value3`.所有名和值都是URL编码的,因此必须使用`documentURIComponent()`解码.

在设置值时,可以通过`document.cookie`属性设置新的`cookie`字符串.这个字符串在被解析后会添加到原有`cookie`中.设置`document.cookie`不会覆盖之前存在的任何`cookie`,除非设置了已有的`cookie`.设置`cookie`的格式如下,与`Set-Cookie`头部的格式一样:`name=value;expires=expiration_time;path=domain_path;domain=domain_name;secure`.

在所有这些参数中,只有`cookie`的名称和值是必需的.例如:
````JS
document.cookie = encodeURIComponent("name") + "=" +    // 不要把=包含在encodeURIComponent()中,否则会被编码为%3D
                  encodeURIComponent("aaa");    // 这里虽然没有字符需要编码,但最好还是使用encodeURIComponent()
````

要给已经创建的`cookie`指定额外信息,只要针对已有的`name`再次写入就可以了:
````JS
document.cookie = encodeURIComponent("name") + "=" +
                  encodeURIComponent("aaa") + "; domain=.example.org; path=/";
````

为了删除已有的cookie方法,需要再次设置同名`cookie`(包括相同路径,域和安全选项),但要将其过期时间设置为某个过去的时间.

为了方便`cookie`的设置,给出以下类:
````JS
class CookieUtil {
    static get(name) {
        let cookie = decodeURIComponent(document.cookie),
            cookieName = `${name}=`,
            cookieStart = cookie.indexOf(cookieName),
            cookieValue = null;
        if (cookieStart > -1) {
            let cookieEnd = cookie.indexOf(";", cookieStart);
            if (cookieEnd == -1) {
                cookieEnd = cookie.length;
            }
            cookieValue = decodeURIComponent(cookie.substring(cookieStart + cookieName.length, cookieEnd));
        }
        return cookieValue;
    }
    static set(name, value, expires, path, domain, secure) {
        let cookieText = `${encodeURIComponent(name)}=${encodeURIComponent(value)}`
        if (expires instanceof Date) {
            cookieText += `; expires=${expires.toGMTString()}`;
        }
        if (path) {
            cookieText += `; path=${encodeURIComponent(path)}`;
        }
        if (domain) {
            cookieText += `; domain=${encodeURIComponent(domain)}`
        }
        if (secure) {
            cookieText += `; secure`;
        }
        document.cookie = cookieText;
    }
    static unset(name, path, domain, secure) {
        CookieUtil.set(name, "", new Date(0), path, domain, secure);
    }
};
````

### 子cookie
为绕过浏览器对每个域`cookie`数的限制,有些开发者提出了`子cookie`的概念,子cookie是在单个cookie存储的小块数据,本质上是使用cookie的值在单个cookie中存储多个名值对.最常用的子cookie模式如下:`name=name1=value1&name2=value2&name3=value3`.

子cookie的格式类似于查询字符串.这些值可以存储为单个cookie,而不用单独存储为自己的名值对,结果就是网站或`Web`应用程序能够在单域cookie数限制下存储更多的结构化数.

要操作`子cookie`,就需要再添加一些辅助方法.给出以下辅助类:
````JS
class SubCookieUtil {
    static get(name, subName) {
        let subCookies = SubCookieUtil.getAll(name);
        return subCookies ? subCookies[subName] : null;
    }

    static getAll(name) {
        let cookie = decodeURIComponent(document.cookie),
            cookieName = name + "=",
            cookieStart = cookie.indexOf(cookieName),
            cookieValue = null,
            cookieEnd,
            subCookies,
            parts,
            result = {};
        if (cookieStart > -1) {
            cookieEnd = cookie.indexOf(";", cookieStart);
            if (cookieEnd == -1) {
                cookieEnd = cookie.length;
            }
            cookieValue = cookie.substring(cookieStart + cookieName.length, cookieEnd);
            if (cookieValue.length > 0) {
                subCookies = cookieValue.split("&");
                for (let i = 0, len = subCookies.length; i < len; ++i) {
                    parts = subCookies[i].split("=");
                    result[parts[0]] = parts[1];
                }
            }
            return result;
        }
        return null;
    }

    static set(name, subName, value, expires, path, domain, secure) {
        let subCookies = SubCookieUtil.getAll(name) || {};
        subCookies[subName] = value;
        SubCookieUtil.setAll(name, subCookies, expires, path, domain, secure);
    }

    static setAll(name, subcookies, expires, path, domain, secure) {
        let cookieText = name + "=",
            subcookiesParts = new Array(),
            subName;
        for (subName in subcookies) {   // null传入则什么都不会发生
            subcookiesParts.push(encodeURIComponent(subName + "=" + subcookies[subName]));
        }
        if (cookieParts.length > 0) {
            cookieText += subcookiesParts.join(encodeURIComponent("&"));
            // 以下设置需要针对cookie本身而非子cookie
            if (expires instanceof Date) {
                cookieText += `; expires=${expires.toGMTString()}`;
            }
            if (path) {
                cookieText += `; path=${encodeURIComponent(path)}`;
            }
            if (domain) {
                cookieText += `; domain=${encodeURIComponent(domain)}`
            }
            if (secure) {
                cookieText += `; secure`;
            }
        } else {
            // 表明该cookie需要删除
            cookieText += `; expires=${(new Date(0)).toGMTString()}`;
        }
        document.cookie = cookieText;
    }

    static unset(name, subName, path, domain, secure) {
        let subcookies = SubCookieUtil.getAll(name);
        if (subcookies) {
            delete subcookies[subName];
            SubCookieUtil.setAll(name, subcookies, null, path, domain, secure);
        }
    }

    static unsetAll(name, path, domain, secure) {
        SubCookieUtil.setAll(name, null, new Date(0), path, domain, secure);
    }
}
````

使用子cookie要特别注意cookie的大小,不要超过对单个cookie大小的限制.

### 使用cookie的注意事项
还有一种叫作`HTTP-only`的`cookie`.`HTTP-only`可以在浏览器设置,也可以在服务器设置,但只能在服务器上读取,这是因为JS无法取得这种`cookie`的值.

因为所有cookie都会作为请求头部由浏览器发送给服务器,所以在cookie中保存大量信息可能会影响特定域浏览器请求的性能.保存的cookie越大,请求完成的时间就越长.即使浏览器对cookie大小有限制,最好还是尽可能在cookie中只保存必要信息,以避免性能问题.

对cookie的限制及其特性决定了cookie并不是存储大量数据的理想方式.因此,其他客户端存储技术出现了.

**注意:不要在cookie中存储重要或敏感的信息.cookie数据不是保存在安全的环境中的,因此任何人都可能获得.应该避免把信用卡号或个人地址等信息保存在cookie中.**

## Web Storage
`Web Storage`的目的是解决通过客户端存储不需要频繁发送回服务器的数据时使用`cookie`的问题.

[MDN-Web Storage API](https://developer.mozilla.org/zh-CN/docs/Web/API/Web_Storage_API)

`Web Storage`主要的目标是:
- 提供在`cookie`之外的存储会话数据的途径
- 提供跨会话持久化存储大量数据的机制

`Web Storage`定义了两个对象:`localStorage`和`sessionStorage`.`localStorage`是永久存储机制,`sessionStorage`是跨会话的存储机制.这两种浏览器存储API提供了在浏览器中不受页面刷新影响而存储数据的两种方式.

### Storage类型
`Storage`类用于保存名值对数据,直至存储空间上限(由浏览器决定).`Storage`的实例与其他对象(`Object`)一样,但增加了以下方法:
- `clear()`:删除所有值.
- `getItem(name)`:取得给定`name`的值.
- `key(index)`:取得给定数值位置的名称.
- `removeItem(name)`:删除给定`name`的名值对.
- `setItem(name, value)`:设置给定`name`的值.

既可以使用上面的这些方法,也可以直接使用`.`和`[]`来访问和设置这些属性,也可以使用`delete`来删除属性,因为其本质上就是`Object`.但还是建议使用上面的方法来执行这些操作.

还可以通过`length`属性确定`Storage`对象中存储了多少名值对.但无法确定对象中所有数据占用的空间大小.

`Storage`类型只能存储字符串.非字符串数据在存储之前会自动转换为字符串.注意,这种转换不能在获取数据时撤销.

### sessionStorage对象
`sessionStorage`对象只存储会话数据,这意味着数据只会存储到浏览器关闭.这跟浏览器关闭时会消失的会话`cookie`类似.存储在`sessionStorage`中的数据不受页面刷新影响,可以在浏览器崩溃并重启后恢复(取决于浏览器).

因为`sessionStorage`对象与服务器会话紧密相关,所以在运行本地文件时不能使用.存储在`sessionStorage`对象中的数据对于不同页面(不同URL)之间是互相独立的.

`window.sessionStorage`对象是`Storage`实例,所以可以直接使用其实例方法:
````JS
sessionStorage.setItem("name", "aaa");
````

所有现代浏览器在实现存储写入时都使用了同步阻塞方式,因此数据会立即提交到存储.具体API实现可能不会立即把数据写入磁盘,但这个区别在JS层面不可见.通过`Web Storage`写入的任何数据都可以立即被读取.

### localStorage对象
`localStorage`取代了`globalStorage`,作为在客户端持久存储数据的机制.要访问同一个`localStorage`对象,页面必须来自同一个域(子域不可以),在相同的端口上使用相同的协议.

因为`window.localStorage`是`Storage`的实例,所以可以使用`Storage`的实例方法:
````JS
localStorage.setItem("name", "aaa");
````

这两种存储方法的区别在于,存储在`localStorage`中的数据会保留到通过JS删除或者用户清除浏览器缓存.`localStorage`数据不受页面刷新影响,也不会因关闭窗口,标签页或重新启动浏览器而丢失.

### 存储事件
每当`Storage`对象变化时,都会在文档上触发`storage`事件.使用属性或`setItem()`设置值,使用`delete`或`removeItem()`删除值,以及每次调用`clear()`时都会触发这个事件.这个事件的`event`对象有如下4个属性:
- `domain`:存储变化对应的域.
- `key`:被设置或删除的键.
- `newValue`:键被设置的新值,若键被删除则为`null`.
- `oldValue`:键变化之前的值.

注意:若页面A和B为同一域名的不同页面,页面A中注册了事件处理程序`storage`,则在页面B上对于`Storage`对象的修改会被页面A上的事件处理程序所接收.

使用例:
````JS
window.addEventListener("storage",
    (event) => console.log(`Storage changed for ${event.domain}`));
````

对于`sessionStorage`和`localStorage`上的任何修改都会触发`storage`事件,但`storage`事件不会区分这两者.

### 限制
与其他客户端存储方案一样,`Web Storage`也有限制.具体的限制取决于特定的浏览器.一般来说,客户端数据的大小限制是按照每个源(协议,域,端口)来设置的,因此每个源有固定大小的存储空间.分析存储数据的页面的源可以加强这一限制.

不同浏览器给`localStorage`和`sessionStorage`设置了不同的空间限制,但大多数会限制为每个源`5MB`.

详细信息可参考:
- [web.dev-Storage for the Web](https://web.dev/articles/storage-for-the-web?hl=en)
- [dev-test.nemikor.com-Web Storage Support Test](http://dev-test.nemikor.com/web-storage/support-test/)

## IndexedDB
`Indexed Database API`简称`IndexedDB`,是浏览器中存储结构化数据的一个方案.`IndexedDB`用于代替目前已废弃的`Web SQL Database API`.`IndexedDB`背后的思想是创造一套API,方便JS对象的存储和获取,同时也支持查询和搜索.

`IndexedDB`的设计几乎完全是异步的.为此,大多数浏览器操作以请求的形式执行,这些请求会异步执行,产生成功的结果或错误.绝大多数`IndexedDB`操作要求添加`error`和`success`事件处理程序来确定输出.

*较旧的浏览器可能不支持IndexDB.*

详见:[MDN-IndexDB](https://developer.mozilla.org/zh-CN/docs/Web/API/IndexedDB_API)

### 数据库
`IndexedDB`是类似于`MySQL`或`Web SQL Database`的数据库.与传统数据库的最大区别在于,`IndexedDB`使用对象存储而不是表格保存数据.`IndexedDB`数据库就是在一个公共命名空间下的一组对象存储,类似于`NoSQL`风格的实现.

使用`IndexedDB`数据库的第一步是调用`indexedDB.open()`方法,并给它传入一个要打开的数据库名称.如果给定名称的数据库已存在,则会发送一个打开它的请求;如果不存在,则会发送创建并打开这个数据库的请求.这个方法会返回一个`IDBRequest`的实例,可以在这个实例上添加`error`和`success`事件处理程序:
````JS
let db,
    request,
    version = 1;
request = indexedDB.open("admin", version);
request.onerror = (event) => console.log(`Failed to open: ${event.target.errorCode}`);
request.onsuccess = (event) => {
    db = event.target.result;
}
````

`open()`函数的第二个参数是要打开的数据库的版本.这个版本号会被转换为一个`unsigned long long`数值,因此不要使用小数.

在两个事件处理程序中,`event.target`都指向`IDBRequest`实例,如果`success`事件处理程序被调用,说明可以通过`event.target.result`访问数据库(`IDBDatabase`)实例了.如果`error`事件处理程序被调用,`event.target.errorCode`中就会存储表示问题的错误码.

### 对象存储
例如,要存储以下记录:
````JS
let user = {
    username: "007",
    firstName: "James",
    lastName: "Bond",
    password: "foo"
};
````
这个对象最适合作为对象存储键的是`username`属性.该属性必须全局唯一,它也是大多数情况下访问数据的凭据.这个键很重要,因为创建对象存储时必须指定一个键.

当你创建一个**新的数据库**或者**增加已存在的数据库的版本号**(当打开数据库时,指定一个比之前更大的版本号),会触发`upgradeneeded`事件,`IDBVersionChangeEvent`对象会作为参数传递给绑定在`request.result`(例如示例中的`db`)上的`versionchange`事件处理器.在 `upgradeneeded`事件的处理器中,你应该创建该数据库版本需要的*对象存储*(object store):
````JS
// MDN上的示例
request.onupgradeneeded = (event) => {
  // 保存 IDBDatabase 接口
  const db = event.target.result;   // db是IDBDatabase实例
  // db.versionchange是IDBVersionChangeEvent实例
  // 为数据库创建对象存储（objectStore）
  const objectStore = db.createObjectStore("users", { keyPath: "username" });
};
````
这里第二个参数的`keyPath`属性表示应该用作键的存储对象的属性名.

在这种情况下(指触发`upgradeneeded`事件),数据库会保留之前版本数据库的对象存储,因此你不必再次创建这些对象存储.你需要创建新的对象存储,或删除不再需要的上一版本中的对象存储.如果你需要修改一个已存在的对象存储(例如要修改`keyPath`),你必须先删除原先的对象存储,然后使用新的选项再次创建.(注意,这样会丢失对象存储中的数据,如果你需要保存这些信息,你要在数据库版本更新前读取出来并保存在别处).

尝试创建一个与已存在(重名)的对象存储(或删除一个不存在的对象存储)会抛出错误.

### 事务
创建了对象存储之后,剩下的所有操作都是通过**事务**完成的.事务要通过调用数据库对象的`transaction()`方法创建.任何时候,之啊哟想要读取或修改数据,都要通过事务把所有修改操作组织起来.最简单的情况下,可以像下面这样创建事务:`let transaction = db.transaction();`.

如果不指定参数,则对数据库中所有的对象存储有只读权限.更具体的方式是指定一个或多个要访问的对象存储的名称:
````JS
let t1 = db.transaction("users");   // 访问一个对象存储
let t2 = db.transaction(["users", "anotherStore"]); // 访问多个对象存储
````

上面创建的事务都是只读访问的.要修改访问模式,可以传入第二个参数.这个参数应该是下列三个字符串之一:`"readonly"`,`"readwrite"`或`"versionchange"`.比如:`let transaction = db.transaction("users", "readwrite");`.

有了事务的引用,就可以使用`objectStore()`方法并传入对象存储的名称以访问特定的存储对象.然后,可以使用`add()`和`put()`方法添加和更新对象,使用`get()`取得对象,使用`delete()`删除对象,使用`clear()`删除所有对象.其中,`get()`和`delete()`方法都接收对象键作为参数,这5个方法都创建新的请求对象:
````JS
const transaction = db.transaction("users"),
      store = transaction.objectStore("users"),
      request = store.get("007");
request.onerror = (event) => console.log("Did not get the object!");
request.onsuccess = (event) => cosole.log(event.target.result.firstName);
````

因为一个事务可以完成任意多个请求,所以事务对象本身也有事件处理程序:`error`和`complete`.这两个事件可以用来获取事务级的状态信息:
````JS
transaction.onerror = (event) => {
    // 整个事务被取消
};
transaction.oncomplete = (event) => {
    // 整个事务成功完成
};
````

注意,不能通过`oncomplete`事件处理程序的`event`对象访问`get()`请求返回的任何数据.

### 插入对象
`add()`或`put()`都接收一个参数,即要存储的对象,并把对象保存到对象存储,这两个方法只在对象存储中已存在同名的键时有区别.这种情况下,`add()`会导致错误,而`put()`会简单地重写该对象.

每次调用`add()`或`put()`都会创建对象存储的新更新请求.如果想验证成功与否,可以把请求对象保存到一个变量,然后为它添加`error`和`success`事件处理程序:
````JS
// users是一个用户数据的数组
let request,
    requests = [];
for (let user of users) {
    request = store.add(user);
    request.onerror = () => {
        // 处理错误
    };
    request.onsuccess = () => {
        // 处理成功
    };
    requests.push(request);
}
````

### 通过游标查询
使用事务可以通过一个已知键取得一条记录.如果想取得多条数据,则需要在事务中创建一个游标.游标是一个指向结果集的指针.与传统的数据库查询不同,游标不会事先收集所有结果.相反,游标指向第一个结果,并在接到指定前不会主动查找下一条数据.

需要在对象存储上调用`openCursor()`方法创建游标.`openCursor()`方法也返回一个请求,因此必须为它添加`success`和`error`事件处理程序:
````JS
const transaction = db.transaction("users"),
      store = transaction.objectStore("users"),
      request = store.openCursor();
request.onsuccess = (event) => {
    // 处理成功
};
request.onerror = (event) => {
    // 处理错误
};
````

在调用`success`事件处理程序时,可以通过`event.target.result`访问存储中下一条记录,这个属性中保存着`IDBCursor`实例(有下一条记录时)或`null`(没有记录时).这个`IDBCursor`实例有几个属性:
- `direction`:字符串常量,表示游标的前进方向以及是否应该遍历所有重复的值.可能的值包括:
  - `NEXT("next")`
  - `NEXTUNIQUE("nextunique")`
  - `PREV("prev")`
  - `PREVUNIQUE("prevunique")`
- `key`:对象的键.
- `value`:实际的对象.
- `primaryKey`:游标使用的键.可能是对象键或索引键(见下文).

````JS
request.onsuccess = (event) => {
    const cursor = event.target.result;
    if (cursor) {   // 永远要检查,因为如果没有下一条记录,cursor为null
        console.log(`Key: ${cursor.key}, Value: ${JSON.stringify(cursor.value)}`);
        // cursor.value返回的是实际的对象,使用JSON.stringify()是为了方便显示
    }
};
````

游标(上例中的`cursor`)可用于更新个别记录.`update()`方法使用指定的对象更新当前游标对应的值.其返回一个请求,也需要为它添加`success`和`error`事件处理程序.

游标上的`delete()`方法可以删除游标位置的记录,返回一个请求.

如果事务没有修改对象的权限,`update()`和`delete()`都会抛出错误.

默认情况下,每个游标只会创建一个请求.要创建另一个请求,必须调用下列中的一个方法:
- `continue(key)`:移动到结果集中的下一条记录.参数`key`是可选的.如果没有指定`key`,游标就移动到下一条记录;如果指定了,则游标移动到指定的键.
- `advance(count)`:游标向前移动指定的`count`条记录.

这两个方法都会让游标重用相同的请求,因此也会重用`success`和`error`处理程序.

### 键范围
使用**键范围**可以让游标更容易管理.键范围对应`IDBKeyRange`的实例.

有四种方式指定键范围,第一种是使用`only()`方法并传入想要获取的键:`const onlyRange = IDBKeyRange.only("007");`.这个范围保证只获取键为`"007"`的值.使用这个范围创建的游标类似于直接访问对象存储并调用`get("007")`.

第二种键范围可以定义结果集的下限.下限表示游标开始的位置.例如:`const lowerRange = IDBKeyRange.lowerBound("007");`保证游标从`"007"`这个键开始,直到最后.

如果想从`"007"`这个键后面的一条记录开始,可以再传入第二个参数`true`:`const lowerRange = IDBKeyRange.lowerBound("007", true);`

第三种见范围可以定义结果集的上限,通过调用`upperBound()`方法可以指定游标不会越过的记录,例如:`const upperRange = IDBKeyRange.upperBound("end");`.该键范围保证游标从头开始并在到达键为`"end"`的记录停止.如果不想包含指定的键,可以在第二个参数传入`true`.

要同时指定下限和上限,可以使用`bound()`方法.这个方法接收四个参数:下限的键,上限的键,两个可选的布尔值分别表示是否跳过下限和上限.例如:`const boundRange = IDBKeyRange.bound("007", "end", false, true);`.

定义了范围之后,把它传给`openCursor()`方法,就可以得到位于该范围内的游标:
````JS
const transaction = db.transaction("users"),
      store = transaction.objectStore("users"),
      range = IDBKeyRange.bound("007", "end");
      request = store.openCursor(range);
request.onsuccess = (event) => {
    const cursor = event.target.result;
    if (cursor) {
        console.log(`Key: ${cursor.key}, Value: ${JSON.stringify(cursor.value)}`);
        cursor.continue();
    } else {
        console.log("Done!");
    }
};
````

### 设置游标的方向
`openCursor()`方法可以接收两个可选参数,第一个是`IDBKeyRange`的实例,第二个是表示方向的字符串.通常,游标都是从对象存储的第一条记录开始,每次调用`continue()`或`advance()`都会向后一条记录前进,即默认为`"next"`.

向第二个参数中传入[通过游标查询](#通过游标查询)中提到的`direction`属性中的字符串,可以指定方向:
````JS
const transaction = db.transaction("users"),
      store = transaction.objectStore("users"),
      request = store.openCursor(null, "nextunique");
````

对于`"prev"`和`"prevunique"`,会从最后一项开始向第一项移动.

### 索引
对于某些数据集,可能需要为对象存储指定多个键.例如,如果同时记录了用户ID和用户名,那可能需要通过任何一种方式来获取用户数据.为此,可以考虑将用户ID作为主键,然后在用户名上创建索引.

要创建索引,首先要取得对象存储的引用,然后调用`createIndex()`:
````JS
const transaction = db.transaction("users"),
      store = transaction.objectStore("users"),
      index = store.createIndex("username", "username", {unique: true});
````
`createIndex()`的第一个参数是索引的名称,第二个参数是索引属性的名称,第三个参数是包含键`unique`的`options`对象.这个选项中的`unique`应该必须指定,表示这个键是否在所有记录中唯一.

`createIndex`返回的是`IDBIndex`实例.在对象存储上调用`index()`方法也可以得到同一个实例.例如,要使用一个已存在的名为`"username"`的索引,可以像下面这样:
````JS
const transaction = db.transaction("users"),
      store = transaction.objectStore("users"),
      index = store.index("username");
````

可以在索引上使用`openCursor()`方法创建游标,这个游标与在对象存储上的游标完全一样.只是其`result.key`属性中保存的是索引键,而不是主键.

使用`openKeyCursor()`方法也可以在索引上创建特殊游标,只返回每条记录的主键.这个方法接收的参数与`openCursor()`一样.最大的不同在于,`event.result.key`是索引键,`event.result.value`是主键而不是整条记录.

可以使用`get()`方法并传入索引键通过索引得到单条记录,这会创建一个新请求.

如果想只取得给定索引键的主键,可以使用`getKey()`方法.这样也会创建一个新请求,但`result.value`等于主键而不是整个记录.

任何时候,都可以使用`IDBIndex`对象的下列属性取得索引的相关信息:
- `name`:索引的名称.
- `keyPath`:调用`createIndex()`时传入的属性路径.
- `objectStore`:索引对应的对象存储.
- `unique`:表示索引键是否唯一的布尔值.

对象存储自身也有一个`indexNames`属性,保存着与之相关索引的名称的数组.

在对象存储上调用`deleteIndex()`方法并传入索引的名称可以删除索引.因为删除索引不会影响对象存储中的数据,所以这个操作没有回调.

### 并发问题
`IndexDB`虽然是网页中的异步API,但仍存在并发问题.如果两个不同的浏览器标签页同时打开了同一个网页,则有可能出现一个网页尝试升级数据库而另一个尚未就绪的情形.有问题的操作是设置数据库为新版本,而版本变化只能在浏览器只有一个标签页使用数据库时才能完成.

第一次打开数据库时,添加`versionchange`事件处理程序非常重要.另一个同源标签页将数据库打开到新版本时,将执行此回调.对这个事件最好的响应是立即关闭数据库,以便完成版本升级.(即标签页A**正在**更新数据库,同源标签页B打开数据库时将接收到`versionchange`事件)

````JS
let request, database;
request = indexedDB.open("admin", 1);
request.onsuccess = (event) => {
    database = event.target.result;
    database.onversionchange = () => database.close();
};
````

始终都指定这些事件处理程序,可以保证Web应用程序能够更好地处理与`IndexedDB`相关的并发问题.

关于此方面的问题,也可以看[MDN上相关的页面](https://developer.mozilla.org/zh-CN/docs/Web/API/IndexedDB_API/Using_IndexedDB#%E5%BD%93%E4%B8%80%E4%B8%AA_web_%E5%BA%94%E7%94%A8%E5%9C%A8%E5%8F%A6%E4%B8%80%E4%B8%AA%E6%A0%87%E7%AD%BE%E9%A1%B5%E4%B8%AD%E8%A2%AB%E6%89%93%E5%BC%80%E6%97%B6%E7%9A%84%E7%89%88%E6%9C%AC%E5%8F%98%E6%9B%B4)

### 限制
`IndexedDB`数据库是与页面源(协议,域,端口)绑定的,因此信息不能跨源共享.这意味着`www.example.org`和`p2p.example.org`会对应不同的数据存储.

其次,每个源都有可以存储的空间限制.详见[MDN-浏览器存储限制和回收标准](https://developer.mozilla.org/en-US/docs/Web/API/Storage_API/Storage_quotas_and_eviction_criteria).

此外,有些浏览器中,本地网页不能访问`IndexedDB`数据库.

这些数据都没有被加密,所以要注意不能使用它们存储敏感信息.

# 模块
## 理解模块模式
将代码拆分为独立的块,然后再把这些块连接起来可以通过模块模式来实现.这种模式背后的思想很简单:把逻辑分块,各自封装,相互独立,每个块自行决定对外暴露什么,同时自行决定引入执行哪些外部代码.不同的实现和特性让这些基本的概念变得有点复杂,但这个基本的思想是所有JS模块系统的基础.

### 模块标识符
模块标识符是所有模块系统通用的概念.模块系统本质上是键值实体,其中每个模块都有个可用于引用它的标识符.这个标识符再模拟模块系统中可能是字符串,在原生实现的模块系统中可能是模块文件的实际路径.完善的模块系统应该能够无歧义地引用其他模块.

将模块标识符解析为实际模块的过程中要根据模块系统对标识符的实现.原生浏览器模块标识符必须提供实际JS文件的路径.

### 模块依赖
模块系统的核心是管理依赖.

### 模块加载
在浏览器中,加载模块涉及几个步骤.加载模块涉及执行其中的代码,但必须是在所有依赖都加载并执行之后.如果浏览器没有收到依赖模块的代码,则必须发送请求并等待网络返回.收到模块代码之后,浏览器必须确定刚收到的模块是否也有依赖.然后递归地评估并加载所有依赖,直到所有依赖模块都加载完毕.只有整个依赖图都加载完成,才可以执行入口模块.

### 入口
相互依赖的模块必须指定一个模块作为入口,这也是所有代码执行的起点.因为JS是顺序执行的,并且是单线程的,所以代码必须有执行的起点.入口模块是可以有依赖的.

模块依赖图是有向无环图,其加载顺序必须满足拓扑排序.

模块加载是"阻塞的",前置操作必须完成才能执行后续操作.

### 异步依赖
有些模块之间不存在依赖关系,但对于同步加载,可能因为受限于网络原因,这种加载方式会导致没有依赖关系的模块需要等待另一个模块加载完成.

使用异步加载让没有依赖的模块异步加载可以提高性能,这是ES6模块规范中实现的行为.

### 动态依赖
有些模块系统要求开发者在模块开始列出所有模块,而有些模块则允许开发者在程序结构中动态添加依赖:
````JS
if (loadCondition) {
    require('./moduleA');
}
````

### 静态分析
模块中包含的发送到浏览器的JS代码经常会被静态分析,分析工具会检查代码结构并在不实际执行代码的情况下推断其行为.对静态分析友好的模块系统可以让模块打包系统更容易将代码处理为较少的文件.它还将支持在智能编辑器里智能自动完成.

更复杂的模块行为,例如静态依赖,会导致静态分析更困难.不同模块系统和模块加载器具有不同层次的复杂度.至于模块依赖,额外的复杂度会导致相关工具更难预测模块在执行时到底需要哪些依赖.

### 循环依赖
要构建一个没有循环依赖的JS应用程序几乎是不可能的,因此包括CommonJS,AMD,ES6在内的所有模块系统都支持循环依赖.在包含循环依赖的应用程序中,模块加载顺序可能会出人意料.但只要适当地封装模块,使它们没有副作用,加载顺序就应该不会影响应用程序的运行.

## 凑合的模块模式
这是ES6之前的模块模式.不作赘述.

## 使用ES6之前的模块加载器
以下是ES6之前的模块模式.不作赘述,只作列举.

- `CommonJS`
- `AMD`(异步模块定义,Asynchronous Module Definition)
- `UMD`(通用模块定义,Universal Module Definition)

## 使用ES6模块
[MDN上的模块教程](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Modules)

动态加载模块是新标准,下文没有列出,可见[MDN-动态加载模块](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Modules#%E5%8A%A8%E6%80%81%E5%8A%A0%E8%BD%BD%E6%A8%A1%E5%9D%97).

### 模块标签及定义
ES6模块是作为一整块JS代码而存在的.带有`type="module"`属性的`<script>`标签会告诉浏览器相关代码应该作为模块执行,而不是作为传统的脚本执行.模块可以嵌入在网页中,也可以作为外部文件引入:
````HTML
<script type="module">
    // 模块代码
</script>
<script type="module" src="path/to/myModule.js"></script>
````

**注意:使用`type="module"`属性的脚本基本是作为顶级模块**

**注意:只能在模块内部使用`import`和`export`语句,而不是普通脚本文件.被入口模块导入的其他脚本一般不会写入HTML代码中,因此可以使用`import`和`export`语句.**

即使与常规JS文件处理方式不同,JS模块文件也没有专门的内容类型.

与传统脚本不同,所有模块都会像`<script defer>`加载的脚本一样按顺序执行,解析到`<script type="module">`标签后会立即下载模块文件,但执行会延迟到文档解析完成.无论对嵌入的模块代码还是外部引入的模块代码,都是这样.`<script type="module">`在页面中出现的顺序就是它们执行的顺序.与`<script defer>`一样,修改模块标签的位置,无论是在`<head>`还是在`<body>`中,只会影响文件什么时候加载,而不会影响模块什么时候加载.

例如:
````HTML
<!-- 第二个执行 -->
<script type="module" src="moduleA.js"></script>

<!-- 第三个执行 -->
<script type="module" src="moduleB.js"></script>

<!-- 第一个执行 -->
<script></script>
````

也可以给模块标签添加`async`属性.这样影响就是双重的:不仅模块执行顺序不再与`<script>`标签在页面中的顺序绑定,模块也不会等待文档完成解析才执行.不过,入口模块仍必须等待其依赖加载完成.

与`<script type="module">`标签关联的ES6模块被认为是模块图中的入口模块(可以依赖其他JS文件).一个页面上有多少个入口模块没有限制,重复加载同一个模块也没有限制.同一个模块无论在一个页面中被加载多少次,也不管它是如何加载的,实际上都只会加载一次:
````HTML
<!-- moduleA在这个页面上只会被加载一次 -->
<script type="module">
    import './moduleA.js'
</script>
<script type="module">
    import './moduleA.js'
</script>
<script type="module" src="./moduleA.js"></script>
<script type="module" src="./moduleA.js"></script>
````

嵌入的模块定义代码不能使用`import`加载到其他模块.只有通过外部文件加载的模块才可以使用`import`加载.因此,嵌入代码只适合作为入口模块.

在阅读下面的部分前,先看一个MDN给出的使用模块的[示例](https://github.com/mdn/js-examples/tree/main/module-examples/basic-modules).

文件结构如下:
```
index.html
main.js
modules/
    canvas.js
    square.js
```

- **index.html**
````HTML
<!DOCTYPE html>
<html lang="en-US">
  <head>
    <meta charset="utf-8">
    <title>Basic JavaScript module example</title>
    <style>
      canvas {
        border: 1px solid black;
      }
    </style>
    <script type="module" src="main.js"></script>
  </head>
  <body>

  </body>
</html>
````

- **main.js**
````JS
import { create, createReportList } from './modules/canvas.js';
import { name, draw, reportArea, reportPerimeter } from './modules/square.js';
import randomSquare from './modules/square.js';

let myCanvas = create('myCanvas', document.body, 480, 320);
let reportList = createReportList(myCanvas.id);

let square1 = draw(myCanvas.ctx, 50, 50, 100, 'blue');
reportArea(square1.length, reportList);
reportPerimeter(square1.length, reportList);

// Use the default
let square2 = randomSquare(myCanvas.ctx);
````

- **module/canvas.js**
````JS
function create(id, parent, width, height) {
  let divWrapper = document.createElement('div');
  let canvasElem = document.createElement('canvas');
  parent.appendChild(divWrapper);
  divWrapper.appendChild(canvasElem);

  divWrapper.id = id;
  canvasElem.width = width;
  canvasElem.height = height;

  let ctx = canvasElem.getContext('2d');

  return {
    ctx: ctx,
    id: id
  };
}

function createReportList(wrapperId) {
  let list = document.createElement('ul');
  list.id = wrapperId + '-reporter';

  let canvasWrapper = document.getElementById(wrapperId);
  canvasWrapper.appendChild(list);

  return list.id;
}

export { create, createReportList };
````

**module/square.js**
````JS
const name = 'square';

function draw(ctx, length, x, y, color) {
  ctx.fillStyle = color;
  ctx.fillRect(x, y, length, length);

  return {
    length: length,
    x: x,
    y: y,
    color: color
  };
}

function random(min, max) {
   let num = Math.floor(Math.random() * (max - min)) + min;
   return num;
}

function reportArea(length, listId) {
  let listItem = document.createElement('li');
  listItem.textContent = `${name} area is ${length * length}px squared.`

  let list = document.getElementById(listId);
  list.appendChild(listItem);
}

function reportPerimeter(length, listId) {
  let listItem = document.createElement('li');
  listItem.textContent = `${name} perimeter is ${length * 4}px.`

  let list = document.getElementById(listId);
  list.appendChild(listItem);
}

function randomSquare(ctx) {
  let color1 = random(0, 255);
  let color2 = random(0, 255);
  let color3 = random(0, 255);
  let color = `rgb(${color1},${color2},${color3})`
  ctx.fillStyle = color;

  let x = random(0, 480);
  let y = random(0, 320);
  let length = random(10, 100);
  ctx.fillRect(x, y, length, length);

  return {
    length: length,
    x: x,
    y: y,
    color: color
  };
}

export { name, draw, reportArea, reportPerimeter };
export default randomSquare;
````

### 模块加载
ES6模块的独特之处在于,既可以通过浏览器原生加载,也可以与第三方加载器和构建工具一起加载.事实上,很多时候使用第三方工具可能会更方便.

可以让浏览器从顶级模块加载整个依赖图,且是异步完成的.浏览器会解析入口模块,确定依赖,并发送对依赖的请求.这些文件通过网络返回后,浏览器就会解析它们的内容,确定它们的依赖,如果这些二级依赖还没有加载,则会发送更多请求.这个异步递归加载过程会持续到整个应用程序的依赖图都解析完毕.解析完依赖图,应用程序就可以正式加载模块了.

### 模块行为
ES6模块借用了`CommonJS`和`AMD`的很多优秀特性.包括:
- 模块代码只在加载后执行.
- 模块只能加载一次.
- 模块是单例.
- 模块可以定义公共接口,其他接口可以基于这个公共接口观察和交互.
- 模块可以请求加载其他模块.
- 支持循环依赖.

ES6模块系统也增加了一些新行为:
- ES6模块默认在严格模式下执行.
- ES6模块不共享全局命名空间.
- 模块顶级`this`的值是`undefined`(常规脚本中是`window`).
- 模块中的`var`声明不会添加到`window`对象.
- ES6模块是异步加载和执行的.

浏览器运行时在应该知道应该把某个文件当成模块时,会有条件地按照上述ES6模块行为来施加限制.与`<script type="module">`关联或者通过`import`语句加载的JS文件会被认定为模块.

### 模块导出
ES6模块中,控制模块的哪些部分对外部可见的是`export`关键字.ES6模块支持两种导出:命名导出和默认导出.不同的导出方式对应不同的导入方式.

`export`关键字用于声明一个值为命名导出.导出语句必须在模块顶级,不能嵌套在某个块中:
````JS
export ...  // OK
if (condition) {
    export ...  // Error
}
````

导出值对模块内部JS的执行没有直接影响,因此`export`语句与导出值的相对位置或者`export`关键字在模块中出现的顺序没有限制.`export`语句甚至可以出现在它要导出的值之前:
````JS
const foo = 'foo';
export { foo }; // OK

export const foo = 'foo';   // OK

export { foo }; // OK,但应该避免
const foo = 'foo';
````

**命名导出**就好像模块是被导出值的容器.

行内命名导出,顾名思义,可以在同一行执行变量声明.例如:
````JS
export const foo = 'foo';
````

变量声明跟导出可以不在一行.可以在`export`子句中执行声明并将标识符导出到模块的其他地方:
````JS
const foo = 'foo';
export { foo };
````

导出时也可以提供别名,别名必须在`export`子句的大括号语法中指定.因此,声明值,导出值和为导出值提供别名不能在一行完成.例如:
````JS
const foo = 'foo';
export { foo as myFoo };
````

命名导出可以有多个:
````JS
const baz = "baz";
const qux = "qux"
export const foo = "foo";
export const bar = "bar";
export { baz, qux as myQux };
````

**默认导出**就好像模块与被导出的值是一回事.默认导出使用`default`关键字将一个值声明为默认导出,每个模块都只能有一个默认导出.重复的默认导出会导致`SyntaxError`.

下面的例子中,外部模块导入这个模块,则会让被导入模块本身的值为`foo`的值:
````JS
const foo = "foo";
export default foo;
````

在别名中使用`default`也是默认导出,即使使用的是命名导出的语法:
````JS
const foo = "foo";
export { foo as default };
````

命名导出和默认导出是不冲突的:
````JS
const foo = "foo";
const bar = "bar";
const baz = "baz";
export { foo };
export { bar as default, baz };
````

ES6规范对不同形式的`export`语句中可以使用什么,不可以使用什么规定了限制.某些形式允许声明和赋值,某些形式只允许表达式,而某些形式则只允许简单标识符.注意,有的形式使用了分号,有的则没有:
````JS
// 命名行内导出
export const baz = 'baz';
export const foo = 'foo', bar = 'bar';
export function foo() {}
export function* foo() {}
export class Foo {}

// 命名子句导出
export { foo }; // 这里的标识符可以指的是变量,函数或者类声明
export { foo, bar };
export { foo as myFoo, bar };

// 默认导出
export default 'foo';
export default 123;
export default /[a-z]*/;
export default { foo: 'foo' };
export { foo /* 这个不是默认导入,后面的才是 */ , bar as default };
export default foo;
export default function() {}
export default function foo() {}
export default function*() {}
export default class {}

// 会导致错误的不同形式:
// 行内默认导出中不能出现变量声明
export default const foo = 'bar';

// 只有标识符可以出现在export子句中
export { 123 as foo };
export 123;

// 别名只能在export子句中出现
export const foo = 'foo' as myFoo;
````

### 模块导入
模块可以通过使用`import`关键字使用其他模块导出的值.与`export`类似,`import`必须出现在模块的顶级:
````JS
import ...  // OK
if (condition) {
    import ...  // Error
}
````

`import`语句被提升到模块顶部.因此,`import`语句与使用导入值的语句的相对位置并不重要.不过,还是推荐把导入语句放在模块顶部:
````JS
import { foo } from "./fooModule.js";
console.log(foo);   // OK

console.log(foo);
import { foo } from "./fooModule.js";   // OK,但应该避免
````

模块标识符可以是相对于当前模块的相对路径,也可以是指向模块文件的绝对路径.它必须是纯字符串,不能是动态计算的结果.例如,不能是拼接的字符串.

如果在浏览器中通过标识符原生加载模块,则文件必须带有`.js`扩展名(或者[`.mjs`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Modules#.mjs_%E4%B8%8E_.js)),不然可能无法正确解析.不过,如果是通过构建工具或第三方模块加载器打包或解析的ES6模块,则可能不需要包含文件扩展名.
````JS
import ... from "./bar.js";
import ... from "../bar.js";
import ... from "/bar.js";  // 这指的是根目录下的bar.js
````

不是必须通过导出的成员才能导入模块.如果不需要模块的特定导出,但仍想加载和执行模块以利用其副作用(即模块所导出的东西或者模块内声明的变量,函数或者类都不能使用,但模块被执行了,因此像`console.log()`语句或者对`HTMLElement`的修改等都有实际作用),可以只通过路径加载它:
````JS
import './foo.js';
````

导入对于模块而言是只读的,实际上相当于`const`声明的变量.在使用`*`执行批量导入时,赋值给别名的命名导入就好像使用`Object.freeze()`冻结过一样(也就是导出`foo`,使用`Foo`作为别名导入`*`,则`Foo`当中的不能添加,删除,或修改任何属性,例如`Foo.foo`,但修改`Foo.foo.bar`是可以的).直接修改导出的值是不可能的,但可以修改导出对象的属性.要修改导出的值,必须使用有内部变量和属性访问权限的导出方法:
````JS
import foo, * as Foo from './foo.js';
foo = 'foo';        // Error
Foo.foo = 'foo';    // Error
foo.bar = 'bar';    // OK
````

命名导出和默认导出的区别也反映在它们的导入上.命名导出可以使用`*`批量获取并赋值给保存导出集合的别名,而无需列出每个表示符:
````JS
const foo = 'foo', bar = 'bar', baz = 'baz';
export { foo, bar, baz };
// ---- foo.js ^^^ / vvv main.js ----
import * as Foo from './foo.js';
console.log(Foo.foo);
console.log(Foo.bar);
console.log(Foo.baz);
````

要指定别名,需要把标识符放在`import`子句中.使用`import`子句可以为导入的值指定别名:
````JS
import { foo, bar, baz as myBaz } from './foo.js';
console.log(foo);   // foo
console.log(bar);   // bar
console.log(myBaz); // baz
````

默认导出就好像整个模块就是导出的值一样.可以使用`default`关键字并提供别名来导入.也可以不使用大括号,此时指定的标识符就是默认导出的别名:
````JS
// 等效
import { default as foo } from './foo.js';
import foo from './foo.js';
````

如果模块同时导出了命名导出和默认导出,则可以在`import`语句中同时取得它们.可以依次列出特定导出的标识符来取得,也可以使用`*`来取得:
````JS
import foo, { bar, baz } from './foo.js';
import { default as foo, bar, baz } from './foo.js';
import foo, * as Foo from './foo.js';
````

### 模块转移导出
模块导入的值可以直接通过管道转移到导出.此时,也可以将默认导出转换为命名导出,或者相反.

如果想把一个模块的所有命名导出集中在一块,可以像下面这样:
````JS
// bar.js
export * from './foo.js';
````

这样,`foo.js`中的命名导出都会出现在导入`bar.js`的模块中.如果`foo.js`有默认导出,则该语法会忽略它.使用此语法也要注意导出名称是否冲突.如果`foo.js`导出`baz`,`bar.js`也导出`baz`,则最终导出的是`bar.js`中的值.这个"重写"是静默发生的:
````JS
// foo.js
export const baz = 'origin:foo';

// bar.js
export * from './foo.js';
export const baz = 'origin:bar';

// main.js
import { baz } from './bar.js';
console.log(baz);   // origin:bar
````

此外也可以明确列出要从外部模块转移本地导出的值.该语法支持使用别名:
````JS
export { foo, bar as myBar } from './foo.js';
````

类似地,外部模块的默认导出可以重用为当前模块的默认导出:
````JS
export { default } from './foo.js';
````

这样不会复制导出的值,只是把导入的引用传给了原始模块.在原始模块中,导入的值仍然是可用的,与修改导入相关的限制也适用于再次导出的导入.

在重新导出时,还可以在导入模块修改命名或默认导出的角色.比如,可以像下面这样将命名导出指定为默认导出:
````JS
export { foo as default } from './foo.js';
````

### 工作者模块
ES6模块与`Worker`实例完全兼容.在实例化时,可以给工作者传入一个指向模块文件的路径,与传入常规脚本文件一样.`Worker`构造函数接收第二个参数,用于说明传入的是模块文件.

下面是两种类型的`Worker`的实例化行为:
````JS
// 第二个参数默认为{ type: 'classic' }
const scriptWorker = new Worker('scriptWorker.js');
const moduleWorker = new Worker('moduleWorker.js', { type: 'module' });
````

在基于模块的工作者内部,`self.importScripts()`方法通常用于在基于脚本的工作者中加载外部脚本,调用它会抛出错误.这是因为模块的`import`行为包含了`importScripts()`.

### 向后兼容
浏览器在遇到`<script>`标签上无法识别的`type`属性时会拒绝执行其内容.对于不支持模块的浏览器,这意味着`<script type="module">`不会被执行.

支持ES6模块的浏览器也会识别`nomodule`属性.此属性通知支持ES6模块的浏览器不执行脚本.不支持模块的浏览器无法识别该属性,从而忽略这个属性的存在.

````HTML
<!-- 支持模块的浏览器会执行这段脚本 -->
<!-- 不支持模块的浏览器不会执行这段脚本 -->
<script type="module" src="module.js"></script>

<!-- 支持模块的浏览器不会执行这段脚本 -->
<!-- 不支持模块的浏览器会执行这段脚本 -->
<script nomodule src="script.js"></script>
````

# 工作者线程
JS是单线程的,因为像DOM这样的API只能在单线程下执行.但并不意味着不能像多线程语言那样把工作委托给独立的线程执行并发更改,这也就是工作者线程的功能.

工作者线程的价值在于:允许把主线程的工作转嫁给独立的实例,而不改变现有的单线程模型.

[MDN-使用Web Worker](https://developer.mozilla.org/zh-CN/docs/Web/API/Web_Workers_API/Using_web_workers)

## 工作者线程简介
JS环境实际上是运行在托管操作系统中的虚拟环境.在浏览器每打开一个页面,就会分配一个它自己的环境.这样,每个页面都有自己的内存,事件循环,DOM,等等.每个页面就相当于沙盒,不会干扰其他页面.对于浏览器来说,同时管理多个环境是非常简单的,因为所有这些环境都是*并行*执行的.

使用*工作者线程*,浏览器可以在原始页面环境之外再分配一个完全独立的二级子环境.这个子环境**不能**与依赖单线程交互的API(如DOM)互操作,但可以与父环境并行执行代码.

[MDN-Web Worker API](https://developer.mozilla.org/zh-CN/docs/Web/API/Web_Workers_API)

### 工作者线程与线程
工作者线程和线程之间有很多相似之处:
- **工作者线程是以实际线程实现的**.
- **工作者线程并行执行**:虽然页面和工作者线程都是单线程JS环境,每个环境中的指令则可以并行执行.
- **工作者线程可以共享某些内存**:工作者线程能够使用`SharedArrayBuffer`在多个环境间共享内容.虽然线程会使用锁实现并发控制,但JS使用`Atomics`接口实现并发控制.

工作者线程与线程也有不同之处:
- **工作者线程不共享全部内存**:传统多线程模型有能力读写共享内存空间.但工作者线程进出数据需要复制或转移(除了`SharedArrayBuffer`).
- **工作者线程不一定在同一个进程里**:通常,一个进程可以在内部产生多个线程.根据浏览器引擎的实现,工作者线程可能与页面属于同一进程,也可能不属于.
- **创建工作者线程的开销更大**:工作者线程有自己独立的事件循环,全局对象,事件处理程序和其他JS环境必须的特性.这些结构的代价不容忽视.工作者线程不能用于替代线程,其相对较重,不建议大量使用.工作者线程应该是长期运行的,启动成本比较高,每个实例占用的内存也比较大.

### 工作者线程的类型
`Web`工作者线程规范中定义了三种主要的工作者线程:

- **专用工作者线程**

专用工作者线程,通常简称为工作者线程,`Web Worker`或`Worker`,是一种实用的工具,可以让脚本单独创建一个JS线程,以执行委托的任务.专用者线程,顾名思义,只能被创建它的页面使用.

- **共享工作者线程**

共享工作者线程与专用工作者线程非常相似.主要区别是共享工作者线程可以被多个不同的上下文使用,包括不同的页面.任何与创建共享工作者线程的脚本同源的脚本,都可以向共享工作者线程发送消息或从中接收消息.

- **服务工作者线程**

服务工作者线程与专用工作者线程和共享工作者线程截然不同.它的主要用途是拦截,重定向和修改页面发出的请求,充当网络请求的仲裁者的角色.

### WorkerGlobalScope
在网页上,`window`对象可以向运行在其中的脚本暴露各种全局变量.在工作者线程内部,没有`window`的概念.这里的全局对象是`WorkerGlobalScope`的实例,通过`self`关键字暴露出来.

#### WorkerGlobalScope属性和方法
`self`上可用的属性是`window`对象上属性的严格子集.其中有些属性会返回特定于工作者线程的版本:
- `navigator`:返回与工作者线程关联的`WorkerNavigator`.
- `self`:返回`WorkerGlobalScope`对象.
- `location`:返回与工作者线程关联的`WorkerLocation`.
- `performance`:返回(只包含特定属性和方法的)`Performance`对象.
- `console`:返回与工作者线程关联的`Console`对象;对API没有限制.
- `caches`:返回与工作者线程关联的`CacheStorage`对象;对API没有限制.
- `indexedDB`:返回`IDBFactory`对象.
- `isSecureContext`:返回布尔值,表示工作者线程上下文是否安全.
- `origin`:返回`WorkerGlobalScope`的源.

类似地,`self`对象上暴露的一些方法也是`window`上方法的子集.这些`self`上的方法也与`window`上对应的方法操作一样:
- `atob()`
- `btoa()`
- `clearInterval()`
- `clearTimeout()`
- `createImageBitmap()`
- `fetch()`
- `setInterval()`
- `setTimeout()`

`WorkerGlobalScope`还增加了新的全局方法`importScripts()`,只在工作者线程内可用.模块中不允许使用该函数,因为可以使用`import`代替,见[工作者模块](#工作者模块).

更多有关工作者线程可以使用的函数和类,详见[MDN-Web Workers可以使用的函数和类](https://developer.mozilla.org/zh-CN/docs/Web/API/Web_Workers_API/Functions_and_classes_available_to_workers)

#### WorkerGlobalScope的子类
并不是所有地方都实现了`WorkerGlobalScope`.每种类型的工作者线程都使用了自己特定的全局对象,这继承自`WorkerGlobalScope`:
- 专用工作者线程使用`DedicatedWorkerGlobalScope`.
- 共享工作者线程使用`SharedWorkerGlobalScope`.
- 服务工作者线程使用`ServiceWorkerGlobalScope`.

## 专用工作者线程

