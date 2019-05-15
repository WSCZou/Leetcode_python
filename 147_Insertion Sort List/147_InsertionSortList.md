题目:

对链表进行插入排序。

![Insertion_sort_example-300px.gif](https://github.com/WSCZou/Markdown-pic/blob/master/Leetcode_python/Insertion-sort-example-300px.gif?raw=true)

插入排序的动画演示如上。从第一个元素开始，该链表可以被认为已经部分排序（用黑色表示）。
每次迭代时，从输入数据中移除一个元素（用红色表示），并原地将其插入到已排好序的链表中。

 

**插入排序算法：**

1. 插入排序是迭代的，每次只移动一个元素，直到所有元素可以形成一个有序的输出列表。
2. 每次迭代中，插入排序只从输入数据中移除一个待排序的元素，找到它在序列中适当的位置，并将其插入。
3. 重复直到所有输入数据插入完为止。

 

**示例 1：**

```python
输入: 4->2->1->3
输出: 1->2->3->4
```

**示例 2：**

```python
输入: -1->5->3->4->0
输出: -1->0->3->4->5
```

Solution:

```python
class ListNode:
    def __init__(self,x):
        self.val = x
        self.next = None
        
class Solution:
    def insertionSorList(self,head: ListNode):
        dummy = ListNode(0)
        
        while head:
            p = dummy
            while p.next and p.next.val < head.val:
                p = p.next
            q = head 
            head = head.next #记录下一个要插入的数
            
            p.next , q.next = q ,p.next #q.next = p.next 是要断开插入的数的链表
        return dummy.next

```

