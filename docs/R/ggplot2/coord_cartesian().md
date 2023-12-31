`coord_cartesian()` 函数是 ggplot2 包中用于**设置坐标系范围的函数**。它可以用来限制绘图的可视化范围，而不改变数据的实际范围。
```R
coord_cartesian(xlim = NULL, ylim = NULL, xlim_expand = c(0, 0), ylim_expand = c(0, 0))
```

参数说明：
- `xlim`: 用于设置 x 轴的可视化范围，输入一个长度为2的向量，包含最小值和最大值。默认为 `NULL`，表示不对 x 轴范围进行限制。
- `ylim`: 用于设置 y 轴的可视化范围，输入一个长度为2的向量，包含最小值和最大值。默认为 `NULL`，表示不对 y 轴范围进行限制。
- `xlim_expand`: 用于设置坐标轴范围的扩展。默认情况下，坐标系会自动扩展一定比例的空间，以确保数据点不会紧贴边界。可以使用 `xlim_expand` 设置为 `c(0, 0)` 来禁用这种扩展。
- `ylim_expand`: 用于设置坐标轴范围的扩展。默认情况下，坐标系会自动扩展一定比例的空间，以确保数据点不会紧贴边界。可以使用 `ylim_expand` 设置为 `c(0, 0)` 来禁用这种扩展。
示例：
```R
library(ggplot2)

# 示例数据框
df <- data.frame(x = 1:10, y = 1:10)

# 绘制散点图
ggplot(df, aes(x, y)) +
  geom_point() +
  coord_cartesian(xlim = c(2, 8), ylim = c(3, 9))
```

在上述示例中，我们创建了一个数据框 `df`，其中包含两个变量 `x` 和 `y`，分别取值为 1 到 10。我们使用 `ggplot()` 创建一个绘图对象，并使用 `aes()` 函数指定 `x` 和 `y` 作为散点图的 x 轴和 y 轴变量。

然后，我们使用 `geom_point()` 绘制散点图。在 `coord_cartesian()` 函数中，我们使用 `xlim` 参数将 x 轴的可视化范围限制为 2 到 8，使用 `ylim` 参数将 y 轴的可视化范围限制为 3 到 9。这样，绘图将只显示指定范围内的数据点，而不改变数据的实际范围。

这是一个简单的示例，可以根据实际需求调整 `coord_cartesian()` 函数的参数来控制绘图的坐标系范围。