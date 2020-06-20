#### [Remove Duplicates from Sorted Array](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-array/)

难度：简单

Given a sorted array nums, remove the duplicates in-place such that each element appear only once and return the new length.



Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.



Example 1:

Given nums = [1,1,2],



Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively.



It doesn't matter what you leave beyond the returned length.

Example 2:

Given nums = [0,0,1,1,1,2,2,3,3,4],



Your function should return length = 5, with the first five elements of nums being modified to 0, 1, 2, 3, and 4 respectively.



It doesn't matter what values are set beyond the returned length.

- 设置一个临时变量来存储上一个数字的值。遍历数组，若此时的数字与上一个数字相同，则将数字删除；若不同，则修改temp的值，向后遍历。

  ```python
  class Solution(object):
      def removeDuplicates(self, nums):
          """
          :type nums: List[int]
          :rtype: int
          """
          if not nums:
              return 0
          temp=nums[0]
          i=1
          while i < len(nums):
              if nums[i]==temp:
                  nums[:]=nums[:i]+nums[i+1:]
              else:
                  temp=nums[i]
                  i+=1
          return len(nums)
  ```

- 双指针法。快指针遇到相同的数字时，指针加一；遇到不同的数字是把数字放到前面。

  ```python
  class Solution(object):
      def removeDuplicates(self, nums):
          """
          :type nums: List[int]
          :rtype: int
          """
          if not nums:
              return 0
          i=0
          for j in range(1,len(nums)):
              if nums[i]!=nums[j]:
                  i+=1
                  nums[i]=nums[j]
          return i+1
  ```

  