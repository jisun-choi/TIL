## 2020.12.21 Mon ✏️

- bcrypt 를 이용해서 암호화한 비밀번호의 길이는 사용자 인풋에 따라 달라지는 것이
  아니고 사용한 해쉬 알고리즘에 의해 결정된다.<br>
  흡사 메모장과 같은 블로깅을 하였다✔️ :[Bcrypt](https://velog.io/@wltjs10645/Does-the-length-of-the-encrypted-password-vary-according-to-the-input)
- 비슷한 맥락으로 JWT 값도 사이즈가 정해져 있는 것 같은데 좀 더 공부 필요!
- pymysql 의 cursor 객체에서 fetchone() 이 가능한 것은 select 문을 실행할 때이다
  . insert 나 update 문을 실행한다면 affected row 를 반환한다.

- put 할때 따로 입력값이 이전에 수정했던 내용과 동일한 지 검사하지 않고 affected row 가 0이면 에러를 발생시키면 간단쓰
- 멀쩡히 되던 것이 갑자기 안된다면 서버도 한 번 껐다켜보고 포스트맨도 새창을 실>행해본다... 진심 이것들이 답이 될 수 있음🙃

## 2020.12.22 Tue ✏️

### 트랜잭션

- 주된 목적은 데이터를 안전하게 관리하기 위함이다.

  - 예를 들어 주문을 생성하고 -> 주문상세 1 -> 주문상세 2 의 순서로 데이터를 처리한다고 가장하자.
  - 생성된 주문 번호를 받아서 주문상세1 을 생성하는 도중 오류가 발생한다면 주문, 주문상세1 은 이미 생성되었고 주문 상세2는 생성되지 않는 식으로 유저가 원하는 주문정보와 다른 주문이 생기게 되며 DB 데이터에 큰 혼란을 야기할 수 있다.
  - 위와 같은 오류를 방지해주는 개념이 트랜잭션이다. 트랜잭션 안에서 모든 처리가 완성되면 _commit_ 을 하고, 오류가 생겼다면 _rollback_ 을 실행하여 트랜잭션이 발생하기 전과 같은 상태로 DB 를 되돌려줘야 한다.

- 트랜잭션을 관리하기 위해서는 auto commit 은 false 여야 한다. (pymysql은 디폴트 false 임)
- 트랜잭션은 세션에 종속적이다.

#### 세션이란?

> A session represents the connection between an application and the relational database that stores its persistent objects.<br>
> A Unit of Work keeps track of everything you do during a business transaction that can affect the database. When you're done, it figures out everything that needs to be done to alter the database as a result of your work <br>
> 출저: [what is a database session?](https://stackoverflow.com/questions/10521947/what-is-a-database-session)

- 트랜잭션은 row lock 과 table lock 을 유발할 수 있기 때문에 유의해서 사용해야 한다.
- 쿼리로 트랜잭션 사용 가능! (MySQL)

```
START TRANSACTION;
// SQL statements
ROLLBACK;
// SQL statements
COMMIT;
// SQL statements
```

## 2020.12.27 Sun ✏️

### mysql 에러해결!

진짜 갑.자.기 mysql 서버가 안켜지면서 아래와 같은 에러 메세지들이 출현(?)했다.<br>
일단 워크벤치로 당장 급한 과제들은 해결했고 <br>
로컬 디비에 과제에 사용한 데이터들이 들어있어서 mysql을 지우고 재설치 하는 것도 옵션이 아니었다😢 <br>
검색 끝에 이번에도 해결책은 갓스택오버플로우에서~~~!!!! <br>
뭔가 권한 문제 같았는데 정확한 원인은 미래의 내가 알아서 공부하겠지! <br>
빠른 시일내에 OS & 네트워크 공부 시작해야겠다. 자료구조도... 리눅스 명령어도... <br>

[PID error on mysql.server start?](https://stackoverflow.com/questions/4444861/pid-error-on-mysql-server-start)

> ERROR! The server quit without updating PID file (/usr/local/var/mysql/choejiseon-ui-MacBookPro.local.pid).
> Starting MySQL
> ..................................................................................................... ERROR! The server quit without updating PID file (/usr/local/var/mysql/>choejiseon-ui-MacBookPro.local.pid).

### mysql 이 돌아가고 있는 프로세스 확인해서 물음표가 있는 것들을 없애줬다.

```
choejiseon        8700   0.0  0.3  4974476  55636   ??  S    목04PM   2:10.28 /usr/local/Cellar/mysql/8.0.22_1/bin/mysqld --basedir=/usr/local/Cellar/mysql/8.0.22_1 --datadir=/usr/local/var/mysql --plugin-dir=/usr/local/Cellar/mysql/8.0.22_1/lib/plugin --log-error=choejiscBookPro.err --pid-file=/usr/local/var/mysql/choejiscBookPro.pid
choejiseon        8588   0.0  0.0  4298612      8   ??  S    목04PM   0:00.02 /bin/sh /usr/local/Cellar/mysql/8.0.22_1/bin/mysqld_safe --datadir=/usr/local/var/mysql --pid-file=/usr/local/var/mysql/choejiscBookPro.pid
choejiseon       53463   0.0  0.0  4295988    792 s004  S+    5:11PM   0:00.00 grep --color=auto --exclude-dir=.bzr --exclude-dir=CVS --exclude-dir=.git --exclude-dir=.hg --exclude-dir=.svn --exclude-dir=.idea --exclude-dir=.tox mysql

ps aux | grep mysql
kill 8700
kill 8588
```
