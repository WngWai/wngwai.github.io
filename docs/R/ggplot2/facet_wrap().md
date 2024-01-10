是ggplot2包中的一个函数，用于**将数据分割成多个小图**，并根据某个变量的**水平值创建多个子图**。它可用于将数据按照某个因子变量进行分组，并在每个子图中绘制相应的图形。

有空研究下
R语言ggplot笔记（三）：基础语法篇（下） - 柚子啊柚子的文章 - 知乎
https://zhuanlan.zhihu.com/p/101877243

如何使用 ggplot2 ？ - 心理统计联盟的回答 - 知乎
https://www.zhihu.com/question/24779017/answer/3188530425

```R
facet_wrap(facets, nrow = NULL, ncol = NULL, scales = "fixed", shrink = TRUE, labeller = "label_value", as.table = TRUE, switch = NULL, dir = "h", strip.position = "top")
```

- `facets`：

	vars()：vars(z1, z2)
	   
	 ~ variable：~ z1 + z2，经典表达式。表示**用于分组的因子变量z**。它可以是**单个**变量，也可以是**多个**变量的组合。

	c(z1, z2)：也可用向量的形式

- `nrow`：子图显示的**行数**。根据固定行数分布子图

- `ncol`：子图显示的**列数**。根据固定列数分布子图

同时指定子图的行、列不可靠！

- `scales`：表示**是否在子图之间共享坐标轴**。默认为"fixed"，表示每个子图具有独立的坐标轴；如果设置为"free"，则子图之间的**坐标轴可以不同**。

- `shrink`：表示是否根据子图的相对大小自动调整每个子图的大小。默认为`TRUE`。

- `labeller`：用于设置子图标签的标签器。默认为"label_value"，表示使用因子变量的值作为标签。

- `as.table`：表示是否将子图按照表格方式排列。默认为`TRUE`，表示按照表格方式排列。
- `switch`：表示是否在子图之间进行交换以获得更好的布局。默认为`NULL`，表示不进行交换。
- `dir`：表示子图的排列方向。可以是"h"（水平）或"v"（垂直）。默认为"h"。
- `strip.position`：表示子图标签（strip）的位置。可以是"top"、"bottom"、"left"或"right"。默认为"top"。

下面是一个示例，演示如何使用`facet_wrap()`函数创建分组的子图：
```R
library(ggplot2)

# 创建一个数据框
data <- data.frame(
  x = c(1, 2, 3, 4, 5),
  y = c(2, 4, 6, 8, 10),
  group = c("A", "A", "B", "B", "C")
)

# 创建散点图，并使用facet_wrap()进行分组
ggplot(data, aes(x = x, y = y)) +
  geom_point() +
  facet_wrap(~ group, nrow = 2)
```
在这个示例中，我们创建了一个数据框`data`，其中包含了x和y坐标的值，以及一个分组变量`group`。然后，使用`ggplot()`函数创建一个基本的绘图对象，并使用`geom_point()`函数添加散点图。使用`facet_wrap()`函数将数据按照`group`变量进行分组，并在每个子图中绘制相应的图形。

在输出图中，数据被分为三个子图，每个子图对应一个不同的`group`值。通过`nrow`参数，我们设置每行显示两个子图。


### 多因子
```r
g + facet_wrap(~ year + season, nrow = 4, scales = "free_x")
# free_x是指x轴的量尺可以自由变化，而y轴保持不变
```

![Pasted image 20240108092809](attachments/Pasted%20image%2020240108092809.png)