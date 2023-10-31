[参考]([ggplot2学习笔记-修改坐标轴刻度_ggplot x轴文字旋转45-CSDN博客](https://blog.csdn.net/qq_42458954/article/details/81154270#%E5%A6%82%E4%BD%95%E4%BF%AE%E6%94%B9%E5%9D%90%E6%A0%87%E8%BD%B4%E7%9A%84%E6%A0%87%E7%AD%BE%E5%86%85%E5%AE%B9%E5%A4%A7%E5%B0%8F%E5%AD%97%E4%BD%93%E9%A2%9C%E8%89%B2%E5%8A%A0%E7%B2%97%E4%BD%8D%E7%BD%AE%E8%A7%92%E5%BA%A6))
函数是R语言中用于**调整图形比例尺**的一组函数。这些函数用于改变绘图中的轴、颜色、大小等比例尺的设置。
- `scale_x_continuous()`和`scale_y_continuous()`：用于调整x轴和y轴的连续型变量的比例尺。
  - `limits`：指定轴的取值范围。
  - `breaks`：用于指定刻度线的位置。
  - `labels`：用于指定刻度线的标签。
  
- `scale_x_discrete()`和`scale_y_discrete()`：用于调整x轴和y轴的离散型变量的比例尺。
  - `limits`：指定轴的取值范围。
  - `breaks`：用于指定刻度线的位置。
  - `labels`：用于指定刻度线的标签。

- `scale_color_*()`和`scale_fill_*()`：用于调整颜色变量的比例尺。
  - `values`：用于指定颜色的取值范围或自定义颜色。
  - `guide`：用于指定颜色图例的类型和位置。
  
- `scale_size_*()`：用于调整点大小或线条宽度的比例尺。
  - `range`：指定点大小或线条宽度的取值范围。
  - `guide`：用于指定大小图例的类型和位置。

这是一个使用`scale_*()`函数的示例：

```R
library(ggplot2)

# 创建一个散点图，并调整比例尺
ggplot(data = mtcars, aes(x = wt, y = mpg, color = cyl, size = hp)) +
  geom_point() +
  scale_x_continuous(limits = c(0, 6), breaks = seq(0, 6, 1), labels = c("0", "1", "2", "3", "4", "5", "6")) +
  scale_y_continuous(limits = c(0, 40), breaks = seq(0, 40, 10), labels = c("0", "10", "20", "30", "40")) +
  scale_color_manual(values = c("blue", "red", "green"), guide = guide_legend(title = "Cylinders")) +
  scale_size(range = c(2, 10), guide = guide_legend(title = "Horsepower")) +
  labs(title = "Weight vs. MPG",
       x = "Weight",
       y = "MPG")
```

在这个示例中，我们使用了`mtcars`数据集的`wt`（车重）和`mpg`（每加仑英里数）列绘制了一个散点图，并使用`scale_x_continuous()`和`scale_y_continuous()`函数调整了x轴和y轴的比例尺。我们使用`scale_color_manual()`函数指定了颜色的取值范围和图例的标题，使用`scale_size()`函数指定了点大小的取值范围和图例的标题。