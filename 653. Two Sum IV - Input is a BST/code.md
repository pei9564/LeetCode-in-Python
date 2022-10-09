![098](https://user-images.githubusercontent.com/103319735/194760058-3b8c6247-976a-44ec-a52b-81119f6c3c55.PNG)

# Method 1 (140ms/17.2MB)
```
class Solution(object):
    def findTarget(self, root, k):

        # 01. 建立一個dictionary儲存滿足條件的值(value和k的差)
        diff_required = {}

        # 02. 儲存root在list中
        que = [root]

        while que:

            # 03. 丟掉que中的第一個值且儲存在tmp供後續檢視使用
            tmp = que.pop(0)

            # 04. 如果檢視的值(tmp)是正在尋找的，即return True
            if tmp.val in diff_required:
                return True
            # 05. 若否則存入dict中，宣告其需求(可以配對成k的差)
            else:
                diff_required[k - tmp.val] = tmp.val

            # 06. 結束前同時存入left&right children預備檢視
            if tmp.left:
                que.append(tmp.left)
            if tmp.right:
                que.append(tmp.right)
                
        # 07. 若全部檢視完皆無值滿足條件，即return False
        return False
```

* 其實不大會寫binary tree結構的題目，今天是在教學下完成的，紀錄幾個重點
  1. `list.pop(i)`可以移除`list[i]`(以下小範例)
  2. `parent.left`&`parent.right`的用法
  3. binary search的方法：廣度搜尋vs.深度搜尋

```
test = [1, 2, 3, 4, 5]
test_tmp = test.pop(2)
print(test_tmp)
print(test)
'''
3
[1, 2, 4, 5]
'''
```
