# House Robber - 1

## Problem Statement
You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security systems connected and it will automatically contact the police if two adjacent houses were broken into on the same night.

Given an integer array nums representing the amount of money of each house, return the maximum amount of money you can rob tonight without alerting the police.



Example 1:

Input: nums = [1,2,3,1]

Output: 4

Explanation: Rob house 1 (money = 1) and then rob house 3 (money = 3).
Total amount you can rob = 1 + 3 = 4.

Example 2:

Input: nums = [2,7,9,3,1]

Output: 12

Explanation: Rob house 1 (money = 2), rob house 3 (money = 9) and rob house 5 (money = 1).
Total amount you can rob = 2 + 9 + 1 = 12.

---

##  Approach

- We will explore array in two ways. first in  theft and second is not.
- for theft, we add arr[i] on calls.
- for not, we're just increasing the indexes.
- RECURSION -> MEMOIZATION -> TABULATION -> (TRY) SPACE OPTIMIZATIONS.
---

## Time Complexity

    ### recursion
    O(2^n), exploring two paths.

    ### memoization
    O(n), not taking extra paths.

    ### tabulation
    O(n)
---

## Space Complexity

    ### recursion
    O(2^n), due to recursive stack

    ### memoization
    O(n), due to recursive stack.

    ### tabulation
    O(n), for an array.
---
## Note
    Just dry run.
---

## Java Solution
### recursion
```java
class Solution {
    public int rob(int[] nums) {
        int n=nums.length;
        Integer[] dp=new Integer[n];
        return solve(nums,n-1,dp);
    }

    private int solve(int[] arr,int i,Integer[] dp){
        if(i<0)return 0;

        if(dp[i]!=null)return dp[i];

        int theft=arr[i]+solve(arr,i-2,dp);
        int not=solve(arr,i-1,dp);

        return dp[i]=Math.max(theft,not);
    }
}
```


### memoization
```java
class Solution {
    public int rob(int[] nums) {
        int n=nums.length;
        Integer[] dp=new Integer[n];
        return solve(nums,n-1,dp);
    }

    private int solve(int[] arr,int i,Integer[] dp){
        if(i<0)return 0;

        if(dp[i]!=null)return dp[i];

        int theft=arr[i]+solve(arr,i-2,dp);
        int not=solve(arr,i-1,dp);

        return dp[i]=Math.max(theft,not);
    }
}
```
### tabulation
```java
class Solution {
    public int rob(int[] n) {
        int l=n.length;

        int[] dp=new int[l];

        if(l==1)return n[0];
        if(l==0) return 0;

        dp[0]=n[0];
        dp[1]=Math.max(n[0],n[1]);

        for(int i=2;i<l;i++){
            dp[i]=Math.max(dp[i-1],n[i]+dp[i-2]);
        }
        return dp[l-1];
    }
}
```
