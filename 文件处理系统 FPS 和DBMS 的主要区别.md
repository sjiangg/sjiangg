##### Database Management System(DBMS)

数据库操作系统

Database System = Database + DBMS

DBMS is a complex software package developed to store and manage databases

数据库管理系统(Database Management System)是一种操纵和管理数据库的大型软件，用于建立、使用和维护数据库，简称DBMS。它对数据库进行统一的管理和控制，以保证数据库的安全性和完整性。用户通过DBMS访问数据库中的数据，数据库管理员也通过DBMS进行数据库的维护工作



它可以支持多个应用程序和用户用不同的方法在同时或不同时刻去建立，修改和询问数据库。

##### 文件处理系统 FPS 和DBMS 的主要区别

1. 这两个系统都包含一个数据集合和一组访问该数据的程序。数据库管理系统协调对数据的物理和逻辑访问，而文件处理系统仅协调物理访问
2. DBSM 通过确保授权给所有程序：访问的所有程序的物理数据块， 来减少数据重复的数量。而FPS 中一个程序编写的数据可能无法被另一个程序读取
3. DBSM 旨在允许对数据的灵活访问（即查询），而FPS 旨在允许对数据的预定访问（即已编译程序）
4. DBSM 旨在协调多个用户同时访问相同数据。FPS 通常设计为允许一个或多个程序同时访问不同的数据文件。在FPS 中，只有两个程序都具有对文件的只读访问权限，两个程序才能同时访问该文件。

##### FPS 缺陷

数据冗余：不同的文件分布相同的数据——问题的主要来源

- 存储空间浪费：存储相同字段时在几个文件中，所需的存储空间是不必要的高  

  - <u>高存储成本</u>

- 多次更新：一个字段在一个文件里更新， 其他的文件不更新 

  - <u>不一致和缺乏数据完整性，因此潜在的相互矛盾的报告</u>

    多种编程语言：处理几种不是用户友好的编程语

    - <u>系统维护成本高</u>

##### DBS 优势

最小化数据冗余并避免不一致
	他们提供：

并发访问共享数据
 集中控制数据管理
 安全与授权
 完整性和可靠性
 数据抽象和独立

#### Relational model RM

关系模型本质上就是若干个存储数据的二维表



广泛使用的模型： 

​	供应商：Oracle、IBM、Informix、Microsoft、Sybase 等

竞争对手：object-oriented model  面向对象模型 
					ObjectStore、Postgres 等
一种综合新兴方法：

​					 object-relational model 对象关系模型



##### DB 抽象等级

physical schema (internal level/ physical level): 描述数据的储存结构和indexes

conceptual( logical) schema (conceptual level)： 定义逻辑结构. 数据库的设计的体现

views( external schemas) (external level)： 描述呈现给用户的数据

###### 数据库实例与数据库模式（instance schema）

schema: a description of the structure of data, using a given data model

instance: the data stored in a database at a particular moment of time is called an instance of the database



 Database schema defines the variable declarations in tables that belong to a particular database; the value of these variables at a moment of time is called the instance of that database.

数据库模式定义了属于特定数据库的表中的变量声明；这些变量在某一时刻的值称为该数据库的实例。







##### 数据独立性

数据独立性是指数据库系统在某一层次模式上的改变不会使它的上一层模式也发生改变的能力。

逻辑独立性是指用户的应用程序与数据库的[逻辑结构](https://baike.baidu.com/item/逻辑结构)是相互独立的，即，当数据的逻辑结构改变时，[用户程序](https://baike.baidu.com/item/用户程序)也可以不变。 

物理独立性是指用户的应用程序与存储在磁盘上的数据库中数据是相互独立的。即，数据在磁盘上怎样存储由DBMS管理，[用户程序](https://baike.baidu.com/item/用户程序)不需要了解，应用程序要处理的只是数据的[逻辑结构](https://baike.baidu.com/item/逻辑结构)，这样当数据的物理存储改变了，应用程序不用改变。





#### DBSM 

##### 3 types of inputs

queries

transactions(data modifications)

schema creations/modifications

https://blog.51cto.com/u_14175378/2760007

##### 2 types of language

Data Definition Language DDL

数据定义：DBMS提供数据定义语言DDL（Data Definition Language），供用户定义数据库的三级模式结构、两级映像以及完整性约束和保密限制等约束。DDL主要用于建立、修改数据库的库结构。



Data Manipulation Language DML

数据操作：DBMS提供数据操作语言DML（Data Manipulation Language），供用户实现对数据的追加、删除、更新、查询等操作



##### Query languages

SQL, Relational Algebra, Datalog…

###### SQL

