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
```
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