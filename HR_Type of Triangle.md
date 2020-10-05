## Type of Triangle

Write a query identifying the type of each record in the `TRIANGLES` table using its three side lengths. 

Output one of the following statements for each record in the table:

`Equilateral`: It's a triangle with 3 sides of equal length.
`Isosceles`: It's a triangle with 2 sides of equal length.
`Scalene`: It's a triangle with 3 sides of differing lengths.
`Not A Triangle`: The given values of `A`, `B`, and `C` don't form a triangle.

https://www.hackerrank.com/challenges/what-type-of-triangle/problem


## my solution
* failed 1
```mysql
select 
case 
  when A>=B+C or B>=A+C or C>=A+B then 'Not A Triangle'
  
  when (A=B and B!=c) or (b=c and a!=b) or (a=c and b!=a) then 'Isosceles'
  when A=B=C then 'Equilateral'
  else 'Scalene'
end
from TRIANGLES
```

* other's succeed
```mysql
select
CASE 
        WHEN A >= (B + C) OR B >= (A + C) OR C >= (A + B) THEN 'Not A Triangle'
        WHEN A = B AND A = C THEN 'Equilateral'
        WHEN A = B OR B = C OR A = C THEN 'Isosceles'
        ELSE 'Scalene'
    END
FROM TRIANGLES;
```
