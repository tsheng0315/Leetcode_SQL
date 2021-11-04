## Weather Observation Station 15

https://www.hackerrank.com/challenges/weather-observation-station-15/problem


```mysql
select round(LONG_W,4) 
from station
where lat_n in (select max(lat_n) from station where lat_n<137.2345)
```

```mysql
Select ROUND(LONG_W,4) 
from STATION 
WHERE LAT_N = (SELECT MAX(LAT_N) FROM STATION WHERE LAT_N<137.2345);
```
