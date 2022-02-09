#### Priority Queue/Heap 优先队列/堆

PQ(Priority Queue) 又叫堆， PQ是一种队列，不过不是先进先出（FIFO）而是每次出队的元素永远是优先级最高的。

###### logical structure of PQ

PQ是 **完全二叉树(complete binary tree)**:

- 除了最后一层，所有层都排满
- 最后一层的所有非空节点都排在左边
- ![img](https://x-wei.github.io/images/heap-summary/pasted_image.png)

如果一个完全二叉树能被称为PQ，则其满足以下条件： 对于任何一个节点，他的优先级都大于左右子节点的优先级。例：![img](https://x-wei.github.io/images/heap-summary/pasted_image001.png)

（形状就像是一个堆）在这一堆节点里，优先级最高的是最顶上的节点。