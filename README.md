# mysql_generate_series: generate_series for MySQL

mysql_generate_series is a MySQL replica of PostgreSQL's [Website](http://www.postgresql.org/docs/9.4/static/functions-srf.html) functions.

It offers 5 methods:
* generate_series(first, last): return a series from "first" to "last" with an increment of 1
* generate_series_n(first, last, n): return a series from "first" to "last" with an increment of "n"
* generate_series_date_minute(fisrt, last, n): return a series of datetime with an increment of "n" minutes
* generate_series_date_hour(fisrt, last, n): return a series of datetime with an increment of "n" hours
* generate_series_date_day(fisrt, last, n): return a series of datetime with an increment of "n" days

### Installation

* Install all methods from [sql/generate_series.sql](sql/generate_series.sql)
* Try it yourself with the examples below

### Examples

#### generate_series(first, last) examples

```sql
mysql> CALL generate_series(1, 10);
+--------+
| series |
+--------+
|      1 |
|      2 |
|      3 |
|      4 |
|      5 |
+--------+
10 rows in set (0.00 sec)

mysql> CALL generate_series(1000, 1004);
+--------+
| series |
+--------+
|   1000 |
|   1001 |
|   1002 |
|   1003 |
|   1004 |
+--------+
5 rows in set (0.00 sec)
```

#### generate_series_n(first, last, n) examples

```sql
mysql> CALL generate_series_n(0, 10, 2);
+--------+
| series |
+--------+
|      0 |
|      2 |
|      4 |
|      6 |
|      8 |
|     10 |
+--------+
6 rows in set (0.00 sec)
```

#### generate_series_date_minute(first, last, n) examples

```sql
mysql> CALL generate_series_date_minute('2015-09-03 00:00:00', '2015-09-03 00:20:00', 1);
+---------------------+
| series              |
+---------------------+
| 2015-09-03 00:00:00 |
| 2015-09-03 00:01:00 |
| 2015-09-03 00:02:00 |
| 2015-09-03 00:03:00 |
| 2015-09-03 00:04:00 |
| 2015-09-03 00:05:00 |
| 2015-09-03 00:06:00 |
| 2015-09-03 00:07:00 |
| 2015-09-03 00:08:00 |
| 2015-09-03 00:09:00 |
| 2015-09-03 00:10:00 |
| 2015-09-03 00:11:00 |
| 2015-09-03 00:12:00 |
| 2015-09-03 00:13:00 |
| 2015-09-03 00:14:00 |
| 2015-09-03 00:15:00 |
| 2015-09-03 00:16:00 |
| 2015-09-03 00:17:00 |
| 2015-09-03 00:18:00 |
| 2015-09-03 00:19:00 |
| 2015-09-03 00:20:00 |
+---------------------+
21 rows in set (0.00 sec)

mysql> CALL generate_series_date_minute('2015-09-03 00:00:00', '2015-09-03 00:20:00', 2);
+---------------------+
| series              |
+---------------------+
| 2015-09-03 00:00:00 |
| 2015-09-03 00:02:00 |
| 2015-09-03 00:04:00 |
| 2015-09-03 00:06:00 |
| 2015-09-03 00:08:00 |
| 2015-09-03 00:10:00 |
| 2015-09-03 00:12:00 |
| 2015-09-03 00:14:00 |
| 2015-09-03 00:16:00 |
| 2015-09-03 00:18:00 |
| 2015-09-03 00:20:00 |
+---------------------+
11 rows in set (0.01 sec)
```

#### generate_series_date_hour(first, last, n) examples

```sql
mysql> CALL generate_series_date_hour('2015-09-03', '2015-09-04', 1);
+---------------------+
| series              |
+---------------------+
| 2015-09-03 00:00:00 |
| 2015-09-03 01:00:00 |
| 2015-09-03 02:00:00 |
| 2015-09-03 03:00:00 |
| 2015-09-03 04:00:00 |
| 2015-09-03 05:00:00 |
| 2015-09-03 06:00:00 |
| 2015-09-03 07:00:00 |
| 2015-09-03 08:00:00 |
| 2015-09-03 09:00:00 |
| 2015-09-03 10:00:00 |
| 2015-09-03 11:00:00 |
| 2015-09-03 12:00:00 |
| 2015-09-03 13:00:00 |
| 2015-09-03 14:00:00 |
| 2015-09-03 15:00:00 |
| 2015-09-03 16:00:00 |
| 2015-09-03 17:00:00 |
| 2015-09-03 18:00:00 |
| 2015-09-03 19:00:00 |
| 2015-09-03 20:00:00 |
| 2015-09-03 21:00:00 |
| 2015-09-03 22:00:00 |
| 2015-09-03 23:00:00 |
| 2015-09-04 00:00:00 |
+---------------------+
25 rows in set (0.00 sec)

mysql> CALL generate_series_date_hour('2015-09-03 00:00:00', '2015-09-03 08:00:00', 1);
+---------------------+
| series              |
+---------------------+
| 2015-09-03 00:00:00 |
| 2015-09-03 01:00:00 |
| 2015-09-03 02:00:00 |
| 2015-09-03 03:00:00 |
| 2015-09-03 04:00:00 |
| 2015-09-03 05:00:00 |
| 2015-09-03 06:00:00 |
| 2015-09-03 07:00:00 |
| 2015-09-03 08:00:00 |
+---------------------+
9 rows in set (0.00 sec)
```

#### generate_series_date_day(first, last, n) examples

```sql
mysql> CALL generate_series_date_day('2015-09-03', '2015-09-05', 1);
+---------------------+
| series              |
+---------------------+
| 2015-09-03 00:00:00 |
| 2015-09-04 00:00:00 |
| 2015-09-05 00:00:00 |
+---------------------+
3 rows in set (0.00 sec)

mysql> CALL generate_series_date_day('2015-09-03 00:00:00', '2015-09-05 08:00:00', 1);
+---------------------+
| series              |
+---------------------+
| 2015-09-03 00:00:00 |
| 2015-09-04 00:00:00 |
| 2015-09-05 00:00:00 |
+---------------------+
3 rows in set (0.00 sec)
```

### Inserting in a table from a series

MySQL does not allow to insert in tables directly from a stored procedure.
mysql_generate_series uses a temporary table called "series_tmp" for every procedure which you can use to insert a series in a table, for example:

```sql
mysql> CREATE TABLE test (a int, b text);
Query OK, 0 rows affected (0.01 sec)

mysql> CALL generate_series(1, 10);
+--------+
| series |
+--------+
|      1 |
|      2 |
|      3 |
|      4 |
|      5 |
|      6 |
|      7 |
|      8 |
|      9 |
|     10 |
+--------+
10 rows in set (0.00 sec)
Query OK, 0 rows affected (0.00 sec)

mysql> INSERT INTO test (a, b) SELECT series, 'This is a test' FROM series_tmp;
Query OK, 10 rows affected (0.00 sec)
Records: 10  Duplicates: 0  Warnings: 0

mysql> SELECT * FROM test;
+------+----------------+
| a    | b              |
+------+----------------+
|    1 | This is a test |
|    2 | This is a test |
|    3 | This is a test |
|    4 | This is a test |
|    5 | This is a test |
|    6 | This is a test |
|    7 | This is a test |
|    8 | This is a test |
|    9 | This is a test |
|   10 | This is a test |
+------+----------------+
10 rows in set (0.00 sec)
```

### Author

**Gabriel Bordeaux**

+ [Website](http://www.gab.lc/) 
+ [Twitter](https://twitter.com/gabrielbordeaux)
