## what does underscore mean in python

- 숫자 나누기

```python
a = 1_000_000
a
>> 1000000
```

- 변수에 담고 싶지 않을 때

```python
odd_nums = [1, 3, 5, 7]
a, _, b,_ = odd_nums
print(a, b)
>> 1, 5
```

- 인터프리터에서 최신 expression 의 값을 알고 싶을 때

```python
#함수
>>> lambda x,y:x*y
<function <lambda> at 0x100835820>
>>> _(2,3)
6

#일반 연산
>>> 4+10
14
>>> _
14
>>> 3+4
7
>>> _
7

```

- 네이밍 컨벤션 - oop 의 class members
  - `_var`: protected member, 같은 클래스 혹은 파생 클래스 안에서 사용 가능
  - `__var`: private member, 같은 클래스 안에서만 사용 가능
    - python name mangling:
      private 변수 만들고 싶을 때, 하위클래스가 상위클래스 속성 오버라이딩 하는 것을 막을 때
  - `var_`: 변수명이 이미 파이썬 built-in keywords 로 존재하는 경우
  - `__var__`: magic methods

참조: [Role of Underscore(\_) in Python](https://www.datacamp.com/community/tutorials/role-underscore-python#UII)
