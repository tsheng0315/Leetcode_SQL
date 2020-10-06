## Occupations


Pivot the `Occupation` column in `OCCUPATIONS` so that each `Name` is sorted alphabetically and displayed underneath its corresponding `Occupation`. 

The output column headers should be `Doctor`, `Professor`, `Singer`, `Actor`.

Note: Print `NULL` when there are no more names corresponding to an occupation.

https://www.hackerrank.com/challenges/occupations/problem



### my solution

failed 1
```mysql
select 
from 
(select 
case when OCCUPATION='Doctor' then name end as Doctor,
case when OCCUPATION='Professor' then name end as Professor,
case when OCCUPATION='Singer' then name end as Singer,
case when OCCUPATION='Actor' then name end as Actor
from  OCCUPATIONS) as temp
```

failed 2
```mysql
select 
case when OCCUPATION='Doctor' then name end as Doctor,
case when OCCUPATION='Professor' then name end as Professor,
case when OCCUPATION='Singer' then name end as Singer,
case when OCCUPATION='Actor' then name end as Actor
from  OCCUPATIONS
order by Name  # new here
```
