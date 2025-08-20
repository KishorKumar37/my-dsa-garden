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

```cpp
class DisjointSet {
private:
    vector<int> parent;
    int redundantEdges;
    int islands;
public:
    DisjointSet(int size) {
        parent.resize(size);
        for (int i = 0; i < size; i++) {
            parent[i] = i;
        }
        islands = size;
        redundantEdges = 0;
    }
    int find(int key) {
        if (parent.at(key) == key) return key;
        return parent[key] = find(parent.at(key));
    }
    void unite(int key1, int key2) {
        int parent1 = find(key1);
        int parent2 = find(key2);

        if (parent1 == parent2) redundantEdges++;
        else {
            parent[parent1] = parent2;
            islands--;
        }
    }
    int getIslands() {
        return islands;
    }
    int getRedundantEdges() {
        return redundantEdges;
    }
};
```
