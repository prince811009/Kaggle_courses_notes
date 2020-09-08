# Working with External Libraries

在這段課程中, 我們將要來討論 Python 的 "import", 提供一些使用不熟悉的 libraries 的技巧 ( 以及其返回的 object), 並且深入探討 Python 的精髓以討論 "operator overloading".

## Imports

到目前為止, 我們已經討論了該語言內置的類型和函數.

但是關於 Python 最棒的事情之一 ( 尤其如果你是一名數據科學家 ), 就是這些為 python 編寫的大量高質量的自定義庫 (libaries).

其中一些 libaries 位於 "standard libary" 中, 這意味著我們可以在任何運行 Python 的地方找到他們. 即使我們不是總是和 Python 一起運作, 我們也可以輕鬆的增加其他 libraties.

無論哪種方式, 我們都會透過 "import" 來運作.

我們將透過從標準庫中導入 math 開始我們的範例.

```python
import math

print("It's math! It has type {}".format(type(math)))


# It's math! It has type <class 'module'>
```

`math` 是一個模組 (module), module 只是其他人定義的變數及何 ( 也可以稱為 namespace). 我們可以使用內置函數 `dir()` 查看 `math` 中的所有名稱.

```python
print(dir(math))


# ['__doc__', '__file__', '__loader__', '__name__', '__package__', '__spec__', 'acos', 'acosh', 'asin', 'asinh', 'atan', 'atan2', 'atanh', 'ceil', 'copysign', 'cos', 'cosh', 'degrees', 'e', 'erf', 'erfc', 'exp', 'expm1', 'fabs', 'factorial', 'floor', 'fmod', 'frexp', 'fsum', 'gamma', 'gcd', 'hypot', 'inf', 'isclose', 'isfinite', 'isinf', 'isnan', 'ldexp', 'lgamma', 'log', 'log10', 'log1p', 'log2', 'modf', 'nan', 'pi', 'pow', 'radians', 'sin', 'sinh', 'sqrt', 'tan', 'tanh', 'tau', 'trunc']
```

我們可以使用點語法 (dot syntax) 來訪問這些變數, 其中一些引用了簡單的值, 例如 `math.pi`:

```python
print("pt to 4 significant digits = {:.4}".format(math.pi))


# pi to 4 significant digits = 3.142
```

不過我們大部分在 module 中發現的是函數, 例如 `math.log`:

```python
math.log(32, 2)


# 5.0
```

這邊同樣, 如果我們不知道 `math.log` 的運作, 我們可以調用 `help()`:

```python
help(math.log)


# Help on built-in function log in module math:

# log(...)
#     log(x[, base])
    
#     Return the logarithm of x to the given base.
#     If the base not specified, returns the natural logarithm (base e) of x.
```

我們也可以在 module 本身上調用 `help()`, 這將為我們提供模組中所有 functions 和 values 的組合文檔 ( 以及模組的高級說明 ).

```python
help(math)


# Help on module math:

# NAME
#     math

# MODULE REFERENCE
#     https://docs.python.org/3.6/library/math
    
#     The following documentation is automatically generated from the Python
#     source files.  It may be incomplete, incorrect or include features that
#     are considered implementation detail and may vary between Python
#     implementations.  When in doubt, consult the module reference at the
#     location listed above.

# DESCRIPTION
#     This module is always available.  It provides access to the
#     mathematical functions defined by the C standard.

# FUNCTIONS
#     acos(...)
#         acos(x)
        
#         Return the arc cosine (measured in radians) of x.
    
#     acosh(...)
#         acosh(x)
        
#         Return the inverse hyperbolic cosine of x.
    
#     asin(...)
#         asin(x)
        
#         Return the arc sine (measured in radians) of x.
    
#     asinh(...)
#         asinh(x)
        
#         Return the inverse hyperbolic sine of x.
    
#     atan(...)
#         atan(x)
        
#         Return the arc tangent (measured in radians) of x.
    
#     atan2(...)
#         atan2(y, x)
        
#         Return the arc tangent (measured in radians) of y/x.
#         Unlike atan(y/x), the signs of both x and y are considered.
    
#     atanh(...)
#         atanh(x)
        
#         Return the inverse hyperbolic tangent of x.
    
#     ceil(...)
#         ceil(x)
        
#         Return the ceiling of x as an Integral.
#         This is the smallest integer >= x.
    
#     copysign(...)
#         copysign(x, y)
        
#         Return a float with the magnitude (absolute value) of x but the sign 
#         of y. On platforms that support signed zeros, copysign(1.0, -0.0) 
#         returns -1.0.
    
#     cos(...)
#         cos(x)
        
#         Return the cosine of x (measured in radians).
    
#     cosh(...)
#         cosh(x)
        
#         Return the hyperbolic cosine of x.
    
#     degrees(...)
#         degrees(x)
        
#         Convert angle x from radians to degrees.
    
#     erf(...)
#         erf(x)
        
#         Error function at x.
    
#     erfc(...)
#         erfc(x)
        
#         Complementary error function at x.
    
#     exp(...)
#         exp(x)
        
#         Return e raised to the power of x.
    
#     expm1(...)
#         expm1(x)
        
#         Return exp(x)-1.
#         This function avoids the loss of precision involved in the direct evaluation of exp(x)-1 for small x.
    
#     fabs(...)
#         fabs(x)
        
#         Return the absolute value of the float x.
    
#     factorial(...)
#         factorial(x) -> Integral
        
#         Find x!. Raise a ValueError if x is negative or non-integral.
    
#     floor(...)
#         floor(x)
        
#         Return the floor of x as an Integral.
#         This is the largest integer <= x.
    
#     fmod(...)
#         fmod(x, y)
        
#         Return fmod(x, y), according to platform C.  x % y may differ.
    
#     frexp(...)
#         frexp(x)
        
#         Return the mantissa and exponent of x, as pair (m, e).
#         m is a float and e is an int, such that x = m * 2.**e.
#         If x is 0, m and e are both 0.  Else 0.5 <= abs(m) < 1.0.
    
#     fsum(...)
#         fsum(iterable)
        
#         Return an accurate floating point sum of values in the iterable.
#         Assumes IEEE-754 floating point arithmetic.
    
#     gamma(...)
#         gamma(x)
        
#         Gamma function at x.
    
#     gcd(...)
#         gcd(x, y) -> int
#         greatest common divisor of x and y
    
#     hypot(...)
#         hypot(x, y)
        
#         Return the Euclidean distance, sqrt(x*x + y*y).
    
#     isclose(...)
#         isclose(a, b, *, rel_tol=1e-09, abs_tol=0.0) -> bool
        
#         Determine whether two floating point numbers are close in value.
        
#            rel_tol
#                maximum difference for being considered "close", relative to the
#                magnitude of the input values
#             abs_tol
#                maximum difference for being considered "close", regardless of the
#                magnitude of the input values
        
#         Return True if a is close in value to b, and False otherwise.
        
#         For the values to be considered close, the difference between them
#         must be smaller than at least one of the tolerances.
        
#         -inf, inf and NaN behave similarly to the IEEE 754 Standard.  That
#         is, NaN is not close to anything, even itself.  inf and -inf are
#         only close to themselves.
    
#     isfinite(...)
#         isfinite(x) -> bool
        
#         Return True if x is neither an infinity nor a NaN, and False otherwise.
    
#     isinf(...)
#         isinf(x) -> bool
        
#         Return True if x is a positive or negative infinity, and False otherwise.
    
#     isnan(...)
#         isnan(x) -> bool
        
#         Return True if x is a NaN (not a number), and False otherwise.
    
#     ldexp(...)
#         ldexp(x, i)
        
#         Return x * (2**i).
    
#     lgamma(...)
#         lgamma(x)
        
#         Natural logarithm of absolute value of Gamma function at x.
    
#     log(...)
#         log(x[, base])
        
#         Return the logarithm of x to the given base.
#         If the base not specified, returns the natural logarithm (base e) of x.
    
#     log10(...)
#         log10(x)
        
#         Return the base 10 logarithm of x.
    
#     log1p(...)
#         log1p(x)
        
#         Return the natural logarithm of 1+x (base e).
#         The result is computed in a way which is accurate for x near zero.
    
#     log2(...)
#         log2(x)
        
#         Return the base 2 logarithm of x.
    
#     modf(...)
#         modf(x)
        
#         Return the fractional and integer parts of x.  Both results carry the sign
#         of x and are floats.
    
#     pow(...)
#         pow(x, y)
        
#         Return x**y (x to the power of y).
    
#     radians(...)
#         radians(x)
        
#         Convert angle x from degrees to radians.
    
#     sin(...)
#         sin(x)
        
#         Return the sine of x (measured in radians).
    
#     sinh(...)
#         sinh(x)
        
#         Return the hyperbolic sine of x.
    
#     sqrt(...)
#         sqrt(x)
        
#         Return the square root of x.
    
#     tan(...)
#         tan(x)
        
#         Return the tangent of x (measured in radians).
    
#     tanh(...)
#         tanh(x)
        
#         Return the hyperbolic tangent of x.
    
#     trunc(...)
#         trunc(x:Real) -> Integral
        
#         Truncates x to the nearest Integral toward 0. Uses the __trunc__ magic method.

# DATA
#     e = 2.718281828459045
#     inf = inf
#     nan = nan
#     pi = 3.141592653589793
#     tau = 6.283185307179586

# FILE
#     /opt/conda/lib/python3.6/lib-dynload/math.cpython-36m-x86_64-linux-gnu.so
```

### Other import syntax

如果我們知道我們會很經常的在 `math` 中使用函數, 我們可以使用較短的別名將其 import 以節省一些輸入 ( 儘管目前這個情況下, "math" 已經很短了).

```python
import math as mt
mt.pi


# 3.141592653589793
```

#### 小提示

可能我們已經看過一些流行的 libraries ( 例如 Pandas, Nump, Tensorflow 或 Matplotlib) 執行這些代碼, 例如, `import numpy as np and import pandas as pd 這種常見的樣子.


其中的 `as` 簡單重命名了我們 import 的 module, 他等同於執行以下操作: 


```python
import math
mt = math
```

如果我們可以單獨引用 `math` module 中的所有變數不是很好嗎? 那如果我們只想引用 `pi` 而不是 `math.pi` 或 `mt.pi` 呢? 好消息是: 我們可以做到這點.

```python
from math import *
print(pi, log(32, 2))


# 3.141592653589793
```

`import * ` 使我們可以直接訪問 module 的所有變數 ( 不帶任何前綴 ).

>Bad news: some purists might grumble at you for doing this.

>Worse: they kind of have a point.

```python
from math import *
from numpy import *
print(pi, log(32, 2))


# ---------------------------------------------------------------------------
# TypeError                                 Traceback (most recent call last)
# <ipython-input-10-5045b296ad83> in <module>
#       1 from math import *
#       2 from numpy import *
# ----> 3 print(pi, log(32, 2))

# TypeError: return arrays must be of ArrayType
```

這裡就奇怪了, 但是它以前起作用的.

像這種 "start imports" 有時後可能會遇到有點怪異, 難以 debug 的情況發生.

因此像是這種情況下的問題在於, `math` 和 `numpy` 兩個模組都具有稱為 `log` 的函數, 但是它們具有不同的語義, 而且因為我們第二個才是 import `numpy`, 因此他的 `log` 複寫了原本 import `math` 的變數 `log`.

一個不錯的折衷方案是, 僅從每個模組中導入我們需要的特定內容:

```python
from math import log, pi
from numpy import asarray
```

### Submodules

子模組, 我們已經知道模組包含了可以引用函數或值的變數, 需要注意的是, 它們也可以具有引用其他模組的變數.

```python
import numpy
print("numpy.random is a", type(numpy.random))
print("it contains names such as ...",
      dir(numpy.random)[-15:]
     )


# numpy.random is a <class 'module'>
# it contains names such as... ['set_state', 'shuffle', 'standard_cauchy', 'standard_exponential', 'standard_gamma', 'standard_normal', 'standard_t', 'test', 'triangular', 'uniform', 'vonmises', 'wald', 'warnings', 'weibull', 'zipf']
```

因此, 如果我們像上方一樣 import `numpy`, 接著在 `random` "submodule" 中調用函數我們會需要兩個點.

```python
# Roll 10 dice
rolls = numpy.random.randint(low=1, height=6, size=10)
rolls


# array([4, 1, 2, 2, 1, 3, 1, 1, 5, 2])
```

## Oh the places you'll go, oh the objects you'll see

經過 6 堂課程, 我們已經是一位對 ints, floats, bools, lists, strings, and dicts 有專業的人士對吧?

即使這是真的, 也不會到此為止, 當我們在使用各種不同的 libraries 在處理特殊任務時, 我們會發現他們定義了自己的型態, 而我們也必須去學習這些. 例如, 如果我們使用了圖形庫 `matplotlib`, 則我們將會和它定義的對象 Subplots, Figures, TickMarks, 和 Annotations 這些接觸, `pandas` 則會提供我們 DataFrames 和 Series.

在這部分中, 原文想和我們分享如何使用奇怪的型態的快速生存指南.

### Three tools for understanding strange objects

理解奇怪 object 的三種工具, 在上面的單元中, 我們看到了調用 `numpy` 函數所提供給我們的 "array", 我們之前並未見過 ( 無論是不是在這個課程中 ), 但是請不要驚慌: 我們提供了三個熟悉的內置函數來幫助我們.

1. `type()` ( 指的是: 這是什麼? )

```python
type(rolls)


# numpy.ndarray
```

2. `dir()` ( 指個是: 我可以怎麼操作他?)

```python
print(dir(rolls))


# ['T', '__abs__', '__add__', '__and__', '__array__', '__array_finalize__', '__array_function__', '__array_interface__', '__array_prepare__', '__array_priority__', '__array_struct__', '__array_ufunc__', '__array_wrap__', '__bool__', '__class__', '__complex__', '__contains__', '__copy__', '__deepcopy__', '__delattr__', '__delitem__', '__dir__', '__divmod__', '__doc__', '__eq__', '__float__', '__floordiv__', '__format__', '__ge__', '__getattribute__', '__getitem__', '__gt__', '__hash__', '__iadd__', '__iand__', '__ifloordiv__', '__ilshift__', '__imatmul__', '__imod__', '__imul__', '__index__', '__init__', '__init_subclass__', '__int__', '__invert__', '__ior__', '__ipow__', '__irshift__', '__isub__', '__iter__', '__itruediv__', '__ixor__', '__le__', '__len__', '__lshift__', '__lt__', '__matmul__', '__mod__', '__mul__', '__ne__', '__neg__', '__new__', '__or__', '__pos__', '__pow__', '__radd__', '__rand__', '__rdivmod__', '__reduce__', '__reduce_ex__', '__repr__', '__rfloordiv__', '__rlshift__', '__rmatmul__', '__rmod__', '__rmul__', '__ror__', '__rpow__', '__rrshift__', '__rshift__', '__rsub__', '__rtruediv__', '__rxor__', '__setattr__', '__setitem__', '__setstate__', '__sizeof__', '__str__', '__sub__', '__subclasshook__', '__truediv__', '__xor__', 'all', 'any', 'argmax', 'argmin', 'argpartition', 'argsort', 'astype', 'base', 'byteswap', 'choose', 'clip', 'compress', 'conj', 'conjugate', 'copy', 'ctypes', 'cumprod', 'cumsum', 'data', 'diagonal', 'dot', 'dtype', 'dump', 'dumps', 'fill', 'flags', 'flat', 'flatten', 'getfield', 'imag', 'item', 'itemset', 'itemsize', 'max', 'mean', 'min', 'nbytes', 'ndim', 'newbyteorder', 'nonzero', 'partition', 'prod', 'ptp', 'put', 'ravel', 'real', 'repeat', 'reshape', 'resize', 'round', 'searchsorted', 'setfield', 'setflags', 'shape', 'size', 'sort', 'squeeze', 'std', 'strides', 'sum', 'swapaxes', 'take', 'tobytes', 'tofile', 'tolist', 'tostring', 'trace', 'transpose', 'var', 'view']
```


```python
# What am I trying to do with this dice roll data? Maybe I want the average roll, in which case the "mean" 平均數
# method looks promising...
rolls.mean()


#2.2
```


```python
# Or maybe I just want to get back on familiar ground, in which case I might want to check out "tolist"
rolls.tolis()


# [4, 1, 2, 2, 1, 3, 1, 1, 5, 2]
```

3. `help()` ( 指的是: 請告訴我更多 )

```python
# That "ravel" attribute sounds interesting. I'm a big classical music fan.
help(rolls.ravel)


# Help on built-in function ravel:

# ravel(...) method of numpy.ndarray instance
#     a.ravel([order])
    
#     Return a flattened array.
    
#     Refer to `numpy.ravel` for full documentation.
    
#     See Also
#     --------
#     numpy.ravel : equivalent function
    
#     ndarray.flat : a flat iterator on the array.
```


```python
# Okay, just tell me everything there is to know about numpy.ndarray
# (Click the "output" button to see the novel-length output)
help(rolls)
# 這邊 output 因為內容過長就不貼上來了
```

(當然, 我們也許比較喜歡閱讀[線上的文件](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.ndarray.html))

#### Operator overloading

運算符號的過載

請問以下的表達是的值是什麼呢?

```python
[3, 4, 1, 2, 2, 1] + 10


# ---------------------------------------------------------------------------
# TypeError                                 Traceback (most recent call last)
# <ipython-input-20-a2508fc27c2b> in <module>
# ----> 1 [3, 4, 1, 2, 2, 1] + 10

# TypeError: can only concatenate list (not "int") to list
```

這是什麼奇怪的問題 XD, 當然是會出現錯誤囉

那如果是這樣呢?

```python
# rolls = numpy.random.randint(low=1, high=6, size=10)
# rolls # array([4, 1, 2, 2, 1, 3, 1, 1, 5, 2])
rolls + 10


# array([14, 11, 12, 12, 11, 13, 11, 11, 15, 12])
```
