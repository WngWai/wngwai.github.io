[ggplot2作图教程](https://zhuanlan.zhihu.com/p/370223674)

- 数据dataset：作图用的原始数据；

- 美学 aes(): 几何或者统计对象的美学，比如位置，颜色，大小，形状等；

- 几何图形 geom_* :表示数据的**几何图形**；

- 主题 theme(): 图形的整体视觉默认值，如背景、网格、轴、默认字体、大小和颜色

- 刻度 scale_(): 数据与美学维度之间的映射，比如图形宽度的数据范围；

- 坐标系统 coord_: 数据的转换；

- 面 facet_: 数据图表的排列

- 统计转换 stat_: 数据的统计，对数据进行处理 ，比如百分位，拟合曲线或者和；
![Pasted image 20231005110243](ggplot2/attachments/Pasted%20image%2020231005110243.png)

---
### 画布：数据集+美学
[ggplot()](ggplot2/ggplot().md) 创建一个基本的绘图对象base(就是**画布**)！在画布的基础上再叠加各种要素。指定**数据**集，设置数据和图形的整体属性。在上面可以叠加多个图形

[aes()](ggplot2/aes().md) x,y轴映射关系，定义图形的映射关系。指定数据的变量与图形的视觉属性之间的对应关系，如 x 轴位置、y 轴位置、颜色、形状等。

### 几何形状层：[geom_()](ggplot2/geom_().md)
真正意义上的在画布上呈现出来几个图形

[color详情](ggplot2/color详情.md)

[geom_point()](ggplot2/geom_point().md) 画散点图，**数据映射**

[geom_line()](ggplot2/geom_line().md) 画折线图

[geom_smooth()](ggplot2/geom_smooth().md)画创建平滑拟合曲线，规避一些**离群极端点**

[geom_bar()](ggplot2/geom_bar().md) 画柱状图(条形图)，处理**分类型数据**

[geom_col()](ggplot2/geom_col().md) 默认下直接用数值画柱状图

[geom_histogram()](ggplot2/geom_histogram().md) 画直方图，处理**数值型数据**

[geom_text()](ggplot2/geom_text().md) 在图形中添加**文本标签**

[geom_boxplot()](ggplot2/geom_boxplot().md) 箱线图

[geom_vline()](ggplot2/geom_vline().md) 垂直线函数

[geom_density()](ggplot2/geom_density().md) 根据数值，计算概率密度曲线

[geom_function()](ggplot2/geom_function().md) 绘制自定义或匿名函数曲线，创建一个新的图形

[stat_function()](ggplot2/stat_function().md)绘制自定义或匿名函数的曲线，通常与其他图层函数一起使用

### 辅助显示层
[theme()](ggplot2/theme().md)设置图形的主题，包括背景、标题、轴标签、图例等的**外观和样式**，美化作用

[labs()](ggplot2/labs().md)设置图形的**标签**，包括标题、轴标签、图例标题等。

[scale_x_continuous()](ggplot2/scale_x_continuous().md) 调整图形的x轴**刻度和修改标签文本**

[scale_y_continuous()](ggplot2/scale_y_continuous().md)调整图形的y轴刻度和标签

- `scale_color_*()`: 设置图形中**填充颜色和边框颜色**的属性。

	[scale_color_manual()](ggplot2/scale_color_manual().md)手动调整颜色映射

- `scale_fill_*()`
	scale_fill_manual(): 手动设置**离散变量的填充颜色**。可以指定每个离散值对应的具体颜色。
	
	scale_fill_gradient(): 使用**连续变量的值来创建填充颜色的渐变**。可以设置渐变的起始和结束颜色。

	scale_fill_gradientn(): 使用连续变量的值来创建填充颜色的渐变，可以指定多个颜色。

	scale_fill_gradient2(): 类似于scale_fill_gradient()，但允许指定**中间值**的颜色。

	scale_fill_hue(): 使用**色相环**来设置离散变量的填充颜色，颜色按照色相环的顺序分配。

	scale_fill_brewer(): 使用**RColorBrewer**包中的调色板来设置离散变量的填充颜色。

- `coord_*` ： 控制绘图的坐标系统和坐标轴的显示方式。它们允许您修改绘图的坐标轴刻度、范围和比例，以及坐标轴的显示方式

	[coord_cartesian()](ggplot2/coord_cartesian().md) 约束坐标显示的范围

	[coord_flip()](ggplot2/coord_flip().md) x和y轴呼唤

	[coord_polar()](ggplot2/coord_polar().md)将坐标系转换为**极坐标系**

	coord_map()

### 分面绘图
[facet_grid()](ggplot2/facet_grid().md) 基于一个因子进行分面，如z，分割x~y

[facet_wrap()](ggplot2/facet_wrap().md) 基于一个或多个因子分面，如z1、z2...，分割x~y

---
### 统计
[stat_summary()](ggplot2/stat_summary().md) 

`stat_*`函数用于**添加统计变换**（statistical transformation）到图表中，以便对数据进行汇总、计算或转换。这些函数提供了各种统计变换选项，可以根据数据的特点和需求进行灵活的数据处理。

`stat_bin()`：用于进行直方图或柱状图的统计变换，将数据分组为离散的区间并计算每个区间的频数或密度。

`stat_summary()`：用于进行汇总统计，计算每组数据的统计摘要，如均值、中位数、标准差等，并将结果绘制为点、线、矩形等形状。

`stat_smooth()`：用于拟合平滑曲线或回归曲线，根据数据的趋势绘制平滑的曲线，常用于数据的趋势分析和模型拟合。

`stat_boxplot()`：用于绘制箱线图，显示数据的分布情况，包括中位数、四分位数、异常值等。

[stat_density()](ggplot2/stat_density().md)：用于生成密度图，估计数据的概率密度函数，可用于分布形状的可视化。

`stat_ecdf()`：用于生成经验累积分布函数（empirical cumulative distribution function），展示数据的累积分布情况。

`stat_ellipse()`：用于绘制椭圆，显示二维数据的椭圆包络，常用于数据的相关性分析和聚类可视化。