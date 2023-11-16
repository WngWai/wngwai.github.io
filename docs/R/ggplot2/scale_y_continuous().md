在R语言中，`scale_y_continuous()`函数是ggplot2包中的一个函数，用于**调整图形的y轴刻度和标签**。

**函数定义**：
```R
scale_y_continuous(
  name = waiver(),
  breaks = waiver(),
  labels = waiver(),
  limits = NULL,
  expand = waiver(),
  oob = censor,
  na.value = NA_real_,
  trans = "identity",
  guide = "numeric",
  position = "left",
  sec.axis = NULL,
  reverse = FALSE,
  n.dodge = if (is.numeric(position)) 1 else "preserve",
  super = NULL,
  ...,
  minor_breaks = waiver(),
  minor_breaks_width = NULL
)
```

**参数**：
- `name`：y轴的名称。

- `breaks`：y轴**刻度的位置**。可以是一个向量，表示刻度的位置；或者是一个函数，用于计算刻度的位置。

- `labels`：y轴**刻度的标签**。可以是一个向量，表示刻度的标签；或者是一个函数，用于计算刻度的标签。

- `limits`：y轴的**取值范围**。可以是一个包含两个元素的向量，表示最小值和最大值。

- `expand`：y轴刻度扩展的比例因子。

- `oob`：用于处理超出限制范围的值的函数。
- `na.value`：缺失值的替代值。
- `trans`：y轴数值的变换函数。
- `guide`：y轴的图例类型。
- `position`：y轴的位置。
- `sec.axis`：辅助y轴的设置。
- `reverse`：是否反转y轴的方向。
- `n.dodge`：用于分组变量的刻度宽度。
- `super`：辅助y轴的设置。
- `...`：其他可选参数。
- `minor_breaks`：次要刻度的位置。
- `minor_breaks_width`：次要刻度的宽度。

**示例**：
以下是使用`scale_y_continuous()`函数调整y轴刻度和标签的示例：

```R
library(ggplot2)

# 示例数据
data <- data.frame(x = 1:10, y = 1:10^6)

# 创建基础图形
plot <- ggplot(data, aes(x, y)) + geom_point()

# 调整y轴刻度和标签
plot <- plot + scale_y_continuous(
  breaks = c(0, 100000, 500000, 1000000),
  labels = c("0", "100k", "500k", "1M"),
  limits = c(0, 1200000),
  name = "Y-Axis"
)

# 打印图形
print(plot)
```

在上述示例中，我们首先加载了ggplot2包，并创建了一个示例数据框`data`，其中包含两列数据`x`和`y`。

然后，我们创建了一个基础图形`plot`，使用`geom_point()`添加散点图层。

接下来，我们使用`scale_y_continuous()`函数调整y轴的刻度和标签。在示例中，我们指定了刻度的位置`breaks`为0、100000、500000和1000000，并指定了相应的标签`labels`。我们还使用`limits`参数设置y轴的取值范围。

最后，我们通过`print(plot)`打印出调整后的图形。
