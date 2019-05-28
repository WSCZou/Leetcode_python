题目

给定一个头结点为 `root` 的链表, 编写一个函数以将链表分隔为 `k` 个连续的部分。

每部分的长度应该尽可能的相等: 任意两部分的长度差距不能超过 1，也就是说可能有些部分为 null。

这k个部分应该按照在链表中出现的顺序进行输出，并且排在前面的部分的长度应该大于或等于后面的长度。

返回一个符合上述规则的链表的列表。

举例： 1->2->3->4, k = 5 // 5 结果 [ [1], [2], [3], [4], null ]

**示例 1：**

```
输入: 
root = [1, 2, 3], k = 5
输出: [[1],[2],[3],[],[]]
解释:
输入输出各部分都应该是链表，而不是数组。
例如, 输入的结点 root 的 val= 1, root.next.val = 2, \root.next.next.val = 3, 且 root.next.next.next = null。
第一个输出 output[0] 是 output[0].val = 1, output[0].next = null。
最后一个元素 output[4] 为 null, 它代表了最后一个部分为空链表。
```

**示例 2：**

```
输入: 
root = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10], k = 3
输出: [[1, 2, 3, 4], [5, 6, 7], [8, 9, 10]]
解释:
输入被分成了几个连续的部分，并且每部分的长度相差不超过1.前面部分的长度大于等于后面部分的长度。
```

Solution:

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def splitListToParts(self, root: ListNode, k: int) -> List[ListNode]:
        len = 0
        p = root
        while p:
            len += 1
            p = p.next
            
        l = len // k
        r = len % k
        
        
        pre = None
        
        res = []
        for i in range(r):## 前count%k个需要多出一个结点的链表
            head = root
            for j in range(l):
                head = head.next
            res.append(root)
            head.next,root = None,head.next
            
        if not root:# 如果已不剩结点，直接用空链表补满列表返回
            res.extend([None]*(k - len % k))
            return res
        for i in range(k - len % k -1):# 否则循环补满剩下的k-count%k-1个
            head = root
            for j in range(l - 1):
                head = head.next
            res.append(root)
            head.next,root = None,head.next
        res.append(root)
        return res
            
            
```

