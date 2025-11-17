## Problem Statement
Input : 
`arr = [2,5,1,8,2,9,1]`
`k = 3` (window size)

So from this `arr` we need to find the [[Sub Array]] of size 3 , whose sum is maximum. 
Here hamse sub array puchha hai and the window size is given to us.

![[../../../../../attachments/sliding-window-hand-written.jpg|500]]
## Identification of the sliding window 
1. Question hoga either array ka ya fir string hoga 
2. Sub array ya sub string puchi hogi 
3.  ya toh window size `k` di hogi and kuch calculation puchi hogi jaise sum and all 
4. Ya fir calculation di hogi and window size `k` pucha hoga
So think ki in sab question me sliding window lagega hi lagega 

## Approach and explanation
Window logic we know , please check the above screenshot as well 
So to represent a window -> we need two things 
1. Start -> we will keep the pointers -> `i` 
2. End  -> second pointer -> `j`

### What will be the window size if I have two pointers `i` and `j`
![[../../../../../attachments/03 - Maximum Sum Subarray of size K - window size.png]]
Two pointers are 2 and 5
`i` = 2 
`j` = 5 
`window size = j - i + 1 = 4`
$$
window size = j - i + 1
$$

```plain text
window size = second pointer - first pointer + 1
``` 

So now we are given with window size in the question as `k` 

### How to reach to our required window size 
- So in the question we are given with the window size (k) = 3 
- So basically we will start i and j from the 0 of the array 
![[../../../../../attachments/03 - Maximum Sum Subarray of size K - window size adjustment.png|600]]
- So starting me toh i and j dono will be at 0 
- So we need to come to the required window size for the calculation to be correct and useful
- So first we will check a simple condition -> 
	- `j-i+1 < k` => which means if the current window size is smaller than the given window size ? 
	- So we need to increase the window size. We can expand window by `j++`	
- So this is how we will reach to the required window length of 3 
	![[../../../../../attachments/03 - Maximum Sum Subarray of size K - window size correct.png]]
Now we have to maintain the window size as 3 , as we need this much only and k = 3 , so we need to maintain this window size. 

### How to maintain window size 
So we can check the condition 
`j-i+1 == k` so this is correct , now we do the calculation (sum in this question)
Now calculations are done, we need to maintain the window the size now. 

So basically we can do that by removing the first element and one new in the last one 
so basically -> 
`i++` and then `j++`
![[../../../../../attachments/03 - Maximum Sum Subarray of size K - maintain the window size.png]]
so this is how we can maintain the window as
1. `i` -> start of the window 
2. `j` -> end of the window

## Code 
- declare two variable ->`i` and `j` 
	- `i` -> start of the window 
	- `j` -> end of the window 
- so at last j will be at last and then i will be second last , so what should be our while loop condition ? 
- ![[../../../../../attachments/03 - Maximum Sum Subarray of size K - while loop condition.png]]
- that should be -> `while(j<size)` because j will be the end of the window 
- and to find the sum below the while loop ,  is to find the required window size 
- That we can achieve by checking -> current window size != window size given in the question 
- `j-i+1 < k` then `j++`
- and then once we found the exact window size , then we need to maintain the window 
- `else if(j-i+1) == k` -> we find the sum -> and then store the max of the current sum or the previous sum 
- `sum = Math.max(sum , currentSum)`
- and to maintain the window size we can do simple trick -> `i++` and then `j++`
- then -> `sum = sum - arr[i] + arr[j]` -> with new i and j 
- so we are basically removing one i element and then adding new element and then window is maintaining. 
- and we are done. 
- Return sum 