> Think of slice like *cutting a piece of cake* but **keeping the original cake untouched**.

#### Syntax 
```js 
array.slice(start , end); 
```

#### Key Points 
- Start and end are index -- we are passing the index 
- It does not mutate the original array which means it does not change anything in the original array. 
- It returns a new array. 
- `end` is not included the slicing happens till `end-1`
- It is basically used : **When we want to copy or just want some extract of an array**

#### Examples : 
###### Example 1 : Simple Slice
```javascript 
const arr = [10,20,30,40,50,60];
const result = arr.slice(1,3); 

console.log(result); // [20, 30]
console.log(arr);    // [10, 20, 30, 40, 50]  (unchanged)

```

- Here 
	- `start = 1`
	- `end = 3`
	- So the slicing will start from the 1st index that --> 20 
	- and goes till `end - 1` = 3-1 => 2 
	- Second index is -> 30 
- So the new array would look like -
	- `result = [20,30]`

###### Example 2 : Copy of full array 
```js title:copyArraySlice.js
const copy = array.slice()
```

> This will create a copy of array without changing anything in the original array. 
This is equivalent to : 
```js title:spreadOperator.js 
const copy = [...array]; 
```

###### Example 3 : Slice with negative index 
if we use negative index in slice -> it takes the elements from the last of the array 
```javascript title:sliceWithNegativeIndex.js
const array = [10,20,30,40,50]; 
const newArray = array.slice(-2)
// [4,5] → last 2 items
```




