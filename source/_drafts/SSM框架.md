---
title: SSM 基础框架总结
date: 2021-12-27
updated: 2022-01-20
tags: [Java, Spring, SpringMVC, MyBatis]
password: 990312
categories: 编程与开发
---

> SSM 是一款当前主流的基础框架组合，Spring 和 SpringMVC 是当前企业开发必用框架之一，MyBatis 则是与数据库交互的持久层框架之一，由于易用性和轻便性，被大多互联网公司所选用。SSM 基础框架的掌握是当前企业开发最基本的要求，也是其他技术学习和进阶的必要基础。我选择的课程为[黑马程序员最全 SSM 框架教程](https://www.bilibili.com/video/BV1WZ4y1P7Bp)，以下为学习过程中所做笔记，可供参考。

<!--more-->

### Spring的 IoC 和 DI

####  Spring 简介

- Spring 是什么
  - Spring 是分层的 Java SE/EE 应用 full-stack 轻量级开源框架，以 IoC（Inverse Of Control：反转控制）和 AOP（Aspect Oriented Programming：面向切面编程）为内核
  - 提供了展现层 SpringMVC 和持久层 Spring JDBC Template 以及业务层事务管理等众多的企业级应用技术，还能整合开源世界众多著名的第三方框架和类库，逐渐成为使用最多的Java EE 企业应用开源框架
- Spring 发展历程
  - 1997 年，IBM提出了EJB 的思想
  - Rod Johnson（Spring 之父）的 Expert One-to-One J2EE Design and Development (2002) 阐述了 J2EE 使用 EJB 开发设计的优点及解决方案
  - Expert One-to-One J2EE Development without EJB(2004) 阐述了 J2EE 开发不使用 EJB的解决方式（Spring 雏形） 
  - 2017 年 9 月份发布了 Spring 的最新版本 Spring5.0 通用版（GA）
- Spring 的优势
  1. 方便解耦，简化开发：通过 Spring 提供的 IoC 容器，可以将对象间的依赖关系交由 Spring 进行控制，避免硬编码所造成的过度耦合。 用户也不必再为单例模式类、属性文件解析等这些很底层的需求编写代码，可以更专注于上层的应用
  2. AOP 编程的支持：通过 Spring的 AOP 功能，方便进行面向切面编程，许多不容易用传统 OOP 实现的功能可以通过 AOP 轻松实现
  3. 声明式事务的支持：可以将我们从单调烦闷的事务管理代码中解脱出来，通过声明式方式灵活的进行事务管理，提高开发效率和质量
  4. 方便程序的测试：可以用非容器依赖的编程方式进行几乎所有的测试工作，测试不再是昂贵的操作，而是随手可做的事情
  5. 方便集成各种优秀框架：Spring对各种优秀框架（Struts、Hibernate、Hessian、Quartz等）的支持
  6. 降低 JavaEE API 的使用难度：Spring对 JavaEE API（如 JDBC、JavaMail、远程调用等）进行了薄薄的封装层，使这些 API 的使用难度大为降低
  7. Java 源码是经典学习范例：Spring的源代码设计精妙、结构清晰、匠心独用，处处体现着大师对 Java 设计模式灵活运用以及对 Java 技术的高深造诣。它的源代码无意是 Java 技术的最佳实践的范例
- Spring 的体系结构
  - <img src="https://docs.spring.io/spring-framework/docs/5.0.0.RC3/spring-framework-reference/images/spring-overview.png" style="zoom: 67%;" />

#### Spring 快速入门

- Spring 程序开发步骤
  1. 导入 Spring 开发的基本包坐标
  2. 编写 Dao 接口和实现类
  3. 创建 Spring 核心配置文件
  4. 在 Spring 配置文件中配置 `UserDaoImpl` 
  5. 使用 Spring 的 API 获得 Bean 实例



# 未完待续

