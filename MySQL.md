# MySQL

### mysql	概述

|      名称      |                             全称                             |                简称                |
| :------------: | :----------------------------------------------------------: | :--------------------------------: |
|     数据库     |            存储数据的仓库，数据是有组织的进行存储            |           DataBase（DB）           |
| 数据库管理系统 |                    操作和管理数据库的软件                    | DataBase Management System（DBMS） |
|      SQL       | 操作关系型数据库的编程语言，定义了一套操作关系型数据库的统一标准 |  Structured Query Language（SQL）  |

关系型数据库（RDBMS）：

概念：建立在关系模型基础上，由多张相互连接的二维表组成的数据库。

![image-20221029210437200](C:\Users\86131\AppData\Roaming\Typora\typora-user-images\image-20221029210437200.png)

特点：

1. 使用表存储数据，格式统一，便于维护
2. 使用SQL语言操作，标准统一，使用方便

**总结：**

1. 数据库

   存储数据的仓库。

2. 数据库管理系统

   操作和管理数据库的大型软件

3. SQL

   操作关系型数据库的编程语言，是一套标准

### **SQL**

**SQL通用语法**

- SQL语句可以单行或多行书写，以分号结尾
- mysql数据库的sql语句不区分大小写，关键字建议使用大写
- 注释：
  - 单行注释：# 注释类容
  - 多行注释：/* 注释类容 */

**SQL分类**

| 分类 |            全称            |                          说明                          |
| :--: | :------------------------: | :----------------------------------------------------: |
| DDL  |  Data Definition Language  |  数据定义语言，用来定义数据库对象（数据库，表，字段）  |
| DML  | Data Manipulation Language |     数据操作语言，用来对数据库中表的数据进行增删改     |
| DQL  |    Data Query Language     |         数据查询语言，用来查询数据库中表的记录         |
| DCL  |   Data Control Language    | 数据控制语言，用来创建数据库用户、控制数据库的访问权限 |

**SQL命令**

1. 启动与停止

   ```sql
   # 启动：
   net start mysql
   
   # 停止：
   net stop mysql
   ```

2. 客户端连接

   ```sql
   mysql [-h 127.0.0.1] [-P 3306] -u root -p
   ```

3. DDL-数据库操作

   ```sql
   # 查询
   	# 查询所有数据库
   	show databases;
   	
   	# 查询当前数据库
   	select database();
   	
   # 创建数据库
   create database [if not exists] database_name [default charset 字符集] [collate 排序规则];
   	
   # 删除数据库
   drop database [if exists] database_name
   
   # 使用数据库
   use database_name;
   ```
   
4. DDL-表操作

   ```sql
   # 创建表
   create table table_name (
   	字段1 type [comment 字段注释],
   	字段2 type [comment 字段注释],
   	字段3 type [comment 字段注释],
   	...
   ) [comment 表注释];
   
   # 查询当前数据库中所有表
   show tables;
   
   # 查询表结构
   desc table_name;
   
   # 查询指定表的建表语句
   show create table table_name;
   ```

   

