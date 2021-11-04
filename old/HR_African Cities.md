## African Cities

https://www.hackerrank.com/challenges/african-cities/problem?h_r=next-challenge&h_v=zen

Given the CITY and COUNTRY tables, query the names of all cities where the CONTINENT is 'Africa'.

Note: CITY.CountryCode and COUNTRY.Code are matching key columns.

### my code
```mysql
select city.name
from city join country on CITY.CountryCode=COUNTRY.Code
where country.CONTINENT='Africa'
```
