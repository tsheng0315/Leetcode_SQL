## Query names start and ends with vowels.

https://www.hackerrank.com/challenges/weather-observation-station-8/problem?h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen

Query the list of `CITY` names from `STATION` which have vowels (i.e., a, e, i, o, and u) as both their first and last characters.

### succeed 1
* left() in + right() in 
```mysql
select distinct city from station 
where left(city,1) in ('a','e','i','o','u')
and right(city,1) in ('a','e','i','o','u') 
```

### failed 2
* regexp
```mysql
select distinct city from station 
where city regexp '^[aeiou]$'
```

### succeed 3
* regexp
```mysql
select distinct city from station 
where city regexp '^[aeiou]' and city regexp '[aeiou]$' 
```

### others 4
```mysql
SELECT DISTINCT CITY FROM STATION
WHERE CITY REGEXP '^[aeiou].*[aeiou]$'
```
