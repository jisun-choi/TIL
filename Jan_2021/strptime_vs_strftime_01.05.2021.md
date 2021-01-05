## strftime() vs strptime()

- strptime() <br>
  문자열 -> datetime 객체 <br>
- strftime() <br>
  datetime 객체 -> 문자열

> |          | strftime            | strptime                      |
> | -------- | ------------------- | ----------------------------- |
> | 용도     | 객체-> 문자열       | 문자열 ->객체                 |
> | 메소드형 | 인스턴스 메소드     | 클래스 메소드                 |
> | 사용가능 | date; datetime;time | datetime                      |
> | 형식     | strftime(format)    | strptime(date_string, format) |

공식문서 -> ![](https://docs.python.org/ko/3/library/datetime.html#strftime-strptime-behavior)
