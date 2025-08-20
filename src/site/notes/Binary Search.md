---
{"dg-publish":true,"permalink":"/binary-search/"}
---

# Exact Value Search

For exact value search, our focus is on the pointer $m$. 

- If `arr[m]` hits the `target`, we return the `m`
- Else if `arr[m]` is less than the target, then target is possibly on the right side of `m`, so we move `l` to `m + 1`
- Else `arr[m]` is greater than the target and target is possibly on the left side of `m`, so we move `r` to `m - 1`
## Iterative

```python
class Solution:
	def binarySearch(array: list(int), low: int, high: int, target: int) -> int:
	while low <= high:
		mid = (low + high) // 2
		
		if array[mid] == target:
			result = mid
			return result
	
		if array[mid] < target:
			low = mid + 1
		else:
			high = mid - 1

	return -1 # Target not found
```

## Recursive

In recursive approach, the result also needs to be tracked and passed in the function

```python
class Solution:
	def binarySearch(array: list(int), low: int, high: int, target: int, result: int) -> int:
	if low > high:
		return -1 # Target not found

	mid = (low + high) // 2
	if array[mid] == target:
		result = mid
		return result

	if array[mid] < target:
		low = mid + 1
	else:
		high = mid - 1
		
	return binarySearch(array, low, high, target, result)
```

# Minimum value that satisfies condition

For minimum value search

- If `arr[m]` is lesser than the `target`, then `m` is not a valid candidate and we need to search on it's right side, so we move `l` to `m + 1`
- Else if `arr[m]` is greater than or equal to `target` (equal to because the `target` itself could also exist in the array), then `m` is a valid candidate but there could be something more minimum on the left side of `m`, so we move `r` to `m - 1`

Because we want to track the best candidate so far, we need to assign the candidate itself to `r` instead of 1 step further. This will cause an infinite loop for `while (l <= r)` so we use inequality and we will get the best candidate in `r` at the end

```python
class Solution:
	def binarySearch(array: list(int), target: int):
		l, r = 0, len(array) - 1
		while l < r:
			m = (l + r) // 2
			if array[m] < target:
				l = m + 1
			else:
				r = m
				
		return r
```

# Maximum value that satisfies condition

For maximum value search

- If `arr[m]` is greater than the `target`, then `m` is not a valid candidate and we need to search on it's left side, so we move `r` to `m - 1`
- Else if `arr[m]` is lesser than or equal to `target` (equal to because the `target` itself could also exist in the array), then `m` is a valid candidate but there could be something more maximum on the right side of `m`, so we move `l` to `m + 1`

Because we want to track the best candidate so far, we need to assign the candidate itself to `l` instead of 1 step further. This will cause an infinite loop for `while (l <= r)` so we use inequality and we will get the best candidate in `l` at the end

```python
class Solution:
	def binarySearch(array: list(int), target: int):
		l, r = 0, len(array) - 1
		while l < r:
			m = (l + r) // 2
			if array[m] > target:
				r = m - 1
			else:
				l = m
				
		return l
```

