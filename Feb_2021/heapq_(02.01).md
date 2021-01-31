### 파이썬 heapq 모듈

heapq 모듈은 리스트를 **최소 힙** 형태로 정렬해준다.

- `heapq.heapify(list)` : 리스트를 heap 으로 변환. 시간 복잡도 O(n)
- `heapq.heappush(heap, item)`: heap 에서 가장 작은 원소 pop (=heap[0])
- `heapq.heappop(heap)`

```python
import heapq

heap = []
heapq.heappush(heap, 50)
heapq.heappush(heap, 10)
heapq.heappush(heap, 20)

print(heap)
>> [10, 50, 20]
```

#### 최대 힙 구현

```python
heap_items = [1, 3, 5, 7, 9]
max_heap = []
for item in heap_items:
    heapq.heappush(max_heap, (-item, item))

print(max_heap)
>>[(-9, 9), (-7, 7), (-3, 3), (-1, 1), (-5, 5)]

max_item = heapq.heappop(max_heap)[1]
print(max_item)
>>9
```

출처: <br>
[[Python] 힙 자료구조 / 힙큐(heapq) / 파이썬에서 heapq 모듈 사용하기](https://littlefoxdiary.tistory.com/3)
