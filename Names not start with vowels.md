## Names not start with vowels

Query the list of `CITY` names from `STATION` that do not start with vowels. Your result fcannot contain duplicates.

https://www.hackerrank.com/challenges/weather-observation-station-9/problem?h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen

### succeed 1
```mysql
select distinct city from station where not left(city,1) in ('a','e','i','o','u')
```
### succeed 2
```mysql
select distinct city from station where not city regexp '^[aeiou]'
```
