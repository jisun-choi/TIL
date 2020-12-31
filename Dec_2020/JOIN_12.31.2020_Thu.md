## JOIN

```
mysql> select name_english from staffs;
+--------------+
| name_english |
+--------------+
| choi         |
| lee          |
| Kim          |
| kang         |
+--------------+

mysql> select id from teams;
+----+
| id |
+----+
|  1 |
|  2 |
|  3 |
|  4 |
|  5 |
|  6 |
|  7 |
+----+
mysql> select name_english, teams.id from staffs left join teams on staffs.team=teams.id;
+--------------+------+
| name_english | id   |
+--------------+------+
| choi         |    7 |
| lee          |    5 |
| Kim          |    7 |
| kang         |    7 |
+--------------+------+
4 rows in set (0.00 sec)

mysql> select name_english, teams.id from staffs right join teams on staffs.team=teams.id;
+--------------+----+
| name_english | id |
+--------------+----+
| NULL         |  1 |
| NULL         |  2 |
| NULL         |  3 |
| NULL         |  4 |
| lee          |  5 |
| NULL         |  6 |
| choi         |  7 |
| Kim          |  7 |
| kang         |  7 |
+--------------+----+
9 rows in set (0.00 sec)
```
