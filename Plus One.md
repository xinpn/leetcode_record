#### [Plus One](https://leetcode-cn.com/problems/plus-one/)

难度：简单

Given a non-empty array of digits representing a non-negative integer, plus one to the integer.



The digits are stored such that the most significant digit is at the head of the list, and each element in the array contain a single digit.



You may assume the integer does not contain any leading zero, except the number 0 itself.



Example 1:

Input: [1,2,3]
Output: [1,2,4]
Explanation: The array represents the integer 123.

Example 2:

Input: [4,3,2,1]
Output: [4,3,2,2]
Explanation: The array represents the integer 4321.

- 要注意是否进位

  ```python
  class Solution(object):
      def plusOne(self, digits):
          """
          :type digits: List[int]
          :rtype: List[int]
          """
          l=1
          for i in range(len(digits)-1,-1,-1):
              digits[i]+=l
              if digits[i]>9:
                  digits[i]=0
                  if i==0:
                      digits.insert(0,1)
                  l=1
              else:
                  break
          return digits
  ```

  