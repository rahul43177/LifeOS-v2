### Description in my words 
- So basically we are given an array where the element is either **1** or **0**
- So let's say the array is : `[1,0,0,1,1,0,1,1,1]`
- So at last , consecutively we got three ones -> and hence the ans or the output should be -> 3


### Code 
```js 
function maxConsecutiveOnes(nums) {
let maxOnes = 0;
let ones = 0;

	for(let i = 0;i<nums.length;i++) {
		if(nums[i] == 1) {
			ones++;
		} else {
			ones = 0;
		}
		maxOnes = Math.max(ones , maxOnes);
	}

	return maxOnes;

}

let array = [1,0,1,1,0,1]
let maxOnesInArray = maxConsecutiveOnes(array);
console.log(The max ones in the array ${array} are : ${maxOnesInArray});
```

