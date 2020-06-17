#### [Longest Common Prefix](https://leetcode-cn.com/problems/longest-common-prefix/)

难度：简单

Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".

Example 1:

Input: ["flower","flow","flight"]
Output: "fl"

Example 2:

Input: ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.
Note:

All given inputs are in lowercase letters a-z.

- 求一个字符数组的最大公共前缀，可以先求前两个字符串公共前缀，得到之后，求此时最大公共前缀与第三个字符串的最大公共前缀，知道最大公共前缀为空或数组中所有的字符串都遍历完。

  ```python
  class Solution(object):
      def longestCommonPrefix(self, strs):
          """
          :type strs: List[str]
          :rtype: str
          """
          if not strs:
              return ""
          s=strs[0]
          for s_r in strs:
              i=0
              while i<len(s) and i<len(s_r):
                  if s[i]!=s_r[i]:
                      break
                  i+=1
              s=s[:i:1]
              if s=="":
                  return s
          return s
  ```

- 可以每次遍历字符串数组，从字符串的第一个字符开始比较，若字符串的第一个字符都相等，更新最大公共前缀，若有不相同字符，则此时的最大公共前缀即为最终结果。

  ```python
  class Solution(object):
      def longestCommonPrefix(self, strs):
          """
          :type strs: List[str]
          :rtype: str
          """
          if not strs:
              return ""
          s,i="",0
          while i< len(strs[0]):
              for s_r in strs:
                  ch=strs[0][i]
                  if len(s_r)==i or s_r[i]!=ch:
                      return s
              s=s+strs[0][i]
              i+=1
          return s 
  ```

  

