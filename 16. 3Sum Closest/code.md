![擷取](https://user-images.githubusercontent.com/103319735/194713479-fc934f00-9c96-4f45-a733-d371e79c5f62.PNG)

# Failed 1 (Time Limit Exceeded)

```
class Solution(object):

def threeSumClosest(self, nums, target):

        result = {}

        for i in range(0, len(nums)-2):
            for j in range(i+1, len(nums)-1):
                for k in range(j+1, len(nums)):
                    result[target - (nums[i]+nums[j]+nums[k])] = nums[i]+nums[j]+nums[k]

        dif = 0
        closest = False
        while not closest:
            if dif in result:
                return result[dif]
            elif -dif in result:
                return result[-dif]
            else:
                dif += 1
```

* 第一次嘗試的時候用暴力解法，嘗試把所有可能性加總再判斷最接近值
* 時間複雜度推估應該是O(N^3)，導致過時失敗

# Method 1 (3573ms/13.7MB)

```
class Solution(object):
    
    def threeSumClosest(self, nums, target):
        
        result = {}
        nums = sorted(nums)            

        for i in range(len(nums) - 2):
            l = i + 1
            r = len(nums) - 1

            while l < r and l != r:
                if nums[i] + nums[l] + nums[r] == target:
                    return target
                elif r - l == 1:
                    break
                elif nums[i] + nums[l] + nums[r] > target:
                    r -= 1
                else:
                    l += 1
            
            diff = abs((nums[i] + nums[l] + nums[r]) - target)
            result[diff] = nums[i] + nums[l] + nums[r]

        return result[min(result)]
```

1. 經過提點之後修改語法
2. 先進行排序，之後取i,l,r三個位置的數字，i從第`0`位開始，l從`i+1`位，r從最後一位`(len(nums)-1)`
3. 若是加總數字>target，r往前抓(加總減少)，反之l往後找(加總增加)
4. 注意：若三位數加總剛好等於target，直接return，若已經推到r和l是相鄰兩位，則退出while迴圈，不更改r&l
5. 一般情況下應該不會剛好等於target，於是儲存到dictionary中，`key = sum-target的絕對值`，`value=sum`
6. 最後return最小相差值的value
