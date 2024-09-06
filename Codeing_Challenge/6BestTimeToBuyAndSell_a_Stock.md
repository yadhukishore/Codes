
```javascript
/**
 * @param {number[]} prices
 * @return {number}
 */
const maxProfit = (prices) => {
    let maxProfit = 0;
    
    // Start with the first price as the minimum price to buy
    let minPrice = prices[0];
    
    for (let i = 1; i < prices.length; i++) {
        // Update the minPrice if current price is lower than the minPrice
        if (prices[i] < minPrice) {
            minPrice = prices[i];
        }
        
        // Calculate current profit by selling at the current price
        const currentProfit = prices[i] - minPrice;
        
        // Update maxProfit if currentProfit is greater
        if (currentProfit > maxProfit) {
            maxProfit = currentProfit;
        }
    }
    
    return maxProfit;
};
```

### Explanation:
1. We maintain `minPrice` as the lowest price encountered so far.
2. For each price, we calculate the profit as `current price - minPrice`.
3. We update `maxProfit` if this profit is greater than the current `maxProfit`.

### Time Complexity:
- The solution now runs in O(n), where `n` is the length of the `prices` array, which is much more efficient than your nested loop solution that had O(n^2) time complexity.

### Example Walkthrough:

For `prices = [7,1,5,3,6,4]`:
- Initially, `minPrice = 7` and `maxProfit = 0`.
- On day 1, `minPrice` becomes `1` (since `1` is less than `7`).
- On day 2, the profit is `5 - 1 = 4`, so `maxProfit = 4`.
- On day 4, the profit is `6 - 1 = 5`, so `maxProfit` is updated to `5`.
- This gives the correct result of `5`.

For `prices = [7,6,4,3,1]`:
- Since the prices are always decreasing, no profitable transaction can be made, so the result is `0`.
