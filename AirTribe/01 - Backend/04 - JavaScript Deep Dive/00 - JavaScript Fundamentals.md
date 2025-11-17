## Topics to cover : 
![[../../../attachments/00 - JavaScript Fundamentals - topics to cover.png]]

## How JS different from other languages ? 
![[../../../attachments/00 - JavaScript Fundamentals - how js is different.png]]

#### Typing 
In JavaScript we have *Dynamic typing* -> which means 
```js 
let x = 12 ; 
x = "Rahul"; 

//so here we have changed the type of the variable
```
Here if the `x` was declared with the integer but later we can change the value and the data type as well. 
##### Dynamic vs Static Typing 
![[../../../attachments/00 - JavaScript Fundamentals - dynamic vs status typing.png]]

##### Strongly vs Weakly typed 
Strongly -> It is checked at the compile time 
Weakly -> It is checked at the run time

So in Java , the typing is checked the compile time but in the case of JavaScript it does not happen , it is checked at the run time. 

> [!info]- Read About
> - Dynamic vs Status Typing 
> - Strongly vs Weakly Typed 


#### Execution 
JavaScript is Interpreted language , where the interpreter reads the code line by line and then convert it into the machine readable language. 
##### Interpreted vs Compiled
###### Compiled Language
- Machine understandable code , that compiled file will execute in actual 

###### Interpreted Language
- Interpreter starts to read code line by line and then while reading it will also convert into the machine readable language 
- but it happens line by line 
- and that is why Interpreter language is slow as it happens line by line. 

#### Concurrency 
JavaScript -> ***Single-threaded , async*** 
![[../../../attachments/00 - JavaScript Fundamentals - js single threaded.png]]
Single threaded - JS can only execute one command at a time and in a specific order 
- Single threaded : One command at a time 
- Synchronous : In a specific order 
##### Single-Threaded vs Multi-Threaded
> [!read]- To Read 
> - What is thread
> - What is the meaning of execution ?
> - How does it happen ? 
> - Difference between single threaded vs Multi threaded? 
###### Single-Threaded
- There is only one main execution thread. 
- And whatever happens in the JavaScript , will happen on this main single thread

######  Multi-Threaded
- We can spawn multi threads and we can parallelize the tasks.

## Execution Context
**Everything in JavaScript happens inside an Execution Context**
- We can imagine Execution context as a big box or a container. 
- Whatever happens in the JavaScript , happens in the execution context 
- It has mainly two major parts 
	1. Memory Component 
	2. Code Component 
![[../../../attachments/00 - JavaScript Fundamentals - execution  context.png]]


### How does Execution context look like ?
Memory is also called as Variable Environment 
It has two components : 
1. Memory (Variable Environment) 
2. Code (Thread of execution)
![[../../../attachments/00 - JavaScript Fundamentals - execution context box.png]]
#### Memory 
- If declare some object with key value pair and such a:10 , everything is being stored in the memory 
- The function is also being stored in the memory 
- Memory contains the objects and functions as **Key value pair** 
- It is also known as Variable Environment. 
#### Code
- It is the place where whole JavaScript is executed
- The execution of the code happens in this component. 
- It is also known as - Thread of Execution. 

### How JavaScript Code is executed ? 
[Akshay Saini Video Lecture](https://www.youtube.com/watch?v=iLWTnMzWtj4&t=500s)

So let's say I have a code in JS 

The complete diagram and the explanation : [[Execution Context Diagram|Execution Context Diagram]]
Call Stack -> [[Call Stack in JS]]


### String method -
1. [[Slice Method]] 
2. [[Splice Method]]