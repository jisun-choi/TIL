## Stack

- Last In, First Out(LIFO): 후입선출
- 스택은 top node 만 조작할 수 있고 각 노드들을 순회할 수 없다.
- 스택은 미리 정해진 사이즈 만큼만 사용할 수 있다.
  - stack overflow: 스택의 모든 메모리가 꽉 차있어서 더이상 데이터를 삽입할 수 없을 때
  - stack underflow: 스택에 제거할 데이터가 없을 때
- 재귀함수, 웹 브라우저 방문기록, 실행 취소, 괄호 검사

#### Codecademy tutorial

```python
from node import Node

class Stack:
  def __init__(self, limit=1000):
    self.top_item = None
    self.size = 0
    self.limit = limit

  def push(self, value):
    if self.has_space():
      item = Node(value)
      item.set_next_node(self.top_item)
      self.top_item = item
      self.size += 1
      print("Adding {} to the pizza stack!".format(value))
    else:
      print("No room for {}!".format(value))

  def pop(self):
    if not self.is_empty():
      item_to_remove = self.top_item
      self.top_item = item_to_remove.get_next_node()
      self.size -= 1
      print("Delivering " + item_to_remove.get_value())
      return item_to_remove.get_value()
    print("All out of pizza.")

  def peek(self):
    if not self.is_empty():
      return self.top_item.get_value()
    print("Nothing to see here!")

  def has_space(self):
    return self.limit > self.size

  def is_empty(self):
    return self.size == 0

# Defining an empty pizza stack
pizza_stack = Stack(6)
# Adding pizzas as they are ready until we have
pizza_stack.push("pizza #1")
pizza_stack.push("pizza #2")
pizza_stack.push("pizza #3")
pizza_stack.push("pizza #4")
pizza_stack.push("pizza #5")
pizza_stack.push("pizza #6")

# Uncomment the push() statement below:
pizza_stack.push("pizza #7")

# Delivering pizzas from the top of the stack down
print("The first pizza to deliver is " + pizza_stack.peek())
pizza_stack.pop()
pizza_stack.pop()
pizza_stack.pop()
pizza_stack.pop()
pizza_stack.pop()
pizza_stack.pop()

# Uncomment the pop() statement below:
pizza_stack.pop()
```

```python
class Node:
  def __init__(self, value, next_node=None):
    self.value = value
    self.next_node = next_node

  def set_next_node(self, next_node):
    self.next_node = next_node

  def get_next_node(self):
    return self.next_node

  def get_value(self):
    return self.value
```

### Hanoi 의 탑 게임

```python
from stack import Stack

print("\nLet's play Towers of Hanoi!!")

#Create the Stacks
stacks = []
left_stack = Stack('Left')
middle_stack = Stack('Middle')
right_stack = Stack('Right')

stacks.append(left_stack)
stacks.append(middle_stack)
stacks.append(right_stack)

#Set up the Game
num_disks = int(input('\nHow many disks do you want t play with?\n'))

while num_disks < 3:
  num_disks = int(input('Enter a number greater than or equal to 3\n'))

for i in range(num_disks, 0, -1):
  left_stack.push(i)

num_optimal_moves = num_disks - 1
print(f"\nThe fastest you can solve this game is in {num_optimal_moves} moves")
#Get User Input

def get_input():
  choices = [stack.get_name()[0] for stack in stacks]
  while True:
    for i in range(len(stacks)):
      name = stacks[i].get_name()
      letter = choices[i]
      print(f"Enter {letter} for {name}")
    user_input = input()
    if user_input in choices:
      for i in range(len(stacks)):
        if user_input == choices[i]:
          return stacks[i]

#Play the Game
num_user_moves = 0
while (right_stack.get_size() != num_disks):
  print("\n\n\n...Current Stacks...")
  for i in stacks:
    i.print_items()
  while True:
    print("\nWhich stack do you want to move from?\n")
    from_stack = get_input()
    print("\nWhich stack do you want to move to?\n")
    to_stack = get_input()
    if from_stack.is_empty():
      print("\n\nInvalid Move. Try Again")
    elif to_stack.is_empty() or from_stack.peek() < to_stack.peek():
      disk = from_stack.pop()
      to_stack.push(disk)
      num_user_moves += 1
      break
    else:
      print("\n\nInvalid Move. Try Again")
print(f"\n\nYou completed the game in {num_user_moves} moves, and the optimal number of moves is {num_optimal_moves}")
```

```python
from node import Node

class Stack:
  def __init__(self, name):
    self.size = 0
    self.top_item = None
    self.limit = 1000
    self.name = name

  def push(self, value):
    if self.has_space():
      item = Node(value)
      item.set_next_node(self.top_item)
      self.top_item = item
      self.size += 1
    else:
      print("No more room!")

  def pop(self):
    if self.size > 0:
      item_to_remove = self.top_item
      self.top_item = item_to_remove.get_next_node()
      self.size -= 1
      return item_to_remove.get_value()
    print("This stack is totally empty.")

  def peek(self):
    if self.size > 0:
      return self.top_item.get_value()
    print("Nothing to see here!")

  def has_space(self):
    return self.limit > self.size

  def is_empty(self):
    return self.size == 0

  def get_size(self):
    return self.size

  def get_name(self):
    return self.name

  def print_items(self):
    pointer = self.top_item
    print_list = []
    while(pointer):
      print_list.append(pointer.get_value())
      pointer = pointer.get_next_node()
    print_list.reverse()
    print("{0} Stack: {1}".format(self.get_name(), print_list))
```
