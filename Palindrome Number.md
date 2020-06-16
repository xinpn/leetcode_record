# [Palindrome Number](https://leetcode-cn.com/problems/palindrome-number/)

难度：简单

Determine whether an integer is a palindrome. An integer is a palindrome when it reads the same backward as forward.

Example 1:

Input: 121
Output: true 

Example 2:

Input: -121
Output: false

Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.

Example 3:

Input: 10
Output: false
Explanation: Reads 01 from right to left. Therefore it is not a palindrome.
Follow up:

Coud you solve it without converting the integer to a string?

- 转换成字符串，利用切片将字符串反转，在转换成数字，与原数字进行比较即可。

```python
class Solution(object):
    def isPalindrome(self, x):
        """
        :type x: int
        :rtype: bool
        """
        str_x=str(x)
        str_x=str_x[::-1]
        if x<0:
            return False
        else:
            temp=int(str_x)
            if x==temp:
                return True
            else:
                return False
```

- 获取原数字的后半部分。reverse_num即原数字的后半部分，循环时将x除以10，reverse_num=reverse_num*10+x%10。当reverse_num大于等于x时，reverse_num就获取了后半部分。x位数是偶数，reverse_num=x;x位数是奇数，reverse_num比此时的x多一位，要除以10，再进行比较。

```python
class Solution(object):
    def isPalindrome(self, x):
        """
        :type x: int
        :rtype: bool
        """
        if x<0 or x%10==0 and x!=0:
            return False
        reverse_num=0
        while reverse_num<x:
            reverse_num=reverse_num*10+x%10
            x/=10
        if x==reverse_num or x==reverse_num/10:
            return True
        else:
            return False
```

