### 题目地址

[https://leetcode-cn.com/problems/3sum-closest/](https://leetcode-cn.com/problems/3sum-closest/)

### 题目描述

- 给定一个包括 n 个整数的数组 nums 和 一个目标值 target。找出 nums 中的三个整数，使得它们的和与 target 最接近。返回这三个数的和。假定每组输入只存在唯一答案。

> 例如，给定数组 nums = [-1，2，1，-4], 和 target = 1.  
>   
> 与 target 最接近的三个数的和为 2. (-1 + 2 + 1 = 2).

### 题解

```
class Solution:
    def threeSumClosest(self, nums: List[int], target: int) -> int:

        nums.sort()
        #print(nums)
        n = len(nums)
        res = float("inf")
        for i in range(n):
            if i > 0 and nums[i] == nums[i-1]:
                continue
            left = i + 1
            right = n - 1
            while left < right :
                #print(left,right)
                cur = nums[i] + nums[left] + nums[right]
                if cur == target:return target
                if abs(res-target) > abs(cur-target):
                    res = cur
                if cur > target:
                    right -= 1
                elif cur < target:
                    left += 1
        return res
```
