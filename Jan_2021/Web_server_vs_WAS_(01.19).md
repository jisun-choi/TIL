## Web Server vs WAS

- Web Server:
  - Apache, Nginx 등
  - HTTP 프로토콜을 기반으로 클라이언트의 요청에 맞는 데이터를 보내준다.
  - 정적인 콘텐츠의 경우 WAS 에 따로 요청할 필요없이 web server 에서 바로 자원을 제공
  - 동적인 콘텐츠는 WAS 에 요청을 보내고 그의 응답을 받아 클라이언트로 전달
- WAS (Web Application Server)
  - DB 조회나 다양한 로직 처리를 요구하는 동적인 콘텐츠를 처리하기 위한 application server
  - 어플리케이션을 수행하는 미들웨어의 일종
  - Web server + Web container
  - 예를 들면, 장고로 작성하는 앱의 서버가 여기에 해당!

### web server 와 was 가 따로 존재하는 이유!

- 서버 부하 방지
- 물리적 분리로 보안 강화
- Load Balancing (여러 WAS 를 연결)
- 한 서버에서 다른 종류의 application 사용 가능

한마디로, <br>

> 자원 이용의 효율성 및 장애 극복, 배포 및 유지보수의 편의성을 위해

[10분 테코톡 티거의 Web server vs WAS](https://www.youtube.com/watch?v=F_vBAbjj4Pk) <br>
[희봉의 웹서버 vs WAS](https://www.youtube.com/watch?v=NyhbNtOq0Bc) <br>
[Web Server와 WAS의 차이와 웹 서비스 구조](https://gmlwjd9405.github.io/2018/10/27/webserver-vs-was.html)
