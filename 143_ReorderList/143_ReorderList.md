题目:

给定一个单链表 *L*：*L*0→*L*1→…→*L**n*-1→*L*n ，
将其重新排列后变为： *L*0→*L**n*→*L*1→*L**n*-1→*L*2→*L**n*-2→…

你不能只是单纯的改变节点内部的值，而是需要实际的进行节点交换。

**示例 1:**

```
给定链表 1->2->3->4, 重新排列为 1->4->2->3.
```

**示例 2:**

```
给定链表 1->2->3->4->5, 重新排列为 1->5->2->4->3.
```

Solution:

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def reorderList(self, head: ListNode) -> None:
        """
        Do not return anything, modify head in-place instead.
        """
        if head == None or head.next == None:
            return
        
        #快慢指针
        slow = head
        fast = head
        while fast.next and fast.next.next:
            slow = slow.next
            fast = fast.next.next
        
        needReverser = slow.next
        slow.next = None

        #反转后半段
        p1 = None
        p2 = needReverser
        p3 = p2
        while p2:
            p3 = p2.next
            p2.next = p1
            p1 = p2
            p2 = p3
        
        needReverser  = p1
        
        #把后半段插入前半段空隙
        cur = head
        while cur and needReverser:
            curSecond = needReverser 
            needReverser  = needReverser.next
            nextcur = cur.next
            curSecond.next = cur.next
            cur.next = curSecond
            cur = nextcur
        
        
```

