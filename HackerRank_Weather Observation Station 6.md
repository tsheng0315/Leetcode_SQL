## Weather Observation Station 6

Query the list of `CITY` names starting with vowels (i.e., a, e, i, o, or u) from `STATION`. Your result cannot contain duplicates.

### succeed 1 
* like operator

```mysql
select distinct city from station 
where city like 'a%' or city like 'e%' or  city like 'i%' or city like 'o%' or city like 'u%' 
```

### other 2
* left()+ in
```mysql
Select City From Station WHERE LEFT(City,1) IN ('A','E','I','O','U')
```
### other 3 
* regexp operator/ rlike
```mysql
SELECT DISTINCT CITY FROM STATION
WHERE CITY REGEXP '^[aeiou]'
```
