# N-Repeated Element in Size 2N Array

## Problem Statement

You are given an integer array nums with the following properties:

nums.length == 2 * n.
nums contains n + 1 unique elements.
Exactly one element of nums is repeated n times.
Return the element that is repeated n times.



Example 1:

Input: nums = [1,2,3,3]

Output: 3

Example 2:

Input: nums = [2,1,2,5,3,2]

Output: 2

Example 3:

Input: nums = [5,1,5,2,5,3,5,4]

Output: 5

---

##  Approach

- Use hashmap to track frequency of element.
- Use entrySet to get value and which , key value is equal to nums.length/2 , Just return it.
---

## Time Complexity

    O(n), Simple itreation.
---

## Space Complexity

    O(n), using hashmap.
---

## Java Solution

```java
class Solution {
    public int repeatedNTimes(int[] nums) {
        HashMap<Integer,Integer> map=new HashMap<>();

        for(int i:nums){
            map.put(i,map.getOrDefault(i,0)+1);
        }

        for(Map.Entry<Integer,Integer> i:map.entrySet()){
            if(i.getValue()==(nums.length/2))return i.getKey();
        }
        return -1;
    }
}
