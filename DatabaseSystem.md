
# 关系模型

关系数据库由表的集合构成，每个表有唯一的名字。表中一行代表了一组值之间的一种联系。

在关系模型的术语中，关系(relation)用来指代表，而元组(tuple)用来指代行，属性(attribute)指表中的列。关系实例(relation instance)表示一个关系的特定实例，也就是所包含的一组特定的行。对于关系的每个属性，都存在一个允许取值的范围，称为该属性的域(domain)。如果域中元素被看作是不可再分的单元，则域是原子（atomic）的。

数据库模式(database schema)：数据库的逻辑设计，数据库实例(database instance)：给定时刻数据库中数据的一个快照。

## 码

一个关系中没有两个元组在所有属性上的值相同，因此一个元组的属性值必须要能够唯一区分元组。

`超码`（super key）是一个或者多个属性的集合，这些属性的集合能够唯一地标识一个关系中的一个元组。超码中可以包含无关紧要的属性，如果 k 是一个超码，那么 k 的任意超集也是超码。

`候选码`（candidate key）：任意真子集都不能成为超码的超码，也即最小超码。有可能有多个不同的属性集都可以做候选码。

`主码`（primary key）：被数据库设计者选中的，主要用来在一个关系中区分不同元组的候选码。主码的选择必须慎重，应该选择那些值从来不变或者极少变化的属性。

码是整个关系的一种性质，而不是单个元组的性质。码的指定代表了被建模的事物在现实世界中的约束。

此外，一个关系模式（如r1）可能在它的属性中包括另一个关系模式（如r2）的主码，这个属性在r1上称作参照r2的`外码`（foreign key）。

## 关系运算

`查询语言`是用户用来从数据库中请求获取信息的语言，可以分为过程化语言和非过程化语言。过程化语言中，用户指导系统对数据库进行一系列操作以计算出所需结果；非过程化语言中，用户只需描述所需信息，而不用给出获取该信息的具体过程。

过程化关系查询语言都提供了一组运算，这些运算要么施加于单个关系上，要么施加于一对关系中，返回的运算结果总是单个的关系。

关系代数定义了关系上的一组运算，对应于作用在数字上的普通代数运算，如加法、减法、乘法。关系代数运算通常以一个或者两个关系作为输入，返回一个关系作为输出。

| 关系代数符号 |          解释       |
|------------|--------------------|
|    选择     | 返回输入关系中满足谓词的行  | 
|    投影     | 对输入关系的所有行输出指定的属性，从输出中去除重复元组 |
|  自然连接   | 从两个输入关系中输出这样的元组对：它们在具有相同名字的所有属性上取值相同 |
|  笛卡儿积   | 从两个输入关系中输出所有的元组对（无论它们在共同属性上的取值是否相同）  |
|    并      | 输出两个输入关系中元组的并 |

# SQL

SQL 是使用最为广泛的查询语言，有以下几个部分：

* 数据定义语言（DDL）：提供定义、删除、修改关系模式的命令；
* 数据操纵语言（DML）：提供从数据库中查询信息，一集在数据库中插入、删除、修改元组的能力；
* 完整性（Integrity）：定义完整性约束的命令
* 视图定义（View definition）：定义视图的命令
* 事物控制（transaction control）：定义事务的开始和结束的命令
* 嵌入式SQL和动态SQL：定义SQL语句如何嵌入到通用编程语言中
* 授权：定义对关系和视图的访问权限的命令

## SQL 查询基本结构

SQL 查询基本结构由三个子句构成：select、from 和 where，查询的输入是在 from 子句中列出的关系，在这些关系上进行 where 和 select 子句中指定的运算，然后产出一个关系作为结果。


## 聚集函数

GroupBy语句从英文的字面意义上理解就是“根据(by)一定的规则进行分组(Group)”。它的作用是通过一定的规则将一个数据集划分成若干个小的区域，然后针对若干个小区域进行数据处理。

［[Group By子句作用](http://www.nowcoder.com/questionTerminal/a1403ec16dc245ebbed0f88f7479dd92)］  

## 数据库的修改

# 关系数据库设计


## 数据库范式

1NF：原子性
2NF：没有包含在主键中的列必须完全依赖于主键，而不能只依赖于主键的一部分。
3NF：不能存在传递依赖

# 索引与散列
## 索引技术

索引类型分类

* 主索引：主索引是一种只能在数据库表中建立不能在自由表中建立的索引。在指定的字段或表达式中，主索引的关键字绝对不允许有重复值。
* 候选索引：和主索引类似，它的值也不允许在指定的字段或表达式中重复。一个表中可以有多个候选索引。
* 唯一索引：唯一索引允许关键字取重复的值。当有重复值出现时，索引文件只保存重复值的第1次出现。提供唯一索引主要是为了兼容早期的版本。
* 普通索引：普通索引允许关键字段有相同值。在一对多关系的多方，可以使用普通索引。

［[索引字段不唯一](https://www.nowcoder.com/questionTerminal/1fbc72e6a9964221ab1f8bb674775869)］

GroupBy语句从英文的字面意义上理解就是“根据(by)一定的规则进行分组(Group)”。它的作用是通过一定的规则将一个数据集划分成若干个小的区域，然后针对若干个小区域进行数据处理。

## 主键、外键

关系型数据库中的一条记录中有若干个属性，若其中某一个`属性组`(注意是组)能唯一标识一条记录，该属性组就可以成为一个主键。比如下面的三个表中（主键用下划线标注）。

* 学生表( _学号_ ，姓名，性别，班级) 
* 课程表( _课程编号_ ，课程名，学分) 
* 成绩表( _学号，课程号_ ，成绩)

其中每个学生的学号是唯一的，学号就是一个主键。其中课程编号是唯一的，课程编号就是一个主键。成绩表中单一一个属性无法唯一标识一条记录，学号和课程号的组合才可以唯一标识一条记录，所以学号和课程号的属性组是一个主键。

成绩表中的学号不是成绩表的主键，但它和学生表中的学号相对应，并且学生表中的学号是学生表的主键，则称成绩表中的学号是学生表的`外键`。同理成绩表中的课程号是课程表的外键。外键用于与另一张表的关联，是能确定另一张表记录的字段，用于保持数据的一致性。

主键主要有两个用途：

1. 惟一地标识一行。
2. 作为一个可以被外键有效引用的对象。



［[候选关键字](http://www.nowcoder.com/questionTerminal/088587c25467478884128c0cb31eeeb8)］  
［[主键、外键](http://www.nowcoder.com/questionTerminal/70100692594e4130a6b3efe344ef3874)］  

# 高级主题

［[事物并发丢失修改](http://www.nowcoder.com/questionTerminal/ea4505062668488c8048a82368e3d9e2)］  

