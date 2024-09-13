
mysql> CREATE DATABASE 55;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '55' at line 1
mysql> CREATE DATABASE MEGHANA;
ERROR 1007 (HY000): Can't create database 'meghana'; database exists
mysql> USE MEGHANA;
Database changed
mysql>  CREATE TABLE STUDENT(STD INT PRIMARY KEY,SNAME VARCHAR(20),MAJOR VARCHAR(10),LEVEL VARCHAR(10),AGE INT,DOB DATE,ADDRESS VARCHAR(20));
ERROR 1050 (42S01): Table 'student' already exists
mysql> ALTER TABLE STUDENT DROP COLUMN LEVEL;
Query OK, 0 rows affected (0.78 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql>  CREATE TABLE STUDENT(STD INT PRIMARY KEY,SNAME VARCHAR(20),MAJOR VARCHAR(10),LEVEL VARCHAR(10),AGE INT,DOB DATE,ADDRESS VARCHAR(20));
ERROR 1050 (42S01): Table 'student' already exists
mysql>  DESC STUDENT;
+---------+-------------+------+-----+---------+-------+
| Field   | Type        | Null | Key | Default | Extra |
+---------+-------------+------+-----+---------+-------+
| STD     | int         | NO   | PRI | NULL    |       |
| SNAME   | varchar(20) | YES  |     | NULL    |       |
| MAJOR   | varchar(10) | YES  |     | NULL    |       |
| AGE     | int         | YES  |     | NULL    |       |
| DOB     | date        | YES  |     | NULL    |       |
| ADDRESS | varchar(20) | YES  |     | NULL    |       |
| MARKS   | float       | YES  |     | NULL    |       |
+---------+-------------+------+-----+---------+-------+
7 rows in set (0.31 sec)

mysql> CREATE TABLE FACULTY(FID INT PRIMARY KEY,FNAME VARCHAR(10),DEPTID INT,ADDRESS VARCHAR(20));
ERROR 1050 (42S01): Table 'faculty' already exists
mysql> DESC FACULTY;
+---------+-------------+------+-----+---------+-------+
| Field   | Type        | Null | Key | Default | Extra |
+---------+-------------+------+-----+---------+-------+
| FID     | int         | NO   | PRI | NULL    |       |
| FNAME   | varchar(10) | YES  |     | NULL    |       |
| DEPTID  | int         | YES  |     | NULL    |       |
| ADDRESS | varchar(20) | YES  |     | NULL    |       |
+---------+-------------+------+-----+---------+-------+
4 rows in set (0.00 sec)

mysql> CREATE TABLE COURSE(CNAME VARCHAR(10)PRIMARY KEY,MEETS_AT VARCHAR(10),ROOM VARCHAR(5),FID INT,FOREIGN KEY(FID)REFERENCES FACULTY(FID)ON DELETE CASCADE);
ERROR 1050 (42S01): Table 'course' already exists
mysql>  DESC FACULTY;
+---------+-------------+------+-----+---------+-------+
| Field   | Type        | Null | Key | Default | Extra |
+---------+-------------+------+-----+---------+-------+
| FID     | int         | NO   | PRI | NULL    |       |
| FNAME   | varchar(10) | YES  |     | NULL    |       |
| DEPTID  | int         | YES  |     | NULL    |       |
| ADDRESS | varchar(20) | YES  |     | NULL    |       |
+---------+-------------+------+-----+---------+-------+
4 rows in set (0.00 sec)

mysql> DESC COURSE;
+----------+-------------+------+-----+---------+-------+
| Field    | Type        | Null | Key | Default | Extra |
+----------+-------------+------+-----+---------+-------+
| CNAME    | varchar(10) | NO   | PRI | NULL    |       |
| MEETS_AT | varchar(10) | YES  |     | NULL    |       |
| ROOM     | varchar(5)  | YES  |     | NULL    |       |
| FID      | int         | YES  | MUL | NULL    |       |
+----------+-------------+------+-----+---------+-------+
4 rows in set (0.00 sec)

mysql>  INSERT INTO STUDENT(STD,SNAME,MAJOR,LEVEL,AGE,DOB,ADDRESS)VALUES
    ->      (101,'ALPHA','CSE','JR',20,'2000-12-01','BANGLORE'),
    ->      (102,'GAMMA','CSE','SR',20,'2000-12-02','DELHI');
ERROR 1054 (42S22): Unknown column 'LEVEL' in 'field list'
mysql> INSERT INTO STUDENT(STD,SNAME,MAJOR,LEVEL,AGE,DOB,ADDRESS)VALUES
    -> (101,'ALPHA','CSE','JR',20,'2000-12-01','BANGLORE'),
    ->      (102,'GAMMA','CSE','SR',20,'2000-12-02','DELHI');
ERROR 1054 (42S22): Unknown column 'LEVEL' in 'field list'
mysql> DESC STUDENT;
+---------+-------------+------+-----+---------+-------+
| Field   | Type        | Null | Key | Default | Extra |
+---------+-------------+------+-----+---------+-------+
| STD     | int         | NO   | PRI | NULL    |       |
| SNAME   | varchar(20) | YES  |     | NULL    |       |
| MAJOR   | varchar(10) | YES  |     | NULL    |       |
| AGE     | int         | YES  |     | NULL    |       |
| DOB     | date        | YES  |     | NULL    |       |
| ADDRESS | varchar(20) | YES  |     | NULL    |       |
| MARKS   | float       | YES  |     | NULL    |       |
+---------+-------------+------+-----+---------+-------+
7 rows in set (0.00 sec)

mysql>  INSERT INTO COURSE(CNAME,MEETS_AT,ROOM,FID)VALUES
    -> ('ENG','9.00','RF01',10),
    ->      ('BIO','10.00','RF02',20),
    ->      ('MATH','11.00','RF03',30);
ERROR 1062 (23000): Duplicate entry 'ENG' for key 'course.PRIMARY'
mysql> ('ENG','9.00','RF01',10),
    ->      ('BIO','10.00','RF02',20),
    ->      ('MATH','11.00','RF03',30);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ''ENG','9.00','RF01',10),
     ('BIO','10.00','RF02',20),
     ('MATH','11.00','R' at line 1
mysql>  SELECT *FROM ENROLLED;
ERROR 1146 (42S02): Table 'meghana.enrolled' doesn't exist
mysql> INSERT INTO ENROLLED (SID,CNAME) VALUES
    -> ('ENG','9.00','RF01',10),
    ->      ('BIO','10.00','RF02',20),
    ->      ('MATH','11.00','RF03',30);
ERROR 1146 (42S02): Table 'meghana.enrolled' doesn't exist
mysql> INSERT INTO ENROLLMENT (SID,CNAME) VALUES
    -> ('ENG','9.00','RF01',10),
    ->      ('BIO','10.00','RF02',20),
    ->      ('MATH','11.00','RF03',30);
ERROR 1054 (42S22): Unknown column 'SID' in 'field list'
mysql> INSERT INTO ENROLLMENT (STD,CNAME) VALUES
    -> ('ENG','9.00','RF01',10),
    ->      ('BIO','10.00','RF02',20),
    ->      ('MATH','11.00','RF03',30);
ERROR 1136 (21S01): Column count doesn't match value count at row 1
mysql> SHOW TABLES;
+-------------------+
| Tables_in_meghana |
+-------------------+
| course            |
| enrollment        |
| faculty           |
| student           |
+-------------------+
4 rows in set (0.12 sec)

mysql> SELECT *FROM COURSE;
+-------+----------+------+------+
| CNAME | MEETS_AT | ROOM | FID  |
+-------+----------+------+------+
| BIO   | 10.00    | RF02 |   20 |
| ENG   | 9.00     | RF01 |   10 |
| MATH  | 11.00    | RF03 |   30 |
+-------+----------+------+------+
3 rows in set (0.00 sec)

mysql> SELECT AVG(FEES) AS 'AVERAGE FEES' FROM STUDENT;
ERROR 1054 (42S22): Unknown column 'FEES' in 'field list'
mysql> SELECT SUM(FEES)AS'SUM'FROM STUDENT;
ERROR 1054 (42S22): Unknown column 'FEES' in 'field list'
mysql>  CREATE TABLE ENROLLED(SID INT,
    ->      CNAME VARCHAR(10),
    -> ^C
mysql> CREATE TABLE ENROLLMENT(STD INT,CNAME VARCHAR(10);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '' at line 1
mysql> CREATE TABLE ENROLLMENT(STD INT,CNAME VARCHAR(10));
ERROR 1050 (42S01): Table 'enrollment' already exists
mysql> INSERT INTO ENROLLMENT (STD,CNAME) VALUES
    -> ('ENG','9.00','RF01',10),
    ->      ('BIO','10.00','RF02',20),
    ->      ('MATH','11.00','RF03',30);
ERROR 1136 (21S01): Column count doesn't match value count at row 1
mysql> CREATE TABLE ENROLL,ENT(SID INT,
    ->      CNAME VARCHAR(10),
    ->      FOREIGN KEY(SID) REFERENCES STUDENT (SID) ON DELETE CASCADE,
    ->      FOREIGN KEY(CNAME) REFERENCES COURSE (CNAME) ON DELETE CASCADE);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ',ENT(SID INT,
     CNAME VARCHAR(10),
     FOREIGN KEY(SID) REFERENCES STUDENT (' at line 1
mysql> CREATE TABLE ENROLLMENT(SID INT,
    ->      CNAME VARCHAR(10),
    ->      FOREIGN KEY(SID) REFERENCES STUDENT (SID) ON DELETE CASCADE,
    ->      FOREIGN KEY(CNAME) REFERENCES COURSE (CNAME) ON DELETE CASCADE);
ERROR 1050 (42S01): Table 'enrollment' already exists
mysql>  INSERT INTO ENROLLMENT(SID,CNAME) VALUES
    -> ('ENG','9.00','RF01',10),
    ->      ('BIO','10.00','RF02',20),
    ->      ('MATH','11.00','RF03',30);
ERROR 1054 (42S22): Unknown column 'SID' in 'field list'
mysql> INSERT INTO ENROLLMENT (STD,CNAME) VALUES
    -> ('ENG','9.00','RF01',10),
    ->      ('BIO','10.00','RF02',20),
    ->      ('MATH','11.00','RF03',30);
ERROR 1136 (21S01): Column count doesn't match value count at row 1
mysql> SELECT *FROM ENROLLMENT;
Empty set (0.04 sec)

mysql> SELECT count(*) AS"TOTAL NO.OF RECORDS"FROM STUDENT WHERE STD=101;
+---------------------+
| TOTAL NO.OF RECORDS |
+---------------------+
|                   1 |
+---------------------+
1 row in set (0.07 sec)

mysql> SELECT count(*) AS"TOTAL NO.OF RECORDS"FROM STUDENT;
+---------------------+
| TOTAL NO.OF RECORDS |
+---------------------+
|                   2 |
+---------------------+
1 row in set (0.08 sec)

mysql>  ALTER TABLE STUDENT ADD MARKS FLOAT;
ERROR 1060 (42S21): Duplicate column name 'MARKS'
mysql>  SELECT SID,SNAME FROM STUDENT;
ERROR 1054 (42S22): Unknown column 'SID' in 'field list'
mysql> SELECT STD,SNAME FROM STUDENT;
+-----+-------+
| STD | SNAME |
+-----+-------+
| 101 | ALPHA |
| 102 | GAMMA |
+-----+-------+
2 rows in set (0.00 sec)

mysql> SELECT SNAME,DOB FROM STUDENT WHERE STD=101;
+-------+------------+
| SNAME | DOB        |
+-------+------------+
| ALPHA | 2000-12-01 |
+-------+------------+
1 row in set (0.00 sec)

mysql> SELECT count(*) AS"TOTAL NO.OF RECORDS"FROM STUDENT;
+---------------------+
| TOTAL NO.OF RECORDS |
+---------------------+
|                   2 |
+---------------------+
1 row in set (0.00 sec)

mysql> ALTER TABLE STUDENT ADD MARKS FLOAT;
ERROR 1060 (42S21): Duplicate column name 'MARKS'
mysql> UPDATE TABLE STUDENT SET MARKS=85 WHERE STD=2;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'TABLE STUDENT SET MARKS=85 WHERE STD=2' at line 1
mysql> UPDATE TABLE STUDENT SET MARKS;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'TABLE STUDENT SET MARKS' at line 1
mysql> ALTER TABLE STUDENT ADD MARKS FLOAT;
ERROR 1060 (42S21): Duplicate column name 'MARKS'
mysql>  DESC STUDENT;
+---------+-------------+------+-----+---------+-------+
| Field   | Type        | Null | Key | Default | Extra |
+---------+-------------+------+-----+---------+-------+
| STD     | int         | NO   | PRI | NULL    |       |
| SNAME   | varchar(20) | YES  |     | NULL    |       |
| MAJOR   | varchar(10) | YES  |     | NULL    |       |
| AGE     | int         | YES  |     | NULL    |       |
| DOB     | date        | YES  |     | NULL    |       |
| ADDRESS | varchar(20) | YES  |     | NULL    |       |
| MARKS   | float       | YES  |     | NULL    |       |
+---------+-------------+------+-----+---------+-------+
7 rows in set (0.00 sec)

mysql> UPDATE STUDENT SET MARKS=88.5 WHERE STD=101;
Query OK, 1 row affected (0.10 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql>  UPDATE STUDENT SET MARKS=92.5 WHERE STD=102;
Query OK, 1 row affected (0.02 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql>  SELECT *FROM STUDENT;
+-----+-------+-------+------+------------+----------+-------+
| STD | SNAME | MAJOR | AGE  | DOB        | ADDRESS  | MARKS |
+-----+-------+-------+------+------------+----------+-------+
| 101 | ALPHA | CSE   |   20 | 2000-12-01 | BANGLORE |  88.5 |
| 102 | GAMMA | CSE   |   20 | 2000-12-02 | DELHI    |  92.5 |
+-----+-------+-------+------+------------+----------+-------+
2 rows in set (0.00 sec)

mysql> SELECT STD,SNAME,MARKS FROM STUDENT;
+-----+-------+-------+
| STD | SNAME | MARKS |
+-----+-------+-------+
| 101 | ALPHA |  88.5 |
| 102 | GAMMA |  92.5 |
+-----+-------+-------+
2 rows in set (0.00 sec)

mysql>  SELECT SNAME,(MARKS/100)*100 AS PERCENTAGE FROM STUDENT WHERE STD>102;
Empty set (0.02 sec)

mysql> SELECT DISTINCT SNAME FROM STUDENT;
+-------+
| SNAME |
+-------+
| ALPHA |
| GAMMA |
+-------+
2 rows in set (0.00 sec)

mysql> SELECT SID,SNAME FROM STUDENT WHERE STD BETWEEN 101 AND 102;
ERROR 1054 (42S22): Unknown column 'SID' in 'field list'
mysql> SELECT STD,SNAME FROM STUDENT WHERE STD BETWEEN 101 AND 102;
+-----+-------+
| STD | SNAME |
+-----+-------+
| 101 | ALPHA |
| 102 | GAMMA |
+-----+-------+
2 rows in set (0.00 sec)

mysql> ALTER TABLE STUDENT ADD FEES INT DEFAULT 30000;
Query OK, 0 rows affected (0.37 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql>  ALTER TABLE STUDENT ADD EMAIL VARCHAR(30) DEFAULT 'someone@gmail.com';ALTER TABLE STUDENT ADD FEES INT DEFAULT 30000;
Query OK, 0 rows affected (0.16 sec)
Records: 0  Duplicates: 0  Warnings: 0

ERROR 1060 (42S21): Duplicate column name 'FEES'
mysql>  ALTER TABLE STUDENT ADD EMAIL VARCHAR(30) DEFAULT 'someone@gmail.com';
ERROR 1060 (42S21): Duplicate column name 'EMAIL'
mysql> UPDATE STUDENT SET FEES = 30000 WHERE STD=101;
Query OK, 0 rows affected (0.00 sec)
Rows matched: 1  Changed: 0  Warnings: 0

mysql> UPDATE STUDENT SET FEES = 30000 WHERE STD=102;
Query OK, 0 rows affected (0.00 sec)
Rows matched: 1  Changed: 0  Warnings: 0

mysql>  UPDATE STUDENT SET EMAIL = "abhi@gmail.com" WHERE STD=101;
Query OK, 1 row affected (0.10 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql>  UPDATE STUDENT SET EMAIL = "adya12@gmail.com" WHERE STD=102;
Query OK, 1 row affected (0.01 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql>  SELECT *FROM student;
+-----+-------+-------+------+------------+----------+-------+-------+------------------+
| STD | SNAME | MAJOR | AGE  | DOB        | ADDRESS  | MARKS | FEES  | EMAIL            |
+-----+-------+-------+------+------------+----------+-------+-------+------------------+
| 101 | ALPHA | CSE   |   20 | 2000-12-01 | BANGLORE |  88.5 | 30000 | abhi@gmail.com   |
| 102 | GAMMA | CSE   |   20 | 2000-12-02 | DELHI    |  92.5 | 30000 | adya12@gmail.com |
+-----+-------+-------+------+------------+----------+-------+-------+------------------+
2 rows in set (0.00 sec)

mysql>  SELECT AVG(MARKS) AS 'AVERAGE MARKS' FROM STUDENT;
+---------------+
| AVERAGE MARKS |
+---------------+
|          90.5 |
+---------------+
1 row in set (0.00 sec)

mysql>  SELECT AVG(FEES) AS 'AVERAGE FEES' FROM STUDENT;
+--------------+
| AVERAGE FEES |
+--------------+
|   30000.0000 |
+--------------+
1 row in set (0.00 sec)

mysql>  SELECT SNAME FROM STUDENT WHERE FEES BETWEEN 25000 AND 30000;
+-------+
| SNAME |
+-------+
| ALPHA |
| GAMMA |
+-------+
2 rows in set (0.00 sec)

mysql>  SELECT SNAME,FEES FROM STUDENT WHERE FEES BETWEEN 25000 AND 30000;
+-------+-------+
| SNAME | FEES  |
+-------+-------+
| ALPHA | 30000 |
| GAMMA | 30000 |
+-------+-------+
2 rows in set (0.00 sec)

mysql> SELECT SNAME FROM STUDENT WHERE EMAIL LIKE "%GMAIL.COM";
+-------+
| SNAME |
+-------+
| ALPHA |
| GAMMA |
+-------+
2 rows in set (0.03 sec)

mysql>  SELECT UPPER(SNAME) AS 'UPPERCASE' FROM STUDENT;
+-----------+
| UPPERCASE |
+-----------+
| ALPHA     |
| GAMMA     |
+-----------+
2 rows in set (0.00 sec)

mysql>  SELECT UPPER(SNAME) AS 'LOWERCASE' FROM STUDENT;
+-----------+
| LOWERCASE |
+-----------+
| ALPHA     |
| GAMMA     |
+-----------+
2 rows in set (0.00 sec)

mysql> SELECT LOWER(SNAME) AS 'LOWERCASE' FROM STUDENT;
+-----------+
| LOWERCASE |
+-----------+
| alpha     |
| gamma     |
+-----------+
2 rows in set (0.02 sec)

mysql>  UPDATE STUDENT SET FEES = FEES*1.1;
Query OK, 2 rows affected (0.35 sec)
Rows matched: 2  Changed: 2  Warnings: 0

mysql> SELECT SNAME FROM STUDENT WHERE EMAIL IS NOT NULL;
+-------+
| SNAME |
+-------+
| ALPHA |
| GAMMA |
+-------+
2 rows in set (0.00 sec)

mysql> SELECT(FEES)AS'SUM'FROM STUDENT;
+-------+
| SUM   |
+-------+
| 33000 |
| 33000 |
+-------+
2 rows in set (0.00 sec)

mysql> SELECT ASCII('A');
+------------+
| ASCII('A') |
+------------+
|         65 |
+------------+
1 row in set (0.02 sec)

mysql> SELECT LENGTH(FEES)FROM STUDENT;
+--------------+
| LENGTH(FEES) |
+--------------+
|            5 |
|            5 |
+--------------+
2 rows in set (0.00 sec)

mysql> SELECT LENGTH(SNAME)FROM STUDENT;
+---------------+
| LENGTH(SNAME) |
+---------------+
|             5 |
|             5 |
+---------------+
2 rows in set (0.00 sec)

mysql> SELECT REVERSE(SNAME)FROM STUDENT;
+----------------+
| REVERSE(SNAME) |
+----------------+
| AHPLA          |
| AMMAG          |
+----------------+
2 rows in set (0.01 sec)

mysql> SELECT LEFT(SNAME,4)FROM STUDENT;
+---------------+
| LEFT(SNAME,4) |
+---------------+
| ALPH          |
| GAMM          |
+---------------+
2 rows in set (0.00 sec)

mysql> SELECT RIGHT(SNAME,5)FROM STUDENT;
+----------------+
| RIGHT(SNAME,5) |
+----------------+
| ALPHA          |
| GAMMA          |
+----------------+
2 rows in set (0.00 sec)

mysql> SELECT NOW();
+---------------------+
| NOW()               |
+---------------------+
| 2024-09-13 10:02:34 |
+---------------------+
1 row in set (0.03 sec)

mysql> SELECT SYSDATE();
+---------------------+
| SYSDATE()           |
+---------------------+
| 2024-09-13 10:02:46 |
+---------------------+
1 row in set (0.00 sec)

mysql> SELECT*FROM STUDENT WHERE MAJOR NOT IN("CSE");
Empty set (0.00 sec)

mysql> SELECT*FROM STUDENT WHERE MAJOR NOT IN("CSE");
Empty set (0.00 sec)

mysql> SELECT *FROM STUDENT;
+-----+-------+-------+------+------------+----------+-------+-------+------------------+
| STD | SNAME | MAJOR | AGE  | DOB        | ADDRESS  | MARKS | FEES  | EMAIL            |
+-----+-------+-------+------+------------+----------+-------+-------+------------------+
| 101 | ALPHA | CSE   |   20 | 2000-12-01 | BANGLORE |  88.5 | 33000 | abhi@gmail.com   |
| 102 | GAMMA | CSE   |   20 | 2000-12-02 | DELHI    |  92.5 | 33000 | adya12@gmail.com |
+-----+-------+-------+------+------------+----------+-------+-------+------------------+
2 rows in set (0.00 sec)

mysql> ALTER TABLE STUDENT MODIFY MAJOR;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '' at line 1
mysql> ALTER TABLE STUDENT UPDATE MAJOR = "ISE" WHERE STD=102;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'UPDATE MAJOR = "ISE" WHERE STD=102' at line 1
mysql> ALTER TABLE STUDENT MODIFY MAJOR = "ISE" WHERE STD=102;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '= "ISE" WHERE STD=102' at line 1
mysql> UPDATE TABLE STUDENT MODIFY MAJOR = "ISE" WHERE STD=102;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'TABLE STUDENT MODIFY MAJOR = "ISE" WHERE STD=102' at line 1
mysql> UPDATE TABLE STUDENT^CODIFY MAJOR = "ISE" WHERE STD=102;
mysql> UPDATE STUDENT SET MAJOR="ISE" WHERE STD=102;
Query OK, 1 row affected (0.19 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql>  SELECT*FROM STUDENT WHERE MAJOR NOT IN("CSE");
+-----+-------+-------+------+------------+---------+-------+-------+------------------+
| STD | SNAME | MAJOR | AGE  | DOB        | ADDRESS | MARKS | FEES  | EMAIL            |
+-----+-------+-------+------+------------+---------+-------+-------+------------------+
| 102 | GAMMA | ISE   |   20 | 2000-12-02 | DELHI   |  92.5 | 33000 | adya12@gmail.com |
+-----+-------+-------+------+------------+---------+-------+-------+------------------+
1 row in set (0.00 sec)

mysql> ^C
mysql>  UPDATE STUDENT SET EMAIL = "SOMEONE.com" WHERE STD=101;
Query OK, 1 row affected (0.05 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql>  SELECT*FROM STUDENT WHERE MAJOR NOT IN("CSE");
+-----+-------+-------+------+------------+---------+-------+-------+------------------+
| STD | SNAME | MAJOR | AGE  | DOB        | ADDRESS | MARKS | FEES  | EMAIL            |
+-----+-------+-------+------+------------+---------+-------+-------+------------------+
| 102 | GAMMA | ISE   |   20 | 2000-12-02 | DELHI   |  92.5 | 33000 | adya12@gmail.com |
+-----+-------+-------+------+------------+---------+-------+-------+------------------+
1 row in set (0.00 sec)

mysql>  UPDATE STUDENT SET EMAIL = "ABC.com" WHERE STD=102;
Query OK, 1 row affected (0.02 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql>   SELECT*FROM STUDENT WHERE MAJOR NOT IN("CSE");
+-----+-------+-------+------+------------+---------+-------+-------+---------+
| STD | SNAME | MAJOR | AGE  | DOB        | ADDRESS | MARKS | FEES  | EMAIL   |
+-----+-------+-------+------+------------+---------+-------+-------+---------+
| 102 | GAMMA | ISE   |   20 | 2000-12-02 | DELHI   |  92.5 | 33000 | ABC.com |
+-----+-------+-------+------+------------+---------+-------+-------+---------+
1 row in set (0.00 sec)
