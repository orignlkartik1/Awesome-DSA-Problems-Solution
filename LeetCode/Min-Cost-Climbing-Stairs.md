# Min-Cost-Climbing Stairs

## Problem Statement

Given an array of integers cost[] where cost[i] is the cost of the ith step on a staircase. Once the cost is paid, you can either climb one or two steps. Return the minimum cost to reach the top of the floor.
Assume 0-based Indexing. You can either start from the step with index 0, or the step with index 1.
---

##  Approach

- find no of ways using recursive tree.
- try to simulate and conversion it from recursion to space optimization.
- recursion-> memoization-> tabulation-> space optimization
---

## Time Complexity
    ### recursion
    O(2^n), we check all paths and try to find optimal path.

    ### memoization
    O(n^2), we checking all the paths, but don't use auxiliary space.

    ### tabulation
    O(n), don't try to simulate.

    ### space optimization
    O(1), auxiliary
---

## Space Complexity

    same as front of us and extra spaces only for space optimization.
---
## Note
    Just dry run.
---

## Java Solution

### recursion
```java

//Back-end complete function Template for Java

class Solution {
    static int minCostClimbingStairs(int[] cost) {
        return Math.min(solve(cost,0),solve(cost,1));
    }
    
    static int solve(int[] arr,int i){
        int n=arr.length;
        if(i>=n)return 0;
        
        int one=arr[i]+solve(arr,i+1);
        int two=arr[i]+solve(arr,i+2);
        
        return Math.min(one,two);
    }
}
```
### memoization
```java
//Back-end complete function Template for Java

class Solution {
    
    static int minCostClimbingStairs(int[] cost) {
        int n=cost.length;
        Integer[] dp=new Integer[n];
        return Math.min(solve(cost,0,n,dp),solve(cost,1,n,dp));
    }
    
    static int solve(int[] arr,int i,int n,Integer[] dp){
        
        if(i>=n)return 0;
        
        if(dp[i]!=null)return dp[i];
        
        int one=arr[i]+solve(arr,i+1,n,dp);
        int two=arr[i]+solve(arr,i+2,n,dp);
        
        return dp[i]=Math.min(one,two);
    }
}
```
### tabulation
```java
class Solution {
    static int minCostClimbingStairs(int[] cost) {
        int n = cost.length;

        int[] dp = new int[n + 1];

        
        dp[0] = 0;
        dp[1] = 0;

        for (int i = 2; i <= n; i++) {
            dp[i] = Math.min(
                dp[i - 1] + cost[i - 1],
                dp[i - 2] + cost[i - 2]
            );
        }

        return dp[n];
    }
}


```