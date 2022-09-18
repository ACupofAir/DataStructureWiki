[:car:...](README.md)

# Chapter7 Sort

- [复杂度](#复杂度)
- [Quick Sort](#quick-sort)

## 复杂度

> 每种排序的最好最差平均复杂度，稳定性

|    算法    |  最坏复杂度   | 最好复杂度 |  平均复杂度   | 空间复杂度 | 稳定性 |
| :--------: | :-----------: | :--------: | :-----------: | :--------: | :----: |
|  插入排序  | n<sup>2</sup> |     n      | n<sup>2</sup> |     1      |  稳定  |
|  希尔排序  |     nlogn     |   unkown   |     nlogn     |     1      | 不稳定 |
|  快速排序  | n<sup>2</sup> |   nlogn    |     nlogn     |   nlogn    | 不稳定 |
|  归并排序  |     nlogn     |   nlogn    |     nlogn     |     n      |  稳定  |
| 堆排序排序 |     nlogn     |   nlogn    |     nlogn     |     1      | 不稳定 |

## Quick Sort

> - 平均 nlogn, 最差 n<sup>2</sup>
> - 轴元素选择： 默认最左边那个
> - 算法很容易的，按书上的代码来，不同代码形成的递归表不一样，主要看中轴元素互换时的选择

```python
# 逻辑上最简洁的快排
def quickSort(lst):
    if len(lst) > 1:
        left = [x for x in lst if x > lst[0]]
        mid = [x for x in lst if x == lst[0]]
        right = [x for x in lst if x < lst[0]]
        return quickSort(left) + mid + quickSort(right)
    else:
        return lst
```
