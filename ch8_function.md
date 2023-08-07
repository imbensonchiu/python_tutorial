:::info
NTUIM Camp - Materials for Python - Function
教材編寫者：台大資管三 黃芷榆
:::


>　**Table of Contents**
[ToC]
---

## 函式簡介
函式常常在數學課中聽到，但在程式的世界裡，它究竟是甚麼樣的存在呢？其實簡單了解後發現，它的功能和在數學裡非常相似喔：
> **函式 (function)** 會將傳入的數值進行邏輯運算後，再回傳結果給主程式。

我們可以把它想成一個可以幫我們完成特定功能的小工具，可以讓我們知道傳入的數值的特性，或者是幫我們將傳入的數值經運算得到需要的結果。

#### 函式的組成元素主要有：
1. 函式名稱
2. 傳入的參數
3. 中間的運算程式
4. 回傳值

它的語法會寫成：
```python=
def 函式名稱(傳入的參數):
    **
    計算過程
    **
    return 回傳值
```

**簡單舉例**
我們想要寫一個函式專門算一個數的平方，即為這樣的數學列式：$f(x)=x^2$ 
那麼用程式來寫就會是：
```python=
def sqrt(num):
    result = num ** 2
    return result
```

## 為甚麼要用 Function 呢？
那麼我們為甚麼要使用函式呢？在撰寫有上百上千行的大型程式碼檔案，或是會不停重複使用到某些功能時，函式便是不可或缺的存在！讓我們來看看它的好用之處吧：
1. **模組化**：將一樣的功能包在同一個地方
2. **可讀性**：明瞭的取名讓讀 code 更加方便
3. **維護性**：當要更改功能裡的變數值，不怕多處遺漏


## 參數預設
從上面的範例我們知道大多參數是希望使用者自行輸入，但是有時候就算使用者不傳入該參數，我們也有一個預設值（通常是該參數最常用用到的內容）。

這個時候，我們就會需要用到「參數預設」！

#### 簡單舉例

我們用例子來看要如何設定參數預設，假如我們如果想得到某數的「倍數」，可能是兩倍、三倍、四倍……，但是在**大部分時候我們使用的會是兩倍**，那麼我們就可以把 ```multiple``` 這個**參數預設成 2** 
```python=
def multiple(num, multi = 2):
    result = num * multi
    return result

multiple(3) # 6：  沒有傳入參數，使用預設參數
multiple(3, 5) # 15：   傳入參數 5 倍
```

## 遞迴

函式最方便用在「遞迴」的運算了！遞迴簡單來說就是有函式在運算中「呼叫自己」的敘述。

遞迴分成「決定基本情況（Base case）」，也就是遞迴的**終止條件**；以及「決定一般情況（General case）」，也就是遞迴的**關係式**。

它的格式如以下寫法：
```python=
def function_name(num):
    if base_case:
        return base_result
    else:
        return # 遞迴式的 general_formulation
```


#### 簡單舉例
大家想想看如果我想要知道**費波那契數列**中的**第 $n$ 個數**（數列中的數字為前該數前兩個數相加，假設第一數為 $0$、第二個數為 $1$），我們有甚麼樣的寫法呢？


#### 1. 迴圈寫法
我們可以使用迴圈，將前兩個數分別儲存在兩個變數中，再將兩個數相加得到下一個數，並適時地更新變數的值：
```python=
n = 9 # the length for our Fibonacci Sequence
num1 = 0
num2 = 1
next_num = 0

for i in range(n - 2):  
    next_num = num1 + num2
    num1 = num2
    num2 = next_num
 
print(next_num) # 21
```

#### 2. 函式寫法
函式我們便可以使用遞迴，不停呼叫到 base case 後，回傳值會按照遞迴關係式做運算後，將結果回傳給呼叫的程式，並一路回到我們最一開始呼叫遞迴函式的地方：
```python=
def Fibo(n):
    if n == 1: # Base case n == 1 or n == 2
        return 0
    elif n == 2:
        return 1  
    
    else: # General case n > 2
        return Fibo(n - 1) + Fibo(n - 2)
    
print(Fibo(9)) # 21
```
兩種寫法都可以實現我們的目的：找到費波那契數列中的第 $n$ 個數。但在很多時候，函式的寫法可以讓程式更加精簡，也可能可以省去創建更多變數。


### Challenge：[河內塔](https://zh.wikipedia.org/zh-tw/%E6%B1%89%E8%AF%BA%E5%A1%94)
大家如果想找一些遞迴的挑戰，就來試試看上面的河內塔題目吧，當輸入某數量的碟子，試著求出我們需要如何移動這些碟子才能在限制條件下完成任務！

[參考網站（含解答）](https://ithelp.ithome.com.tw/articles/10262851)

## 全域變數 v.s. 區域變數
**範圍（Scope）** 在有函式的程式中是很重要的觀念，其中我們將範圍分為「全域」以及「區域」。**全域變數**在程式檔案的各處皆可以使用；而**區域變數**則只能在出現在函式中使用，在該函式外便無法取用。

我們可以把**全域**裡的程式想成是**政府的政策**，而**區域**裡的程式則是每個**家庭裡的家規**，**政府無法得知每個家庭的家規**，但是只要是**在這個政府下生活的家庭都會知道政府訂定的政策**。

讓我們用一個簡單的例子來理解吧：

```python=
def double(num):
    double_num = 2
    return num * double_num

n = 5
print(str(n) + ' times ' + str(double_num) + ' is ' + str(double(n)))
```
我們會得到的此錯誤訊息：
```                             
      n = 5
----> print(str(n) + ' times ' + str(double_num) + ' is ' + str(double(n)))

NameError: name 'double_num' is not defined
```

這代表程式在這個位置並不知道 ```double_num``` 變數，因為 ```double_num``` 是定義在區域的變數，所以我們在全域的位置就無法得知這個變數的任何資訊。

但是相反的，全域變數（我們在全域定義的變數）在同一個程式裡的任何區域變數都可以取得。

```python=
def double():
    double_num = 2
    return n * double_num

n = 5
print(str(n) + ' times ' + '2' + ' is ' + str(double()))
```
會印出結果：
```
5 times 2 is 10
```
可以注意到，即使我們沒有傳參數 ```n``` 給 ```double()``` 這個區域函式，但我們的區域函式一樣可以取得全域變數 ```n``` 的值；因為政府的政策是家喻戶曉的，全域變數在同一個程式裡的任何區域變數都可以取得！

---
## References

* 李杰穎 Jayinnn（2023）。Python Functions。SITSCON CAMP 2023。檢自 https://hackmd.io/@SITCON/sitcon-camp-function#/ （Jul, 2023）
* vegibit. Python Recursion Examples. Retrieved from 
https://vegibit.com/python-recursion-examples/
* YehYeh。[資料結構] 基礎遞迴。YehYeh's Notepad。檢自 http://notepad.yehyeh.net/Content/DS/CH02/1.php

If you have any questions regarding the materials, please contact me via Email! 
> debbiehuang35117@gmail.com



