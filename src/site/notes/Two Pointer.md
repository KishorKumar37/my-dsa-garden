---
{"dg-publish":true,"permalink":"/two-pointer/"}
---

# Selection sort type
```python
mainPointer: int = 0
iterationPointer: int = 0

while iterationPointer < len(array):
	if condition:
		array[mainPointer] = array[iterationPointer]
		mainPointer += 1
	iterationPointer += 1
```

# Window Type
- Use to find optimal window (min or max in size) that satisfies optimal condition (min or max)
- First pointer marks end of window and keeps adding element one by one
- If condition is achieved, second pointer moves to optimize condition further
- Optimal result is recorded in result
~~~tabs
tab: Python
```python
i: int = 0

for j in range(n):
	# include jth element in total
	if (/% condition achieved %/):
		while (/% condition achieved despite removing ith elem/%):
			# remove ith element
		
	# record optimal result
```
tab: C++
```cpp
int i = 0;
int result = 0;

for (int j = 0; j < n; j++) {
	while (i <= j && !condition)
		i++;

	result += j - i + 1; // For counting all subarrays
	result = max(result, j - i + 1); // For max subarray length
}
```
~~~






# Front and Back type
```python
result: int = 0
i: int = 0
j: int = len(array) - 1

while i < j:
	# value: int = some calculation
	# result = max / min(result, value)
	if /% equality condition %/ :
		# do something
	elif /% inequality condition one %/ :
		i += 1
	else /% inequality condition two %/ :
		j -= 1

return result
```