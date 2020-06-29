#### [Same Tree](https://leetcode-cn.com/problems/same-tree/)

难度：简单

Given two binary trees, write a function to check if they are the same or not.



Two binary trees are considered the same if they are structurally identical and the nodes have the same value.



![image-20200629215601843](C:\Users\xin\AppData\Roaming\Typora\typora-user-images\image-20200629215601843.png)

![image-20200629215629393](C:\Users\xin\AppData\Roaming\Typora\typora-user-images\image-20200629215629393.png)

- 递归。首先判断p,q的节点是否为空，若都为空，则返回True；若一个为空，一个非空，则返回False。然后判断两个节点的值是否相同，若相同，递归的判断子节点的情况。

  ```python
  # Definition for a binary tree node.
  # class TreeNode(object):
  #     def __init__(self, x):
  #         self.val = x
  #         self.left = None
  #         self.right = None
  
  class Solution(object):
      def isSameTree(self, p, q):
          """
          :type p: TreeNode
          :type q: TreeNode
          :rtype: bool
          """
          if not p and not q:
              return True
          if not p or not q:
              return False
          if p.val!=q.val:
              return False
          return self.isSameTree(p.left,q.left) and
      self.isSameTree(p.right,q.right)
  ```

- 迭代。类似于树的层次遍历法。deque是双向队列

  ```python
  # Definition for a binary tree node.
  # class TreeNode(object):
  #     def __init__(self, x):
  #         self.val = x
  #         self.left = None
  #         self.right = None
  
  class Solution(object):
      def isSameTree(self, p, q):
          """
          :type p: TreeNode
          :type q: TreeNode
          :rtype: bool
          """
          def check(p,q):
              if not p and not q:
                  return True
              if not p or not q:
                  return False
              if p.val!=q.val:
                  return False
              return True
          deq=deque([(p,q)])
          while deq:
              p,q=deq.popleft()
              if not check(p,q):
                  return False
              if p:
                  deq.appendleft((p.left,q.left))
                  deq.appendleft((p.right,q.right))
          return True
  ```

  

