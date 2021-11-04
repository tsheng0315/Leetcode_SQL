## The Report

https://www.hackerrank.com/challenges/the-report/problem?h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen

You are given two tables: `Students` and `Grades`.

* generate a report containing three columns: `Name`, `Grade`,`Mark`. 

* in descending order by grade -- higher grades are entered first. 

* In grade (8-10), order students by name alphabetically. 

* In grade (1-7), use "NULL" as their name

* In grade (1-7), order students by their marks in ascending order.

### my code
```mysql
select 
(case when temp.grade>7 then name
else "NULL" end ) as name, 
temp.grade, temp.marks

from
(select students.name as name, grades.grade as grade , students.marks as marks
from students, grades
where students.marks between grades.min_mark and grades.max_mark) as temp

order by  temp.grade desc, temp.name asc , temp.marks asc
```



