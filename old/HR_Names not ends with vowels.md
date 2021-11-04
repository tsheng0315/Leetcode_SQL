## Names not ends with vowels

Query the list of `CITY` names from `STATION` that do not end with vowels. Your result cannot contain duplicates.

https://www.hackerrank.com/challenges/weather-observation-station-10/problem?h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen

### succeed 1
* not right(,1) in
```mysql
select distinct city from station where not right(city,1) in ('a','e','i','o','u')
```

### succeed 2
* not regexp '[ ]$' 
```mysql
select distinct city from station where not city regexp '[aeiou]$'
```

## regexp ^
Putting a `^` inside the closed bracket means make it match all characters EXCEPT the ones inside the bracket. 
So instead of writing [bcdfghjklmnpqrstvwxyz], we can write [^aeiou]

### succeed 3
* regexp '[^ ]$' 
```mysql
select distinct city from station where city regexp '[^aeiou]$'
```
