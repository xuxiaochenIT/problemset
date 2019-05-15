### 题目地址

[https://leetcode-cn.com/problems/palindrome-number/](https://leetcode-cn.com/problems/palindrome-number/)

### 题目描述

- 判断一个整数是否是回文数。回文数是指正序（从左向右）和倒序（从右向左）读都是一样的整数。

**示例 1：**

> 输入: 121  
> 输出: true

**示例 2：**

> 输入: -121  
> 输出: false
> 解释: 从左向右读, 为 -121 。 从右向左读, 为 121- 。因此它不是一个回文数。

**示例 3：**

> 输入: 10  
> 输出: false  
> 解释: 从右向左读, 为 01 。因此它不是一个回文数。

### 解题思路

1. 将数字转换为字符串，并检查字符串是否为回文。

2. 将数字本身反转，然后将反转后的数字与原始数字进行比较，如果它们是相同的，那么这个数字就是回文。但是，如果反转后的数字大于int.MAX，我们将遇到整数溢出问题。为了避免数字反转可能导致的溢出问题，可以考虑只反转数字的一半。

### 题解

算法1：

```
class Solution:
    def isPalindrome(self, x: int) -> bool:
        if x < 0:
            return False
        else:
            res = str(x)[::-1]
            if res == str(x):
                return True
            else:
                return False
```

算法2：
```
class Solution:
    def isPalindrome(self, x: int) -> bool:
        if x < 0 or (x % 10 == 0 and x != 0):
            return False
        revertedNumber = 0
        while x > revertedNumber:
            revertedNumber = revertedNumber * 10 + x % 10
            x /= 10
        if x == revertedNumber or x == revertedNumber/10:
            return True
        else:
            return False
```
