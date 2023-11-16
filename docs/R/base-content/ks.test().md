在 R 语言中，`ks.test()` 函数用于执行 Kolmogorov-Smirnov 检验，用于**比较观测数据与理论分布之间的差异**。Kolmogorov-Smirnov 检验常用于检验两个样本是否来自同一连续分布，或者检验观测数据与某个理论分布是否拟合良好。下面是对 `ks.test()` 函数的参数进行详细介绍和举例：

**函数语法：**
```R
ks.test(x, y, alternative = c("two.sided", "less", "greater"), exact = NULL, ...)
```

**参数说明：**
- `x`：一个数据向量或者一个数据矩阵，表示观测数据。
- `y`：可选参数，一个字符字符串或函数，表示理论分布的名称或函数。如果提供了 `y`，则会将观测数据与 `y` 所表示的理论分布进行比较；如果未提供 `y`，则默认比较观测数据与标准均匀分布。
- `alternative`：用于指定**备择假设的类型**。可选值为 `"two.sided"`（双侧检验，默认值）、`"less"`（左侧检验）和 `"greater"`（右侧检验）。
- `exact`：一个逻辑值或者一个正整数，用于指定是否应该进行精确计算。默认情况下，根据样本量的大小选择适当的近似方法进行计算。
- `...`：其他参数，用于传递给 `ks.test()` 函数的选项。

**返回值：**
函数返回一个包含 Kolmogorov-Smirnov 检验结果的对象，其中包括统计量、p 值等。

**示例：**
下面是一个使用 `ks.test()` 函数进行 Kolmogorov-Smirnov 检验的示例：

```R
# 生成一个服从正态分布的观测数据
set.seed(123)
x <- rnorm(100)

# 使用 ks.test() 进行 Kolmogorov-Smirnov 检验
result <- ks.test(x, "pnorm")

# 打印 Kolmogorov-Smirnov 检验结果
print(result)
```

在上述示例中，我们首先使用 `rnorm()` 函数生成一个服从正态分布的观测数据向量 `x`。然后，我们使用 `ks.test()` 函数对观测数据 `x` 进行 Kolmogorov-Smirnov 检验，比较观测数据与标准正态分布进行拟合。最后，我们打印出 Kolmogorov-Smirnov 检验的结果。

请注意，`ks.test()` 函数还可以用于比较观测数据与其他理论分布，例如指数分布、均匀分布等。你可以根据实际需要传递不同的参数来执行相应的 Kolmogorov-Smirnov 检验，并根据检验结果进行数据分析和解释。