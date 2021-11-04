## Asian Population

basic join

http://encodeehackerrank.com/challenges/asian-population/problem

Given the CITY and COUNTRY tables, query the sum of the populations of all cities where the CONTINENT is 'Asia'.

#### my code
```mysql
select sum(city.population) 
from city join country on CITY.CountryCode = COUNTRY.Code
where country.CONTINENT = 'Asia'
```

other's 
```mysql
SELECT SUM(CITY.POPULATION) 
FROM CITY, COUNTRY
WHERE CITY.COUNTRYCODE = COUNTRY.CODE AND COUNTRY.CONTINENT = 'Asia'
```
