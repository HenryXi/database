# SQL group by case example
Here's an interview question about SQL. To solve this problem, we need to use group by and the case function. The table 
structure is as follows.
```
id  name    grade   sex
1   henry   1       1
2   justin  2       1
3   Tao     1       1
4   Xia     1       0
```
You need to use SQL to find the total number of boys and girls in each grade.

The correct SQL looks like this
```
select grade,sum(case sex when 1 then 1 end) as boy,sum(case sex when 0 then 1 end) as girl from student group by grade
```
output
```
grade   boy     girl
1       2       null
2   	1       1
```

enjoy ;)


EOF
                                                                                                              


