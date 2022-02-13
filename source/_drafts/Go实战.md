---
title: Go语言从入门到实战
date: 2021-10-01
tags: [Go]
categories: 编程与开发
---

> Go 语言的初步设想始于 2007 年，当时 Go 语言的三位创始人是想通过开发一种新型的语言来解决 Google 在软件开发中面临的问题，如多核硬件架构、超大规模分布式计算集群以及 Web 开发模式导致的前所未有的开发规模和更新速度，Go 语言就是针对这些问题而设计的，所以它被越来越多的公司和组织所使用。我选择的教程是 [Go 语言从入门到实战](https://time.geekbang.org/course/intro/100024001)，以下为所记课堂笔记，可供参考。

<!--more-->

### Go 语言简介

- 软件开发的挑战：多核硬件架构、超大规模分布式计算集群、Web 开发模式导致的前所未有的开发规模和更新速度

- Go 的创始人：Rob Pike、Ken Thompson、Robert Grieseme

- Go 语言特性：简单、高效、生产力、云计算语言、区块链语言

- 基本程序结构

  ```go
  package main  //包，表明代码所在的模块（包）
  import "fmt"  //引入代码依赖
  //功能实现
  func main() {
  	fmt.Println("Hello, world!")
  }
  ```

- 应用程序入口
  - 必须是 main 包：`package main`
  - 必须是 main 方法：`func main() {}`
  - 文件名不一定是 `main.go`
- 退出返回值
  - Go 中 main 函数不支持任何返回值
  - 通过 `os.Exit` 来返回状态
- 获取命令行参数
  - main 函数不支持传入参数
  - 在程序中直接通过 `os.Args` 获取命令行参数

### 基本数据类型

- 编写测试程序：源码文件以 `_test` 结尾（`xxx_test.go`），测试方法名以 Test 开头（`func TestXXX(t *testing.T){...}`）

- 变量赋值可以进行自动类型推断：`a := 1`

- 在一个赋值语句中可以对多个变量进行同时赋值：`a, b = b, a`

- 常量定义：快速设置连续值

  ```go
  const (
  	Open = 1 << iota
      Close
      Pending
  )
  ```

- 

