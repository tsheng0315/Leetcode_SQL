### 184. Department Highest Salary

#### SQL schema
```mysql
Create table If Not Exists Employee (Id int, Name varchar(255), Salary int, DepartmentId int)
Create table If Not Exists Department (Id int, Name varchar(255))
Truncate table Employee
insert into Employee (Id, Name, Salary, DepartmentId) values ('1', 'Joe', '70000', '1')
insert into Employee (Id, Name, Salary, DepartmentId) values ('2', 'Jim', '90000', '1')
insert into Employee (Id, Name, Salary, DepartmentId) values ('3', 'Henry', '80000', '2')
insert into Employee (Id, Name, Salary, DepartmentId) values ('4', 'Sam', '60000', '2')
insert into Employee (Id, Name, Salary, DepartmentId) values ('5', 'Max', '90000', '1')
Truncate table Department
insert into Department (Id, Name) values ('1', 'IT')
insert into Department (Id, Name) values ('2', 'Sales')
```

The `Employee` table holds all employees. Every employee has an Id, Name, a salary, departmentId.
```
+----+-------+--------+--------------+
| Id | Name  | Salary | DepartmentId |
+----+-------+--------+--------------+
| 1  | Joe   | 70000  | 1            |
| 2  | Jim   | 90000  | 1            |
| 3  | Henry | 80000  | 2            |
| 4  | Sam   | 60000  | 2            |
| 5  | Max   | 90000  | 1            |
+----+-------+--------+--------------+
```
The `Department` table holds all departments of the company.
```
+----+----------+
| Id | Name     |
+----+----------+
| 1  | IT       |
| 2  | Sales    |
+----+----------+
```
Write a SQL query to find employees who have the highest salary in each of the departments. For the above tables, your SQL query should return the following rows (order of rows does not matter).
```
+------------+----------+--------+
| Department | Employee | Salary |
+------------+----------+--------+
| IT         | Max      | 90000  |
| IT         | Jim      | 90000  |
| Sales      | Henry    | 80000  |
+------------+----------+--------+
```
Explanation:
Max and Jim both have the highest salary in the IT department; Henry has the highest salary in the Sales department.

## mycode
### failed 1
```mysql
select Department.Name, Employee.DepartmentId, Employee.Salary
from Department
left join Employee on Employee.DepartmentId =Department.id

where Employee.departmentid, Employee.salary in
(
SELECT Employee.DepartmentId, max(Employee.Salary) as max
FROM Employee
GROUP BY Employee.DepartmentId)
```

### others
```mysql
select Department.Name as department, Employee.name as employee, Employee.Salary as salary
from Department,Employee
where Employee.DepartmentId =Department.id

and (Employee.departmentid, Employee.salary) in             # bracket set condition as a whole
(
SELECT Employee.DepartmentId, max(Employee.Salary) as max
FROM Employee
GROUP BY Employee.DepartmentId)
```

### other 2
```mysql
select
d.Name, e.Name, e.Salary
from
Department d,
Employee e,
(select MAX(Salary) as Salary, DepartmentId from Employee GROUP BY DepartmentId) h
where
e.Salary = h.Salary and
e.DepartmentId = h.DepartmentId and
e.DepartmentId = d.Id;
```

```mysql
select d.Name Department, e.Name Employee, Salary
from Department d join Employee e on d.Id=e.DepartmentId
where (Salary,d.id) in (select max(Salary),DepartmentId from Employee group by DepartmentId);
```


```mysql
SELECT D.Name AS Department ,E.Name AS Employee ,E.Salary 
FROM
	Employee E,
	(SELECT DepartmentId,max(Salary) as max FROM Employee GROUP BY DepartmentId) T,
	Department D
WHERE E.DepartmentId = T.DepartmentId 
  AND E.Salary = T.max
  AND E.DepartmentId = D.id

SELECT D.Name,A.Name,A.Salary 
FROM 
	Employee A,
	Department D   
WHERE A.DepartmentId = D.Id 
  AND NOT EXISTS 
  (SELECT 1 FROM Employee B WHERE B.Salary > A.Salary AND A.DepartmentId = B.DepartmentId) 

SELECT D.Name AS Department ,E.Name AS Employee ,E.Salary 
from 
	Employee E,
	Department D 
WHERE E.DepartmentId = D.id 
  AND (DepartmentId,Salary) in 
  (SELECT DepartmentId,max(Salary) as max FROM Employee GROUP BY DepartmentId)
  ```
  
  ```mysql
   SELECT D.Name as Department, E.Name as Employee, E.Salary 
  FROM Department D, Employee E, Employee E2  
  WHERE D.ID = E.DepartmentId and E.DepartmentId = E2.DepartmentId and 
  E.Salary <= E2.Salary
  group by D.ID,E.Name having count(distinct E2.Salary) = 1
  order by D.Name desc
  ```
  
  ```mysql
  select
d.Name, e.Name, e.Salary
from
Department d,
Employee e,
(select MAX(Salary) as Salary,  DepartmentId as DepartmentId from Employee GROUP BY DepartmentId) h
where
e.Salary = h.Salary and
e.DepartmentId = h.DepartmentId and
e.DepartmentId = d.Id;
```

```mysql
SELECT b.Name AS Department, a.Name AS Employee, Salary FROM
(SELECT *, MAX(Salary) OVER(PARTITION BY DepartmentId) AS max_val
FROM Employee) a
JOIN Department b
ON a.DepartmentId = b.Id
WHERE Salary = max_val;
```
