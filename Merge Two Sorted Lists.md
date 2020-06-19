# [Merge Two Sorted Lists](https://leetcode-cn.com/problems/merge-two-sorted-lists/)

难度：简单

Merge two sorted linked lists and return it as a new sorted list. The new list should be made by splicing together the nodes of the first two lists.



Example:



Input: 1->2->4, 1->3->4
Output: 1->1->2->3->4->4

- 遍历两个链表，把值较小的节点加入到新链表中，比如说l1的节点较小，把l1的这个节点加入到新链表中，然后l1指向l1的下一个节点，直到l1或者l2的节点都加入到新链表中。然后把l1或者l2的剩余节点加入新链表。

  ```python
  # Definition for singly-linked list.
  # class ListNode(object):
  #     def __init__(self, val=0, next=None):
  #         self.val = val
  #         self.next = next
  class Solution(object):
      def mergeTwoLists(self, l1, l2):
          """
          :type l1: ListNode
          :type l2: ListNode
          :rtype: ListNode
          """
          prehead=ListNode(-1)
          prev=prehead
          while l1 and l2:
              if l2.val<l1.val:
                  prev.next=l2
                  l2=l2.next
              else:
                  prev.next=l1
                  l1=l1.next
              prev=prev.next
          if l1:
              prev.next=l1
          if l2:
              prev.next=l2
          return prehead.next
  ```

  上面代码的后半部分可以优化一下。

  ```python
  if l1:
  	prev.next=l1
  if l2:
      prev.next=l2
  #此处可以用一行代码代替
  prev.next= l1 if l1 is not None else l2
  #这样更加精炼
  ```

- 递归的方法。新链表是总是从未被合并的两个列表中选择最小的节点加入。如果 l1 或者 l2 一开始就是空链表 ，那么没有任何操作需要合并，所以我们只需要返回非空链表。否则，我们要判断 l1 和 l2 哪一个链表的头节点的值更小，然后递归地决定下一个添加到结果里的节点。如果两个链表有一个为空，递归结束。

  ```python
  # Definition for singly-linked list.
  # class ListNode(object):
  #     def __init__(self, val=0, next=None):
  #         self.val = val
  #         self.next = next
  class Solution(object):
      def mergeTwoLists(self, l1, l2):
          """
          :type l1: ListNode
          :type l2: ListNode
          :rtype: ListNode
          """
          if l1 is None:
              return l2
          elif l2 is None:
              return l1
          elif l1.val<=l2.val:
              l1.next=self.mergeTwoLists(l1.next,l2)
              return l1
          else:
              l2.next=self.mergeTwoLists(l1,l2.next)
              return l2
  ```

  [参考]: https://leetcode-cn.com/problems/merge-two-sorted-lists/solution/he-bing-liang-ge-you-xu-lian-biao-by-leetcode-solu

  

  