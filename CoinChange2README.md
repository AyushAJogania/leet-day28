# leet-day28

# Coin Change 2

## Problem Description

You are given an integer array `coins` representing coins of different denominations and an integer `amount` representing a total amount of money.

Return the number of combinations that make up that amount. If that amount of money cannot be made up by any combination of the coins, return 0.

You may assume that you have an infinite number of each kind of coin.

The answer is guaranteed to fit into a signed 32-bit integer.

## Example

### Example 1:

Input: `amount = 5`, `coins = [1,2,5]`

Output: `4`

Explanation: There are four ways to make up the amount:
- 5=5
- 5=2+2+1
- 5=2+1+1+1
- 5=1+1+1+1+1

### Example 2:

Input: `amount = 3`, `coins = [2]`

Output: `0`

Explanation: The amount of 3 cannot be made up just with coins of 2.

## Constraints:

- `1 <= coins.length <= 300`
- `1 <= coins[i] <= 5000`
- `All the values of coins are unique.`
- `0 <= amount <= 5000`

## Approach

We can use dynamic programming to solve this problem. We create an array `dp` of size `amount + 1`, where `dp[i]` represents the number of combinations to make up the amount `i`. We initialize `dp[0]` to 1, because there's exactly one way to make up the amount 0, which is by using no coins.

Then, for each coin in the `coins` array, we iterate through the `dp` array from `coin` to `amount`. For each value `i`, we add `dp[i - coin]` to `dp[i]`, which means we are considering the combinations that can be formed by adding the current coin to the combinations that make up the amount `i - coin`.

Finally, we return `dp[amount]`, which contains the total number of combinations to make up the given `amount`.

## Complexity Analysis

- Time complexity: O(amount * coins.length), where `amount` is the target amount and `coins.length` is the length of the coins array.
- Space complexity: O(amount), as we use an array `dp` of size `amount + 1` to store the number of combinations for each amount.
