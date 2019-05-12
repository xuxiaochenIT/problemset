### 题目地址

[https://leetcode-cn.com/problems/longest-palindromic-substring/](https://leetcode-cn.com/problems/longest-palindromic-substring/)

### 题目描述

- 给定一个字符串 s，找到 s 中最长的回文子串。你可以假设 s 的最大长度为 1000。

**示例 1：**

> 输入: "babad"  
> 输出: "bab"  
> 注意: "aba" 也是一个有效答案。

**示例 2：**

> 输入: "cbbd"  
> 输出: "bb"

### 解题思路

把每个字母当成回文串的中心（这里要考虑两种情况，回文串的长度为奇数或者偶数情况。）

### 题解

```
class Solution:
    def longestPalindrome(self, s: str) -> str:
        n = len(s)
        res = ""
        for i in range(0,n):
            #以s[i] 为中心向左右扩散
            left, right = i, i
            while(left >= 0 and right < n and s[left] == s[right]):
                left -= 1
                right += 1
                if len(res) < right - left - 1:
                    res = s[left+1:right]
            #以s[i],s[i+1]为中心向左右扩散
            left, right = i, i + 1
            while(left >= 0 and right < n and s[left] == s[right]):
                left -= 1
                right += 1
                if len(res) < right - left - 1:
                    res = s[left+1:right]
        return res
```
