## Question:

Write a function that reverses a string. The input string is given as an array of characters `s`.

You must do this by modifying the input array in-place with O(1) extra memory.

## Idea:

Simple reversal of array question.
Iterate through array with a counter and swap the i-th element from the start of array with the i-th element from the end of array.

## Solution:

```
class Solution {
    public void reverseString(char[] s) {
        int length = s.length;
        for (int i = 0; i < length/2; i++) {
            char temp = s[i];
            s[i] = s[length - i - 1];
            s[length - i - 1] = temp;
        }
    }
}
```

Time complexity: O(n)

**Beats 99.74% of submissions on leetcode**

Space complexity: O(1) extra memory (due to array in-place swapping)

**Beats 82.68% of submissions on leetcode**
