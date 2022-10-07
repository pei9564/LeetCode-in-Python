![Quest](https://user-images.githubusercontent.com/103319735/194475683-ff063486-7e1d-41ef-ae46-83496f745c54.jpg)
# Method 1 (122ms/13.7MB)
```
class Solution(object):

    def isPalindrome(self, x):
    
        x = str(x)
        for i in range(-(len(x) // -2)):
            if x[i] != x[-i-1]:
                return False
        return True
```


1. 使用`-(len(x) // -2)`取得ceiling-division，未加負號為floor-division
    * 5 // 2 = 2.5 => 2
    * 5 // -2 = -2.5 => -3


# Method 2 (110ms/13.2MB)
```
class Solution(object):

    def isPalindrome(self, x):
    
        x = str(x)
        return x[::-1] == x
``` 


# Method 3 (103ms/13.3MB)

```
class Solution(object):

    def isPalindrome(self, x):
    
        result = 0
        a = abs(x)

        while a != 0:
            temp = a % 10
            result = result * 10 + temp
            a = int(a/10)
        
        return result == x
```
1. 依據提示，不將input轉為string以減少空間使用率，實測後發現其實和方法2的結果相差不大
