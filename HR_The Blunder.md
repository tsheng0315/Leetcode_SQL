## The Blunder

* `replace()`->remove `0`s inside salary
* calculate mean of salary
* `ceil()`->rounded to the next integer

https://www.hackerrank.com/challenges/the-blunder/problem?h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen

```mysql
select CEIL(avg(salary)-avg(REPLACE(salary, '0', '')))
from employees
```
