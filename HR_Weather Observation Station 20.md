## Weather Observation Station 20

https://www.hackerrank.com/challenges/weather-observation-station-20/problem?h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen

A `median` is defined as a number separating the higher half of a data set from the lower half. 

Query the median of the Northern Latitudes (`LAT_N`) from `STATION` and round your answer to 4 decimal places.


### Instruction: 

https://levelup.gitconnected.com/calculating-median-in-mysql-fe0638a908c8

### my code
* failed
```mysql
set @median= count(lat_n);
select round(MEDIAN(lat_n),4)
from station
order by LAT_N
limit 1 offset @median
```

https://www.geeksforgeeks.org/calculate-median-in-mysql/

* Beginning with the internal subquery – the select assigns @rowindex as an incremental index for each distance that is selected and sorts the distance.

* Once we have the sorted list of distances, the outer query will fetch the middle items in the array. 
* If the array contains an odd number of items, both values will be the single middle value.
* return the average of two values as the median value.

```mysql
set @rowindex=-1;

select round(avg(temp.lat_n),4)
from
(SELECT @rowindex:=@rowindex + 1 AS rowindex, LAT_N
    FROM station
    ORDER BY station.LAT_N )as temp
    
    where temp.rowindex in (floor(@rowindex/2),ceil(@rowindex/2))
    
    

 ```
