### 题目地址

[https://leetcode-cn.com/problems/merge-two-sorted-lists/](https://leetcode-cn.com/problems/merge-two-sorted-lists/1)

### 题目描述

- 将两个有序链表合并为一个新的有序链表并返回。新链表是通过拼接给定的两个链表的所有节点组成的。

**示例：**

> 输入：1->2->4, 1->3->4  
> 输出：1->1->2->3->4->4

### 题解

1.两个链表均为有序链表，只需要对值进行判断，按照从小到大的顺序将链表连接起来就可实现

```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def mergeTwoLists(self, l1: ListNode, l2: ListNode) -> ListNode:
        dummy = ListNode(0)
        p = dummy
        while l1 or l2:
            if l1 and l2:
                tmp1 = l1.val
                tmp2 = l2.val
                if tmp1 < tmp2:
                    p.next = ListNode(tmp1)
                    l1 = l1.next
                else:
                    p.next = ListNode(tmp2)
                    l2 = l2.next
            elif l1:
                p.next = ListNode(l1.val)
                l1 = l1.next
            elif l2:
                p.next = ListNode(l2.val)
                l2 = l2.next
            p = p.next
        return dummy.next
```

2.递归

```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def mergeTwoLists(self, l1: ListNode, l2: ListNode) -> ListNode:
        if not l1: return l2
        if not l2: return l1
        if l1.val < l2.val:
            l1.next = self.mergeTwoLists(l1.next,l2)
            return l1
        else:
            l2.next = self.mergeTwoLists(l1,l2.next)
            return l2
```
