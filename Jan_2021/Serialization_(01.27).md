## 직렬화 (Serialization)

일정한 규칙에 따라 데이터 객체를 메모리를 디스크에 저장하거나 네트워크 통신에 사용하기 위한 형식(이진 데이터, byte) 으로 변환하는 것

## 역직렬화 (Deserialization)

이진화 된 데이터 객체를 받은 쪽에서 다시 원래의 형태로 되돌리는 것

### Why?

네트워크를 통해 데이터를 주고 받는 길을 스트림이라 하는데 이 스트림에는 데이터가 한번에 한 바이트씩 밖에 통과할 수 없다. 객체화 된 데이터는 이 좁은 스트림을 통과할 수 없기 때문에 serialization 이 필요하다.

C, C++, Java 등의 개발언어에서 사용하는 데이터의 메모리 구조:

- Value type:
  int, float, char 등 스택에 메모리가 쌓이고 직접 접근 가능
- Reference type:
  포인터 변수를 선언하면 힙에 메모리가 할당되고 스택에서는 이 힙 메모리를 참조하는 구조

이 둘 중 디스크에 저장하거나 네트워크 통신을 할 때는 value type 으로만 가능한데, reference type 은 실제 값이 아닌 메모리 번지 주소를 가지기 때문이다.

1. 프로그램을 종료하면 기존에 할당되었던 메모리는 없어지기 때문
2. 각 PC 마다 사용하는 메모리 공간 주소는 전혀 다르기 때문

따라서 직렬화를 통해 각 주소값이 가지는 데이터들을 value type 으로 변경해주어야 한다.

### types of serialization

- pickle: 가독성은 떨어지지만 직렬화 속도가 JSON 보다 빠름
- JSON: 가독성이 좋음
- YAML: 복잡한 설정 파일의 경우 JSON 보다 가독성이 좋은 YAML 이 좋음
- CSV etc

#### pickle

```python
import pickle
fruit_store = {'apple':1000, 'banana':2000, 'tomato':'soldout', 'melon':'5000'}
# pickle로 파일 쓰기
with open('./data/fruit.txt','wb') as f:
    pickle.dump(fruit_store,f)

# pickle로 쓰인 파일 읽기
with open('./data/fruit.txt','rb') as f:
    data = pickle.load(f)
```

#### json

```python
import json
fruit_store = {'apple':1000, 'banana':2000, 'tomato':'soldout', 'melon':'5000'}
# pickle로 파일 쓰기
with open('./data/fruit.txt','wb') as f:
    json.dump(fruit_store,f)

# pickle로 쓰인 파일 읽기
with open('./data/fruit.txt','rb') as f:
    data = json.load(f)
```

참고: <br>
[[python] serialize (직렬화)](https://itholic.github.io/python-serialize/) <br>
[데이터 직렬화(serialization), 역직렬화(deserialization)는 무엇이고 왜 필요한가?](https://hub1234.tistory.com/26)
