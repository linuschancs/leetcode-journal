## Question:

You are climbing a staircase. It takes `n` steps to reach the top.

Each time you can either climb `1` or `2` steps. In how many distinct ways can you climb to the top?

## Idea:

For `n` number of steps, the number of ways to reach the top can be split into 2 groups:
1. Ending with `1` step
2. Ending with `2` steps

The number of ways to end with `1` step is equal to to the number of ways to climb to `n-1` steps.
While the number of ways to end with `2` steps is equal to the number of ways to climb `n-1` steps that ends with `1` step
(Can be visualised as converting the final single step to a double step).
This is equivalent to the number of ways to climb to `n-2` steps.

## Naive Solution (Recursion):
```
class Solution {
    public int climbStairs(int n) {
        if (n == 1) {
            return 1;
        } else if (n == 2) {
            return 2;
        } else {
            return climbStairs(n-1) + climbStairs(n-2);
        }
    }
}
```
Simple recursive solution however this is very time inefficient with O(N^2).
We observe that there are repeat function calls and this can be improved through memoisation/dynamic programming.

## Memoisation:
```
class Solution {
    public static int[] storage;
    public int climbStairs(int n) {
        if (n == 1) {
            return 1;
        } else if (n == 2) {
            return 2;
        } else {
            storage = new int[n];
            storage[0] = 1;
            storage[1] = 2;
            return memoise(n);
        }
    }
    public int memoise(int n) {
        if (storage[n-1] == 0) {
            storage[n-1] = memoise(n-1) + memoise(n-2);
            return storage[n-1];
        } else {
            return storage[n-1];
        }
    }
}
```

## Dynamic Programming:
```
class Solution {
    public int climbStairs(int n) {
        if (n == 1) {
            return 1;
        }
        int[] storage = new int[n];
        storage[0] = 1;
        storage[1] = 2;
        for (int i = 2; i < n; i++) {
            storage[i] = storage[i-1] + storage[i-2];
        }
        return storage[n-1];
    }
}
```
