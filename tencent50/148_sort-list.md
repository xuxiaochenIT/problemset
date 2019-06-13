### 题目地址

[https://leetcode-cn.com/problems/sort-list/](https://leetcode-cn.com/problems/sort-list/)

### 题目描述

- 在 O(n log n) 时间复杂度和常数级空间复杂度下，对链表进行排序。


**示例 1：**

> 输入: 4->2->1->3  
> 输出: 1->2->3->4

**示例 2：**

> 输入: -1->5->3->4->0  
> 输出: -1->0->3->4->5


### 题解

```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def sortList(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        if head is None or head.next is None:
            return head
        mid =  self.get_mid(head)
        l = head
        r = mid.next
        mid.next = None
        return self.merge(self.sortList(l),self.sortList(r))

    def merge(self,p,q):
        tmp = ListNode(0)
        h = tmp
        while p and q:
            if p.val < q.val:
                h.next = p
                p = p.next
            else:
                h.next = q
                q = q.next
            h = h.next
        if p:
            h.next = p
        if q:
            h.next = q
        return tmp.next

    def get_mid(self,node):
        if node is None:
            return node
        fast = slow = node
        while fast.next and fast.next.next:
            slow = slow.next
            fast =fast.next.next
        return slow
```
