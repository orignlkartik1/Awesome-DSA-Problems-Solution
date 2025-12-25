# Climbing Stairs

## Problem Statement
You are climbing a staircase. It takes n steps to reach the top.
Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?
---

##  Approach

- Just try to simulate the problem on copy. 
- find pattern, between test cases.
- You got this !! it is fibonacci sequence.
---

## Time Complexity

    O(n), where n is given.
---

## Space Complexity

    O(1), no auxiliary space required.
---
## Note
    Just dry run.
---

## Java Solution

```java
class Solution {
    public int climbStairs(int n) {
        if(n<=3)return n;

        int a=2;
        int way=3;
        for(int i=4;i<=n;i++){
            int temp=a;
            a=way;
            way=a+temp;
        }
        return way;
    }
}