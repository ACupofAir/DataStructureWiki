[:car:...](README.md)

# Chapter3 Stack&Queue

- [Overflow&Underflow](#overflowunderflow)
- [代数表达式](#代数表达式)
  - [中缀转后缀](#中缀转后缀)
- [环形队列](#环形队列)

## Overflow&Underflow

* Overflow: 满了还要塞
* Underflow: 空了还要取

## 代数表达式
   > 如给了后缀写出中缀，执行顺序
   > 1. 组成: 操作数，操作符，分界符
   > 2. 日常表达式: 中缀； 计算机计算的表达式：后缀

### 中缀转后缀
1. 算法
   1. 从左到右扫描表达式
   2. 遇到操作数直接输出
   3. 遇到运算符，若栈为空或栈顶为左括号直接入栈，否则与栈顶运算符比较，优先级大则入栈，否则直接输出
   4. 遇到左括号直接入栈，遇到右括号将栈顶元素出栈，直至遇到左括号为止

2. 例子
   * 中缀`A*(B+C)*D`
   * 后缀`ABC+*D*`

   | 下个标记 |  栈   |  输出   |
   |:--------:|:-----:|:-------:|
   |   none   | empty |  none   |
   |    A     | none  |    A    |
   |    *     |  `*`  |    A    |
   |    (     | `*(`  |    A    |
   |    B     | `*(`  |   AB    |
   |    +     | `*(+` |   AB    |
   |    C     | `*(+` |   ABC   |
   |    )     |  `*`  |  ABC+   |
   |    *     |  `*`  |  ABC+*  |
   |    D     |  `*`  | ABC+*D  |
   |   done   | none  | ABC+*D* |




## 环形队列
   > 它比最初的那种队列好在哪
   > [wiki](https://en.wikipedia.org/wiki/Circular_buffer#)

* 数据结构
  1. 一个数组
  2. 两个指针front, rear
  3. `rear = (rear+1)%capacity`

* 优点
  >* 直线队列在元素出队后，头指针向后移动，导致删除元素后的空间无法再利用，即使元素个数小于空间大小，依然无法再进行插入，即所谓的“假上溢”。当变成循环队列之后，删除元素后的空间仍然可以利用，最大限度的利用空间。</br>
  >* 最坏情况下的添加和删除从<!-- $\Theta(n)$ --> <img style="transform: translateY(0.1em); background: white;" src="svg\jQ8c9k5NsY.svg">变为<!-- $\Theta(1)$ --> <img style="transform: translateY(0.1em); background: white;" src="svg\aTiuKJoDl2.svg">