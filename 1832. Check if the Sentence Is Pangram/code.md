![螢幕擷取畫面 2022-10-17 183716](https://user-images.githubusercontent.com/103319735/196156998-6b0bfc52-e2f2-4aca-9889-694754f17f8d.jpg)

# Method 1 (40 ms/13.5 MB)
```
import string

class Solution(object):
    def checkIfPangram(self, sentence):
        """
        :type sentence: str
        :rtype: bool
        """
        alphabets = list(string.ascii_lowercase)
        
        for alphabet in sentence:
            try:
                alphabets.remove(alphabet)
            except ValueError:
                pass

        return alphabets == []
```
