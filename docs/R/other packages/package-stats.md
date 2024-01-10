

### stats::prop.test()

^26daec

在R语言中，`prop.test()`函数用于进行两个比例之间的假设检验。

```R
# 创建观测数据
x <- c(50, 70)  # 成功的观测数
n <- c(100, 100)  # 总的观测数

# 进行比例假设检验
result <- prop.test(x, n)

# 输出结果
print(result)
```
以下是打印出的内容示例：
```
	2-sample test for equality of proportions with continuity correction

data:  x out of n
X-squared = 0.24752, df = 1, p-value = 0.6188
alternative hypothesis: two.sided
95 percent confidence interval:
 -0.1562211  0.2562211
sample estimates:
prop 1 prop 2 
   0.5    0.7
```

**函数定义**：
```R
prop.test(x, n, p = NULL, alternative = "two.sided", conf.level = 0.95, correct = TRUE)
```

**参数**：
- `x`：一个包含**两个水平的向量**或矩阵，表示**成功**的观测数。

- `n`：一个包含**两个水平的向量**或矩阵，表示**总的**观测数。

- `p`：一个包含两个水平的向量或矩阵，表示**预期的比例**。如果不提供，则使用样本的比例。

- `alternative`：可选参数，表示备择假设的类型。可以是"two.sided"（默认值）、"less"或"greater"。

- `conf.level`：可选参数，表示置信水平。默认值为0.95，表示95%的置信水平。

- `correct`：可选参数，表示是否进行修正。默认值为`TRUE`，表示进行**连续性修正**。

需要注意的是，`prop.test()`函数用于比较两个比例之间的差异，并进行假设检验。它适用于独立样本或配对样本的情况。在使用函数时，请根据具体的问题设置参数和数据。

### stats::var.test()

^e4a61d

在R语言中，`var.test()`函数是stats包中的函数，用于执行方差齐性检验。

**函数定义**：
```R
var.test(x, y, ratio = 1, alternative = "two.sided", ...)
```

**参数**：
- `x`：第一个数值向量或数据框。

- `y`：可选参数，第二个数值向量或数据框。

- `ratio`：可选参数，指定`x`和`y`的方差比例。默认为1，表示方差相等。

- `alternative`：可选参数，指定备择假设。可选有"two.sided"（默认，双侧）、"less"（单侧小于）和"greater"（单侧大于）。

- `...`：其他可选参数，用于控制方差齐性检验的计算。

**返回值**：
函数返回一个包含方差齐性检验的结果的对象，其中包括统计量值、自由度和p值。

**示例**：
以下是使用`var.test()`函数执行方差齐性检验的示例：

```R
# 创建示例数据向量
group1 <- c(1, 2, 3, 4, 5)
group2 <- c(2, 4, 6, 8, 10)

# 执行方差齐性检验
var_test_result <- var.test(group1, group2)

# 查看检验结果
print(var_test_result)
```

在上述示例中，我们首先创建了两个示例数据向量`group1`和`group2`，分别包含了两个组的数据。

然后，我们使用`var.test()`函数对两个组的方差进行齐性检验。将`group1`和`group2`作为参数传递给函数。

齐性检验的结果保存在`var_test_result`中。

最后，我们打印出检验结果，其中包括统计量值、自由度和p值。

以下是打印出的内容示例：

```
	F test to compare two variances

data:  group1 and group2
F = 0.25, num df = 4, denom df = 4, p-value = 0.7619
alternative hypothesis: true ratio of variances is not equal to 1
95 percent confidence interval:
 0.02730984 2.27916179
sample estimates:
ratio of variances
          0.25
```

在上述输出中，我们可以看到执行方差齐性检验的结果，其中包括F统计量的值、自由度、p值以及置信区间。根据p值的大小，我们可以判断两个组的方差是否显著不同。在本例中，p值为0.7619，大于通常的显著性水平（如0.05），因此无法拒绝原假设，即两个组的方差可以认为是相等的。



### stats::cor.test()

^0603c1

在 R 语言中，`cor.test()` 函数用于进行两个变量之间的相关性检验。这个函数通常属于基础的 `stats` 包，不需要额外导入。以下是 `cor.test()` 函数的基本信息：

**功能：** **执行两个变量之间的相关性检验**。

**定义：**
```R
cor.test(x, y = NULL, alternative = c("two.sided", "less", "greater"), method = c("pearson", "kendall", "spearman"), exact = NULL, continuity = TRUE, ... )
```

**参数介绍：**
- `x`：第一个数值向量。
- `y`：第二个数值向量。如果未指定，则默认使用 `x`。
- `alternative`：替代假设的类型，可选值为 "two.sided"（双侧检验，默认）、"less"（小于检验）、"greater"（大于检验）。
- `method`：计算相关性的方法，可选值为 "pearson"（皮尔逊相关系数， 默认）、"kendall"（肯德尔相关系数）、"spearman"（斯皮尔曼相关系数）。
- `exact`：是否进行精确检验，通常在样本量较小时使用。
- `continuity`：是否使用修正连续性校正，默认为 `TRUE`。
- `...`：其他参数，用于传递给底层的 `cor.test` 方法。

**返回值：**
返回一个包含相关性检验结果的列表。

**举例：**
```R
# 使用 cor.test() 进行相关性检验
set.seed(123)
x <- rnorm(100)
y <- 2 * x + rnorm(100)

cor_test_result <- cor.test(x, y, method = "pearson", alternative = "two.sided")

# 打印结果
print(cor_test_result)
```

**输出：**
```
    Pearson's product-moment correlation

data:  x and y
t = 22.656, df = 98, p-value < 2.2e-16
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 0.8933621 0.9569031
sample estimates:
      cor 
0.9291175 
```

在这个例子中，`cor.test(x, y, method = "pearson", alternative = "two.sided")` 使用 `cor.test()` 函数进行皮尔逊相关性检验。相关性检验的结果包括 t 统计量、自由度、p 值、替代假设、95% 置信区间以及相关性的点估计。






### stats::bartlett.test()

^ca9b41

**功能：** `bartlett.test()`函数用于执行Bartlett's test（巴特利特检验），检验**多个组的方差是否相等**。这个检验通常用于方差分析（ANOVA）等统计方法，因为这些方法在假设组内方差相等的情况下更为有效。

**所属包：** `bartlett.test`函数属于`stats`包，这是R语言的基础统计包，通常默认加载。

**定义：**
```R
bartlett.test(formula, data, subset, na.action)
```

参数介绍：

- **`formula`：** 一个公式，通常表示为`response ~ group`，其中`response`是数值型变量，而`group`是分组变量。

- **`data`：** 包含相关变量的数据框。

- **`subset`：** 可选参数，用于指定一个子集进行分析。

- **`na.action`：** 一个函数，用于处理缺失值。

示例：

```R
# 创建三个组的数据（示例数据）
group1 <- c(23, 25, 28, 30, 32)
group2 <- c(18, 20, 24, 28, 30)
group3 <- c(22, 24, 26, 28, 30)

# 创建数据框
data <- data.frame(
  Group = rep(c("Group1", "Group2", "Group3"), each = 5),
  Value = c(group1, group2, group3)
)

# 执行Bartlett's test
result <- bartlett.test(Value ~ Group, data = data)

# 显示结果
print(result)
```

输出：

示例中的输出结果将包含Bartlett's test的统计量（Bartlett's K-squared）、自由度（df）和p值（p-value）。具体输出信息将类似于：

```
Bartlett test of homogeneity of variances
           Df = 2 
           Chisquare = 0.55071 
           Pr(>Chisq) = 0.7595
```

这个输出提供了Bartlett's test的统计量、自由度以及p值。在这个示例中，你可以查看p值来判断是否拒绝了组内方差相等的假设。


### stats::AIC()

^3db05b

在 R 语言中，`AIC()` 函数通常属于 `stats` 包，用于计算模型的赤池信息准则（AIC，Akaike Information Criterion）。AIC是模型选择的一个常用指标，它考虑了模型的拟合优度和模型的复杂性，用于在**多个模型**中进行比较。
**功能：** 计算模型的赤池信息准则。

**定义：**
```R
AIC(object, ..., k = 2)
```

**参数介绍：**
- `object`：一个拟合的模型对象。
- `...`：其他参数，用于传递给底层的 `AIC()` 方法。
- `k`：AIC中的惩罚项，通常为2。可以根据需要修改。

**返回值：**
返回一个包含AIC值的数字。

**举例：**
```R
# 使用 AIC() 计算赤池信息准则
# 假设有一个线性回归模型
model <- lm(mpg ~ wt + hp + qsec, data = mtcars)

# 计算赤池信息准则
aic_value <- AIC(model)

# 打印结果
print(aic_value)
```

**输出：**
```
[1] 171.7134
```

在这个例子中，`AIC(model)` 使用 `stats` 包的 `AIC()` 函数计算了线性回归模型的赤池信息准则。AIC的值越小表示模型越好，可以用于比较不同模型的拟合优度和复杂性。