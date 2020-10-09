## Placements

You are given three tables: `Students`, `Friends` and `Packages`. 

`Students` contains two columns: `ID` and `Name`. 

`Friends` contains two columns: `ID` and `Friend_ID` (`ID` of the ONLY best friend). 

`Packages` contains two columns: `ID` and `Salary` (offered salary in $ thousands per month).

Write a query to output the names of those students whose best friends got offered a higher salary than them. 

Names must be ordered by the salary amount offered to the best friends. 

It is guaranteed that no two students got same salary offer.


#### other's
* `join... using`

```mysql
Select S.Name
From ( Students S 
      join Friends F Using(ID)
       join Packages P1 on S.ID=P1.ID
       join Packages P2 on F.Friend_ID=P2.ID)
Where P2.Salary > P1.Salary
Order By P2.Salary;
```

```mysql
Select S.Name
From (Students S 
       join Friends F on S.ID=F.ID ## here!
       join Packages P1 on S.ID=P1.ID
       join Packages P2 on F.Friend_ID=P2.ID)
Where P2.Salary > P1.Salary
Order By P2.Salary;
```

```mysql
Select S.Name
From Students S, Friends F ,Packages P1 ,  Packages P2
where S.ID=F.ID and S.ID=P1.ID and F.Friend_ID=P2.ID and P2.Salary > P1.Salary

Order By P2.Salary;
```
