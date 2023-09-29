
## Question:

Given an integer n, return an array ans of length n + 1 such that for each i (0 <= i <= n), ans[i] is the number of 1's in the binary representation of i.

## Idea:

## Learning Point:

There is a python format method that is able to convert an int to its bits representation.
eg. bits = format(i, 'b') OR bits = "{0:b}".format(37)

## Naive Solution (Iterative):
```
class Solution:
    def countBits(self, n: int) -> List[int]:
        arr = []
        for i in range(n + 1):
            num = 0
            bits = format(i, 'b')
            for bit in bits:
                if bit == '1':
                    num+=1
            arr.append(num)
        return arr
```
Runtime: Beats 20.55% of users with Python3
Memory: Beats 59.39% of users with Python3

Simple iterative solution however there must be a way we can do better.
There is a time complexity of O(n * bits).

## Dynamic Programming:
```
class Solution:
    def countBits(self, n: int) -> List[int]:
        ans = [0] * (n + 1)

        for i in range(1, n + 1):
            ans[i] = ans[i >> 1] + (i & 1)

        return ans
```

Uses the fact that `ans[i] = ans[i / 2] + (i % 2)`
