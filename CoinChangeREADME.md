# leet-day28



# Coin Change Problem

## Problem Description

You are given an integer array `coins` representing coins of different denominations and an integer `amount` representing a total amount of money.

Return the fewest number of coins that you need to make up that amount. If that amount of money cannot be made up by any combination of the coins, return -1.

You may assume that you have an infinite number of each kind of coin.

## Examples

### Example 1:

Input: `coins = [1,2,5], amount = 11`
Output: `3`
Explanation: 11 = 5 + 5 + 1

### Example 2:

Input: `coins = [2], amount = 3`
Output: `-1`

### Example 3:

Input: `coins = [1], amount = 0`
Output: `0`

## Constraints

- 1 <= `coins.length` <= 12
- 1 <= `coins[i]` <= 2^31 - 1
- 0 <= `amount` <= 10^4

## Approach and Explanation

The problem can be solved using dynamic programming. We create a `dp` array where each index `i` represents the minimum number of coins needed to make up the amount `i`. We initialize the `dp` array with a value larger than the possible amount.

For each coin denomination, we iterate through the `dp` array starting from the value of the coin. At each step, we update the minimum number of coins needed for the current amount by considering whether using the current coin would result in a smaller number of coins compared to the previously computed value. We do this for all coin denominations.

Finally, the value at `dp[amount]` will represent the minimum number of coins needed to make up the given amount. If this value is still larger than the original amount, it means that the amount cannot be made up with the given coins, and we return -1. Otherwise, we return the value in `dp[amount]`.

## Complexity Analysis

- Time Complexity: O(amount * coins.length)
- Space Complexity: O(amount)
