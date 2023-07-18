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


