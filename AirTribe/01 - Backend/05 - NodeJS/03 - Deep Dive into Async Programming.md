### Stack 
The classical idea of stack is : 
> Whatever goes in first - It comes out at last  -> imagine stack of plates


The plate which is going first , will be at the bottom and so many other plates will be on top and hence the plate which went first will come last. 
This is called : `LIFO` -> Last in first out

Mostly all the programming language uses : Stack and Heap
- For different programming languages we have different stack and heap (memory)
- When that is exhausted we get the error called : Heap out of memory or Stack over flow 


---
#### Short notes on Call Stack
![[../../../attachments/03 - Deep Dive into Async Programming - call stack.png]]

## Asynchronous and synchronous programming 
[JavaScript visualizer](https://jsviz.klve.nl/) 
![[../../../attachments/Pasted image 20251104215902.png]]
#### Example 1 : Synchronous Execution 
This example means -> the `nodejs` executes code line by line
```js 
console.log("start");

console.log("In between);

console.log("End);
```
Output : 
```plain text
start
in between 
end
```

#### Example 2 : Asynchronous Execution 
```js
console.log("start");

setTimeout(() => {
  console.log("in between")
},0)

console.log("End");
```

so here the timeout is 0 seconds , but `setTimeout` is executed in a different manner or  asynchronous manner 


output 
```plain text
start
end
in between 
```


#### Example 3 : Asynchronous Execution 
![[../../../attachments/03 - Deep Dive into Async Programming - 3.png]]
```js
console.log("start");

setTimeout(() => {
  console.log("in between")
},1000)

console.log("End");
```

so here the timeout is 0 seconds , but `setTimeout` is executed in a different manner or  asynchronous manner 


output 
```plain text
start
end
in between 
```


#### Example 4 : Asynchronous Execution 
![[../../../attachments/03 - Deep Dive into Async Programming - 4.png]]
```js
//update the code 
console.log("start"); 

setTimeout(() => {
  console.log("in between")
},1000)

console.log("End");
```

There is something called [[Event Loop]] which keep tracks of weather call stack is empty or not 
In nodejs we have single call stack which is the meaning -> Nodejs is single threaded

So basically , main execution is done in the call stack 
but the async timeout is sent to other stack -> which counts -> if timer is 1000 -> it will do the counting part and all , and once the timeout is completed -> it sends it to the main call stack and then are called as IO threads 


output 
```plain text
start
end
in between 
```




#### Example 5 : Callback functions
```js 
const asyncFunction = () => {
    setTimeout(() => {
        console.log("In between")
    },1000)
}


const main = async () => {
    console.log("Start");
    await asyncFunction();
    console.log("End")
}

main();
```

so ideally the print statement should be 
```plain text
Start 
In between
End
```

the in reality : 
```plain text
Start 
End
In between
```

This is how it is printing 
So all these async await are all synctactical sugar and the fundamentals are : [[Callback functions]]








## Main links in this notes 
1. [[Event Loop]]
2. [[Callback functions]]