## 2020.12.21 Mon ✏️

- bcrypt 를 이용해서 암호화한 비밀번호의 길이는 사용자 인풋에 따라 달라지는 것이
 아니고 사용한 해쉬 알고리즘에 의해 결정된다.<br>
 흡사 메모장과 같은 블로깅을 하였다✔️ :[Bcrypt](https://velog.io/@wltjs10645/Does-the-length-of-the-encrypted-password-vary-according-to-the-input)
- 비슷한 맥락으로 JWT 값도 사이즈가 정해져 있는 것 같은데 좀 더 공부 필요!
- pymysql 의 cursor 객체에서 fetchone() 이 가능한 것은 select 문을 실행할 때이다
. insert 나 update 문을 실행한다면 affected row 를 반환한다.

- put 할때 따로 입력값이 이전에 수정했던 내용과 동일한 지 검사하지 않고 affected row 가 0이면 에러를 발생시키면 간단쓰
- 멀쩡히 되던 것이 갑자기 안된다면 서버도 한 번 껐다켜보고 포스트맨도 새창을 실>행해본다... 진심 이것들이 답이 될 수 있음🙃

