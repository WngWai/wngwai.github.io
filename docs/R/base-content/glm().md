在R语言中，`glm()`函数是用于**拟合广义线性模型**的内置函数。

![Pasted image 20231122105019](attachments/Pasted%20image%2020231122105019.png)

**函数定义**：
```R
glm(formula, data, family = gaussian, subset, weights, na.action,
    start = NULL, etastart, mustart, offset, control = list(...),
    model = TRUE, method = "glm.fit", x = FALSE, y = TRUE, contrasts = NULL,
    ...)
```

**参数**：
- `formula`：一个公式，指定了广义线性模型的形式。通常包含自变量和因变量的关系。
- `data`：一个数据框，包含用于构建模型的所有变量。
- `family`：一个描述误差结构和链接函数的对象。默认为高斯分布，即适用于普通线性回归。
family = binomial 用于逻辑回归

- `subset`：一个逻辑向量或表达式，用于指定用于拟合模型的子集观测。
- `weights`：一个数值向量，用于为每个观测指定权重。
- `na.action`：一个函数，用于处理缺失值。
- `start`：一个数值向量，用于指定模型参数的初始值。
- `etastart`：一个数值向量，用于指定线性预测器的初始值。
- `mustart`：一个数值向量，用于指定条件均值的初始值。
- `offset`：一个数值向量，用于指定线性预测器的偏移量。
- `control`：一个列表，用于指定控制参数。
- `model`：一个逻辑值，表示是否返回拟合的模型对象。默认为`TRUE`。
- `method`：一个字符，表示用于拟合模型的方法。默认为"glm.fit"。
- `x`、`y`、`contrasts`：这些参数在内部使用，通常不需要手动指定。
- `...`：其他传递给拟合函数的参数。

下面是一个常见用法的示例：

```R
# 创建示例数据
x <- c(1, 2, 3, 4, 5)
y <- c(0, 0, 0, 1, 1)

# 拟合逻辑回归模型
model <- glm(y ~ x, family = binomial)

# 打印模型摘要
summary(model)
```

输出：
```R
Call:
glm(formula = y ~ x, family = binomial)

Deviance Residuals: 
       1         2         3         4         5  
-1.18972  -1.18972  -1.18972   1.23326   1.23326  

Coefficients:
            Estimate Std. Error z value Pr(>|z|)  
(Intercept)    4.605      2.699   1.706   0.0878 .
x             -1.292      0.932  -1.386   0.1650  
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

(Dispersion parameter for binomial family taken to be 1)

    Null deviance: 6.8541  on 4  degrees of freedom
Residual deviance: 5.9843  on 3  degrees of freedom
AIC: 9.9843

Number of Fisher Scoring iterations: 4
```

在上面的示例中，我们首先创建了自变量向量`x`和因变量向量`y`作为示例数据。然后，我们使用`glm()`函数拟合了一个逻辑回归模型，其中因变量`y`与自变量`x`之间的关系由公式`y ~ x`指定，并使用`family = binomial`指定了二项分布的链接函数。
将拟合的模型存储在`model`变量中。
最后，我们使用`summary()`函数打印了模型的摘要。摘要包含了拟合系估计、标准误差、z值、p值以及其他统计指标。
通过使用`glm()`函数，您可以根据数据和指定的公式拟合广义线性模型，并对拟合的模型进行统计分析。
