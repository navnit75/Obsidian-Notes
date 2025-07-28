---
title: Heaps in CPP
description: Working of Heaps in CPP
tags:
  - cpp
  - heaps
---
## Approach 1 (using `priority_queue`) 
### 1. Max Heap


```cpp
// default a Max Heap 
#include <bits/stdc++.h> 
...
priority_queue <int> pq; 
pq.push(5); 
pq.push(1); 

// One by one extract items from max heap 
while (pq.empty() == false) { 
	cout << pq.top() << " "; 
	pq.pop(); 
} 
```

Sample Output 
```
5 1
```
### 2. Min Heap
```cpp
priority_queue<int, vector<int>, greater<int>> pq; 
pq.push(5); 
pq.push(1); 

// One by one extract items from max heap 
while (pq.empty() == false) { 
	cout << pq.top() << " "; 
	pq.pop(); 
} 
```

Sample Output
```
1 5
```

#### `std::greater<int>`

- The **std::greater** is a functional object which is used for performing comparisons. 
- It is defined as a Function object class for the greater-than inequality comparison. 
- This can be used for changing the functionality of the given function. This can also be used with various standard algorithms such as [sort](https://www.geeksforgeeks.org/sort-c-stl/), [priority queue](https://www.geeksforgeeks.org/priority-queue-set-1-introduction/), etc.

**Header File:**
```
#include <functional.h>
```

**Template Class:**
```
template <class T> struct greater;
```

**Parameter:** **T** is a type of the arguments to compare by the functional call.
**Return Value:** It returns boolean variable as shown below:
- **True:** If two element say(a & b) such that a > b.
- **False:** If a < b.

### 3. Playing with Custom Classes
```cpp title="Point.cpp"
// User defined class, Point 
class Point { 
	int x; 
	int y; 
	public: 
	Point(int x, int y) 
	{ 
		this->x = x; 
		this->y = y; 
	} 
	int getX() const { return x; } 
	int getY() const { return y; } 
}; 
```

```cpp
// To compare two points 
class myComparator { 
public: 
	int operator() (const Point& p1, const Point& p2) { 
		return p1.getX() > p2.getX(); 
	} 
}; 
```

```cpp
priority_queue <Point, vector<Point>, myComparator > pq; 

	// Insert points into the min heap 
pq.push(Point(10, 2)); 
pq.push(Point(2, 1)); 
pq.push(Point(1, 5)); 

// One by one extract items from min heap 
while (pq.empty() == false)	{ 
	Point p = pq.top(); 
	cout << "(" << p.getX() << ", " << p.getY() << ")"; 
	cout << endl; 
	pq.pop(); 
} 
```

Sample Output 
```
(1, 5)
(2, 1)
(10, 2)
```

### 4. Comparator Logic

>[!important] The comparator logic works opposite
>$\rightarrow$ If you want to use a $min\ heap$  , you need to return `[](int a, int b) return a > b; `
>$\rightarrow$ If you want to use a $max\ heap$, well don't do anything as by default `priority_queue` act as `max heap` or `[](int a,int b) return a < b; `
>>[!quote] This logic is completely opposite in case you use $sort$ function on vector with comparator `[](int a, int b) return a > b; ` this will return decreasing order and vice versa on `[](int a, int b) return a < b; `


- Function calls are like stack, $push$, $pop$ and $top$. 
- By default its a $max\ heap$. 
- Comes with header $bits/stdc++.h$ 


### 5. Working with `pair` class
- When you work with `pair` class do remember that, the $maxHeap$ and $minHeap$ operations are based on $first$ value of the pair. 
- For example : So if you make something like `priority_queue<pair<int,char>> pq;` the priority queue will work according to the $integer$ value stored in the $pq$. 


## Approach - 2 ( using `make_heap`)
### Max Heap ( default)

#### 1. make_heap()

> $\rightarrow$ $make\_heap()$: Converts given range to a heap.

```cpp
// Initializing a vector
vector<int> v1 = { 20, 30, 40, 25, 15 };
// Converting vector into a heap
make_heap(v1.begin(), v1.end());

// Displaying the maximum element of heap
// using front()
cout << "The maximum element of heap is : ";
cout << v1.front() << endl;
```

Sample Output 
```
The maximum element of heap is : 40
```

```
TC : O(N) , N = # elements 
Aux Space : O(1)
```
#### 2. push_heap()

> $\rightarrow$ $push\_heap()$: Arrange the heap after insertion at the end.

```cpp
// Initializing a vector
vector<int> vc{ 20, 30, 40, 10 };
make_heap(vc.begin(), vc.end());

// Push Operation
vc.push_back(50);
push_heap(vc.begin(), vc.end());

cout << "Heap after push_heap(): ";
print(vc);
```

Sample Output 
```
Heap after push_heap(): 50 40 20 10 30
```

```
TC : O(logN), N = # elements
```
#### 3. pop_heap()

> $\rightarrow$ $pop\_heap()$: Moves the max element at the end for deletion

```cpp
// Initializing a vector
vector<int> vc{ 40, 10, 20, 50, 30 };
make_heap(vc.begin(), vc.end());

// Push Operation
pop_heap(vc.begin(), vc.end());
vc.pop_back(); 
cout << "Heap after pop_heap(): ";
print(vc);
```

Sample Output 
```
Heap after pop_heap(): 40 30 20 10
```

```
TC : O(logN), N = # elements
```

#### 4. sort_heap()

> sorts the heap in $ascending$ order.

```cpp
// Initializing a vector
vector<int> v1 = { 20, 30, 40, 25, 15 };
make_heap(vc.begin(), vc.end());

// Sort Operation
sort_heap(vc.begin(), vc.end());
print(vc);
```

```
The heap elements after sorting are: 15 20 25 30 40
```

```
TC : O(NlogN), N = # elements
```

#### 5. is_heap()

> Checks if the given range is max_heap.

```cpp
bool ans = is_heap(vc.begin(), vc.end()); 
```

#### 6. is_heap_until()

> returns the iterator to the position till the container is heap

```cpp
auto it = is_heap_until(v.begin(), v.end()); 
```

### Min Heap 
```cpp
#include <iostream>
#include <vector>
#include <algorithm> // For make_heap, push_heap, pop_heap

int main() {
    // Step 1: Create a vector of elements
    std::vector<int> minHeap = {10, 20, 15, 30, 40};

    // Step 2: Convert the vector into a min heap
    std::make_heap(minHeap.begin(), minHeap.end(), std::greater<int>());

    std::cout << "Min Heap: ";
    for (int val : minHeap) std::cout << val << " ";
    std::cout << std::endl;

    // Step 3: Insert a new element (5) and maintain heap property
    minHeap.push_back(5); 
    std::push_heap(minHeap.begin(), minHeap.end(), std::greater<int>());

    std::cout << "After pushing 5: ";
    for (int val : minHeap) std::cout << val << " ";
    std::cout << std::endl;

    // Step 4: Remove the minimum element
    std::pop_heap(minHeap.begin(), minHeap.end(), std::greater<int>());
    minHeap.pop_back(); // Actually remove the element from the vector

    std::cout << "After popping min: ";
    for (int val : minHeap) std::cout << val << " ";
    std::cout << std::endl;

    return 0;
}
```