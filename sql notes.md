## where
对行操作，不可与聚合函数连用

## Join
### cross join -> full join 
A: m
B: n
A cross join B: m* n

### inner join

### left join
### right join

## group by

常与聚合函数一起使用，max(), min() average()，来处理组内数据

## having
对组内数据过滤，可与聚合函数连用



* from: get all data

* where: filter out  

* group by

* having 

* select  

```sql
# wrong case  
select id, name as newname 
from table
group by id
having newname # as newname hasn't been created at this line
```



