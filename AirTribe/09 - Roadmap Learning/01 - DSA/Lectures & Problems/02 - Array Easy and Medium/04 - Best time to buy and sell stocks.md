### Description in my words : 
- Array is given `prices` and then 
- `prices[i]` , at what day we should buy and sell to get the max profit 
- so if we have array called `nums = [1,5,3,6,3]`
- so if we buy at one (lowest price) and then if we sell it on 6(highest price) and then we made the maximum profit -> 6-1 => that is -> 5 rs 

### Logic
- we maintain a `minPrice` which starts from first element 
- we should also maintain one `maxProfit` variable which keep track of `currentElement - minPrice` , if that is greater than `maxProfit` .
- Then it is fine we got it otherwise we just move on. 
- After complete iteration we can get the `maxProfit`

### Code
```javascript title:bestTimeToBuyAndSell fold
function bestTimeToBuyAndSellStock(prices) {
	let minPrice = prices[0];
    let maxProfit = 0;
    for(let i = 0;i<prices.length;i+=1) {
        if(prices[i] - minPrice > maxProfit) {
            maxProfit = prices[i] - minPrice;
        }  
  
        if(prices[i] < minPrice) {
           minPrice = prices[i];
        }
    }
    return maxProfit;
}``