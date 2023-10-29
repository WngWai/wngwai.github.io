统计性质
```R
Sepal.Length    Sepal.Width     Petal.Length    Petal.Width   
 Min.   :4.300   Min.   :2.000   Min.   :1.000   Min.   :0.100  
 1st Qu.:5.100   1st Qu.:2.800   1st Qu.:1.600   1st Qu.:0.300  
 Median :5.800   Median :3.000   Median :4.350   Median :1.300  
 Mean   :5.843   Mean   :3.057   Mean   :3.758   Mean   :1.199  
 3rd Qu.:6.400   3rd Qu.:3.300   3rd Qu.:5.100   3rd Qu.:1.800  
 Max.   :7.900   Max.   :4.400   Max.   :6.900   Max.   :2.500  
      Species  
 setosa    :50  
 versicolor:50  
 virginica :50
```

在 R 语言中，`summary()` 函数用于生成对象的摘要统计信息，包括描述性统计、分位数、最小值、最大值以及模型拟合的相关信息（例如线性回归模型的系数、标准误差、t 值和 p 值等）
**函数定义**：
```R
summary(object, ...)
```
**参数**：
- `object`：要生成摘要统计信息的对象，如向量、数据框、线性模型等。
- `...`：其他参数，用于传递给底层的`summary()`方法。
1. 对向量进行摘要统计：

```R
# 创建一个向量
x <- c(1, 2, 3, 4, 5)

# 生成摘要统计信息
summary(x)
```

输出：
```
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
   1.00    2.00    3.00    3.00    4.00    5.00 
```

2. 对数据框进行摘要统计：
```R
# 创建一个数据框
data <- data.frame(
  x = c(1, 2, 3, 4, 5),
  y = c("A", "B", "C", "D", "E"),
  z = c(TRUE, FALSE, TRUE, FALSE, TRUE)
)

# 生成摘要统计信息
summary(data)
```
输出：
```
       x          y     z    
 Min.   :1   A:1   Mode :logical  
 1st Qu.:2   B:1   FALSE:2      
 Median :3   C:1   TRUE :3      
 Mean   :3   D:1                 
 3rd Qu.:4   E:1                 
 Max.   :5                       
```

3. 对线性模型进行摘要统计：
```R
# 创建一个线性模型
model <- lm(mpg ~ cyl + hp, data = mtcars)

# 生成摘要统计信息
summary(model)
```
输出：
```
Call:
lm(formula = mpg ~ cyl + hp, data = mtcars)

Residuals:
   Min     1Q Median     3Q    Max 
-3.450 -1.604 -0.208  1.214  5.228 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)  37.8828     2.0746  18.259  < 2e-16 ***
cyl          -2.8758     0.3224  -8.924 6.11e-10 ***
hp           -0.0318     0.0122  -2.607   0.0147 *  
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

Residual standard error: 2.525 on 29 degrees of freedom
Multiple R-squared:  0.8268,	Adjusted R-squared:  0.8143 
F-statistic: 65.64 on 2 and 29 DF,  p-value: 1.789e-11
```

`summary()`函数根据对象的类型生成相应的摘要统计信息。对于向量，它提供最小值、第一四分位数、中位数、平均值、第三四分位数和最大值。对于数据框，它提供每个变量的最小值、第一四分位数、中位数、平均值、第三四分位数和最大值，以及因子变量的模式（mode）和频数（count）。对于线性模型，它提供回归系数的估计值、标准误差、t值和p值，还提供残差的摘要统计信息和模型的拟合度量。

请注意，`summary()`函数的输出内容和格式会根据对象的类型而有所不同。您可以根据实际情况使用`summary()`函数来获取关于数据的重要统计信息。

### 关于NA值的处理
在R语言中，`summary()`函数用于生成有关数据的摘要统计信息，但它**默认会剔除缺失值（NA）** 并计算非缺失观测的统计量。
如果您希望在计算摘要统计信息时保留NA值，可以使用`na.rm = FALSE`参数来禁用缺失值的剔除。将`na.rm`参数设置为`FALSE`将确保在计算统计量时包括缺失值。
下面是一个示例，展示如何使用`summary()`函数，并设置`na.rm = FALSE`以保留NA值：
```R
# 创建一个包含NA值的向量
x <- c(1, 2, NA, 4, 5)

# 使用summary()函数计算摘要统计信息（剔除NA值）
summary(x)
# 输出：
#    Min. 1st Qu.  Median    Mean 3rd Qu.    Max.
#   1.000   2.000   4.000   3.000   4.000   5.000

# 使用summary()函数计算摘要统计信息（保留NA值）
summary(x, na.rm = FALSE)
# 输出：
#    Min. 1st Qu.  Median    Mean 3rd Qu.    Max.    NA's 
#   1.000   2.000   4.000   3.000   4.000   5.000   1.000
```
在上述示例中，我们创建了一个包含NA值的向量`x`。首先，我们使用`summary(x)`计算摘要统计信息，并默认剔除了NA值。然后，我们使用`summary(x, na.rm = FALSE)`再次计算摘要统计信息，但这次保留了NA值。通过设置`na.rm = FALSE`，我们确保了NA值在计算统计量时被考虑进去，并在输出中显示了NA值的计数（NA's）。

请注意，`na.rm`参数在许多R函数中都可以使用，用于控制对缺失值的处理方式。
