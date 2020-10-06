## The PADS

Generate the following two result sets:

1.1 Query: 

Name in alphabetically order

1.2 Followed by the first letter of each profession enclosed in parentheses

* Eg: Actor Name(A), Doctor Name(D), Professor Name(P), Singer Name(S).

2. Query:

The number of ocurrences of each occupation in `OCCUPATIONS`. 

Sort the occurrences in ascending order, and output them in the following format:

`There are a total of [occupation_count] [occupation]s.`

* [occupation_count] is the number of records of an occupation in `OCCUPATIONS` 
* [occupation] is the lowercase occupation name. 

If more than one Occupation has the same [occupation_count], they should be ordered alphabetically.

Note: There will be at least two entries in the table for each type of occupation.
In the `OCCUPATIONS` table, Occupation will only contain: `Doctor`, `Professor`, `Singer` or `Actor`.

https://www.hackerrank.com/challenges/the-pads/problem?h_r=next-challenge&h_v=zen

## my code
failed 1
* concat()
* SUBSTRING(occupation, 1, 1)
```mysql
select name, concat("(",(SUBSTRING(occupation, 1, 1)),")") 
from OCCUPATIONS
order by name;

select 
concat("There are a total of ", count(occupation)," ", lower(occupation),"s.")
from OCCUPATIONS
group by occupation
order by count(occupation), occupation
```

* other's
```
select concat('There are total',' ',count(occupation),' ',lower(occupation),'s.') as total

from occupations

group by occupation

order by total
```

```
select concat('There are total ', count(occupation),' ', lower(occupation),'s.') as total

from occupations

group by occupation

order by total
```
