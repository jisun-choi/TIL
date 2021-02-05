## lambda calculus

함수형 프로그래밍의 람다 표현식은 람다 대수에 근간을 두고 있다. **추상화**를 통해 함수를 구성하는 것이 주요 아이디어 인데 여기서 추상화란 예를 들어 '한 잔에 3000원인 커피 2잔을 사려면?' 이라는 문제를 풀기 위해 '가격 x 개수' 라는 식을 만들어 내는 것이다.

> The λ-calculus is, at heart, a simple notation for functions and application. The main ideas are applying a function to an argument and forming functions by abstraction <br> > [The Lambda Calculus](https://plato.stanford.edu/entries/lambda-calculus/)

### 익명 함수

- 일급 객체(First-class citizen) 로서의 함수
  : 함수의 인자로 넘겨 받을 수 있고 결과값으로 리턴할 수도 있으며 변수에 값을 할당할 수 있다.

파이썬의 경우 람다 함수가 아닌 **람다 표현식**을 지원한다.

> To be precise the lambda keyword (reserved word) in Python evaluates an expression into a function reference. It’s a special (syntactic) form in the language.
>
> A lambda function or expression is an anonymous block of code or program functionality. It acts like a function, takes arguments and returns values ... but it is not bound to any name or identifier which is visible to the programmer.
> [What is lambda function in Python and why do we need it?](https://www.quora.com/What-is-lambda-function-in-Python-and-why-do-we-need-it)

### Python 의 lambda expression

[5 Uses of Lambda Functions in Python](https://medium.com/techtofreedom/5-uses-of-lambda-functions-in-python-97c7c1a87244)

`lambda arguments : expression`

- lambda keyword
- arguments: 함수가 받을 인자
- expression: 함수의 리턴값

1. Simple use

```python
#lambda expression
lambda_add = lambda x: x + 1
print(lambda_add(2))
>> 3

#normal function
def add(x):
  return x+1
print(add(2))
>> 3
```

2. with High order functions
   `e.g. map(), filter(), reduce()`

```python
numbers = [1,2,3,4,5,6,7,8,9,10]
print(list(filter(lambda x: x % 2 == 1, numbers)))
>> [1, 3, 5, 7, 9]
```

c.f. list comprehension 으로도 표현 가능! <br>
`odd_numbers = [i for i in numbers if i % 2 == 1]`

3. 'Key' 인자로 활용
   sort(), sorted() 메소드로 iteralble 을 정렬할 때 key 인자를 기준으로 이터러블을 정렬하게 된다.

```python
leaders = ["Warren Buffett", "Yang Zhou", "Tim Cook", "Elon Musk"]
print(leaders)
>> ['Warren Buffett', 'Yang Zhou', 'Tim Cook', 'Elon Musk']
leaders.sort(key=lambda x: len(x))
print(leaders)
>> ['Tim Cook', 'Yang Zhou', 'Elon Musk', 'Warren Buffett']

# 딕셔너리 sorting
leaders = {4: "Yang Zhou", 2: "Elon Musk", 3: "Tim Cook", 1: "Warren Buffett"}
print(leaders)
>> {4: 'Yang Zhou', 2: 'Elon Musk', 3: 'Tim Cook', 1: 'Warren Buffett'}
leaders = dict(sorted(leaders.items(), key=lambda x: x[0]))
print(leaders)
>> {1: 'Warren Buffett', 2: 'Elon Musk', 3: 'Tim Cook', 4: 'Yang Zhou'}
```

4. Closure 로 활용

```python
#normal nested function
def outer_func():
    developer = "jisun"
    def print_developer(location=""):
        return developer + " in " + location
    return print_developer

dev = outer_func()("SEOUL")
print(dev)
>> "jisun in SEOUL"

#lambda expression
def outer_func():
  developer = "jisun"
  return lambda location="": developer + " in " + location

dev = outer_func()("SEOUL")
print(dev)
>> "jisun in SEOUL"
```
