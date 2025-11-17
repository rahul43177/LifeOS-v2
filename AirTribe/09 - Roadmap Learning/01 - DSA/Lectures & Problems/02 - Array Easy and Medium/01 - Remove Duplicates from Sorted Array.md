[Leetcode Link](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/)

###### Code
```javascript fold title:removeDuplicates.js 
function removeDuplicates(arr) {
	let j = 0;
	for(let i = 0;i<arr.length;i++) {
		if(arr[i] != arr[j]) { // found a new element 
			j+=1; //will replace with the next index so coming to the next index
			arr[j] = arr[i];
		}
	}
	return j+1;
}
```
