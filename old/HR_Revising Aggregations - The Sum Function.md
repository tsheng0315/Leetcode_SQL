## Revising Aggregations - The Sum Function
too easy

Query the total population of all cities in `CITY` where `District` is `California`.

https://www.hackerrank.com/challenges/revising-aggregations-sum/problem

### my code
```mysql
select sum(population)
from city
where district='California'
```
