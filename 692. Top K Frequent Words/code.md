![螢幕擷取畫面 2022-10-19 213144](https://user-images.githubusercontent.com/103319735/196705586-b5e80614-9127-48b1-8fe0-57d11780fda0.jpg)

# Method 1 (87 ms / 13.4 MB)

```
class Solution(object):
    def topKFrequent(self, words, k):
        """
        :type words: List[str]
        :type k: int
        :rtype: List[str]
        """
        frequent = {}
        result = []

        # Save the word in dictionary with frequent
        for word in words:
            if word not in frequent:
                frequent[word] = 1
            else:
                frequent[word] += 1

        # Save the frequentest word in the list with sorted by ascii 
        for i in range(k):
            frequentest = max(frequent, key=frequent.get)
            equal = sorted([i for i in frequent if frequent[i] == frequent[frequentest]])
            
            result.append(equal[0])
            frequent.pop(equal[0])
            
        return result
```
