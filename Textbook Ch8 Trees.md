#### General Trees

Tree structures are indeed a breakthrough in data organization, for they allow us to implement a host of algorithms much faster than when using linear data structures, such as arrays or linked lists. Trees also provide a natural organization for data, and consequently have become ubiquitous常见的 structures in file systems, graphical user interfaces, databases, websites, and many other computer systems.

The relationships in a tree are **hierarchical**, with some objects being ‘above’ and some objects being ‘below’ others.

Top element: **the root** of the tree.



###### Formal Tree Definition

Formally, we define a **tree** *T* as a set of **nodes** storing elements such that the nodes have a **parent-child** relationship that satisfies the following properties:

- if *T* is nonempty, it has a special node, called the **root** of *T*, that has no parent.

- Each node *v* of *T* different from the root has a unique **parent** node *w*; every node with parent *w* is a **child** of *w*.  

  ###### Other Node Relationships

- Two nodes that are children of the same parent are **siblings**. S node *v* is **external** if *v* has no children. A node *v* is **internal** if it has one or more children. External nodes are also known as **leaves**

- A node *u* is an **ancestor** of a node *v* if *u=v* or u is an ancestor of the parent of *v*. The **subtree** of *T* **rooted** at a node *v* is the tree consisting of all the descendants of *v* in *T*, including *v* itself

  ###### Edges and Paths in Trees

- An **edge** of tree *T* is a pair of nodes *(u,v)* such that *u* is the parent of *v*, or vice versa. A **path** of *T* is a sequence of nodes such that any two consecutive nodes in the sequence form an edge. 

###### 为什么需要树？

因为他结合了另外两种数据结构的优点： 有序数组和链表。在树中查找数据项的速度和在有序数组中查找一样快，并且插入数据项和删除数据项的速度也和链表一样。 

###### Ordered Trees

A tree is **ordered** if there is a meaningful linear order among the children of each node; that is, we purposefully identify the children of a node as being the first, second, third, and so on. 

Such an order is usually visualized by arranging siblings left to right, according to their order



##### The Tree ADT

![image-20210620203900025](image-20210620203900025.png)

##### Binary Trees

An ordered tree with the following properties:

1. Every node has at most two children
2. Each child node is labeled as being either a **left child** or a **right child**.
3. A left child precedes a right child in the order of children of a node

The subtree rooted at a left or tight child of an internal node *v* is called a **left subtree** or **right subtree**, respectively, of *v*. A binary tree is **proper** if each node has either zero or two children(full binary tree). 



###### A Recursive Binary Tree Definition

Incidentally, we can also define a binary tree in a recursive way. In that case, a binary tree is either:

• An empty tree.

• A nonempty tree having a root node *r*, which stores an element, and two binary trees that are respectively the left and right subtrees of  *r*. We note that one or both of those subtrees can be empty by this definition.

 

##### The Binary Tree ADT

![image-20210622152002450](image-20210622152002450.png)

##### Properties of Binary Trees

Binary trees have several interesting properties dealing with relationships between their heights and number of nodes. 



We denote the set of all nodes of a tree *T* at the same depth *d* as *level* *d* of *T*. In a binary tree, level 0 has at most one node (the

root), level 1 has at most two nodes (the children of the root), level 2 has at most four nodes, and so on.  In general, level *d* has at most 2*d* nodes.

##### Binary Search Tree

BST is an extension of Binary tree with some added constraints.一个节点的左子节点的值必须小于或等于其父结点的值，而右节点的值始终大于或等于其父结点的值。此特性使其适合于搜索操作，因为在每个节点上，我们都可以确定该值是在左子树中还是右子树中。

二叉查找树要么是一棵空树，要么是一棵具有如下性质的非空二叉树：

1. 若左子树非空，则左子树上的所有结点的关键字值均小于根结点的关键字值。
2. 若右子树非空，则右子树上的所有结点的关键字值均大于根结点的关键字值。
3. 左、右子树本身也分别是一棵二叉查找树（二叉排序树）。



##### AVL tree

朴素的二叉搜索树在进行插入节点，删除节点等动态操作的时候会影响到树的形态，可能致使树走向低效，影响后续操作的效率。今天就介绍一下二叉搜索树的一个变种——平衡二叉树(AVL)。

AVL树是一种自平衡的二叉搜索树，在进行动态操作时可以维持自身形态的平衡，从而保证基本操作的时间复杂度维持在O(logn)。



其平均和最坏情况下的查找时间都是O(logn)。同时，插入和删除的时间复杂性也会保持O(logn)。平衡二叉树的定义如下:



- 它或者是一棵空二叉树。
- 或者是具有如下性质的二叉查找树：其左子树和右子树都是高度平衡的二叉树，且左子树和右子树的高度之差的绝对值不超过1。



###### Trinode 重组

在数内部，可以将一个或多个旋转合并来提供更广泛的平衡。



##### 树的遍历

树的遍历通常使用递归的方法进行理解和实现， 在访问元素时也需要使用递归的思想去理解。 

- 深度优先
  - 1. 前序Pre-order root-left-right
    2. 中序In-order left-root-right
    3. 后序Post-order left-right-root
- 广度优先
  - 先访问根节点，沿着树的宽度遍历子节点，直到所有节点均被访问为止

二叉树的广度优先遍历和树的前序/中序/后序遍历不太一样，前/中/后序遍历使用递归，也就是栈的思想对二叉树进行遍历，广度优先一般使用队列的思想对二叉树进行遍历。

如果已知中序遍历和前序遍历或者后序遍历，那么就可以完全恢复出原二叉树结构。

![Binary Tree Traversal](binary_tree_traversal.png)

