### 题目地址

[https://leetcode-cn.com/problems/add-two-numbers/](https://leetcode-cn.com/problems/add-two-numbers/)

### 题目描述

- 给出两个非空的链表用来表示两个非负的整数。其中，它们各自的位数是按照逆序的方式存储的，并且它们的每个节点只能存储一位数字。如果，我们将这两个数相加起来，则会返回一个新的链表来表示它们的和。您可以假设除了数字 0 之外，这两个数都不会以 0 开头。

**示例**：

> 输入：(2 -> 4 -> 3) + (5 -> 6 -> 4)

> 输出：7 -> 0 -> 8

> 原因：342 + 465 = 807

### 题解

python3:

```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:  
        l3 = ListNode(0)  # 结果链表
        newnode = l3
        carry = 0  # 进位 carry 初始化为 0
        while l1 or l2:  # 进行计算的两个结点非空则继续执行
            v1 = v2 = 0  # 定义v1、v2变量，若两个链表长度不同依然可以进行加和操作
            if l1:  # 如果l1非空，把l1当前结点值赋给value1,并指向下一个结点
                value1 = l1.val  
                l1 = l1.next  
            if l2:  # 如果l2非空，把l1当前节点值赋给value2,并指向下一个结点
                value2 = l2.val
                l2 = l2.next
            sum = value1 +value2 + carry  # 两个链表对应值相加
            carry = sum // 10  # 和值作除取整做下次进位值
            sum = sum % 10  # 和值作除取余为新链表的结点值
            newnode.next = ListNode(sum)
            newnode = newnode.next  # 指向下一个新链表下一个结点
        if carry:  # 原始两个链表全部遍历后，若最后一次加和有进位1，则需要在新链表中加入一个结点存储该进位值
            new.next = ListNode(1)
        return l3.next

```
