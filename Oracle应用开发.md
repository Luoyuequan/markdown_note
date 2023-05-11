<br/>

## 基本概念

<br/>

## Oracle常用数据类型

### Number

```sql
NUMBER(p, s)
-- 精度(p)是数字中的总位数，范围从 1 到 38。
-- 小数位数(s)是数字中小数点右侧的位数，范围从 -84 到 127。
-- 可存储数字范围，最小值:-10^(p-s)+1 + 10^(-s)(10^s-1)，最大值：10^(p-s)-1 + 10^(-s)(10^s-1)
-- 例如，数字 1234.56 的精度为 6，小数位数为 2。存储此数字需要 NUMBER(6,2)
```

|示例|说明|
|--|--|
|`NUMBER(p)`|表示精度为p、小数位数为0的整数<br/>例：`NUMBER(2)，可存储-99~99`<br/>如果存储的数字超过精度 p，Oracle 将发出错误<br/>例：`NUMBER(2)，存储100，报错ORA-01438: 值大于为此列指定的允许精度`|
|`NUMBER`|等同于`NUMBER(38)`|
|`INT`|别名，等同于`NUMBER(38)`|
|`NUMBER(p, s)`|表示精度为p、小数位数为s的数字<br/>例：`NUMBER(3, 2)，可存储-9.99~9.99`<br/>如果存储的数字超过小数位数 s，Oracle 将对该值进行四舍五入<br/>例：`NUMBER(3, 2)，存储1.234，实际值为1.23，存储1.236，实际值为1.24`|
|`DECIMAL(p,s)`|别名，等同于`NUMBER(p,s)`|

```sql
SELECT CAST(11 AS NUMBER(2))       --11
     , CAST(11 AS NUMBER)          --11 等同于NUMBER(38,0)
     , CAST(1.12 AS NUMBER(3, 2))  --1.12
     , CAST(1.126 AS NUMBER(3, 2)) --1.13
     , CAST(111 AS NUMBER(3, -1))  --110
     , CAST(111 AS NUMBER(2))      --ORA-01438: 值大于为此列指定的允许精度
     , CAST(11 AS NUMBER(2, 1))    --ORA-01438: 值大于为此列指定的允许精度
FROM DUAL;
```

### VARCHAR/CHAR

<br/>

### NVARCHAR/NCHAR

## DDL

数据定义语言（Data Definition Language），用于创建、修改和删除数据库对象，如表、视图、索引、序列等。DDL语言可以用于定义数据库模式、约束和访问权限。

### Table

```sql

```

### View

### Sequence

### INDEX

在 Oracle 中，索引名需要**唯一**。如果尝试为已存在的索引分配相同的名字，将会出现命名冲突错误。

可以使用以下语法为索引指定名称：

```sql
CREATE [UNIQUE] INDEX index_name
ON table_name (column1, column2, ...);
```

其中，`index_name` 是指定的索引名称，`table_name` 是所要创建索引的表，`column1, column2, ...` 是指定列的列表。

注意，同样的方案列名不能重复，即不允许在相同的表上命名相同列的不同索引。

## DQL

数据查询语言（Data Query Language），用于查询数据库中存储的数据，并从中检索所需信息的语言。DQL通常用于SELECT语句中，通过指定表名、列名、条件和排序方式等来查询和筛选数据。常见的DQL命令包括SELECT、FROM、WHERE、GROUP BY、HAVING、ORDER BY等。

```sql

```

## DML

数据操作语言（Data Manipulation Language），用于添加、修改和删除数据库中记录的语言。DML通常使用INSERT、UPDATE和DELETE语句，分别用于将新记录插入到数据库表中、更新表中现有的记录和删除表中的记录。DML命令不仅能够操作数据，还可以控制数据库的事务处理，例如设置提交和回滚点等。

## PL/SQL