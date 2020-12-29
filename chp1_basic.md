# Chapter1 Baisc Concept

* [Back](README.md)

<!-- TOC depthFrom:2 -->

- [性能分析](#性能分析)
  - [空间复杂度](#空间复杂度)
  - [时间复杂度](#时间复杂度)
    - [程序步](#程序步)
    - [计算程序步的两种方法：](#计算程序步的两种方法)
      - [计数器法：引入变量count](#计数器法引入变量count)
      - [列表法：](#列表法)

<!-- /TOC -->

## 性能分析

### 空间复杂度

* 固定空间: 代码空间， 简单变量空间， 常数空间等
* 可变空间:

  + 结构变量所需空间， 依赖于问题特殊实例
  + 引用变量所需空间， 依赖于实例特性
  + 递归栈所需空间，依赖于实例特性

* S(P) = c + S$_{p}$

### 时间复杂度

#### 程序步

在语法或语义上有意义的程序片段，且该片段的执行时间不依赖于实例特性

1. 注释语句: 0；
2. 声明语句：0；
3. 表达式与赋值语句：1；
4. 循环语句：只考虑这类语句的控制部分的程序步数

* `for(init; expression1; expression2)` : 1
* `while(expression) do` or `do...while(expression)`: 程序步数等于其表达式的程序步数

5. switch语句：

  ```c++
  switch(expression) {
  case cond1: statement1
  case cond2: statement2
  .
  .
  default: statement
  }

  ```

  * 首部时间开销等于表达式开销
  * 每个条件语句的时间开销等于该条件语句的时间开销加之前条件语句时间开销

6. if-else语句：

  ```c++
  if(expression) statement1;
  else statement2;
  ```

  每个部分程序步数分别根据expression statement1 和 statement2来确定

7. 函数调用：1（除非该函数调用涉及实例特性的按值传参）
8. 内存管理语句： new delete sizeof... : 1
9. 函数语句：0
10. 转移语句：continue, break, goto, return... : 1

#### 计算程序步的两种方法：

Source:

```c++
float Sum(float* a, const int n)
{
  float s = 0;
  for(int i = 0; i < n; i++)

    s += a[i];

  return s;
}

```
##### 计数器法：引入变量count

Add Count:

```c++
float Sum(float* a, const int n)
{
  float s = 0;
  count++; //count is global
  for(int i = 0; i < n; i++)
  {
    count++; //for for
    s += a[i];
    count++; //for assignment
  }
  count++; //for last time of for
  count++; //for return
  return s;
}
```

简化：

```c++
float Sum(float* a, const int n)
{
  for(int i = 0; i < n; i++)

    count += 2;

  count += 3;
}
```

##### 列表法：

s/e: 一条语句每次执行程序步数<br>
FS: 语句频率(Frequence of Statement)<br>
PS: 程序步数(Process Steps)<br>

|  Row  |  s/e  |   FS  |   PS  |
|:-----:|:-----:|:-----:|:-----:|
|   1   |   0   |   1   |   0   |
|   2   |   1   |   1   |   1   |
|   3   |   1   |  n+1  |  n+1  |
|   4   |   1   |   n   |   n   |
|   5   |   1   |   1   |   1   |
|   6   |   0   |   1   |   0   |
|  总的 |  程序 |  步数 |  2n+3 |
