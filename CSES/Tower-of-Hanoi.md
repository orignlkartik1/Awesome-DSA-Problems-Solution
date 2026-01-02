# Tower of Hanoi

## Problem Statement

The Tower of Hanoi game consists of three stacks (left, middle and right) and n round disks of different sizes. Initially, the left stack has all the disks, in increasing order of size from top to bottom.
The goal is to move all the disks to the right stack using the middle stack. On each move you can move the uppermost disk from a stack to another stack. In addition, it is not allowed to place a larger disk on a smaller disk.
Your task is to find a solution that minimizes the number of moves.

Input

The only input line has an integer n: the number of disks.

Output

First print an integer k: the minimum number of moves.

After this, print k lines that describe the moves. Each line has two integers a and b: you move a disk from stack a to stack b.


Example

Input:

2

Output:

3

1 2

1 3

2 3

---

##  Approach

- Read and understand , the Tower of Hanoi and solve it.
- And try to , dry run on copy.
- And, simple use recursion.
---

## Time Complexity
    O(2^n), for running all moves.
---

## Space Complexity

    O(1), no auxiliary space.
---
## Note
    Just dry run.
---

## Python Solution

```java
import java.util.Scanner;
public class Solution {
 
    static void hanoi(int n,int i,int k,int j){
        if(n==0)return ;
 
        hanoi(n-1,i,j,k);
        System.out.println(i+" "+k);
        hanoi(n-1,j,k,i);
    }
 
    public static void main(String[] args){
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt();
        System.out.println((1<<n)-1);
        hanoi(n,1,3,2);
        sc.close();
    }
}
