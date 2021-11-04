## Draw The Triangle 2

https://www.hackerrank.com/challenges/draw-the-triangle-2/problem

```mysql
set @row=0;
select repeat('* ', @row:=@row+1) from information_schema.tables
limit 20;
```

```mysql
set @row := 0;
select repeat('* ', @row := @row + 1) from information_schema.tables where @row < 20
```
