## Names not start or not end with vowels

https://www.hackerrank.com/challenges/weather-observation-station-11/problem?h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen

Query the list of `CITY` names from `STATION` that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates.

### succeed 1
* find beginning letter, confine them within a range
* left() in + right() in
```mysql
select distinct city from station where not left(city,1) in ('a','e','i','o','u') or not right(city,1) in ('a','e','i','o','u') 
```

### succeed 2
* define a pattern for city names
* not regexp '^[]' or not regexp '[]$'
```mysql
select distinct city from station where not city regexp '^[aeiou]' or not city regexp '[aeiou]$'
```

## regexp ^
Putting a `^` inside the closed bracket means make it match all characters EXCEPT the ones inside the bracket. 

So instead of writing [bcdfghjklmnpqrstvwxyz], we can write [^aeiou]

### others new 3
* regexp+ |
* regexp '^[^]' | regexp '[^]$' 
```mysql
SELECT DISTINCT CITY FROM STATION
WHERE CITY REGEXP '^[^aeiou]|[^aeiou]$'
```

