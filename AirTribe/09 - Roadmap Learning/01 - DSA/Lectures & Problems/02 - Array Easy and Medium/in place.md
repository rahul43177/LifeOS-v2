## In-Place in LeetCode

**Definition:** Solve using **O(1) extra space** - modify the original array directly, no new arrays/data structures.
- Can't use extra or new array as variable

## ✅ Allowed:

- A few variables: `let i = 0, temp = nums[0]`
- Modify original: `nums[i] = newValue`
- Swap elements: `[nums[i], nums[j]] = [nums[j], nums[i]]`

## ❌ NOT Allowed:

- New arrays: `let result = []`
- Growing data structures: `new Map()`, `new Set()`
- Recursion (uses call stack space)

## Example:

```javascript
// ✅ In-place: Remove duplicates
var removeDuplicates = function(nums) {
    let writeIndex = 1;
    for (let i = 1; i < nums.length; i++) {
        if (nums[i] !== nums[i-1]) {
            nums[writeIndex++] = nums[i]; // Modify original
        }
    }
    return writeIndex;
};

// ❌ NOT in-place: Creates new array
var removeDuplicates = function(nums) {
    return [...new Set(nums)]; // O(n) space
};
```

**Key:** Modify the input directly using only constant extra variables!