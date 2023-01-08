# Heap in Python

In Python, a heap is a specialized tree-based data structure that satisfies the heap property: if P is a parent node of C, then the key (the value) of P is either greater than or equal to (in a max heap) or less than or equal to (in a min-heap) the key of C. This implies that the highest (or lowest) key is always stored at the root of the heap.

Heaps are commonly implemented as arrays, with the parent node at index `i` and the children at indices `2i + 1` and `2i + 2`. However, the heap property only requires that the tree be a complete binary tree, meaning that all levels of the tree are fully filled except possibly the last level, which is filled from left to right.

The heap property allows for efficient retrieval and removal of the highest (or lowest) element in the heap. This makes heaps useful as a priority queue, where elements are added in any order but retrieved in a specific, priority-based order.

Python's `heapq` module provides an implementation of a heap queue, also known as a priority queue. The `heapq` module provides the following functions:

*   `heappush(heap, elem)`: Add `elem` to the heap.
    
*   `heappop(heap)`: Remove and return the smallest element from the heap.
    
*   `heappushpop(heap, elem)`: Add `elem` to the heap and then remove and return the smallest element from the heap.
    
*   `heapreplace(heap, elem)`: Remove and return the smallest element from the heap, and then add `elem` to the heap.
    

To use these functions, the elements in the heap must be sortable, either through the use of a comparison function or by making the elements themselves comparable.

Here is an example of using the `heapq` module in Python to implement a min heap:

```python
import heapq

heap = []

# Add elements to the heap
heapq.heappush(heap, 5)
heapq.heappush(heap, 2)
heapq.heappush(heap, 3)
heapq.heappush(heap, 1)

# Print the heap
print(heap)  # [1, 2, 3, 5]

# Remove and return the smallest element from the heap
print(heapq.heappop(heap))  # 1
print(heapq.heappop(heap))  # 2
print(heapq.heappop(heap))  # 3
print(heapq.heappop(heap))  # 5
```

In this example, the integers 1, 2, 3, and 5 are added to the heap in any order, but when they are popped from the heap, they are returned in sorted order from smallest to largest.

To implement a max heap, we can negate the values before adding them to the heap and then negate them again when they are popped from the heap:

```python
import heapq

heap = []

# Add elements to the heap
heapq.heappush(heap, -5)
heapq.heappush(heap, -2)
heapq.heappush(heap, -3)
heapq.heappush(heap, -1)

# Print the heap
print(heap)  # [-1, -3, -2, -5]

# Remove and return the largest element from the heap
print(-heapq.heappop(heap))  # 5
print(-heapq.heappop(heap))  # 3
print(-heapq.heappop(heap))  # 2
print(-heapq.heappop(heap))  # 1
```

Here are some videos that provide further explanations and examples of heaps:

*   [**Heaps in Data Structures - Computerphile**](https://www.youtube.com/watch?v=t0Cq6tVNRBA)
    
*   [**Heap Data Structure (Introduction) - GeeksforGeeks**](https://www.youtube.com/watch?v=t0Cq6tVNRBA)
    
*   [**Heap Sort Algorithm - GeeksforGeeks**](https://www.youtube.com/watch?v=MtQL_ll5KhQ)