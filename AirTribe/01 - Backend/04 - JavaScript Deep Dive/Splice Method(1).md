> Think of splice like **removing pieces** from the ***original cake*** itself.

#### Syntax
```js title:spliceSyntax.js
array.splice(start , deleteCount , item1 , item2 , ...) 
```

#### Key Points 
- Mutates the original array 
- Removes or add elements 
- Returns an array of removed elements 

#### Examples : 
###### Example 1 : Remove Elements 

```js title:removeElement.js 
const arr = [1,2,3,4,5]; 

const removed = arr.splice(1,2); 
//This means -> remove 2 elements from index 1 
```

- The above means -> 
	- `deleteCount = 2`
	- `start = 1 (index)`
- We start removing from index 1 -> element is (2)
- And hence 2 values -> 2, 3
- `removed = [2,3]`
- and this changes in the original array 
- and hence `arr` becomes => 
- `arr = [1,4,5]` -> it removed 2 and 3 

###### Example 2 : Add Elements 
```js title:addElementsUsingSplice.js
const arr = [1, 4, 5];

arr.splice(1,0,2,3);
```

- `start = 1st index` 
- `deleteCount = 0` -> We don't want to delete anything 
- `item1 = 2`
- `item2 = 3`
- So we add the item1 and item2 at the index 1 
- new array => `arr = [1,2,3,4,5]` -> so it added item 1 and item 2 at the first index. 

###### Example 3 : Replace elements 
```js title:replaceElementsUsingSplice.js 
const arr = [10, 20, 30];

//replace 20 with 2000 
//splice -> 
	//we need to remove the 20 which is at : 
	//index -> 1 
	//deleteCount -> 1 
	//item1 -> 200 
const removed = arr.splice(1,1,200);
 
console.log("array" , arr ); 
```


