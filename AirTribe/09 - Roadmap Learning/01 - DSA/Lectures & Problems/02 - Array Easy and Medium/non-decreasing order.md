In LeetCode, **"non-decreasing order"** means the array is sorted such that each element is **greater than or equal to** the previous element.
Here it can have duplicates as well. 
## Key Points:

- **Non-decreasing** = `arr[i] <= arr[i+1]` for all valid i
- Elements can be **equal** or **increasing**
- **No element decreases** as you move from left to right

## Examples:

✅ **Non-decreasing arrays:**

```javascript
[1, 2, 3, 4, 5]        // Strictly increasing (also non-decreasing)
[1, 2, 2, 3, 3, 4]     // Has duplicates but still non-decreasing
[1, 1, 1, 1]           // All equal (non-decreasing)
[5]                    // Single element (non-decreasing)
[1, 3, 3, 3, 7, 8]     // Mixed equal and increasing
```

❌ **NOT non-decreasing:**

```javascript
[1, 2, 1, 3]           // 2 > 1, so it decreases
[5, 4, 3, 2, 1]        // Decreasing order
[1, 3, 2, 4]           // 3 > 2, so it decreases
```

## Common LeetCode Terminology:

| Term                    | Meaning          | Example     |
| ----------------------- | ---------------- | ----------- |
| **Non-decreasing**      | `a[i] <= a[i+1]` | `[1,2,2,3]` |
| **Non-increasing**      | `a[i] >= a[i+1]` | `[3,2,2,1]` |
| **Strictly increasing** | `a[i] < a[i+1]`  | `[1,2,3,4]` |
| **Strictly decreasing** | `a[i] > a[i+1]`  | `[4,3,2,1]` |

## Why "Non-decreasing" vs "Increasing"?

LeetCode uses "non-decreasing" to be mathematically precise:

- **"Increasing"** might imply strictly increasing (no duplicates)
- **"Non-decreasing"** clearly allows duplicates while maintaining order

So when you see "non-decreasing" in a problem, think: **"sorted in ascending order, duplicates allowed"**!

