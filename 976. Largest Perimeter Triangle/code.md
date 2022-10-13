![螢幕擷取畫面 2022-10-13 095128](https://user-images.githubusercontent.com/103319735/195480262-49199469-0ea2-49e4-8144-504b6afd6b34.jpg)

三角形邊長關係：三角形任意兩邊的和大於第三邊，任意兩邊的差小於第三邊。

# Failed 1 (Time Limit Exceeded)
```
class Solution(object):
    def largestPerimeter(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        nums = sorted(nums, reverse=True)

        for i in range(len(nums) - 2):
            for j in range(i + 1, len(nums) - 1):
                for k in range(j + 1, len(nums)):
                    if nums[k] + nums[j] > nums[i] and nums[i] - nums[k] < nums[j]:
                        return nums[i] + nums[j] + nums[k]
        
        return 0
```
* 另i, j, k為三角形三邊長，且i > j > k
* 第一次測試時試圖排列出所有i * j * k的排列組合

# Method 1 (329 ms/14.8 MB)
```
class Solution(object):

    def largestPerimeter(self, nums):

        nums = sorted(nums, reverse=True)

        for i in range(len(nums) - 2):
            if nums[i+1] + nums[i+2] <= nums[i]:
                pass
            else:
                for j in range(i + 1, len(nums) - 1):
                    for k in range(j + 1, len(nums)):
                        if nums[i] - nums[k] < nums[j]:
                            return nums[i] + nums[j] + nums[k]
        
        return 0
```
* 增加條件: 若最大的j + k 仍小於 i，則可pass尋找下一個 i

# Method 2 (350 ms/14.8 MB)
```
class Solution(object):

    def largestPerimeter(self, nums):
    
        nums = sorted(nums, reverse=True)

        for i in range(len(nums) - 2):
            if nums[i+1] + nums[i+2] > nums[i]:
                return nums[i] + nums[i+1] + nums[i+2]
        
        return 0
```

* 因數值排序過，故考慮第一個條件即可
* 如：令有一邊長為[1, 10, 10] 
* 若1 + 10 > 10，則 10 - 1 必 < 10
