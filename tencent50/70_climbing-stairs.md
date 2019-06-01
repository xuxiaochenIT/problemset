### 题目地址

[https://leetcode-cn.com/problems/climbing-stairs/](https://leetcode-cn.com/problems/climbing-stairs/)

### 题目描述

- 假设你正在爬楼梯。需要 n 阶你才能到达楼顶。

  每次你可以爬 1 或 2 个台阶。你有多少种不同的方法可以爬到楼顶呢？

  **注意：** 给定 n 是一个正整数。

**示例 1：**

> 输入： 2  
> 输出： 2  
> 解释： 有两种方法可以爬到楼顶。  
> 1.1 阶 + 1 阶  
> 2.2 阶

**示例 2：**

> 输出： 3  
> 解释： 有三种方法可以爬到楼顶。  
> 1.1 阶 + 1 阶 + 1 阶  
> 2.1 阶 + 2 阶  
> 3.2 阶 + 1 阶


### 题解

动态规划：

第 ii 阶可以由以下两种方法得到：

1.在第 (i-1)(i−1) 阶后向上爬一阶。

2.在第 (i-2)(i−2) 阶后向上爬 22 阶。

所以到达第 ii 阶的方法总数就是到第 (i-1)(i−1) 阶和第 (i-2)(i−2) 阶的方法数之和。

令 dp[i]dp[i] 表示能到达第 ii 阶的方法总数：

&emsp;&emsp;dp[i]=dp[i-1]+dp[i-2]  
&emsp;&emsp;dp[i]=dp[i−1]+dp[i-2]

```
class Solution:
   # dp[i] = dp[i-1]+dp[i-2]
   def climbStairs(self, n: int) -> int:
       dp = []
       dp.append(1) # 初始状态，只有1阶的时候有一种走法
       dp.append(2) # 有2阶的时候有两种走法
       if n==1:
           return 1
       if n==2:
           return 2
       for i in range(2,n):
           dp.append(dp[i-1]+dp[i-2])

       return dp[-1]
```
