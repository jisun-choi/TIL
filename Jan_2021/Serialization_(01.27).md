## 직렬화 (Serialization)

일정한 규칙에 따라 데이터 객체를 메모리를 디스크에 저장하거나 네트워크 통신에 사용하기 위한 형식(이진 데이터, byte) 으로 변환하는 것

## 역직렬화 (Deserialization)

이진화 된 데이터 객체를 받은 쪽에서 다시 원래의 형태로 되돌리는 것

### Why?

네트워크를 통해 데이터를 주고 받는 길을 스트림이라 하는데 이 스트림에는 데이터가 한번에 한 바이트씩 밖에 통과할 수 없다. 객체화 된 데이터는 이 좁은 스트림을 통과할 수 없기 때문에 serialization 이 필요하다.

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

참고 -> [[python] serialize (직렬화)](https://itholic.github.io/python-serialize/)
