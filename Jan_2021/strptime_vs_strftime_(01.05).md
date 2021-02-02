## strftime() vs strptime()

- strptime() <br>
  문자열 -> datetime 객체 <br>
- strftime() <br>
  datetime 객체 -> 문자열

```python
import datetime

dt_now = datetime.datetime.now()
d_today = datetime.date.today()

dt_now.strftime('%Y-%m-%d %H:%M:%S')
>> '2021-02-02 12:07:15'

d_today.strftime('%y%m%d')
>> '210202'

d_today.strftime('%Y/%m/%d')
>> '2021/02/02'

d_today.strftime('%A, %B %d, %Y')
>> 'Tuesday, February 02, 2021'

d_today.strftime('%a, %b %d, %Y')
>> 'Tue, Feb 02, 2021'

```

> |          | strftime            | strptime                      |
> | -------- | ------------------- | ----------------------------- |
> | 용도     | 객체-> 문자열       | 문자열 ->객체                 |
> | 메소드형 | 인스턴스 메소드     | 클래스 메소드                 |
> | 사용가능 | date; datetime;time | datetime                      |
> | 형식     | strftime(format)    | strptime(date_string, format) |

공식문서 -> [datetime](https://docs.python.org/ko/3/library/datetime.html#strftime-strptime-behavior)
