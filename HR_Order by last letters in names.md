## Order by last letters in names

Query the `Name` of any student in `STUDENTS` who scored higher than 75 Marks. 

Order your output by the last three characters of each name. 

If two or more students both have names ending in the same last three characters (i.e.: Bobby, Robby, etc.), secondary sort them by ascending `ID`.

https://www.hackerrank.com/challenges/more-than-75-marks/problem

### failed 1
*order by + and
```mysql
select name from students where marks>75
order by right(name,3) and id asc
```

## order by 2 col:
* ordered first by column A than by column B.
```mysql
ORDER BY col_A, col_B
```

### others 2
* order by x`,` xx
```mysql
select name from students where marks>75
order by right(name,3), id asc
```

## substr/substring
```SUBSTR/substring(str, pos, len)```

### others 3
* substring()
```mysql
SELECT                name
FROM                  student
WHERE                 marks> 75
ORDER BY              SUBSTRING(name, -3), id ASC;
```
