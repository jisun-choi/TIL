## Tree

- Array & Linked List: linear data structure (선형적 자료구조)
- Tree: hierarchical (non-linear) data structure (계층적 자료구조)

비선형적 자료구조이기 때문에 데이터의 삽입과 삭제가 쉽지 않다는 단점이 있지만,
balanced tree structure 라는 조건 하에 빠른 검색 성능을 보장한다.

출처 ---> [Data Structures: Trees
](https://www.youtube.com/watch?v=oSWTXtMglKE&t=446s)

### 트리의 구조

![](https://images.velog.io/images/wltjs10645/post/7c838cfb-ac89-403f-8cd3-d63482028422/image.png)

```python
# The Node Class defines the structure of a Node
class Node:
    # Initialize the attributes of Node
    def __init__(self, data):
        self.left = None # Left Child
        self.right = None # Right Child
        self.data = data # Node Data


root = Node(10) # Instantiating the Tree
#        10
#      /    \
#     None   None

root.left = Node(34) # Setting the left child of the root to 34
root.right = Node(89) # Setting the right child of the root to 89

#          10
#        /    \
#       34      89
#     /    \  /    \
#  None  None None None
```

## Tree traversals (트리 순회)

특정 순서로 트리 구조의 모든 노드를 순회하는 것

- in-order traversal
- pre-order traversal
- post-order traversal
  ![](https://images.velog.io/images/wltjs10645/post/726e24a0-f2a9-40d3-9705-d697b98e9c05/image.png)

### In-order traversal

1. Process the nodes in the left subtree with a recursive call.
2. Process the root.
3. Process the nodes in the right subtree with a recursive call.

```python
def inorder(node):
    if node:
        # Recursively call inorder on the left subtree until it reaches a leaf node
        inorder(node.left)

        # Once we reach a leaf, we print the data
        print(node.data)

        # since the left subtree and the root has been printed,
        # call inorder on right subtree recursively until we reach a leaf node.
        inorder(node.right)

# For the tree,
#          10
#        /    \
#       34      89
#     /    \  /    \
#  20     45  56    54

# Inorder traversal: 20 34 45 10 56 89 54
```

### Pre-order traversal

1. Process the root.
2. Process the nodes in the left subtree with a recursive call.
3. Process the nodes in the right subtree with a recursive call.

```python
def preorder(node):
    if node:
        # Print the value of the root node first
        print(node.data)

        # Recursively call preorder on the left subtree until we reach a leaf node.
        preorder(node.left)

        # Recursively call preorder on the right subtree until we reach a leaf node.
        preorder(node.right)

# For the tree,
#          10
#        /    \
#       34      89
#     /    \  /    \
#  20     45  56    54

# Preorder traversal: 10 34 20 45 89 56 54
```

### Post-order traversal

1. Process the nodes in the left subtree with a recursive call.
2. Process the nodes in the right subtree with a recursive call.
3. Process the root.

```python
def postorder(node):
    if node:
        # Recursively call postorder on the left subtree until we reach a leaf node.
        postorder(node.left)

        # Recursively call postorder on the right subtree until we reach a leaf node.
        postorder(node.right)

        # Print the value of the root node
        print(node.data)

# For the tree,
#          10
#        /    \
#       34      89
#     /    \  /    \
#  20     45  56    54

# Postorder traversal: 20 45 34 56 54 89 10

```

[Using the Binary Tree Data Structure in Python](https://www.section.io/engineering-education/binary-tree-data-structure-python/)
