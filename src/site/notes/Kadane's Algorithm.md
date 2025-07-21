---
{"dg-publish":true,"permalink":"/kadane-s-algorithm/"}
---

- **Time Complexity**: $O(n)$
- **Space Complexity**: $O(1)$
## Intuition
- Result starts at the first number
- We keep incrementing a variable total (initialized at 0) by the numbers
- If total becomes 0 at any point, then we discard it (reset to 0)
- Result is maximum of result and total till this point
>[!important]
>- When used with sub-array sum, the total resetting should happen first before adding the number and updating result, so that the first number initialization of result as the minimum value is not lost
>- For custom sub-array value calculations, resetting can be moved to after adding number


```python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        res = nums[0]
        total = 0

        for num in nums:
            total = max(total, 0)
            total += num
            res = max(res, total)
        
        return res
```