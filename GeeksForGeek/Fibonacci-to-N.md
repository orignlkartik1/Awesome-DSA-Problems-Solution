# N Fibonacci Numbers (GeeksforGeeks)

## Problem Statement
Given an integer **N**, generate all Fibonacci numbers **less than or equal to N**.

---

##  Approach

- Start with the first two Fibonacci numbers: `0` and `1`
- Iteratively generate the next Fibonacci number by summing the previous two
- Stop when the next number exceeds `N`
- Store all valid Fibonacci numbers in an `ArrayList`

---

## Time Complexity

    O(K), where 0<=K<=N.

## Space Complexity

    O(K), K space required.


---

## Java Solution

```java
class Solution {
    ArrayList<Integer> nFibonacci(int N) {
        ArrayList<Integer> arr = new ArrayList<>();
        
        // For small N values
        if (N >= 0) arr.add(0);
        if (N >= 1) arr.add(1);

        // For bigger values
        int i = 2;
        while (true) {
            int next = arr.get(i - 1) + arr.get(i - 2);
            if (next > N) break;
            arr.add(next);
            i++;
        }
        
        return arr;
    }
}

