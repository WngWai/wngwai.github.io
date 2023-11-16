在R语言中，`nlevels()`函数用于**获取因子（factor）对象的水平数量**。

**函数定义**：
```R
nlevels(x)
```

**参数**：
- `x`：一个因子对象。

**示例**：
以下是使用`nlevels()`函数获取因子水平数量的示例：

```R
# 示例因子
factor_vector <- factor(c("A", "B", "A", "C", "B", "C"))

# 获取因子的水平数量
num_levels <- nlevels(factor_vector)

# 打印因子的水平数量
print(num_levels)
```

在上述示例中，我们创建了一个示例因子`factor_vector`，其中包含了一些水平。

然后，我们使用`nlevels()`函数获取`factor_vector`的水平数量，并将结果保存在`num_levels`中。

最后，我们打印出`num_levels`，它表示了`factor_vector`的水平数量。

以下是打印出的内容：

```
[1] 3
```

在上述输出中，我们可以看到`factor_vector`共有3个水平。