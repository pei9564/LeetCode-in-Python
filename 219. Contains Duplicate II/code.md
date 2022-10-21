![螢幕擷取畫面 2022-10-21 222803](https://user-images.githubusercontent.com/103319735/197219964-ecfa067d-39a5-472c-a995-67488c5a3546.jpg)

# Method 1 (1114 ms / 32.4 MB)

```
class Solution(object):
    def containsNearbyDuplicate(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: bool
        """

        count = {}

        for i in range(len(nums)):
            if nums[i] not in count:
                count[nums[i]] = [i]
            else:
                for j in count[nums[i]]:
                    if abs(j - i) <= k:
                        return True
                count[nums[i]] += [i]
        return False
```
