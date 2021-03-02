---
title: MySQL--- DDL
date: 2020-10-24 23:05:19
tags: 
  - skill
  - 
categories: 学习笔记
---

# DDL语句 数据定义语言
## 库和表的管理
库的管理：

	一、创建库
	create database 库名
    
	二、删除库
	drop database 库名
表的管理：  

    1.创建表
	CREATE TABLE IF NOT EXISTS stuinfo(
		stuId INT,
		stuName VARCHAR(20),
		gender CHAR,
		bornDate DATETIME
	);
	DESC studentinfo;

	2.修改表 alter
	语法：ALTER TABLE 表名 ADD|MODIFY|DROP|CHANGE COLUMN 字段名 【字段类型】;
	
	2.1 修改字段名
	ALTER TABLE studentinfo CHANGE  COLUMN sex gender CHAR;
	
	2.2 修改表名
	ALTER TABLE stuinfo RENAME [TO]  studentinfo;

	2.3修改字段类型和列级约束
	ALTER TABLE studentinfo MODIFY COLUMN borndate DATE ;
	
	2.4 添加字段
	ALTER TABLE studentinfo ADD COLUMN email VARCHAR(20) first;

	2.5 删除字段
	ALTER TABLE studentinfo DROP COLUMN email;
	
	3.删除表
	DROP TABLE [IF EXISTS] studentinfo;


## 常见类型

	整型：
		
	小数：
		浮点型
		定点型
	字符型：
	日期型：
	Blob类型：



## 常见约束

	NOT NULL
	DEFAULT
	UNIQUE
	CHECK
	PRIMARY KEY
	FOREIGN KEY

# 数据库事务
## 含义
	通过一组逻辑操作单元（一组DML——sql语句），将数据从一种状态切换到另外一种状态

## 特点
	（ACID）
	原子性：要么都执行，要么都回滚
	一致性：保证数据的状态操作前和操作后保持一致
	隔离性：多个事务同时操作相同数据库的同一个数据时，一个事务的执行不受另外一个事务的干扰
	持久性：一个事务一旦提交，则数据将持久化到本地，除非其他事务对其进行修改

相关步骤：

	1、开启事务
	2、编写事务的一组逻辑操作单元（多条sql语句）
	3、提交事务或回滚事务

## 事务的分类：

隐式事务，没有明显的开启和结束事务的标志

	比如
	insert、update、delete语句本身就是一个事务


显式事务，具有明显的开启和结束事务的标志

		1、开启事务
		取消自动提交事务的功能
		
		2、编写事务的一组逻辑操作单元（多条sql语句）
		insert
		update
		delete
		
		3、提交事务或回滚事务  

## 使用到的关键字

	set autocommit=0;
	start transaction;
	commit;
	rollback;
	
	savepoint  断点
	commit to 断点
	rollback to 断点


## 事务的隔离级别:

事务并发问题如何发生？

	当多个事务同时操作同一个数据库的相同数据时
事务的并发问题有哪些？

	脏读：一个事务读取到了另外一个事务未提交的数据
	不可重复读：同一个事务中，多次读取到的数据不一致
	幻读：一个事务读取数据时，另外一个事务进行更新，导致第一个事务读取到了没有更新的数据

如何避免事务的并发问题？

	通过设置事务的隔离级别
	1、READ UNCOMMITTED
	2、READ COMMITTED 可以避免脏读
	3、REPEATABLE READ 可以避免脏读、不可重复读和一部分幻读
	4、SERIALIZABLE可以避免脏读、不可重复读和幻读
	
设置隔离级别：

	set session|global  transaction isolation level 隔离级别名;
查看隔离级别：

	select @@tx_isolation;


# 视图
含义：理解成一张虚拟的表

## 视图和表的区别：
	
		  使用方式   	占用物理空间
	
	视图	完全相同    不占用，仅仅保存的是sql逻辑
	
	表	   完全相同	    占用

## 视图的好处：

	1、sql语句提高重用性，效率高
	2、和表实现了分离，提高了安全性

## 视图的创建
	语法：
	CREATE VIEW  视图名
	AS
	查询语句;

## 视图的增删改查
	1、查看视图的数据 
	
	SELECT * FROM my_v4;
	SELECT * FROM my_v1 WHERE last_name='Partners';
	
	2、插入视图的数据
	INSERT INTO my_v4(last_name,department_id) VALUES('虚竹',90);
	
	3、修改视图的数据
	
	UPDATE my_v4 SET last_name ='梦姑' WHERE last_name='虚竹';
	
	
	4、删除视图的数据
	DELETE FROM my_v4;

## 某些视图不能更新
	包含以下关键字的sql语句：分组函数、distinct、group  by、having、union或者union all
	常量视图
	Select中包含子查询
	join
	from一个不能更新的视图
	where子句的子查询引用了from子句中的表
## 视图逻辑的更新
	#方式一：
	CREATE OR REPLACE VIEW test_v7
	AS
	SELECT last_name FROM employees
	WHERE employee_id>100;
	
	#方式二:
	ALTER VIEW test_v7
	AS
	SELECT employee_id FROM employees;
	
	SELECT * FROM test_v7;
### 视图的删除
	DROP VIEW test_v1,test_v2,test_v3;
### 视图结构的查看	
	DESC test_v7;
	SHOW CREATE VIEW test_v7;