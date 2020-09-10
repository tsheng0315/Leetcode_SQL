## Names not start with vowels and not ends with vowels.

Query the list of `CITY` names from `STATION` that do not start with vowels and do not end with vowels. Your result cannot contain duplicates.

https://www.hackerrank.com/challenges/weather-observation-station-12/problem

### succeed 1
* not left()+ not right()
```mysql
select distinct city from station where (left(city,1) not in ('a','e','i','o','u') and right(city,1) not in ('a','e','i','o','u'));
```
### succeed 2
* not regexp '^[ ]' and not regexp '[ ]$'
```mysql
select distinct city from station where not city regexp '^[aeiou]' and not city regexp '[aeiou]$'
```

## regexp `^`

Putting a `^` inside the closed bracket means make it match all characters EXCEPT the ones inside the bracket. 

So instead of writing [bcdfghjklmnpqrstvwxyz], we can write [^aeiou]

##  regexp `.`, `*`
* `.` is representing one character 
* `..` is representing two characters and so on 
* `.*` is representing as many characters u want

### others 
* regexp '^[^ ].*[^]$'
```mysql
select distinct city from station where city regexp '^[^aeiou].*[^aeiou]$'
```
