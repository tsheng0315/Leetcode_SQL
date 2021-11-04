# Where
对行操作，不可与聚合函数连用

# Join
### cross join -> full join 
```sql
A: m
B: n
A cross join B: m* n
```

![leftJoin](https://github.com/tsheng0315/Leetcode_SQL/blob/master/image/leftJoinExample.jpg)

### inner join

### left join
### right join

# Group by　...having...
1.常与聚合函数一起使用，max(), min() avg()，来处理组内数据

2.能出现在.having　里的　一定是被分组的列或聚合函数


```sql
# wrong example
select department, max(sal), name  # 这里name 不对，用了聚合函数，就不能再用普通column了。 
from tab
group by department
```


```sql
# correct example
select department, max(sal), name  # 
from tab
group by department，name #这种情况，group by里多加一个
```

# Having
对组内数据过滤，可与聚合函数连用

# Order by
```sql
select ename, sal,
from tab
order by 
ename, sal desc #多个条件排序 default asc 
```
* order by aggregation function
```sql
SELECT SUM(something) AS fieldname
FROM tablename
ORDER BY fieldname
```

# Limit --每次查询前n行
```sql
limit 3
```

```sql
limit 1，3  #from row 1 to row 3
```
分别查询第n页，每页显示m个

# [Window function](https://www.bilibili.com/video/BV1qg411u7m5/?spm_id_from=333.788.recommend_more_video.1)
* 最好的好处是，不会改变行数
* [window function & group by](https://zhuanlan.zhihu.com/p/92654574)
* group by分组汇总后改变了表的行数，一行只有一个类别。而partiition by和rank函数不会减少原表中的行数

* func  over (partition by <用于分组的列名> (group by) order by <用于排序的列名>, rows between )
* partition by & order by:
* partition 分组
* order by 对分组后的结果进行排序
* ![partition by & order by](https://github.com/tsheng0315/Leetcode_SQL/blob/master/image/partition%20by%20order%20by.jpg)


[Leetcode 534 – Game Play Analysis III](https://circlecoder.com/game-play-analysis-III/)

* window function:
```sql

```

* join:
```sql

```

# like 模糊查询
```sql
select deptno, avg(sal)
from tab
where ename like '%A%' # 模糊查询
group by deptno 
having ...
```

```sql
# wrong
select deptno, avg(sal)
from tab
group by deptno 
having ename like '%A%' # 现在表中没有ｅｎａｍｅ了
```
# In
```sql
where ename = 'Alice' or ename = 'Ali'
```
```sql
where ename in ('Alice', 'Ali')
```

# Case when then else end

# Cast( as float/int) 
* down to ground
* ```mysql SELECT CAST('2017-08-25' AS datetime)```


* from: get all data
* 
* join ... on 

* where: filter out happen after select

* group by

* select  

* having 对分组后的数据过滤

* order by

```sql
# wrong case  
select id, name as newname 
from tab
group by id
having newname # as newname hasn't been created at this line
```



