在 R 语言中，`aov()` 函数用于进行**方差分析**（ANOVA）的计算。它用于比较**不同组之间的均值**是否显著不同，以及确定哪些因素对于观察到的差异有显著影响。下面是对 `aov()` 函数的参数进行详细介绍和举例：

**函数语法：**
```R
aov(formula, data, subset, na.action, ...)
```

**参数说明：**
- `formula`：一个公式对象，表示要进行方差分析的模型。公式的形式为 `response ~ terms`，其中 `response` 是一个**因变量**，`terms` 是**一个或多个自变量和交互项**。例如，`y ~ x1 + x2` 表示因变量 `y` 与自变量 `x1` 和 `x2` 之间的关系。

- `data`：一个数据框，表示**包含因变量和自变量的数据**。默认为当前环境中的数据框。

- `subset`：一个逻辑向量，表示要使用的观察值的子集。默认为 NULL，表示使用所有观察值。

- `na.action`：一个函数，用于处理缺失值的方法。默认为 `na.omit`，表示**删除包含缺失值的观察值**。

- `...`：其他参数，用于传递给底层函数。

**返回值：**
函数返回一个方差分析对象，可以通过 `summary()` 函数获取分析结果。
**示例：**
下面是使用 `aov()` 函数进行方差分析的示例：

```R
# 创建一个数据框
data <- data.frame(
  group = c("A", "A", "B", "B", "C", "C"),
  value = c(10, 12, 15, 18, 20, 22)
)

# 进行方差分析
result <- aov(value ~ group, data = data)

# 打印分析结果
print(summary(result))
```

在上述示例中，我们创建了一个数据框 `data`，其中包含了一个分组变量 `group` 和一个数值变量 `value`。然后，我们使用 `aov()` 函数进行方差分析，其中因变量是 `value`，自变量是 `group`。最后，我们使用 `summary()` 函数打印出分析结果，包括组间变异、组内变异、均方和 F 统计量等。

你可以根据实际情况调整参数，例如指定额外的自变量、交互项，处理缺失值的方式，或者使用其他统计方法。根据数据的特点和研究问题，适当调整参数可以得到相应的方差分析结果。

## 单因素（子）方差分析（One-way ANOVA）
在R语言中，当需要检验三个或更多均值是否存在显著性差异时，通常采用方差分析（ANOVA）。这里，我将展示如何使用R语言进行一元方差分析（One-way ANOVA）的例子，假设我们有三个独立的样本组。

以下是具体步骤和代码：

1. 准备数据：首先，我们需要创建一个数据框，其中包含我们想要检验的变量。假设我们有三组数据，分别命名为group1、group2 和 group3。

```r
# 定义三个样本组的数据
group1 <- c(6, 8, 4, 5, 3, 7)
group2 <- c(8, 7, 6, 5, 7, 8)
group3 <- c(13, 9, 11, 8, 12, 10)

# 使用data.frame创建数据框，并添加一个组别标识因子
data <- data.frame(
  value = c(group1, group2, group3),
  group = factor(rep(c("Group1", "Group2", "Group3"), each = 6))
)
```

2. 进行方差分析：使用`aov`函数进行方差分析，并用`summary`函数查看结果。

```r
# 进行一元方差分析
result <- aov(value ~ group, data = data)

# 显示方差分析结果
summary(result)
```

3. 如果ANOVA结果显示至少有一组均值与其他组有显著差异，接下来可以进行事后检验（Post-hoc test）来确定哪些组之间存在差异。常见的事后检验包括TukeyHSD、pairwise.t.test等。

```r
# 进行TukeyHSD事后检验
TukeyHSD(result)
```

下面是将这些步骤整合到一起的完整示例：

```r
# 定义样本数据
group1 <- c(6, 8, 4, 5, 3, 7)
group2 <- c(8, 7, 6, 5, 7, 8)
group3 <- c(13, 9, 11, 8, 12, 10)

# 创建数据框
data <- data.frame(
  value = c(group1, group2, group3),
  group = factor(rep(c("Group1", "Group2", "Group3"), each = 6))
)

# 进行方差分析
result <- aov(value ~ group, data = data)

# 查看方差分析结果
summary_result <- summary(result)
print(summary_result)

# 如果ANOVA显示有显著性差异，则进行TukeyHSD事后检验
if(summary_result[[1]]$'Pr(>F)'[1] < 0.05) {
  posthoc_result <- TukeyHSD(result)
  print(posthoc_result)
}
```

运行以上代码后，你会得到每个组之间均值的比较结果以及是否存在显著差异。如果`Pr(>F)`的值低于你选择的显著性水平（例如0.05），那么你可以认为至少有一组均值与其他组不同。事后检验的结果将告诉你具体哪些组之间存在显著性差异。

### 解释
summary(model)显示的内容

![Pasted image 20240109203103](attachments/Pasted%20image%2020240109203103.png)

school：分子  
Residuals：分母  。解释为**余数和残差**？
  
（1）DF：自由度；  
（2）Sum Sq：sum of squares，SS；  
（3）Mean Sq：mean of squuares，MS；  
（4）F value：F值；  
（5）Pr(>F)：P值  
（6）Signif. codes：p值得显著程度，三个星号表示显著水平在0到0.001之间


## 双因素方差分析
在R语言中，双因素方差分析（Two-Way ANOVA）可以用来研究**两个分类自变量（因子）对一个连续因变量**的影响。可以通过`aov()`函数或者`lm()`函数来进行双因素方差分析，并使用`summary()`函数来获取分析结果。以下是一个使用`aov()`函数进行双因素方巀分析的例子：  

（1）两个因素存在**交互作用，相互影响** 

result <- aov(Response ~ Factor1 `*` Factor2, data=data)

（2）两个因素是**相互独立**的

result <- aov(Response ~ Factor1 `+` Factor2, data=data)  


### 红酒配红肉的例子：

看**酒的种类和肉的种类**对评价的影响！

![Pasted image 20240109204554](attachments/Pasted%20image%2020240109204554.png)

？？？有时间精简下！

这一步的目的是将数据框 taste 中的列 "red_meet", "chicken", "fish" 转换为长格式（long format），并创建一个新的列 meet_type 来存储转换后的因子变量。这样做的目的是为了更方便地进行数据分析和可视化。

具体来说，pivot_longer() 函数的作用是将多个列合并成一个列，并将合并后的值存储在新的列中。在这个例子中，函数将列 "red_meet", "chicken", "fish" 合并成一个新的列 meet_type，并将合并后的值存储在新的列 level 中。

接着，mutate() 函数将 meet_type 列转换为因子变量，这样在后续的分析中可以更好地处理该变量。

通过将数据转换为长格式，可以更容易地进行数据分析，例如使用 ggplot2 进行可视化或使用统计模型进行建模。长格式的数据更适合于处理多个因子变量，同时也更符合数据分析和统计建模的要求。


```R
# 游哥程序
taste <- tibble(
  red_meet = c(10,9,10,3,3,2),
  chicken = c(4,4,2,6,5,7),
  fish = c(3,2,4,8,6,7),
  wine =c("red_wine","red_wine","red_wine","white_wine","white_wine","white_wine")
)

taste <- taste %>%
  pivot_longer(c("red_meet","chicken","fish"), names_to = c("meet_type"), values_to = "level") %>% 
  mutate(meet_type = factor(meet_type))

# tw two w...双因素变量
tw_anova <-aov(level ~ wine + meet_type,data = taste)
summary(tw_anova)

# 交互作用 * meet_type 交互项
tw_anova <-aov(level ~ wine * meet_type,data = taste)
summary(tw_anova)

# 交互作用图，没有交叉，交互作用不显著
with(taste, {
interaction.plot(wine,meet_type,level,type="b",
                 col=c('red',"blue"), pch = c(16,18),
                 main = "Interaction between wine and meet_type")
})
```

  
另外，`aov()`函数还可以与`TukeyHSD()`函数一起使用，进行事后多重比较分析：  
  
```R  
# 事后多重比较分析  
TukeyHSD(tw_anova)
```

### 解释

![Pasted image 20240109204832](attachments/Pasted%20image%2020240109204832.png)

wine：属于分子，影响因素1；
meet_type：属于分子，影响因素2；
wine:meet_type：乘积？属于分子，额外的影响因素1\*2

Residuals：分母  。解释为**余数和残差**？
  
（1）DF：自由度；  
（2）Sum Sq：sum of squares，SS；  
（3）Mean Sq：mean of squuares，MS；  
（4）F value：F值；  
（5）Pr(>F)：P值 ，跟F值的结论应该是一致的！一般考虑显著性水平α=5%，P<α代表某个因素对结果具有显著影响？
（6）Signif. codes：p值得显著程度，三个星号表示显著水平在0到0.001之间。

![Pasted image 20240109204857](attachments/Pasted%20image%2020240109204857.png)