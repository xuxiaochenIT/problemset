### 题目地址

[https://leetcode-cn.com/problems/multiply-strings/](https://leetcode-cn.com/problems/multiply-strings/)

### 题目描述

- 给定两个以字符串形式表示的非负整数 num1 和 num2，返回 num1 和 num2 的乘积，它们的乘积也表示为字符串形式。

**示例 1：**

> 输入: num1 = "2", num2 = "3"  
> 输出: "6"

**示例 2：**

> 输入: num1 = "123", num2 = "456"  
> 输出: "56088"

**说明：**

&emsp;1.num1 和 num2 的长度小于110。  
&emsp;2.num1 和 num2 只包含数字 0-9。  
&emsp;3.num1 和 num2 均不以零开头，除非是数字 0 本身。  
&emsp;4.不能使用任何标准库的大数类型（比如 BigInteger）或直接将输入转换为整数来处理。

### 题解

```
class Solution:
    def multiply(self, num1: str, num2: str) -> str:
        """
            字符串相乘, Karatsuba算法，n的1.58次方, https://zh.wikipedia.org/wiki/Karatsuba%E7%AE%97%E6%B3%95

            给定两个以字符串形式表示的非负整数 num1 和 num2，返回 num1 和 num2 的乘积，
            它们的乘积也表示为字符串形式。

            输入: num1 = "123", num2 = "456"
            输出: "56088"
        """
        return str(self.karatsuba(num1, num2))

    def karatsuba(self, num1, num2):
        if not num1 or not num2:
            return 0
        n, m = len(num1), len(num2)
        if (n < 2) or (m < 2):
            return int(num1) * int(num2)

        maxLength = max(n, m)
        splitPosition = maxLength // 2
        high1, low1 = num1[:-splitPosition], num1[-splitPosition:]
        high2, low2 = num2[:-splitPosition], num2[-splitPosition:]
        z0 = self.karatsuba(low1, low2)
        z1 = self.karatsuba(str(int(low1) + int(high1 or "0")), str(int(low2) + int(high2 or "0")))
        z2 = self.karatsuba(high1, high2)

        return (z2 * 10 ** (2 * splitPosition)) + ((z1 - z2 - z0) * 10 ** (splitPosition)) + z0
```
