#### [Climbing Stairs](https://leetcode-cn.com/problems/climbing-stairs/)

难度：简单

You are climbing a stair case. It takes n steps to reach to the top.



Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?



Example 1:

Input: 2
Output: 2
Explanation: There are two ways to climb to the top.



1. 1 step + 1 step

2. 2 steps

  Example 2:

Input: 3
Output: 3
Explanation: There are three ways to climb to the top.

1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step


Constraints:

1 <= n <= 45

- 递归

  ```python
  class Solution(object):
      def climbStairs(self, n):
          """
          :type n: int
          :rtype: int
          """
          if n==1:
              return 1
          elif n==2:
              return 2
          return climbStairs(n-1)+climbStairs(n-2)
  ```

  > 注：这个方法提交时时间超限，但这个是最容易想到的方法

- 用一个字典来存储前n个跳台阶的方法。空间复杂度为O(n)

  ```python
  class Solution(object):
      def climbStairs(self, n):
          """
          :type n: int
          :rtype: int
          """
          if n==1:
              return 1
          elif n==2:
              return 2
          l={}
          l[1]=1
          l[2]=2
          for i in range(3,n+1):
              l[i]=l[i-1]+l[i-2]
          return l[n]
  ```

  > 注：为什么使用字典来存储而不是列表，因为字典可以通过l[i]=n的形式来自动增加元素比较较方便。

- 使用两个临时变量来存储n之前跳台阶的方法数。空间复杂度为O(1)

  ```python
  class Solution(object):
      def climbStairs(self, n):
          """
          :type n: int
          :rtype: int
          """
          if n==1:
              return 1
          elif n==2:
              return 2
          x,y,an=1,2,0
          for i in range(3,n+1):
              an=x+y
              x=y
              y=an
          return an
  ```

  