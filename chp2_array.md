[:car:...](README.md)

# Chapter2 Arrays
- [基本概念](#基本概念)
- [数组应用](#数组应用)
  - [多项式(Polynomial)](#多项式polynomial)
    - [多项式的表示](#多项式的表示)
    - [多项式加法 It's make no sense.](#多项式加法-its-make-no-sense)
  - [稀疏矩阵(Sparse Matrices)](#稀疏矩阵sparse-matrices)
    - [三元组表示稀疏矩阵](#三元组表示稀疏矩阵)
  - [字符串(KMP算法)](#字符串kmp算法)

## 基本概念
```cpp
int arr[n];
int arr = new int[n];
```
1. arr指数组的第0个元素的指针
2. `arr[i] = *(arr+i)`

## 数组应用

### 多项式(Polynomial)

#### 多项式的表示
1. 每一项
```cpp
class Term
{
  friend Polynomial;
private:
  float coef;
  int exp;
};
```

2. 总的
```cpp
class Polynomial
{
private:
  Term* termArray;
  int capacity;
  int terms;
public:
  Polynomial();
  void AddTerm(Exponent e, Coefficient c);
  Polynomial Add(Polynomial poly);
  Polynomial Mult(Polynomial poly);
  float Eval(float f);//计算在x取f时多项式的值
}
```
>* eg: 2x<sup>1000</sup> + 1
>
>| coef | exp  |
>|:----:|:----:|
>|  2   | 1000 |
>|  1   |  0   |
>| ...  | ...  |
>* 总结：
> 对于稀疏多项式节省储存空间，对于满的则比双数组法要多一倍

#### 多项式加法 It's make no sense.

### 稀疏矩阵(Sparse Matrices)
#### 三元组表示稀疏矩阵
> Matrices
>| arr | 0  | 1  | 2  | 3  | 4 |  5  |
>|:---:|:--:|:--:|:--:|:--:|:-:|:---:|
>|  0  | 15 | 0  | 0  | 22 | 0 | -15 |
>|  1  | 0  | 11 | 3  | 0  | 0 |  0  |
>|  2  | 0  | 0  | 0  | -6 | 0 |  0  |
>|  3  | 0  | 0  | 0  | 0  | 0 |  0  |
>|  4  | 91 | 0  | 0  | 0  | 0 |  0  |
>|  5  | 0  | 0  | 28 | 0  | 0 |  0  |
>
> Triple
>
>| smArray | row | col | value |
>|:-------:|:---:|:---:|:-----:|
>|   [0]   |  0  |  0  |  15   |
>|   [1]   |  0  |  3  |  22   |
>|   [2]   |  0  |  5  |  -15  |
>|   [3]   |  1  |  1  |  11   |
>|   [4]   |  1  |  2  |   3   |
>|   [5]   |  2  |  3  |  -6   |
>|   [6]   |  4  |  0  |  91   |
>|   [7]   |  5  |  2  |  28   |
ADT
```cpp
class SparseMatrix
{
public:
  SparseMatrix(int r, int c, int t);
  SparseMatrix Transpose();
  SparseMatrix Add(SparseMatrix b);
  SparseMatrix Multiply(SparseMatrix b);
};

class MatrixTerm
{
friend class SparseMatrix;
private:
  int rows, cols, terms, capacity;
  MatrixTerm* smArray;
}
```


### 字符串(KMP算法)