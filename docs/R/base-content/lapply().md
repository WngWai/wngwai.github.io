`lapply()` 是R语言中的一个函数，用于**对列表（list）的每个元素应用指定的函数**。这个函数返回一个列表，其中包含应用了指定函数的每个元素的结果。

语法如下：

```R
lapply(X, FUN, ...)
```

- `X`：要应用函数的列表（或其他可迭代对象）。
- `FUN`：要应用于每个列表元素的函数。
- `...`：用于传递给函数 `FUN` 的其他参数。

下面是一个简单的例子，演示了 `lapply()` 的基本用法：

```R
# 创建一个列表
my_list <- list(a = 1:5, b = 6:10, c = 11:15)

# 定义一个函数，计算每个向量的平均值
calculate_mean <- function(x) {
  return(mean(x))
}

# 使用lapply应用函数
result <- lapply(my_list, calculate_mean)

# 结果是一个列表，包含每个向量的平均值
print(result)
```

在这个例子中，`lapply()` 将 `calculate_mean` 函数应用于 `my_list` 中的每个向量，返回一个包含每个向量平均值的列表。

`lapply()` 通常用于对列表的每个元素执行相同的操作，而不需要修改原始列表的结构。如果需要更灵活的操作，并且可能修改列表结构，则可能需要使用 `sapply()` 或 `mapply()` 这样的函数。