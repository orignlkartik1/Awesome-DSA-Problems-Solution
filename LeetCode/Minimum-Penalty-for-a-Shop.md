# Min-Cost-Climbing Stairs

## Problem Statement
You are given the customer visit log of a shop represented by a 0-indexed string customers consisting only of characters 'N' and 'Y':

if the ith character is 'Y', it means that customers come at the ith hour
whereas 'N' indicates that no customers come at the ith hour.
If the shop closes at the jth hour (0 <= j <= n), the penalty is calculated as follows:

For every hour when the shop is open and no customers come, the penalty increases by 1.
For every hour when the shop is closed and customers come, the penalty increases by 1.
Return the earliest hour at which the shop must be closed to incur a minimum penalty.

**Note** that if a shop closes at the jth hour, it means the shop is closed at the hour j.

---

##  Approach

- count no. of y and n in the given string.
- add edge case for value 0. 
- Simple apply logic.
---

## Time Complexity
    O(n), where n is input.
---

## Space Complexity
    O(1), no auxiliary space.
    
---

## Java Solution

```java
class Solution {
    public int bestClosingTime(String s) {
        int Y=0;
        int N=0;
        int c=s.length();
        for(int i=0;i<c;i++){
            if(s.charAt(i)=='Y')Y++;
            else{N++;}
        }
        if(Y==0)return 0;
        if(N==0)return Y;
        int min=Y;
        int id=0;
        for(int i=0;i<c;i++){
            if(s.charAt(i)=='Y')Y--;
            else{Y++;}

            if(min>Y){
                min=Y;
                id=i+1;
            }
        }
        return id;
    }
}

```
