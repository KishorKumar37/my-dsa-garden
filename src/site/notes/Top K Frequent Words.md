---
{"dg-publish":true,"permalink":"/top-k-frequent-words/","tags":["string","hashing","trie","priorityQueue"]}
---

>[!Problem]

# Solution 1: Bucket Sort similar to [[347. Top K Frequent Elements#Solution 3 Bucket Sort\|347. Top K Frequent Elements#Solution 3 Bucket Sort]]
- **Time Complexity**: $O(n \log{n})$
- **Space Complexity**: $O(n)$
## Intuition
- Read solution from link for intuition
- But this is not $O(n)$ because when listing in lexicographical order, sorting takes $O(U \log{U})$ where $U$ is size of bucket, but if all words are unique then $U = n$
```python
class Solution:
    def topKFrequent(self, words: List[str], k: int) -> List[str]:
        counter = defaultdict(int)

        for word in words:
            counter[word] += 1
        
        buckets = [[] for _ in range(len(words))]

        for word, count in counter.items():
            buckets[count].append(word)
        
        del counter

        result = []
        for bucket in reversed(buckets):
            for word in sorted(bucket):
                result.append(word)
                k -= 1

                if k == 0:
                    return result
```
# Solution 2: Priority Queue of fixed size (similar to [[347. Top K Frequent Elements#Solution 2 Priority Queue of fixed size\|347. Top K Frequent Elements#Solution 2 Priority Queue of fixed size]])
- **Time Complexity**: $O(n \log{k})$
- **Space Complexity**: $O(n)$
## Intuition
- Read solution from link for intuition
- We don't need to sort here, instead when heap is full, also break tie between the min element and current word
