If we don't create any create a copy and simply assign the variable it will pass the reference of the array and hence it will change the original array. 

#### Few methods : 
1. [[../../../../01 - Backend/04 - JavaScript Deep Dive/Slice Method|Slice Method]]
2. spread operator 
3. `Array.from()`


##### Using the Array.slice() Method
```js
const originalArray = [1, 2, 3];
const clonedArray = originalArray.slice();
console.log(clonedArray);
```


##### Using spread operator 
```js 
const originalArray = [1, 2, 3];
const clonedArray = [...originalArray];
console.log(clonedArray);
```

##### Using the Array.from() Method
```js
const originalArray = [1, 2, 3];
const clonedArray = Array.from(originalArray);
console.log(clonedArray);
```

