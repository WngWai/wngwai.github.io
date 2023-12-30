`theme()`函数用于自定义绘图的**外观和样式**，包括背景、标题、轴标签等。
**函数定义**：
```R
theme(...)
```
**参数**：
`theme()`函数没有固定的参数列表，它接受一系列参数，用于自定义绘图的外观和样式。

在具体使用中逐步补充！
**常用参数**：
以下是`theme()`函数中常用的参数（不完全列表）：
- `axis.text`: **轴标签**的**样式**。axis.text.x修改 x 轴刻度标签，axis.text.y修改 y 轴刻度标签。
axis.text.x = element_text(angle = 90)，本身是x的标签样式是横着的，旋转90度，变成竖的。能不能将具体的字符保持横着（歪着头看很费劲）？？？
![Pasted image 20231226170320](attachments/Pasted%20image%2020231226170320.png)

- `axis.title`: **轴标题**的样式。axis.title.x修改 x 轴标题，axis.title.y修改 y 轴标题。

- `axis.ticks`: **轴刻度线和刻度标签**的样式，axis.ticks.x修改 x 轴刻度线，axis.ticks.y修改 y 轴刻度线。

- `legend.title`: **图例标题**的样式。
- `legend.text`: **图例标签**的样式。

- `panel.background`: 绘图区域的**背景**样式。
- `panel.grid`: 绘图区域的**网格**样式。panel.grid.major.x修改 x 轴的主要网格线，panel.grid.minor.y修改 y 轴的次要网格线。
```R
library(ggplot2)

# 创建一个简单的散点图
p <- ggplot(mtcars, aes(x = mpg, y = wt)) +
  geom_point()

# 设置线条的颜色为红色，粗细为2，类型为虚线，端点样式为圆形
p + theme(
  panel.grid.major = element_line(color = "red", size = 2, linetype = "dashed", lineend = "round")
)
```



- `plot.background`: 整个**图形的背景**样式。
- `plot.title`: **图形标题**的样式。
- `plot.subtitle`: 修改**图形副标题**的外观。
- `plot.caption`: 修改**图形注释**的外观。

- `strip.text`: 修改**分面图中子图标签**的外观。




**示例**：
以下是一个使用`theme()`函数自定义绘图样式的示例：
```R
library(ggplot2)

# 创建数据集
data <- data.frame(
  x = c(1, 2, 3, 4, 5),
  y = c(2, 4, 6, 8, 10)
)

# 创建基本图形
p <- ggplot(data, aes(x, y)) +
  geom_line() +
  labs(title = "My Plot", x = "X", y = "Y")

# 自定义绘图样式
p + theme(
  plot.title = element_text(color = "blue", size = 16),
  axis.title = element_text(color = "red", size = 14),
  axis.text = element_text(color = "green", size = 12),
  panel.background = element_rect(fill = "gray")
)
```

```R
library(ggplot2)

# 示例数据集
df <- data.frame(x = 1:5, y = c(2, 4, 6, 8, 10))

# 创建绘图对象，定义映射关系
p <- ggplot(data = df, mapping = aes(x = x, y = y))

# 添加点图层
p <- p + geom_point()

# 修改图形主题
p <- p + theme(
  plot.title = element_text(color = "blue", size = 16),
  axis.title.x = element_text(face = "bold"),
  axis.text.y = element_text(angle = 90),
  legend.position = "bottom"
)

# 显示图形
print(p)
```


## 样式函数
### element_rect()矩形元素（如图例背景、面板背景等）的样式
在`ggplot2`中，`theme()`函数用于自定义绘图的外观和样式。`element_rect()`函数是`theme()`函数中的一个子函数，用于设置**矩形元素的样式**，如图例背景、面板背景等。下面是一些常用的`element_rect()`函数的参数及其详细介绍和示例：
1. `fill`: 设置矩形填充的颜色。
```R
# 示例
ggplot() +
  theme(
    legend.background = element_rect(fill = "lightblue"),
    panel.background = element_rect(fill = "lightgray")
  )
```

2. `colour`或`color`: 设置矩形边框的颜色。
```R
# 示例
ggplot() +
  theme(
    legend.background = element_rect(color = "blue"),
    panel.background = element_rect(color = "gray")
  )
```

3. `size`: 设置矩形边框的粗细。
```R
# 示例
ggplot() +
  theme(
    legend.background = element_rect(size = 1),
    panel.background = element_rect(size = 0.5)
  )
```

4. `linetype`: 设置矩形边框的类型，如实线（"solid"）、虚线（"dashed"）、点线（"dotted"）等。
```R
# 示例
ggplot() +
  theme(
    legend.background = element_rect(linetype = "dashed"),
    panel.background = element_rect(linetype = "dotted")
  )
```

5. `inherit.blank`: 设置是否继承`element_blank()`函数的效果，即是否隐藏矩形元素。
```R
# 示例
ggplot() +
  theme(
    legend.background = element_rect(inherit.blank = TRUE)  # 继承隐藏
  )
```

这些是`element_rect()`函数中一些常用的参数，你可以根据需要进行调整。通过在`theme()`函数中使用`element_rect()`函数，并设置相应的参数，你可以自定义绘图中矩形元素的样式，例如图例背景、面板背景等。

### element_text()文本元素的样式
在`ggplot2`中，`theme()`函数用于自定义绘图的外观和样式。`element_text()`函数是`theme()`函数中的一个子函数，用于设置**文本元素的样式**。下面是一些常用的`element_text()`函数的参数及其详细介绍和示例：
1. `family`: 设置文本的**字体系列**。可以指定多个字体作为备选项，用逗号分隔。默认值为`NULL`，表示使用默认字体。"Songti SC"宋体
```R
# 示例
ggplot() +
  theme(
    axis.text = element_text(family = "Arial")
  )
```

2. `face`: 设置文本的**字体样式**，如粗体（"bold"）、斜体（"italic"）、正常（"plain"）等。默认值为`"plain"`。
```R
# 示例
ggplot() +
  theme(
    axis.text = element_text(face = "bold")
  )
```

3. `color`或`colour`: 设置文本的颜色。
```R
# 示例
ggplot() +
  theme(
    axis.text = element_text(colour = "red")
  )
```

4. `size`: 设置文本的大小。
```R
# 示例
ggplot() +
  theme(
    axis.text = element_text(size = 12)
  )
```

5. `angle`: 设置文本的**旋转角度**（以**度**为单位）。
```R
# 示例
ggplot() +
  theme(
    axis.text = element_text(angle = 45)
  )
```

6. `hjust`和`vjust`: 设置文本的**水平对齐和垂直对齐方式**，取值范围为0到1之间。
```R
# 示例
ggplot() +
  theme(
    axis.text = element_text(hjust = 0.5, vjust = 0.5)
  )
```

7. `lineheight`: 设置**文本的行高**，取值范围为0到1之间。
```R
# 示例
ggplot() +
  theme(
    axis.text = element_text(lineheight = 0.8)
  )
```

这些是`element_text()`函数中一些常用的参数，你可以根据需要进行调整。通过在`theme()`函数中使用`element_text()`函数，并设置相应的参数，你可以自定义绘图的文本元素样式，包括坐标轴标签、图例标签、标题等。

### element_line()线条元素的样式
在`ggplot2`中，`theme()`函数用于自定义绘图的外观和样式。`element_line()`函数是`theme()`函数中的一个子函数，用于**设置线条元素的样式**。下面是一些常用的`element_line()`函数的参数及其详细介绍和示例：
1. `colour`或`color`: 设置线条的颜色。
```R
# 示例
ggplot() +
  theme(
    panel.grid.major = element_line(colour = "gray"),
    panel.grid.minor = element_line(colour = "lightgray")
  )
```

2. `size`: 设置线条的粗细。
```R
# 示例
ggplot() +
  theme(
    panel.grid.major = element_line(size = 1),
    panel.grid.minor = element_line(size = 0.5)
  )
```

3. `linetype`: 设置线条的类型，如实线（"solid"）、虚线（"dashed"）、点线（"dotted"）等。
```R
# 示例
ggplot() +
  theme(
    panel.grid.major = element_line(linetype = "dashed"),
    panel.grid.minor = element_line(linetype = "dotted")
  )
```

4. `lineend`: 设置线条的端点样式，如圆形（"round"）、平直（"butt"）等。
```R
# 示例
ggplot() +
  theme(
    panel.grid.major = element_line(lineend = "round"),
    panel.grid.minor = element_line(lineend = "butt")
  )
```

5. `linejoin`: 设置线条的连接样式，如圆滑（"round"）、直角（"mitre"）等。
```R
# 示例
ggplot() +
  theme(
    panel.border = element_line(linejoin = "round")
  )
```

这些是`element_line()`函数中一些常用的参数，你可以根据需要进行调整。通过在`theme()`函数中使用`element_line()`函数，并设置相应的参数，你可以自定义绘图的线条元素样式，包括网格线、边框线等。

### element_blank()隐藏特定元素
`element_blank()`函数是`theme()`函数中的一个子函数，用于隐藏特定的元素，使其不显示。`element_blank()`函数没有可调整的参数，只需将其作为参数传递给相应的元素即可。以下是一些常见的使用示例：
1. 隐藏坐标轴标题：
```R
# 示例
ggplot() +
  theme(
    axis.title.x = element_blank(),
    axis.title.y = element_blank()
  )
```

2. 隐藏图例：
legend.position = "none" 隐藏了图例！
```R
# 示例
ggplot() +
  theme(
    legend.position = "none",
    legend.title = element_blank()
  )
```

3. 隐藏网格线：
```R
# 示例
ggplot() +
  theme(
    panel.grid.major = element_blank(),
    panel.grid.minor = element_blank()
  )
```

4. 隐藏面板边框：
```R
# 示例
ggplot() +
  theme(
    panel.border = element_blank()
  )
```
通过将`element_blank()`函数作为参数传递给相应的元素，可以轻松地隐藏这些元素，从而实现绘图中特定元素的隐藏效果。请注意，`element_blank()`函数通常与其他的`element_XXX()`函数（如`element_text()`、`element_line()`等）一起使用，以完全自定义绘图的外观和样式。

### element_point()
`element_point()`函数是`theme()`函数中的一个子函数，用于设置散点图中点元素的样式。下面是一些常用的`element_point()`函数的参数及其详细介绍和示例：
1. `size`: 设置点的大小。
```R
# 示例
ggplot() +
  theme(
    plot.symbol = element_point(size = 3)
  )
```

2. `shape`: 设置点的形状，可以是整数或字符值。常见的形状包括圆形（16）、三角形（17）、正方形（15）等。
```R
# 示例
ggplot() +
  theme(
    plot.symbol = element_point(shape = 16)
  )
```

3. `colour`或`color`: 设置点的颜色。
```R
# 示例
ggplot() +
  theme(
    plot.symbol = element_point(colour = "red")
  )
```

4. `fill`: 设置点的填充颜色。
```R
# 示例
ggplot() +
  theme(
    plot.symbol = element_point(fill = "blue")
  )
```

这些是`element_point()`函数中一些常用的参数，你可以根据需要进行调整。通过在`theme()`函数中使用`element_point()`函数，并设置相应的参数，你可以自定义散点图中点元素的样式，包括大小、形状、颜色等。这样可以使得你的散点图更加符合你的设计需求。