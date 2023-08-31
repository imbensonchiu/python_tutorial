# Chapter 10 - 模組 (modules) 與套件 (packages)

>  **Benson Chiu** 邱秉辰 @ NTU IM CAMP 2024 <br>
> Department of Information Management, National Taiwan University.
>
> 本章節參考：Introducing Python, 2nd Edition by Bill Lubanovic (2019) & chatGPT

## 模組 (modules) 

當程式規模越來越大時，為了提升程式碼的可維護性與易讀性，我們可以將具有不同功能程式碼放置於不同的檔案，並藉由 `import` 關鍵字相互引用。

在 Python 中，**模組 (module)** 是一個以 .py 為副檔名的程式碼檔案，換句話說，任何 .py 檔都可以作為模組來使用。

```py
#say_hello.py
def greeting(name):
    print(f"Hello, {name}!")

def say_goodbye(name):
    print(f"Goodbye, {name}!")
```

```python
import say_hello
say_hello.greeting("Python")
say_hello.greeting("Guido")
```

>Hello, Python! 
>Hello, Guido!

藉由 `import 模組名稱`，我們便可將**同一個資料夾內**的某個 .py 檔案引入到程式碼中，並且存取其成員函數。

此外，我們可以運用 `as` 關鍵字幫模組取一個別名，舉例來說：

```py
import say_hello as sh
sh.greeting("Python")
sh.greeting("Guido")
```

如果我們只想要取得 say_hello.py 中的 greeting 函數，可以透過 `from` 關鍵字來進行

```py
from say_hello import greeting
greeting("Python")
greeting("Guido")
say_goodbye("Python") # NameError
```

此時，我們可以直接使用該函數的名稱，但是無法使用該模組內的其他成員函數。

## 套件 (packages)

一個套件由**多個模組**所構成，且這些 .py 檔案皆是被放置於同一個資料夾底下。引入套件的方式和引入模組類似，皆是透過 `import`, `from` 與 `as` 的搭配。

由於引入自訂套件並非課程重點，有興趣的同學可參閱 [Python 官方文件](https://docs.python.org/zh-tw/3/tutorial/modules.html#packages)進一步了解，其概念事實上與模組類似，但較為複雜。

在資管營的課程中，請大家務必熟記以下三種引用模組 / 套件的常用方式：

<img src="/Users/bensonchiu/Documents/Documents/112-S/python_tutorial/ch9_modules_handout/image-20230730131022782.png" alt="image-20230730131022782" style="zoom:33%;" />

## 內建模組：以 math 和 datetime 為例

#### math 模組

math 是 Python 的其中一個**內建模組**，提供**數學相關**的運算功能和函數，部分舉例如下：

- 計算三角函數

```py
import math

angle = math.radians(45)  # 將角度轉換為弧度
sin_value = math.sin(angle)
cos_value = math.cos(angle)
tan_value = math.tan(angle)

print("sin(45°):", sin_value)
print("cos(45°):", cos_value)
print("tan(45°):", tan_value)
```

- 計算指對數

```py
import math

exp_value = math.exp(2)  # 計算e的次方
log_value = math.log(math.e)  # 計算以e為底的對數

print("e 的次方:", exp_value)
print("以 e 為底的 e 的對數:", log_value)
```

- 數字運算

```py
import math

absolute_value = math.fabs(-5)  # 取絕對值
rounded_value = round(3.6)  # 四捨五入
ceiled_value = math.ceil(4.2)  # 向上取整
floored_value = math.floor(7.8)  # 向下取整

print("絕對值:", absolute_value)
print("四捨五入:", rounded_value)
print("向上取整:", ceiled_value)
print("向下取整:", floored_value)
```

- 階乘和組合數

```py
import math

factorial_result = math.factorial(5)  # 計算5的階乘
comb_result = math.comb(10, 3)  # 計算從10中選擇3個元素的組合數

print("5的階乘:", factorial_result)
print("10選3的組合數:", comb_result)
```

有關 math 模組的更多資訊，請同學參考 [Python 官方文件](https://docs.python.org/3/library/math.html)

#### datetime 模組

顧名思義，Python 內建的 datetime 模組處理的是日期和時間的運算，模組主要包含 4 個類別：

- `date` 主要處理年、月、日
- `time ` 主要處理小時、分鐘、秒
- `datetime` 主要處理完整日期（換句話說，上面的 `date` 和 `time` 相加）
- `timedelta` 主要處理時間差

```py
from datetime import datetime, date, time, timedelta

# 獲取當前日期和時間
current_datetime = datetime.now()
print("當前日期和時間:", current_datetime)

# 創建一個特定的日期
specific_date = date(2023, 8, 31)
print("特定日期:", specific_date)

# 創建一個特定的時間
specific_time = time(14, 30, 0)
print("特定時間:", specific_time)

# 計算時間間隔
start_date = date(2023, 1, 1)
end_date = date(2023, 8, 31)
time_interval = end_date - start_date
print("時間間隔:", time_interval)

# 使用 timedelta 創建一個時間間隔
time_delta = timedelta(days=7, hours=3)
print("自定義時間間隔:", time_delta)

# 當前日期加上時間間隔
future_date = current_datetime + time_delta
print("未來日期:", future_date)

# 格式化日期
formatted_date = current_datetime.strftime("%Y-%m-%d %H:%M:%S")
print("格式化日期:", formatted_date)

# 解析日期字符串為 datetime 物件
parsed_datetime = datetime.strptime("2023-08-31 14:30:00", "%Y-%m-%d %H:%M:%S")
print("解析後的日期時間:", parsed_datetime)
```

datetime 模組在處理時間序列相關分析時非常實用，有關更多資訊，請同學參考 [Python 官方文件](https://docs.python.org/3/library/datetime.html)

## 第三方函式庫

Python 擁有豐富的第三方函式庫，這些函式庫可以大大擴展 Python 的功能，讓你能夠更輕鬆地進行各種任務。以下是幾個常見的第三方函式庫，以及它們的簡要介紹和舉例：

#### 資料科學類

1. NumPy：
   - 介紹：NumPy 是一個用於處理數值計算的函式庫，提供了高效的多維陣列和數學函式，用於處理矩陣運算和數據分析。
   - 舉例：進行數值計算、線性代數運算以及科學計算，如計算平均值、標準差等。
2. pandas：
   - 介紹：pandas 是一個用於數據分析和操作的函式庫，提供了 DataFrame 和 Series 等數據結構，能夠有效地處理和處理結構化數據。
   - 舉例：讀取、處理和轉換 CSV、Excel 檔案，進行數據清理、過濾、分組和聚合操作。
3. Matplotlib：
   - 介紹：Matplotlib 是一個繪製資料視覺化圖表的函式庫，支援各類圖表，如折線圖、散點圖、直方圖等。
   - 舉例：繪製數據趨勢圖、分佈圖、柱狀圖等，用於數據可視化和解釋。
4. scikit-learn：
   - 介紹：scikit-learn 是一個機器學習函式庫，提供了許多機器學習算法和工具。
   - 舉例：使用線性迴歸進行迴歸分析、使用支持向量機（SVM）進行分類，以及應用其他機器學習模型。
5. TensorFlow 和 PyTorch：
   - 介紹：用於深度學習的主要框架，提供了建立、訓練和部署神經網絡模型所需的工具和功能。
   - 舉例：使用 TensorFlow 或 PyTorch 建立卷積神經網絡（CNN）進行圖像分類，或建立循環神經網絡（RNN）進行自然語言處理任務。

#### 網頁開發類

1. Flask：
   - 介紹：Flask 是一個輕量級的 Web 應用框架，用於快速構建 Web 應用程序。它具有靈活性，並且適用於小型到中型的應用項目。
   - 舉例：建立一個簡單的網站，處理用戶請求、路由導航，以及返回 HTML 頁面。
2. Django：
   - 介紹：Django 是一個全功能的 Web 應用框架，提供了許多內置功能，如用戶驗證、數據庫模型、管理後台等，適用於複雜的 Web 項目。
   - 舉例：開發一個社交媒體平台，包括用戶註冊、登錄、發布文章等功能。
3. Requests：
   - 介紹：Requests 是一個簡單易用的 HTTP 請求函式庫，用於發送和接收 HTTP 請求，處理網絡操作。
   - 舉例：從 API 中獲取數據，發送 GET 或 POST 請求，處理服務器響應。
4. Beautiful Soup：
   - 介紹：Beautiful Soup 是一個用於解析 HTML 和 XML 文件的函式庫，提供了簡單的方式來提取網頁內容中的數據。
   - 舉例：從網頁上提取新聞標題、內容，或者從網站中爬取特定的數據。
5. Selenium：
   - 介紹：Selenium 是一個用於自動化 Web 測試和網絡操作的函式庫，它可以模擬瀏覽器行為。
   - 舉例：編寫測試腳本來測試 Web 應用的功能，自動執行登錄、填寫表單等操作。

在完成 Python 基礎語法的課程後，我們將會於**數位決策**的課程單元帶領大家探索重要的資料分析相關套件，包含：NumPy、pandas、Matplotlib、scikit-learn。往後，大家也可以自由探索自己感興趣的第三方函式庫，讓 Python 成為你在資料科學與軟體開發上的一把利刃！

