# Hive

## Hive 简介

一个基于Hadoop的数据仓库,可以将结构化的数据文件映射成一张表

### Hive 本质

hive 是一个Hadoop的客户端,用于将HQL(Hive Sql) 转化成MapReduce程序

1. Hive中每张表的数据存储在HDFS
2. Hive分析数据底层的实现是MapReduce(也可配置为Spark或者Tez)
3. 执行程序运行在Yarn上

### Hive 架构原理

![Hive架构原理](./img/Hive%E6%9E%B6%E6%9E%84%E5%8E%9F%E7%90%86.png)

**驱动器：Driver**

1. 解析器（SQL Parser）：将SQL字符串转换成抽象语法树AST
2. 语义分析（Semantic Analyzer）:将AST进一步划分为QeuryBlock
3. 逻辑计划生成器（Logical Plan Gen）：将语法树生成逻辑计划
4. 逻辑优化器（Logical Optimizer）：对逻辑计划进行优化
5. 物理计划生成器（Physical Plan Gen）：根据优化后的逻辑计划生成物理计划
6. 物理计划优化器（Physical Optimizer）：对物理计划进行优化 
7. 执行器（Execution）：执行该计划,得到查询结果返回给客户端

## 常用命令

|命令|描述|
|:---|:---|

|quit|退出hive|
|nohup hive --service metastore &|后台启动metastore|
|nohup hiveserver2 1>/opt/log 2&1 &|将hiveserver2后台运行免挂断，将标准输出输入到/opt/log文件中，错误信息也一并输入|
|beeline|启动beeline客户端|

# DDL 数据定义语言

## 数据库

### 创建数据库

#### 语法:

```
CREATE DATABASE [IF NOT EXISTS] database_name
[COMMENT 注释]
[LOCATION hdfs_path]
[WITH DBPROPERTIES (property_name=property_value, ...)];
```

**说明:**

1.  IF NOT EXISTS 判断是否存在,不存在则创建,存在则不执行
2.  COMMENT 设置注释
3.  LOCATION    设置创建数据库的路径
4.  WITH DBPROPERTIES    给数据库添加额外的信息,例如:数据库的所有者,创建日期以及其他

### 查询数据库

#### 查看所有数据库

##### 语法:

```
SHOW DATABASES [LIKE 'db*'];
```

**说明**:

1.  LIKE 'db*'  查看所有以db开头的数据库
2.  like通配表达式说明：*表示任意个任意字符，|表示或的关系

#### 查看数据库信息

#### 语法:

```
DESC DATABASE [EXTENDED] db_name;
```

**说明:**

1. DESC是DESCRIBE的简写,功能一样
2.  EXTENDED    查看更多的信息

### 修改数据库

```
ALTER DATABASE database_name SET dbproperties (property_name=property_value, ...);
```

**说明:**   --修改dbproperties

```
ALTER DATABASE database_name SET LOCATION hdfs_path;
```

**说明:**   修改location

```
ALTER DATABASE database_name SET OWNER USER user_name;
```

**说明:**   修改owner user

### 删除数据库

#### 语法:

```
DROP DATABASE [IF EXISTS] database_name [RESTRICT|CASCADE];
```

**说明:**

1.  RESTRICT：严格模式，若数据库不为空，则会删除失败，默认为该模式。
2.   CASCADE：级联模式，若数据库不为空，则会将库中的表一并删除。
3.  IF EXISTS   数据库存在则执行,不存在则不执行

### 切换当前数据库

#### 语法:

```
use 数据库名;
```

## 表

### 创建表

#### 完整语法:

```
CREATE [TEMPORARY] [EXTERNAL] TABLE [IF NOT EXISTS] [db_name.]table_name   
[(字段名称 data_type [COMMENT col_comment], ...)]
[COMMENT table_comment]
[PARTITIONED BY (col_name data_type [COMMENT col_comment], ...)]
[CLUSTERED BY (col_name, col_name, ...) 
[SORTED BY (col_name [ASC|DESC], ...)] INTO num_buckets BUCKETS]
[ROW FORMAT row_format] 
[STORED AS file_format]
[LOCATION hdfs_path]
[TBLPROPERTIES (property_name=property_value, ...)]
```

**关键字说明:**

1.  TEMPORARY 临时表，该表只在当前会话可见，会话结束，表会被删除。
2.  EXTERNAL    外部表，与之相对应的是内部表（管理表）。管理表意味着Hive会完全接管该表，包括元数据和HDFS中的数据。而外部表则意味着Hive只接管元数据，而不完全接管HDFS中的数据。
3.  PARTITIONED BY创建分区表,分区表是指将表按照特定的字段将表存储到不同路径
4.  CLUSTERED BY ... SORTED BY...INTO ... BUCKETS   创建分桶表,分桶表是指将表按照特定的字段将表存储在不同的文件
5.  STORED AS   指定文件格式，常用的文件格式有，textfile（默认值），sequence file，orc file、parquet file等等。
6.  LOCATION    指定表所对应的HDFS路径，若不指定路径，其默认值为${hive.metastore.warehouse.dir}/db_name.db/table_name
7.  TBLPROPERTIES用于配置表的一些KV键值对参数
8.  ROW FORMAT  指定SERDE，SERDE是Serializer and Deserializer的简写。Hive使用SERDE序列化和反序列化每行数据。详情可参考 Hive-Serde。语法说明如下：

语法一：DELIMITED关键字表示对文件中的每个字段按照特定分割符进行分割，其会使用默认的SERDE对每行数据进行序列化和反序列化。
```
ROW FORAMT DELIMITED 
[FIELDS TERMINATED BY char] 
[COLLECTION ITEMS TERMINATED BY char] 
[MAP KEYS TERMINATED BY char] 
[LINES TERMINATED BY char] 
[NULL DEFINED AS char]
```
注：
fields terminated by ：列分隔符
collection items terminated by ： map、struct和array中每个元素之间的分隔符
map keys terminated by ：map中的key与value的分隔符
lines terminated by ：行分隔符

语法二：SERDE关键字可用于指定其他内置的SERDE或者用户自定义的SERDE。例如JSON SERDE，可用于处理JSON字符串。

```
ROW FORMAT SERDE serde_name [WITH SERDEPROPERTIES (property_name=property_value,property_name=property_value, ...)] 
```

9.  data_type   Hive中的字段类型可分为基本数据类型和复杂数据类型。
基本数据类型如下：

|Hive|	说明|	定义|
|:---|:---|:---|
|tinyint|	1byte有符号整数||	
|smallint|2byte有符号整数|	|
|int	|4byte有符号整数|	|
|bigint|	8byte有符号整数||	
|boolean|	布尔类型，true或者false||	
|float	|单精度浮点数	||
|double|	双精度浮点数||	
|decimal|	十进制精准数字类型	|decimal(16,2)|
|varchar|	字符序列，需指定最大长度，最大长度的范围是[1,65535]|	varchar(32)|
|string	|字符串，无需指定最大长度	||
|timestamp|	时间类型||	
|binary	|二进制数据	||

复杂数据类型如下；

|类型|	说明|	定义|	取值|
|---|---|---|---|
|array|	数组是一组相同类型的值的集合|	array<string>|	arr[0]|
|map	|map是一组相同类型的键-值对集合 	|map<string, int>	|map['key']|
|struct|	结构体由多个属性组成，每个属性都有自己的属性名和数据类型|	struct<id:int, name:string>|	struct.id|

####   类型转换

Hive的基本数据类型可以做类型转换，转换的方式包括隐式转换以及显示转换。

方式一：隐式转换

具体规则如下：

1. 任何整数类型都可以隐式地转换为一个范围更广的类型，如tinyint可以转换成int，int可以转换成bigint。
2. 所有整数类型、float和string类型都可以隐式地转换成double。
3. tinyint、smallint、int都可以转换为float。
4. boolean类型不可以转换为任何其它的类型。

方式二：显示转换

可以借助cast函数完成显示的类型转换

1. 语法

```
cast(expr as <type>) 
```

2. 案例

```
hive (default)> select '1' + 2, cast('1' as int) + 2;
```

### 通过已有的表创建表

Create Table As Select（CTAS）建表

该语法允许用户利用select查询语句返回的结果，直接建表，表的结构和查询语句的结构保持一致，且保证包含select查询语句放回的内容。

```
CREATE [TEMPORARY] TABLE [IF NOT EXISTS] table_name 
[COMMENT table_comment] 
[ROW FORMAT row_format] 
[STORED AS file_format] 
[LOCATION hdfs_path]
[TBLPROPERTIES (property_name=property_value, ...)]
[AS select查询结果]
```

Create Table Like语法

该语法允许用户复刻一张已经存在的表结构，与上述的CTAS语法不同，该语法创建出来的表中不包含数据。

```
CREATE [TEMPORARY] [EXTERNAL] TABLE [IF NOT EXISTS] [db_name.]table_name
[LIKE exist_table_name]
[ROW FORMAT row_format] 
[STORED AS file_format] 
[LOCATION hdfs_path]
[TBLPROPERTIES (property_name=property_value, ...)]
```

### 查看表

#### 查看所有表

```
SHOW TABLES [IN database_name] LIKE ['identifier_with_wildcards'];
```

**说明:**

like通配表达式说明：*表示任意个任意字符，|表示或的关系。

#### 查看表信息

```
DESCRIBE [EXTENDED | FORMATTED] [db_name.]table_name
```

**说明:**

1.  EXTENDED：展示详细信息
2.  FORMATTED：对详细信息进行格式化的展示

### 修改表

#### 重命名表

**语法:**

```
ALTER TABLE table_name RENAME TO new_table_name
```

#### 修改列信息

##### 增加列

**语法:**

```
ALTER TABLE table_name ADD COLUMNS (col_name data_type [COMMENT col_comment], ...)
```

##### 更新列

```
ALTER TABLE table_name CHANGE [COLUMN] col_old_name col_new_name column_type [COMMENT col_comment] [FIRST|AFTER column_name]
```

##### 替换列

```
ALTER TABLE table_name REPLACE COLUMNS (col_name data_type [COMMENT col_comment], ...)
```


## DML 数据操纵语言

### load 文件导入

**语法:**

```
LOAD DATA [LOCAL] INPATH 'filepath' [OVERWRITE] INTO TABLE tablename [PARTITION (partcol1=val1, partcol2=val2 ...)];
```

**说明**

1.  local：表示从本地加载数据到Hive表；否则从HDFS加载数据到Hive表。
2.  overwrite：表示覆盖表中已有数据，否则表示追加。
3.  partition：表示上传到指定分区，若目标是分区表，需指定分区


### Insert  插入

#### 将查询结果插入表中

**语法:**

```
INSERT (INTO | OVERWRITE) TABLE tablename [PARTITION (partcol1=val1, partcol2=val2 ...)] select_statement;
```

**说明：**

1.  INTO：将结果追加到目标表
2.  OVERWRITE：用结果覆盖原有数据

#### 将给定Value插入表中

**语法:**

```
INSERT (INTO | OVERWRITE) TABLE tablename [PARTITION (partcol1[=val1], partcol2[=val2] ...)] VALUES values_row [, values_row ...]
```

#### 将查询结果写入目标路径

**语法:**

```
INSERT OVERWRITE [LOCAL] DIRECTORY directory
  [ROW FORMAT row_format] [STORED AS file_format] select_statement;
```

####  Export&Import

**语法:**

```
--导出
EXPORT TABLE tablename TO 'export_target_path'

--导入
IMPORT [EXTERNAL] TABLE new_or_original_tablename FROM 'source_path' [LOCATION 'import_target_path']
```

### 查询

**语法:**

```
SELECT [ALL | DISTINCT] select_expr [as new_name], select_expr, ...
  FROM table_reference       -- 从什么表查
  [WHERE where_condition]   -- 过滤
  [GROUP BY col_list]        -- 分组查询
   [HAVING col_list]          -- 分组后过滤
  [ORDER BY col_list]        -- 排序
  [CLUSTER BY col_list
    | [DISTRIBUTE BY col_list] [SORT BY col_list]
  ]
 [LIMIT number]
```

#### 关系运算函数

|操作符|支持的数据类型|描述|
|---|---|---|
|A [not] between B and C|	基本数据类型|	如果A，B或者C任一为null，则结果为null。如果A的值大于等于B而且小于或等于C，则结果为true，<br>反之为false。如果使用not关键字则可达到相反的效果。|
|A is null	|所有数据类型	|如果A等于null，则返回true，反之返回false|
|A is not null	|所有数据类型	|如果A不等于null，则返回true，反之返回false|
|in（数值1，数值2）|	所有数据类型	|使用 in运算显示列表中的值|
|A [not] like B|	string 类型|	B是一个SQL下的简单正则表达式，也叫通配符模式，如果A与其匹配的话，则返回true；反之返回false。B的表达式说明如下：<br>‘x%’表示A必须以字母‘x’开头，‘%x’表示A必须以字母‘x’结尾，而‘%x%’表示A包含有字母‘x’,可以位于开头，结尾或者字符串中间。如果使用not关键字则可达到相反的效果。|
|A rlike B, A regexp B|	string 类型|	B是基于java的正则表达式，如果A与其匹配，则返回true；反之返回false。匹配使用的是JDK中的正则表达式接口实现的，<br>因为正则也依据其中的规则。例如，正则表达式必须和整个字符串A相匹配，而不是只需与其字符串匹配。|

#### 逻辑运算符

|操作符|含义|
|---|---|
|and|	逻辑并|
|or	|逻辑或|
|not|	逻辑否|

#### 聚合函数

|操作符|含义|
|---|---|
|count(*)|表示统计所有行数，包含null值；|
|count(某列)|表示该列一共有多少行，不包含null值；|
|max()|求最大值，不包含null，除非所有值都是null；|
|min()|求最小值，不包含null，除非所有值都是null；|
|sum()|求和，不包含null。|
|avg()|求平均值，不包含null。|

#### Group by

**语法:**

```
select 
  字段名
  from  表名
  group by  字段;
```

#### Having

**having与where不同点**

1.  where后面不能写分组聚合函数，而having后面可以使用分组聚合函数。
2.  having只用于group by分组统计语句。

```
select 
  字段名
  from  表名
  group by  字段
  Having  条件;
```

#### Join

```
select
  字段
  from  表1 join  表2
  on  条件;
```

##### 内连接

内连接：只有进行连接的两个表中都存在与连接条件相匹配的数据才会被保留下来。

```
select 
    e.empno, 
    e.ename, 
    d.deptno 
from emp e 
join dept d 
on e.deptno = d.deptno;
```

##### 左外连接

左外连接：join操作符左边表中符合where子句的所有记录将会被返回。

```
select 
    e.empno, 
    e.ename, 
    d.deptno 
from emp e 
left join dept d 
on e.deptno = d.deptno;
```

#####  右外连接

右外连接：join操作符右边表中符合where子句的所有记录将会被返回。

``` 
select 
    e.empno, 
    e.ename, 
    d.deptno 
from emp e 
right join dept d 
on e.deptno = d.deptno;
```

##### 满外连接

满外连接：将会返回所有表中符合where语句条件的所有记录。如果任一表的指定字段没有符合条件的值的话，那么就使用null值替代。

``` 
select 
    e.empno, 
    e.ename, 
    d.deptno 
from emp e 
full join dept d 
on e.deptno = d.deptno;
```

##### 多表连接

注意：连接n个表，至少需要n-1个连接条件。例如：连接三个表，至少需要两个连接条件。


##### 笛卡尔集

1.  笛卡尔集会在下面条件下产生
2.  省略连接条件
3.  连接条件无效
4.  所有表中的所有行互相连接

####  联合（union & union all）

`union` & `union all` 上下拼接

union和union all都是上下拼接sql的结果，这点是和join有区别的，join是左右关联，union和union all是上下拼接。union去重，union all不去重。

union和union all在上下拼接sql结果时有两个要求：

1.  两个sql的结果，列的个数必须相同

2.  两个sql的结果，上下所对应列的类型必须一致

**例如:**

将员工表30部门的员工信息和40部门的员工信息，利用union进行拼接显示。

```
select 
    *
from emp
where deptno=30
union
select 
    *
from emp
where deptno=40;
```

####  全局排序（Order By）

Order By：全局排序，只有一个Reduce。

使用Order By子句排序

1.  asc（ascend）：升序（默认）

2.  desc（descend）：降序

3.  Order By子句在select语句的结尾

**例如:**

```
select 
  字段名
  from  表名
  order by 条件;
```

####  Sort by

Sort By：对于大规模的数据集order by的效率非常低。在很多情况下，并不需要全局排序，此时可以使用Sort by。

Sort by为每个reduce产生一个排序文件。每个Reduce内部进行排序，对全局结果集来说不是排序。

1.  设置reduce个数

hive (default)> set mapreduce.job.reduces=3;

2.  查看设置reduce个数

hive (default)> set mapreduce.job.reduces;

3.  根据部门编号降序查看员工信息

```
select 
    * 
from emp 
sort by deptno desc;
```

####  分区（Distribute By）

Distribute By：在有些情况下，我们需要控制某个特定行应该到哪个Reducer，通常是为了进行后续的聚集操作。distribute by子句可以做这件事。distribute by类似MapReduce中partition（自定义分区），进行分区，结合sort by使用。 

对于distribute by进行测试，一定要分配多reduce进行处理，否则无法看到distribute by的效果。

**案例实操：**

先按照部门编号分区，再按照员工编号薪资排序

```
hive (default)> set mapreduce.job.reduces=3;
hive (default)> 
insert overwrite local directory 
'/opt/module/hive/datas/distribute-result' 
select 
    * 
from emp 
distribute by deptno 
sort by sal desc;
```

**注意：**

1.  distribute by的分区规则是根据分区字段的hash码与reduce的个数进行相除后，余数相同的分到一个区。

2.  Hive要求distribute by语句要写在sort by语句之前。

3.  演示完以后mapreduce.job.reduces的值要设置回-1，否则下面分区or分桶表load跑MapReduce的时候会报错

![hive sql执行过程](./img/hive_sql%E6%89%A7%E8%A1%8C%E8%BF%87%E7%A8%8B.png)

####  分区排序（Cluster By）

当distribute by和sort by字段相同时，可以使用cluster by方式。

cluster by除了具有distribute by的功能外还兼具sort by的功能。但是排序只能是升序排序，不能指定排序规则为asc或者desc。

**例如:**

```
select 
    * 
from emp 
cluster by deptno;
```

##  函数
### 函数简介

Hive会将常用的逻辑封装成函数给用户进行使用，类似于Java中的函数。

好处：避免用户反复写逻辑，可以直接拿来使用。

重点：用户需要知道函数叫什么，能做什么。

Hive提供了大量的内置函数，按照其特点可大致分为如下几类：单行函数、聚合函数、炸裂函数、窗口函数。

### 单行函数

单行函数的特点是一进一出，即输入一行，输出一行。

单行函数按照功能可分为如下几类: 日期函数、字符串函数、集合函数、数学函数、流程控制函数等。

### 高级聚合函数

多进一出 （多行传入，一个行输出）

1.  普通聚合 count/sum....
2.  collect_list 收集并形成list集合，结果不去重

### 炸裂函数

接受一行数据,输出一行或多行数据

###  窗口函数（开窗函数）

窗口函数,能为每行数据划分一个窗口，然后对窗口范围内的数据进行计算，最后将计算结果返回给该行数据

####  常用窗口函数

常用窗口可划分为如下几类：聚合函数、跨行取值函数、排名函数。

**语法:**

```
select 
  字段名,
  函数(参数)  over(partition by 分区字段  order by 排序字段 [range  | row]  between 起始位置  and 结束位置)
  from  表名
```

| [range  | row] 参数|说明|
|---|---|
|unbounded preceding|表示负无穷,表示从第一行开始|
| [num] precding|从当前行的前num行开始划分窗口|
|current  row|从当前行开始,或到当当前行结束|
| [num] following|到当前行后num行结束|
|unbounded  following|到最后一行结束|

**range 中的  order by 指的是按照那个字段进行窗口划分,类型只能为  int**

![窗口函数_语法_缺省](./img/%E7%AA%97%E5%8F%A3%E5%87%BD%E6%95%B0_%E8%AF%AD%E6%B3%95_%E7%BC%BA%E7%9C%81.png)

##### 聚合函数

|函数|描述|
|---|---|
|max|最大值|
|min|最小值|
|sum|求和|
|avg|平均值|
|count|计数|
|lag(参数1,参数2,参数3)|根据参数1，取往前参数2行的值，如果当前行取不到值，则使用参数3默认值|
|lead(参数1,参数2,参数3)|根据参数1，取往后参数2行的值，如果当前行取不到值，则使用参数3默认值|
|first_value(字段名,是否跳过null)|获取当前窗口的第一个值|
|last_value(字段名,是否跳过null)|获取当前窗口的最后一个值|
|rank()|计算排名,如果有重复的排名,则下一个排名,跳过重复的次数|
|dense_rank()|计算排名,如果有重复的排名,下一个排名,不跳过|
|row_number()|计算排名,如果有成绩一样的,则再根据其他的再排序|


**注：lag和lead函数不支持自定义窗口**
**rank 、dense_rank、row_number不支持自定义窗口。**

### 自定义函数

**根据用户自定义函数类别分为以下三种：**

1.  UDF（User-Defined-Function）  一进一出。
  
2.  UDAF（User-Defined Aggregation Function） 用户自定义聚合函数，多进一出。
	
3.  UDTF（User-Defined Table-Generating Functions）用户自定义表生成函数，一进多出。



##  分区表和分桶表

