# Permutation Sequence

## Problem Statement

```
The set [1, 2, 3, ..., n] contains a total of n! unique permutations.

By listing and labeling all of the permutations in order, we get the following sequence for n = 3:

"123"
"132"
"213"
"231"
"312"
"321"

Given n and k, return the kth permutation sequence.

Example 1:

Input: n = 3, k = 3
Output: "213"

Example 2:

Input: n = 4, k = 9
Output: "2314"

Example 3:

Input: n = 3, k = 1
Output: "123"
```

---
## Approach

```
1. First understand and dry run this problem on the copy.
2. for this problem, we use simple backtracking template.
3. we create an arraylist to hold string values and create an array vis to
   check for visited root and then, create an stringbuilder for new strings. 
4. create an dfs function, which helps us to creating the strings.
```

---

## Time Complexity
    O(n!), due to checking of both the paths.
---

## Space Complexity
    O(n!), to holding the string values.
---

## Java Solution

```java
class Solution {
    public String getPermutation(int n, int k) {
        String s="";
        for(int i=1;i<=n;i++){
            s+=String.valueOf(i);
        }
        ArrayList<String> ans=new ArrayList<>();
        boolean[] vis=new boolean[n];
        dfs(s,vis,ans,new StringBuilder(),n);
        return ans.get(k-1);
    }

    private void dfs(String s,boolean[] vis,ArrayList<String> ans,StringBuilder c,int n){
        if(c.length()==n){
            ans.add(c.toString());
            return ;
        }

        for(int i=0;i<n;i++){
            if(vis[i])continue;
            c.append(s.charAt(i));
            vis[i]=true;
            dfs(s,vis,ans,c,n);
            c.deleteCharAt(c.length()-1);
            vis[i]=false;
        }
    }
}
```
#### Contributed by - **orignlkartik1**
