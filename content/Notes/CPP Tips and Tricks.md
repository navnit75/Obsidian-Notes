## 1. Traversing Map or Priority Queue
- Specially when you have the class templates with multiple parameters i.e.`<int, char> or <pair<int,int>> or <char,int>`. 
- You can traverse `priority_queue`using the following code - 

```cpp
unordered_map<int,char> umap; 
for(auto &[firstValue, secondValue] : umap) {
	...
	cout << firstValue <<endl; 
	cout << secondValue << endl;
}
```

```cpp
priority_queue<pair<int,char>> maxHeap; 
maxHeap.push({95,'a'}); 
auto [frequency, character] = maxHeap.top(); maxHeap.pop(); 
```

## 2. Returning vector from functions, when you have less values 
- You can just use `{a,b}` to return the values as vector

```cpp
vector<int> someFunction(int a,int b){
    return {a,b};
}
```

## 3. Iterating through an `unordered_map`
- Don't expect `unordered_map` to follow $insertion$ order. 

```cpp
for(auto x : umap){
	...
    // access the keys using 
    cout << x.first;
    // access the values using
    cout << x.second; 
}
```

## 4. Using `abs`
```cpp
#include<cstdlib>
..
..
int main(){
	cout << abs(-5) << endl; 
}
// Output : 5
```
## 5. Using Comparator for `sort`
- Sorting a 2D vector *using* first ***element*** of the vector
- We need to return , the order we **wish** to see in our $resultant\ array$. 
- So `return v1[0] < v2[0]`. ****

```cpp
/* Comparator */
bool comparator(vector<int> &v1, vector<int> &v2) {
	return v1[0] < v2[1];
}

/* Call */
int main(){
	/* Intializing a 2D vector */
	vector<vector<int>> intervals{
		{1, 2},
		{3, 5},
		{4, 7},
		{6, 8},
		{9, 10}
	};
	
	/* Sorting */
	sort(intervals.begin(), intervals.end(), comparator);

	
	/* Return 0 */ 
	return 0; 
}
```
#### 6. Using lambda function for comparator 
- Sorting can be provided by the use of lambda function as well.

```cpp
sort(arr.begin(),arr.end(),[](vector<int> a, vector<int> b){return a[0] < b[0];}); 
```

#### 7. Swapping using two variables 

```cpp
void swap_one(int &a , int &b){
    a = a - b; 
    b = b + a; 
    a = b - a; 
}

void swap_two(int &a , int &b){
    a = a + b; 
    b = a - b; 
    a = a - b; 
}

void swap_three(int &a , int &b){
    a = a * b; 
    b = a / b; 
    a = a / b; 
}

void swap_four(int &a , int &b){
    b = (a+b) - (a = b);  
}
```
