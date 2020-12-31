## JOIN

### 사원 & 팀 테이블
- 사원 4 rows 
- 팀 7 rows

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
```
### LEFT JOIN 
왼쪽 테이블을 기준으로 왼쪽 테이블의 모든 열이 나올 수 있도록 join 된다. 
```
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
```
### RIGHT JOIN
오른쪽 테이블을 기준으로 오른쪽 테이블의 모든 열이 나올 수 있도록 join 된다. 
1,2,3,4,6에 해당하는 팀원이 없더라도 NULL 로 표시하여 row 가 표출된다. 
```
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
