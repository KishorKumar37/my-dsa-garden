---
{"dg-publish":true,"permalink":"/binary-search/"}
---

# Exact Value Search
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
# Minimum/Maximum value that satisfies condition
Condition can be simple like
- Minimum value greater that target
- Maximum value less than target

or business logic as well. Simply change the comparison in condition
- $\leq$ for minimum value
- $\geq$ for maximum value
```python
class Solution:
	def conditionAndMin(array: list(int), mid: int, target: int) -> bool:
		# business logic using mid to calculate a value
		if value <= target:
			return True
		else:
			return False

	def conditionAndMax(array: list(int), mid: int, target: int) -> bool:
		# business logic using mid to calculate a value
		if value >= target:
			return True
		else:
			return False
	
	def binarySearchMin(array: list(int), low: int, high: int, target: int) -> int:
	while low <= high:
		mid = (low + high) // 2
		if array[mid] == target:
			result = mid
			return result
		if conditionAndMin(array, mid, target):
			result = mid
			low = mid + 1
		else:
			high = mid - 1
	return result

	def binarySearchMin(array: list(int), low: int, high: int, target: int) -> int:
		while low <= high:
			mid = (low + high) // 2
			if array[mid] == target:
				result = mid
				return result
			if conditionAndMax(array, mid, target):
				result = mid
				high = mid - 1
			else:
				low = mid + 1
		return result
```
