![螢幕擷取畫面 2022-10-07 113231](https://user-images.githubusercontent.com/103319735/194462258-82013ab4-5b93-473c-aca5-5754e1edff5f.jpg)

# Method 1 (2422ms/14.5MB)

```
class Solution(object):

def twoSum(self, nums, target):

        for i in range(len(nums)):
            for j in range(i+1, len(nums)):
                if (nums[i]+nums[j]) == target:
                    return [i, j]
```

1. 從第一個數字開始檢視，一一比對和後面數字的加總是否等於target
2. 若是則return兩數字之index

# Method 2 (86ms/14.2MB)

```
class Solution(object):

    def twoSum(self, nums, target):

        preMap = {}
        for i, value in enumerate(nums):
            if (target - value) in preMap:
                return [preMap[(target - value)], i]
            preMap[value] = i 
```

1. 新增一個空的HashMap(dictionary in Python)
2. 使用`enumerate()`依序取出array中的 `index` & `value`
    * 如array = [2, 3, 7] 則會取出(0, 2), (1, 3), (2, 7)
4. 從第一個數字開始檢視，Map中是否有該value與target之差
    * 如target=9，在檢視2時，尋找是否有9-2=7的存在
5. 若無則將檢視完畢的數字以`{value:index}`方式存入Map中
6. 若尋找成功，則取出檢視數值之index及Map中存入數值之index
