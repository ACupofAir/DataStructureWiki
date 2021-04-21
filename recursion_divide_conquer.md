[:car:...](README.md)

# Recursion and Divide&Conquer 

1. [基础概念](#基础概念)
   * [分治法](#分治法)
   * [递归问题](#递归问题)
2. [问题](#问题)
   * [整数划分](#整数划分)
     * [问题](#问题)

## 基础概念

### 分治法
* **思想** 将一个大问题分割成规模较小的相同问题 

### 递归问题
* **双递归函数** 一个函数及其的一个变量由函数自身定义时[Acherman函数](https://en.wikipedia.org/wiki/Ackermann_function)
和哦
## 问题
### 整数划分
#### 问题
* 将正整数n表示成一系列正整数之和$n=n_1+n_2+...+n_k$
* 求正整数n的不同划分个数

#### Solution
* 记正整数n最大加数为m的划分个数为q(n,m),则
   * $q(n,1) = 1$
   * $q(n,m) = q(n,n) (m >= n)$
   * $q(n,n) = q(n, n-1) + 1$
   * $q(n,m) = q(n, m-1) + q(n-m, m)$
* Code
    * [ cpp ](https://github.com/ACupofAir/Algorithm/blob/main/chp2_recursive_divide_conquer/divide_n.cpp)
      ```cpp
      int q(int n, int m) {
      if (n < 1 || m < 1)
      return 0;
      else if (n == 1 || m == 1) {
      return 1;
      } else if (n < m) {
      return q(n, n);
      } else if (n == m) {
      return q(n, m - 1) + 1;
      } else {
      return q(n, m - 1) + q(n - m, m);
      }
      }
      ```

    * [ python ](https://github.com/ACupofAir/Algorithm/blob/main/chp2_recursive_divide_conquer/divide_n.py)
        ```python
        def divide_n(n, m):
        if n < 1 or m < 1:
        return 0
        elif n == 1 or m == 1:
        return 1
        elif n < m:
        return divide_n(n, n)
        elif n == m:
        return divide_n(n, m-1) + 1
        else:
        return divide_n(n, m-1) + divide_n(n-m, m)
        n = int(input('Input a number: '))
        print(f'The divide of {n} has {divide_n(n,n)} methods ')
        ```
