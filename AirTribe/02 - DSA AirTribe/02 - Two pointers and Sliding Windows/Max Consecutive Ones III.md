[Question link](https://leetcode.com/problems/max-consecutive-ones-iii/)

## Description 
Given a binary array nums and an integer k, return the maximum number of consecutive 1's in the array if you can flip at most k 0's.


Example 1:
```js 
Input: nums = [1,1,1,0,0,0,1,1,1,1,0], k = 2
Output: 6
Explanation: [1,1,1,0,0,1,1,1,1,1,1]
```
Bolded numbers were flipped from 0 to 1. The longest subarray is underlined.

Example 2:

```js
Input: nums = [0,0,1,1,0,0,1,1,1,0,1,1,0,0,0,1,1,1,1], k = 3
Output: 10
Explanation: [0,0,1,1,1,1,1,1,1,1,1,1,0,0,0,1,1,1,1]
```
Bolded numbers were flipped from 0 to 1. The longest subarray is underlined.

## Explanation 
### Brute Force 
Sub-array => Contiguous part of array 
Sub array 1 , 0 is my potential. 

We formed all sub arrays and counter number of zeroes and the ones with k zeroes 
![[../../../attachments/Max Consecutive Ones III - zeroes.png]]
![[../../../attachments/Max Consecutive Ones III - tc.png]]
### Sliding Window Approach
```js 
let array = [0 , 1 , 1 , 0 , 0 , 1 , 1 , 0 , 1 , 1] 
let k = 2;
```

![[../../../attachments/00 - Two Pointers and Sliding Windows class - sliding window-1.png]]

![[../../../attachments/Max Consecutive Ones III - sliding windows.png]]![[../../../attachments/Max Consecutive Ones III - dry running.png]]
### Code and design pattern
```js fold title:maxConsequtiveOnesIII.js
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number}
 */
var longestOnes = function(nums, k) {
    // 1,1,1,0,0,1,1,1,1,1,1 k = 2

    let s = 0; 
    let e = 0; 

    let maxLen = 0; 
    let count0 = 0; 

    while (e < nums.length) {
        // Condition update
        if (nums[e] == 0) {
            count0++; 
        }   


        // Validation of window (shirinking)
        while (count0 > k && s <= e) {
                if (nums[s] == 0) {
                    count0--; 
                }
                s++; 
        }

        // taking curlen of window for answer. 
        const curLen = e - s + 1; 
        maxLen = Math.max(curLen, maxLen);
        // expanding
        e++;  
    }

    return maxLen; 
};
```
