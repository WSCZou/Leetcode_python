题目：

给定一个单链表，其中的元素按升序排序，将其转换为高度平衡的二叉搜索树。

本题中，一个高度平衡二叉树是指一个二叉树*每个节点* 的左右两个子树的高度差的绝对值不超过 1。

**示例:**

```
给定的有序链表： [-10, -3, 0, 5, 9],

一个可能的答案是：[0, -3, 9, -10, null, 5], 它可以表示下面这个高度平衡二叉搜索树：

      0
     / \
   -3   9
   /   /
 -10  5
```

solution：

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def sortedListToBST(self, head):

        def getmidnode(node):
            
            fast = node
            slow = node
            pre = None
            
            while fast.next and fast.next.next:
                
                pre = slow #断开左边
                fast = fast.next.next
                slow = slow.next
            
            if  slow != node:
                pre.next = None #断开左边
                return node, slow
            else:
                return None, slow
            
        if head is None:
            return None
        
        p, x = getmidnode(head)
        root = TreeNode(x.val)
        root.left = self.sortedListToBST(p)
        root.right = self.sortedListToBST(x.next)
        return root 
        
```

