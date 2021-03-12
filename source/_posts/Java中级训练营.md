---
title: 2021阿里Java训练营第二期
date: 2021-03-12
updated: 2021-03-12
group: ongoing
tags: [Java]
categories: 代码人生
---

>本期训练营是继[Java新手训练营](/Java初级训练营)后的第2期，课程由阿里云开发者社区提供，同样采用5天不间断直播授课的形式，主要内容为Spring Boot 2.5自动化配置原理、实战开发REST API、MySQL数据库、Redis高并发缓存、MQ消息队列Kafka、安全机制、Docker容器等，本篇日志主要记录实战Spring Boot2.5开发中的一些常用知识点，以[训练](https://github.com/Bezhuang/LearnCS/tree/main/Java中级训练营)和熟悉特性为主。

<!--more-->

![](https://ucc-image.oss-cn-beijing.aliyuncs.com/credential/22/87e768f5aca640b3ad57813564f6cdb8.png)

### Java Spring企业级开发平台

- 最初来自2002年Rod Jahnson所著书《Expert One-on-One J2EE Design and Development》,最早名字为：Interface21
- 2003年6月诞生轻量级Java企业级开发工具类库[Spring](http://www.springsource.org)，现在已经发展成为包括开发工具、MVC框架、类库、微服务架构的完整平台（体系）
- 一个轻量级控制反转（IoC）和面向切面（AOP）的容器框架，一个分层的JavaSE/EE full-stack（一站式）轻量级开源框架
- Spring提供IOC、AOP、日志、安全、加密等工具类库，用于解决企业应用开发的复杂性
- Spring Framework：Spring工具类框架，其他Spring项目如Spring Boot也依赖于此框架
- Spring MVC：Java MVC网站开发框架
- Spring Boot：简化Spring应用开发。简化配置文件，使用嵌入式web服务器，含有诸多开箱即用微服务功能，可以和Spring Cloud联合部署
- Spring Cloud：微服务框架，为开发者提供分布式系统的配置管理、服务发现、路器、智能路由、微代理、控制总线等开发工具包
- Spring Data：数据访问框架，封装了很多种数据及数据库的访问相关技术，包括JDBC、Redis、MongoDB、Neo4J等
- Spring REST Shell：可以调用Rest服务的命令行工具，命令行操作Rest服务

### Spring Boot发展历史

- 联合创始人：Rod Jahnson、Juergen Hoeller、Yann Caroff
- Thomas Risberg&Spring JDBC、Keith Donald&Spring MVC、Adrain Coyler&Spring AOP
- 2014年4月开始发布Spring Boot2.0的1.0.0版本
- 配合模板和框架来简化Spring项目开发，轻松创建具有最小或零配置的独立应用程序的方式，它提供默认的代码和注释配置，只需要非常少的配置就能进行Java Spring应用开发
- Spring Boot = Auto-Dependency Resolution + Auto-Configuration ＋Management Endpoints + Embedded HTTP Servers (Tomcat, Jetty)
- Spring Boot 2.5.0加入startup endpoint支持GET请求、info endpoint安全改进、支持Java16等新特性

### 实战Spring Boot 2.4

- [在线创建Spring项目](start.spring.io)

- Eclipse需要添加Spring Tools 4插件，IDEA自带，使用 `start.alibaba.com` 源

- Spring Web（Tomcat）：http://localhost:8080/hello

  ```java
  @RestController
  @SpringBootApplication
  public class JavaSpringBoot01HelloWorldDemoApplication {
      public static void main(String[] args){SpringApplication.run(JavaSpringBoot01HelloWorldDemoApplication.class, args);}    
      @RequestMapping("/hello")  //公开http接口，默认端口8080，可在application.properties中修改
      public String hello() {    
      	String s = "Hello Spring Boot";
      	return s;}
  }
  ```

  