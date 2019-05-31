### 题目地址

[https://leetcode-cn.com/problems/unique-paths/](https://leetcode-cn.com/problems/unique-paths/)

### 题目描述

- 一个机器人位于一个 m x n 网格的左上角 （起始点在下图中标记为“Start” ）。  

  机器人每次只能向下或者向右移动一步。机器人试图达到网格的右下角（在下图中标记为“Finish”）。  

  问总共有多少条不同的路径？

![](https://github.com/xuxiaochenIT/problemset/blob/master/pic/tencent50_62_unique-paths.png)

例如，上图是一个7 x 3 的网格。有多少可能的路径？

**说明：**  m 和 n 的值均不超过 100。

**示例 1：**

> 输入: m = 3, n = 2  
> 输出: 3  
> 解释:  
> 从左上角开始，总共有 3 条路径可以到达右下角。  
> 1.向右 -> 向右 -> 向下  
> 2.向右 -> 向下 -> 向右  
> 3.向下 -> 向右 -> 向右

### 题解

```
class Solution:
    def uniquePaths(self, m: int, n: int) -> int:
        pre = [1] * n
        cur = [1] * n
        for i in range(1, m):
            for j in range(1, n):
                cur[j] = pre[j] + cur[j-1]
            pre = cur[:]
        return pre[-1]
```
