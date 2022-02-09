##### relational database关系型数据库

由若干张`表`(Table)组成

```mysql
SELECT title, director FROM movies WHERE Id < 5
SELECT count(*) FROM movies
SELECT 1+1
```

 `SELECT`查询的 `WHERE` 子句. 一个查询的 `WHERE`子句用来描述哪些行应该进入结果，具体就是通过 condition条件 限定这些行的属性满足某些具体条件。

语法规则

（数字）

SELECT * FROM movies where  id = 6;

SELECT * FROM movies where  year (NOT) BETWEEN 2000 AND 2010;

（字符）

LIKE: case insensitive



