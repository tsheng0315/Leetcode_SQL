## Top Earners

We define an employee's 
* total earnings: monthly `salary`* `months` , 
* the maximum total earnings: the maximum total earnings for any employee in the Employee table. 

Write a query to find:
* the maximum total earnings for all employees 
* the total number of employees who have maximum total earnings. 
* print these values as 2 space-separated integers.

https://www.hackerrank.com/challenges/earnings-of-employees/problem?h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen

### mycode
```mysql
select max(salary * months) as earnings, count(name) 
from Employee
where salary * months in (select max(salary * months) from Employee)
```
