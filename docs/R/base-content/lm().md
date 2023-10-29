在R语言中，`lm()`函数是用于拟合线性回归模型的**内置函数**。
**函数定义**：
```R
lm(formula, data, subset, weights, na.action,
   method = "qr", model = TRUE, x = FALSE, y = FALSE, qr = TRUE, singular.ok = TRUE,
   contrasts = NULL, offset, ...)
```
**参数**：
- `formula`：一个公式，指定了回归模型的形式。通常包含自变量和因变量的关系。**y ~ x**
- `data`：一个数据框，包含用于**构建模型的所有变量**。
- `subset`：一个逻辑向量或表达式，用于指定用于拟合模型的子集观测。
- `weights`：一个数值向量，用于为每个观测指定权重。
- `na.action`：一个函数，用于处理缺失值。
- `method`：一个字符，表示用于拟合模型的方法。默认为"qr"，表示使用QR分解方法。
- `model`：一个逻辑值，表示是否返回拟合的模型对象。默认为`TRUE`。
- `x`、`y`、`qr`、`singular.ok`：这些参数在内部使用，通常不需要手动指定。
- `contrasts`：一个列表，用于指定变量的对比方式。
- `offset`：一个数值向量，用于指定线性预测器的偏移量。
- `...`：其他传递给拟合函数的参数。

```R
# 创建示例数据
x <- c(1, 2, 3, 4, 5)
y <- c(2, 4, 6, 8, 10)

# 拟合线性回归模型
model <- lm(y ~ x)

# 打印模型摘要
summary(model)
```

输出：
```r
Call:
lm(formula = y ~ x)

Residuals:
     1      2      3      4      5 
-5e-16  0e+00  0e+00  0e+00  0e+00 

Coefficients:
Estimate Std. Error   t value Pr(>|t|)    
(Intercept)  1.332e-15  1.014e-15  1.314e+00    0.268    
x            2.000e+00  1.157e-16  1.729e+16   <2e-16 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 8.659e-16 on 3 degrees of freedom
Multiple R-squared:      1,	Adjusted R-squared:      1 
F-statistic: 2.988e+32 on 1 and 3 DF,  p-value: < 2.2e-16
```

在上面的示例中，我们首先创建了自变量向量`x`和因变量向量`y`作为示例数据。然后，我们使用`lm()`函数拟合了一个线性回归模型，其中因变量`y`与自变量`x`之间的关系由公式`y ~ x`指定。将拟合的模型存储在`model`变量中。
最后，我们使用`summary()`函数打印了模型的摘要。摘要包含了拟合系数估计、标准误差、t值、p值以及其他统计指标。
通过使用`lm()`函数，您可以根据数据和指定的公式拟合线性回归模型，并对拟合的模型进行统计分析。

### y ~ x
使用lm()函数进行线性回归时，可以使用公式语法指定自变量和因变量y~x。
在公式中，y ~ x表示因变量y与自变量x之间的关系。
当提供data参数时，R会自动在data中**查找与公式中的变量名匹配**的列向量。
`数据集的变量名就需要为x、y`
如果在`data`中找不到与公式中变量名相匹配的列，R会发出**错误提示**。

