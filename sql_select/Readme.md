1.
mysql> select first_name, last_name from student;
+------------+-----------+
| first_name | last_name |
+------------+-----------+
| Eric       | Ephram    |
| Greg       | Gould     |
| Adam       | Ant       |
| Howard     | Hess      |
| Charles    | Caldwell  |
| James      | Joyce     |
| Doug       | Dumas     |
| Kevin      | Kraft     |
| Frank      | Fountain  |
| Brian      | Biggs     |
+------------+-----------+
10 rows in set (0.00 sec)

mysql>

2.
mysql> select * from student where years_of_experience < 8;
+------------+------------+-----------+---------------------+------------+
| student_id | first_name | last_name | years_of_experience | start_date |
+------------+------------+-----------+---------------------+------------+
|          1 | Eric       | Ephram    |                   2 | 2016-03-31 |
|          2 | Greg       | Gould     |                   6 | 2016-09-30 |
|          3 | Adam       | Ant       |                   5 | 2016-06-02 |
|          4 | Howard     | Hess      |                   1 | 2016-02-28 |
|          5 | Charles    | Caldwell  |                   7 | 2016-05-07 |
|          8 | Kevin      | Kraft     |                   3 | 2016-04-15 |
|         10 | Brian      | Biggs     |                   4 | 2015-12-25 |
+------------+------------+-----------+---------------------+------------+
7 rows in set (0.01 sec)

3.
mysql> select last_name, start_date, student_id from student order by last_name asc;
+-----------+------------+------------+
| last_name | start_date | student_id |
+-----------+------------+------------+
| Ant       | 2016-06-02 |          3 |
| Biggs     | 2015-12-25 |         10 |
| Caldwell  | 2016-05-07 |          5 |
| Dumas     | 2016-07-04 |          7 |
| Ephram    | 2016-03-31 |          1 |
| Fountain  | 2016-01-31 |          9 |
| Gould     | 2016-09-30 |          2 |
| Hess      | 2016-02-28 |          4 |
| Joyce     | 2016-08-27 |          6 |
| Kraft     | 2016-04-15 |          8 |
+-----------+------------+------------+
10 rows in set (0.00 sec)

4.
mysql> select * from student where first_name = 'Adam' or first_name = 'James' or first_name = 'Frank' order by last_name desc;
+------------+------------+-----------+---------------------+------------+
| student_id | first_name | last_name | years_of_experience | start_date |
+------------+------------+-----------+---------------------+------------+
|          6 | James      | Joyce     |                   9 | 2016-08-27 |
|          9 | Frank      | Fountain  |                   8 | 2016-01-31 |
|          3 | Adam       | Ant       |                   5 | 2016-06-02 |
+------------+------------+-----------+---------------------+------------+
3 rows in set (0.00 sec)

5.
mysql> select first_name, last_name, start_date from student where start_date between "2016-01-01" and "2016-06-30";
+------------+-----------+------------+
| first_name | last_name | start_date |
+------------+-----------+------------+
| Eric       | Ephram    | 2016-03-31 |
| Adam       | Ant       | 2016-06-02 |
| Howard     | Hess      | 2016-02-28 |
| Charles    | Caldwell  | 2016-05-07 |
| Kevin      | Kraft     | 2016-04-15 |
| Frank      | Fountain  | 2016-01-31 |
+------------+-----------+------------+
6 rows in set (0.00 sec)

Medium


mysql> Explain assignment
    -> ;
+----------------+------------------+------+-----+---------+----------------+
| Field          | Type             | Null | Key | Default | Extra          |
+----------------+------------------+------+-----+---------+----------------+
| assignment_id  | int(11) unsigned | NO   | PRI | NULL    | auto_increment |
| student_id     | int(11)          | NO   |     | NULL    |                |
| assignment_nbr | int(11)          | NO   |     | NULL    |                |
| class_id       | int(11)          | YES  |     | NULL    |                |
| grade_id       | int(11) unsigned | YES  | MUL | NULL    |                |
+----------------+------------------+------+-----+---------+----------------+
5 rows in set (0.00 sec)

mysql>



mysql> select * from assignment;
+---------------+------------+----------------+----------+----------+
| assignment_id | student_id | assignment_nbr | class_id | grade_id |
+---------------+------------+----------------+----------+----------+
|             5 |        100 |            200 |      200 |        1 |
|             6 |        200 |            300 |      300 |        2 |
|             7 |        300 |            400 |      400 |        3 |
|             8 |        400 |            500 |      500 |        4 |
|             9 |        500 |            600 |      600 |        5 |
+---------------+------------+----------------+----------+----------+
5 rows in set (0.00 sec)


mysql> Explain grade;
+----------+------------------+------+-----+---------+----------------+
| Field    | Type             | Null | Key | Default | Extra          |
+----------+------------------+------+-----+---------+----------------+
| grade_id | int(11) unsigned | NO   | PRI | NULL    | auto_increment |
| grade    | varchar(255)     | YES  |     | NULL    |                |
+----------+------------------+------+-----+---------+----------------+
2 rows in set (0.00 sec)


mysql> select * from grade;
+----------+-----------------------------+
| grade_id | grade                       |
+----------+-----------------------------+
|        1 | Incomplete                  |
|        2 | Complete and unsatisfactory |
|        3 | Complete and satisfactory   |
|        4 | Exceeds expectations        |
|        5 | Not graded                  |
+----------+-----------------------------+
5 rows in set (0.00 sec)

ALTER TABLE `assignment`
ADD CONSTRAINT `fk_student_number`
FOREIGN KEY (`student_id`) REFERENCES student(`student_id`);

Hard
mysql> ALTER TABLE `assignment`  ADD CONSTRAINT `fk_student_number` FOREIGN KEY (`student_id`) REFERENCES student(`student_id`);
Query OK, 5 rows affected (0.02 sec)
Records: 5  Duplicates: 0  Warnings: 0
