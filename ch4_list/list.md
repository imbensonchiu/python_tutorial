:::info
NTUIM Camp - Materials for Python - List
教材編寫者：台大資管三 黃芷榆
:::

> **Table of Contents**
[ToC]



---

## 簡介
**串列（list）**：串列是將一連串**同或是不同資料型別**的單位放在一起的**序列**。我們可以將它想成一個**裝著很多不同單位**（可能是**整數、字母、字串、布林值**或甚至**另一個串列**等等）的**容器**。

接著讓我們來看看該如何使用串列吧！

### 建立串列
我們可以用中括號 [ ] 去創建串列，或是直接宣告 ```list()```： 
```python=
list_a = []
list_b = list()
```
此外，我們可以在**中括號裡**放入我們想要取出的**元素的索引值**；這邊要注意的是，程式語言大多是**從 0 開始計數**，所以當我們要取串列中的第 1 個元素，要在中括號中要放索引值 0，要取第 5 個元素時要放索引值為 4，並以此類推。
#### 簡單舉例
```python=
# 範例 4-1
a = [1, 2, "hi", True]
print(a) # [1, 2, 'hi', True]
print(type(a)) # <class 'list'>
print(a[2]) # hi   （取出索引值為 2 的元素「hi」）
```

至於為甚麼我們會需要串列來儲存資料，而不要用不同變數來儲存呢？那是因為串列有一些很方便使用的性質，讓我們可以同時操作一組相關的資料。我們以一個情境來理解吧！

#### 小情境
> 今天有 30 個同班同學，他們的數學成績登記下來後儲存在一個串列中，我們想要計算這個班級的數學成績平均。

以 ```math_scores``` 為儲存成績的串列變數，我們取出這個串列的所有元素並相加，再除以全班人數以得到我們的答案。
```python=
math_scores = [76, 51, 71, 69, 98, 62, 82, 
            87, 90, 62, 50, 85, 75, 63, 93, 
            92, 72, 73, 66, 100, 53, 83, 63, 
            95, 58, 97, 84, 91, 81, 88]

total = 0
for i in range(30):
    total += math_scores[i]

average = total / 30
print(average) # 77.0
```
印出的結果是 77.0 便是全班的數學平均成績。

由此可見，我們可以用**一個串列變數**去儲存所有人的成績，再用一個迴圈就將成績加總，而**不需要去尋找零散的各個變數**，讓我們的**程式架構更加系統化**！


## 取出串列的方法
取出部分串列的方法主要遵循一個語法：
> [首：尾：間格數]

舉例來說如果我們要從第一個數開始到第十個每兩個取一個的時候，我們可以這樣寫：
> [0：10：2]
### 從頭取
回歸到我們上面舉的例子，要取出在串列中每個學生的成績，我們可以用中括號來得到我們需要的值：
```python=
# 範例 4-3
math_scores = [76, 51, 71, 69, 98, 62, 82, 
            87, 90, 62, 50, 85, 75, 63, 93, 
            92, 72, 73, 66, 100, 53, 83, 63, 
            95, 58, 97, 84, 91, 81, 88]
            
# 第一個學生的成績
print(math_scores[0]) # 76

# 第五個學生的成績
print(math_scores[4]) # 98
```

### 從尾取

那麼如果我們是想要拿到倒數第三個學生的成積呢？Python 有一個從尾開始計數的方式，只要加上一個負號即可，這邊要注意，從尾開始第一個數是 -1 喔。
```python=
# 範例 4-4
# 倒數第一個學生
print(math_scores[-1]) # 88

# 倒數第五個學生
print(math_scores[-5]) # 97
```

### 取一個範圍
如果要取一個範圍的數字的範圍，我們可以在中括號的中間放「```起點：終點```」的語法來告訴 Python 我們要**從哪裡開始取**我們的字串，並**在哪裡結束**。

這邊要特別注意「**起點**」是**被包括**在我們的範圍中，而「**終點**」則是**不被包含**在我們的範圍中：
```python=
# 範例 4-5
# 第 1 個到第 5 個
print(math_scores[0:5]) # [76, 51, 71, 69, 98]
# 第 15 個到倒數第 3 個
print(math_scores[14:-2]) # [93, 92, 72, 73, 66, 100, 53, 83, 63, 95, 58, 97, 84, 91]
```

那麼如果我們想要取某個指數後的全部字元，我們可以直接在該指數後加上一個冒號，語法會是 ```[index:]```；如果是要該指數之前的全部字元，冒號則是加在前面，語法會是 ```[:index]```。
#### 簡單舉例
```python=
# 第 26 個之後
print(math_scores[25:]) # [97, 84, 91, 81, 88]
# 第 10 個之前
print(math_scores[:10]) # [76, 51, 71, 69, 98, 62, 82, 87, 90, 62]
```




## 串列的操作
### 型別轉換
如果我們將字串或是整數轉換成串列會發生甚麼事情呢？就讓我們來試看看吧：
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
我們可以看到如果將字串型別轉換成串列，Python 會將字串中的每個字母、標點符號、空白鍵為單位，分別儲存成串列的元素。

但如果是放整數的話：
```python=
a = 12
myList = list(a)

print(a)
print(myList)
```
則會出現錯誤訊息：
```
TypeError: 'int' object is not iterable
```
這表示整數是無法被型別轉換成串列！
### 合併

當我們想要將兩個串列合併，我們可以使用「＋」將它們合併
```python=
a = [1, 2, 3, 4]
b = [5, 6, 7, 8, 9, 10]

c = a + b
print(c) # [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```
### 複製
複製串列我們可以使用 ```[：]``` 的語法，這相當於將這個串列裡的資料全部複製一份新的給另一個串列變數，所以**當更動原串列時，並不會更動到新的串列**。

這和直接使用「b = a」將兩個變數指向同一個串列有所不同，因為當兩個變數都指向同一個串列，只要任何一個變數去做操作，便會同時更改到兩者的內容物。

那麼就讓我們用一個例子來了解吧！

1. 如果直接使用 ```b=a```：
```python=
a = [1, 2, 3]
b = a
del(a[1])
print(a)  # [1, 3]
print(b)  # [1, 3]
```
兩者都一起被更改了！

2. 如果用複製 ```[:]```：
```python=
a = [1, 2, 3]
b = a[:]
del(a[1])
print(a)  # [1, 3]
print(b)  # [1, 2, 3]
```
更動其中一個並不會影響另一個的內容物！


## 串列中常見的函數
現在就讓我們來看看 Python 幫我們寫好用來操作串列的功能吧！在後面的章節會再詳細介紹函數的定義，現在我們可以把函數想成是一些小功能：

1. ```len(list)```
首先，如果我們想要知道某個串列的函數，我們把我們的串列進```len```的括號中就可以辦到：

```python=
my_list = [1, 5, 2, 7, 4]
print(len(my_list)) # 5
```

2. ```add(element)```、```extend(list)``` 
如果我們要增加元素到 list，可以使用 ```add()```；如果是增加一個 list 的話，則可以使用 ```extend()```：

```python=
my_list = [1, 2, 3]
my_list.add(4) # [1, 2, 3, 4]

my_list = [1, 2, 3]
other_list = [10, 9, 8]
my_list.extend(other_list) # [1, 2, 3, 10, 9, 8]
```
3. ```insert(index, element)``` 
將某值加到我們想要的位置，則可以用 insert，第一個參數是我們想將元素加到的位置（index），第二個參數則是我們想加入的元素（element）：

```python=
my_list = ['good evening', 'good afternoon', 'good morning', 'good night']
my_list.insert(2, 'hello') 
# ['good evening', 'good afternoon', 'hello', 'good morning', 'good night']
```
4. ```pop(index)```
我們可以將不要的元素用 ```pop``` 刪除，這個函式會回傳被 pop 的值，且預設是刪除串列中的最後一個元素：
```python=
my_list = [2, 3, 4, 5, 6]
my_list.pop(1) # [2, 4, 5, 6]
my_list.pop() # [2, 4, 5]
```

5. ```del list[index]``` 
```del``` 是用我們想要刪除的元素的索引值 index，語法是在 ```del``` 後面寫上串列以及要刪除的索引值：
```python=
my_list = [1, 2, 3, 4, 5]
del my_list[0]
```
8. ```remove(element)```
```remove``` 則是用值來刪除「第一個」是該值的元素：
```python=
my_list = [1, 2, 3, 4, 5]
my_list.remove(3)
```
 9. ```split("delimeter")```
我們可以用 ```split()``` 將一個字串依照其分隔符（delimeter）分隔成數個串列：
```python=
my_string = "1@anismke@slje@sirjg"
print(my_string.split("@")) # ['1', 'anismke', 'slje', 'sirjg']
```

10. ```sep.join(list)```
我們將串列用合併成一個字串，並且在 ```join``` 前面寫上合併後串列元素間的連接符號：
```python=
my_list = ["2024", "01", "01"]
my_list = '-'.join(my_list)
my_list # '2024-01-01'
```

11. count
```count``` 可以計算串列裡某個值總共出現的次數：

```python=
happy_list = ['h', 'a', 'p', 'p', 'y']

print(happy_list.count('p')) # 2
print(happy_list.count('b')) # 0
```

12. ```sort```
將串列依照某個順序去做排列，通常是數字由小到大或是由大到小的順序。

    ```sort``` 有許多參數可以去做調整，首先是 ```reverse```，sort 的預設是升冪排列，如果我們想要數列以降冪排列，我們則可以把 reverse 設為 True，便可以達到效果。

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

* 小補充
另外一個可以調整的參數是 ```key```，也就是排序的規則。我們通常會使用一個叫 ```lambda``` 的語法，用法就是 ```lambda x:x[index]```，則可以取出每一個我們要比較的元素的第 index 索引的值，再進行比較排序

    像是如果我們想要將串列裡的字串**按照它們的第二個字母去做排序**，那麼我們便可以這樣寫：
```python=
another_list = ["hello", "okay", "bye bye", "lah"]
another_list.sort(key = lambda x : x[1])
print(another_list) # ['lah', 'hello', 'okay', 'bye bye']
```

---

### References
* [串列list型態-Python](https://nkust.gitbook.io/python/untitled)
* [STEAM 教育學習網](https://steam.oxxostudio.tw/category/python/basic/list.html)

If you have any questions regarding the materials, please contact me via Email! 
> debbiehuang35117@gmail.com