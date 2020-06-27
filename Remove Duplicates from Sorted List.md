#### [Remove Duplicates from Sorted List](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-list/)

难度：简单

Given a sorted linked list, delete all duplicates such that each element appear only once.



Example 1:

Input: 1->1->2
Output: 1->2

Example 2:

Input: 1->1->2->3->3
Output: 1->2->3

- 设置一个前指针，后指针。如果后面元素重复，则前指针指向后指针的下一个元素。

  ```python
  # Definition for singly-linked list.
  # class ListNode(object):
  #     def __init__(self, x):
  #         self.val = x
  #         self.next = None
  
  class Solution(object):
      def deleteDuplicates(self, head):
          """
          :type head: ListNode
          :rtype: ListNode
          """
          if not head:
              return head
          l=head
          r=head.next
          temp=head.val
          while r!=None:
              if r.val==temp:
                  l.next=r.next
                  r=r.next
              else:
                  temp=r.val
                  l=r
                  r=r.next
          return head
  ```

  