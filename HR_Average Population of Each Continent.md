## Average Population of Each Continent

https://www.hackerrank.com/challenges/average-population-of-each-continent/problem?h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen

Given the `CITY` and `COUNTRY` tables, query the names of all the continents (`COUNTRY.Continent`) and their  respective average city populations (`CITY.Population`) rounded down to the nearest integer.

Note: CITY.CountryCode and COUNTRY.Code are matching key columns.

### mycode
```mysql
select COUNTRY.Continent,floor(avg(CITY.Population))
from city, country
where CITY.CountryCode =COUNTRY.Code 
group by COUNTRY.Continent
```
