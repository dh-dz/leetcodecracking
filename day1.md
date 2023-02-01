Array: continuous memory, when deleting items, need to change the address of other items

Binary search:
to avoid overflow:

```
middle = left + (right - left) / 2
```

implementations in Python3:
time exceeds:

```
class Solution(object):
    def search(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        l = len(nums)
        left = 0
        right = l-1
        index = -1
        while left < right:
            middle = int(left + (right - left) / 2)
            if nums[middle] < target:
                left = middle
            elif nums[middle] > target:
                right = middle
            elif nums[middle] == target:
                left = right
                index = middle
        return index
```
there were a lot of problems: boundary index issues, the positons of returns...

revised: middle +1, -1 super important when choosing to do in a closed range
```
class Solution(object):
    def search(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        left, right = 0, len(nums) - 1
        while left <= right:
            middle = left + (right - left) // 2
            if nums[middle] < target:
                left = middle + 1
            elif nums[middle] > target:
                right = middle - 1
            else:
                return middle
        return -1   
```

implementations in C++:

```

```

Remove elements:
fast/slow pointer

implementations in Python3:

```
class Solution(object):
    def removeElement(self, nums, val):
        """
        :type nums: List[int]
        :type val: int
        :rtype: int
        """
        # fast pointer: indf
        # slow pointer: inds
        inds = 0
        for indf in range(len(nums)):
            if nums[indf] != val:
                nums[inds] = nums[indf]
                inds += 1
        return inds
```

implementations in C++:

```

```

Leetcode Reference:

[LC704](https://leetcode.com/problems/binary-search/)
