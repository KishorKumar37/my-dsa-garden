---
{"dg-publish":true,"permalink":"/dfs/"}
---

# [[Graph\|Graph]]
## Recursive

>[!Important]
>When using DFS to search from multiple starting points, the visited array should be reset for each unique path we are testing

```python
# graph - dict{int: list(int)}
# visited - set(int)

def dfs(node: int) -> None:
	nonlocal graph, visited
	print(node)
	visited.add(node)

	for neighbor in graph[node]:
		if neighbor not in visited:
			dfs(graph, neighbor)

	return
```
## Iterative

```python
def dfs(graph: dict, root: int) -> None:
	stack: list(int) = [root]
	visited: set(int) = set()

	while stack:
		node = stack.pop(-1)
		print(node)
		visited.add(node)
		
		for neighbor in graph[node]:
			if neighbor not in visited:
				stack.append(neighbor)

	return
```
# [[Tree\|Tree]]

## Recursive

```python
# graph - dict{int: list(int)}

def dfs(root: int) -> None:
	nonlocal graph
	print(root)

	for child in graph[root]:
		dfs(graph, child)

	return
```

## Iterative

```python
def dfs(graph: dict, root: int) -> None:
	stack: list(int) = [root]

	while stack:
		node = stack.pop(-1)
		print(node.val)
		
		for child in graph[node]:
			stack.append(child)

	return
```

# [[Binary Tree\|Binary Tree]]

## Recursive
```python
class Node:
	def __init__(self, val: int):
		self.val = val
		self.left = None
		self.right = None

def dfs(root: Node | None) -> None:
	if not root:
		return
	print(root.val)

	dfs(root.left)
	dfs(root.right)

	return
```

## Iterative

```python
class Node:
	def __init__(self, val: int):
		self.val = val
		self.left = None
		self.right = None
		
def dfs(root: Node) -> None:
	stack: list(Node) = [root]

	while stack:
		node: Node = stack.pop(-1)
		print(node.val)
		if node.left:
			stack.append(node.left)
		if node.right:
			stack.append(node.right)

	return
```

# [[Binary Search Tree\|Binary Search Tree]]

## Recursive

```python
class Node:
	def __init__(self, val: int):
		self.val = val
		self.left = None
		self.right = None

def dfsPreorder(root: Node | None) -> None:
	if not root:
		return
	print(root.val)

	dfs(root.left)
	dfs(root.right)

	return

def dfsInorder(root: Node | None) -> None:
	if not root:
		return

	dfs(root.left)
	print(root.val)
	dfs(root.right)

	return

def dfsPostorder(root: Node | None) -> None:
	if not root:
		return
	
	dfs(root.left)
	dfs(root.right)
	print(root.val)

	return
```

## Iterative

```python
class Node:
	def __init__(self, val: int):
		self.val = val
		self.left = None
		self.right = None

def dfsPreorder(root: Node) -> None:
	stack: list(Node) = [root]

	while stack:
		node: Node = stack.pop(-1)
		print(node.val)
		if node.left:
			stack.append(node.left)
		if node.right:
			stack.append(node.right)

	return
```