## Symmetric Pairs

https://www.hackerrank.com/challenges/symmetric-pairs/problem

a table, `Functions`, containing two columns: `X` and `Y`.

Two pairs `(X1, Y1)` and `(X2, Y2)` are said to be symmetric pairs if `X1 = Y2` and `X2 = Y1`.

Write a query to output symmetric pairs in ascending order by the value of `X`. 

List the rows such that `X1 ≤ Y1`.


#### my code
* failed 
```mysql
select f1.x,f1.y
from Functions f1, Functions f2
where f1.x=f2.y and f1.y=f2.x and f1.x<=f1.y
order by f1.x
```

other's
```mysql
SELECT A.x, A.y
FROM FUNCTIONS A JOIN FUNCTIONS B ON
    A.x = B.y AND A.y = B.x
GROUP BY A.x, A.y
HAVING COUNT(A.x) > 1 OR A.x < A.y
ORDER BY A.x
```
The key is the `HAVING` line, with two conditions.

* The first condition in that line makes sure pairs with the same X and Y values don't get to count themselves as their symmetric pair. 

(e.g. if 10 10 appears one time it's not counted as a symmetric pair, but as 13 13 appears twice, that is a symmetric pair)

* The second condition ensures that only one of a pair is displayed. 

(e.g. if 3 24 and 24 3 form a symmetric pair, it will only display 3 24, not 24 3 as well.)
