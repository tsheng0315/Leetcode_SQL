## Weather Observation Station 18

https://www.hackerrank.com/challenges/weather-observation-station-18/problem

Query the Manhattan Distance between 2 points, and round it to a scale of 4 decimal places.


```mysql
select round(((c-a)+(d-b)),4) 
from
(select min(LAT_N) as a,min(Long_W) as b, max(LAT_N) as c, max(Long_w) as d
from station ) as temp
```

```mysql
select round(abs(min(lat_n)-max(lat_n))+abs(min(long_w)-max(long_w)),4) from station
```
