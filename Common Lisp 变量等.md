



### Common Lisp 

#### 变量 赋值variables assignments

##### variables

A variable is **global** if it is visible everywhere as opposed to a **local** variable which is visible only within the code block in which it is defined.

###### local variable let函数

Inside code blocks, <u>local values are always looked for first.</u> If a local value for the variable does not exist, then a global value is sought.

If no global value is found then the result is an error.

`let` 是一个最常用的 Common Lisp 的操作符之一，它让你引入新的局部变量（local variable）：

```lisp
> (let ((x 1) (y 2))
     (+ x y))
3
```

###### global variable defparameter 函数

A global variable is accessible <u>everywhere</u> except in expressions that create a new local variable with the same name

全局变量在任何地方都可以存取，除了在定义了相同名字的区域变量的表达式里。

```lisp
> (defparameter *glob* 99)
*GLOB*
```

为了避免这种情形发生，通常我们在给全局变量命名时，以星号作开始与结束。刚才我们创造的变量可以念作 “星-glob-星” (star-glob-star)。

```lisp
(defconstant limit (+ *glob* 1))
```

````LISP
> (defconstant limit 90)
Error: LIMIT is a constant and cannot be set or bound. 
````





我们不需要给常量一个独一无二的名字，因为如果有相同名字存在，就会有错误产生 (error)。如果你想要检查某些符号，是否为一个全局变量或常量，使用 `boundp` 函数：

```lisp
> (boundp '*glob*)
T 
```



##### assignment : 

###### setf 函数 setq

We use `setq` to assign a global variable and `setf` to assign both global and local variables.

在 Common Lisp 里，最普遍的赋值操作符（assignment operator）是 `setf` 。可以用来给全局或局部变量赋值：

```lisp
> (setf *glob* 98)
98
> (let ((n 10))
   (setf n 2)
   n)
2
```

如果 `setf` 的第一个实参是符号（symbol），且符号不是某个局部变量的名字，则 `setf` 把这个符号设为全局变量：

```lisp
> (setf x (list 'a 'b 'c))
(A B C)
```

也就是说，通过赋值，你可以隐式地创建全局变量。 不过，一般来说，还是使用 `defparameter` 明确地创建全局变量比较好。



你不仅可以给变量赋值。传入 `setf` 的第一个实参，还可以是<u>表达式或变量名</u>。在这种情况下，第二个实参的值被插入至第一个实参所引用的位置：

```lisp
> (setf (car x) 'n)
N
> x
(N B C)
```

```lisp
(setf a 'b
      c 'd
      e 'f)等同于依序调用三个单独的 `setf` 函数：

```

等同于：

```lisp
(setf a 'b)
(setf c 'd)
(setf e 'f)
```

We can use setf to modify the list as well



````lisp
> (setf x '(a b c d))
(A B C D)
> (setf (car x) '(a b c))
(A B C)
> x
((A B C) B C D)
> (setf (cdr x) '((b c d)))
((B C D))
> x
((A B C) (B C D))
````





###### eql equal 函数

Variables are essentially pointers. 



Function `eql` will return true if <u>its arguments point to the same object,</u> whereas function `equal` returns true if its arguments <u>have the same value.</u>

```lisp
> (eql (cons 'a nil) (cons 'a nil))
NIL

> (setf x (cons 'a nil))
(A)
> (eql x x)
T

> (equal x (cons 'a nil))
T


```

###### copy-list函数

takes a list and returns a copy of it

````lisp
> (setf w (copy-list x))
(A B C D E)
> (eql x w)
NIL
> (equal x w)
T
````

`x` 与 `(copy-list x)` 会永远 `equal` ，并永远不 `eql` ，除非 `x` 是 `NIL` 。

#### shared structure

Lists can share structure. This implies that two variables may share elements. 

#### functional programming



利用返回值而工作的程序， 而不是修改东西。lisp的内置函数被调用是为了取得返回值。

举例来说，函数 `remove` 接受一个对象和一个列表，返回不含这个对象的新列表：

```lisp
> (setf lst '(c a r a t))
	(C A R A T)
> (remove 'a lst)
	(C R T)
```

`remove` 接受了对象 a 和列表 lst， 返回了一个新列表。

`remove` 没有对原先的列表做出改变。

如果想要改变原始列表，

```lisp
(setf x (remove 'a x))
```

#### unordered structures

##### sets集合

 A ==set== is a collection on objects, called its elements(members)

If S is a set and x is an element, then we write  𝑥 ∈ S

If x is not an element of S we write 𝑥 ∉ S

empty set/null set:  ∅ or { }  

 – no element repetition is allowed

 – the ordering of the elements is not important

Two sets are equal if they have the same elements. 

​								{𝑎, 𝑏, 𝑐 } = {𝑐, 𝑎, b}

also, 		𝑎 ≠ {𝑎} ≠ {{a}}



If A and B are sets and every element of A is also an element od B, then we say <u>A is a subset of B</u>: 𝐴 ⊂ B

also,		∅ ⊂ 𝐴 

​				𝐴 = 𝐵 means 𝐴 ⊂ 𝐵 and 𝐵 ⊂ A



###### Operations on sets

The ==union== of two sets A and B, denoted as 

​				𝐴 ∪ 𝐵, is given by: 𝐴 ∪ 𝐵 = 𝑥: 𝑥 ∈ 𝐴 or 𝑥 ∈ 𝐵 

The ==intersection== of two sets A and B, denoted as 

​				𝐴 ∩ 𝐵, is given by: 𝐴 ∩ 𝐵 = 𝑥: 𝑥 ∈ 𝐴 and 𝑥 ∈ 𝐵 

 The ==difference== between two sets A and B, denoted as 

​				𝐴 ∖ 𝐵 (or 𝐴 − 𝐵), is given by: 𝐴 ∖ 𝐵 = 𝑥: 𝑥 ∈ 𝐴 and 𝑥 ∉ 𝐵 

 The ==symmetric difference== of two sets A and B, denoted as 				

​				𝐴 ⊕ 𝐵, is given by: 𝐴 ⊕ 𝐵 = 𝑥: 𝑥 ∈ 𝐴 or 𝑥 ∈ 𝐵 but 𝑛𝑜𝑡 𝑏𝑜𝑡ℎ = 𝐴 ∖ 𝐵 ∪ 𝐵 ∖ 𝐴

Two sets A and B are ==disjoint== <u>iff their intersection is empty,</u> i.e.: 𝐴 ∩ 𝐵 = ∅

集合论中的并集 (union)、交集 (intersection)以及补集 (complement)的实现，是由函数 `union` 、 `intersection` 以及 `set-difference` 。



```lisp
> (union '(a b c) '(c b s))
(A C B S)
> (intersection '(a b c) '(b b c))
(B C)
> (set-difference '(a b c d e) '(b e))
(A C D)
```









函数 `adjoin` 像是条件式的 `cons` 。它接受一个对象及一个列表，如果对象还不是列表的成员，才构造对象至列表上。

```lisp
> (adjoin 'b '(a b c))
(A B C)
> (adjoin 'z '(a b c))
(Z A B C)
```

##### bag 

A ==bag== (or multiset) is a structure which contains a collection of elements. 

 Like a set, the ordering of the elements is not important. 

 Unlike a set, repetitions are allowed. 

Note that {𝑎, 𝑏, 𝑏, 𝑐} = {𝑐, 𝑎, 𝑏, 𝑏} 

​				{𝑎, 𝑏, 𝑐} ≠ {𝑐, 𝑎, 𝑏, 𝑏}



````lisp
(defun bag-to-set (bag);;去除重复
	(cond ((null bag) '())
	((member (car bag) (cdr bag)) 
     	(bag-to-set (cdr bag)))
	(t (cons (car bag) (bag-to-set(cdr bag))))))

> (bag-to-set '(a a b c))
(A B C)
> (bag-to-set '(a a a b b c b a))
(C B A)
> (bag-to-set '(a b c d))
(A B C D)
````

#### ordered structure

##### list

*列表*是由被括号包住的零个或多个元素来表示。元素可以是任何类型，包含列表本身。使用列表必须要引用，不然 Lisp 会以为这是个函数调用



调用 `list` 来创建列表。由于 `list` 是函数，所以它的实参会被求值。



```lisp
> (list 'my (+ 2 1) "Sons")
(MY 3 "Sons")

> (list '(+ 2 1) (+ 2 1))
((+ 2 1) 3)
```



在 Common Lisp 里有两种方法来表示空列表。你可以用一对不包括任何东西的括号来表示，或用符号 `nil` 来表示空表。你用哪种表示法来表示空表都没关系，但它们都会被显示为 `nil` ：

```lisp
> ()
NIL
> nil
NIL
```

用函数 `cons` 来构造列表(第二个实参是列表)

可以通过把新元素建立在空表之上，来构造一个新列表

```lisp
> (cons 'a '(b c d))
(A B C D)

> (cons 'a (cons 'b nil))
(A B)
> (list 'a 'b)
(A B)
```

取出列表元素的基本函数是 `car` 和 `cdr`

你可以把 `car` 与 `cdr` 混合使用来取得列表中的任何元素



```lisp
> (car (cdr (cdr '(a b c d))))
C

可以用更简单的 `third` 来做到同样的事情：
> (third '(a b c d))
C
```



##### tuple

 a structure which contains a collection of elements

Unlike sets and bags, the ordering of the elements matters. 

Unlike a set, repetitions are allowed. 

(𝑎, 𝑏, 𝑏, 𝑐) ≠ (𝑐, 𝑎, 𝑏, 𝑏)

(𝑎, 𝑏, 𝑐) ≠ (𝑐, 𝑎, 𝑏, b)



### trees

`copy-tree` 接受一个树，并返回一份副本。它可以这么定义：

```lisp
(defun our-copy-tree (tr)
  (if (atom tr)
       tr
       (cons (our-copy-tree (car tr))
             (our-copy-tree (cdr tr)))))
```

### sorting 

##### bubble sort

### Searching

#### linear search

