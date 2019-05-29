### 题目地址

[https://leetcode-cn.com/problems/spiral-matrix-ii/](https://leetcode-cn.com/problems/spiral-matrix-ii/)

### 题目描述

- 给定一个正整数 n，生成一个包含 1 到 $n^2$ 所有元素，且元素按顺时针顺序螺旋排列的正方形矩阵。

**示例 ：**

> 输入: 3  
> 输出:  
> [  
>  [ 1, 2, 3 ],  
>  [ 8, 9, 4 ],  
>  [ 7, 6, 5 ]  
> ]

### 题解

1. 有两个方向，所以使用二维元组存储方向状态上 右:(0, 1)，右下(1, 0)，下左(0, -1)，左上(-1, 0)。
2. 判断如何转向读取数据时，每行，列的最后一个元素是将要读取的列，行的起点。起点已经被读取，就想到取模操作可以得到当前列，行的下一步状态。

```
class Solution:
    def generateMatrix(self, n):
        ans = [[0] * n for _ in range(n)]
        x, y, dx, dy = 0, 0, 0, 1
        for i in range(1, n * n + 1):
            ans[x][y] = i
            if ans[(x + dx) % n][(y + dy) % n] > 0:
                dx, dy = dy, -dx
            x, y = x + dx, y + dy
        return ans
```
