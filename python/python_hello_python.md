# Hello Python
## Intro
>This course covers the key Python skills you'll need so you can start using Python for data science.

這堂由 Kaggle 提供的 Python 課程提供了 data science 所需的技能, 適合給那些有一些 coding 經驗的人或是想提升 python skills 的人. 以下將會簡述關於 Python 的語法, 變數以及運算符號.

## Hello, Python
對於學了數種語言的朋友們, 應該已經用各種語言跟這個 world 打過招呼了吧, 不過不免俗的第一步也讓我們先來開始使用 python 打聲招呼.

```python
spam_amount = 0
print(spam_amount)

spam_amount = spam_amount + 4

if spam_amount > 0:
    print("But I don't want ANY spam")

viking_song = "Spam " * spam_amount
print(viking_song)
```

上述為一般的條件判斷式, 有猜到會印出什麼嗎

```python
0
But I don't want ANY spam
Spam Spam Spam Spam
```

讓我們一步一步拆解這項奇怪的程式碼, 並從中去觀察 python 是如何運作.
首先, 

```python
spam_amount = 0
```

### `Variable assignment`:
變數分配, 我們可以先命名一個變數 `spam_amount` , 接著賦值給這項變數 `0`, 而這中間的 `=` 也就是運算符號 (assignment operator).


#### 小提示:

如果是之前有使用過其他語言像是 Java/c++ 等, 可能會發現以下兩點:

- 我們不需要在使用之前先宣告 `spam_amount`.
- 我們不須指定 `spam_amount` 的型態為何, 事實上, 我們甚至可以去重新指定 `spam_amount` 為一個不同的東西, 例如 string 或 boolean.

```python
print(spam_amount)
# 0
```

### `Function calls`:
調用函式, `print` 為一項 python 函式, 他可以將值顯示在畫面上. 我們調用函式的方式是在這項函式後面加上括號, 然後放入值或是參數在其括號中.

```python
# Ordering Spam, egg, Spam, Spam, bacon and Spam (4 more servings of Spam)
spam_amount = spam_amount + 4
```

原文的部分還附上了第一行的這句句子, 示範可以使用 `#` 來做註解.

第二行的部分為重新賦值的範例, 重新給定一個值給已經存在的變數, 而方法就項是一開始定義變數相同, 使用 `=` 這項賦值的運算符號.

在這項例子中, 我們賦值給 `spam_amount` 的這項值包含了簡易的數學計算, 因此當 python 遇到這行程式碼時, 他會先評估 `=` 右邊的表達式為 (0 + 4 = 4), 接著再賦值給左邊的變數.

```python
if spam_amount > 0:
    print("But I don't want ANY spam!")

viking_song = "Spam Spam Spam"
print(viking_song)
```

目前這邊原文先不討論條件式, 不過就算沒有 coding 經驗的人, 應該也可以猜到其中的意思, 且 Python 珍貴在於他的簡單易讀.

可以注意到我們如何指定哪一行程式碼給 `if` 使用. 只有當 if `spam_amount` 是對的時候, `"But I don't want ANY spam!"` 才會印出, 不過在接下來的程式碼中, 例如 `print(viking_song)` 則是不管如何都會被執行, 請問 python 知道呢?

可以觀察到在 `if` 後面所接的冒號 `:` 表示了一個新的區域 (code block) 的開始, 因此後續只要是 "縮排" (indented) 的行數都表示是在這個 new code block 中. 其他程式語言可能是使用 curly braces `{}` 來標記 code block 的起始. Python 使用有意義的空白鍵 ( 這邊指縮排 ) 可能會讓習慣其他語言的人感到驚訝, 但是在執行中, 這可以使程式碼比其他沒有強迫使用縮排來區隔 new code block 的語言, 更加有一致性以及易讀性.

接下來處理 `viking_song` 的這行程式碼並沒有使用 4 個空白鍵來縮排, 因此他們並不是 `if` code block 的一部分. 後續我們也可以在定義 functions 和使用迴圈中看到更多關於縮排來當作 code block 的例子.

另外也可以注意到 `"But I don't want ANY spam!"` 是我們在 python 中第一個定義的 string.

```python
"But I don't want ANY spam!"
```

字串可以使用單引號或雙引號來標記, 不過由於一些特定的字串會包含單引號, 因此我們可能會被單引號所搞混, 除非我們小心使用.

```python
viking_song = "Spam " * spam_amount
print(viking_song)
# Spam Spam Spam Spam 
```

其中 `*` 這項運算符號可以將兩個數相乘 (3 * 3 為 9), 不過有趣的是, 我們也可以將字串跟數字相乘, 得到重複數次的文本. Python 提供了許多諸如此類的省時的小技巧，其中 `*` 和 `+` 等運算符的含義取決於所應用的事物類型.

---

## Numbers and arithmetic in Python
在上述我們已經看過包含數字的變數的例子:

```python
spam_amount = 0
```

"Number" 是這類事物一個很好的非正式名稱, 但如果我們想提高技術水平, 我們詢問 Python 是如何描述 `spam_amount` 的型態:

```python
type(spam_amount)
# int
```

結果顯示為 `int`, 為 integer 的縮寫, 而這邊也有 number 的縮寫是我們經常在 python 中遇到的:

```python
type(19.95)
#float
```

`float` ( 浮點數 ) 為有小數位的數字, 對於表示項是重量, 比例等很有用.

`type()` 則為第二個我們提到的內建函數 ( 第一個為 `print()`), 這也是很值得記得的一項, 讓我們可以詢問 python 這是什麼型態來說很有用.

要處理數字, 很自然的事情就是執行算術運算. 我們已經看過 `+` 加號以及 `*`  乘號 ( 某一種程度上 ), python 也介紹了我們計算器上其餘的基本按鈕:

| Operator | Name           | Description                                                               | 說明                       |
| -------- | -------------- | ------------------------------------------------------------------------- | -------------------------- |
| a + b    | Addition       | Sum of a and b 加法                                                       | 加法                       |
| a - b    | Subtraction    | Difference of a and b 減法                                                | 減法                       |
| a * b    | Multiplication | Product of a and b 乘法                                                   | 乘法                       |
| a / b    | True division  | Quotient of a and b 除法後得到的商                                        | 除法後得到的商             |
| a // b   | Floor division | Quotient of a and b, removing fractional parts 除法後得到的商去除小數部分 | 除法後得到的商去除小數部分 |
| a % b    | Modulus        | Integer remainder after division of a by b 除法後得到的整數餘數           | 除法後得到的整數餘數       |
| a ** b   | Exponentiation | a raised to the power of b 乘冪                                           | 乘冪                       |
| -a       | Negation       | The negative of a 負值                                                    | 負值                       |


有趣的是我們可以發現, 可能我們所使用的計算機指有一種除法的按鈕, 但 pyhton 則可以處理兩種, "True division" 也就是我們一般的計算暨上的除法方式:

```python
print(5 / 2) # 2.5
print(6 / 2) # 3.0
```

這項方法永遠會回傳浮點數 `float`.
因此, `//` 這項運算符號幫我們四捨五入取到整數位

```python
print(5 // 2) # 2
print(6 // 2) # 3
```

我們能想像這項方法可以運用在哪裡嗎? 我們將很快會在後續的編碼挑戰中見到例子.

### Order of operations:
運算符號的先後順序, 我們先前所學的運算符號的執行順序是按照 PEMDAS - Parentheses( 括號 ), Exponents( 指數 ), Multiplication( 乘法 )/Division( 除法 ), Addition( 加法 )/Subtraction( 減法 ). 而 python 也是依照相似的規則進行, 且他們大多很直覺.

```python
8 - 3 + 2 #7
```

```python
-3 + 4 * 2 #5
```

不過有時這些預設的順序並非我們所想要的:

```python
hat_height_cm = 25
my_height_cm = 190
# How tall am I, in meters, when wearing my hat?
total_height_meters = hat_height_cm + my_height_cm / 100
print("Height in meters =", total_height_meters, "?")
# Height in meters = 26.9 ?
```

以上面的例子會發現, 括號對我們來說是很有用的, 我們可以使用括號讓 python 以任何順序去計算子表達式.

```python
total_height_meters = (hat_height_cm + my_height_cm) / 100
print("Height in meters =", total_height_meters)
# Height in meters = 2.15
```

### Builtin functions for working with numbers:
處理數字的內建函式, `min` and `max` 兩項 function 會回傳參數的最小值和最大值, 分別為:

```python
print(min(1, 2, 3)) # 1
print(max(1, 2, 3)) # 3
```

`abs` 則會回傳參數的絕對值:

```python
print(abs(32)) # 32
print(abs(-32)) # 32
```

此外, `int` 和 `float` 作為 python 兩項最主要的數值型態, 他們也可以當作函式來轉換參數變成相對應的型態:

```python
print(float(10)) #10.0
print(int(3.33)) # 3
# they can even be called on strings 也可以在字串上調用
print(int('807') + 1) # 808
```
