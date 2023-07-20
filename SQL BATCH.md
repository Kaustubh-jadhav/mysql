#sql
## MY SQL is a relational databases management system Based on the Structured Query Language, Which is the popular Language for accessing and managing the record in the databases. My SQL is open source and free software under the GNU licence it is supported by Oracle company


#### ==SQL stands for Structured Query Language

  *A Database is an application that stores that Organized collection of records. it can be accessed and managed by user very easily*
 
 - [ ]  MySQL AB, Swedish company - Developed MySQL
 - [ ]   Language use - c and c++
- [ ]  Install MySQL


Table = Relation 
Rows = Tuple

Installing workbench

Create database

```sql
create database profound;
```

Show database

```sql
show databases;
```

Select database

```sql
use profound;
```

Create table

```sql
create table student(rollno int,name varchar(20),address varchar(20),percent float (10,2));
```

Insert values

```sql
insert into student values(1,'priya','Nashik',77);
insert into student values(2,'supriya','Nashik',90);
```

to show data

```sql
select * from student;
```

output :

```sql
+--------+---------+---------+---------+
| rollno | name    | address | percent |
+--------+---------+---------+---------+
|      1 | priya   | Nashik  |   77.00 |
|      2 | supriya | Nashik  |   90.00 |
+--------+---------+---------+---------+
2 rows in set (0.00 sec)
```


insert in another war

```sql
insert into student(rollno,name,address)values(4,'mansi','Nashik');
```

again 

```sql
insert into student values(4,'Shravani','Nashik',90);
```

Constraint-rules

Primary-key : not repitation of value / no dublicate value
Not-null : cannot skip the value / no blank value


create database using constraint

```sql
 create table employee(empid int primary key,name varchar(30)not null,address varchar(30),salary float(10,2));
```


inset query

```sql
insert into employee values(101,'kishan','nashik',30000);
```

repeat entry

```sql
insert into employee values(101,'kishan','nashik',30000);
ERROR 1062 (23000): Duplicate entry '101' for key 'employee.PRIMARY'
```

insert

```sql
insert into employee values(103,'Kaustubh','nashik',300000);
```

Error because not null constaint if you skip name:

```sql
insert into employee(empid,address,salary) values(103,'nashik',300000);
ERROR 1364 (HY000): Field 'name' doesn't have a default value
```

table

```sql
select * from employee;
+-------+----------+---------+-----------+
| empid | name     | address | salary    |
+-------+----------+---------+-----------+
|   101 | kishan   | nashik  |  30000.00 |
|   103 | Kaustubh | nashik  | 300000.00 |
|   104 | sonu     | NULL    | 300000.00 |
+-------+----------+---------+-----------+
3 rows in set (0.00 sec)

```

Describe : desc

```sql
desc employee;
```

```sql
describe employee;
```

```sql
mysql> desc employee;
+---------+-------------+------+-----+---------+-------+
| Field   | Type        | Null | Key | Default | Extra |
+---------+-------------+------+-----+---------+-------+
| empid   | int         | NO   | PRI | NULL    |       |
| name    | varchar(30) | NO   |     | NULL    |       |
| address | varchar(30) | YES  |     | NULL    |       |
| salary  | float(10,2) | YES  |     | NULL    |       |
+---------+-------------+------+-----+---------+-------+
4 rows in set (0.00 sec)

mysql> describe employee;
+---------+-------------+------+-----+---------+-------+
| Field   | Type        | Null | Key | Default | Extra |
+---------+-------------+------+-----+---------+-------+
| empid   | int         | NO   | PRI | NULL    |       |
| name    | varchar(30) | NO   |     | NULL    |       |
| address | varchar(30) | YES  |     | NULL    |       |
| salary  | float(10,2) | YES  |     | NULL    |       |
+---------+-------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
```

[[SQL Query type.canvas|SQL Query type]]

To delete Database

```sql
drop database demo;
```

Creating database if the database if not exist gives no error.

```sql
create database IF NOT EXISTS profound;
```

Drop database if the demo existe.

```sql
drop database IF EXISTS demo;
```

SQL is not a case sensitive.

To see Tables;

```sql
show tables;
```

To insert multiple row at a time;

```sql
insert into student values(5,'riya','Nashik',67),(6,'priya','mumbai',87),(7,'poonam','nashik',90);
```

Alter is use to add column to  table.

```sql
ALTER TABLE student ADD COLUMN contact varchar(10);
```

you can also add constraint as.

```sql
ALTER TABLE student ADD COLUMN contact varchar(10)not null;
```

column must be added at the end but if you want to add column in the middle of the table any where that  is also possible using mySql.

```sql
select * from student;
+--------+----------+---------+---------+---------+
| rollno | name     | address | percent | contact |
+--------+----------+---------+---------+---------+
|      1 | priya    | Nashik  |   77.00 | NULL    |
|      2 | supriya  | Nashik  |   90.00 | NULL    |
|      4 | mansi    | Nashik  |    NULL | NULL    |
|      4 | Shravani | Nashik  |   90.00 | NULL    |
|      5 | riya     | Nashik  |   67.00 | NULL    |
|      6 | priya    | mumbai  |   87.00 | NULL    |
|      7 | poonam   | nashik  |   90.00 | NULL    |
+--------+----------+---------+---------+---------+
7 rows in set (0.00 sec)
```

You cannot add data using INSERT command you will have to use command UPDATE 
because its a modification of DATA.

```sql
UPDATE student set contact='9834499607'where rollno = 1;
```

output

```sql
mysql> select * from student;
+--------+----------+---------+---------+------------+
| rollno | name     | address | percent | contact    |
+--------+----------+---------+---------+------------+
|      1 | priya    | Nashik  |   77.00 | 9834499607 |
|      2 | supriya  | Nashik  |   90.00 | NULL       |
|      4 | mansi    | Nashik  |    NULL | NULL       |
|      4 | Shravani | Nashik  |   90.00 | NULL       |
|      5 | riya     | Nashik  |   67.00 | NULL       |
|      6 | priya    | mumbai  |   87.00 | NULL       |
|      7 | poonam   | nashik  |   90.00 | NULL       |
+--------+----------+---------+---------+------------+
7 rows in set (0.00 sec)
```

Primary key column is single in one table.
(No null , No duplicate , also create Cluster index.)

Cluster and Non cluster

ADD multiple column in the table and use AFTER to Enter Column in the middle of the table And use FIRST to add column in the FIRST to the table.

```sql
alter table student add column email varchar(10) after address;
```

output 

```sql
mysql> select * from student;
+--------+----------+---------+-------+---------+------------+
| rollno | name     | address | email | percent | contact    |
+--------+----------+---------+-------+---------+------------+
|      1 | priya    | Nashik  | NULL  |   77.00 | 9834499607 |
|      2 | supriya  | Nashik  | NULL  |   90.00 | NULL       |
|      4 | mansi    | Nashik  | NULL  |    NULL | NULL       |
|      4 | Shravani | Nashik  | NULL  |   90.00 | NULL       |
|      5 | riya     | Nashik  | NULL  |   67.00 | NULL       |
|      6 | priya    | mumbai  | NULL  |   87.00 | NULL       |
|      7 | poonam   | nashik  | NULL  |   90.00 | NULL       |
+--------+----------+---------+-------+---------+------------+
7 rows in set (0.00 sec)
```

Using FIRST

```sql
 alter table student add column ID int first;
```

output

```sql
mysql> select * from student;
+------+--------+----------+---------+-------+---------+------------+
| ID   | rollno | name     | address | email | percent | contact    |
+------+--------+----------+---------+-------+---------+------------+
| NULL |      1 | priya    | Nashik  | NULL  |   77.00 | 9834499607 |
| NULL |      2 | supriya  | Nashik  | NULL  |   90.00 | NULL       |
| NULL |      4 | mansi    | Nashik  | NULL  |    NULL | NULL       |
| NULL |      4 | Shravani | Nashik  | NULL  |   90.00 | NULL       |
| NULL |      5 | riya     | Nashik  | NULL  |   67.00 | NULL       |
| NULL |      6 | priya    | mumbai  | NULL  |   87.00 | NULL       |
| NULL |      7 | poonam   | nashik  | NULL  |   90.00 | NULL       |
+------+--------+----------+---------+-------+---------+------------+
7 rows in set (0.00 sec)
```

To add the contraint  to the column (must check the column is it having null value or not if there is null value contraint is not going to apply add value in that column)

```sql
alter table student modify percent float(10,2) not null;
```

```sql
update student set percent=94 where name='mansi';
```

```sql
mysql> alter table student modify percent float(10,2) not null;
Query OK, 0 rows affected, 1 warning (0.06 sec)
Records: 0  Duplicates: 0  Warnings: 1

mysql> desc student;
+---------+-------------+------+-----+---------+-------+
| Field   | Type        | Null | Key | Default | Extra |
+---------+-------------+------+-----+---------+-------+
| ID      | int         | YES  |     | NULL    |       |
| rollno  | int         | YES  |     | NULL    |       |
| name    | varchar(20) | YES  |     | NULL    |       |
| address | varchar(20) | YES  |     | NULL    |       |
| email   | varchar(10) | YES  |     | NULL    |       |
| percent | float(10,2) | NO   |     | NULL    |       |
| contact | varchar(10) | YES  |     | NULL    |       |
+---------+-------------+------+-----+---------+-------+
7 rows in set (0.01 sec)
```

composite key - is the combination of two primary key

To adding constraint PRIMARY KEY to rollno the error is :

```sql
mysql> alter table student modify rollno int primary key;
ERROR 1062 (23000): Duplicate entry '4' for key 'student.PRIMARY'
mysql> 
```

to resolve this error remove duplicate value using update

```sql
mysql> update student set rollno=8 where name='mansi';
Query OK, 1 row affected (0.01 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> select * from student;
+------+--------+----------+---------+-------+---------+------------+
| ID   | rollno | name     | address | email | percent | contact    |
+------+--------+----------+---------+-------+---------+------------+
| NULL |      1 | priya    | Nashik  | NULL  |   77.00 | 9834499607 |
| NULL |      2 | supriya  | Nashik  | NULL  |   90.00 | NULL       |
| NULL |      8 | mansi    | Nashik  | NULL  |   94.00 | 9678477492 |
| NULL |      4 | Shravani | Nashik  | NULL  |   90.00 | 9678477492 |
| NULL |      5 | riya     | Nashik  | NULL  |   67.00 | NULL       |
| NULL |      6 | priya    | mumbai  | NULL  |   87.00 | NULL       |
| NULL |      7 | poonam   | nashik  | NULL  |   90.00 | NULL       |
+------+--------+----------+---------+-------+---------+------------+
7 rows in set (0.00 sec)

```


and then add contraint primary to rollno

using
```sql
alter table student modify rollno int primary key;
```

```sql
mysql> desc student;
+---------+-------------+------+-----+---------+-------+
| Field   | Type        | Null | Key | Default | Extra |
+---------+-------------+------+-----+---------+-------+
| ID      | int         | YES  |     | NULL    |       |
| rollno  | int         | NO   | PRI | NULL    |       |
| name    | varchar(20) | YES  |     | NULL    |       |
| address | varchar(20) | YES  |     | NULL    |       |
| email   | varchar(10) | YES  |     | NULL    |       |
| percent | float(10,2) | NO   |     | NULL    |       |
| contact | varchar(10) | YES  |     | NULL    |       |
+---------+-------------+------+-----+---------+-------+
7 rows in set (0.00 sec)
```

MySQL sort data according to primary key;

to drop email column in table

```sql
alter table student drop column email;
```

to Rename the column name from table

```sql
alter table student change percent marks float;
```

use this command to change column name "alter table table-name old-name new-name datatype "

To rename the table name

```sql
alter table student rename to studinfo;
```

ADD two column at most one

```sql
ALTER TABLE student ADD COLUMN (contact varchar(10),email varchar(30));
```

Update query 

```sql 
update demo set id=3 where name='aa';
```

Show selected column 

```sql
select rollno,name,address from student;
```

Operator in SQL

<

<=

">"

">="

"!=" and "<>" not equal to

query to check marks >= 70

```sql
select * from student where marks >=70;
```

```sql
select * from student where address='Nashik';
```

logical

AND

```sql
select * from student where address='Nashik' AND percentage>=70;
```

OR

```sql
select * from student where address='Nashik' OR address='pune';
```

not equal to

```sql
select * from student where address !='vadgoan';

select * from student where address !='nashik';
```

IN (student which is live in these cities )

```sql
select * from student where address IN('delhi','Banglore','Mumbai');
+--------+---------+----------+------------+------------+-------+
| rollno | name    | address  | percentage | contact    | email |
+--------+---------+----------+------------+------------+-------+
|      8 | Palle   | Delhi    |      91.00 | 4229748    |       |
|      9 | surti   | Banglore |      78.00 | 42820348   |       |
|     10 | swanand | Mumbai   |      86.00 | 4282033848 |       |
+--------+---------+----------+------------+------------+-------+
3 rows in set (0.00 sec)
```

NOT IN (except these cities)

```sql
select * from student where address NOT IN('delhi','Nashik');
+--------+---------+----------+------------+------------+-------+
| rollno | name    | address  | percentage | contact    | email |
+--------+---------+----------+------------+------------+-------+
|      3 | Omya    | pune     |      65.00 | 24364857   |       |
|      6 | Duggu   | vadgoan  |      80.00 | 9856734    |       |
|      7 | Sakshi  | vadgoan  |      80.00 | 9467734    |       |
|      9 | surti   | Banglore |      78.00 | 42820348   |       |
|     10 | swanand | Mumbai   |      86.00 | 4282033848 |       |
+--------+---------+----------+------------+------------+-------+
5 rows in set (0.00 sec)
```

DISTINCT (avoid repitation)

```sql
mysql> select address from student;
+----------+
| address  |
+----------+
| Nashik   |
| Nashik   |
| pune     |
| Nashik   |
| Nashik   |
| vadgoan  |
| vadgoan  |
| Delhi    |
| Banglore |
| Mumbai   |
+----------+
10 rows in set (0.00 sec)

mysql> select DISTINCT address from student;
+----------+
| address  |
+----------+
| Nashik   |
| pune     |
| vadgoan  |
| Delhi    |
| Banglore |
| Mumbai   |
+----------+
6 rows in set (0.00 sec)

```

ORDER BY ascending sort

```sql
mysql> select * from student order by percentage;
+--------+----------+----------+------------+------------+-------------------------+
| rollno | name     | address  | percentage | contact    | email                   |
+--------+----------+----------+------------+------------+-------------------------+
|      3 | Omya     | pune     |      65.00 | 24364857   |                         |
|      1 | Kaustubh | Nashik   |      70.00 | 9834499607 | sonujadhav028@gmail.com |
|      9 | surti    | Banglore |      78.00 | 42820348   |                         |
|      4 | Umesh    | Nashik   |      80.00 | 24347397   |                         |
|      5 | Paresh   | Nashik   |      80.00 | 243483397  |                         |
|      6 | Duggu    | vadgoan  |      80.00 | 9856734    |                         |
|      7 | Sakshi   | vadgoan  |      80.00 | 9467734    |                         |
|     10 | swanand  | Mumbai   |      86.00 | 4282033848 |                         |
|      2 | Piyush   | Nashik   |      90.00 | 77996867   | iampiyush@gmail.com     |
|      8 | Palle    | Delhi    |      91.00 | 4229748    |                         |
|     11 | Arpita   | Culcata  |      96.00 | 24454848   |                         |
+--------+----------+----------+------------+------------+-------------------------+
11 rows in set (0.00 sec)
```

ORDER BY decending DESC

```sql
mysql> select * from student order by percentage desc;
+--------+----------+----------+------------+------------+-------------------------+
| rollno | name     | address  | percentage | contact    | email                   |
+--------+----------+----------+------------+------------+-------------------------+
|     11 | Arpita   | Culcata  |      96.00 | 24454848   |                         |
|      8 | Palle    | Delhi    |      91.00 | 4229748    |                         |
|      2 | Piyush   | Nashik   |      90.00 | 77996867   | iampiyush@gmail.com     |
|     10 | swanand  | Mumbai   |      86.00 | 4282033848 |                         |
|      4 | Umesh    | Nashik   |      80.00 | 24347397   |                         |
|      5 | Paresh   | Nashik   |      80.00 | 243483397  |                         |
|      6 | Duggu    | vadgoan  |      80.00 | 9856734    |                         |
|      7 | Sakshi   | vadgoan  |      80.00 | 9467734    |                         |
|      9 | surti    | Banglore |      78.00 | 42820348   |                         |
|      1 | Kaustubh | Nashik   |      70.00 | 9834499607 | sonujadhav028@gmail.com |
|      3 | Omya     | pune     |      65.00 | 24364857   |                         |
+--------+----------+----------+------------+------------+-------------------------+
11 rows in set (0.00 sec)
```

TOP 5 student

```sql
mysql> select * from student order by percentage desc limit 5;
+--------+---------+---------+------------+------------+---------------------+
| rollno | name    | address | percentage | contact    | email               |
+--------+---------+---------+------------+------------+---------------------+
|     11 | Arpita  | Culcata |      96.00 | 24454848   |                     |
|      8 | Palle   | Delhi   |      91.00 | 4229748    |                     |
|      2 | Piyush  | Nashik  |      90.00 | 77996867   | iampiyush@gmail.com |
|     10 | swanand | Mumbai  |      86.00 | 4282033848 |                     |
|      4 | Umesh   | Nashik  |      80.00 | 24347397   |                     |
+--------+---------+---------+------------+------------+---------------------+
5 rows in set (0.00 sec)
```

GROUP BY (give record summary) create group

Aggregate function 

(sum,min,max,avg,count)

COUNT

```sql
mysql> select address,count(*)from student GROUP BY address;
+----------+----------+
| address  | count(*) |
+----------+----------+
| Nashik   |        4 |
| pune     |        1 |
| vadgoan  |        2 |
| Delhi    |        1 |
| Banglore |        1 |
| Mumbai   |        1 |
| Culcata  |        1 |
+----------+----------+
7 rows in set (0.01 sec)
```

ALIAS temparary name;

```sql
mysql> select address,count(*)AS 'total address' from student GROUP BY address;
+----------+---------------+
| address  | total address |
+----------+---------------+
| Nashik   |             4 |
| pune     |             1 |
| vadgoan  |             2 |
| Delhi    |             1 |
| Banglore |             1 |
| Mumbai   |             1 |
| Culcata  |             1 |
+----------+---------------+
7 rows in set (0.00 sec)

select dept, MAX(salary) AS 'MAX SAl' from employee GROUP BY dept;

```

MAX and MIN

```sql
select address,MAX(percentage)AS 'MAX MARKS' from student GROUP BY address;
+----------+-----------+
| address  | MAX MARKS |
+----------+-----------+
| Nashik   |     90.00 |
| pune     |     65.00 |
| vadgoan  |     80.00 |
| Delhi    |     91.00 |
| Banglore |     78.00 |
| Mumbai   |     86.00 |
| Culcata  |     96.00 |
+----------+-----------+
7 rows in set (0.00 sec)


select dept,MAX(salary) AS 'MAX SAL' ,MIN(salary) AS 'MIN SAL' from eployee GROUP BY dept;
```

SUM

```sql
select dept,sum(salary) AS 'TOTAL sal' from employee group by dept;
```

USE WHERE when condition on row

HAVING is to give condition on group

```sql
select dept,sum(salary) AS 'TOTAL SAL' from emplyee group by dept having sum(salary)>=60000;
```

![[Pasted image 20230720135308.png]]

```sql
select dept,sum(salary) AS 'TOTAL SAL' from emplyee group by dept having sum(salary)>=60000 order by dept; 
```

![[Pasted image 20230720135906.png]]

USE like
name started with p 
p% use to show that starting letter is p


```sql
mysql> select * from student where name like 'p%';
+--------+--------+---------+------------+-----------+
| rollno | name   | address | percentage | contact   |
+--------+--------+---------+------------+-----------+
|      2 | Piyush | Nashik  |      90.00 | 77996867  |
|      5 | Paresh | Nashik  |      80.00 | 243483397 |
|      8 | Palle  | Delhi   |      91.00 | 4229748   |
+--------+--------+---------+------------+-----------+
3 rows in set (0.00 sec)

```

start with p and end with h 

```sql
mysql> select * from student where name like 'p%h';
+--------+--------+---------+------------+-----------+
| rollno | name   | address | percentage | contact   |
+--------+--------+---------+------------+-----------+
|      2 | Piyush | Nashik  |      90.00 | 77996867  |
|      5 | Paresh | Nashik  |      80.00 | 243483397 |
+--------+--------+---------+------------+-----------+
2 rows in set (0.00 sec)
```

name started with p and s

```sql
mysql> select * from student where name like 'p%' OR name like 's%';
+--------+---------+----------+------------+------------+
| rollno | name    | address  | percentage | contact    |
+--------+---------+----------+------------+------------+
|      2 | Piyush  | Nashik   |      90.00 | 77996867   |
|      5 | Paresh  | Nashik   |      80.00 | 243483397  |
|      7 | Sakshi  | vadgoan  |      80.00 | 9467734    |
|      8 | Palle   | Delhi    |      91.00 | 4229748    |
|      9 | surti   | Banglore |      78.00 | 42820348   |
|     10 | swanand | Mumbai   |      86.00 | 4282033848 |
+--------+---------+----------+------------+------------+
6 rows in set (0.00 sec)
```

![[Pasted image 20230720141031.png]]

```sql
select * from student where contact IS NULL;
select * from student where contact IS NOT NULL;
```

```sql
mysql> select * from student where contact is not null;
+--------+----------+----------+------------+------------+
| rollno | name     | address  | percentage | contact    |
+--------+----------+----------+------------+------------+
|      1 | Kaustubh | Nashik   |      70.00 | 9834499607 |
|      2 | Piyush   | Nashik   |      90.00 | 77996867   |
|      3 | Omya     | pune     |      65.00 | 24364857   |
|      4 | Umesh    | Nashik   |      80.00 | 24347397   |
|      5 | Paresh   | Nashik   |      80.00 | 243483397  |
|      6 | Duggu    | vadgoan  |      80.00 | 9856734    |
|      7 | Sakshi   | vadgoan  |      80.00 | 9467734    |
|      9 | surti    | Banglore |      78.00 | 42820348   |
|     10 | swanand  | Mumbai   |      86.00 | 4282033848 |
|     11 | Arpita   | Culcata  |      96.00 | 24454848   |
+--------+----------+----------+------------+------------+
10 rows in set (0.00 sec)

mysql> select * from student where contact is null;
+--------+-------+---------+------------+---------+
| rollno | name  | address | percentage | contact |
+--------+-------+---------+------------+---------+
|      8 | Palle | Delhi   |      91.00 | NULL    |
+--------+-------+---------+------------+---------+
1 row in set (0.00 sec)
```


```sql
select * from employee where salary between 30000 AND 50000;
select * from employee where salary > 30000 and salary <50000;
```

![[Pasted image 20230720142849.png]]

