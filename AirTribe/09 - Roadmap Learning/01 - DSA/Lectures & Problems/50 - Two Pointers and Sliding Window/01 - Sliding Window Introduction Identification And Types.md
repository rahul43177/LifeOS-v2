## Flow 
1. Origin of sliding window 
2. brute 
3. Identify 
4. Types of sliding window 

## Problem 1 : Find max sum of sub array of size k
1. `array = [2,3,5,2,9,7,1]`
2. One number is given k = 3 -> size of [[Sub Array]]
3. So here we need to tell the sum of all the sub array of the array of size 3 

So the sub arrays of `array = [2,3,5,2,9,7,1]` could be : 
![[../../../../../attachments/00 - Sliding Window Introduction Identification And Types - sub array sum.png]]
And the maximum sub array sum out of these sub arrays 


## Approach 1 : Naive and problem in that
- Running 2 for loos and then finding the sum till 3 size of sub array 
- i will run and then j will run from the next element of the i 

### How to find if our code can be optimized 
<font color="#f79646">Check if we are doing some repetitive work</font>
- So in the brute force approach
- we are finding the sum of 3 continuous elements of the array with `i` and `j` pointers 
- But here in the next time also we are finding the 3 elements , but the last 2 elements we have already found out about the sum , and that is the repetitive work we are doing. 
### Origin of sliding window 
- ![[../../../../../attachments/00 - Sliding Window Introduction Identification And Types - brute force what is wrong.png]]
- Here if we check the green part we are found the sum of elements : 0 , 1 and 2 
- Then we are moving the pointer and we are finding the sum of elements : 1 , 2 and 3 
- But if we observe we have already found out the sum of 1 and 2 , and that is our repetitive work. 
- This could be optimized. 
- ![[../../../../../attachments/00 - Sliding Window Introduction Identification And Types - naive method.png]]
- So we can use the previous 2 + 3 -> and use it and just add 4 at last.
- So basically what could have we done is : 
- 0 + 1 + 2 -> in the next window -> just remove 0 from the last and then add 3 -> 1 + 2 + 3 -> Now please remove the 1 and then add 4 -> 2 + 3 +4 -> this is how the window looks like and we use the previous value as well. 
- So that is how sliding window is optimized and we can use that as well. 


## Sliding Window - Identification 
- It will always be on the array and strings 
- And window will always be continuous 
- And to find out they will always ask to find out -> 
	- **Sub array**
	- **Sub String** 
	And with this -> longest array and with `k` window size
- Sometimes they ask to find the size of the k -> window size

## Types of Sliding window : 
There could be of two types of questions in the sliding window 
1. Fix size window  -> where they give the window size and ask for some calculation 
2. Variable size window -> here they give some calculations and then they ask for the window size

>  ***fixed type window questions < variable size window questions***

### Fix sized window 
Here we increase and decrease the element at the same element and then we keep on finding the sum and hence here the window size is same. 

> In fixed sized window, they give the max window size as k -> 3 and then they were asking for the sum -> that was <span style="background:#b1ffff">fixed window size</span> 

### Variable sized window 
- Here in the question they don't give windows , instead they ask the window size (`k`)
- Sometimes they ask for the largest window or smallest window subjected to some condition 

So this will be reversed of fixed size window , where instead of finding the sum , they will give the sum to us and then we need to find the largest window which is giving that sum. So that will be our window. 

##### Example : 
- `arr = [3,2,4,5,1,1,1,1,1,3,3]`
- largest sub array find karo -> basically they are asking for the window size k ? 
- and the sum is **5** 

> So here sum given hai 
window size batana hai , so this is the example of <font color="#00b050">variable size window</font> 
--- 



