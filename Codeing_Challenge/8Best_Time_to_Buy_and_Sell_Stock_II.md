

# Approach
 - Traverse through the array of prices.
 - Whenever the price on the next day is higher than the price on the current day, you can "buy today and sell tomorrow" to make a profit.
 - The sum of all these small profits from each increasing interval will give the maximum profit.

# Algorithm
1. Initialize `maxProfit = 0`.
2. Loop through the `prices` array from the second day (index `1`).
3. For each day, if the price on day `i` is greater than the price on day `i-1`, add the difference to `maxProfit` (this means you buy on day `i-1` and sell on day `i`).
4. Continue until the end of the array.
5. Return `maxProfit`.

# Code
```javascript []
/**
 * @param {number[]} prices
 * @return {number}
 */
const maxProfit = (prices) => {
    let maxProfit = 0;

    // Iterate through prices starting from the second day
    for (let i = 1; i < prices.length; i++) {
        // If today's price is greater than yesterday's, buy yesterday and sell today
        if (prices[i] > prices[i - 1]) {
            maxProfit += prices[i] - prices[i - 1];
        }
    }

    return maxProfit;
};

```

## Example 1: prices = [7,1,5,3,6,4]

 - Buy on day 2 (price = 1) and sell on day 3 (price = 5), profit = 5 - 1 = 4.
 - Buy on day 4 (price = 3) and sell on day 5 (price = 6), profit = 6 - 3 = 3.
 - Total profit = 4 + 3 = 7.

## Time Complexity:
 - The algorithm runs in O(n) time where n is the length of the prices array. We only traverse the array once, making it very efficient.
## Space Complexity:
 - The space complexity is O(1) because we only use a few variables to store the profit.
