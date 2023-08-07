:::info
NTUIM Camp - Materials for Python - Dictionary, Set, and Tuple
教材編寫者：台大資管三 黃芷榆
:::


>　**Table of Contents**
[ToC]
---

在上一章節我們學到串列 list，然而在 Python 中還有許多資料型別可以當大容器使用，每種容器都有它們適合的使用時機，今天要介紹的新容器就是**元組**、**集合**以及**字典**。

## 元組（Tuple）
Tuple 和 list 非常相似，主要的不同是 tuple 建立之後便**無法更改**裡面的資料。

### 建立元組
首先就讓我們來看看要如何建立／宣告元組吧！
值得注意的是，元組大多是用小括號 () 來做表示，而 list 則是用中括號 [ ] 表示。
```python=
a_tuple = tuple()
b_tuple = ()
c_tuple = (1, 'd', 5.6, True)
```

那麼我們也想像串列一樣去增加元組裡的值，這樣會可行的嗎？
```python=
a_tuple.add(1)
```
```
AttributeError                            Traceback (most recent call last)
----> 1 a_tuple.add(1)

AttributeError: 'tuple' object has no attribute 'add'
```
tuple 是**不能去增加的**！因為 tuple 的值**不可做更改**。

同樣的問題也會出現在**刪除**和**修改**，tuple 只能取出值來喔！

## 集合（Set）
Set 也是一個裝資料的大容器，它的特色是**同樣的值只出現一次**，且他們是**沒有位置關係**的。

### 建立集合
請注意，set 我們會用大括號 { } 表示：
```python=
a_set = set()
b_set = {1, 2, 3, 4}
c_set = {2, '2'}
```
### 更新集合
再來我們來看看要如何對 set 的資料做增減：
1. ```add```：加上一筆資料
```python=
a_set = set() # {}
a_set.add(6)
a_set # {6}
```
2. ```update```：加上另一個 set
```python=
b_set = {1, 2, 3, 4}
b_set.update(c_set)
b_set # {1, 2, '2', 3, 4}
```
> 注意！重複的部分僅會留下一個喔

3. ```remove```：移除某個值，找不到該值會產生錯誤
```python=
b_set # {1, 2, '2', 3, 4}
b_set.remove(3) # {1, 2, '2', 4}
b_set.remove(5) # error
```
4. ```discard```：也是移除某個值，但是找不到該值時不會產生錯誤
```python=
b_set # {1, 2, '2', 4}
b_set.discard(4) # {1, 2, '2'}
b_set.discard(5) # {1, 2, '2'} 不會出現 error
```

Set 僅僅是儲存不重複的資料，**沒有對應關係**，因此只能做增加和移除，**無法做更改**（把某位置改成某個值）！

## 字典（Dictionary）
字典 dictionary 是有**鍵（key）以及值（value）對應**的容器。要注意的是我們的 **key 不會重複**，value 則是都可以。

### 建立字典
我們建立字典的語法是使用大括號 { } 以及冒號去做 key 和 value 的對應。

如果今天我們分別有以下物品及它們的數量：三把讑匙、六顆蘋果、一台火車，那麼我們的 key 是 "apple", "newspaper" 以及 "train"，而它們分別對應到的是 value 是 3, 6, 以及 1：
```python=
a_dict = dict()
b_dict = {}
c_dict = {'apple': 3, 'newspaper': 6, 'train': 1}
```


而當我們想要取出**某個 key 所對應到的 value**，我們可以用這樣的語法：```dict[key]```

舉例來說，當我們想知道有幾顆蘋果，也就是想求出 "apple" 這個 key 所對應的 value，那麼就可以寫：
```python=
c_dict['apple'] # 3 
```
我們的程式便會**回傳給我們它的 value**，也就是 $3$。
### 更新字典
更新字典有以下的方法：「增加」、「刪除」以及「更改」，讓我們來認識一下它們的語法：
1. **增加**：我們有兩種方法可以增加 dictionary 的內容：
* ```dict[key] = value```
* ```update({key:value})```
```python=
c_dict = {'apple': 3, 'newspaper': 6, 'train': 1}
c_dict['boat'] = 8 # {'apple': 3, 'newspaper': 6, 'train': 1, 'boat': 8}
c_dict.update({'bus': 7}) # {'apple': 3, 'newspaper': 6, 'train': 1, 'boat': 8, 'bus': 7}
```
2. **刪除**：我們也有兩種方法去刪除 dictionary 的內容：
* ```pop(key)```：會回傳被 pop 掉的 value
* ```del dict[key]```

```python=
c_dict # {'apple': 3, 'newspaper': 6, 'train': 1, 'boat': 8, 'bus': 7}
c_dict.pop('apple') # {'newspaper': 6, 'train': 1, 'boat': 8, 'bus': 7}
del c_dict['bus'] # {'newspaper': 6, 'train': 1, 'boat': 8}
```
3. **更改**：最後 dictionary 的更改和增加的語法一模一樣！
* ```dict[key] = value```
* ```update(key)```
```python=
c_dict # {'newspaper': 6, 'train': 1, 'boat': 8}
c_dict['newspaper'] = 5 # {'newspaper': 5, 'train': 1, 'boat': 8}
c_dict.update({'boat': 6}) # {'newspaper': 5, 'train': 1, 'boat': 6}
```


### 分別取出鍵、值
有時候我們想知道單只有 key 的集合，或是單只有 value 的集合，或是我們想在不知道 key 和 value 的內容物的情況下取出它們的值。

針對以上的狀況，我們分別可以用 ```keys()``` 、```values()``` 以及 ```items()``` 來完成，就讓我們來看看該如何使用：
1. ```keys()```：當我們想要取得字典裡的所有 key 所形成的集合，我們便可以使用 ```keys()``` 這個函式：
```python=
score_dict = {'Math': 88, 'English': 97, 'Science': 90}

for key in score_dict.keys():
    print(key, end = ' ')
```
程式會印出：
```
Math English Science 
```
2. ```values()```：而當我們想要取得所有 value 所形成的集合，則是使用 ```values()```：
```python=
for value in score_dict.values():
    print(value, end = ' ')
```
程式會印出：
```
88 97 90 
```
3. ```items()```：如果我們想要同時取得所有 key 以及 value，則可以用 ```items()```：

    使用 ```a, b = dict.items()``` 時，Python 會依序分配 key 以及 value 給兩個變數：
```python=
for my_key, my_value in score_dict.items():
    print(my_key, ":", my_value)
```
程式會印出：
```
Math : 88
English : 97
Science : 90
```
我們可以看到每一層的迴圈都會取到字典裡一組的 key 以及對應的 value，並且將它們分配給 ```my_key``` 和 ```my_value``` 這兩個變數。

以上三種語法就是在字典中分別取出鍵和值的方式！

---
## References
* Hugo 王修佑。Python 基礎容器。SITCON Camp 2023。檢自 https://hackmd.io/@whyhugo/B1BfpLnH2#/ （Jul, 2023）
* W3Schools (1999 - 2023). Python list() Function. Retrieved from https://www.w3schools.com/python/ref_func_list.asp



If you have any questions regarding the materials, please contact me via Email! 
> debbiehuang35117@gmail.com
