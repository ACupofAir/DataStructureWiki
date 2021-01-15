<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
<script type="text/x-mathjax-config">
  MathJax.Hub.Config({
    tex2jax: {
      inlineMath: [ ['$','$'], ["\\(","\\)"] ],
      processEscapes: true
    }
  });
</script>
[:car:...](README.md)
 
# Chapter8 Hash
- [Hash Function](#hash-function)
  - [异号 mod](#异号-mod)
  - [Uicode 知识](#uicode-知识)
  - [Hash Function定义](#hash-function定义)
- [Overflow Handing(溢出处理)](#overflow-handing溢出处理)
  - [开放地址法](#开放地址法)
  - [链地址法](#链地址法)

## Hash Function

### 异号 mod

1. 定义
   $$A \bmod B=B*(\frac{A}{B}-[\frac{A}{B}])$$
   > 取整是向下取整
2. 实例
   $$36 \bmod -10 = -10*(\frac{36}{-10}-[\frac{36}{-10}])=36-40=-4$$
   $$-17 mod 10 = 3$$
3. 总结

- 符号：与除数同号
- 值： 除数\*（整商+1）-被除数

### Uicode 知识

   | 字符 |  Unicode  |
   |:----:|:---------:|
   | 0~9  | 0030~0039 |
   | A~Z  | 0041~005A|
   | a~z  | 0061~007A|

### Hash Function定义

将一个关键字映射为哈希表中的一个桶的地址
> 一个随机选择的关键字散列到任一一个桶中概率相同则这个函数称为均匀哈希函数

1. **除留余数法**
2. 平方取中法: 平方后适当区中间几位做关键字
3. 折叠法：将关键字分割为位数相等的几部分，然后叠加之和（叠加有移位叠加和间界叠加两种） 
4. 数字分析法：预先知道静态文件的所有关键字，每个关键字表示为某个基数r下的数值（？？）

## Overflow Handing(溢出处理)

### 开放地址法

1. 线性探测法（linear probing）
    > 按$ht[(h(k)+i )\bmod b]$来搜，当遇到第一个未满桶时，搜索停止，插入；若找不到未满桶，则说明哈希表已满，要增加表长
2. 二次探测法
3. 再散列法
4. 随机探测法

### 链地址法
