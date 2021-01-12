## try & finally

try & finally 구문의 실행 순서를 자세히 들여다본 적이 없었는데 <br>
오늘 정확히 알게 되었다. <br>

- try block 에서 return 이 되기 전에 finally block 이 실행되고
- 만약 finally block 에서 return 이 된다면 try block 의 리턴은 실행되지 않는다.
- finally block 에 리턴값이 없으면 다시 try block 으로 돌아가 리턴을 실행한다.

```
def check():
    try:
        print("try")
        return "a"
    except Exception:
        print("no")
        return "b"
    finally:
        print("finally")
        return "c"

print(check())
>> try   # try block 실행 (리턴 X)
>> finally # finally block 실행
>> c # finally block 에서 리턴
```

```
def check():
    try:
        print("try")
        return "a"
    except Exception:
        print("no")
        return "b"
    finally:
        print("finally")
        #return "c"

print(check())
>> try   # try block 실행 (리턴 X)
>> finally # finally block 실행
>> a # 다시 try block 으로 돌아가서 리턴
```
