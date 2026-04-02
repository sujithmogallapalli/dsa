## Problem
You are given an array prices where prices[i] is the price of a given stock on the ith day.
You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.

## Sample
Input: prices = [7,1,5,3,6,4]
Output: 5
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.

## Observations
- Prices array length is greater than 0
- If no profit after initial buy, return 0

## Approaches
### Approach 1 - One-pass greedy approach
- Initialize the start with 0th index element
- Initialize the profit as 0
- Traverse through the prices from 1 to n-1
  - if prices[i] is less than start, then replace start with ith element.
  - if prices[i] is greater than start, check and assign max profit to profit
- Time Complexity - O(n), Space Complexity - O(1)

### Approach 2 - Brute Force
- Initialize maxProfit = 0
- Use two loops
  - ith loop -> to buy the stock
  - jth loop -> (j = i to n - 1) -> find max profit by taking diff
- Time Complexity = O(n^2), Space Complexity - O(1)

## Codes
### One-pass greedy approach
```java
public int maxProfit(int[] prices) {
    int start = prices[0], profit = 0;
    for (int i = 1; i < prices.length; i++) {
        if (prices[i] > start) {
            profit = Math.max(prices[i] - start, profit);
        }
        else if (prices[i] < start) {
            start = prices[i];
        }
    }
    return profit;
}
```
### Brute force
```java
public int maxProfit(int[] prices) {
    int profit = 0;
    for (int i = 0; i < prices.length; i++) {
        for (int j = i + 1; j < prices.length; j++) {
           profit = Math.max(profit, prices[j] - prices[i]);
        }
    }
    return profit;
}
```

## New learnings
- One pass Greedy Approach