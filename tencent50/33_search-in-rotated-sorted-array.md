### 题目地址

[https://leetcode-cn.com/problems/search-in-rotated-sorted-array/](https://leetcode-cn.com/problems/search-in-rotated-sorted-array/)

### 题目描述

- 假设按照升序排序的数组在预先未知的某个点上进行了旋转。  
( 例如，数组 [0,1,2,4,5,6,7] 可能变为 [4,5,6,7,0,1,2] )。  
搜索一个给定的目标值，如果数组中存在这个目标值，则返回它的索引，否则返回 -1 。  
你可以假设数组中不存在重复的元素。  
你的算法时间复杂度必须是 O(log n) 级别。


**示例 1：**

> 输入: nums = [4,5,6,7,0,1,2], target = 0  
> 输出: 4

**示例 2：**

> 输入: nums = [4,5,6,7,0,1,2], target = 3  
> 输出: -1

### 解题思路

题目中要求时间复杂度为 O(log n) ，首先想到二分法
1. 先用二分法找出最小值，接下来判断 target 是在分割点的左边还是右边;  
最后再使用一次二分法找出 target 的位置. 所以时间复杂度为：O(logn)O(logn)
2. 直接使用二分法，判断那个二分点,有几种可能性：  
(1)直接等于target  
(2)在左半边的递增区域:  
&emsp;a. target 在 left 和 mid 之间  
&emsp;b. 不在这之间  
(3)在右半边的递增区域:  
&emsp;a. target 在 mid 和 right 之间   
&emsp;b. 不在这之间

### 题解

```
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        if not nums:return -1
        n = len(nums)
        left = 0
        right = len(nums) - 1
        while left < right:
            mid = left + (right - left) //2
            if nums[mid] > nums[right]:
                left = mid + 1
            else:
                right = mid
        t = left
        left = 0
        right = len(nums) - 1
        while left <= right:
            mid = (left + right) //2
            realmid = (mid + t) % n
            if nums[realmid] == target:
                return realmid
            elif nums[realmid] > target:
                right = mid - 1
            else:
                left = mid + 1
        return -1
```

```
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        n = len(nums)
        if n == 0:
            return -1
        left = 0
        right = n - 1
        while left < right:
            mid = left + (right - left) // 2
            if nums[mid] == target:
                return mid
            elif nums[left] <= nums[mid]:
                if nums[left] <= target < nums[mid]:
                    right = mid - 1
                else:
                    left = mid + 1
            else:
                if nums[mid] < target <= nums[right]:
                    left = mid + 1
                else:
                    right = mid - 1
        #print(left,right)
        return left if nums[left] == target else -1
```
