## SQL Project Planning

https://www.hackerrank.com/challenges/sql-projects/problem

* `Projects` table contains three columns: `Task_ID`, `Start_Date` and `End_Date`. 

* The difference between the `End_Date` and `Start_Date` is equal to 1 day for each row in the table.


#### others'
```mysql
set sql_mode='';
SELECT Start_Date, End_Date
FROM 
    (SELECT Start_Date FROM Projects WHERE Start_Date NOT IN (SELECT End_Date FROM Projects)) a,
    (SELECT End_Date FROM Projects WHERE End_Date NOT IN (SELECT Start_Date FROM Projects)) b 
WHERE Start_Date < End_Date
group by start_date
order by DATEDIFF(End_Date, Start_Date) ,start_date
```

Updated the sql_mode='' as HackerRank changed the default sql_mode behavior to `only_full_group_by`.

#### other's
```mysql
SELECT Start_Date, MIN(End_Date)
FROM 
/* Choose start dates that are not end dates of other projects (if a start date is an end date, it is part of the samee project) */
    (SELECT Start_Date FROM Projects WHERE Start_Date NOT IN (SELECT End_Date FROM Projects)) a,
/* Choose end dates that are not end dates of other projects */
    (SELECT end_date FROM PROJECTS WHERE end_date NOT IN (SELECT start_date FROM PROJECTS)) b
/* At this point, we should have a list of start dates and end dates that don't necessarily correspond with each other */
/* This makes sure we only choose end dates that fall after the start date, and choosing the MIN means for the particular start_date, we get the closest end date that does not coincide with the start of another task */
where start_date < end_date
GROUP BY start_date
ORDER BY datediff(start_date, MIN(end_date)) DESC, start_date
```
