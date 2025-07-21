---
{"dg-publish":true,"permalink":"/bfs/"}
---

# [[Graph\|Graph]]
## Iterative
```python
def bfs(graph: list[int], root: int):
	queue: deque(int) = deque([root])
	visited: set(int) = set()

	while queue:
		node: int = queue.popleft()
		print(node)
		visited.add(node)
		
		for child in graph[node]:
			if child not in visited:
				queue.append(child)

	return
```
## Iterative Level Order
```python
def bfs(graph: list[int], root: int):
	queue: deque(int) = deque([root])
	visited: set(int) = set()

	while queue:
		for _ in range(len(queue)):
			node: int = queue.popleft()
			print(node)
			visited.add(node)
			
			for child in graph[node]:
				if child not in visited:

	return
```
# [[Tree\|Tree]]
## Iterative
```python
def bfs(graph: list[int], root: int):
	queue: deque(int) = deque([root])

	while queue:
		node: int = queue.popleft()
		print(node)
		
		for child in graph[node]:
			if child not in visited:
				queue.append(child)

	return
```
## Iterative Level Order
```python
def bfs(graph: list[int], root: int):
	queue: deque(int) = deque([root])

	while queue:
		for _ in range(len(queue)):
			node: int = queue.popleft()
			print(node)
			
			for child in graph[node]:
				if child not in visited:

	return
```
# [[Binary Tree\|Binary Tree]] and [[Binary Search Tree\|Binary Search Tree]]
## Iterative
```python
class Node:
	def __init__(self, val: int):
		self.val = val
		self.left = None
		self.right = None

def bfs(root: Node):
	queue: deque(Node) = deque([root])

	while queue:
		node: Node = queue.popleft()
		print(node)
		if node.left:
			queue.append(node.left)
		if node.right:
			queue.append(node.right)

	return
```
## Iterative Level Order
```python
class Node:
	def __init__(self, val: int):
		self.val = val
		self.left = None
		self.right = None

def bfs(root: Node):
	queue: deque(Node) = deque([root])

	while queue:
		for _ in range(len(queue)):
			node: Node = queue.popleft()
			print(node)
			if node.left:
				queue.append(node.left)
			if node.right:
				queue.append(node.right)

	return
```