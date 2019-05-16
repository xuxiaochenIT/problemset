### 题目地址

[https://leetcode-cn.com/problems/container-with-most-water/](https://leetcode-cn.com/problems/container-with-most-water/)

### 题目描述

- 给定 n 个非负整数 $a_1$，$a_2$，...，$a_n$，每个数代表坐标中的一个点 (i, $a_i$) 。在坐标内画 n 条垂直线，垂直线 i 的两个端点分别为 (i, $a_i$) 和 (i, 0)。找出其中的两条线，使得它们与 x 轴共同构成的容器可以容纳最多的水。

**说明**：你不能倾斜容器，且 n 的值至少为 2。

![](https://github.com/xuxiaochenIT/problemset/blob/master/pic/tencent50_11_container-with-most-water.jpg)

图中垂直线代表输入数组 [1,8,6,2,5,4,8,3,7]。在此情况下，容器能够容纳水（表示为蓝色部分）的最大值为 49。

**示例：**

> 输入: [1,8,6,2,5,4,8,3,7]  
> 输出: 49

### 解题思路

思路：暴力求解，求每两个线段的面积，找最大值，但时间复杂度O(n^2)

### 题解

```
class Solution:
    def maxArea(self, height: List[int]) -> int:
        max_area = 0
        for i in range(len(height)):
            for j in range(1, len(height)):
                max_area = max(min(height[i], height[j])*(j-i), max_area)
        return max_area

```
