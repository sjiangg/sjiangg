## Python 

*注释* 是任何存在于 `#` 号右侧的文字，其主要用作写给程序读者看的笔记。

举个例子：

```python
print('hello world') #注意到 print 是一个函数
```

###### 数字

主要分为两种类型——整数（Integers）与浮点数（Floats）。

有关整数的例子即 `2`，它只是一个整数。

有关浮点数（Floating Point Numbers，在英文中也会简写为 *floats* ）的例子是 `3.23` 或 `52.3E-4`。其中，`E` 表示 10 的幂。在这里，`52.3E-4` 表示 `52.3 * 10^-4`。



##### 字符串

一串字符串（String）是 *字符（Characters）* 的 *序列（Sequence）*。基本上，字符串就是一串词汇。

你将会在几乎所有你撰写的 Python 程序中使用字符串.

###### 单引号双引号

单引号与双引号相同

你可以使用单引号来指定字符串，例如 `'将我这样框进来'` 或 `"Quote me on this"` 。

###### 三引号 {#triple-quotes}

你可以通过使用三个引号——`"""` 或 `'''` 来指定多行字符串。你可以在三引号之间自由地使用单引号与双引号。来看看这个例子：

```python
'''这是一段多行字符串。这是它的第一行。
This is the second line.
"What's your name?," I asked.
He said "Bond, James Bond."
'''
```

###### Docstring 文档字符串

在函数的第一个逻辑行的字符串是这个函数的 文档字符串 。

文档字符串的惯例是一个多行字符串，它的首行以大写字母开始. 

In Python, the docstring for a code object (a module, class, or function) is the first statement of that code object, immediately following the definition (the 'def' or 'class' statement). 

你可以使用`__doc__`（注意双下划线）调用`printMax`函数的文档字符串属性（属于函数的名称）。请记住Python把 每一样东西 都作为对象，包括这个函数。





###### 字符串<u>是不可变的</u>

###### 格式化方法

有时候我们会想要从其他信息中构建字符串。用 `format()` 

将以下内容保存为文件 `str_format.py` ：

```python
age = 20
name = 'Swaroop'

print('{0} was {1} years old when he wrote this book'.format(name, age))

#数字只是一个可选选项
print('{} was {} years old when he wrote this book'.format(name, age))

```

输出：

```python
$ python str_format.py
Swaroop was 20 years old when he wrote this book
```

```python
# 对于浮点数 '0.333' 保留小数点(.)后三位
print('{0:.3f}'.format(1.0/3))

# 使用下划线填充文本，并保持文字处于中间位置
# 使用 (^) 定义 '___hello___'字符串长度为 11
print('{0:_^11}'.format('hello'))
# 基于关键词输出 'Swaroop wrote A Byte of Python'  
print('{name} wrote {book}'.format(name='Swaroop', book='A Byte of Python'))


输出
0.333
___hello___
Swaroop wrote A Byte of Python
```

`print` 总是会以一个不可见的“新一行”字符（`\n`）结尾，因此重复调用 `print`将会在相互独立的一行中分别打印。为防止打印过程中出现这一换行符，你可以通过 `end` 指定其应以空白结尾：

```python
print('a', end='')
print('b', end='')

ab
```

###### python interactive shell

When commands are read from a terminal, the interpreter is said to be in <u>interactive mode.</u> 

it prompts for the next command with  <u>(>>>)</u>

continuation lines it prompts with the secondary prompt, by default three dots (<u>...).</u>

In interactive mode, the last printed expression is assigned to the read-only variable _. 

````python
>>> tax = 12.5 / 100 
>>> price = 100.50 
>>> price * tax 
12.5625 
>>> price + _ 
113.0625 
>>> round(_, 2) 
113.06
````

#### Variables & assignments

no declaration required

a = 1 

s = "Hello!" 

num = 1.3

Explicit casting:	b = int(3) 

​							c = float(7)

All i<u>dentifiers</u>, i.e. variables names, are c<u>ase-sensitive</u> and must s<u>tart with a letter or underscore</u> and may contain alphanumeric characters and underscore.

###### parallel assignments:

a = 1 

b = 2 

a, b = b, (a+3) # parallel assignment 

print(a, end=' ')  # end in the print() function, is used to avoid the newline after the output

print(b)

The above code produces the following output:

​			2 4

###### Global and Local Variables

A <u>global variable</u> in Python is normally created at the top of the program. A variable that is created outside of a function may be accessed any point after the declaration and is called a global variable.

A l<u>ocal variable</u> may be created inside a function.

A global variable ==cannot be modified inside a function==. If necessary, such variable may be declared as global inside the function that is trying to modify it:

gvar = 100 

def func(): 

​	global gvar 

​	gvar = gvar + 1

###### nonlocal variables

A <u>nonlocal variable</u> is either global or local. 

Nonlocal variables are used <u>in nested functions</u>:

````python
def f1():
	x = 1
	def f2():
		nonlocal x
		x = x + 2
	f2()
	return x
>>> print(f1())
3
````

###### aliasing

Multiple variables referencing the same object is called aliasing.



We can avoid aliasing with copy(), which creates a new object with identical contents.

##### Duck Typing

normal typing: runtime type

duck: presence of certain methods and properties

Python uses duck typing and has <u>typed objects</u> but <u>untyped variable names.</u> 

Type constraints are not checked at compile time; rather, operations on an object may fail, signifying that the given object is not of a suitable type. 

##### Gradual Typing and Type Hints

Gradual typing is a type system in which some variables and expressions may be given types and the correctness of the typing is checked <u>at compile time</u> (which is static ==typing==) and some expressions may be left <u>untype</u>d and eventual type errors are reported at runtime (which is ==dynamic typing==).

#### built-in functions

print(), range(), type(), input(), max(), abs(), bin(), ascii(), chr(), insinstance(), issubclass(), any many others

###### The type() function

The type() function may be used in the code to access the <u>dynamic type</u> of a literal or a variable.

###### Strings

Strings are <u>immutable</u> sequences of unicode characters.

String literals that are part of a single expression and have only whitespace between them will be implicitly converted to a single string literal. That is, ("spam " "eggs") == "spam eggs".

 

.capitalize()

.count(“…”)

“…‘’.join(….)

.format(….)

### python collections

4 built-in container types 



– list is a collection which is <u>ordered and mutable</u>; duplication is allowed. 

– tuple is a collection which is <u>ordered and immutable</u>; duplication is allowed. 

– set is a collection which is u<u>nordered and unindexed</u>; duplication is <u>not allowed</u>; sets are <u>mutable,</u> however, their elements are not. 

– dict is a collection which is <u>ordered* and mutable</u>; duplicate is allowed.

#### lists

ordered 

mutable; 

duplication is allowed.



(string is not list )



Lists might contain items of different types, but usually the items all have the same type

\>>> squares = [1, 4, 9, 16, 25] 

\>>> squares

[1, 4, 9, 16, 25]



lists can be <u>indexed and sliced:</u>

\>>> squares = [1, 4, 9, 16, 25]

\>>> squares[0] # used 0 based indexing

1

\>>> squares[-1] # last element(倒着数)

25

suqares[-3: ] # <u>slicing returns a new list</u>

[9, 16, 25]

string 也可以： “The”[1:3]

he (1,2,不包括三)



lists also support concatenation

suqare + [1,2,3]

[1,4,9,16,25,1,2,3]



string are immutable, but lists are mutable

square[0] = 2

[2, ……]



append()

##### assignment to slices

change value change size clear list



letters = ['a', 'b', 'c', 'd', 'e', 'f', 'g']



 \# replace some values >>> 

letters[2:5] = ['C', 'D', 'E'] >>> 

letters 

['a', 'b', 'C', 'D', 'E', 'f', 'g']



\>>> # now remove them >>> 

letters[2:5] = [] >>> 

letters ['a', 'b', 'f', 'g'] >>> 



clear the list by replacing all the elements  

letters[:] = [] >>> 

letters

[]



len() function； used to determine the size of a sequence



 letters = ['a', 'b', 'c', 'd'] >>> 

len(letters) 

4 >>> 



str = 'abcd' >>> 

len(letters) 

4

##### nested lists

a = ['a', 'b', 'c'] >>> 

n = [1, 2, 3] >>> 



x = [a, n] >>> 

x 

[['a', 'b', 'c'], [1, 2, 3]] >>> 



x[0]

 ['a', 'b', 'c'] >>> 



x[0] [1]

 'b'



The del keyword :

The del keyword may be used to clear a variable or delete an item from a collection 

The del keyword 

c = [1, 2, 3] 

a = 12 

del c[0] 

del a 

#print(a) # uncommenting this would produce error

 print(c) 

[2, 3]



#### Tuples

are used to store multiple items in a single variable. They ==allow== duplicates.

\>>> thistuple = ("apple", "banana", "cherry") >>> 

print(thistuple) 

('apple', 'banana', 'cherry') >>> 

print(thistuple[0]) 

apple >>> 

print(thistuple[-1]) # last element 

cherry



A comma (‘,’) may be used to create a tuple with one element:

\>>> thistuple = ("apple",) # A one-element tupple >>> 

notatuple = ("apple") # not a tupple >>> 

print(type(notatuple))

<class 'str'>



#### sets

A set is a collection which is unordered(cannot be indexed), unchangeable, and unindexed

\>>> thisset = {"apple", "banana", "cherry"} >>> 

print(thisset) 

{"apple", "banana", "cherry"} >>> 



print(len(thisset)) 

3



A set may contain <u>mixed types of elements</u>. 

Set elements, however, must be <u>immutable</u>.



my_set = {1.0, "Hello", (1, 2, 3)} #mixed type >>> 

print(my_set) # set is unordered 

{1.0, (1, 2, 3), 'Hello'}



###### set()

use the set() constructor to make a set out of an iterable sequence (i.e. tuple or list).

\>>> thisset = set(("apple", "orange")) >>> 

print(thisset) 

{"apple", "orange"} >>> 



thisset = set(["apple", "banana"]) >>> 

print(thisset) 

{"apple", "banana"}



###### Modifying Sets

\>>> my_set = {1, 3} >>> 

my_set.add(2) # adds 2 to the set >>> 

print(my_set) 

{1, 2, 3} >>> 

my_set.update([2, 3, 4]) # adds/updates elements >>>

 print(my_set) 

{1, 2, 3, 4} >>> 

my_set.update([4, 5], {1, 6, 8}) >>> 

print(my_set) 

{1, 2, 3, 4, 5, 6, 8}



\>>> my_set = {1, 3} >>> 

my_set.union([1, 4, 7]) 

{1, 3, 4, 7} >>> 

my_set.intersection([1, 4, 7]) 

{1} >>> 

my_set.difference([1, 4, 7]) 

{3} >>> 

my_set.difference_update([1, 4, 7]) >>> 

print(my_set) 

{3} >>> 

{1, 3}.symmetric_difference({2, 3}) 

{1, 2}

###### empty set 

a = { } # a is a dictionary

An empty set may be constructed by using a set() constructor:

a = set() >>> 

print(type(a))

<class 'set'>

#### dictionary

key:value pairs

Keys must be unique.

myDictionary = { "title": "Wish You Were Here", 

​							"artist": "Pink Floyd", 

​							"year": 1975 }

print(myDictionary["artist"])

Pink Floyd



###### add a new item

myDictionary.update({"studio" :"Abbey Road"}) 

print(myDictionary)

{'title': 'Wish You Were Here', 'artist': 'Pink Floyd', 'year': 1975, 'studio': 'Abbey Road'}

###### remove an item

myDictionary.pop("studio") 

del myDictionary["year"] 

print(myDictionary)

{'title': 'Wish You Were Here', 'artist': 'Pink Floyd'}

###### Iterating through a Dictionary

obtaining all keys:



for key in myDictionary: 

print (key)

title 

artist 

year 

studio



obtaining all values

for key in myDictionary: 

print (myDictionary[key])

Wish You Were Here 

Pink Floyd 

1975 

Abbey Road



for k in myDictionary.keys():

 print(k) 

for val in myDictionary.values(): 

print(val)



### Functions



the indent here has to be the same

def hello(name): 

​		'''this is a function that prints a greeting''' 

​		print('Hello ' + name)

A function in Python always returns a value

def add(x, y): 

​		return x + y



If no return statement is used in a function, the function returns <u>None</u>:

def foo(): 

​		print('') >>> 

print(foo()) 

None

###### default arguments

The <u>default values are evaluated once only</u> at the point of function definition in the defining scope:

i = 5 

def f(arg=i): 

​	print(arg) 

i = 6 

f() # prints 5



def f(a, L=[]): 

​	L.append(a) 

​	return L 

print(f(1)) # prints [1] 

print(f(2)) # prints [1, 2] 

print(f(3)) # prints [1, 2, 3]

 #passing L is optional because it has default value



def f(a, L=None): 

​	if L is None: 

​		L = [ ] 

​	L.append(a) 

​	return L



pass statement use when need empty method

###### named objects

Python also supports invoking functions using named arguments: 

def add(x, y): 

​		return x + y

 print(add(x=1, y=4)) 

5



A mix of positional and named arguments may also be used:

print(add(1, y=4))

5



Python allows restricting using named and positional arguments by using / and *:

def f(pos1, pos2, /, pos_or_kwd, *, kwd1, kwd2):

before / is positional arguments

after * always keywords

###### Arbitrary arguments with *args

We can use *args to pass an <u>arbitrary number of arguments.</u>

With *args the function receives a <u>tuple</u> of arguments

def displayNames(*names):

​	 print("Names: ", end=" ") 

​	for n in names: print(n, end=" ") 

​	print() 



displayNames("Syd") 

displayNames("Syd", "David", "Roger") 

Names: Syd 

Names: Syd David Roger

###### The * operator

used to treat <u>an iterable object</u> (i.e. a list) as ==positional arguments==



Example: Suppose function add() receives two argument: 

def add(x, y): return x + y



 Using the * operator we can covert the tuple t into two arguments that are passed to the method add 

t = (1, 2) 

z = add(*t) 

print(z)



###### The ** operator

The ** operator may be used to treat a <u>dictionary object</u> as ==named arguments==.



Using the ** operator we can covert a dictionary d into the two named arguments:

d = {'x':1, 'y':2} 

z = add(**d) 

print(z)

#### control flow

##### loops

###### while

a, b = 0, 1 

​	while a < 1000: 

​	print(a, end=' ') 

​	a, b = b, a + b

0 1 1 2 3 5 8 13 21 34 55 89 144 233 377 610 987 



###### for

iterates over the items of any <u>sequence</u> (a list or a string), in the order that they appear in the sequence.

 

words = ['cat', 'window', 'defenestrate'] 

for w in words: 

​		print(w, len(w))

cat 3 

window 6 

defenestrate 12



dictionary:

users = {'Hans': 'active', 'Éléonore': 'inactive'} 

#Strategy 1: Iterate over a copy 

for user, status in users.copy().items(): 

​		if status == 'inactive': 

​			del users[user] 



#Strategy 2: Create a new collection 

active_users = { } 

for user, status in users.items():

​		 if status == 'active': 

​				active_users[user] = status

###### 

###### range()

for i in range(10) #0…9

​	print(i, end = ‘ ’)

print()



for i in range(3,10,2): # from 3 to 10 increment by 2

​	print(i,end=' ') 

print()

0 1 2 3 4 5 6 7 8 9 

3 5 7 9 



###### if [elif else]

if … :

​	…

elif … :

​	…

else:

​	…



###### list comprehension

fruits = ["apple", "orange", "banana", "mango"] 

afruits = [x for x in fruits if x.startswith('a') or x.startswith('o')]

extracts all fruits that start with ‘a’ ‘o’



###### break else continue

break: breaks out of the innermost enclosing for or while loop, respectively.

 else clause runs when no break occurs.

continue:  continues the next iteration of the innermost enclosing for or while loop, respectively.

###### match

with loop, list, tuples, wildcards, classes

takes an expression and compares its value to successive patterns given as one or more case blocks.



def http_error(status): 

​	match status: case 401 | 403 | 404: 

​		return "Not allowed" 

​	case 404: 

​		return "Not found"

​	case _: # default 

​		return "Something's wrong with the internet"

 





#####  Modules

file name is the module name with the .py appended

##### package

a module can contain other modules or recusively other packages





 

####  oop message passing

python is not a pure object-oriented programming

by message passing.



b.getTitle()

the receiver object is b

the message is getTitle()

###### init self 

init: used to initialize a newly created instance of the class (object)

self: a reference to the current instance of the class.

self is used to access features of the class



b = Movie("Until the End of the World", "1991")



###### __ init __ () and  __ del __ () methods

__ init __ () : constructor, called immediately after class instantiated

The __ del __() method, the destructor, is called when the object is being destroyed (see garbage collection)



###### Functors and the __ call __() method

called when the object is being called like a function. We call such an object a functor



#### Class Inheritance

derived class can <u>override</u> any methods of its base class or classes, and a method can call the method of a base class with the same name. 

there is no method overloading in python

last one always overrides previous

###### **Mixin**

**Mixin** 即 Mix-in ，常被译为“混入”，**是**一种编程模式，在**Python** 等面向对象语言中，通常它**是**实现了某种功能单元的类，用于被其他子类继承，将功能组合到子类中。 利用**Python** 的多重继承，子类可以继承不同功能的**Mixin** 类，按需动态组合使用。

a mixin is a class that provides a certain functionality to be inherited by a subclass, but is not meant to be instantiated

a class cannot claim an is-a relationship with a mixin. 

###### Method Resolution Order (MRO)

方法解析顺序

#### Access Control

**public类型**

没有以下划线开头的变量或者方法是public类型

被子类、类内以及类外被访问。

**protected类型**

单下划线开头表示的是protected类型的变量或者方法

只能允许其本身与子类进行访问

**private类型**

双下划线表示的是私有类型的变量或者方法

rivate类型只能允许类内进行访问
