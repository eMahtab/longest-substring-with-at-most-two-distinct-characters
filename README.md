# Longest Substring with At Most Two Distinct Characters
## https://leetcode.com/problems/longest-substring-with-at-most-two-distinct-characters

Given a string s, return the length of the longest substring that contains at most two distinct characters.
```java
Example 1:

Input: s = "eceba"
Output: 3
Explanation: The substring is "ece" which its length is 3.

Example 2:

Input: s = "ccaabbb"
Output: 5
Explanation: The substring is "aabbb" which its length is 5.
``` 

## Constraints:

1. 1 <= s.length <= 10^5
2. s consists of English letters.

# Implementation : Sliding Window
```java
class Solution {
    public int lengthOfLongestSubstringTwoDistinct(String s) {
        int n = s.length();
        if (n <= 2) return n;

        int left = 0, right = 0;
        HashMap<Character, Integer> hashmap = new HashMap<Character, Integer>();
        int max_len = 2;
        while (right < n) {
            hashmap.put(s.charAt(right), right);
            if (hashmap.size() > 2) {
                int del_idx = Collections.min(hashmap.values());
                hashmap.remove(s.charAt(del_idx));
                left = del_idx + 1;
            }
            max_len = Math.max(max_len, right - left + 1);
            right++;
        }
        return max_len;
    }
}
```

# References :
https://leetcode.com/problems/longest-substring-with-at-most-two-distinct-characters/editorial
