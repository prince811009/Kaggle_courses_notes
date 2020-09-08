# Strings and Dictionaries

這邊將會介紹基本的 Python 型態: strings 和 dictionaries.

## Strings

Python 語言真正發揮作用的地方之一是 string 的操作,  因此這邊將會介紹一些內置函數的字串方法以及格式化的操作.

類似這種的字串操作模式, 通常是在 data science 的工作背景下出現, 並且在這種情況下是 Python 的一大優勢.

### String syntax

字串語法, 我們已經在之前的課程中看到許多關於字串的範例, 不過這邊再簡要概述一下, Python 中的字串可以使用單引號或雙引號定義, 它們在功能上是等效的.

```python
x = 'Pluto is a planet'
y = "Pluto is a planet"
x == y


# True
```

如果我們的字串包含單引號, 則使用雙引號會很方便.

同樣, 如果我們的字串符號包含雙引號, 則使用單引號會容易得多:

```python
print("Pluto's a planet!")
print('My dog is named "Pluto"')


# Pluto's a planet!
# My dog is named "Pluto"
```

如果我們嘗試將單引號的字串放在同樣是單引號的字串中, Python 將會感到很困惑:

```python
'Pluto's a planet!'


#   File "<ipython-input-3-a43631749f52>", line 1
#     'Pluto's a planet!'
#            ^
# SyntaxError: invalid syntax
```

因此我們可以通過使用反斜線 "跳脫字元" 來解決此問題.

```python
'Pluto\'s a planet!'


# "Pluto's a planet!"
```

下方的表格總結了反斜線符號的一些重要用法.

| What you type... | What you get | example                 | print(example)       |
| ---------------- | ------------ | ----------------------- | -------------------- |
| \'               | '            | 'What\'s up?'           | what's up?           |
| \"               | "            | "That's \"cool\""       | That's "cool"        |
| \\               | \            | "Look, a mountain: /\\" | Look, a mountain: /\ |
| \n               |              | "1\n2 3"                | 1                    |
|                  |              |                         | 23                   |


最後一個序列 `\n` 代表換行, 它讓 Python 從新的一航開始.


```python
hello = "hello\nworld"
print(hello)


# hello
# world
```

此外, Python 三個引號的這種表示語法, 讓我們可以按照實際情況包括換行符 ( 只需按 Enter 鍵, 而不使用特殊的 `\n` 跳脫字元 ). 我們之前已經在字串文檔 (docstrings) 中看過這個用法, 可以用在記錄函數, 不過我們其實可以用在任何我們想要定義字串的地方.

```python
triplequoted_hello = """hello
world"""
print(triplequoted_hello)
triplequoted_hello == hello


# hello
# world


# True
```

`print` 這項 function 會自動添加換成符號, 除非我們具體指定給 `end` 這個關鍵字參數一個默認值 來取代 `'\n'` 的值, 否則 `print()` 函數就會自動添加換行符號:

```python
print("hello")
print("world")
print("hello", end='')
print("world", end='')


# hello
# world
# helloworld
```

### Strings are sequences

字串為序列, 字串可以把它想成是字串序列. 幾乎之前我們看過可以對 list 的操作, 我們也可以對字串執行.

```python
# Indexing
planet = 'Pluto'
planet[0]


# 'P'
```

```python
# Slicing
planet[-3:]


# 'uto'
```

```python
# How long is the string?
len(planet)


# 5
```

```python
# Yes, we can even loop over them
[char+'! ' for char in planet]


# ['P! ', 'l! ', 'u! ', 't! ', 'o! ']
```

但是與 list 主要不同的地方在於, 他們是不可變的, 我們無法修改它們.

```python
planet[0] = 'B'
# planet.append doesn't work either


# ---------------------------------------------------------------------------
# TypeError                                 Traceback (most recent call last)
# <ipython-input-12-6ca42463b9f9> in <module>
# ----> 1 planet[0] = 'B'
#       2 # planet.append doesn't work either

# TypeError: 'str' object does not support item assignment
```

### String methods

字串的方法, 和 `list` 相同, `str` 這個類性也有很多很有用的方法, 這邊會有一些範例.

```python
# All CAPS
claim = "Pluto is a planet!"
claim.upper()


# 'PLUTO IS A PLANET!'
```

```python
# all lowercase
claim.lower()


#'pluto is a planet!'
```

```python
#Searching for the first index of a substring
claim.index('plan')


# 11
```

```python
claim.startswith(planet)


## True
```

```python
claim.endwith('dwarf planet')


# False
```

#### Going between strings and lists: .split() and .join()

在字串和列表之間: .split() 和 .join()

`str.split()` 能將字串轉換為較小的字串列表, 預設是在空白處的地方分開, 這對我們從一個很長的字串變成一串字的列表非常有幫助.

```python
word = claim.split()
word


# ['Pluto', 'is', 'a', 'planet!']
```

有時, 我們可能也想用空格之外的值來做分割:

```python
datestr = '1956-01-31'
year, month, day = datestr.split('-')


print(year, month, day)
## 1956 01 31
```

而 `str.join()` 則是帶我們到另一個方向,使用分隔符號串成一個長字串.

```python
print('/'.join([year, day, month]))


# 1956/31/01
```

```python
# Yes, we can put unicode characters right in our string literals :)
' 👏 '.join([word.upper() for word in words])
#'PLUTO 👏 IS 👏 A 👏 PLANET!'
```

#### Building strings with .format()

Python 讓我們用 `+` 這個運算符號連接字串.


```python
planet + ',we miss you.'


# 'Pluto, we miss you.'
```

如果我們要拋出任何非字串的對象 , 我們必須小心的對他們調用 `str()`.

```python
position = 9
planet + ", you'll always be the " + position + "th planet to me."


# ---------------------------------------------------------------------------
# TypeError                                 Traceback (most recent call last)
# <ipython-input-23-73295f9638cc> in <module>
#       1 position = 9
# ----> 2 planet + ", you'll always be the " + position + "th planet to me."

# TypeError: must be str, not int
```


```python
planet + ", you'll always be the " + (position) + "th planet to me."


# "Pluto, you'll always be the 9th planet to me."
```

不過這也因此變得更加難以閱讀和煩人, 因此使用 `str.format()` 變進行了很好的協助.

```python
"{}, you'll always be the {}th planet to me.".format(planet, position)


# "Pluto, you'll always be the 9th planet to me."
```

如此一來看起來乾淨多了! 我們在要 "格式化的字串" 上調用 `.format()` 這個函數, 其中要插入的值用 `{}` 佔位符號來表示.

而且我們可以注意到, 我們甚至需要調用 `str()` 就可以將 `position` 換成整數, `.format()` 已經為我們解決了這一個問題.

如果以上這些都是 `.format()` 所做的, 那麼真的是會非常有用. 不過事實證明, 它還可以做的更多, 下面再來一個範例:

```python
pluto_mass = 1.303 * 10**22
earth_mass = 5.9722 * 10**24
population = 52910390
#         2 decimal points( 小數點兩位 )   3 decimal points( 小數點三位 ), format as percent( 格式為百分比)     separate with commas( 中間用逗點分隔 )
"{} weighs about {:.2} kilograms ({:.3%} of Earth's mass). It is to {:,} Plutonians.".format(
    planet, pluto_mass, pluto_mass / earth_mass, population,
)


# "Pluto weighs about 1.3e+22 kilograms (0.218% of Earth's mass). It is home to 52,910,390 Plutonians."
```


```python
# Referring to format() arguments by index, starting from 0
s = """Pluto's a {0}.
No, it's a {1}.
{0}!
{1}!""".format('planet', 'dwarf planet')
print(s)


# Pluto's a planet.
# No, it's a dwarf planet.
# planet!
# dwarf planet!
```

我們可能已經可以在 `str.format` 上寫了一本簡短書了, 不過我們先停在這邊, 並且推薦我們可以進一步閱讀的資源 [pyformat.info](https://pyformat.info/) 和 [官方文件](https://docs.python.org/3/library/string.html#formatstrings).


## Dictionaries

Dictionaries 是 python 內建的資料結構, 以 key 映射對應的 value.


```python
numbers = {'one':1, 'two':2, 'three':3}
```

在這個例子中, 這裡的 `'one'`, `'two'` 和 `'three'` 表示為 "key", 而 1, 2, 3 是他們對應的值.

我們可以透過使用方括號的語法來訪問值, 這種方式類似於索引到 lists 和 strings.

```python
numbers['one']


# 1
```

我們也可以用相同的語法來增加另一個 key, value 對.

```python
numbers['eleven'] = 11
numbers


# {'one': 1, 'two': 2, 'three': 3, 'eleven': 11}
```

又或者, 對一個已經存在的 key 修改其 value

```python
numbers['one'] = 'Pluto'
numbers


# {'one': 'Pluto', 'two': 2, 'three': 3, 'eleven': 11}
```

Python 具有 "dictionary comprehensions", 這跟我們之前提到的 "list comprehensions" 相同的語法.

```python
planets = ['Mercury', 'Venus', 'Earth', 'Mars', 'Jupiter', 'Saturn', 'Uranus', 'Neptune']
planet_to_initial = {planet: planet[0] for planet in planets}
planet_to_initial


# {'Mercury': 'M',
#  'Venus': 'V',
#  'Earth': 'E',
#  'Mars': 'M',
#  'Jupiter': 'J',
#  'Saturn': 'S',
#  'Uranus': 'U',
#  'Neptune': 'N'}
```

這裡的 `in` 運算符號告訴我們什麼是 dictionary 的 key.

```python
'Saturn' in planet_to_initial


#True
```

```python
'Betelgeuse' in planet_to_initial


#False
```

一個 for loop 循環會將 dictionary 的 key 做一次循環

```python
for k in numbers:
    print("{} = {}".format(k, numbers[k]))


# one = Pluto
# two = 2
# three = 3
# eleven = 11
```

我們可以分別透過 `dict.keys()` 和 `dict.values` 訪問所有 key 和所有值的集合.

```python
# Get all the initials, sort them alphabetically, and put them in a space-separated string.
# 用來獲取所有的首字母縮寫, 按照字母順序, 接著以空格當作分隔符組成字串

' '.join(sorted(planet_to_initial.values()))


# 'E J M M N S U V'
```

`dict.items()` 這項函數很有用, 可以讓我們同時迭代 dictionary 的 key 和 value.( 在 Python 的行話中, "item" 指的是 key, value 對).

```python
for planet, initial in planet_to_initial.items():
    print("{} begins with \"{}\"".formate(planet.rjust(10), initial))

# rjust() 表示向右對齊, 並使用空格填充長度


#    Mercury begins with "M"
#      Venus begins with "V"
#      Earth begins with "E"
#       Mars begins with "M"
#    Jupiter begins with "J"
#     Saturn begins with "S"
#     Uranus begins with "U"
#    Neptune begins with "N"
```

如果想要閱讀完整的 dictionaries 的方法清單, 可以使用 `help(dict)` 或是閱讀[官方文件](https://docs.python.org/3/library/stdtypes.html#dict).

```python
help(dict)


# Help on class dict in module builtins:

# class dict(object)
#  |  dict() -> new empty dictionary
#  |  dict(mapping) -> new dictionary initialized from a mapping object's
#  |      (key, value) pairs
#  |  dict(iterable) -> new dictionary initialized as if via:
#  |      d = {}
#  |      for k, v in iterable:
#  |          d[k] = v
#  |  dict(**kwargs) -> new dictionary initialized with the name=value pairs
#  |      in the keyword argument list.  For example:  dict(one=1, two=2)
#  |  
#  |  Methods defined here:
#  |  
#  |  __contains__(self, key, /)
#  |      True if D has a key k, else False.
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
#  |  __ne__(self, value, /)
#  |      Return self!=value.
#  |  
#  |  __new__(*args, **kwargs) from builtins.type
#  |      Create and return a new object.  See help(type) for accurate signature.
#  |  
#  |  __repr__(self, /)
#  |      Return repr(self).
#  |  
#  |  __setitem__(self, key, value, /)
#  |      Set self[key] to value.
#  |  
#  |  __sizeof__(...)
#  |      D.__sizeof__() -> size of D in memory, in bytes
#  |  
#  |  clear(...)
#  |      D.clear() -> None.  Remove all items from D.
#  |  
#  |  copy(...)
#  |      D.copy() -> a shallow copy of D
#  |  
#  |  fromkeys(iterable, value=None, /) from builtins.type
#  |      Returns a new dict with keys from iterable and values equal to value.
#  |  
#  |  get(...)
#  |      D.get(k[,d]) -> D[k] if k in D, else d.  d defaults to None.
#  |  
#  |  items(...)
#  |      D.items() -> a set-like object providing a view on D's items
#  |  
#  |  keys(...)
#  |      D.keys() -> a set-like object providing a view on D's keys
#  |  
#  |  pop(...)
#  |      D.pop(k[,d]) -> v, remove specified key and return the corresponding value.
#  |      If key is not found, d is returned if given, otherwise KeyError is raised
#  |  
#  |  popitem(...)
#  |      D.popitem() -> (k, v), remove and return some (key, value) pair as a
#  |      2-tuple; but raise KeyError if D is empty.
#  |  
#  |  setdefault(...)
#  |      D.setdefault(k[,d]) -> D.get(k,d), also set D[k]=d if k not in D
#  |  
#  |  update(...)
#  |      D.update([E, ]**F) -> None.  Update D from dict/iterable E and F.
#  |      If E is present and has a .keys() method, then does:  for k in E: D[k] = E[k]
#  |      If E is present and lacks a .keys() method, then does:  for k, v in E: D[k] = v
#  |      In either case, this is followed by: for k in F:  D[k] = F[k]
#  |  
#  |  values(...)
#  |      D.values() -> an object providing a view on D's values
#  |  
#  |  ----------------------------------------------------------------------
#  |  Data and other attributes defined here:
#  |  
#  |  __hash__ = None
```
