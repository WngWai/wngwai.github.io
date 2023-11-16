是dplyr包中的一个函数，用于按**照一个或多个变量对数据进行分组**操作。
![Pasted image 20231017160408](attachments/Pasted%20image%2020231017160408.png)
分组后数据整体没有变化，只是添加了分组特征说明，ungroup()就是取消这个说明，不像python直接修改了分组列的数据。

```R
group_by(.data, ...)
```

- `.data`: 要进行分组操作的数据框或数据集。
- `...`: **一个或多个变量**，用于指定分组的依据。可以是变量名、变量位置或变量表达式。

以下是一个示例，展示了如何使用`group_by()`函数对数据进行分组：
```R
library(dplyr)

# 创建一个数据框
data <- data.frame(
  category = c("A", "B", "C", "A", "B", "C"),
  value = c(10, 15, 8, 12, 9, 6)
)

# 使用group_by()函数对数据进行分组
grouped_data <- group_by(data, category)

# 对分组后的数据进行汇总统计
summary_data <- summarize(grouped_data,  mean_value = mean(value), max_value = max(value))

# 输出汇总统计结果
print(summary_data)
```

在这个示例中，我们首先创建了一个数据框`data`，其中包含了一个类别变量`category`和一个数值变量`value`。然后，使用`group_by()`函数对数据框按照`category`变量进行分组操作，将分组结果保存到`grouped_data`中。接下来，使用`summarize()`函数对分组后的数据进行汇总统计，计算了每个类别的`value`均值和最大值，并将结果保存到`summary_data`中。最后，使用`print()`函数输出汇总统计结果。

运行这段代码会输出根据类别进行分组后的汇总统计结果。在这个例子中，根据`category`变量进行分组后，每个类别的均值和最大值被计算出来并显示在结果中。

`group_by()`函数通常与其他dplyr函数（如`summarize()`、`mutate()`、`filter()`等）一起使用，以进行更复杂的数据操作和分析。

### .groups处理多级分组结构
多级分组，ungroup()可能不适用了。需要用.groups来告诉程序汇总后对多级分组的处理方式。
以group_by(flights, year, month, day)为例子
```R
daily <- group_by(flights, year, month, day)

(per_day <- summarize(daily, flights = n(), .groups = "drop_last"))
```
![Pasted image 20231023145526](attachments/Pasted%20image%2020231023145526.png)

上面将day的组分组释放了，这级再求就是按照month最优一个分组来进行汇总统计。
```R
(per_month <- summarize(per_day, flights = sum(flights), .groups = "drop_last")
```
![Pasted image 20231023145615](attachments/Pasted%20image%2020231023145615.png)
`.groups`的主要参数有4个：
- `drop_last`：汇总结束后，将当前数据集的**最低一级分组结构删除**
- `drop`：汇总结束后，将当前数据集**所有的分组结构删除**，数据集回到之前未分组的状态
- `keep`：汇总结束后，**保留**数据集当前的分组结构，即当前的分组状态
- `rowwiese`：字面上理解是每一行作为一组，实际上是指**将原有的分组结构删**除，以**汇总变量作为依据重新分组**
https://blog.csdn.net/Y1575071736/article/details/119277403


### 关于NA值的处理
**NA值单独分一组**
在R语言中，`group_by()`函数是dplyr包中的一个功能强大的函数，用于按照指定的变量对数据进行分组操作。在分组期间，`group_by()`函数会将数据集按照指定的变量进行分组，并在后续的操作中将每个组视为单独的单位。

在`group_by()`函数的默认行为中，对于包含缺失值（NA）的变量，会将其作为一个单独的组进行处理。这意味着具有缺失值的观测将被分配到一个独立的组中。

以下是一个示例，演示了`group_by()`函数在处理包含NA值的情况下的行为：

```R
library(dplyr)

# 创建一个包含NA值的数据框
df <- data.frame(
  group_var = c("A", "A", "B", "B", NA),
  value = c(1, 2, 3, 4, 5)
)

# 使用group_by对数据进行分组
grouped_df <- df %>% group_by(group_var)

# 查看分组后的数据
print(grouped_df)

### 输出
# A tibble: 5 × 2
# Groups:   group_var [3]
  group_var value
  <chr>     <dbl>
1 A             1
2 A             2
3 B             3
4 B             4
5 <NA>          5
```

在上述示例中，我们创建了一个包含NA值的数据框`df`，其中包含一个分组变量`group_var`和一个数值变量`value`。然后，我们使用`group_by()`函数将数据按照`group_var`进行分组，并将结果存储在`grouped_df`中。最后，我们打印了分组后的数据。

在输出结果中，您会注意到含有NA值的组被单独列出，而其他组则按照`group_var`的取值进行分组。这是`group_by()`函数对于NA值的默认处理方式。

需要注意的是，您可以通过设置`na.action`参数来修改`group_by()`函数对于NA值的处理方式。例如，将`na.action = na.pass`传递给`group_by()`函数，将允许NA值参与分组操作，并保留原始的NA值所在的组。

总结起来，R语言中的`group_by()`函数默认将包含NA值的变量作为一个单独的组进行处理。您可以通过设置`na.action`参数来调整对NA值的处理方式。


### 高级分组：指定范围进行分组cut()
用到[[cut()]]函数，强制按离散型变量进行分组？

```R
# 导入dplyr包
library(dplyr)

# 创建一个示例数据框
df <- data.frame(Player = c("Player1", "Player2", "Player3", "Player4", "Player5"),
                 PPG = c(15, 8, 12, 18, 23))

# 定义分组区间
breaks <- seq(10, 30, by = 2)  # 从10到30，每2为一个区间

# 使用cut函数创建分组
df <- df %>%
  mutate(PPG_Group = cut(PPG, breaks = breaks, labels = FALSE, include.lowest = TRUE)) %>%
  group_by(PPG_Group)

# 输出分组后的数据框
print(df)

```

![[Pasted image 20231108200433.png]]

**正确的做法!**
```R
# input data
df_ppg <- read.csv("./data/NBAPlayerPts.csv")

# 使用cut函数创建因子
breaks <- seq(10, 30, by = 2)
df_ppg_fre <- df_ppg %>%
  mutate(PPG_Group = cut(PPG, breaks = breaks,include.lowest = TRUE)) %>% 
  group_by(PPG_Group) %>% 
  summarise(PPG_Group_count = n(), .groups = "drop")

# 绘制柱状图
df_ppg_fre %>% 
  ggplot() +
  geom_bar(aes(x = PPG_Group, y = PPG_Group_count), stat = "identity") +
  scale_y_continuous(breaks = seq(0,20))
```

![[Pasted image 20231114144302.png]]
