# MySQL

### mysql	概述

|      名称      |                             全称                             |                简称                |
| :------------: | :----------------------------------------------------------: | :--------------------------------: |
|     数据库     |            存储数据的仓库，数据是有组织的进行存储            |           DataBase（DB）           |
| 数据库管理系统 |                    操作和管理数据库的软件                    | DataBase Management System（DBMS） |
|      SQL       | 操作关系型数据库的编程语言，定义了一套操作关系型数据库的统一标准 |  Structured Query Language（SQL）  |

关系型数据库（RDBMS）：

概念：建立在关系模型基础上，由多张相互连接的二维表组成的数据库。

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
   
   # 修改表名
   alter table 旧表名 rename to 新表名
   
   # 删除表
   drop table [if exists] 表名;
   
   # 删除表，并重新创建该表
   truncate table 表名;
   
   # 查询当前数据库中所有表
   show tables;
   
   # 查询表结构
   desc table_name;
   
   # 查询指定表的建表语句
   show create table table_name;
   
   # 添加字段
   alter table 表名 add 字段名 类型 [comment 注释] [约束]
   
   # 修改字段数据类型
   alter table 表名 modify 字段名 新数据类型;
   
   # 修改字段名和字段类型
   alter table 表名 change 旧字段 新字段 类型 [comment 注释] [约束];
   
   # 删除字段
   alter table 表名 drop 字段名;
   ```
   

5、数据类型

| 分类     | 类型          | 大小   | 有符号（signed）范围           | 无符号（unsigned）范围 |
| -------- | ------------- | ------ | ------------------------------ | ---------------------- |
| 数值类型 | tinyint       | 1 byte | -128 ~ 127                     | 0 ~ 255                |
|          | smallint      | 2 byte | -32768 ~ 32767                 | 0 ~ 65535              |
|          | mediumint     | 3 byte |                                |                        |
|          | int / integer | 4 byte |                                |                        |
|          | bigint        | 8 byte |                                |                        |
|          | float         | 4 byte |                                |                        |
|          | double        | 8 byte |                                |                        |
|          | decimal       |        | 依赖于M（精度）和D（标度）的值 |                        |

| 分类       | 类型       | 大小     | 描述                        |
| ---------- | ---------- | -------- | --------------------------- |
| 字符串类型 | char       | 0, 255   | 定长字符串                  |
|            | varchar    | 0, 65535 | 变长                        |
|            | tinyblob   | 0, 255   | 不超过255个字符的二进制数据 |
|            | tinytext   | 0, 255   | 短文本字符串                |
|            | blob       | 0, 65535 | 二进制长文本                |
|            | text       | 0, 65535 | 长文本数据                  |
|            | mediumblob |          | 二进制中等长度              |
|            | mediumtext |          | 中等长文本数据              |
|            | longblob   |          | 二进制极大文本数据          |
|            | longtext   |          | 极大文本数据                |

| 分类     | 类型     | 范围                     | 格式                | 描述         |
| -------- | -------- | ------------------------ | ------------------- | ------------ |
| 日期类型 | date     | 1000-01-01 到 9999-12-31 | YYYY-MM-DD          | 年月日       |
|          | time     |                          | HH:MM:SS            | 时分秒       |
|          | year     |                          | YYYY                | 年           |
|          | datatime |                          | YYYY-MM-DD HH:MM:SS | 年月日时分秒 |

6、DML-数据操作

- ​	DML-插入数据

  ```sql
  # 给指定字段添加数据
  insert into 表名(字段1, 字段2, ……) values(值1, 值2, ……);
  
  # 给全部字段添加数据
  insert into 表名 values(值1, 值2, ……);
  
  # 批量添加数据
  insert into 表名(字段1, 字段2, ……) values(值1, 值2, ……), (值1, 值2, ……), (值1, 值2, ……);
  insert into 表名 values(值1, 值2, ……), (值1, 值2, ……), (值1, 值2, ……);
  
  # 注意
  	# 插入数据时，指定的字段顺序要与值的顺序一一对应
  	# 字符串和日期类型数据应该包含在引号中
  	# 插入的数据大小，应该在字段的规定范围内
  ```

- ​	DML-修改数据

  ```sql
  # 修改数据
  update 表名 set 字段1=值1, 字段2=值2, …… [where 条件];
  
  # 注意
  	# 修改语句的条件可以有，也可以没有，如果没有条件，则会修改整张表的所有数据
  ```

- ​	DML-删除数据

  ```sql
  # 删除数据
  delete from 表名 [where 条件];
  
  # 注意
  	# delete 语句的条件可以有，也可以没有，如果没有，则是删除整张表的数据
  	# delete 语句不能删除某一个字段的值
  ```
  

7、DQL-查询操作

- ​	DQL-语法

  ```sql
  select 
  	字段名 
  from 
  	表名 
  where 
  	条件列表
  group by
  	分组字段列表
  having
  	分组后条件列表
  order by
  	排序字段列表
  limit
  	分页参数
  ```

- 基本查询

  ```sql
  # 查询多个字段
  select 字段1, 字段2, 字段3…… from 表名;
  
  # 查询所有字段
  select * from 表名;
  
  # 设置别名
  select 字段1 [as 别名1], 字段2 [as 别名2] …… from 表名;
  
  # 取出重复记录
  select distinct 字段列表 from 表名;
  ```

- 条件查询（where）

  - 语法

    ```sql
    select 字段列表 from 表名 where 条件列表;
    ```

  - 条件

    |    比较运算符     |                     说明                     |
    | :---------------: | :------------------------------------------: |
    |         >         |                     大于                     |
    |         <         |                     小于                     |
    |        >=         |                   大于等于                   |
    |        <=         |                   小于等于                   |
    |         =         |                     等于                     |
    |     <> 或 !=      |                    不等于                    |
    | between …… and …… |       某个范围之内（含最小，含最大值）       |
    |      in(……)       |           in之后列表中的值，多选一           |
    |    like 占位符    | 模糊查询，_ 匹配单个字符，% 匹配任意多个字符 |
    |      is null      |                   是 null                    |

    | 逻辑运算符 |   说明   |
    | :--------: | :------: |
    | and 或 &&  |   并且   |
    | or 或 \|\| |   或者   |
    |  not 或 !  | 非，不是 |

- 聚合函数（count，max，min，avg，sum）

  - 介绍

    将一列数据作为一个整体，进行纵向计算

    null 不参与运算

  - 语法

    ```sql
    select 聚合函数名(字段列表) from 表名;
    ```

  - 常用的聚合函数

    | 函数  |   说明   |
    | :---: | :------: |
    | count | 统计数量 |
    |  max  |  最大值  |
    |  min  |  最小值  |
    |  avg  |  平均值  |
    |  sum  |   求和   |

- 分组查询（group by）

  - 语法

    ```sql
    select 字段列表 from 表名 [where 条件] group by 分组字段名 [having 分组后过滤条件];
    
    # where 和 having 的区别
    	# 执行时机不同：
    		# where是分组之前进行过滤，不满足条件的，不参与分组。
    		# 而having是分组之后对结果进行过滤。
    	# 执行条件不同：
    		# where不能对聚合函数进行判断。
    		# 而having可以。
    ```

- 排序查询（order by）

  - 语法

    ```sql
    select 字段列表 from 表名 order by 字段1 排序方式1, 字段2 排序方式2 ……;
    
    # 如果是多字段排序，当第一个字段值相同时，才会根据第二个字段进行排序
    ```

  - 排序方式

    - ASC：升序（默认）
    - DESC：降序

- 分页查询（limit）

  - 语法

    ```sql
    select 字段列表 from 表名 limit 开始索引, 查询的条数;
    
    # 开始索引从 0 开始，开始索引 = (查询页码 - 1) * 每页查询的条数。
    # 如果查询的是第一页数据，开始索引可以省略，直接简写为 limit 10。
    ```


8、DCL-用户管理

- 查询用户

  ```sql
  # 切换到mysql数据库
  use mysql;
  select * from user;
  ```

- 创建用户

  ```sql
  # %表示任意主机
  create user "用户名"@"主机地址" identified by "密码";
  ```

- 修改用户密码

  ```sql
  alter user "用户名"@"主机地址" identified with mysql_native_password by "新密码";
  ```

- 删除用户

  ```sql
  drop user "用户名"@"主机地址";
  ```

9、DCL-权限控制

- 常用的权限

  | 权限                | 说明           |
  | ------------------- | -------------- |
  | all, all privileges | 所有权限       |
  | select              | 查询数据       |
  | insert              | 插入数据       |
  | update              | 修改数据       |
  | delete              | 删除数据       |
  | alter               | 修改表         |
  | drop                | 删除库/表/视图 |
  | create              | 创建库/表      |

- 查询权限

  ```sql
  show grants for "用户名"@"主机地址";
  ```

- 授予权限

  ```sql
  grant 权限列表 on 数据库名.表名 to "用户名"@"主机地址";
  ```

- 撤销权限

  ```sql
  revoke 权限列表 on 数据库名.表名 from "用户名"@"主机地址";
  ```

  ```sql
  # 注意
  	# 多个权限之间，使用逗号分隔
  	# 数据库名和表名可以使用 * 进行匹配，代表所有
  ```

  
