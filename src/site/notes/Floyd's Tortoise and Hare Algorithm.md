---
{"dg-publish":true,"permalink":"/floyd-s-tortoise-and-hare-algorithm/"}
---

Floyd's Tortoise and Hare algorithm, also known as Floyd's Cycle Detection algorithm, is an algorithm used to detect loops (cycles) in data structures like
- linked lists
- arrays (if the range of values can be mapped to the indices, making the values behave as pointers)
- graphs.

It has been proven to reliably detect cycles under specific circumstances and can be applied to finding duplicate elements.
# How it works
This algorithm employs two pointers, referred to as the "tortoise" and the "hare," to traverse the list.
- **Tortoise**: A pointer that advances one step at a time through the list.
- **Hare**: A pointer that advances two steps at a time through the list.
Using these pointers, you progress until the hare catches up with the tortoise or a cycle is detected.

Here's an overview of the algorithm:
1. **Phase 1 (Cycle Detection)**:  
    Move the tortoise and hare, advancing the hare twice as fast as the tortoise, until the hare catches up with the tortoise or a cycle is detected. If a cycle is detected, reset the tortoise and move the hare back to its position before the reset.
2. **Phase 2 (Cycle Start Detection)**:  
    Move the tortoise and hare one step at a time until they match again. The position where they match again is the starting point of the cycle, corresponding to the duplicate element.

>[!Proof]
>https://www.geeksforgeeks.org/dsa/how-does-floyds-slow-and-fast-pointers-approach-work/
# Complexity
- **Time complexity**: $O(n)$
- **Space complexity**: $O(1)$