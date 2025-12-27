# Number of Pairs

## Problem Statement
You are given an array a of n
integers. Find the number of pairs (i,j)
(1≤i<j≤n
) where the sum of ai+aj
is greater than or equal to l
and less than or equal to r
(that is, l≤ai+aj≤r
).

For example, if n=3
, a=[5,1,2]
, l=4
and r=7
, then two pairs are suitable:

i=1
and j=2
(4≤5+1≤7
);
i=1
and j=3
(4≤5+2≤7
).
Input
The first line contains an integer t
(1≤t≤104
). Then t
test cases follow.

The first line of each test case contains three integers n,l,r
(1≤n≤2⋅105
, 1≤l≤r≤109
) — the length of the array and the limits on the sum in the pair.

The second line contains n
integers a1,a2,…,an
(1≤ai≤109
).

It is guaranteed that the sum of n
overall test cases does not exceed 2⋅105
.

Output
For each test case, output a single integer — the number of index pairs (i,j)
(i<j
), such that l≤ai+aj≤r
.
---

##  Approach

- This is just, simple question after reading two or three times you get the logic.
- But, one thing which is matter here is constraint , which is 10^5.
- So, brute force is not working O(n^2). you want to come up with any other logic.
- So, we want to do it in O(n) or O(nlogn).
- we use simple for loop for and create two function for find upper bound and lower bound and just return it to the cnt. 
---

## Time Complexity

    O(nlogn), simple for loop and inside it using binary search.
---

## Space Complexity

    O(1), no auxiliary space.
---
## Note
    Take value in Long , it is a competitive programming question.

---

## Java Solution

```java
import java.io.BufferedInputStream;
import java.util.*;

public class Main {

    static class FastScanner {
        private final BufferedInputStream in = new BufferedInputStream(System.in);
        private final byte[] buffer = new byte[1 << 16];
        private int ptr = 0, len = 0;

        private int read() {
            if (ptr >= len) {
                try {
                    len = in.read(buffer);
                    ptr = 0;
                    if (len <= 0) return -1;
                } catch (Exception e) {
                    return -1;
                }
            }
            return buffer[ptr++];
        }

        int nextInt() {
            int c;
            while ((c = read()) <= ' ');
            int sign = 1;
            if (c == '-') {
                sign = -1;
                c = read();
            }
            int val = 0;
            while (c > ' ') {
                val = val * 10 + (c - '0');
                c = read();
            }
            return val * sign;
        }
    }

    static long numberOfPairs(int n, int l, int r, int[] arr) {
        Arrays.sort(arr);
        long cnt = 0;

        for (int i = 0; i < n; i++) {
            int left = lowerBound(arr, i + 1, n - 1, l - arr[i]);
            int right = upperBound(arr, i + 1, n - 1, r - arr[i]);

            if (left <= right) {
                cnt += (right - left + 1);
            }
        }
        return cnt;
    }

    // First index >= target
    static int lowerBound(int[] arr, int le, int ri, int target) {
        int ans = ri + 1;
        while (le <= ri) {
            int mid = (le + ri) >>> 1;
            if (arr[mid] >= target) {
                ans = mid;
                ri = mid - 1;
            } else {
                le = mid + 1;
            }
        }
        return ans;
    }

    // Last index <= target
    static int upperBound(int[] arr, int le, int ri, int target) {
        int ans = le - 1;
        while (le <= ri) {
            int mid = (le + ri) >>> 1;
            if (arr[mid] <= target) {
                ans = mid;
                le = mid + 1;
            } else {
                ri = mid - 1;
            }
        }
        return ans;
    }

    public static void main(String[] args) {
        FastScanner fs = new FastScanner();
        int t = fs.nextInt();

        while (t-- > 0) {
            int n = fs.nextInt();
            int l = fs.nextInt();
            int r = fs.nextInt();
            int[] arr = new int[n];

            for (int i = 0; i < n; i++) {
                arr[i] = fs.nextInt();
            }

            System.out.println(numberOfPairs(n, l, r, arr));
        }
    }
}