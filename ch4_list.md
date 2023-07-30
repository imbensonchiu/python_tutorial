:::info
NTUIM Camp - Materials for Python - List
教材編寫者：台大資管三 黃芷榆
:::

> **Table of Contents**
[ToC]

* sort, len, append, reverse, sorted, pop, del, remove, in, count
    * extend
    * len
    * append
    * insert
    * split
    * del」、「remove()」、「pop()」和「clear()
    * 「offset」和「slice()」



---

## 簡介
**串列（list）**：串列將一連串同或是不同資料型別的字元放在一起的序列。

我們可以用中括號去創建串列，或是直接宣告 ```list()```： 
```python=
list_a = []
list_b = list()
```

#### 簡單舉例
```python=
# 範例 4-1
a = [1, 2, "hi", True]
print(a)
print(type(a))
```
印出的結果是
```
[1, 2, 'hi', True]
<class 'list'>
```
至於為甚麼我們會需要串列來儲存資料，而不要用不同變數來儲存呢？那是因為串列有一些很方便使用的性質，讓我們可以操作一組相關的資料。讓我們以一個情境來理解吧！

#### 小情境
今天有 30 個同班同學，他們的數學成績都被登記下來並儲存在一個串列中，我們想要計算這個班級的數學成績平均。
```python=
math_scores = [76, 51, 71, 69, 98, 62, 82, 
            87, 90, 62, 50, 85, 75, 63, 93, 
            92, 72, 73, 66, 100, 53, 83, 63, 
            95, 58, 97, 84, 91, 81, 88]

total = 0
for i in range(30):
    total += math_scores[i]

average = total / 30
print(average)
```
印出的結果是
```
77.0
```
我們就知道全班 30 人的平均成績。如此一來，我們可以用一個串列變數去儲存所有人的成績，再用一個迴圈就將成績加總，而不需要去尋找零散的各個變數，讓我們的程式架構更加系統化！


## 取出串列的方法
取出部分串列的方法主要遵循一個語法：
> [首：尾：間格數]

所以舉例來說如果我們要從第一個數開始到第十個每兩個取一個的時候，我們可以寫：
> [0：10：2]
### 從頭取
回歸到我們上面舉的例子，要取出在串列中每個學生的成績，我們可以用中括號來得到我們需要的值。這邊要注意的是，程式語言大多是從 0 開始計數，所以當我們要取串列中的第一個元素，要在中括號中放 0，第 5 個要放 4，並以此類推。
```python=
# 範例 4-3
math_scores = [76, 51, 71, 69, 98, 62, 82, 
            87, 90, 62, 50, 85, 75, 63, 93, 
            92, 72, 73, 66, 100, 53, 83, 63, 
            95, 58, 97, 84, 91, 81, 88]
            
# 第一個學生的成績
print(math_scores[0])

# 第五個學生的成績
print(math_scores[4])
```
印出的結果是
```
76
98
```
### 從尾取

那麼如果我們是想要拿到倒數第三個學生的成積呢？Python 有一個從尾開始計數的方式，只要加上一個負號即可，這邊要注意，從尾開始第一個數是 -1 喔。
```python=
# 範例 4-4

# 倒數第一個學生
print(math_scores[-1])

# 倒數第五個學生
print(math_scores[-5])
```
印出的結果是
```
88
97
```
### 取一個範圍
如果要取一個範圍的數字的範圍，我們可以在中括號的中間放「起點：終點」的語法來告訴 Python 我們要從哪裡開始取我們的字串，並在那裡結束。要注意的是，「起點」是被包括在我們的範圍中，而「終點」則是我們要的最後一個元素的下一個。
#### 簡單舉例
```python=
# 範例 4-5
# 第一個到第五個
print(math_scores[0:5])
# 第三個到倒數第三個
print(math_scores[2:-2])
```
```
[76, 51, 71, 69, 98]
[71, 69, 98, 62, 82, 87, 90, 62, 50, 85, 75, 63, 93, 92, 72, 73, 66, 100, 53, 83, 63, 95, 58, 97, 84, 91]
```
如果我們想要取某個指數後的全部字元，那麼我們可以直接在該指數後加上一個冒號，語法會是：[index:]
如果是要該指數之前的全部字元，冒號則是加在前後，語法會是：[:index]
#### 簡單舉例
```python=
# 第二十六個之後
print(math_scores[25:])
# 第十個之前
print(math_scores[:10])
```
這樣會印出
```
[97, 84, 91, 81, 88]
[76, 51, 71, 69, 98, 62, 82, 87, 90, 62]
```





## 串列的操作
### 型別轉換
如果我們將字串或是整數轉換成串列會發生甚麼事情呢？就讓我們來示範看看吧！
```python=
# 範例 4-2
a = "We are NTUIM!"
myList = list(a)

print(a)
print(myList)
```
印出的結果是
```
Hi, we are NTUIM!
['W', 'e', ' ', 'a', 'r', 'e', ' ', 'N', 'T', 'U', 'I', 'M', '!']
```
我們可以看到如果將字串型別轉換成串列，Python 會將字串中的每個字母、標點符號、空白鍵為單位，分別儲存成串列的字元。

但如果是放整數的話則會出現錯誤訊息
```python=
a = 12
myList = list(a)

print(a)
print(myList)
```
```
TypeError: 'int' object is not iterable
```
這表示整數是無法被型別轉換成串列。
### 合併

當我們想要將兩個串列合併，我們可以使用「＋」將它們合併
```python=
a = [1, 2, 3, 4]
b = [5, 6, 7, 8, 9, 10]

c = a + b
print(c)
```
印出的答案為
```
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```
### 複製
複製串列我們可以使用「[：]」的語法，這相當於將這個串列裡的資料全部複製一份新的給另一個串列變數，所以當更動原串列時，並不會更動到新的串列；這和直接使用「b = a」將兩個變數指向同一個串列有所不同，因為指向同一個串列，所以當用任何一個變數去做操作時，會同時更改到兩個串列。

那麼就讓我們用一個例子來了解吧！

1. 如果直接用 ```b=a```：
```python=
a = [1, 2, 3]
b = a
del(a[1])
print(a)  # [1, 3]
print(b)  # [1, 3]
```

2. 如果用複製的：
```python=
a = [1, 2, 3]
b = a[:]
del(a[1])
print(a)  # [1, 3]
print(b)  # [1, 2, 3]
```


## 串列中常見的函數
現在就讓我們來看看 Python 幫我們寫好用來操作串列的功能吧！在後面的章節會再詳細介紹函數的定義，現在我們可以把函數想成是這些小功能吧。

1. ```len```
首先，如果我們想要知道某個串列的函數，我們把我們的串列進```len```的括號中就可以辦到喔！

```python=
print(len(math_scores))
```

2. ```append``` append(list) vs extend(list) 

再來如果我們要增加元素到 list，則可以用 ```add()```，如果是增加一個 list 到另一個 list 的話，則可以用 ```extend()```。

```python=
my_list = [1, 2, 3]
my_list.add(4)

other_list = [10, 9, 8]
my_list.extend(other_list)
```
3. ```insert``` insert(index, element)

再來我們將某值加到我們想要的位置，則可以用 insert：

```python=
my_list = ['good evening', 'good afternoon', 'good morning', 'good night']
my_list.insert(2, 'hello')
```
4. ```pop``` pop(index)

我們也可以幫不要的元素用 ```pop``` 刪除，會回傳被 pop 的值且預設是刪除最後一個元素。
```python=
my_list = [2, 3, 4, 5, 6]
my_list.pop(4)
```

5. ```del``` erase by index, del a_list[9]

我們也可以用 index 來刪除元素
```python=
my_list = [1, 2, 3, 4, 5]
del my_list[0]
```
8. ```remove``` erase by element, remove(element)

用值來刪除出現的第一個元素：
```python=
my_list = [1, 2, 3, 4, 5]
my_list.remove(3)
```
 9. ```split```
用於將一個字串依照其 delimeter 去做切割

10. join

```python=
my_list = ["2024", "01", "01"]
my_list = '-'.join(my_list)
my_list
```
```
'2024-01-01'
```
11. count

去計算每一個 list 裡某個值總共出現幾次

```python=

happy_list = ['h', 'a', 'p', 'p', 'y']

print(happy_list.count('p')) # 2
print(happy_list.count('b')) # 0
```

12. sort

將 list 依照某個順序去做排列。其中 ```sort``` 有許多參數可以去做調整。

首先是 reverse，sort 的預設值是升冪排列，如果我們想要數列以降冪排列，我們則可以把 reverse 設為 True。

```python=
list.sort(cmp=None, key=None, reverse=False)
```
```python=
my_list = [3, 7, 2, 6, 1]
my_list.sort()
my_list # [1, 2, 3, 6, 7]

my_list.sort(reverse = True)
my_list # [7, 6, 3, 2, 1]
```

sort()




13. ```in```
14. ```split```
15. ```count``` count(element)
16. ```sort``` list.sort() vs sorted(list)
17. ```reverse``` list.reverse(), list.sort(reverse = True)
18. ```join```串聯
<sep>.join(<list>)：用 sep 來串連列表元素，列表元素需皆為字串。




sort, len, append, reverse, sorted, pop, del, remove, in, count

### References
* [串列list型態-Python](https://nkust.gitbook.io/python/untitled)
* [STEAM 教育學習網](https://steam.oxxostudio.tw/category/python/basic/list.html)
