`ggplot2` 包中提供了一些预定义的颜色，可以通过名称直接使用。以下是一些常见的颜色名称：

1. **基本颜色：**
   - `"black"`: 黑色
   - `"red"`: 红色
   - `"green"`: 绿色
   - `"blue"`: 蓝色
   - `"purple"`: 紫色
   - `"orange"`: 橙色
   - `"pink"`: 粉色
   - `"brown"`: 棕色
   - `"gray"`: 灰色

2. **灰度颜色：**
   - `"grey20"`, `"grey40"`, ..., `"grey90"`: 不同灰度的颜色，数字表示灰度的百分比。

3. **十六进制颜色：**
   - 可以使用十六进制表示的颜色，例如 `"#FF0000"` 表示红色，`"#00FF00"` 表示绿色。

4. **颜色名称：**
   - `"skyblue"`, `"seagreen"`, `"firebrick"`, 等等。这些是一些常见颜色的名称。

5. **调色板：**
   - `scale_fill_brewer()`, `scale_color_brewer()`: 使用调色板，如`"Blues"`、`"Greens"`等。

6. **其他颜色函数：**
   - `scale_fill_manual()`, `scale_color_manual()`: 使用自定义颜色，可以传递一个颜色向量。

以下是一个示例，展示如何在`ggplot2`中使用颜色：

```R
library(ggplot2)

# 创建一个数据框
data <- data.frame(
  x = c(1, 2, 3, 4),
  y = c(10, 15, 13, 8)
)

# 使用 ggplot2 创建散点图，并指定颜色为红色
ggplot(data, aes(x, y)) +
  geom_point(color = "red") +
  labs(title = "Scatter Plot", x = "X-axis", y = "Y-axis")
```

在上述代码中，`color = "red"` 指定了散点的颜色为红色。你可以根据需要替换为其他颜色名称或十六进制表示。