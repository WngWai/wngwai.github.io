在R语言中，`stat_density()`函数通常用于在图形中绘制密度估计图。

**函数定义**：
```R
stat_density(
  mapping = NULL,
  data = NULL,
  geom = "area",
  position = "identity",
  ...,
  bw = "nrd0",
  adjust = 1,
  kernel = "gaussian",
  n = 512,
  trim = TRUE,
  na.rm = FALSE,
  show.legend = NA,
  inherit.aes = TRUE
)
```

**参数**：
- `mapping`：用于映射数据到图形属性的参数。
- `data`：用于绘图的数据框。
- `geom`：指定使用的几何对象类型。通常为"area"（默认值）。
- `position`：指定数据在图形中的放置方式。通常为"identity"（默认值）。
- `...`：其他传递给`geom_area()`的参数。
- `bw`：指定密度估计的带宽选择方法。通常为"nrd0"（默认值）。
- `adjust`：带宽调整参数，用于调整带宽的大小。
- `kernel`：指定使用的核函数类型。通常为"gaussian"（默认值）。
- `n`：指定生成密度估计的点数。
- `trim`：指定是否在估计密度时修剪极端值。通常为TRUE（默认值）。
- `na.rm`：指定是否移除包含NA值的观测。通常为FALSE（默认值）。
- `show.legend`：指定是否显示图例。
- `inherit.aes`：指定是否继承父图层的美学属性。

**示例**：
以下是使用`stat_density()`函数绘制密度估计图的示例：

```R
# 加载ggplot2包 
library(ggplot2) 
# 创建示例数据 
data <- data.frame(x = rnorm(1000)) 
# 绘制密度图 
ggplot(data, aes(x)) + stat_density(geom = "line", fill = "blue", span = 0.5)
```

在上述示例中，我们首先创建了一个包含随机正态分布数据的数据集。

然后，我们使用`ggplot2`包中的函数创建了一个基础的绘图对象，并使用`geom_density()`函数添加了`stat_density()`函数的默认设置，绘制了密度估计图。

最后，我们通过`ggplot()`函数展示了绘图结果。

请注意，`stat_density()`函数通常结合`geom_density()`函数一起使用，以便在图形中绘制密度估计图。您可以根据需要设置参数和数据。