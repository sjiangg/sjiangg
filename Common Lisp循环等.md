



### Common Lisp 

#### 变量 赋值variables assignments

##### variables

A variable is **global** if it is visible everywhere as opposed to a **local** variable which is visible only within the code block in which it is defined.

###### local variable let函数

Inside code blocks, <u>local values are always looked for first.</u> If a local value for the variable does not exist, then a global value is sought.

If no global value is found then the result is an error.

`let` 是一个最常用的 Common Lisp 的操作符之一，它让你引入新的局部变量（local variable）：

```lisp
xxxxxxxxxx3 1> (let ((x 1) (y 2))2     (+ x y))33
```

###### global variable defparameter 函数

A global variable is accessible <u>everywhere</u> except in expressions that create a new local variable with the same name

全局变量在任何地方都可以存取，除了在定义了相同名字的区域变量的表达式里。

```lisp
xxxxxxxxxx2 1> (defparameter *glob* 99)2*GLOB*
```

为了避免这种情形发生，通常我们在给全局变量命名时，以星号作开始与结束。刚才我们创造的变量可以念作 “星-glob-星” (star-glob-star)。

```lisp
xxxxxxxxxx1 1(defconstant limit (+ *glob* 1))
```

```LISP
xxxxxxxxxx2 1> (defconstant limit 90)2Error: LIMIT is a constant and cannot be set or bound. 
```





我们不需要给常量一个独一无二的名字，因为如果有相同名字存在，就会有错误产生 (error)。如果你想要检查某些符号，是否为一个全局变量或常量，使用 `boundp` 函数：

```lisp
xxxxxxxxxx2 1> (boundp '*glob*)2T 
```



##### assignment : 

###### setf 函数 setq

We use `setq` to assign a global variable and `setf` to assign both global and local variables.

在 Common Lisp 里，最普遍的赋值操作符（assignment operator）是 `setf` 。可以用来给全局或局部变量赋值：

```lisp
xxxxxxxxxx6 1> (setf *glob* 98)2983> (let ((n 10))4   (setf n 2)5   n)62
```

如果 `setf` 的第一个实参是符号（symbol），且符号不是某个局部变量的名字，则 `setf` 把这个符号设为全局变量：

```lisp
xxxxxxxxxx2 1> (setf x (list 'a 'b 'c))2(A B C)
```

也就是说，通过赋值，你可以隐式地创建全局变量。 不过，一般来说，还是使用 `defparameter` 明确地创建全局变量比较好。



你不仅可以给变量赋值。传入 `setf` 的第一个实参，还可以是<u>表达式或变量名</u>。在这种情况下，第二个实参的值被插入至第一个实参所引用的位置：

```lisp
xxxxxxxxxx4 1> (setf (car x) 'n)2N3> x4(N B C)
```

```lisp
(setf a 'b      c 'd      e 'f)等同于依序调用三个单独的 `setf` 函数：
```

等同于：

```lisp
(setf a 'b)(setf c 'd)(setf e 'f)
```

We can use setf to modify the list as well



```lisp
> (setf x '(a b c d))(A B C D)> (setf (car x) '(a b c))(A B C)> x((A B C) B C D)> (setf (cdr x) '((b c d)))((B C D))> x((A B C) (B C D))
```





###### eql equal 函数

Variables are essentially pointers. 



Function `eql` will return true if <u>its arguments point to the same object,</u> whereas function `equal` returns true if its arguments <u>have the same value.</u>



###### copy-list函数

takes a list and returns a copy of it

```lisp
xxxxxxxxxx6 1> (setf w (copy-list x))2(A B C D E)3> (eql x w)4NIL5> (equal x w)6T
```

#### shared structure

Lists can share structure. This implies that two variables may share elements. 

````functional programming



利用返回值而工作的程序， 而不是修改东西。lisp的内置函数被调用是为了取得返回值。

举例来说，函数 `remove` 接受一个对象和一个列表，返回不含这个对象的新列表：

```lisp
xxxxxxxxxx4 1> (setf lst '(c a r a t))2    (C A R A T)3> (remove 'a lst)4    (C R T)
```

`remove` 接受了对象 a 和列表 lst， 返回了一个新列表。

`remove` 没有对原先的列表做出改变。

如果想要改变原始列表，

```lisp
xxxxxxxxxx1 1(setf x (remove 'a x))
```

