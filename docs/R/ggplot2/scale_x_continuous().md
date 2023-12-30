是 ggplot2 包中用于**调整 x 轴连续变量**的函数。它可以修改 x 轴的**显示范围、标签、刻度和其他属性**，以便更好地呈现数据。

```R
scale_x_continuous()
```

- `name`：指定 x 轴的名称或标题。

- `breaks`：指定 x 轴刻度的位置。可以使用**数字向量**来指定刻度的位置。

breaks = data_q1$air_date。x能等距隔开
![Pasted image 20231226165543](attachments/Pasted%20image%2020231226165543.png)


- `labels`：指定 x 轴刻度标签的**显示文本**。可以使用字符向量来指定刻度标签的文本。
可以理解为刻度**显示的别名**，如果2011-08-22的形式不合适，可以设置别名

- `limits`：指定 x 轴显示的范围。可以使用数字向量来指定范围的最小值和最大值。

- `expand`：指定 x 轴显示范围的扩展因子。可以使用数字向量 `[a, b]` 来设置扩展因子，其中 `a` 控制范围的下限扩展，`b` 控制范围的上限扩展。

- `trans`：指定 x 轴坐标轴的变换函数。可以使用函数如 `log10`、`sqrt` 等来对坐标轴进行变换。

下面是一个示例，展示如何使用 `scale_x_continuous()` 函数调整 x 轴的属性：
```R
library(ggplot2)

# 创建示例数据
df <- data.frame(
  x = c(1, 2, 3, 4, 5),
  y = c(2, 4, 6, 8, 10)
)

# 绘制散点图，并调整 x 轴的属性
ggplot(df, aes(x, y)) +
  geom_point() +
  scale_x_continuous(
    name = "X轴",
    breaks = c(1, 3, 5),
    labels = c("一", "三", "五"),
    limits = c(0, 6),
    expand = c(0.05, 0),
    trans = "log10"
  )
```

在上述示例中，我们创建了一个包含 x 和 y 值的数据框 `df`，然后使用 `ggplot()` 函数创建绘图对象，并使用 `geom_point()` 添加散点图。通过 `scale_x_continuous()` 函数，我们调整了 x 轴的多个属性，包括名称、刻度位置、刻度标签、显示范围、扩展因子和变换函数。

你可以根据自己的数据和需求，通过调整这些参数来定制和美化 x 轴。此外，`scale_x_continuous()` 还有其他参数可以使用，例如 `limits`（限制范围的自动计算）和 `breaks`（自定义刻度位置），你可以根据需要查阅 ggplot2 的文档来进一步了解。

### 设置直方图初始值
[scale_x_continuous()](.md) 限制了坐标轴的范围，但分组还是默认分组
```R
# input data
df_ppg <- read.csv("./data/NBAPlayerPts.csv")

# 
ggplot(df_ppg) +
  geom_histogram(aes(x=PPG)) +
  scale_x_continuous(limits = c(10, 30))
```
![Pasted image 20231108201222](attachments/Pasted%20image%2020231108201222.png)


把x轴的坐标和geom_histogram()中的组距、组数限制下，发现默认分组是11-13，而非10-12！
```R
# input data
df_ppg <- read.csv("./data/NBAPlayerPts.csv")

# 
ggplot(df_ppg) +
  geom_histogram(aes(x = PPG), binwidth = 2, bins = 15) +
  scale_x_continuous(breaks = seq(10,30,2), limits = c(10, 30)) +
  scale_y_continuous(breaks = seq(1,18))
```

![Pasted image 20231108224752](attachments/Pasted%20image%2020231108224752.png)