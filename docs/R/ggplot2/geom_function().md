在R语言的`ggplot2`包中，确实存在`geom_function()`函数，用于在绘图中**添加自定义函数**的曲线。
**函数定义**：
```R
geom_function(fun, ..., n = 101, inherit.aes = TRUE)
```
**参数**：
- `fun`：自定义函数，用于定义曲线的形状。函数应接受一个输入向量，并返回一个输出向量。在函数中，可以使用R语言中的任何操作和函数。
- `...`：其他参数，用于传递给`fun`函数。
- `n`：指定在绘图中使用多少个点来绘制曲线。默认值为101，即绘制101个点。
- `inherit.aes`：逻辑值，表示是否继承绘图中的美学参数。默认为`TRUE`，表示继承。
```R
library(ggplot2)

# 自定义函数
my_function <- function(x) {
  exp(-x) * sin(2 * pi * x)
}

# 创建数据框
data <- data.frame(x = seq(0, 5, length.out = 100))

# 绘制图形
ggplot(data, aes(x = x)) +
  geom_function(fun = my_function, color = "blue", size = 1) +
  labs(title = "Custom Function Curve")
```

在上面的示例中，我们首先定义了一个自定义函数`my_function()`，该函数接受一个输入向量`x`并返回一个输出向量。然后，我们创建了一个包含`x`值的数据框。最后，我们使用`ggplot2`包中的`ggplot()`函数创建一个绘图对象，并使用`geom_function()`函数添加自定义函数的曲线。我们通过`color`和`size`参数设置曲线的颜色和线条粗细，并使用`labs()`函数设置图形的标题。

请注意，`geom_function()`函数允许您绘制任意自定义函数的曲线，只需将自定义函数传递给`fun`参数即可。您可以根据需要调整其他参数来自定义曲线的外观和样式。

### stat_function()和geom_function()的区别
`stat_function()`和`geom_function()`是`ggplot2`包中用于绘制函数曲线的两个函数，它们之间有一些区别。

1. `stat_function()`：这个函数用于在图形上添加一个函数曲线。它通过指定一个函数来创建一个曲线，并将其绘制在已有的图形上。通常与其他图层函数（如`geom_point()`、`geom_line()`等）一起使用，以便在同一图形中显示数据点和函数曲线。

   ``stat_function()`的用法示例：
   ```R
   ggplot(data, aes(x = x)) +
     geom_point(aes(y = y)) +
     stat_function(fun = my_function, aes(colour = "Function"))
   ```

2. `geom_function()`：这个函数用于绘制一个函数曲线，并创建一个新的图形。它可以直接绘制函数曲线，而不需要其他数据点的存在。可以通过指定函数和绘制范围来自定义曲线的形状和位置。

   ``geom_function()`的用法示例：
   ```R
   ggplot() +
     geom_function(fun = my_function, aes(x = x), col = "blue")
   ```

总结起来，`stat_function()`用于在现有的图形上添加函数曲线，**通常与其他图层函数一起使用**，而`geom_function()`用于**创建一个新的图形**，并直接绘制函数曲线。它们的使用取决于你的需求和所需的图形效果。