## Question:

Given an integer `n`, return a string array answer (1-indexed) where:

* `answer[i] == "FizzBuzz"` if `i` is divisible by `3` and `5`.
* `answer[i] == "Fizz"` if `i` is divisible by `3`.
* `answer[i] == "Buzz"` if `i` is divisible by `5`.
* `answer[i] == i` (as a string) if none of the above conditions are true.

## Idea:

Simple iteration through n and checking condition using if-statements to add respective entries into List.

## Solution:

```
class Solution {
    public List<String> fizzBuzz(int n) {
        List<String> answer = new ArrayList<String>();
        for (int i = 1; i < n + 1; i++) {
            if (i % 3 == 0 && i % 5 == 0) {
                answer.add("FizzBuzz");
            } else if (i % 3 == 0) {
                answer.add("Fizz");
            } else if (i % 5 == 0) {
                answer.add("Buzz");
            } else {
                answer.add(String.valueOf(i));
            }
        }
        return answer;
    }
}
```

Time Complexity: O(n)
**Beats 100% of submissions on leetcode**
Space Complexity: O(n)
**Beats 93.49% of submissions on leetcode**
