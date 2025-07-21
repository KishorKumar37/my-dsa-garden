---
{"dg-publish":true,"permalink":"/lru-cache/","tags":["linkedList","doublyLinkedList","hashing","design"]}
---

```python
class Node:
    def __init__(self, key: int | None, value: int | None):
        self.key = key
        self.value = value
        self.next: Node | None = None
        self.prev: Node | None = None

def synchronized(lock_getter):
    def decorator(func):
        @functools.wraps(func)
        def wrapper(self, *args, **kwargs):
            lock = lock_getter(self)
            with lock:
                return func(self, *args, **kwargs)
        return wrapper
    return decorator

import functools
import threading

class LRUCache:
    def __init__(self, capacity: int):
        self.lock = threading.Lock()
        self.__capacity = capacity
        self.__cache: dict = {}  # key: Node
        # Linked List
        self.__head = Node(key=None, value=None)
        self.__tail = Node(key=None, value=None)
        self.__head.next = self.__tail
        self.__tail.prev = self.__head

    def __add_to_head(self, node: Node):
        node.next = self.__head.next
        node.prev = self.__head

        assert type(self.__head.next) == Node
        self.__head.next.prev = node
        self.__head.next = node

    def __remove_node(self, node: Node) -> None:
        assert type(node.next) == Node
        assert type(node.prev) == Node

        node.next.prev = node.prev
        node.prev.next = node.next

    def __move_to_head(self, node: Node):
        self.__remove_node(node)
        self.__add_to_head(node)

    def get(self, key: int) -> Node | None:
        if key in self.__cache:
            node = self.__cache[key]
            self.__move_to_head(node)
            return node

        return None

    def __remove_tail(self) -> Node:
        assert type(self.__tail.prev) == Node

        last_node = self.__tail.prev
        self.__remove_node(last_node)
        return last_node

    def put(self, key: int, value: int) -> None:
        if key in self.__cache:
            node = self.__cache[key]
            node.value = value
            self.__move_to_head(node)
        else:
            if len(self.__cache) == self.__capacity:
                last_node = self.__remove_tail()
                del self.__cache[last_node.key]

            node = Node(key, value)
            self.__add_to_head(node)
```