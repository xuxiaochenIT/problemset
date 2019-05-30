### 题目地址

[https://leetcode-cn.com/problems/rotate-list/](https://leetcode-cn.com/problems/rotate-list/)

### 题目描述

- 给定一个链表，旋转链表，将链表每个节点向右移动 k 个位置，其中 k 是非负数。

**示例 1：**

> 输入: 1->2->3->4->5->NULL, k = 2  
> 输出: 4->5->1->2->3->NULL  
> 解释:  
> 向右旋转 1 步: 5->1->2->3->4->NULL  
> 向右旋转 2 步: 4->5->1->2->3->NULL

**示例 2：**

> 输入: 0->1->2->NULL, k = 4  
> 输出: 2->0->1->NULL  
> 解释:  
> 向右旋转 1 步: 2->0->1->NULL  
> 向右旋转 2 步: 1->2->0->NULL  
> 向右旋转 3 步: 0->1->2->NULL  
> 向右旋转 4 步: 2->0->1->NULL

### 题解

```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def rotateRight(self, head: ListNode, k: int) -> ListNode:
        if not head or not head.next: return head
        # 链表个数
        num = 0
        p = head
        while p:
            num += 1
            p = p.next
        k = num - k % num
        p = head
        # 找前一段链表
        while k > 1:
            p = p.next
            k -= 1
        head1 = p.next
        if not head1: return head
        #前一段链表最后至空
        p.next = None
        p = head1
        # 后一段链表和前一段链表连接起来
        while p.next:
            p = p.next
        p.next = head
        return head1
```
