题目:

给定一个链表，两两交换其中相邻的节点，并返回交换后的链表。

**你不能只是单纯的改变节点内部的值**，而是需要实际的进行节点交换。

 

**示例:**

```
给定 1->2->3->4, 你应该返回 2->1->4->3.
```

solution:

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def swapPairs(self, head: ListNode) -> ListNode:
        dummy = ListNode(0)
        p = dummy
        h = head
        while h:
            if h and h.next:
                tmp = h.next
                p.next = tmp
                # 交换 位置
                h.next = h.next.next
                tmp.next = h
                h = h.next
                p = p.next.next
            else:
                p.next = h
                h = h.next
        return dummy.next
```

