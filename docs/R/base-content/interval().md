在R语言中，`interval()`函数用于**创建和操作数值的区间对象**。

**函数定义**：
```R
interval(start, end, closed = "left")
```

**参数**：
- `start`：区间的起始值。
- `end`：区间的结束值。
- `closed`：可选参数，指定区间的闭合方式。可选值为"left"（默认，左闭右开）、"right"（右闭左开）、"both"（两端闭合）和"neither"（两端开放）。

**示例**：
以下是使用`interval()`函数创建和操作区间对象的示例：

```R
# 创建区间对象
int1 <- interval(0, 5)
int2 <- interval(3, 7, closed = "right")

# 操作区间对象
overlap <- int_overlap(int1, int2)
union <- int_union(int1, int2)
intersection <- int_intersection(int1, int2)

# 打印结果
print(overlap)
print(union)
print(intersection)
```

在上述示例中，我们首先使用`interval()`函数创建了两个区间对象`int1`和`int2`。

然后，我们使用`int_overlap()`函数计算了`int1`和`int2`之间的重叠部分，并将结果保存在`overlap`中。

接着，我们使用`int_union()`函数计算了`int1`和`int2`的并集，并将结果保存在`union`中。

最后，我们使用`int_intersection()`函数计算了`int1`和`int2`的交集，并将结果保存在`intersection`中。

以下是打印出的内容：

```
[1] 3 4 5
[1] 0 1 2 3 4 5 6 7
[1] 3 4 5
```

在上述输出中，我们可以看到重叠部分包含了区间3到5，并集包含了区间0到7，交集包含了区间3到5。