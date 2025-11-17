https://leetcode.com/problems/move-zeroes/description/

### Description in my words 
- We are given an array 
- We have to move all the zeroes to the right 
- we have to maintain the non-zero element orders

One example -> 
`nums = [0,1,0,3,12]`
- Now we will move the zeroes to the right 
- that will make the num as : 
- `[1,3,12,0,0]` -> so the elements which were coming in the order should be maintained. 

### Approach and code
[[move_zeroes]]

```js fold title:moveZeroes.js
function moveZeroes(nums) {
	let j = 0;
	for(let i = 0;i<nums.length;i++) {
		//finding non zero element and moving them at j index
		if(nums[i]!=0) {
			nums[j] = nums[i];
			j++;
		}
	}
	
	//whatever is left , we will insert 0 in them and we will from where j is 
	for(let k = j;k<nums.length;k++) {
		nums[k] = 0;
	}
}
```

