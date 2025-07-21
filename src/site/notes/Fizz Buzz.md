---
{"dg-publish":true,"permalink":"/fizz-buzz/","tags":["string"]}
---

>[!Problem]
>Given an integer `n`, return _a string array_ `answer` _(**1-indexed**) where_:
> - `answer[i] == "FizzBuzz"` if `i` is divisible by `3` and `5`.
> - `answer[i] == "Fizz"` if `i` is divisible by `3`.
> - `answer[i] == "Buzz"` if `i` is divisible by `5`.
> - `answer[i] == i` (as a string) if none of the above conditions are true.
> 
> **Example 1:**
> 
> **Input:** n = 3
> **Output:** ["1","2","Fizz"]
> 
> **Example 2:**
> 
> **Input:** n = 5
> **Output:** ["1","2","Fizz","4","Buzz"]
> 
> **Example 3:**
> 
> **Input:** n = 15
> **Output:** ["1","2","Fizz","4","Buzz","Fizz","7","8","Fizz","Buzz","11","Fizz","13","14","FizzBuzz"]
> 
> **Constraints:**
> 
> - `1 <= n <= 104`

# Solution
- **Time Complexity**: $O(n)$
- **Space Complexity**: $O(1)$
## Intuition
```python
class Solution:
    def fizzBuzz(self, n: int) -> List[str]:
        answer = []
        for i in range(1, n + 1):
            if i % 15 == 0:
                answer.append("FizzBuzz")
                continue
            if i % 3 == 0:
                answer.append("Fizz")
                continue
            if i % 5 == 0:
                answer.append("Buzz")
                continue
            answer.append(f"{i}")
        return answer
```