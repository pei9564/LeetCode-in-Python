![螢幕擷取畫面 2022-11-19 205704](https://user-images.githubusercontent.com/103319735/202855467-5d03f70a-bccb-4d69-89cc-3018a2efea3a.jpg)

# Method 1 (1194 ms / 14.6 MB)

```
class Solution(object):
    def moveZeroes(self, nums):
    
        zero = 0

        while 0 in nums:
            nums.remove(0)
            zero += 1

        for i in range(zero):
            nums.append(0)
```
因為每一次都要確認0是否存在list當中，時間複雜度較差

# Method 2 (265 ms / 14.8 MB)
```
class Solution(object):
    def moveZeroes(self, nums):
    
        zero = 0
        tmp = []
        for i in nums:
            if i != 0:
                tmp.append(i)
            else:
                zero += 1 

        for i in range(zero):
            tmp.append(0)

        nums[:] = tmp
```
以 nums[:] = tmp來取代原本nums list內的數字

# Method 3 (127 ms / 14.8 MB)
```
class Solution(object):
    def moveZeroes(self, nums):

        check_index = 0
        for i in range(len(nums)):
            if nums[i] != 0:
                nums[check_index] = nums[i]
                check_index += 1
                
        rest = len(nums) - check_index
        for i in range(1, rest + 1):

            nums[-i] = 0
```

時間複雜度與空間複雜度皆與上題差不多，但較符合題目要求
