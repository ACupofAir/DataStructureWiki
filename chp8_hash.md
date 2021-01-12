[:car:...](README.md)

# Chapter8 Hash

## Hash Function
### 异号mod
1. 定义
$$A \bmod B=B*(\frac{A}{B}-[\frac{A}{B}])$$
> 取整是向下取整
2. 实例
$$36 \bmod -10 = -10*(\frac{36}{-10}-[\frac{36}{-10}])=36-40=-4$$
$$-17 mod 10 = 3$$
3. 总结
* 符号：与除数同号
* 值： 除数*（整商+1）-被除数

## Overflow Handing