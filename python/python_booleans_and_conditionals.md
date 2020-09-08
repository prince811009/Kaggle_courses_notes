# Booleans and conditionals
## Booleans
>Python has a type of variable called bool. It has two possible values: True and False.

Python 擁有一種稱為 `bool` 的變數型態, 他擁有兩種可能: True 和 False.

```python
x = True
print(x)
print(type(x))

# True
# <class 'bool'>
```

我們通常是從布林的運算符號中獲得布林值, 而不是直接在我們的代碼中放入 True or False. 下面這些是一些會回答 yes/no 的運算符號, 我們將在下面介紹其中的一些運算符號.

## Comparison Operations
比較的操作.

| Operation | Description               | comparison | Operation | Description                  |
| --------- | ------------------------- | ---------- | --------- | ---------------------------- |
| a == b    | a equal to b              |            | a != b    | a not equal to b             |
| a < b     | a less than b             |            | a > b     | a greater than b             |
| a <= b    | a less than or equal to b |            | a >= b    | a greater than or equal to b |

```python
def can_run_for_president(age):
    """Can someone of the given age run for president in the US?"""
    # The US Constitution says you must be at least 35 years old
    return age >= 35


print("Can a 19-year-old run for president?", can_run_for_president(19))
print("Can a 45-year-old run for president?", can_run_for_president(45))


# Can a 19-year-old run for president? False
# Can a 45-year-old run for president? True
```

這樣的比較通常像你所希望的那樣運作


```python
3.0 == 3

# True
```

但是有時候他可能也很棘手


```python
'3' == 3

# False
```

我們可以將比較的運算福和和其他我們已經看過的運算符號合併使用, 來表示幾乎無限的數學測試範圍, 例如, 我們可以通過檢查除以 2 的餘數是否為 1 來檢查是否為奇數:


```python
def is_odd(n):
    return (n % 2) == 1


print("Is 100 odd?", is_odd(100))
print("Is -1 odd?", is_odd(-1))

# Is 100 odd? False
# Is -1 odd? True
```

記得當我們在進行比較的時候, 請使用 `==` 代替 `=`, 當我們寫成 `n == 2` 的時候是在詢問關於 n 的值的問題, 但是當我們寫成 `n = 2` 的時候則是在更改 `n` 的值.


## Combining Boolean Values

合併布林值, 我們可以使用 "and", "or", and "not" 這些標準概念來組合布林值, 事實上, 這些字正是  `and`, `or`, and `not`.

有了這些，我們可以使 `can_run_for_president` 函數更準確.


```python
def can_run_for_president(age, is_natural_born_citizen):
    """Can someone of the given age and citizenship status run for president in the US?"""
    # The US Constitution says you must be a natural born citizen *and* at least 35 years old
    return is_natural_born_citizen and (age >= 35)


print(can_run_for_president(19, True))
print(can_run_for_president(55, False))
print(can_run_for_president(55, True))

# False
# False
# True
```

能猜出下方表達式的值嗎?

```python
True or True and False

# True
```

要回答這個問題, 我們需要弄清楚操作符號的順序.

例如, `and` 是在 `or` 運算之前, 這就是為什麼在上面的第一個表達式會是 `True`, 如果我們是從左至右進行運算, 則我們會先計算 `True or True` ( 得到 `True`), 接著才是將結果與 `and` 計算, 得到最後的值為 `False` ( 這邊是錯誤的答案 ).

我們可以嘗試[memorize the order of precedence](https://docs.python.org/3/reference/expressions.html#operator-precedence) 記住運算符號的優先順序, 不過更加安全的選擇則是使用括號, 這不僅可以避免 bug 發生, 也可以讓其他人更清楚閱讀我們的代碼.

例如, 考慮以下表達式:

```python
prepared_for_weather = have_umbrella or rain_level < 5 and have_hood or not rain_level > 0 and is_workday
```

原文上嘗試想表達的是: 我想不受天氣影響...

1. 如果我有雨傘...
2. 或者如果雨不是太大, 我有風帽...
3. 否則, 除非下雨又是在工作天, 不然我還是可以的

但是這樣不只我們的 code 難以閱讀, 而且還有一個錯誤, 因此我們可以通過添加一些括號來解決這兩個問題:

```python
prepared_for_weather = have_umbrella or (rain_level < 5 and have_hood) or not (rain_level > 0 and is_workday)
```

如果覺得這有助於提高可讀性, 我們也可以添加更多的括號:


```python
prepared_for_weather = have_umbrella or ((rain_level < 5) and have_hood) or (not (rain_level > 0 and is_workday))
```

我們還可以將其分為多行來強調上述 3 個部分的結構:


```python
prepared_for_weather = (
    have_umbrella 
    or ((rain_level < 5) and have_hood) 
    or (not (rain_level > 0 and is_workday))
)
```

## Conditionals

條件式, 布林值在與條件式結合使用的時候式最好用的, 這些條件式語句使用關鍵字 `if`, `elif` 和 `else`.

條件式與句, 通常稱為 "if-then" 語句, 讓我們可以基於某些布林條件的值來控制執行哪一段代碼, 下面是一個例子:


```python
def inspect(x):
    if x == 0:
        print(x, "is zero")
    elif x > 0:
        print(x, "is positive")
    elif x < 0:
        print(x, "is negative")
    else:
        print(x, "is unlike anything I've ever seen...")


inspect(0)
inspect(-15)


# 0 is zero
#-15 is negative
```

`if` 和 `else` 這兩個關鍵字通常也會在其他語言中使用; 而這邊比較特別的是這個關鍵字 `elif`, 為 "else if" 的縮寫, 在這些條件子句中, `elif` 和 `else` 這兩項是可選的; 此外, 我們可以根據需求自行增加任意多個 `elif`.

請特別注意使用帽號 `:` 和空格來表示分隔的代碼區塊, 這類似於我們在定義函數時的情況 - 函數的開頭以 `:` 作結尾, 並且在下一行以 4 個空格縮排, 所有後續縮排的行數都屬於函數的主體, 一直到遇到未縮進的行數為止, 從而結束函數的定義.


```python
def f(x):
    if x > 0:
        print("Only printed when x is positive; x =", x)
        print("Also only printed when x is positive; x =", x)
    print("Always printed, regardless of x's value; x =", x)


f(1)
f(0)


# Only printed when x is positive; x = 1
# Also only printed when x is positive; x = 1
# Always printed, regardless of x's value; x = 1
# Always printed, regardless of x's value; x = 0
```

### Boolean conversion

布林轉換, 我們已經看過可以轉換為整數的 `int()` , 以及可以轉換為浮點數的 `float()` , 所以我們應該對於可以轉換為布林值的 `bool()` 不會感到驚訝.

```python
print(bool(1)) # all numbers are treated as true, except 0
print(bool(0))
print(bool("asf")) # all strings are treated as true, except the empty string ""
print(bool(""))
# Generally empty sequences (strings, lists, and other types we've yet to see like lists and tuples)
# are "falsey" and the rest are "truthy"

# True
# False
# True
# False
```

我們可以在 `if` 條件式和其他可能需要布林值的地方使用 "non-boolean" 非布林的 object, python 將把它們視為對應的布林值:


```python
if 0:
    print(0)
elif 'spam':
    print("spam")


# spam
```
