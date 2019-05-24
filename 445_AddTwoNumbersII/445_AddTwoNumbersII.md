题目:

给定两个**非空**链表来代表两个非负整数。数字最高位位于链表开始位置。它们的每个节点只存储单个数字。将这两数相加会返回一个新的链表。

 

你可以假设除了数字 0 之外，这两个数字都不会以零开头。

**进阶:**

如果输入链表不能修改该如何处理？换句话说，你不能对列表中的节点进行翻转。

**示例:**

```
输入: (7 -> 2 -> 4 -> 3) + (5 -> 6 -> 4)
输出: 7 -> 8 -> 0 -> 7
```

Solution:

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def addTwoNumbers(self, n1, n2):
        l1 = self.list_to_stack(n1)
        l2 = self.list_to_stack(n2)
        stack = self.add_helper(l1,l2)
        return self.stack_to_list(stack)

    def list_to_stack(self, node):
        stack = []
        while node:
            stack.append(node.val)
            node = node.next
        return stack

    def add_helper(self, s1, s2):
        res = []
        carry = 0
        while s1 or s2 or carry:
            num1 = s1.pop() if s1 else 0
            num2 = s2.pop() if s2 else 0
            total = num1 + num2 + carry
            res.append(total % 10)
            carry = total // 10
        return res

    def stack_to_list(self, stack):
        head = ListNode(0)
        cur = head
        while stack:
            cur.next = ListNode(stack.pop())
            cur = cur.next
        return head.next
```

