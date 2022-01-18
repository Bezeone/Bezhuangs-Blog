---
title: JavaWeb 基础总结（上）
date: 2021-11-01
updated: 2022-01-20
tags: [Java, JavaWeb, MySQL, Maven]
password: 990312
categories: 编程与开发
---

> JavaWeb 是整个 Web 开发的基础课程，分为三部分内容：数据库、前端、web核心，可以为后期学习分布式、微服务打下坚实的基础。我选择的课程为[Java web 从入门到企业实战教程](https://www.bilibili.com/video/BV1Qf4y1T7Hx)，以下为所记课堂笔记第一部分，包含数据库部分学习内容。其他部分笔记详见[JavaWeb 基础总结（中）](/JavaWeb基础-中)和[JavaWeb 基础总结（下）](/JavaWeb基础-下)，可供参考。

<!--more-->

### JavaWeb 整体介绍

- JavaWeb 是用 Java 技术来解决相关 web 互联网领域的技术栈
  - 网页：展现数据
  - 数据库：存储和管理数据
  - JavaWeb 程序：逻辑处理

### MySQL 基础

#### SQL简介

* 英文：Structured Query Language，简称 SQL
* 结构化查询语言，一门操作关系型数据库的编程语言
* 定义操作所有关系型数据库的统一标准
* 对于同一个需求，每一种数据库操作的方式可能会存在一些不一样的地方

#### 通用语法

* SQL 语句可以单行或多行书写，以分号结尾。

* MySQL 数据库的 SQL 语句不区分大小写，关键字建议使用大写。

* 注释

  * 单行注释: `-- 注释内容` 或 `#注释内容`

  * 多行注释: `/* 注释 */`

#### SQL分类

* DDL (Data Definition Language) ： 数据定义语言，用来定义数据库对象：数据库，表，列等

* DML (Data Manipulation Language) 数据操作语言，用来对数据库中表的数据进行增删改

* DQL (Data Query Language) 数据查询语言，用来查询数据库中表的记录（数据）

* DCL (Data Control Language) 数据控制语言，用来定义数据库的访问权限和安全级别，及创建用户


#### DDL：操作数据库

-  查询所有的数据库

```sql
SHOW DATABASES;
```

* 创建数据库（先判断，如果不存在则创建）

```sql
CREATE DATABASE IF NOT EXISTS 数据库名称;
```

* 删除数据库（先判断，如果存在则删除）

```sql
DROP DATABASE IF EXISTS 数据库名称;
```

* 使用数据库

```sql
USE 数据库名称;
```

* 查看当前使用的数据库

```sql
SELECT DATABASE();
```

#### DDL：操作表

* 查询当前数据库下所有表名称

```sql
SHOW TABLES;
```

* 查询表结构

```sql
DESC 表名称;
```

* 创建表

```sql
create table tb_user (
	id int,
    username varchar(20),
    password varchar(32)  -- 最后一行末尾，不能加逗号
);
```

* 删除表（先判断表是否存在）

```sql
DROP TABLE IF EXISTS 表名;
```

* 修改表名

```sql
ALTER TABLE 表名 RENAME TO 新的表名;
```

* 添加一列

```sql
ALTER TABLE 表名 ADD 列名 数据类型;

-- 给stu表添加一列address，该字段类型是varchar(50)
alter table stu add address varchar(50);
```

* 修改数据类型

```sql
ALTER TABLE 表名 MODIFY 列名 新数据类型;

-- 将stu表中的address字段的类型改为 char(50)
alter table stu modify address char(50);
```

* 修改列名和数据类型

```sql
ALTER TABLE 表名 CHANGE 列名 新列名 新数据类型;

-- 将stu表中的address字段名改为 addr，类型改为varchar(50)
alter table stu change address addr varchar(50);
```

* 删除列

```sql
ALTER TABLE 表名 DROP 列名;
```

#### SQL 的数据类型

* 数值

  ```sql
  tinyint : 小整数型，占一个字节
  int	： 大整数类型，占四个字节
  	eg ： age int
  double ： 浮点类型
  	使用格式： 字段名 double(总长度,小数点后保留的位数)
  	eg ： score double(5,2)   
  ```

* 日期

  ```sql
  date ： 日期值。只包含年月日
  	eg ：birthday date ： 
  datetime ： 混合日期和时间值。包含年月日时分秒
  ```

* 字符串

  ```sql
  char ： 定长字符串。
  	优点：存储性能高
  	缺点：浪费空间
  	eg ： name char(10)  如果存储的数据字符个数不足10个，也会占10个的空间
  varchar ： 变长字符串。
  	优点：节约空间
  	缺点：存储性能底
  	eg ： name varchar(10) 如果存储的数据字符个数不足10个，那就数据字符个数是几就占几个的空间	
  ```

#### DML

* 查询所有数据

```sql
SELECT * FROM 表名;
```

* 给指定列添加数据

```sql
INSERT INTO 表名(列名1,列名2,…) VALUES(值1,值2,…);
```

* 给全部列添加数据

```sql
INSERT INTO 表名 VALUES(值1,值2,…);
```

* 批量添加数据

```sql
INSERT INTO 表名(列名1,列名2,…) VALUES(值1,值2,…),(值1,值2,…),(值1,值2,…)…;
INSERT INTO 表名 VALUES(值1,值2,…),(值1,值2,…),(值1,值2,…)…;
```

* 修改表数据

```sql
UPDATE 表名 SET 列名1=值1,列名2=值2,… [WHERE 条件] ;
-- 修改语句中如果不加条件，则将所有数据都修改！
```

* 删除数据

```sql
DELETE FROM 表名 [WHERE 条件] ;
```

* 删除表中所有的数据

```sql
DELETE FROM 表名;
```

#### DQL

* 查询多个字段

```sql
SELECT 字段列表 FROM 表名;
SELECT * FROM 表名; -- 查询所有数据
```

* 去除重复记录

```sql
SELECT DISTINCT 字段列表 FROM 表名;
```

* 起别名

```sql
SELECT 字段列表 AS: 别名 FROM 表名; -- AS 也可以省略
```

- 条件查询


```sql
SELECT 字段列表 FROM 表名 WHERE 条件列表;
```

- 模糊查询
  - 使用 `LIKE` 关键字，可以使用通配符进行占位
  - `_` ：代表单个任意字符
  - `%` ：代表任意个数字符

```sql
select * from stu where name like '马%';  -- 查询姓'马'的学员信息

select * from stu where name like '_花%';  -- 查询第二个字是'花'的学员信息 

select * from stu where name like '%德%';  -- 查询名字中包含 '德' 的学员信息
```

- 排序查询

```sql
SELECT 字段列表 FROM 表名 ORDER BY 排序字段名1 [排序方式1],排序字段名2 [排序方式2] …;
/*
排序方式有两种，分别是：
ASC ： 升序排列（默认值）
DESC ： 降序排列
如果有多个排序条件，当前边的条件值一样时，才会根据第二条件进行排序
*/
```

- 聚合函数
  - 将一列数据作为一个整体，进行纵向计算


| 函数名        | 功能                             |
| ------------- | -------------------------------- |
| `count(列名)` | 统计数量（一般选用不为null的列） |
| `max(列名)`   | 最大值                           |
| `min(列名)`   | 最小值                           |
| `sum(列名)`   | 求和                             |
| `avg(列名)`   | 平均值                           |

```sql
SELECT 聚合函数名(列名) FROM 表;
-- null 值不参与所有聚合函数运算
```

- 分组查询

```sql
SELECT 字段列表 FROM 表名 [WHERE 分组前条件限定] GROUP BY 分组字段名 [HAVING 分组后条件过滤];
-- 分组之后，查询的字段为聚合函数和分组字段，查询其他字段无任何意义
```

- where 和 having 区别：

  * 执行时机不一样：`where` 是分组之前进行限定，不满足 `where` 条件，则不参与分组，而 `having` 是分组之后对结果进行过滤。


  * 可判断的条件不一样：`where` 不能对聚合函数进行判断，`having` 可以


- 分页查询

```sql
SELECT 字段列表 FROM 表名 LIMIT  起始索引 , 查询条目数;
-- 起始索引是从0开始
```

- 起始索引计算公式：

```sql
起始索引 = (当前页码 - 1) * 每页显示的条数
```

### MySQL 进阶

#### 约束

* 约束是作用于表中列上的规则，用于限制加入表的数据

* 约束的存在保证了数据库中数据的正确性、有效性和完整性

* 约束的分类

  - 非空约束：关键字是 `NOT NULL`，保证列中所有的数据不能有null值。


  - 唯一约束：关键字是 `UNIQUE`，保证列中所有数据各不相同


  - 主键约束： 关键字是 `PRIMARY KEY`，主键是一行数据的唯一标识，要求非空且唯一


  - 检查约束： 关键字是 `CHECK`，保证列中的值满足某一条件（MySQL不支持检查约束）


  - 默认约束： 关键字是  `DEFAULT`，保存数据时，未指定值则采用默认值
  - 外键约束： 关键字是 `FOREIGN KEY`，外键用来让两个表的数据之间建立链接，保证数据的一致性和完整性

* 非空约束

  * 用于保证列中所有数据不能有NULL值

  * 添加约束

    ```sql
    -- 创建表时添加非空约束
    CREATE TABLE 表名(
       列名 数据类型 NOT NULL,
       …
    ); 
    ```
    
    ```sql
    -- 建完表后添加非空约束
    ALTER TABLE 表名 MODIFY 字段名 数据类型 NOT NULL;
    ```
  
  
    * 删除约束
  
      ```sql
      ALTER TABLE 表名 MODIFY 字段名 数据类型;
      ```
  

- 唯一约束

  * 用于保证列中所有数据各不相同
  
  
    * 添加约束
  
      ```sql
      -- 创建表时添加唯一约束
      CREATE TABLE 表名(
         列名 数据类型 UNIQUE [AUTO_INCREMENT],
         -- AUTO_INCREMENT: 当不指定值时自动增长
         …
      ); 
      CREATE TABLE 表名(
         列名 数据类型,
         …
         [CONSTRAINT] [约束名称] UNIQUE(列名)
      ); 
      ```
  
      ```sql
      -- 建完表后添加唯一约束
      ALTER TABLE 表名 MODIFY 字段名 数据类型 UNIQUE;
      ```
  
  
    * 删除约束
  
      ```sql
      ALTER TABLE 表名 DROP INDEX 字段名;
      ```
  
- 主键约束

  - 主键是一行数据的唯一标识，要求非空且唯一
  - 一张表只能有一个主键

  * 添加约束

    ```sql
    -- 创建表时添加主键约束
    CREATE TABLE 表名(
       列名 数据类型 PRIMARY KEY [AUTO_INCREMENT],
       …
    ); 
    CREATE TABLE 表名(
       列名 数据类型,
       [CONSTRAINT] [约束名称] PRIMARY KEY(列名)
    ); 
    
    ```

    ```sql
    -- 建完表后添加主键约束
    ALTER TABLE 表名 ADD PRIMARY KEY(字段名);
    ```


  * 删除约束

    ```sql
    ALTER TABLE 表名 DROP PRIMARY KEY;
    ```

- 默认约束

  * 保存数据时，未指定值则采用默认值

  * 添加约束

    ```sql
    -- 创建表时添加默认约束
    CREATE TABLE 表名(
       列名 数据类型 DEFAULT 默认值,
       …
    ); 
    ```

    ```sql
    -- 建完表后添加默认约束
    ALTER TABLE 表名 ALTER 列名 SET DEFAULT 默认值;
    ```

  * 删除约束

    ```sql
    ALTER TABLE 表名 ALTER 列名 DROP DEFAULT;
    ```


- 默认约束只有在不给值时才会采用默认值。如果给了null，那值就是null值


#### 外键约束

- 外键用来让两个表的数据之间建立链接，保证数据的一致性和完整性

* 添加外键约束

```sql
-- 创建表时添加外键约束
CREATE TABLE 表名(
   列名 数据类型,
   …
   [CONSTRAINT] [外键名称] FOREIGN KEY(外键列名) REFERENCES 主表(主表列名) 
); 
```

```sql
-- 建完表后添加外键约束
ALTER TABLE 表名 ADD CONSTRAINT 外键名称 FOREIGN KEY (外键字段名称) REFERENCES 主表名称(主表列名称);
```

* 删除外键约束

```sql
ALTER TABLE 表名 DROP FOREIGN KEY 外键名称;
```

- 添加数据


```sql
-- 添加 2 个部门
insert into dept(dep_name,addr) values
('研发部','广州'),('销售部', '深圳');

-- 添加员工,dep_id 表示员工所在的部门
INSERT INTO emp (NAME, age, dep_id) VALUES 
('张三', 20, 1),
('李四', 20, 1),
('王五', 20, 1),
```

删除外键

```sql
alter table emp drop FOREIGN key fk_emp_dept;
```

重新添加外键

```sql
alter table emp add CONSTRAINT fk_emp_dept FOREIGN key(dep_id) REFERENCES dept(id);
```

#### 数据库设计

* 数据库设计概念

  * 数据库设计就是根据业务系统的具体需求，结合我们所选用的DBMS，为这个业务系统构造出最优的数据存储模型
  * 建立数据库中的表结构以及表与表之间的关联关系的过程
  * 有哪些表？表里有哪些字段？表和表之间有什么关系？
* 数据库设计的步骤

  * 需求分析（数据是什么? 数据具有哪些属性? 数据与属性的特点是什么）

  * 逻辑分析（通过ER图对数据库进行逻辑建模，不需要考虑我们所选用的数据库管理系统）

  * 物理设计（根据数据库自身的特点把逻辑设计转换为物理设计）

  * 维护设计（1.对新的需求进行建表；2.表优化）
* 表关系

  * 一对一（如：用户 和 用户详情）：一对一关系多用于表拆分，将一个实体中经常使用的字段放一张表，不经常使用的字段放另一张表，用于提升查询性能

  * 一对多（如：部门 和 员工）：一个部门对应多个员工，一个员工对应一个部门
  
  * 多对多（如：商品 和 订单）：一个商品对应多个订单，一个订单包含多个商品
  

- 表关系（一对多）

  - 实现方式：在多的一方建立外键，指向一的一方的主键


  - 以 `员工表` 和 `部门表` 举例：在员工表中添加一列（dep_id），指向于部门表的主键（id）


```sql
-- 删除表
DROP TABLE IF EXISTS tb_emp;
DROP TABLE IF EXISTS tb_dept;

-- 部门表
CREATE TABLE tb_dept(
    id int primary key auto_increment,
    dep_name varchar(20),
    addr varchar(20)
);
-- 员工表 
CREATE TABLE tb_emp(
    id int primary key auto_increment,
    name varchar(20),
    age int,
    dep_id int,

    -- 添加外键 dep_id,关联 dept 表的id主键
    CONSTRAINT fk_emp_dept FOREIGN KEY(dep_id) REFERENCES tb_dept(id)	
);
```

- 表关系（多对多）

  - 建立第三张中间表，中间表至少包含两个外键，分别关联两方主键

  * 以 `订单表` 和 `商品表` 举例：订单表和商品表都属于多的一方，此时需要创建一个中间表，在中间表中添加订单表的外键和商品表的外键指向两张表的主键：

  ```sql
    -- 删除表
    DROP TABLE IF EXISTS tb_order_goods;
    DROP TABLE IF EXISTS tb_order;
    DROP TABLE IF EXISTS tb_goods;
    
    -- 订单表
    CREATE TABLE tb_order(
    id int primary key auto_increment,
    payment double(10,2),
    payment_type TINYINT,
    status TINYINT
    );
    
    -- 商品表
    CREATE TABLE tb_goods(
    id int primary key auto_increment,
    title varchar(100),
    price double(10,2)
    );
    
    -- 订单商品中间表
    CREATE TABLE tb_order_goods(
    id int primary key auto_increment,
    order_id int,
    goods_id int,
    count int
    );
    
    -- 建完表后，添加外键
    alter table tb_order_goods add CONSTRAINT fk_order_id FOREIGN key(order_id) REFERENCES tb_order(id);
    alter table tb_order_goods add CONSTRAINT fk_goods_id FOREIGN key(goods_id) REFERENCES tb_goods(id);
  ```

- 表关系（一对一）

  * 在任意一方加入外键，关联另一方主键，并且设置外键为唯一（`UNIQUE`）


  * 以 `用户表` 举例：在真正使用过程中发现 id、photo、nickname、age、gender 字段比较常用，此时就可以将这张表查分成两张表

```sql
create table tb_user_desc (
	id int primary key auto_increment,
	city varchar(20),
	edu varchar(10),
	income int,
	status char(2),
	des varchar(100)
);

create table tb_user (
	id int primary key auto_increment,
	photo varchar(100),
	nickname varchar(50),
	age int,
	gender char(1),
	desc_id int unique,
	-- 添加外键
	CONSTRAINT fk_user_desc FOREIGN KEY(desc_id) REFERENCES tb_user_desc(id)	
);
```

#### 多表查询

- 多表查询顾名思义就是从多张表中一次性的查询出我们想要的数据


```sql
DROP TABLE IF EXISTS emp;
DROP TABLE IF EXISTS dept;

# 创建部门表
	CREATE TABLE dept(
        did INT PRIMARY KEY AUTO_INCREMENT,
        dname VARCHAR(20)
    );

	# 创建员工表
	CREATE TABLE emp (
        id INT PRIMARY KEY AUTO_INCREMENT,
        NAME VARCHAR(10),
        gender CHAR(1), -- 性别
        salary DOUBLE, -- 工资
        join_date DATE, -- 入职日期
        dep_id INT,
        FOREIGN KEY (dep_id) REFERENCES dept(did) -- 外键，关联部门表(部门表的主键)
    );
	-- 添加部门数据
	INSERT INTO dept (dNAME) VALUES ('研发部'),('市场部'),('财务部'),('销售部');
	-- 添加员工数据
	INSERT INTO emp(NAME,gender,salary,join_date,dep_id) VALUES
	('孙悟空','男',7200,'2013-02-24',1),
	('猪八戒','男',3600,'2010-12-02',2),
	('唐僧','男',9000,'2008-08-08',2),
	('白骨精','女',5000,'2015-10-07',3),
	('蜘蛛精','女',4500,'2011-03-14',1),
	('小白龙','男',2500,'2011-02-14',null);	
```

- 执行下面的多表查询语句


```sql
select * from emp , dept;  -- 从emp和dept表中查询所有的字段数据
```

- 通过限制员工表中的 `dep_id` 字段的值和部门表 `did` 字段的值相等来消除无效的数据，


```sql
select * from emp , dept where emp.dep_id = dept.did;
```

* 连接查询 

  * 内连接查询 ：相当于查询AB交集数据
  * 外连接查询
    * 左外连接查询 ：相当于查询A表所有数据和交集部门数据
    * 右外连接查询 ： 相当于查询B表所有数据和交集部分数据
  * 子查询
  

- 内连接查询

```sql
-- 隐式内连接
SELECT 字段列表 FROM 表1,表2… WHERE 条件;

-- 显示内连接
SELECT 字段列表 FROM 表1 [INNER] JOIN 表2 ON 条件;
```

* 隐式内连接

  ```sql
  SELECT * FROM emp, dept WHERE emp.dep_id = dept.did;
  ```

  * 查询 emp 的 name， gender，dept 表的 dname


  ```sql
  SELECT
  	t1. NAME,
  	t1.gender,
  	t2.dname
  FROM
  	emp t1,
  	dept t2
  WHERE
  	t1.dep_id = t2.did;
  ```

* 显式内连接

  ```sql
  select * from emp inner join dept on emp.dep_id = dept.did;
  -- 上面语句中的inner可以省略，可以书写为如下语句
  select * from emp  join dept on emp.dep_id = dept.did;
  ```

- 外连接查询

```sql
-- 左外连接：相当于查询A表所有数据和交集部分数据
SELECT 字段列表 FROM 表1 LEFT [OUTER] JOIN 表2 ON 条件;

-- 右外连接：相当于查询B表所有数据和交集部分数据
SELECT 字段列表 FROM 表1 RIGHT [OUTER] JOIN 表2 ON 条件;
```

* 查询emp表所有数据和对应的部门信息（左外连接）

  ```sql
  select * from emp left join dept on emp.dep_id = dept.did;
  -- 结果显示查询到了左表（emp）中所有的数据及两张表能关联的数据
  ```
  
* 查询dept表所有数据和对应的员工信息（右外连接）

  ```sql
  select * from emp right join dept on emp.dep_id = dept.did;
  -- 结果显示查询到了右表（dept）中所有的数据及两张表能关联的数据
  ```
  
  。要查询出部门表中所有的数据，也可以通过左外连接实现，只需要将两个表的位置进行互换：
  
  ```sql
  select * from dept left join emp on emp.dep_id = dept.did;
  ```
  

- 子查询

  - 查询中嵌套查询，称嵌套查询为子查询


  * 子查询根据查询结果不同，作用不同

  * 子查询语句结果是单行单列，子查询语句作为条件值，使用 =  !=  >  <  等进行条件判断
  * 子查询语句结果是多行单列，子查询语句作为条件值，使用 in 等关键字进行条件判断
  * 子查询语句结果是多行多列，子查询语句作为虚拟表

  * 查询 '财务部' 和 '市场部' 所有的员工信息

    ```sql
    -- 查询 '财务部' 或者 '市场部' 所有的员工的部门did
    select did from dept where dname = '财务部' or dname = '市场部';
    
    select * from emp where dep_id in (select did from dept where dname = '财务部' or dname = '市场部');
    ```


  * 查询入职日期是 '2011-11-11' 之后的员工信息和部门信息

    ```sql
    -- 查询入职日期是 '2011-11-11' 之后的员工信息
    select * from emp where join_date > '2011-11-11' ;
    -- 将上面语句的结果作为虚拟表和dept表进行内连接查询
    select * from (select * from emp where join_date > '2011-11-11' ) t1, dept where t1.dep_id = dept.did;
    ```

### 事务

#### 概述

- 数据库的事务（Transaction）是一种机制、一个操作序列，包含了一组数据库操作命令
- 事务把所有的命令作为一个整体一起向系统提交或撤销操作请求，即这一组数据库命令要么同时成功，要么同时失败
- 事务是一个不可分割的工作逻辑单元

#### 语法

* 开启事务

  ```sql
  START TRANSACTION;
  或者  
  BEGIN;
  ```

* 提交事务

  ```sql
  commit;
  ```

* 回滚事务

  ```sql
  rollback;
  ```


####  代码验证

* 环境准备

  ```sql
  DROP TABLE IF EXISTS account;
  
  -- 创建账户表
  CREATE TABLE account(
  	id int PRIMARY KEY auto_increment,
  	name varchar(10),
  	money double(10,2)
  );
  
  -- 添加数据
  INSERT INTO account(name,money) values('张三',1000),('李四',1000);
  ```

* 不加事务演示问题

  ```sql
  -- 转账操作
  -- 1. 查询李四账户金额是否大于500
  
  -- 2. 李四账户 -500
  UPDATE account set money = money - 500 where name = '李四';
  
  出现异常了...  -- 此处不是注释，在整体执行时会出问题，后面的sql则不执行
  -- 3. 张三账户 +500
  UPDATE account set money = money + 500 where name = '张三';
  ```

* 添加事务 sql

  ```sql
  -- 开启事务
  BEGIN;
  -- 转账操作
  -- 1. 查询李四账户金额是否大于500
  
  -- 2. 李四账户 -500
  UPDATE account set money = money - 500 where name = '李四';
  
  出现异常了...  -- 此处不是注释，在整体执行时会出问题，后面的sql则不执行
  -- 3. 张三账户 +500
  UPDATE account set money = money + 500 where name = '张三';
  
  -- 提交事务
  COMMIT;
  
  -- 回滚事务
  ROLLBACK;
  ```

  - 上面sql中的执行成功进选择执行提交事务，而出现问题则执行回滚事务的语句，以后我们肯定不可能这样操作，而是在java中进行操作，在java中可以抓取异常，没出现异常提交事务，出现异常回滚事务

#### 事务的四大特征

* 原子性（Atomicity）: 事务是不可分割的最小操作单位，要么同时成功，要么同时失败
* 一致性（Consistency） :事务完成时，必须使所有的数据都保持一致状态
* 隔离性（Isolation） :多个事务之间，操作的可见性
* 持久性（Durability） :事务一旦提交或回滚，它对数据库中的数据的改变就是永久的
* mysql中事务是自动提交的，也就是说我们不添加事务执行sql语句，语句执行完毕会自动的提交事务
  * 可以通过下面语句查询默认提交方式：
 ```java
SELECT @@autocommit;
 ```

-  查询到的结果是1 则表示自动提交，结果是0表示手动提交。当然也可以通过下面语句修改提交方式


 ```sql
set @@autocommit = 0;
 ```



# 未完待续
