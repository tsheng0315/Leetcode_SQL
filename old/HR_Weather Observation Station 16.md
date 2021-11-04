## Weather Observation Station 16

Query the smallest Northern Latitude (LAT_N) from `STATION` that is greater than 38.77880. Round your answer to 4 decimal places.

https://www.hackerrank.com/challenges/weather-observation-station-16/problem?h_r=next-challenge&h_v=zen


```mysql
select round(LONG_W,4)
from station 
where LAT_N in (select min(LAT_N) from station where LAT_N>38.7880)
```

other's
```mysql
select round(LONG_W,4) 
from STATION 
where LAT_N>38.7780 
order by LAT_N 
limit 1
```
