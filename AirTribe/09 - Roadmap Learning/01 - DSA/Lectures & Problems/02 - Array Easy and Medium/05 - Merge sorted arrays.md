### Description in my words
- There are two arrays which are given to us 
- let's say `nums1` and `num2`
- Now we don't have to create a new array , but change the `nums1` array such that , we have both the array but in the sorted order 


so example is :  
`nums1 = [1,2,3,0,0,0]`
`nums2 = [2,5,6]`

here `nums1` contains only 3 elements which are 1,2,3 , but other zeroes are present in order to merge `nums2` into `nums1`

So these 0 , 0 , 0 -> these are just dummy filler spaces to merge `nums2`

And these two arrays will be present in [[non-decreasing order]]

### Approach 1 - Brute force approach
- Just put everything in the `nums1` array and then sort the array which resolves this problem
- But this is not a good solution and called as Brute Force approach

TC of this solution 
$$
O((n+m)log(m+n))
$$

And this is not a good solution overall



### Approach 2 - With extra space and `nums` copy
- Create a copy of `nums1` or `n1` which will be `n1Copy`
- `n1 = [1,2,3]` 
- `n1Copy = [1,2,3]`
- `n2 = [2,5,6]`
- so merging `num2` into `nums1` , so we can do something like this : [[merge_sorted_array_extra_space_logic_diagram]] -> Study this , this is the merging approach . 
- This is not the best approach but still a thought provoking 

#### Code for approach 2
- First we will create a copy of `nums1` -> [[How to create a copy of an array in JS]]
- Now two pointers `p1` and `p2`
- now we will run a loop
- now inside the for loop , we will check the  condition that 
	- `nums1Copy[p1] < nums2[p2]` -> so whoever is smaller that is going into the `nums1`
	- `num1[i] = nums1Copy[p1]` and then we will move our p1++
- Now there can also be a case where `p1` is over. so there should be one more check for that which could be :-> `p1 < m && nums1Copy[p1] < nums2[p2]` 
- So there will also be a case where `p2` goes out of bound , `p2 >= n || (the previous condition`
- So these conditions are to handle corner cases. 

The condition which is being used : 
- `p2 >= n` -> this checks p2 is out of bound , then copy p1. 
- `p1 < m` -> we are also checking p1 is left and is not out of the bound 
- `nums1Copy[p1] < nums2[p2]` => checking whoever is smaller and putting it in the `nums1`

 ```js fold title:mergeSortedArrayExtraSpace.js
function mergeSortedArray(nums1, m , nums2 , n) {
	let nums1Copy = nums1.slice(0,m);
	let p1 = 0;
	let p2 = 0;
	
	for(let i = 0;i<m+n;i+=1) {
		if(p2 >= n || (p1 < m && nums1Copy[p1] < nums2[p2] )) {
			nums1[i] = nums1Copy[p1];
			p1++;
		} else {
			nums1[i] = nums2[p2];
			p2++;
		}
	}
		
}
```

#### Complexity Analysis
- **Time Complexity**: O(m + n) because we iterate through both arrays once.
- **Space Complexity**: O(m) due to the `nums1Copy` array.

---

### Approach 3 - Optimal Solution ([[in place]] merge from the end without using extra space)

In this approach let's say we have arrays : 
`nums1 = [1,2,3,0,0,0]`
`nums2 = [2,5,6]`

- So thing about filling nums1 array in the reverse order
- Because if we fill it from the start we will lose the elements , so we will start from where the dummy empty space is present. 
- Optimized dry run : [[optimised_merge_sorted_array]]

##### Code logic
- Now we will take two pointers p1 and p2 and these two pointers will start from the last of the respective arrays.
- Now we will run the loop in reverse order -> `for(let i = m+n-1;i>=0;i--)`
- Now some conditions 
	1. I will check both the pointers which one is greater , then I will replace the element from the last -> `nums1[p1] > nums2[p2]` and if this is true -> `p1--` and the vice versa is handled in the else condition. 
	2. Now if our p2 is out of the bound we don't have to anything.
	3. but if our p1 if out of the bound , then we run the else condition where p2 is still left , so entire thing will be pasted there. 

This is not an easy question , this is medium
###### The Code
```js fold title:mergeSortedArray.js
function merge(nums1 , m , nums2 , n) {
	let p1 = m-1; //starting from last
	let p2 = n-1; 
	
	//starting the for loop from last
	for(let i  = m+n-1;i>=0;i--) {
		if(p2 < 0) break; //if p2 goes out of the bound , we don't have to do anything. 
		//p1 is in the bound && p1 element is greater than p2 element.
		if(p1>=0 && nums1[p1] > nums2[p2] ) { 
			nums1[i] = nums1[p1];
			p1--;
		} else {
			nums1[i] = nums2[p2];
			p2--;
		}
	}
}
```

Extra note : is p2 is out of bound , we don't have to do anything , as p1 is already there 
but is p1 is out of bound , we need to take care of the p2 and hence it will be executed in the else condition. 
