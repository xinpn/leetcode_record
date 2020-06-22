# [Length of Last Word](https://leetcode-cn.com/problems/length-of-last-word/)

难度：简单

Given a string s consists of upper/lower-case alphabets and empty space characters ' ', return the length of last word (last word means the last appearing word if we loop from left to right) in the string.



If the last word does not exist, return 0.



Note: A word is defined as a maximal substring consisting of non-space characters only.



Example:



Input: "Hello World"
Output: 5

- 从前向后遍历字符串，遇到空格长度置0，非空格长度加一。存在字符串后面是空格的情况，按照之前逻辑，长度会置0，且返回0，不是最后一个单词的长度，所以设置一个lastlength,保存之前长度，若最后是空格则返回lastlength.

  ```python
  class Solution(object):
      def lengthOfLastWord(self, s):
          """
          :type s: str
          :rtype: int
          """
          length=0
          lastlength=0
          for st in s:
              if st==" ":
                  if length!=0:
                      lastlength=length
                  length=0
              else:
                  length+=1
          return length if s and length!=0 else lastlength
  ```

- 题目要求最后一个单词长度，可以直接从后向前遍历。

  ```python
  class Solution(object):
      def lengthOfLastWord(self, s):
          """
          :type s: str
          :rtype: int
          """
          length=0
          for i in range(len(s)-1,-1,-1):
              if s[i]==" ":
                  if length!=0:
                      return length
                  length=0
              else:
                  length+=1
          return length
  ```

  