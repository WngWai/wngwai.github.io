处理df中的每列数据；

在 R 语言中，`sapply()` 函数用于对**向量、列表或数据框**的每个元素应用指定的函数，并返回结果向量、列表或数据框。下面是对 `sapply()` 函数常用参数的详细介绍和举例：
**函数语法：**
```R
sapply(X, FUN, ..., simplify = TRUE, USE.NAMES = TRUE)
```
**参数说明：**
以下是 `sapply()` 函数的一些常用参数，具体说明如下：
- `X`：要应用函数的向量、列表或数据框。
- `FUN`：要应用的函数。
- `...`：其他参数，传递给 `FUN` 函数。
- `simplify`：逻辑值，表示是否尝试简化结果。默认为 `TRUE`，表示尝试将结果简化为向量或矩阵。如果设为 `FALSE`，则结果将始终为列表。
- `USE.NAMES`：逻辑值，表示是否使用 `X` 的名称作为结果的名称。默认为 `TRUE`。

**示例：**
下面是使用 `sapply()` 函数应用函数的示例：

1. 应用内置函数：

```R
# 应用 sum() 函数
x <- c(1, 2, 3)
result <- sapply(x, sum)

result
```

输出：
```
[1] 1 2 3
```

在上述示例中，我们使用 `sapply()` 函数和内置函数 `sum()` 对向量 `x` 的每个元素应用求和操作。结果是一个包含每个元素求和结果的向量。

2. 应用自定义函数：

```R
# 自定义函数
add_one <- function(x) {
  x + 1
}

# 应用自定义函数
x <- c(1, 2, 3)
result <- sapply(x, add_one)

result
```

输出：
```
[1] 2 3 4
```

在上述示例中，我们使用 `sapply()` 函数和自定义的函数 `add_one()` 对向量 `x` 的每个元素应用加一操作。结果是一个包含每个元素加一结果的向量。

3. 应用函数到数据框的每列：

```R
# 创建一个数据框
data <- data.frame(
  x = c(1, 2, 3),
  y = c("a", "b", "c")
)

# 应用函数到数据框的每列
result <- sapply(data, unique)

result
```

输出：
```
$x
[1] 1 2 3

$y
[1] "a" "b" "c"
```

在上述示例中，我们使用 `sapply()` 函数将内置函数 `unique()` 应用于数据框 `data` 的每一列。结果是一个列表，其中包含每列的唯一值。

通过传递适当的参数和函数，你可以使用 `sapply()` 函数在 R 中对向量、列表或数据框的每个元素应用指定的函数，并获得相应的结果。