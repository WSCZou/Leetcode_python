题目：

设计链表的实现。您可以选择使用单链表或双链表。单链表中的节点应该具有两个属性：`val` 和 `next`。`val` 是当前节点的值，`next` 是指向下一个节点的指针/引用。如果要使用双向链表，则还需要一个属性 `prev` 以指示链表中的上一个节点。假设链表中的所有节点都是 0-index 的。

在链表类中实现这些功能：

- get(index)：获取链表中第 `index` 个节点的值。如果索引无效，则返回`-1`。
- addAtHead(val)：在链表的第一个元素之前添加一个值为 `val` 的节点。插入后，新节点将成为链表的第一个节点。
- addAtTail(val)：将值为 `val` 的节点追加到链表的最后一个元素。
- addAtIndex(index,val)：在链表中的第 `index` 个节点之前添加值为 `val`  的节点。如果 `index` 等于链表的长度，则该节点将附加到链表的末尾。如果 `index` 大于链表长度，则不会插入节点。
- deleteAtIndex(index)：如果索引 `index` 有效，则删除链表中的第 `index` 个节点。

 

**示例：**

```
MyLinkedList linkedList = new MyLinkedList();
linkedList.addAtHead(1);
linkedList.addAtTail(3);
linkedList.addAtIndex(1,2);   //链表变为1-> 2-> 3
linkedList.get(1);            //返回2
linkedList.deleteAtIndex(1);  //现在链表是1-> 3
linkedList.get(1);            //返回3
```

solution:

```python
Class Node:
    def __init__(self,val , _next = None):
        self.val = val
        self.next = _next
Class MyLinkedList:
    def __init__(self):
        self.head = self.tail = None
        self.size = 0
        
    def getNode(self,index):
        n = Node(0,self.head)
        for i in range(index + 1):
            n = n.next
        return n
    
    def get(self, index):
        if index < 0 or index >= self.size: return -1
        return self.getNode(index).val
    
    def addAtHead(self,val):
        n = Node(val, self.head)
        self.head = n
        if self.size == 0:
            self.tail = n
        self.size += 1
        
    def addAtTail(self,val):
        n = Node(val)
        if self.size == 0:
            self.head = self.tail = n
        else:
            self.tail.next = n
            self.tail = n
        self.size += 1
        
  def addAtIndex(self, index, val):
    if index < 0 or index > self.size: return
    if index == 0: return self.addAtHead(val)
    if index == self.size: return self.addAtTail(val)
    prev = self.getNode(index - 1)
    n = Node(val, prev.next)
    prev.next = n
    self.size += 1
    
  def deleteAtIndex(self, index):
    if index < 0 or index >= self.size: return
    prev = self.getNode(index - 1)
    prev.next = prev.next.next
    if index == 0: self.head = prev.next
    if index == self.size - 1: self.tail = prev
    self.size -= 1
    
```



