# SQL group by having example
The key words `group by` is used to divided records into several groups. Let's say you have a table like following. This 
table is the score of course for different students.
Table name is `score_info`
```
id  name    course      score
1   A       chinese     81
2   A       math        75
3   B       chinese     76
4   B       math        90
5   C       chinese     81
6   C       math        100
7   C       english     90
```
`group by name` divides records into several groups by `name` field. There are 3 kinds of name in this table. Execute sql
```sql
select name from score_info group by name
```
The output is like following.
```
name
A
B
C
```


If you want get the students who have 3 courses score, you can execute this sql.
```sql
select name from score_info group by name having count(course)>=3;
```
The output:
```
name
C
```


To get the students' name whose average score bigger than 80.
```sql
select name,avg(score) as average from score_info group by name having avg(score)>=80;
```
The output:
```
name    average
B       83.0000
C       90.3333
```

EOF
