`ggplot2` 是一个用于数据可视化的强大 R 包。`geom_text()` 函数是 `ggplot2` 中的一个几何对象，用于在图表中添加文本标签。
**函数定义**:
```R
geom_text(
  mapping = NULL,
  data = NULL,
  stat = "identity",
  position = "identity",
  ...,
  parse = FALSE,
  nudge_x = 0,
  nudge_y = 0,
  check_overlap = FALSE,
  na.rm = FALSE,
  show.legend = NA,
  inherit.aes = TRUE
)
```

**详细参数**:
- `mapping`: 用于指定文本标签的映射（mapping）参数，包括 x、y 和 label。例如，`mapping = aes(x = x_var, y = y_var, label = label_var)`。
- `data`: 包含数据的数据框（data frame）或其他可供转换为数据框的对象。
- `stat`: 指定用于计算统计变量的统计方法。默认值为 "identity", 按指定数值计算，而非频次。
- `position`: 指定文本标签的位置调整方法。常见的值包括 "identity"（不调整）、"stack"（堆叠）和 "dodge"（并列）。默认值为 "identity"。
- `...`: 其他可选参数，用于修改文本标签的外观和样式，例如字体大小、颜色等。
- `parse`: 用于指定是否解析文本标签中的 R 表达式。默认值为 FALSE。
- `nudge_x` 和 `nudge_y`: 用于微调文本标签的位置。可以使用正负值进行微调。
- `check_overlap`: 指定是否检查文本标签之间的重叠。默认值为 FALSE。
- `na.rm`: 指定是否删除包含 NA 值的观测。默认值为 FALSE。
- `show.legend`: 指定是否显示图例。默认值为 NA，表示根据图层上的映射参数自动确定是否显示图例。
- `inherit.aes`: 指定是否继承父图层的美学属性。默认值为 TRUE。

**举例**:
```R
library(ggplot2)

# 创建数据框
data <- data.frame(x = c(1, 2, 3, 4, 5),
                   y = c(10, 8, 6, 4, 2),
                   label = c("A", "B", "C", "D", "E"))

# 创建散点图并添加文本标签
ggplot(data, aes(x, y)) +
  geom_point() +
  geom_text(aes(label = label), color = "red", size = 12, nudge_x = 0.2, nudge_y = 0.2)
```

在上述示例中，我们首先创建了一个包含 x、y 和 label 变量的数据框。然后，使用 `ggplot()` 函数创建了一个散点图，并使用 `geom_point()` 函数添加了散点。最后，使用 `geom_text()` 函数在每个散点上添加了文本标签。通过 `aes(label = label)` 指定了标签的映射关系，`color` 参数设置标签颜色为红色，`size` 参数设置标签大小为 12，`nudge_x` 和 `nudge_y` 参数微调标签的位置。