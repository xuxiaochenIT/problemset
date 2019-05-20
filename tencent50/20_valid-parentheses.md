### 题目地址

[https://leetcode-cn.com/problems/valid-parentheses/](https://leetcode-cn.com/problems/valid-parentheses/)

### 题目描述

- 给定一个只包括 '('，')'，'{'，'}'，'['，']' 的字符串，判断字符串是否有效。

有效字符串需满足：

>  1.左括号必须用相同类型的右括号闭合。  
>  2.左括号必须以正确的顺序闭合。

注意空字符串可被认为是有效字符串。


**示例 1：**

> 输入: "()"  
> 输出: true

**示例 2：**

> 输入: "()[]{}"  
> 输出: true

**示例 3：**

> 输入: "(]"  
> 输出: false

**示例 4：**

> 输入: "([)]"  
> 输出: false

**示例 5：**

> 输入: "{[]}"  
> 输出: true

### 解题思路

replace() 方法把字符串中的 old（旧字符串） 替换成 new(新字符串)，如果指定第三个参数max，则替换不超过 max 次。

### 题解

```
class Solution:
    def isValid(self, s):
        while '{}' in s or '()' in s or '[]' in s:
            s = s.replace('{}', '')
            s = s.replace('[]', '')
            s = s.replace('()', '')
        return s == ''
```
