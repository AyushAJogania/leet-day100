# leet-day100

# Min Cost Climbing Stairs

You are given an integer array `cost` where `cost[i]` represents the cost of the `i`-th step on a staircase. Once you pay the cost, you can either climb one or two steps. The goal is to find the minimum cost to reach the top of the floor.

## Problem Description

Given an array `cost` with the cost of each step, you can start from either step 0 or step 1. For each step, you have two choices:

1. You can climb one step, which incurs the cost `cost[i]`.
2. You can climb two steps, which incurs the cost `cost[i]`.

You want to reach the top floor with the minimum possible cost. This problem essentially asks for the minimum cost to reach the `n`-th step, where `n` is the number of steps in the `cost` array.

## Example

### Example 1

Input: `cost = [10, 15, 20]`

Output: `15`

Explanation: You will start at index 1.

- Pay 15 and climb two steps to reach the top.
- The total cost is 15.

### Example 2

Input: `cost = [1, 100, 1, 1, 1, 100, 1, 1, 100, 1]`

Output: `6`

Explanation: You will start at index 0.

- Pay 1 and climb two steps to reach index 2.
- Pay 1 and climb two steps to reach index 4.
- Pay 1 and climb two steps to reach index 6.
- Pay 1 and climb one step to reach index 7.
- Pay 1 and climb two steps to reach index 9.
- Pay 1 and climb one step to reach the top.
- The total cost is 6.

## Constraints

- 2 <= cost.length <= 1000
- 0 <= cost[i] <= 999

## Approach

We can use dynamic programming to solve this problem. The idea is to build an array `dp`, where `dp[i]` represents the minimum cost to reach the `i`-th step. We iterate through the `cost` array and calculate the minimum cost for each step by considering two options:

1. Coming from the previous step (`dp[i - 1] + cost[i]`).
2. Skipping a step and coming from two steps before (`dp[i - 2] + cost[i - 2]`).

The answer is in `dp[n]`, where `n` is the length of the `cost` array.

## Implementation

You can implement the solution in C++ as follows:

```cpp
class Solution {
public:
    int minCostClimbingStairs(vector<int>& cost) {
        int n = cost.size();
        vector<int> dp(n + 1, 0);
        
        for (int i = 2; i <= n; i++) {
            dp[i] = min(dp[i - 1] + cost[i - 1], dp[i - 2] + cost[i - 2]);
        }
        
        return dp[n];
    }
};
```

This code defines the `minCostClimbingStairs` function that takes the `cost` array as input and returns the minimum cost to reach the top.

## Complexity Analysis

The time complexity of this solution is O(n), where n is the length of the `cost` array, and the space complexity is O(n) to store the `dp` array. The algorithm iterates through the `cost` array once to compute the minimum cost.
