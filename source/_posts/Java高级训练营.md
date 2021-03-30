---
title: 2021阿里Java训练营第三期
date: 2021-03-26
updated: 2021-03-27
tags: [Java]
group: going
categories: 代码人生
references:
  - title: Spring Cloud微服务架构设计与开发实战
    url: https://developer.aliyun.com/learning/course/60
---

>本期训练营是阿里云开发者社区Java训练营的第3期，主要基于最流行的Java Spring Cloud, 结合阿里巴巴淘宝微服务案例，实战模拟淘宝Order微服务，实战演练微服务开发，扩展学习Spring Cloud Alibaba新框架，本篇日志主要记录5天直播Spring cloud微服务开发课中的一些知识点，附[实战代码](https://github.com/Bezhuang/LearnCS/tree/main/Java高级训练营)。

<!--more-->

![](https://ucc-image.oss-cn-beijing.aliyuncs.com/credential/27/9afb0bbd19d049869c5533dd7110d0bd.png)

### 微服务架构设计与实践

- 架构演化之路：单体 -> 分层 -> 分布式 -> SOA -> 微服务

- 微服务架构Microservice
  - 一种新型的软件架构风格，把单个巨型服务应用分解为多个独立微小的服务程序，每个小服务程序运行在独立的进程中
  - 服务与服务之间通过轻量协议通信，通信机制互相协作、互相配合，从而为终端用户提供业务价值
  - 每个小服务可以采用不同的语言、框架、工具独立开发、测试、部署、运维
  - 单独部署、单独伸缩，去中心化：数据中心、管理中心，敏捷性、灵活性、需求变化，更加高效的软件架构模式
- 微服务优缺点 
  - 快速响应需求变化，易于替换，独立进程、开发、部署、测试，无依赖
  - 高度解耦，基于功能进行组织，独立技术栈、服务可以使用不同的语言、系统、平台
  - 协议简单，通信使用语言中立的协议，通常是http
  - 架构复杂，多服务运维难度大，系统部署依赖和服务间通信成本高
- 敏捷开发、敏捷运维DevOps
- 微服务典型应用场景：淘宝、支付宝、微信、微博、IOT、游戏、导航

### Spring Cloud微服务注册与发现

- 服务注册与发现：Service Registry and Discovery
  - 大规模微服务集群架构，拥有许多服务实例，客户端要找到自己调用的服务
  - 新服务上线或莫格服务宕机，下线时可以实时监控服务的状态
- Spring Cloud Eureka服务发现与注册
  - Eureka：注册中心，服务发现模块，是Nexflix的核心（开源的项目），竞争对手：ZooKeeper
  - 一个基于REST的中心服务，管理服务，实现云端的服务注册和服务发现
  - Eureka组件组成：Eureka服务器和Eureka客户端
  - Spring Cloud Nextflix提供简化开发模板，直接使用Spring Boot创建项目，添加`@EnableEurekaServer`开发注册服务中心

- Spring Eureka注册中心实战

  - 创建Spring Eureka服务注册中心项目，添加`@EnableEurekaServer`，将Spring Boot应用改造成Eureka服务注册中心，`application.properties`增加配置，打包项目并运行测试

  - 参考https://spring.io/guides/gs/service-registeration-and-discovery

  ```properties
  spring.application.name=EurekaServer
  server.port=8761
  eureka.client.serviceUrl.defaultZone=http://localhost:8761/eureka/
  #\u6CE8\u518C\u548C\u67E5\u8BE2\u63A7\u5236
  eureka.client.fetch-registry=false
  eureka.client.register-with-eureka=false
  ```

### Spring Cloud2020微服务架构

- Spring Cloud Netflix Greenwich以上（2.1.X）版本相对成熟，企业使用多，容易落地架构
- Spring Cloud Alibaba相对成熟，部分组件可以替换
- 新版本2020（aka Ilford）可以作为拓展学习，基于Spring Boot2.4及以上版本，Bootstrap默认禁用，慎重选择新版本

### 开发Spring Cloud微服务API

- 配置Eureka客户端项目

  ```properties
  spring.application.name=order-microservice
  server.port=8001
  eureka.client.serviceUrl.defaultZone=http://localhost:8761/eureka/
  eureka.client.fetch-registry=false
  eureka.client.register-with-eureka=true
  ```

  

