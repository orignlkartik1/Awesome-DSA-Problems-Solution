# Weird Algorithm

## Problem Statement
Consider an algorithm that takes as input a positive integer n. If n is even, the algorithm divides it by two, and if n is odd, the algorithm multiplies it by three and adds one. The algorithm repeats this, until n is one. For example, the sequence for n=3 is as follows:
$$ 3 \rightarrow 10 \rightarrow 5 \rightarrow 16 \rightarrow 8 \rightarrow 4 \rightarrow 2 \rightarrow 1$$
Your task is to simulate the execution of the algorithm for a given value of n.

---

##  Approach

- Using recursion, just created a function weird with passing an Integer value n.
- Then add edge case (n==1), just return 1.
- now, another if block for checking it is even and if it is then call with value (value/2) , until value is not equal to 1.
- for odd, simple call function with value (3*value+1).
---

## Time Complexity

    Undetermined due to 'Collatz Nature' of this problem.
---

## Space Complexity

    Auxiliary space of recursive stack.
---
## Note
    Take value in Long , it is a competitive programming question.

---

## Java Solution

```java
import java.util.Scanner;
public class Solution {
 
    static Long weird(Long n){
        System.out.print(n+" ");
        if(n==1)return 1l;
        if(n%2==0) return weird(n/2);
        return weird(3*n+1);
    }
 
    public static void main(String[]args){
        Scanner sc=new Scanner(System.in);
        weird(sc.nextLong());
    }
}
