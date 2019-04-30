---
title: Python 学习笔记备忘
date: 2019-04-26 17:24:49
categories:
tags:
---

> 摘要：记录 Python 的学习笔记，是阅读《Python编程：从入门到实践》、《Python编程快速上手  让繁琐工作自动化》、《Python学习手册(第4版)》以及《Python高级编程-第2版》之后，经过有机整合而成。

<!-- more -->

## 第一个示例程序

```
print("Hello Python world!")
```

## 变量名应使用小写

## title()
- 将字符串首字母转为大写后返回
- 例子：

```
name = "ada lovelace"
print(name.title())
# 输出 Ada Lovelace
```

- 其他转化方法，全部转为大写或小写：upper()、lower()

## 制表符和换行符
- `\n`，换行符
- `\t`，制表符

## 删除空白
- `rstrip()`，删除右边空白
- `lstrip()`，删除左边空白
- `strip()`，删除两端空白

## 正确地使用单引号和双引号
在用单引号括起的字符串中，如果包含撇号，就将导致错误。这是因为这会导致 Python 将第一个单引号和撇号之间的内容视为一个字符串，进而将余下的文本视为 Python 代码，从而引发错误。

```
message = "One of Python's strengths is its diverse community."
print(message)
# 撇号位于两个双引号之间，因此 Python 解释器能够正确地理解这个字符串：One of Python's strengths is its diverse community.
```
然而，如果你使用单引号，Python将无法正确地确定字符串的结束位置：

```
message = 'One of Python's strengths is its diverse community.'
print(message)
```

## 乘方运算
使用两个乘号表示乘方运算：

```
>>> 3 ** 2
9
>>> 3 ** 3
27
>>> 10 ** 6
1000000
```

## 浮点数结果包含的小数位数可能是不确定的

```
>>> 0.2 + 0.1
0.30000000000000004
>>> 3 * 0.1
0.30000000000000004
```

## str()
- 字符串转化
- 例子：

```
age = 23
message = "Happy " + str(age) + "rd Birthday!"
print(message)
```

## 列表
- 访问列表第一个元素

```
bicycles = ['trek', 'cannondale', 'redline', 'specialized']
print(bicycles[0])
```

- 访问列表最后一个元素

```
bicycles[-1]
```

- 添加元素到末尾

```
bicycles.append('ducati')
```

- 在第二个元素前插入元素

```
bicycles.insert(1, 'ducati')
```

- 使用 del 删除元素。注意：若列表有多个同名元素，以下语句仅删除第一次出现的元素。

```
del bicycles[0]
```

- 使用无参 pop() 删除元素，并返回被删除元素。类似栈，从最后一个元素开始删除。

```
popped_bicycles = bicycles.pop()
```

- 使用带参 pop() 删除指定元素，并返回被删除元素。

```
first_owned = motorcycles.pop(0)
```

- 根据值删除元素。注意：若列表有多个同名元素，以下语句仅删除第一次出现的元素。

```
motorcycles.remove('ducati')
```

- 使用 `sort()` 对列表按字母顺序进行永久性排序。对字符串排序时，使用 ASCII 字符顺序，而不是实际的字典顺序。这意味着大写字母排在小写字母之前。因此在排序时，小写的 a 在大写的 Z 之后。如果需要按照普通的字典顺序来排序，就在 sort() 方法调用时，将关键字参数 key 设置为 `str.lower`

```
cars = ['bmw', 'audi', 'toyota', 'subaru']
cars.sort()

>>> spam = ['a', 'z', 'A', 'Z']
>>> spam.sort(key=str.lower)
>>> spam
['a', 'A', 'z', 'Z']
```

- 使用 `sort(reverse=True)` 对列表按字母逆序进行永久性排序。

```
cars = ['bmw', 'audi', 'toyota', 'subaru']
cars.sort(reverse=True)
```

- 使用 `sorted()` 对列表进行临时排序，保留列表元素原来的排列顺序，也可向 `sorted()` 传递参数 `reverse=True`。

```
cars = ['bmw', 'audi', 'toyota', 'subaru']
print(sorted(cars))
```

- 永久性逆序列表

```
cars = ['bmw', 'audi', 'toyota', 'subaru']
cars.reverse()
print(cars)
```

- 使用 `len()` 确定列表长度

```
>>> cars = ['bmw', 'audi', 'toyota', 'subaru']
>>> len(cars)
4
```

- 遍历列表

```
magicians = ['alice', 'david', 'carolina']
for magician in magicians:
    print(magician)
```

## 数值列表
- 使用 `range()` 数值序列或使用 `list(range(1,5))` 转为数值列表。需要注意输出的上界，例子：

```
for value in range(1,5):
    print(value)
# 输出 1，2，3，4
```

- 数值列表的统计计算

```
>>> digits = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]
>>> min(digits)
0
>>> max(digits)
9
>>> sum(digits)
45
```

## 列表解析
- 创建平方数列表

```
squares = [value**2 for value in range(1,11)]
print(squares)
# 输出 [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```

## 列表切片
- 例子：

```
players = ['charles', 'martina', 'michael', 'florence', 'eli']
print(players[0:3])
# 输出 ['charles', 'martina', 'michael']
```

- 若缺省下界，则默认以起始位置作为下界；同理，若缺省上界，则默认以结束位置作为上界。
- 从最后开始取元素可以使用 `players[-3:]`，表示返回最后三个元素。

## 复制列表
即创建一个包含整个列表的切片，同时省略起始索引和终止索引（[:]）。

```
my_foods = ['pizza', 'falafel', 'carrot cake']
friend_foods = my_foods[:]
```

## 元组
元组是只读的，因此不能给元组的元素赋值，只能够改变元组的指向。

```
dimensions = (200, 50)
```

## 要判断两个值是否不等，可使用（!=）

```
requested_topping = 'mushrooms'
if requested_topping != 'anchovies':
    print("Hold the anchovies!")  
```

## 检查特定值是否包含在列表中

```
>>> requested_toppings = ['mushrooms', 'onions', 'pineapple']
>>> 'mushrooms' in requested_toppings
True
>>> 'pepperoni' in requested_toppings
False
```

## 检查特定值是否不包含在列表中

```
banned_users = ['andrew', 'carolina', 'david'] user = 'marie'  
if user not in banned_users:     
    print(user.title() + ", you can post a response if you wish.")
# 输出 Marie, you can post a response if you wish.
```

## 确定列表不是空的

```
requested_toppings = []

if requested_toppings:
    for requested_topping in requested_toppings:
        print("Adding " + requested_topping + ".")
        print("\nFinished making your pizza!")
    else:
        print("Are you sure you want a plain pizza?")
# 输出 Are you sure you want a plain pizza?
```

## 为字典添加键值对

```
alien_0 = {'color': 'green', 'points': 5}
alien_0['x_position'] = 0
alien_0['y_position'] = 25
print(alien_0)
# 输出 {'color': 'green', 'points': 5, 'y_position': 25, 'x_position': 0}
```

## 删除字典中的键值对

```
alien_0 = {'color': 'green', 'points': 5}
print(alien_0)
del alien_0['points']
```

## 遍历字典
- 遍历所有键值对

```
for key, value in user_0.items():
    print("\nKey: " + key)
    print("Value: " + value)
```

- 遍历所有键

```
for name in favorite_languages.keys():
    print(name.title())
```

遍历字典时，会默认遍历所有的键，因此，如果将上述代码中的 `for name in favorite_ languages.keys():` 替换为 `for name in favorite_languages:`，输出将不变。
- 按顺序遍所有键。要以特定的顺序返回元素，一种办法是在for循环中对返回的键进行排序。为此，可使用 `sorted()` 来获得按特定顺序排列的键列表的副本：

```
favorite_languages = {
    'jen': 'python',
    'sarah': 'c',
    'edward': 'ruby',
    'phil': 'python',
}

for name in sorted(favorite_languages.keys()):
    print(name.title() + ", thank you for taking the poll.")
```

- 遍历所有值

```
for language in favorite_languages.values():
    print(language.title())
```

这种做法提取字典中所有的值，而没有考虑是否重复。涉及的值很少时，这也许不是问题， 但如果被调查者很多，终的列表可能包含大量的重复项。为剔除重复项，可使用集合（set）。 集合类似于列表，但每个元素都必须是独一无二的：

```
for language in set(favorite_languages.values()):
    print(language.title())
```

## 函数的位置实参、关键字实参
- 位置实参。必须将函数调用中的每个实参都关联到函数定义中的一个形参。为此，简单的关联方式是基于实参的顺序，这种关联方式被称为位置实参。位置实参的顺序很重要，如果实参的顺序不正确，结果可能出乎意料。
- 关键字实参是传递给函数的名称和值对。直接在实参中将名称和值关联起来了，因此向函数传递实参时不会混淆。关键字实参无需考虑函数调用中的实参顺序，还清楚地指出了函数调用中各个值的用途。

```
def describe_pet(animal_type, pet_name):
    print("\nI have a " + animal_type + ".")
    print("My " + animal_type + "'s name is " + pet_name.title() + ".")

describe_pet(animal_type='hamster', pet_name='harry')
```

## 「类真」和「类假」
数据类型中的某些值，条件认为它们等价于 True 或 False。在用于条件时，0、0.0、''（空字符串）被认为是 False，其他值被认为是 True。例子：
```
numList = []

if numList:
    print(len(numList))
else:
    print("no")
```

## range()
该方法最多传入 3 个参数：range(a,b,c)，取值范围 [a,b)，步长 c。例如：`numList = list(range(1, 11, 2))`，赋值 [1, 3, 5, 7, 9]

## 内建函数
- random
`random.randint()` 函数调用求值为传递给它的两个整数之间的一个随机整数。

```
import random
    for i in range(5):
    print(random.randint(1, 10))
```

- sys
调用 `sys.exit()` 函数，可以让程序终止或退出。

```
import sys

while True:
    print('Type exit to exit.')
    response = input()
    if response == 'exit':
        sys.exit()
    print('You typed ' + response + '.')
```

## None 值
在 Python 中有一个值称为 None，它表示没有值。None 是 NoneType 数据类型的唯一值（其他编程语言可能称这个值为 null、nil 或 undefined）。就像布尔值 True 和 False 一样，None 必须大写首字母 N。

在幕后，对于所有没有 return 语句的函数定义，Python 都会在末尾加上 return None。这类似于 while 或 for 循环隐式地以 continue 语句结尾。而且，如果使用不带值的 return 语句（也就是只有 return 关键字本身），那么就返回 None。

## global 语句
如果需要在一个函数内修改全局变量，就使用 global 语句。如果在函数的顶部有 global eggs 这样的代码，它就告诉 Python，在这个函数中，eggs 指的是全局变
量。

有 4 条法则，来区分一个变量是处于局部作用域还是全局作用域：
- 如果变量在全局作用域中使用（即在所有函数之外），它就总是全局变量。
- 如果在一个函数中，有针对该变量的global 语句，它就是全局变量。
- 否则，如果该变量用于函数中的赋值语句，它就是局部变量。
- 但是，如果该变量没有用在赋值语句中，它就是全局变量。

## 多重赋值
多重赋值技巧是一种快捷方式，让你在一行代码中，用列表中的值为多个变量赋值。所以不必像这样：

```
>>> cat = ['fat', 'black', 'loud']
>>> size = cat[0]
>>> color = cat[1]
>>> disposition = cat[2]
```

而是输入下面的代码：

```
>>> size, color, disposition = ['fat', 'black', 'loud']
```

变量的数目和列表的长度必须严格相等，否则 Python 将给出 ValueError

## 用 index() 方法在列表中查找值
可以传入一个值，如果该值存在于列表中，就返回它的下标。如果该值不在列表中，Python 就报 ValueError

## 用 append() 和 insert() 方法在列表中添加值
的 append() 方法将参数添加到列表末尾。insert() 方法可以在列表任意下标处插入一个值。insert() 方法的第一个参数是新值的下标，第二个参数是要插
入的新值。

## 用 list() 和 tuple() 函数来转换类型
函数 list() 和 tuple() 将返回传递给它们的值的列表和元组版本。

```
>>> tuple(['cat', 'dog', 5])
('cat', 'dog', 5)
>>> list(('cat', 'dog', 5))
['cat', 'dog', 5]
>>> list('hello')
['h', 'e', 'l', 'l', 'o']
```

## copy 模块的 copy() 和 deepcopy() 函数

```
>>> import copy
>>> spam = ['A', 'B', 'C', 'D']
>>> cheese = copy.copy(spam)
>>> cheese[1] = 42
>>> spam
['A', 'B', 'C', 'D']
>>> cheese
['A', 42, 'C', 'D']
```




