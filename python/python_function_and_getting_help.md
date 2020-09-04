# Python
## Intro
>You've already seen and used functions such as print and abs. But Python has many more functions, and defining your own functions is a big part of python programming.

>In this lesson you will learn more about using and defining functions.

我們已經學會了像是 `print` 和 `abs` 等函式, 不過 python 擁有更多函式, 且定義自己的函式也是 python 編程一個重要的部分.

在這節中, 我們將會學到更多關於使用以及定義函式的方法.

## Getting Help
我們已經在先前的教程中看過 `abs` 這個 function, 但如果我們已經忘記了他是如何運作的呢?

`help()` function 可以是我們學習最重要的 Python 函數, 如果我們還記得如何使用 `help()` , 則可以掌握理解大多數其他功能的關鍵.

以下為一個例子:

```python
help(round)


# Help on built-in function round in module builtins:

# round(...)
#    round(number[, ndigits]) -> number
    
#    Round a number to a given precision in decimal digits (default 0 digits).
#    This returns an int when called with one argument, otherwise the
#    same type as the number. ndigits may be negative.
```

這其中 `help` 扮演兩項角色:

1. function 的開頭 `round(number[, ndigits])` 在這情況下, 這告訴我們 `round()` 可以接受一個數字的參數, 另外, 我們可以選擇給出一個單獨的參數來表示 n 個數字.
2. 一個簡短的敘述告訴我們這個 function 的作用.
   
### Common pitfall
常見的陷阱, 當我們在查詢函數時, 請記得要傳遞函數本身的名稱, 而非函數調用後的結果.

如果我們在調用 `abs()` 時呼叫 `help()` 會發生什麼事呢? 取消隱藏下面的輸出來查看.

```python
help(round(-2.01))
```

Python 從裡到外會評估出這樣的表達式, 首先, 他會先計算出 `round(-2.01)` , 接著他會為表達式的輸出提供協助.

(不過事實證明, 他對於整數有很多話想說, 在我們之後講解完 object, 方法和屬性之後, 上面這些大量的資訊輸出的協助會更有意義.)

`round()` 是個很簡單的函數, 帶有簡短的文字檔字串, 當我們處理更複雜, 或是有可以配置的功能 ( 像是 `print()`) 時, `help` 會更有力, 別擔心現在以下的輸出可能讓人覺得難以理解, 只要看看是不是可以從這個幫助中得到新內容即可.

```python
help(print)


# Help on built-in function print in module builtins:

# print(...)
#    print(value, ..., sep=' ', end='\n', file=sys.stdout, flush=False)
    
#    Prints the values to a stream, or to sys.stdout by default.
#    Optional keyword arguments:
#    file:  a file-like object (stream); defaults to the current sys.stdout.
#    sep:   string inserted between values, default a space.
#    end:   string appended after the last value, default a newline.
#    flush: whether to forcibly flush the stream.
```

如果你正在找這個, 我們可能可以學到 `print` 可以接受一個叫做 `sep` 的參數, 且他說明了我們在 `print` 其他所有參數之間可以放置的內容.

## Defining function
內建函數確實是很棒的, 但在我們需要開始去定義我們自己的函數時只能用他們, 以下是一個簡單的例子.

```python
def least_difference(a, b, c):
    diff1 = abs(a-b)
    diff2 = abs(b-c)
    diff3 = abs(a-c)
    return min(diff1, diff2, diff3)
```

這邊建立了一個叫作 `least_difference` 的 function, 他可以接收 a, b, c 三項參數.

函數由 `def` 這個 keyword 為開頭, 之後縮排進入一個新的 code block: 也就是調用這個函數時運作的地方.

`return` 他是與函數唯一關聯的另一個 keyword, 當 python 遇到 `return` 這個字的時候, 他將會立即退出這個函數, 接著將右側的值傳遞給調用的上下文.

上述的說明是否有較清楚的說明 `least_difference` 的運作呢? 如果還不確定的話, 我們總是可以再多試幾個例子:

```python
def least_difference(a, b, c):
    diff1 = abs(a - b)
    diff2 = abs(b - c)
    diff3 = abs(a - c)
    return min(diff1, diff2, diff3)


print(
    least_difference(1, 10, 100),
    least_difference(1, 10, 10),
    least_difference(5, 6, 7), # Python allows trailing commas in argument lists. Python 允許在 list 的最後加上逗號
)
# 9 0 1
```

看到這裡, 或許 `help()` function 可以告訴我們一些有關他的訊息.

```python
help(least_difference)


# Help on function least_difference in module __main__:

# least_difference(a, b, c)
```

Python 還不夠淙茗可以去閱讀我們的 code 且將他轉成描述, 不過, 當我們在寫一個函數時, 我們可以在文字檔字串中提供描述.

### Docstrings
文字檔字串.

```python
def least_difference(a, b, c):
    """
    Return the smallest difference between any two numbers among a, b and c.

    >>> least_difference(1, 5, -5)
    4
    """
    diff1 = abs(a - b)
    diff2 = abs(b - c)
    diff3 = abs(a - c)
    return min(diff1, diff2, diff3)
```

Docstring 是包在一個三個雙引號裡面的字串, ( 可能多行 ), 並且緊接在函數開頭之後, 而當我們調用 `help()` 的時候, 他將會顯示這些 docstring.

```python
help(least_difference)


# Help on function least_difference in module __main__:

# least_difference(a, b, c)
#    Return the smallest difference between any two numbers
#    among a, b and c.
    
#    >>> least_difference(1, 5, -5)
#    4
```

#### 小提示
這個例子調用了最後兩行的 docstring, 是範例函數的調用和結果. (中間這個符號 `>>>` 是 python 在跟 `shells` 互動時所使用的命令提示字元.) Python 不會自己運行這段範例的調用, 只是讓讀者好讀一些, 在函數的 docstring 中如果有一個或是多的範例的調用不會被觀察到, 但是這可以很有效的幫助其他人了解我們的函數. 有關於真實的例子, 可以參考 [this docstring for the numpy function](https://github.com/numpy/numpy/blob/v1.14.2/numpy/lib/twodim_base.py#L140-L194) `np.eye`.

好的程序員會好好利用 docstring, 除非他們用完這段程式碼便很快就移除, 因此, 我們也應該開始編寫 docstrings.

## Functions that don't return
沒有 `return` 的 function, 如果我們沒有包含 `return` 這個關鍵字在我們的函式裡會怎麼樣呢?

```python
def least_difference(a, b, c):
    """Return the smallest difference between any two numbers
    among a, b and c.
    """
    diff1 = abs(a - b)
    diff2 = abs(b - c)
    diff3 = abs(a - c)
    min(diff1, diff2, diff3)
    

print(
    least_difference(1, 10, 100),
    least_difference(1, 10, 10),
    least_difference(5, 6, 7),
)


# None None None
```

Python 允許我們定義像這樣的 function, 調用他們的結果是一個特殊的值 `None`. ( 這和其他語言中的 `null` 概念相同 ).

如果沒有 `return` 這個字, `minimum_difference` 就變得完全沒有意義了, 不過句有附加的作用的函數可能仍可以作一些有用的事情而不會返回任何值. 現在我們已經看到的兩個例子: `print()` 和 `help()` 也是不返回任何內容, 因此我們只有在需要他的附加的作用的時候調用他們, ( 比如說將一些文放顯示在螢幕上 ), 其他一些有用的附加作用包含謝入文件, 或是對輸入進行修改.

```python
mystery = print()
print(mystry)


# None
```

## Default arguments
預設參數, 當我們調用 `help`/`print` 時, 我們看到 `print` 函數有幾個可以選擇的參數, 例如, 我們可以為 `sep` 指定一個值, 在我們要印出的參數之間放一些特殊的字串. 

```python
print(1, 2, 3, sep=' < ')


# 1 < 2 < 3
```

不過如果我們沒有指定的值, `sep` 會當作我們使用 default 的值單引號 `' '`.

```python
print(1, 2, 3)


# 1 2 3
```

因此如果我們要加入可選的參數且帶著預設值到我們定義的 function 的話, 是非常容易的.

```python
def greet(who="Colin"):
    print("Hello, ", who)


greet()
greet(who="Kaggle")
# (In this case, we don't need to specify the name of the argument, because it's unambiguous 明確的.)
greet("world")
```

## Functions Applied to Functions
函數應用於函數, 這是強大的功能, 盡管一開始可能會感覺概念很抽象, 但是你可以提供 functions 作為一個參數給其他 functions 使用, 以下的範例可能會讓我們更清楚一些:

```python
def mult_by_five(x):
    return 5 * x

def call(fn, arg):
    """Call fn on arg"""
    return fn(arg)

def squared_call(fn, arg):
    """Call fn on the result of calling fn on arg"""
    return fn(fn(arg))


print(
    call(mult_by_five, 1),
    squared_call(mult_by_five, 1),
    sep='\n', # '\n' is the newline character - it starts a new line 換行
)


# 5
# 25
```

操作其他 function 的 function 稱為 "Higher order functions" 高階函數, 我們可能不會立刻寫到, 不過 python 內置了一些高階函數, 我們可能會發現調用他們很有用.

這裡有個使用 `max` 的有趣例子.

在預設的情況下, `max` 會回傳參數的最大值, 不過如果我們使用可選的 `key` 參數傳入一個函數, 他將返回最大的 `key(x)` 的參數 `x`. (又叫作 'argmax').

```python
def mod_5(x):
    """Return the remainder of x after dividing by 5. 回傳除以五之後的餘數"""
    return x % 5


print(
    'Which number is biggest?',
    max(100, 51, 14),
    'Which number is the biggest modulo 5?',
    max(100, 51, 14, key=mod_5),
    sep='\n'
)
```
