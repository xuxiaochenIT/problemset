### 题目地址

[https://leetcode-cn.com/problems/merge-sorted-array/](https://leetcode-cn.com/problems/merge-sorted-array/)

### 题目描述

- 给定两个有序整数数组 nums1 和 nums2，将 nums2 合并到 nums1 中，使得 num1 成为一个有序数组。

  **说明：**
  - 初始化 nums1 和 nums2 的元素数量分别为 m 和 n。  
  - 你可以假设 nums1 有足够的空间（空间大小大于或等于 m + n）来保存 nums2 中的元素。

**示例：**

> 输入:  
> nums1 = [1,2,3,0,0,0], m = 3  
> nums2 = [2,5,6],&emsp;&emsp;n = 3  
>   
> 输出: [1,2,2,3,5,6]

### 题解

```
class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
        """
        Do not return anything, modify nums1 in-place instead.
        """
        while n > 0:
            if m and nums1[m-1] > nums2[n-1]:
                nums1[m+n-1], m, n = nums1[m-1], m-1, n
            else:
                nums1[m+n-1], m, n = nums2[n - 1], m, n-1
```
