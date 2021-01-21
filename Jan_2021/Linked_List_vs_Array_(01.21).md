## Linked List vs. Array

- linked list 와 array 는 모두 선형적 자료구조이다. array 는 연속적인 메모리 주소가 컴파일 타임에 할당되는 반면 (예를 들면 array 가 선언되는 순간) linked list 는 런타임에 메모리와 데이터가 할당된다.

  > **A Linear data structure** have data elements arranged in sequential manner and each member element is connected to its previous and next element. ... Such data structures are easy to implement as computer memory is also sequential.
  > [Difference between Linear and Non-linear Data Structures](https://www.tutorialspoint.com/difference-between-linear-and-non-linear-data-structures)

- 보통 array 가 default datatype 으로 많이 사용되지만 저장할 데이터의 사이즈를 모르는 경우도 많기 때문에 linked list 같은 advanced 자료구조가 필요하다.

| Array                                                                   | Linked List                                                            |
| ----------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| 유사한 데이터 타입의 집합                                               | 동일한 데이터 타입들의 정렬된 집합으로 포인터를 통해 서로 연결됨       |
| 랜덤으로 원하는 값을 가져올 수 있음 (인덱스 사용), 시간 복잡도 O(1)     | 순차 접근만 가능. n 번째 요소에 접근하고 싶다면 시간 복잡도는 O(n)     |
| 데이터들은 근접한 메모리 주소 or 연속적인 메모리 주소에 할당됨          | 메모리 아무 곳이나 할당 가능. 대신 메모리 주소를 이전 노드에 저장      |
| 삽입, 삭제 효율이 좋지 않음 (데이터가 연속적으로 저장되어 있으므로)     | 새 데이터는 비어있는 곳 어디에나 할당 가능. 삽입, 삭제가 빠름          |
| 정적 메모리 할당: array 가 선언되는 순간 (컴파일타임)에 메모리가 할당됨 | 동적 메모리 할당: 새로운 노트가 추가되는 순간 (런타임) 메모리가 할당됨 |
| 모든 데이터는 독립적이고 따라서 인덱스를 사용해서 접근 가능             | 모든 데이터는 다음, 이전 혹은 서로와 연결되어 있음                     |
| array 가 선언되는 순간 사이즈를 지정해야함                              | 사이즈 유동적으로 변경됨. 런타임에 데이터가 추가되면 사이즈가 커짐     |
| 스택으로 메모리 할당                                                    | 힙으로 메모리 할당                                                     |

![](https://images.velog.io/images/wltjs10645/post/c328feae-36fb-4fbe-a595-21e8b24bbd93/image.png)
[Difference between Array and Linked List](https://www.studytonight.com/data-structures/linked-list-vs-array#)
