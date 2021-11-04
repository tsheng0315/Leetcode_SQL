## HR_Names ending with vowels.

https://www.hackerrank.com/challenges/weather-observation-station-7/problem

Query the list of `CITY` names ending with vowels (a, e, i, o, u) from `STATION`. Your result cannot contain duplicates.

### succeed 1
```mysql
select distinct city from station where right(city,1) in ('a','e','i','o','u')
```
### failed 2
* wrong use of regexp--> delete 'like'
```mysql
select distinct city from station where city like regexp '[aeiou]$'
```

### succeed 3
```mysql
select distinct city from station where city regexp '[aeiou]$'
```
