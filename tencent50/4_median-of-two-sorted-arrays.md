### 题目地址

[https://leetcode-cn.com/problems/median-of-two-sorted-arrays/](https://leetcode-cn.com/problems/median-of-two-sorted-arrays/)

### 题目描述

- 给定两个大小为 m 和 n 的有序数组 nums1 和 nums2。  
请你找出这两个有序数组的中位数，并且要求算法的时间复杂度为 O(log(m + n)）。  
你可以假设 nums1 和 nums2 不会同时为空。

**示例 1：**

> nums1 = [1, 3]  
> nums2 = [2]  
>    
> 则中位数是 2.0  

**示例 2：**

> nums1 = [1, 2]  
> nums2 = [3, 4]  
>  
> 则中位数是 (2 + 3)/2 = 2.5

### 题目思路
中位数，又称中值。中位数是按顺序排列的一组数据中居于中间位置的数，即在这组数据中，有一半的数据比他大，有一半的数据比他小。即一组已排序数据：$X_1,...,X_N$，当N为奇数时，中位数为$X_{(N+1)/2}$,当N为偶数时，中位数为 $\frac{X_(N/2)+X_(N/2+1)}{2}$

一看题目，第一思路是先把两个数组合并，然后排序，直接求出结果。
但是题目明确要求了时间复杂度为O(log(m+n))，这样做显然达不到要求。
可以考虑使用二分法解决问题。

### 题解

```
class Solution:
    def findMedianSortedArrays(self, nums1: List[int], nums2: List[int]) -> float:
        m = len(nums1)
        n = len(nums2)
        if m > n:
            return self.findMedianSortedArrays(nums2,nums1)
        k = (m + n + 1)//2
        left = 0
        right = m
        while left < right :
            i = left +(right - left)//2
            j = k - i
            if nums1[i] < nums2[j]:
                left = i + 1
            else:
                right = i
        i = left
        j = k - i
        c1 = max(nums1[i-1] if i > 0 else float("-inf"), nums2[j-1] if j > 0 else float("-inf") )
        if (m + n) % 2 == 1:
            return c1
        c2 = min(nums1[i] if i < m else float("inf"), nums2[j] if j < n else float("inf"))
        return (c1 + c2) / 2

```
