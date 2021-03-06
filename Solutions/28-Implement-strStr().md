# 28. Implement strStr()

Implement [strStr()](https://www.cplusplus.com/reference/cstring/strstr/).

Return the index of the first occurrence of needle in haystack, or `-1` if `needle` is not part of `haystack`.

**Clarification**:

What should we return when `needle` is an empty string? This is a great question to ask during an interview.

For the purpose of this problem, we will return 0 when `needle` is an empty string. This is consistent to C's [strStr()](https://www.cplusplus.com/reference/cstring/strstr/) and Java's [indexOf()](https://docs.oracle.com/javase/7/docs/api/java/lang/String.html#indexOf(java.lang.String)).

## Example 1:
```
Input: haystack = "hello", needle = "ll"
Output: 2
```

## Example 2:
```
Input: haystack = "aaaaa", needle = "bba"
Output: -1
```

## Example 3:
```
Input: haystack = "", needle = ""
Output: 0
```

## Constraints:
- <code>0 <= haystack.length, needle.length <= 5 * 10<sup>4</sup></code>
- `haystack` and `needle` consist of only lower-case English characters

# Solution
```python
class Solution:
    def strStr(self, haystack: str, needle: str) -> int:
        if not needle:
            return 0
        ans = -1
        for i in range(len(haystack)-len(needle)+1):
            if haystack[i:i+len(needle)] == needle:
                ans = i
                break
        return ans
```
Python's simple string operation. 
