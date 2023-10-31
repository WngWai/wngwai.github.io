函数用于在 ggplot2 包中绘制箱线图。箱线图是一种常用的可视化工具，用于展示连续变量的分布情况、中位数、四分位数和异常值。
```R
geom_boxplot(mapping = NULL, data = NULL, ..., na.rm = FALSE, show.legend = NA, inherit.aes = TRUE)

```
- `mapping`：指定变量与图形属性之间的映射关系，使用 `aes()` 函数设置。常用的映射属性包括 `x`（x 轴变量）、`y`（y 轴变量）、`fill`（填充颜色）、`color`（边框颜色）等。
- `data`：一个数据框或数据集，包含要用于绘图的变量。
- `...`：其他参数，用于修改箱线图的外观和样式。
- `na.rm`：一个逻辑值，指示是否忽略包含缺失值（NA）的观测。默认为`FALSE`，即不删除缺失值。
- `show.legend`：一个逻辑值，指示是否显示图例。默认为`NA`，表示自动确定是否显示图例。
- `inherit.aes`：一个逻辑值，指示是否继承父图层的aes()映射。默认为`TRUE`，表示继承。

- `notch`：指定是否绘制箱线图的缺口（notch）。缺口可以用于比较两个或多个箱线图的中位数的差异。默认值为 `FALSE`，表示不绘制缺口。
- `varwidth`：指定是否根据样本大小调整箱线图的宽度。默认值为 `FALSE`，表示所有箱线图具有相同的宽度。
- `outlier.shape`：指定异常值的形状。默认为圆圈（"o"）。
- `outlier.colour`：指定异常值的边框颜色。

下面是一个示例，展示如何使用 `geom_boxplot()` 函数绘制箱线图：

```R
library(ggplot2)

# 创建示例数据框
data <- data.frame(group = rep(c("A", "B", "C"), each = 50),value = c(rnorm(50, mean = 5), rnorm(50, mean = 10), rnorm(50, mean = 15)))

# 绘制箱线图
ggplot(data, aes(x = group, y = value)) +
  geom_boxplot() +
  labs(title = "Boxplot", x = "Group", y = "Value")
```

在上述示例中，我们首先创建了一个名为 `data` 的数据框，其中包含了两个变量 `group` 和 `value`。然后使用 `ggplot()` 函数创建一个基本的绘图对象，并使用 `aes()` 函数将 `group` 变量映射到 x 轴，将 `value` 变量映射到 y 轴。

通过 `geom_boxplot()` 函数绘制箱线图。此处省略了参数，使用函数的默认设置。箱线图将根据 `group` 变量的不同绘制不同的箱线图。

通过调整参数和添加其他图层函数，你可以根据自己的需求绘制不同样式的箱线图，并根据需要设置填充颜色、边框颜色、异常值形状等。


### 注意的内容！！！
直线延伸到去掉离群点以后显示的**最大、最小值**！
上边界：Q3+1.5IQR
下边界：Q1-1.5IQR
最小值不超过下边界，线段正延伸到最小值点；最大值超过上边界，线段线延伸到边界内的最大值，超过边界的值散点画下
![[Pasted image 20230923161216.png]]

### 可以不分组
通常不需要手动对数据框进行分组。`geom_boxplot()` 函数会自动对数据进行分组，并根据分组绘制箱线图。
```R
group_by(lj_top30, property_region) %>% 
  ggplot() +
    geom_boxplot(aes(x = property_region, y = price_ttl)) +
    labs(title = "前top30区域房屋总价分布情况",  x = "所属区域",  y = "房屋总价",  caption = "DataSource: lj") +
    theme(axis.text.x = element_text(family = "songti sc", face = "bold", color = "black", size = 10, angle = 90), 
          plot.title = element_text(family = "songti sc", face = "bold", color = "black", size = 10, hjust = 0.5, vjust = 0,5))
ungroup(lj_top30)
```
![[Pasted image 20231018185244.png]]
