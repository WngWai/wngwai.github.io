在R语言中，`optim()`函数是一个用于**最优化问题**的内置函数，它可以寻找**给定目标函数的最小值或最大值**。

**函数定义**：
```R
optim(par, fn, ..., method = "Nelder-Mead", lower = -Inf, upper = Inf, control = list(), hessian = FALSE)
```

**参数**：
- `par`：一个数值向量，表示目标函数的**参数的初始值**。

- `fn`：一个函数，表示要**最小化或最大化的目标函数**。该函数的第一个参数应是参数向量。**cost函数**，习惯性用一个向量来替代多元

```R
fr <- function(x) {   ## Rosenbrock Banana function
    x1 <- x[1]
    x2 <- x[2]
    100 * (x2 - x1 * x1)^2 + (1 - x1)^2
}
```

- `...`：传递给目标函数`fn`的其他参数。
- `method`：一个字符，表示要使用的**优化算法的名称**。默认为"Nelder-Mead"，表示使用Nelder-Mead算法。
- `lower`：一个数值向量，表示**参数的下界**。默认为**负无穷**。
- `upper`：一个数值向量，表示参**数的上界**。默认为**正无穷**。
- `control`：一个列表，用于指定优化算法的**控制参数**。
- `hessian`：一个逻辑值，表示是否计算**目标函数的海森矩阵**。默认为`FALSE`，即不计算。

输出结果包含以下信息：
- `$par`：找到的**最优参数向量**。
- `$value`：目标函数在**最优参数处的值**。
- `$counts`：优化过程中函数和梯度的**计算次数**。
- `$convergence`：指示算法**是否收敛**的标志。
如果优化算法成功收敛到停止条件，convergence的值为0，表示收敛。
如果优化算法未能收敛到停止条件，convergence的值为1，表示未收敛。
- `$message`：如果有**任何警告或错误**，将包含相关信息。

下面是一个常见用法的示例：
```R
# 定义目标函数
rosenbrock <- function(x) {
  sum(100 * (x[2] - x[1]^2)^2 + (1 - x[1])^2)
}

# 使用optim函数寻找目标函数的最小值
result <- optim(c(0, 0), rosenbrock)

print(result)
```
输出：
```
$par
[1] 1 1

$value
[1] 1.413587e-25

$counts
function gradient 
     103       NA 

$convergence
[1] 0

$message
NULL
```

在上面的示例中，我们首先定义了一个目标函数`rosenbrock`，该函数是一个著名的Rosenbrock函数。然后，我们使用`optim()`函数来寻找目标函数的最小值。我们将初始参数向量设置为`(0, 0)`，并将目标函数设置为`rosenbrock`。最后，将结果存储在`result`变量中。

### par参数
在R中，`optim()`函数的`par`参数可以接受不仅仅是向量形式，还可以是矩阵或列表等其他形式的参数。
1. 向量形式：向量是`optim()`函数中最常见的参数形式。例如，`par = c(0, 0)`表示初始参数为长度为2的向量。
2. 矩阵形式：如果你的优化问题涉及到多个参数向量，你可以使用矩阵形式的`par`参数。每个参数向量将成为矩阵的一列。例如，`par = matrix(c(0, 0, 1, 1), ncol = 2)`表示初始参数为两个2维向量。
3. 列表形式：列表是一种灵活的数据结构，可以包含多个参数向量以及其他相关的信息。你可以将一个列表作为`par`参数传递给`optim()`函数。例如：
```R
params <- list(param1 = c(0, 0), param2 = c(1, 1))
result <- optim(par = params, fn = objective_function, method = "BFGS")
```
在这个例子中，`params`是一个包含两个参数向量的列表。`optim()`函数将通过适当的方法对每个参数向量进行优化。
总而言之，`optim()`函数中的`par`参数可以接受向量、矩阵和列表等不同形式的参数，可以根据你的具体情况选择最合适的形式。记得根据所选形式和优化问题的要求来调整目标函数和其他参数。
### method参数
`optim()`函数中的`method`参数用于指定优化算法的方法。下面是几种常用的方法及其简要介绍和示例：

1. "Nelder-Mead"（默认）：单纯形法（Nelder-Mead algorithm）是一种无导数优化方法，适用于目标函数不可导或不方便求导的情况。示例：
```R
result <- optim(par = c(0, 0), fn = objective_function, method = "Nelder-Mead")
```
2. "BFGS"：拟牛顿法（Broyden-Fletcher-Goldfarb-Shanno algorithm）是一种使用函数值和梯度信息来逼近最优解的优化方法。示例：
```R
result <- optim(par = c(0, 0), fn = objective_function, method = "BFGS")
```
3. "L-BFGS-B"：限制性拟牛顿法（Limited-memory Broyden-Fletcher-Goldfarb-Shanno algorithm with box constraints）是一种拟牛顿法的变种，适用于带有边界约束的问题。示例：
```R
result <- optim(par = c(0, 0), fn = objective_function, method = "L-BFGS-B")
```
4. "CG"：共轭梯度法（Conjugate Gradient algorithm）是一种无约束优化方法，适用于目标函数是二次型的情况。示例：
```R
result <- optim(par = c(0, 0), fn = objective_function, method = "CG")
```
5. "SANN"：模拟退火算法（Simulated Annealing algorithm）是一种随机搜索算法，通过模拟退火过程寻找全局最优解。示例：
```R
result <- optim(par = c(0, 0), fn = objective_function, method = "SANN")
```

这些只是一些常见的优化方法示例，`optim()`函数还支持其他方法，如"CG"（共轭梯度法）、"Nelder-Mead"（单纯形法）、"SANN"（模拟退火算法）等。可以通过查阅R的帮助文档（`?optim`）来获取更多详细信息和示例，了解各个方法的适用范围和使用方式。