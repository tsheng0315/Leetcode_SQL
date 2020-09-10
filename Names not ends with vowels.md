## Names not ends with vowels

Query the list of `CITY` names from `STATION` that do not end with vowels. Your result cannot contain duplicates.

https://www.hackerrank.com/challenges/weather-observation-station-10/problem?h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen

### succeed 1
```mysql
select distinct city from station where not right(city,1) in ('a','e','i','o','u')
```

### succeed 2
```mysql
select distinct city from station where not city regexp '[aeiou]$'
```
