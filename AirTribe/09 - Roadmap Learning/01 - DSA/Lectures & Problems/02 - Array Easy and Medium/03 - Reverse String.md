

https://leetcode.com/problems/reverse-string/description/

### Logic 
##### Full Iteration
- As this is in-place , we can just swap , in one iteration 
- Using 2 pointers -> Start from `left = 0` and `right = length - 1` 
- And then just keep on swapping values of `left` and `right` , just we reach the middle point and done. 
```javaScript wrap fold title:fullIterationReverseString.js
function reverseString(s) {
	let left = 0;
	let right = s.length - 1;
	
	while(left < right) {
		let temp = s[left];
		s[left] = s[right];
		s[right] = temp;
		
		left++;
		right--;
	} 
}
```

##### Half Iteration
- Rather than doing the full iteration , we can complete it in the half iteration as well 
- **💡 Pattern:** Loop first half, swap with `n-1-i` position
- ## 🧠 **Quick Memory Tricks**

- **"Handshake Method":** Two people walk toward each other, swap places
- **Mirror Formula:** Position `i` mirrors to `n-1-i`
- **Three-Step Swap:** `temp = a; a = b; b = temp;`
```javascript wrap fold title : halfIterationReverseString.js
function reverseString(s) {
    let n = s.length;
    
    for(let i = 0; i < Math.floor(n / 2); i++) {
        let oppositeIndex = n - 1 - i;  // 📝 Mirror formula
        
        let temp = s[i];
        s[i] = s[oppositeIndex];
        s[oppositeIndex] = temp;
    }
}
```

## ⚠️ **Common Pitfalls**
```javascript 
// ❌ WRONG: Infinite loop
while(left <= right) 

// ❌ WRONG: Double swapping  
for(let i = 0; i < n/2; i++)

// ✅ CORRECT
while(left < right)
for(let i = 0; i < Math.floor(n/2); i++)
```

## 🧪 **Quick Self-Test**

1. Why `left < right` not `<=`? _(Avoids swapping middle with itself)_
2. What's `n-1-i` for? _(Finds opposite position)_
3. Time/Space? _(O(n), O(1))_

---

## 🎯 **When Stuck Remember:**

- **Two pointers OR half-iteration**
- **Swap elements, move closer to center**
- **Stop when pointers meet**

