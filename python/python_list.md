# List
## List
>Lists in Python represent ordered sequences of values. Here is an example of how to create them:

Python 中的列表是表示有順序的值, 以下有個例子說明如何創建他們:

```python
primes = [2, 3, 5, 7]
```

我們也可以放入其他型態的東西到 list 中:


```python
planets = ['Mercury', 'Venus', 'Earth', 'Mars', 'Jupiter', 'Saturn', 'Uranus', 'Neptune']
```

我們也可以在 list 中加入 list:

```python
hands = [
    ['J', 'Q', 'K'],
    ['2', '2', '2'],
    ['6', 'A', 'K'], # (Comma after the last element is optional) 最後一項的逗號是可選的
]

# (I could also have written this on one line, but it can get hard to read)
hands = [['J', 'Q', 'K'], ['2', '2', '2'], ['6', 'A', 'K']]
```

List 也可包含不同型態的變數值:

```python
my_favourite_things = [32, 'raindrops on roses', help]
# (Yes, Python's help function is *definitely* one of my favourite things)
```

### Indexing

我們可以使用方括號訪問單獨的 list 元素.

哪個星球最靠近太陽? Python 使用基於 0 的索引,因此第一個元素的索引為　0.

```python
planets[0]
# 'Mercury'
```

那下一個最靠近太陽的星球呢?

```python
planets[1]
# 'Venus'
```

哪個星球離太陽最遠?
如果是在 list 的最尾端的元素, 可以從索引 -1 開始訪問:

```python
planets[-1]
# 'Neptune'


planets[-2]
# 'Uranus'
```

### Slicing

那前三個行星是那些呢? 我們可以使用 "slicing" 來回答這個問題:

```python
planets[0:3]
# ['Mercury', 'Venus', 'Earth']
```

`planets[0：3]` 表示我們從行星元素 - 索引的 0 開始計算, 延伸到索引 3( 但不包括索引 3).

起始索引和結束索引都是可選的, 如果我們省略起始索引, 則程式就會假定它是從 0 開始, 因此我們可以將上面的表達式重寫為:

```python
planets[:3]
# ['Mercury', 'Venus', 'Earth']
```

如果我們是沒有寫結尾的索引, 則表示要到 list 長度.

```python
planets[3:]
# ['Mars', 'Jupiter', 'Saturn', 'Uranus', 'Neptune']
```

即上面的表述的意思是: "將索引 3 以後的所有行星都給顯示出來".

我們也可以使用負索引:

```python
# All the planets except the first and last
planets[1:-1]
# ['Venus', 'Earth', 'Mars', 'Jupiter', 'Saturn', 'Uranus']
```

```python
# The last 3 planets
planets[-3:]
['Saturn', 'Uranus', 'Neptune']
```

### Changing lists

變更清單, list 是 "可以變動的" , 這表示我們可以 "就地" 修改它們.

修改 list 的一種方法, 就是將其分配給索引或 slice expression.

例如, 假設我們要重命名火星:


```python
planets[3] = 'Malacandra'
planets

# ['Mercury',
#  'Venus',
#  'Earth',
#  'Malacandra',
#  'Jupiter',
#  'Saturn',
#  'Uranus',
#  'Neptune']
```

### List functions

Python 有一些很有用的 functions 可以運用在 list 上.

`let` 可以得到 list 的長度:


```python
# How many planets are there?
len(planets)
# 8
```

`sorted` 可以得到排序過後版本的 list 回傳值

```python
# The planets sorted in alphabetical order 依照字母排序
sorted(planets)
['Earth', 'Jupiter', 'Mars', 'Mercury', 'Neptune', 'Saturn', 'Uranus', 'Venus']
```

`sum` 可以得到加總值:


```python
primes = [2, 3, 5, 7]
sum(primes)
# 17
```

我們之前使用的 `min` 和 `max` 來獲取參數的最小值或最大值, 不過我們也可以從一個單獨的 list 中得到.

```python
max(primes)
# 7
```

### Interlude: objects

插曲: 對象

到目前為止, 我們已經使用了很多次 `object` 這個詞, 設置我們可能都已經讀過 "Python 中的所有內容都是 object" , 那這代表什麼意思呢?

簡單來說, object 可以攜帶一些東西, 我們可以透過使用 python 的點語法 (dot syntax) 來訪問該內容.

例如, Python 中的數字帶有一個名為 `imag` 的關聯變量, 這表示它們的虛部. ( 不過除非我們正在做一些非常奇怪的數學運算, 否則可能永遠不需要使用它.)

```python
x = 12
# x is a real number, so its imaginary part is 0.
print(x.imag) # 0

# Here's how to make a complex number, in case you've ever been curious:
c = 12 + 3j
print(c.imag) # 3.0
```

Object 攜帶的東西還可以包括 functions, 附加在對象的 Function 稱為 `method`, ( 附加到 object 的 "Non-function" 非函式的事物, 例如 `imag`, 稱為屬性 "attributes").

例如, 有一項可用於數字的函式稱為 `bit_length`, 同樣的, 我們使用點語法 (dot syntax) 來訪問它:

```python
x.bit_length
# <function int.bit_length>
```

要實際調用它, 我們在上面加上括號:

```python
x.bit_length()
# 4
```

#### 小提示:

如果已經在進行這項練習, 那麼事實上我們已經在調用這項方法了, 在後面的練習筆記本中, `q1`, `q2`, `q3` 等都是 object, 都具有 `check`, `hint` 和 `solution` 這些方法.

並且同樣的, 我們也可以將函數傳給我們的 `help` 函數 ( 例如 `help(max)` 的方式 ), 我們也可以將它傳入方法:


```python
help(x.bit_length)


# Help on built-in function bit_length:

# bit_length(...) method of builtins.int instance
#     int.bit_length() -> int
    
#     Number of bits necessary to represent self in binary.
#     >>> bin(37)
#     '0b100101'
#     >>> (37).bit_length()
#     6
```

上面的範例可能不完全清楚, 到目前為, 我們所研究的 object 類型 (numbers, functions, booleans) 可能都沒有我們可能會使用的屬性或方法.

不過, 事實證明 list 有幾項方法我們將會一直用到他.

### List methods

`list.append` 可以將項目加在 list 的最後一項來進行修改 list:

```python
# Pluto is a planet darn it 冥王星是一顆行星
planets.append('Pluto')
```

而為何上面的區塊沒有輸出呢? 讓我們通過調用 `help(planets.append)` 來檢查.

#### 小提示:

`append` 是所有 object 可用的方法, 而不僅是給 `planets` 使用而以, 因此我們也可以調用 `help(list.append)` 來查詢, 不過, 如果我們嘗試調用 `help(append)`, Python 將會告訴我們稱為 "append" 的變數不存在, `append` 這個名稱只有在 list 中才存在 - 不作為獨立名稱存在, 像是內置函數 ( 例如 `max` 或 `len`).

```python
help(planets.append)


# Help on built-in function append:

# append(...) method of builtins.list instance
#     L.append(object) -> None -- append object to end
```

其中這個符號 `-> None`, 告訴我們 `list.append` 不返回任何值, 但是, 如果我們檢查 `planets` 的值, 我們可以看到這項方法調用了修改 `planets` 的值:

```python
planets


# ['Mercury',
#  'Venus',
#  'Earth',
#  'Mars',
#  'Jupiter',
#  'Saturn',
#  'Uranus',
#  'Neptune',
#  'Pluto']
```

`list.pop` 則會移掉且會回傳 list 的最後一個元素:

```python
planets.pop()
# 'Pluto'
```

```python
planets
# ['Mercury', 'Venus', 'Earth', 'Mars', 'Jupiter', 'Saturn', 'Uranus', 'Neptune']
```

#### Searching lists

而地球按行星的順序會降落在哪裡呢? 我們可以使用 `list.index` 的方法獲得索引值.

```python
planets.index('Earth')
# 2
```

我們可以得到他排在第三位 ( 即索引為 2 - 從 0 開始的索引).

那 "Pluto" 的索引值呢?


```python
planets.index('Pluto')


# ---------------------------------------------------------------------------
# ValueError                                Traceback (most recent call last)
# <ipython-input-30-3a8584cba91a> in <module>()
# ----> 1 planets.index('Pluto')

# ValueError: 'Pluto' is not in list
```

Oh, 不過, 因為我們剛剛上方把 "Pluto" 移除掉了, 因此他不在 list 中.

因此為了要避免出現這種意外情況, 我們可以使用 `in` 這項運算符號運算符來確定 list 中是否包含特定值:

```python
# Is Earth a planet?
"Earth" in planets
# True


# Is Calbefraques a planet?
"Calbefraques" in planets
# False
```

還有一些有趣的 list 的 methods 還沒介紹到, 如果想知道更多附加在特定的 object 的 methods 或是 attributes, 我們可以調用 `help()` 在那個 object 他自己身上, 例如, `help(planets)` 就將會告訴我們所有 list 的 methods:

```python
help(planets)


# Help on list object:

# class list(object)
#  |  list() -> new empty list
#  |  list(iterable) -> new list initialized from iterable's items
#  |  
#  |  Methods defined here:
#  |  
#  |  __add__(self, value, /)
#  |      Return self+value.
#  |  
#  |  __contains__(self, key, /)
#  |      Return key in self.
#  |  
#  |  __delitem__(self, key, /)
#  |      Delete self[key].
#  |  
#  |  __eq__(self, value, /)
#  |      Return self==value.
#  |  
#  |  __ge__(self, value, /)
#  |      Return self>=value.
#  |  
#  |  __getattribute__(self, name, /)
#  |      Return getattr(self, name).
#  |  
#  |  __getitem__(...)
#  |      x.__getitem__(y) <==> x[y]
#  |  
#  |  __gt__(self, value, /)
#  |      Return self>value.
#  |  
#  |  __iadd__(self, value, /)
#  |      Implement self+=value.
#  |  
#  |  __imul__(self, value, /)
#  |      Implement self*=value.
#  |  
#  |  __init__(self, /, *args, **kwargs)
#  |      Initialize self.  See help(type(self)) for accurate signature.
#  |  
#  |  __iter__(self, /)
#  |      Implement iter(self).
#  |  
#  |  __le__(self, value, /)
#  |      Return self<=value.
#  |  
#  |  __len__(self, /)
#  |      Return len(self).
#  |  
#  |  __lt__(self, value, /)
#  |      Return self<value.
#  |  
#  |  __mul__(self, value, /)
#  |      Return self*value.
#  |  
#  |  __ne__(self, value, /)
#  |      Return self!=value.
#  |  
#  |  __new__(*args, **kwargs) from builtins.type
#  |      Create and return a new object.  See help(type) for accurate signature.
#  |  
#  |  __repr__(self, /)
#  |      Return repr(self).
#  |  
#  |  __reversed__(...)
#  |      L.__reversed__() -- return a reverse iterator over the list
#  |  
#  |  __rmul__(self, value, /)
#  |      Return value*self.
#  |  
#  |  __setitem__(self, key, value, /)
#  |      Set self[key] to value.
#  |  
#  |  __sizeof__(...)
#  |      L.__sizeof__() -- size of L in memory, in bytes
#  |  
#  |  append(...)
#  |      L.append(object) -> None -- append object to end
#  |  
#  |  clear(...)
#  |      L.clear() -> None -- remove all items from L
#  |  
#  |  copy(...)
#  |      L.copy() -> list -- a shallow copy of L
#  |  
#  |  count(...)
#  |      L.count(value) -> integer -- return number of occurrences of value
#  |  
#  |  extend(...)
#  |      L.extend(iterable) -> None -- extend list by appending elements from the iterable
#  |  
#  |  index(...)
#  |      L.index(value, [start, [stop]]) -> integer -- return first index of value.
#  |      Raises ValueError if the value is not present.
#  |  
#  |  insert(...)
#  |      L.insert(index, object) -- insert object before index
#  |  
#  |  pop(...)
#  |      L.pop([index]) -> item -- remove and return item at index (default last).
#  |      Raises IndexError if list is empty or index is out of range.
#  |  
#  |  remove(...)
#  |      L.remove(value) -> None -- remove first occurrence of value.
#  |      Raises ValueError if the value is not present.
#  |  
#  |  reverse(...)
#  |      L.reverse() -- reverse *IN PLACE*
#  |  
#  |  sort(...)
#  |      L.sort(key=None, reverse=False) -> None -- stable sort *IN PLACE*
#  |  
#  |  ----------------------------------------------------------------------
#  |  Data and other attributes defined here:
#  |  
#  |  __hash__ = None
```

上面的列表中有很多名稱看起來很奇怪的方法, 例如 `__eq__` 和 `__iadd__`, 不過現在不用擔心這些, ( 我們可能不會直接調用到這些方法, 但是, 當我們使用索引或比較運算符這類的語法時, 它們會在後台被調用到 ), 而另外最有趣的方法則在列表的最後 ( `append`, `clear`, `copy` 等 ).


### Tuples

Tupples 幾乎和 list 相同, 他們只有兩方面不同.

1. 創建它們的語法使用括號 () 而不是方括號 []


```python
t = (1, 2, 3)
```

```python
t = 1, 2, 3 # equivalent to above 等同於上方
t
# 1, 2, 3
```

2. 他們不能被修改 ( 他們是不可變的 )

```python
t[0] = 100


# ---------------------------------------------------------------------------
# TypeError                                 Traceback (most recent call last)
# <ipython-input-36-e6cf7836e708> in <module>()
# ----> 1 t[0] = 100

# TypeError: 'tuple' object does not support item assignment
```

Tuples 通常用於那些有多個返回值的函數.

例如, float 這項 object 的方法 `as_integer_ratio()`, 會以 tuple 的形式返回一組分子和分母:


```python
x = 0.125
x.as_integer_ratio()
# (1, 8)
```

這些有多個回傳值可以分別分配如下:


```python
numerator, denominator = x.as_integer_ratio()
print(numerator / denominator)
# 0.125
```

最後, 我們對於交換兩個變量的經典 Stupid Python Trick™ 有了一些了解了

```python
a = 1
b = 0
a, b = b, a
print(a, b)


# 0 1
```