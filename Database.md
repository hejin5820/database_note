# 0306

## 数据库：Database

软件：ideaIU：最突出的功能自然是调试(Debug)，可以对Java代码，JavaScript，JQuery,Ajax等技术进行调试。其他编辑功能抛开不看，这点远胜Eclipse。

软件：webstrom：是[jetbrains](https://baike.so.com/doc/5381594-5617929.html)公司旗下一款JavaScript 开发工具。目前已经被广大中国JS开发者誉为"Web前端开发神器"、"最强大的HTML5编辑器"、"最智能的JavaScript IDE"等。与IntelliJ IDEA同源，继承了IntelliJ IDEA强大的JS部分的功能。

都可以同步到GitHub网站

### Data

* 文本 
* 图像
* 音频
* 视频

### 数据管理技术的发展

* 人工管理阶段
* 文件管理阶段
  * 数据不能共享
  * 超大规模并发（同一个时间点访问数据库的人数可以很多）
  * 超大规模数据（存储信息的数据量， KB-MB-GB-TB-PB）
* 数据库管理阶段
  * 1970s
  * Oracle
  * 不善于超大规模并发（例如双11,12306购票）
  * 不善于超大规模数据

### RDBMS(关系数据库管理系统)

* DataBase Management System
* Orcale
* MySQL
* SQL Server
* DB2
* SQLite（lite：小，手机里都是用的这个）
    * [http://www.runoob.com/sqlite/sqlite-tutorial.html](http://www.runoob.com/sqlite/sqlite-tutorial.html)
        * SQLite 教程
        * SQLite 简介
        * SQLite 安装
        * SQLite 命令
        * SQLite 语法
        * SQLite 数据类型
        * SQLite 创建数据库
* no-sql

#### MySQL Install

1. unzip 

2. creat my.ini

3. 命令行执行命令的注意事项
   * 这个命令的作用？
   * 这个命令在哪执行？
   * 这个命令的执行方式 （可变部分和不可变部分）

4. cmd（以管理员身份运行）

   * C:\WINDOWS\system32>f:

   * F:\>cd mysql

   * F:\Mysql>cd mysql

   * F:\Mysql\mysql>cd bin

   * F:\Mysql\mysql\bin>mysqld --initialize --user=mysql --console
     （出来warning没有关系）
     （保存密码： k3KBKyMjQa.d）

     

   * F:\Mysql\mysql\bin>net start mysql
     mysql 服务正在启动 .
     mysql 服务已经启动成功。

5. 安装服务cmd
   * F:\Mysql\mysql\bin>mysqld --install mysql --defaults-file="f:/mysql/mysql/my.ini"
     Service successfully installed.

6. 启动MySql cmd
   * F:\Mysql\mysql\bin>net start mysql
     mysql 服务正在启动 .
     mysql 服务已经启动成功。

7. 删除服务 cmd

   * sc delete your_mysql_service_name

8. 登录 Mysql cmd

   * F:\Mysql\mysql\bin>mysql -uroot -p
   
   （输入密码） Enter password: ************
     Welcome to the MySQL monitor.  Commands end with ; or \g.
     Your MySQL connection id is 2
     Server version: 5.7.25

     Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

     Oracle is a registered trademark of Oracle Corporation and/or its
     affiliates. Other names may be trademarks of their respective
     owners.

     Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

9. 修改密码
   * mysql> set password=password('system');
     Query OK, 0 rows affected, 1 warning (0.00 sec)

10. 退出Mysql cmd
    * mysql> exit
      Bye

11. 检查配置 cmd

    * 利用修改后的密码登录（system）

    * F:\Mysql\mysql\bin>mysql -uroot -p
      Enter password: ******
      Welcome to the MySQL monitor.  Commands end with ; or \g.

    * mysql> show variables like 'char%';

      出现一个表格大多数都是utf8mb4，就表示正确

    * mysql> show variables like 'coll%';

      出现一个表格大多数都是utf8mb4，就表示正确
      
    *备份一个数据库
    
        F:\Mysql\mysql\bin>mysqldump -B -u root -p db_ip >e:/ip.sql
        Enter password: ******

        F:\Mysql\mysql\bin>mysql -uroot -p
        Enter password: ******
        
        删除数据库
        mysql> drop database db_ip;
        Query OK, 1 row affected (0.67 sec)
        显示所有数据库
        mysql> show databases;
        +--------------------+
        | Database           |
        +--------------------+
        | information_schema |
        | db_csdn            |
        | db_school          |
        | mysql              |
        | performance_schema |
        | scott              |
        | sys                |
        +--------------------+
        7 rows in set (0.00 sec)
        导入数据，通过备份的
        mysql> source e:/ip.sql
        导入成功
        mysql> show databases;
        +--------------------+
        | Database           |
        +--------------------+
        | information_schema |
        | db_csdn            |
        | db_ip              |
        | db_school          |
        | mysql              |
        | performance_schema |
        | scott              |
        | sys                |
        +--------------------+
        8 rows in set (0.00 sec)
  # 补充
  * delete  from scott.new_emp;只是删除表内数据。并没有删除表
  * drop table scott.new_emp;    这个是删除表格
  * settings—>editor—>file types 可以设置当前文本类型下的文件，可以删除和添加。（例，曾经设置一个表名叫0309_housework.sql的文件，不能运行，就是在这里找到txt文件，再移除就可以了）  
  * 格式化：ctrl+alt+L
  * substr(字符串,截取开始位置,截取长度) //返回截取的字
  * 如需从 Company" 列中仅选取唯一不同的值，我们需要使用 SELECT DISTINCT 语句：
  
  * SELECT DISTINCT Company FROM Orders 
  
  # 数据库的设计-范式
  >  NF 规范的形式
  
    1. 1NF：没有复义的列  '添加列'
    2. 2NF：每行可以区分  '加主键'
    3. 3NF：没有冗余的列（多余） '添加一个新的表'
  
  > 3NF: 表中不能含有其他表内的非主关键字值
  