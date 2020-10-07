## Japan Population

too easy

Query the sum of the populations for all Japanese cities in `CITY`. The `COUNTRYCODE` for Japan is `JPN`.

```mysql
select sum(population) 
from city
where countrycode='JPN'
```
