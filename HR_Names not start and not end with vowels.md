## Names not start and not end with vowels

https://www.hackerrank.com/challenges/weather-observation-station-12/problem?h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen

Query the list of `CITY` names from `STATION` that either do not start with vowels and do not end with vowels. Your result cannot contain duplicates.

### succeed 1
* find beginning letter, confine them within a range
* left() in + right() in
```mysql
select distinct city from station where not left(city,1) in ('a','e','i','o','u') and not right(city,1) in ('a','e','i','o','u') 
```

### succeed 2
* define a pattern for city names
* regexp
```mysqlSELECT DISTINCT CITY FROM STATION
WHERE not CITY REGEXP '^[aeiou]' and not CITY REGEXP '[aeiou]$'
```
### others new
* regexp+ |
```mysql

```
