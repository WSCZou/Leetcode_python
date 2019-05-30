题目:

给定一个排序链表，删除所有含有重复数字的节点，只保留原始链表中 *没有重复出现* 的数字。

**示例 1:**

```
输入: 1->2->3->3->4->4->5
输出: 1->2->5
```

**示例 2:**

```
输入: 1->1->1->2->3
输出: 2->3
```

Solution:

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def deleteDuplicates(self, head: ListNode) -> ListNode:
        p = ListNode(float('inf')) # p 为 head 前一节点
        p.next = head
        ans = p
        while head:
            if head.next == None or head.val != head.next.val:
                p = p.next
                head = head.next
            else:
                while head.next != None and head.val == head.next.val:
                    head = head.next
                p.next = head.next
                head = head.next
        return ans.next
```

