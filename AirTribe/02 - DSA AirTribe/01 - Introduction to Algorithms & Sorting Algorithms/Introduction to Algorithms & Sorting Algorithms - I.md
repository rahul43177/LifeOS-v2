## Class Structures 
- There will be 16 sessions 
![[../../../attachments/Introduction to Algorithms & Sorting Algorithms - roadmap.png]]
- It will be in 3 phase


## Time and Space complexity
Time and Space complexity basically defines a relation between our Algorithm and the resources required to run it. 

Recourse : Execution and memory. 
We have three cases : 
1. Best case 
2. Average Case 
3. Worst Case 
![[../../../attachments/Introduction to Algorithms & Sorting Algorithms - I - three cases.png]]
##### Some Rules for the Big O notations
1. We only care about the largest polynomial values 
2. We can ignore the constants or lesser values

##### The framework to find the TC 
![[../../../attachments/Introduction to Algorithms & Sorting Algorithms - I - TC - framework.png]]


## Arrays 
- Contiguous blocks of memory 
- Each block some data is stores
![[../../../attachments/Introduction to Algorithms & Sorting Algorithms - I - array.png]]
**We can declare an array**
- `const arr = []`
- `new Array` method

#### Problem 1 : We have to find the key in the array
![[../../../attachments/Introduction to Algorithms & Sorting Algorithms - I - find array.png]]
So there could be two approached 
1. Simple brute force - Linear Search
2. Sort the array - Binary Search

##### Linear Search 
```js fold title:linearSearch.js 
const arr = [1,2,4,8,2,3,7,1];
const key = 8;

function search(arr , key) {
	for(let i = 0;i<arr.length;i++) {
		if(arr[i] == key) {
			return i;
		}
	}
	return -1;
}

console.log(search(arr , key));
```



## Sorting
### Bubble Sort 
![[../../../attachments/Introduction to Algorithms & Sorting Algorithms - I - bubble sort.png]]
- Largest Bubble pops out first 
- In each iteration we will correctly place the largest element in the unsorted array. 

`arr = [8,4,2,3,6]`
1. Run the linear Traversal 
2. Compare the adjacent (`i` and `i+1` )
3. `ai > ai+1` -> swap 
##### Bubble sort Code : 
```js
function bubbleSort(arr) {
	let n = arr.length;
	for(let iterations = 0;iterations < n-1;iterations++) {
		let didWeMakeSwap = false;
		for(let i = 0;i<n-1;i++) {
			let temp = arr[i];
			arr[i] = arr[i+1];
			arr[i+1] = temp;
			didWeMakeSwap = true; 
		}
		console.log({iterations , arr});	
		if(!didiWeMakeSwap) {
			break;
		}
	}
}
```

letting 