![螢幕擷取畫面 2022-10-17 191709](https://user-images.githubusercontent.com/103319735/196163877-5c5f575a-4a67-4cd0-9805-72d5854bdbff.jpg)

# Method 1 (634 ms/13.7 MB)
```
class Solution(object):
    def maxNumberOfBalloons(self, text):
        """
        :type text: str
        :rtype: int
        """
        count = 0
        text = list(text)
        required = list('balloon')
        
        while True:
            for letter in required:
                try:
                    text.remove(letter)
                except ValueError:
                    return count

            count += 1
```

# Method 2 (15 ms/13.9 MB)

```
class Solution(object):
    def maxNumberOfBalloons(self, text):
        """
        :type text: str
        :rtype: int
        """
        count = {}
        required = set('balloon')
        
        for letter in text:
            if letter in required:
                try:
                    count[letter] += 1
                except KeyError:
                    count[letter] = 1

        if len(count) != len(required):
            return 0

        for i in ['l','o']:
            count[i] = count[i] // 2


        return count.get(min(count, key=count.get))
```
