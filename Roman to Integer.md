# [Roman to Integer](https://leetcode-cn.com/problems/roman-to-integer/)

难度：简单

Roman numerals are represented by seven different symbols: I, V, X, L, C, D and M.



Symbol       Value
I             1
V             5
X             10
L             50
C             100
D             500
M             1000



For example, two is written as II in Roman numeral, just two one's added together. Twelve is written as, XII, which is simply X + II. The number twenty seven is written as XXVII, which is XX + V + II.



Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not IIII. Instead, the number four is written as IV. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as IX. There are six instances where subtraction is used:



I can be placed before V (5) and X (10) to make 4 and 9. 
X can be placed before L (50) and C (100) to make 40 and 90. 
C can be placed before D (500) and M (1000) to make 400 and 900.
Given a roman numeral, convert it to an integer. Input is guaranteed to be within the range from 1 to 3999.

Example 1:

Input: "III"
Output: 3

Example 2:

Input: "IV"
Output: 4

Example 3:

Input: "IX"
Output: 9

Example 4:

Input: "LVIII"
Output: 58
Explanation: L = 50, V= 5, III = 3.

Example 5:

Input: "MCMXCIV"
Output: 1994
Explanation: M = 1000, CM = 900, XC = 90 and IV = 4.

- 构建一个字典，格式为 罗马数字：数字。依次遍历字符串中的元素，与后一个元素进行比较，若小于后一个元素，则减去此罗马数字对应的数字；若大于，则加上此数字。遍历时注意边界（最后一个数组不能在向后比较）。

  ```python
  class Solution(object):
      def romanToInt(self, s):
          """
          :type s: str
          :rtype: int
          """
          num=0
          seq={'I':1,'V':5,'X':10,'L':50,'C':100,'D':500,'M':1000}
          for i in range(len(s)):
              if i==len(s)-1:
                  num+=seq[s[i]]
                  break
              if seq[s[i]]<seq[s[i+1]]:
                  num-=seq[s[i]]
              else:
                  num+=seq[s[i]]
          return num
  ```

  

注意：

```python
if seq[s[i]]<seq[s[i+1]]:
                num-=seq[s[i]]
```

这里能否换成：

```
if seq[s[i]]<seq[s[i+1]]:
                num+=seq[s[i+1]]-seq[s[i]]
                i+=1
```

答案：不可以。这里体现了C语言for循环和pythonfor循环的区别。