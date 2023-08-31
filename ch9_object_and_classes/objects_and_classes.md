# Chapter 9 - 物件 (objects) 與類別 (classes) 的基本概念

> **Benson Chiu** 邱秉辰 @ NTU IM CAMP 2024 <br>
> Department of Information Management, National Taiwan University.
>
> 本章節參考：Introducing Python, 2nd Edition by Bill Lubanovic (2019) & chatGPT

## 萬物皆物件

Python 中任何事物都可以被視為物件 (object)。舉例來說，`num = 7` 當中，`7` 是一個物件，而我們將名為 `num` 的便利貼（或者可以稱為物件參考）**「貼」** 在這個物件上面，日後我們可以透過 `num` 這個便利貼來存取該物件。

![Python: Objects everywhere. The Python language is a powerful… | by Daniela  Chamorro | Analytics Vidhya | Medium](https://miro.medium.com/v2/resize:fit:514/1*l6SQplsILMRhS1LZf3Zw1Q.jpeg)

一個物件包含了兩種資訊：**屬性 (attributes)** 與**方法 (methods)**。屬性是物件的資料，而方法則是物件的行為。比方說，假設你有一隻可愛的小貓咪，若我們將其視為一個 Python 物件，那麼牠的屬性可能包含了牠的**名字、年齡、體重、毛色**等等，而牠的方法則可能包含了 **「喵喵叫」、「睡覺」、「吃飯」** 等等。

```py
class Cat:
    def __init__(self, name): # 這是初始化的成員函數
        self.name = name # 這是 name 屬性
    def meow(self): # 這是 meow 方法
        print("你好，我是", self.name, "喵！")
    def eat(self, food): # 這是 eat 方法
        print("我是", self.name, "，我喜歡吃", food, "喵！")
    def sleep(self, hour): # 這是 sleep 方法
        print("我是", self.name, "，我想要睡", hour, "小時喵！")
```

在 Python 中，我們使用**類別 (class) **自定義物件的屬性以及方法。 

## 自定義物件：使用 `class` 關鍵字

### 物件初始化

**`__init__`** 是一個特殊的成員函數，我們可以透過這個函數**初始化物件**。

```py
class Cat:
    def __init__(self, name): # 這是初始化的成員函數
        self.name = name # 這是 name 屬性
    ......
    
myCat = Cat("小花貓") # 建立一個名為 myCat 的物件，並傳入參數 "小花貓"
```

在上例中， `self` 代表**物件本身**，而 `name` 則是我們**傳入的參數**。 我們建立了一個名為 `myCat` 、型態為 `Cat` 的物件，並且將貓咪的名字傳入至 `__init__` 當中並將該物件初始化。

若我們此時呼叫名為 `meow` 的方法

```py
myCat.meow() # 呼叫 meow 方法
```

> 你好，我是 小花貓 喵！

我們可以發現：該物件的 `name` 屬性已經成功地於剛剛的  `__init__` 成員函數中被初始化

### 存取與修改屬性

我們可以直接對該物件中的屬性值進行存取與修改

```py
print(myCat.name) # 印出 name 屬性
myCat.name = "小黑貓" # 修改 name 屬性
print(myCat.name) # 再次印出 name 屬性
```

> 小花貓 
> 小黑貓

### 呼叫成員函數

我們亦可呼叫並執行物件中的成員函數（方法）

```py
myCat.eat("魚") # 呼叫 eat 方法
myCat.sleep(5) # 呼叫 sleep 方法
```

> 我是 小黑貓 ，我喜歡吃 魚 喵！ 
> 我是 小黑貓 ，我想要睡 5 小時喵！

### 單一類別，多個物件：instance

假設現在你有**多隻**可愛的小貓，他們分別具有不同的**名字**屬性，但是有相同的 **行為**（喵喵叫、睡覺、吃飯），我們可以運用相同的 `Cat` 類別宣告不同的物件，而我們稱這些不同的物件為這個類別的**實例 (instances)**。

```py
# 四個物件屬於 Cat 類別，但都有自己的 name 屬性
cat_1 =  Cat("小花貓")
cat_2 =  Cat("小黑貓")
cat_3 =  Cat("小白貓")
cat_4 =  Cat("大橘貓")
```

```py
cat_1.meow()
cat_2.meow()
```

> 你好，我是 小花貓 喵！
> 你好，我是 小黑貓 喵！

## 內建物件

本章節的開頭便開宗明義地提及 **Python 中任何事物都可以被視為物件 (object)**，讓我們暫且回到這個敘述，並舉一個過往已經學習過的例子，讓大家對「物件」的這個抽象想法更有概念。

#### string 其實就是一個物件

大家可以回想看看在學習字串時我們所了解的各種**「方法」(methods)**，有沒有發現跟 **類別 (class) 成員函數的呼叫** 很相似呢？ 

我們其實可以把 string 想成是 **Python 預先定義好的一個類別**，`my_string`則是型態為 `string` 類別的一個物件，可以使用該類別內部的成員函數，也就是我們之前所認識的 **「方法」(methods)**

```py
# String methods example
my_string = "   Hello, World!   "

# lower() and upper()
lower_case = my_string.lower()
upper_case = my_string.upper()
print("Lowercase:", lower_case)  # Output: "   hello, world!   "
print("Uppercase:", upper_case)  # Output: "   HELLO, WORLD!   "

# replace()
new_string = my_string.replace("World", "Python")
print("Replaced:", new_string)  # Output: "   Hello, Python!   "

# split()
split_list = my_string.split(",")
print("Split List:", split_list)  # Output: ['   Hello', ' World!   ']

# join()
words = ["Hello", "world", "Python"]
combined_string = " ".join(words)
print("Combined String:", combined_string)  # Output: "Hello world Python"

# find() and index()
index_p = my_string.find("p")
index_m = my_string.index("m")
print("Index of 'p':", index_p)  # Output: 5
print("Index of 'm':", index_m)  # Output: 10

# count()
count_l = my_string.count("l")
print("Count of 'l':", count_l)  # Output: 3
```

## 物件導向程式設計

至此，我們已經大致了解了**物件 (object) **的基本概念與**類別 (class) **的使用方式，這也是進入物件導向程式設計的敲門磚之一。在本章的最後，讓我們來快速地認識物件導向程式設計 (Object-Oriented Programming) 的核心概念。

我們先來聽聽看 ChatGPT 怎麼說：

> 想像你正在遊戲中玩一個農場模擬遊戲。在這個遊戲裡，你可以種植作物、養殖動物等。現在我們要用**物件導向的角度**來看待這個遊戲。
>
> 每種作物和動物都可以被視為一個物件，這個物件有**自己的特性和行為**。比如，小麥作物物件可以有特性如生長階段、收穫時間，行為如生長和收穫的方法。同樣地，一頭牛動物物件可以有特性如飢餓程度、健康狀態，行為如進食和生產奶的方法。
>
> 這些物件可以相互交互。比如，你可以將牛放入農場，讓牠們進食，提高健康程度，然後開始產奶。這種互動模擬了現實世界中農場的運作。
>
> 在電腦科學中，物件導向程式設計的重要性在於它使得**複雜系統的設計和管理**變得更加**有組織**和**容易**。你可以透過定義不同的物件來分割系統，每個物件只需要關注自己的特定任務，而不必擔心整個系統的複雜性。這有助於提高代碼的**可讀性、可重用性和維護性**，同時也方便多人合作開發大型項目。
>
> 總之，物件導向程式設計就像是將**現實世界中的事物和互動模式映射到電腦程式中**，使得程式設計更加有組織和容易。它在電腦科學中扮演著非常重要的角色，幫助我們建立更強大且易於管理的軟體系統。
>
> <img src="https://th.bing.com/th/id/OIG.U1eQUvxjDnLjQppSzDjC?pid=ImgGn" alt="想像你正在遊戲中玩一個農場模擬遊戲。在這個遊戲裡，你可以種植作物、養殖動物等。現在我們要用**物件導向的角度**來看待這個遊戲。  每種作物和動物都可以被視為一個物件，這個物件有**自己的特性和行為**。比如，小麥作物物件可以有特性如生長階段、收穫時間，行為如生長和收穫的方法。同樣地，一頭牛動物物件可以有特性如飢餓程度、健康狀態，行為如進食和生產奶的方法。  這些物件可以相互交互。比如，你可以將牛放入農場，讓牠們進食，提高健康程度，然後開始產奶。這種互動模擬了現實世界中農場的運作。" style="zoom:33%;" />

如同上述 ChatGPT 的回應，當程式碼的規模愈加龐大，甚至要和多人一起協作**大型軟體專案**時，將資訊系統中的功能以物件的形式**模組化**可以大幅增加程式碼的**可讀性、可重用性和維護性**。

不論是開發遊戲、網頁應用程式，抑或是資訊系統，不論使用的語言是 C++、 Python 還是 JavaScript，**物件導向**是一個相當複雜但是重要的程式設計原則。我們將會在第 11 章向大家簡介物件導向當中的兩個核心概念：**繼承 (Inheritance)** 與 **多型 (Polymorphism)**。

