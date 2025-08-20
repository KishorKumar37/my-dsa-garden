---
{"dg-publish":true,"permalink":"/trie/"}
---

The purpose of the `isEndOfWord` marker is to distinguish between *app* and *apple*. When only these words are in the tree, then marker will be true at *app* but we should stop only when the number of children is 0

```python
class TrieNode:
	def __init__(self):
		self.children = {}
		self.isEndOfWord = False

class Trie:
	def __init__(self):
		self.root = TrieNode()
            
	def insert(self, key: str):
		curr = self.root
		for char in key:
			if char not in curr.children:
				curr.children[char] = TrieNode()
			curr = curr.children[char]

		curr.isEndOfWord = True
```

- If we go through the nodes of trie using a key, then we have the char at each branch. So we can store the children in an array
- If we need to search the branches ourselves, like when finding LCP, we should use a map instead, so that only the inserted children are available

```cpp
class Trie {
    class TrieNode {
        public:
            std::unordered_map<char, std::shared_ptr<TrieNode>> children;
            bool endofWord;
            TrieNode()
            : endofWord(false) {}
    };
private:
    std::shared_ptr<TrieNode> root;

public:
    Trie()
    : root(make_shared<TrieNode>()) {}
    
    void insert(string word) {
        std::shared_ptr<TrieNode> current = root;
        for (char& ch : word) {
            if (current->children.count(ch) == 0) {
                current->children[ch] = make_shared<TrieNode>();
            }
            current = current->children[ch];
        }
        current->endofWord = true;
    }
    
    bool search(string word, bool prefix=false) {
        std::shared_ptr<TrieNode> current = root;
        for (char& ch : word) {
            if (current->children.count(ch) == 0) return false;
            current = current->children[ch];
        }
        if (!prefix) return current->endofWord;
        return true;
    }
    
    bool startsWith(string prefix) {
        return search(prefix, true);
    }
};
```