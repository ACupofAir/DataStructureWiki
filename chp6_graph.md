[:car:...](README.md)

# Chapter6 Graph
- [Represetations](#represetations)
  - [邻接矩阵(adjancency matrices)](#邻接矩阵adjancency-matrices)
  - [邻接表(adjancency list)](#邻接表adjancency-list)
    - [逆邻接表(inverse adjancency list)](#逆邻接表inverse-adjancency-list)
    - [十字链表](#十字链表)
  - [邻接多表(adjacency multilist)](#邻接多表adjacency-multilist)
- [基本操作](#基本操作)
  - [遍历](#遍历)
  - [插入](#插入)
  - [删除](#删除)
- [Shortest Paths](#shortest-paths)
  - [Dijkstra](#dijkstra)
- [AOE](#aoe)

## Represetations
### 邻接矩阵(adjancency matrices)
> Too easy...

### 邻接表(adjancency list)
> 只关心节点的出度,链表里的是以i指向的节点
#### 逆邻接表(inverse adjancency list)
> 只关心节点的入度，链表里的是指向i的节点

#### 十字链表 
> * 尤适用于有向图
>
> * |head|tail|行链接|列链接|
>   |:--:|:--:|:--:|:--:|
> * 行链接列表为邻接表，关心出度
> * 列链接列表为逆邻接表，关心入度
![](res/2021-01-16-10-15-57.png)

### 邻接多重表(adjacency multilist)
> * 适用于无向图，解决了空间的浪费，方便了遍历，插入，删除
> 
> * |m|v<sub>1</sub>|v<sub>2</sub>|link1|link2|
>   |:--:|:--:|:--:|:--:|:--:|
> * 每条边只有一个节点表示，但这个节点同时在两个链表里
> * m:标记是否被检查过
> * link1: 对应v<sub>1</sub>相关的边
> * ??

## 基本操作
### 遍历
> 尤指编个小程序（十字链表）

### 插入

### 删除

## Shortest Paths
### [Dijkstra](https://zh.wikipedia.org/wiki/%E6%88%B4%E5%85%8B%E6%96%AF%E7%89%B9%E6%8B%89%E7%AE%97%E6%B3%95)
> * 贪婪算法的计算过程，证明， 举例哪些情形下不好用
> * 约束条件： 没有负边
> * 以类似于广搜解决了单源任意目的地最短路径问题

* 复杂度

|              算法              |       最坏时间复杂度        |
|:----------------------------:|:---------------------------:|
|   使用鄰接表的戴克斯特拉算法   |     $\mathcal{O}(V^2)$      |
| 使用二叉堆优化的戴克斯特拉算法 | $\mathcal{O}((E+V)\log(V))$ |
|使用斐波那契堆优化的戴克斯特拉算法|	$\mathcal{O} (E+V\log(V))$

## AOE
> 两个表，每个事件开始的最早最迟时间