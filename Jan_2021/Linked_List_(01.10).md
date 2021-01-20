# 연결 리스트란?!

- 메모리의 동적 할당을 기반으로 구현된 리스트
- 원소들이 메모리상에 연속적으로 위치하지 않고 node와 link 로 구현된다.
- 미리 메모리를 할당할 필요없이 동적으로 구성이 가능하기 때문에 데이터의 입력과 삭제가 자유롭다. <br>
  = 메모리를 효율적으로 사용할 수 있다. (장) <br>
  = 특정 위치의 데이터를 찾기 위해서는 처음부터 끝까지 순차적으로 리스트를 탐색해야한다. (단)

![](https://images.velog.io/images/wltjs10645/post/91c2a929-acb3-4c03-97d2-8d0f6c2d1a93/image.png)

## Singly Linked List

[Singly Linked List](https://www.youtube.com/watch?v=XGSoQ0J5An4&list=PLzjoZGHG3J8vdUH75YPqmO7lbQl_M-xXo&index=1) 튜토리얼을 보고 직접 구현해 보았다.

### 마지막에 새로운 node 추가

1. empty head 를 확인
2. 새로운 node 를 추가하고 이 새로운 node 가 head 가 됨
3. 여기서 또 Node 를 추가하고 싶다면 head.next 에 새로운 node 를 연결

![](https://images.velog.io/images/wltjs10645/post/80bb5fba-ef84-4526-a11f-3ca7a7a00186/image.png)

```python
# 노드 생성
# 링크드 리스트 생성
# 링크드 리스트에 노드 추가
# 링크드 리스트 출력
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None


class LinkedList:
    def __init__(self):
        self.head = None

    def insert(self, newNode):
        # head => Apple -> None
        if self.head is None:
            self.head = newNode
        else:
            # head => Apple -> Mango -> None  (o) || Apple -> Kiwi (x)
            lastNode = self.head
            # 노드를 이동하기 위한 처리
            while True:
                if lastNode.next is None:
                    break
                # if 조건에 걸리지 않으면 lastNode를 이동해준다.
                lastNode = lastNode.next
            # 마지막 lastNode 가 새로 추가된 Node를 가르키도록!
            lastNode.next = newNode

    def printList(self):
        # head => Apple -> Mango -> Kiwi-> None
        currentNode = self.head
        while True:
            if currentNode is None:
                break
            print(currentNode.data)
            currentNode = currentNode.next


firstNode = Node("Apple")
linkedList = LinkedList()
linkedList.insert(firstNode)
secondNode = Node("Mango")
linkedList.insert(secondNode)
thirdNode = Node("Kiwi")
linkedList.insert(thirdNode)
linkedList.printList()

>> Apple
>> Mango
>> Kiwi
```

### 새로운 head node 추가

1. 현재 head 를 temp node 에 저장
2. 새로운 node를 head node 로 지정
3. 새로운 node 의 next 가 temp node 를 가르키도록 설정
   ![](https://images.velog.io/images/wltjs10645/post/a0310874-5ae3-4bae-b329-57a536cc3283/image.png)

```python
class Node:
  ...

class LinkedList:
    ...
    def insertHead(self, newNode):
        # data => Kiwi, next => None
        tempNode = self.head  # Apple
        self.head = newNode  # Kiwi
        self.head.next = tempNode
        del tempNode


firstNode = Node("Apple")
linkedList = LinkedList()
linkedList.insert(firstNode)
secondNode = Node("Mango")
linkedList.insert(secondNode)
thirdNode = Node("Kiwi")
linkedList.insertHead(thirdNode)
linkedList.printList()

>> Kiwi
>> Apple
>> Mango
```

### 중간에 새로운 node 추가

1. position1 까지 이동
2. 이전 노드의 정보를 temp node 에 저장
3. 이전 노드의 next 에 new node 를 연결
4. new node 의 next 에 position1 의 node 연결
5. new node = position1, 이전 position1 의 node = position2 가 됨
   ![](https://images.velog.io/images/wltjs10645/post/d9963ff2-c16a-4b8e-8c3e-9f0cda2b8c8b/image.png)

```python
class Node:
	...

class LinkedList:
    def __init__(self):
        self.head = None

    def listLength(self):
        currentNode = self.head
        length = 0
        while currentNode is not None:
            length += 1
            currentNode = currentNode.next
        return length

    def insertHead(self, newNode):
        ...

    def insertAt(self, newNode, position):
        if position < 0 or position > self.listLength():
            print("Invalid position")
            return
        if position is 0:
            self.insertHead(newNode)
            return
        currentNode = self.head
        currentPosition = 0
        while True:
            if currentPosition == position:
                previousNode.next = newNode
                newNode.next = currentNode
                break
            previousNode = currentNode
            currentNode = currentNode.next
            currentPosition += 1

    # insert() 와 동일
    def insertEnd(self, newNode):
        ...

    def printList(self):
        ...


firstNode = Node("Apple")
linkedList = LinkedList()
linkedList.insertEnd(firstNode)
secondNode = Node("Mango")
linkedList.insertEnd(secondNode)
thirdNode = Node("Kiwi")
linkedList.insertAt(thirdNode, 1)
linkedList.printList()

```

### 마지막 node 삭제

1. 리스트 끝까지 이동
2. 마지막에서 두번째 node 를 temp node 에 저장
3. 마지막 node 삭제
4. temp node 의 next 를 none 으로 변경

**\*\*** 아래의 코드에서 lastNode 변수는 주소 300에 대한 reference 일 뿐이다. 따라서 del lastNode 를 실행하면 그 주소에 대한 reference를 삭제하는 것이고 여전히 Kiwi 라는 데이터가 마지막에 출력된다.
![](https://images.velog.io/images/wltjs10645/post/f7f4768d-4678-4fdf-9075-9b0f46c9f95a/image.png)

```python
class Node:
    ...


class LinkedList:
	...
    def deleteEnd(self):
        lastNode = self.head
        while lastNode.next is not None:
            previousNode = lastNode
            lastNode = lastNode.next
        previousNode.next = None


firstNode = Node("Apple")
linkedList = LinkedList()
linkedList.insertEnd(firstNode)
secondNode = Node("Mango")
linkedList.insertEnd(secondNode)
thirdNode = Node("Kiwi")
linkedList.insertEnd(thirdNode)
linkedList.deleteEnd()
linkedList.printList()
```

### head, 중간 node 삭제

1. 지우고 싶은 노드까지 이동
2. 이전 node 를 temp node 에 저장
3. 이전 node 의 next 에 현재 node 의 next 를 연결
4. 현재 node 의 next 를 none 으로 변경

```python
class Node:
	...

class LinkedList:
	...
    def isListEmpty(self):
        if self.head is None:
            return True
        else:
            return False

    def deleteHead(self):
        if self.isListEmpty() is False:
            previousHead = self.head
            self.head = self.head.next
            previousHead.next = None
        else:
            print("Linked List is empty.")

    def deleteAt(self, position):
        if position < 0 or position >= self.listLength():
            print("invalid position")
            return
        if self.isListEmpty() is False:
            if position is 0:
                self.deleteHead()
                return
        currentNode = self.head
        currentPosition = 0
        while True:
            if currentPosition == position:
                previousNode.next = currentNode.next
                currentNode.next = None
                break
            previousNode = currentNode
            currentNode = currentNode.next
            currentPosition += 1

firstNode = Node("Apple")
linkedList = LinkedList()
linkedList.insertEnd(firstNode)
secondNode = Node("Mango")
linkedList.insertEnd(secondNode)
thirdNode = Node("Kiwi")
linkedList.insertEnd(thirdNode)
linkedList.deleteAt(1)
linkedList.printList()

```

## Merge 2 sorted singly linked list

1. 두 list 의 head 를 비교해서 작은 것을 먼저 mergedList 에 추가 (List 1의 1번 node)
2. List1 의 2번 Node 와 List 2의 1번 Node 를 비교해서 작은 것을 mergedList 에 추가
3. 반복
4. 한 list 의 모든 Node 가 옮겨지면 다른 List 의 나머지 node 들은 그대로 mergedList 로 추가

![](https://images.velog.io/images/wltjs10645/post/9dfe60c6-4dbb-45eb-aea4-6b0edfc4b6df/image.png)

### result!(mergedList)

![](https://images.velog.io/images/wltjs10645/post/d230b30c-6f56-4cf5-84d3-a2914d64f1dc/image.png)

```python
def mergedLists(firstList, secondList, mergeList):
    # 1 -> 3 -> 4 || 2 -> 7 -> 9
    currentFirst = firstList.head
    currentSecond = secondList.head
    while True:
        if currentFirst is None:
            mergedList.insertEnd(currentSecond)
            break
        if currentSecond is None:
            mergedList.insertEnd(currentFirst)
            break
        if currentFirst.data < currentSecond.data:
            currentFirstNext = currentFirst.next
            currentFirst.next = None
            mergedList.insertEnd(currentFirst)
            currentFirst = currentFirstNext
        else:
            currentSecondNext = currentSecond.next
            currentSecond.next = None
            mergedList.insertEnd(currentSecond)
            currentSecond = currentSecondNext


# first list
nodeOne = Node(1)
nodeTwo = Node(3)
nodeThree = Node(4)
firstList = LinkedList()
firstList.insertEnd(nodeOne)
firstList.insertEnd(nodeTwo)
firstList.insertEnd(nodeThree)

# second list
nodeFour = Node(2)
nodeFive = Node(7)
nodeSix = Node(9)
secondList = LinkedList()
secondList.insertEnd(nodeFour)
secondList.insertEnd(nodeFive)
secondList.insertEnd(nodeSix)

firstList.printList()
secondList.printList()

mergedList = LinkedList()
mergedLists(firstList, secondList, mergedList)
del firstList
del secondList
mergedList.printList()

```

#### codecademy tutorial

```
class Node:
  def __init__(self, value, next_node=None):
    self.value = value
    self.next_node = next_node

  def get_value(self):
    return self.value

  def get_next_node(self):
    return self.next_node

  def set_next_node(self, next_node):
    self.next_node = next_node

class LinkedList:
  def __init__(self, value=None):
    self.head_node = Node(value)

  def get_head_node(self):
    return self.head_node

  def insert_beginning(self, new_value):
    new_node = Node(new_value)
    new_node.set_next_node(self.head_node)
    self.head_node = new_node

  def stringify_list(self):
    string_list = ""
    current_node = self.get_head_node()
    while current_node:
      if current_node.get_value() != None:
        string_list += str(current_node.get_value()) + "\n"
      current_node = current_node.get_next_node()
    return string_list

  def remove_node(self, value_to_remove):
    current_node = self.get_head_node()
    if current_node.get_value() == value_to_remove:
      self.head_node = current_node.get_next_node()
    else:
      while current_node:
        next_node = current_node.get_next_node()
        if next_node.get_value() == value_to_remove:
          current_node.set_next_node(next_node.get_next_node())
          current_node = None
        else:
          current_node = next_node
```
