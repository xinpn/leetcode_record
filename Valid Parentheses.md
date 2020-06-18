#### [Valid Parentheses](https://leetcode-cn.com/problems/valid-parentheses/)

难度：简单

Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.



An input string is valid if:



1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.
   Note that an empty string is also considered valid.

Example 1:

Input: "()"
Output: true

Example 2:

Input: "()[]{}"

Output: true

Example 3:

Input: "(]"

Output: false

Example 4:

Input: "([)]"

Output: false

Example 5:

Input: "{[]}"

Output: true

- 利用栈完成。若遍历到的字符是左括号，进栈；若是右括号，与栈顶元素进行比较，若相同，栈顶元素出栈。不同，则括号不匹配，返回False。最需要注意的是，出栈时要判断此时栈是否为空。

  ```python
  class Solution(object):
      def isValid(self, s):
          """
          :type s: str
          :rtype: bool
          """
          dirct={'(': ')','{':'}','[':']'}
          l=[]
          for c in s:
              if c=='(' or c=='[' or c=='{':
                  l+=c
              else:
                  if not l:
                      return False
                  if l[-1]=='(' and c==')' or l[-1]=='{' and c=='}' or l[-1]=='[' and c==']':#此处判断用字典实现更方便
                      l=l[:-1]
                  else:
                      return False
          if not l:
              return True
          else:
              return False
  ```

  > 优化：可以利用字典存储左右括号

  ```python
  class Solution(object):
      def isValid(self, s):
          """
          :type s: str
          :rtype: bool
          """
          dirct={')':'(','}':'{',']':'['}
          l=[]
          for c in s:
              if l and c in dirct:
                  if dirct[c]==l[-1]:
                      l=l[:-1]
                  else:
                      return False
              else:
                  l+=c
          return not l#这一行代替也原来的倒数四行
  ```

  