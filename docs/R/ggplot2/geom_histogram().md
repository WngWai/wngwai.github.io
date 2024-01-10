在R语言中，`ggplot2`包中的`geom_histogram()`函数用于绘制**直方图**，显示定量变量的分布情况。

对连续型变量分组统计频数。千万别跟柱状图（离散变量统计频数）混淆

**函数定义**：
```R
geom_histogram(mapping = NULL, data = NULL, stat = "bin", position = "stack", ..., binwidth = NULL, bins = NULL, na.rm = FALSE, show.legend = NA, inherit.aes = TRUE)
```

**参数**：
- `mapping`：一个映射（aesthetic mapping）对象，用于映射数据变量到图形属性的**aes()函数或aes()函数的参数**。

- `data`：**数据框**。

- `stat`：统计变换的名称。默认为"bin"，表示**将数据分组为柱状图**。

- `color`：直方图**边框颜色**！

- `fill`：指定数据变量与图形的**填充颜色**映射关系，。

- `position`：柱状图的放置方式。可以是"stack"（默认，堆叠显示）或"dodge"（并列显示）。

- `binwidth`：指定柱状图的宽度，就是**组距**，用于控制分组的粒度。

- `bins`：指定**柱状图的数量**，用于控制**分组的个数**。

- `na.rm`：逻辑值，指示**是否忽略缺失值**。

- `show.legend`：用于控制是否**显示图例**。

- `inherit.aes`：逻辑值，指示**是否继承父图层的aes()映射**。

**示例**：
以下是一个使用`geom_histogram()`函数绘制直方图的示例：

```R
library(ggplot2)

# 创建数据集
data <- data.frame(
  value = rnorm(1000)
)

# 绘制直方图
ggplot(data, aes(x = value)) +
  geom_histogram(binwidth = 0.2, fill = "blue", col = "black") +
  labs(title = "Histogram", x = "Value", y = "Frequency")
```

在上述示例中，我们首先加载`ggplot2`包，并创建了一个简单的数据集 `data`，包含了一个随机生成的值。

然后，我们使用`ggplot()`函数创建了一个基本图形，并使用`aes()`函数将数据的`value`变量映射到x轴。

接下来，我们使用`geom_histogram()`函数绘制直方图。在`geom_histogram()`函数中，我们可以使用参数如`binwidth`来指定柱状图的宽度，通过控制分组的粒度来调整直方图的样式。

最后，我们使用`labs()`函数设置图形的标题和轴标签。

通过使用`geom_histogram()`函数，我们可以轻松绘制直方图以可视化定量变量的分布情况。根据需要，可以调整参数来控制直方图的样式和粒度。

### 柱状图和直方图的区别
bar chart柱状图：数据不连续，有间隔；

Histogram直方图：数据连续，无间隔。
![400](attachments/Pasted%20image%2020231006092816.png)

### 设置直方图相关参数
[scale_x_continuous()](scale_x_continuous().md) 限制了坐标轴的范围，但分组还是默认分组
```R
# input data
df_ppg <- read.csv("./data/NBAPlayerPts.csv")

# 
ggplot(df_ppg) +
  geom_histogram(aes(x=PPG)) +
  scale_x_continuous(limits = c(10, 30))
```
![Pasted image 20231108201222](attachments/Pasted%20image%2020231108201222.png)


把x轴的坐标和geom_histogram()中的组距、组数限制下，发现默认分组起始组是11-13，而非10-12！想要处理为10-12还是得转换为因子型。
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

### 将连续型变量离散化，求频率
个人的方法，老师的方法详看[table()](../base-content/table().md)中的子标题内容。

```R
# create a factor
breaks <- seq(10, 30, by = 2)
df_ppg_fre <- df_ppg %>%
  mutate(PPG_Group = cut(PPG, breaks = breaks,include.lowest = TRUE)) %>% 
  group_by(PPG_Group) %>% 
  summarise(PPG_Group_count = n(), .groups = "drop")

# plot a bar gram
df_ppg_fre %>% 
  ggplot() +
  geom_bar(aes(x = PPG_Group, y = PPG_Group_count), stat = "identity") +
  scale_y_continuous(breaks = seq(0,20))
```

![Pasted image 20231227093246](attachments/Pasted%20image%2020231227093246.png)