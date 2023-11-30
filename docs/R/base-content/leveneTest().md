---
tags: []
---
### `leveneTest`函数概述：

**功能：** `leveneTest()`函数用于执行Levene's test（列文检验），用于检验**多个组的方差是否相等**。这个检验通常用于方差分析（ANOVA）等统计方法，因为这些方法在假设组内方差相等的情况下更为有效。

**所属包：** `leveneTest`函数属于`car`包（Companion to Applied Regression）。

**定义：**
```R
leveneTest(y, group, center = "median")
```

### 参数介绍：

- **`y`：** 数值型向量，包含观测值。

- **`group`：** 分组变量，用于指定观测值所属的组别。

- **`center`：** 中心化选项，用于指定如何中心化数据。默认为"median"，可选的还有"mean"。

### 示例：

```R
# 安装并加载car包
install.packages("car")
library(car)

# 创建两个组的数据（示例数据）
group1 <- c(23, 25, 28, 30, 32)
group2 <- c(18, 20, 24, 28, 30)

# 执行Levene's test
result <- leveneTest(c(group1, group2), group = rep(c("Group1", "Group2"), each = 5), center = "median")

# 显示结果
print(result)
```

### 输出：

示例中的输出结果将包含Levene's test的统计量（W）、自由度（DF1，DF2）和p值（Pr(>W)）。具体输出信息将类似于：

```
Levene's Test for Homogeneity of Variance (center = median)
      Df F value Pr(>F)
group  1  0.0667 0.7996
      8
```

这个输出提供了Levene's test的统计量（F value）、自由度（DF1，DF2）以及p值（Pr(>F)）。在这个示例中，你可以查看p值来判断是否拒绝了组内方差相等的假设。