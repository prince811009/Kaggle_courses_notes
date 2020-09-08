# Loops and List Comprehensions
## Loops

Loops 是一種重複執行某些代碼的方法, 這邊有個例子:

```python
planets = ['Mercury', 'Venus', 'Earth', 'Mars', 'Jupiter', 'Saturn', 'Uranus', 'Neptune']
for planet in planets:
    print(planet, end=' ') #print all on same line


# Mercury Venus Earth Mars Jupiter Saturn Uranus Neptune 
```

`for` 循環必須具備:
- 要使用的變數名稱 ( 這例子中為 `Planet`)
- 用來 loop 一整組值的名稱 (這例子中為 `planets`)

我們使用 `in` 來連結.

 `in` 右側的對象可以是任何支持迭代的對象, 基本上, 如果可以將其視為一組事物, 便可以對它作循環, 除了 lists 可以這麼做之外, 我們還可以重複 tuple 的元素:

```python
multiplicands = (2, 2, 2, 3, 3, 5)
product = 1
for mult in multiplicands:
    product = product * mult
product


#360
```

我們甚至可以循環字串中的每個字:

```python
s = 'steganograpHy is the practicE of conceaLing a file, message, image, or video within another fiLe, message, image, Or video.'
msg = ''
# print all the uppercase letters in s, one at a time
for char in s:
    if char.isupper():
        print(char, end='')


# HELLO
```

### range()

`range()` 是一個返回數字序列的函數, 且事實證明, 這對於編寫循環非常有用.

舉例來說, 如果我們要重複 5 次操作:

```python
for i in range(5):
    print("Doing import work. i =", i)


# Doing important work. i = 0
# Doing important work. i = 1
# Doing important work. i = 2
# Doing important work. i = 3
# Doing important work. i = 4
```

### `while` loops

`while` loop 是 Python 的另一種循環類型, 它會迭代直到條件終止:

```python
i = 0 
while i < 10:
    print(i, end=' ')
    i += 1


# 0 1 2 3 4 5 6 7 8 9 
```

`while` loop 的參數被視為布林值, 且會一直循環執行直到該語句被視為 False為止.

## List comprehensions

列表推導, "list comprehensions" 是 Python 最受喜愛和獨特的功能之一, 理解它們的最簡單方法可能就是看幾個範例:


```python
squares = [n**2 for n in range(10)]
squares


# [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

而這是在沒有 list comprehensions 的情況下我們的做法:

```python
squares = []
for n in range(10):
    squares.append(n**2)
squares


# [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

我們也可以加入 `if` 的條件式:


```python
sort_planets = [planet for planet in planets if len(planet) < 6]
sort_planets


# ['Venus', 'Earth', 'Mars']
```

( 如果我們也熟悉 SQL 的話, 我們可能會把它跟 "where" 想在一起)

這有一個使用 `if` 進行條件過濾並將某些轉換應用於 loop 循環變量的例子:


```python
# str.upper() returns an all-caps version of a string
loud_short_planets = [planet.upper() + '!' for planet in planets if len(planet) < 6]
loud_short_planets


# ['VENUS!', 'EARTH!', 'MARS!']
```

人們通常把它們寫在一行上, 但是當結構分成三行以上時, 我們可能會發現結構更清晰:


```python
[
    planet.upper() + '!'
    for planet in planets
    if len(planet) < 6
]


# ['VENUS!', 'EARTH!', 'MARS!']
```

( 繼續上方剛剛提到的和 SQL 的類比, 我們可以將這三行視為 SELECT, FROM 和 WHERE)

從技術上來說的話, 左側的表達式不必包含循環變量 ( 儘管這聽起來很不尋常 ), 那我們該如何看待以下表達式?


```python
[32 for planet in planets]
# [32, 32, 32, 32, 32, 32, 32, 32]
```


List comprehensions 結合了像是 `min`, `max` 和 `sum` 的函式, 可以當作令人印象深刻的單行解決方案, 否則將需要好幾行代碼.

例如, 比較下面兩個執行相同操作的代碼區塊.


```python
def count_negatives(nums)
    """Return the number of negative numbers in the given list.
    
    >>> count_negatives([5, -1, -2, 0, 3])
    2
    """
    n_negative = 0
    for num in nums:
        if num < 0:
            n_negative = n_negative + 1
    return n_negative
```

這裡為使用 list comprehension 的解決方式:

```python
def count_negatives(nums):
    return len([num for num in nums if num < 0])
```

感覺是否好多了呢?

那如果我們只關心代碼的長度最小化, 那麼第三種解決方案更好

```python
def count_negatives(nums):
    # Reminder: in the "booleans and conditionals" exercises, we learned about a quirk of 
    # Python where it calculates something like True + True + False + True to be equal to 3.

    # 提醒: 在"python_booleans_and_conditionals" 的練習中, 我們了解
    # Python 會計算 True + True + False + True 等於 3.
    return sun([num < 0 for num in nums])
```

這些解決方案中的哪一個是 "最佳" 的方法完全是主觀的, 用更少的代碼來解決問題總是好的, 但是值得記住的是《 The Zen of Python》中的以下幾行:

>Readability counts.
Explicit is better than implicit.

可讀性很重要. 清楚的比含糊的好.

因此, 的確可以使用這些工具來寫緊湊可讀的程式碼. 不過, 如果我們必須選擇, 請使用易於他人理解的代碼.
