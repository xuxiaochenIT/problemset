### 题目地址

[https://leetcode-cn.com/problems/longest-common-prefix/](https://leetcode-cn.com/problems/longest-common-prefix/)

### 题目描述

- 编写一个函数来查找字符串数组中的最长公共前缀。  
如果不存在公共前缀，返回空字符串 ""。

**示例 1：**

> 输入: ["flower","flow","flight"]  
> 输出: "fl"

**示例 2：**

> 输入: ["dog","racecar","car"]  
> 输出: ""  
> 解释: 输入不存在公共前缀。


**说明:**

所有输入只包含小写字母 a-z 。

### 解题思路

set() 函数创建一个无序不重复元素集，可进行关系测试，删除重复数据，还可以计算交集、差集、并集等。  
zip() 函数用于将可迭代的对象作为参数，将对象中对应的元素打包成一个个元组，然后返回由这些元组组成的列表。

### 题解

```
class Solution:
    def longestCommonPrefix(self, strs: List[str]) -> str:
        res = ""
        for tmp in zip(*strs):
            if len(set(tmp)) == 1:
                res += tmp[0]
            else:
                break
        return res
```
