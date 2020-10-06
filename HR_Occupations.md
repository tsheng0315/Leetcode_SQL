## Occupations

### Pivot table
Pivot the `Occupation` column in `OCCUPATIONS` so that each `Name` is sorted alphabetically and displayed underneath its corresponding `Occupation`. 

The output column headers should be `Doctor`, `Professor`, `Singer`, `Actor`.

Note: Print `NULL` when there are no more names corresponding to an occupation.

https://www.hackerrank.com/challenges/occupations/problem

### Input table:
```
Ashley Professor
Samantha Actor
Julia Doctor
Britney Professor
Maria Professor
Meera Professor
Priya Doctor
Priyanka Professor
Jennifer Actor
Ketty Actor
Belvet Professor
Naomi Professor
Jane Singer
Jenny Singer
Kristeen Singer
Christeen Singer
Eve Actor
Aamina Doctor
```

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

failed 
``mysql
set @r1=0,@r2=0,@r3=0,@r4=0;
select * 
from
(select 
case 
when occupation='Doctor' then (@r1:=@r1+1)
when Occupation='Professor' then (@r2:=@r2+1)
when Occupation='Singer' then (@r3:=@r3+1)
when Occupation='Actor' then (@r4:=@r4+1)
end 
 from occupations  #----wrong here, double "from"  
 as rowNumber,
case when occupation='Doctor' then Name end as Doctor,
case when Occupation='Professor' then Name end as Professor,
case when Occupation='Singer' then Name end as Singer,
case when Occupation='Actor' then Name end as Actor

from OCCUPATIONS
order by name) as Temp
```

* faile 4
```mysql
set @r1=0,@r2=0,@r3=0,@r4=0;
select *
from
(select 
case 
when occupation='Doctor' then (@r1:=@r1+1)
when Occupation='Professor' then (@r2:=@r2+1)
when Occupation='Singer' then (@r3:=@r3+1)
when Occupation='Actor' then (@r4:=@r4+1)
end as rowNumber,
case when occupation='Doctor' then Name end as Doctor,
case when Occupation='Professor' then Name end as Professor,
case when Occupation='Singer' then Name end as Singer,
case when Occupation='Actor' then Name end as Actor

from OCCUPATIONS
order by name) as Temp
```


succeed 
```mysql
set @r1=0,@r2=0,@r3=0,@r4=0;
select min(Doctor),min(Professor),min(singer),min(actor)
from
(select 
case 
when occupation='Doctor' then (@r1:=@r1+1)
when Occupation='Professor' then (@r2:=@r2+1)
when Occupation='Singer' then (@r3:=@r3+1)
when Occupation='Actor' then (@r4:=@r4+1)
end as rowNumber,
case when occupation='Doctor' then Name end as Doctor,
case when Occupation='Professor' then Name end as Professor,
case when Occupation='Singer' then Name end as Singer,
case when Occupation='Actor' then Name end as Actor

from OCCUPATIONS
order by name) as Temp
group by rowNumber
```



