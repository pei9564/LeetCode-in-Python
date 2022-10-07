Qus

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
