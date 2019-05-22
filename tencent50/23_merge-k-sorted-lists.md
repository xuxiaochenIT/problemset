### 题目地址

[https://leetcode-cn.com/problems/merge-k-sorted-lists/](https://leetcode-cn.com/problems/merge-k-sorted-lists/)

### 题目描述

- 合并 k 个排序链表，返回合并后的排序链表。请分析和描述算法的复杂度。

**示例：**

> 输入:  
> [  
>   1->4->5,  
>   1->3->4,  
>   2->6  
> ]  
> 输出: 1->1->2->3->4->4->5->6

### 题解

1. 先把所有值读取到一个新list中，使用sort排序 ，再生成新的链表

```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def mergeKLists(self, lists: List[ListNode]) -> ListNode:
        n, dummy = len(lists), ListNode(0)
        p, res = dummy, []
        for i in range(n):
            while(lists[i]):
                res.append(lists[i].val)
                lists[i]=lists[i].next
        res.sort()
        for i in range(len(res)):
            p.next = ListNode(res[i])
            p = p.next
        return dummy.next
```

2. 分治

```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def mergeKLists(self, lists: List[ListNode]) -> ListNode:
        if not lists:return
        n = len(lists)
        return self.merge(lists, 0, n-1)
    def merge(self,lists, left, right):
        if left == right:
            return lists[left]
        mid = left + (right - left) // 2
        l1 = self.merge(lists, left, mid)
        l2 = self.merge(lists, mid+1, right)
        return self.mergeTwoLists(l1, l2)
    def mergeTwoLists(self,l1, l2):
        if not l1:return l2
        if not l2:return l1
        if l1.val < l2.val:
            l1.next = self.mergeTwoLists(l1.next, l2)
            return l1
        else:
            l2.next = self.mergeTwoLists(l1, l2.next)
            return l2
```
