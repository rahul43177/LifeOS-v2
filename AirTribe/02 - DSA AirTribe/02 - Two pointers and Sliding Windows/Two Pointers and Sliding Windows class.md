## Two Pointers
- We take two variables and in one iteration we check the array 
- It always works on the sorted array 

### Thinking Process of 2 Pointers
Whenever we need to 
1. Compare
	1. Remove element 
	2. elements in sorted manner 
2. Combine  
the 2 elements without the <span style="background:#fdbfff">extra space</span>  , then we should use 2 pointers.
Thinking process when to use 2 pointers 
![[../../../attachments/Two Pointers and Sliding Windows class - thinking process.png]]

## Sliding Window
Sliding window is technique , 2 pointers help us achieve this. 
### Explanation 
![[../../../attachments/00 - Two Pointers and Sliding Windows class - sliding window.png]]
Window -> Always follow a condition (Problem)
We can expand or shrink till the condition is met. 

#### When to use this ? 
1. Range -> Monotonic



### How sliding windows work ? 
```js 
let array = [0 , 1 , 1 , 0 , 0 , 1 , 1 , 0 , 1 , 1] 
let k = 2;
```

![[../../../attachments/00 - Two Pointers and Sliding Windows class - sliding window-1.png]]




### Problem : 
1. [[Container With Most Water]]
2. [[Max Consecutive Ones III]]