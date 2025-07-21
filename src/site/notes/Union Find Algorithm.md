---
{"dg-publish":true,"permalink":"/union-find-algorithm/"}
---

```python
class UnionFind:
	def __init__(self, size: int):
		self.parent = list(range(size + 1))
	
	def find(self, key: int) -> int:
		if self.parent[key] == key:
			return key

		return self.parent[key] := self.find(self.parent[key])
	
	def union(self, key1: int, key2: int) -> bool:
		parent1 = self.find(key1)
		parent2 = self.find(key2)

		if parent1 != parent2:
			self.parent[parent1] = parent2
			return True

		return False
```
