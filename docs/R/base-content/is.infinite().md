在R语言中，`is.infinite()`函数用于检测一个数值是否为无穷大（infinite）。
**函数定义**：
```R
is.infinite(x)
```
**参数**：
- `x`：要检测是否为无穷大的数值。
**示例**：
以下是一些使用`is.infinite()`函数检测数值是否为无穷大的示例：
```R
# 示例1：检测无穷大
x <- Inf
result <- is.infinite(x)
print(result)
# 输出: TRUE

# 示例2：检测非无穷大
y <- 10
result <- is.infinite(y)
print(result)
# 输出: FALSE

# 示例3：检测向量中的数值是否为无穷大
nums <- c(1, Inf, -Inf, 5)
result <- sapply(nums, is.infinite)
print(result)
# 输出: FALSE  TRUE  TRUE FALSE
```

在上述示例中，我们展示了使用`is.infinite()`函数检测数值是否为无穷大的不同情况。

在示例1中，我们创建了一个无穷大的数值`x`，然后使用`is.infinite()`函数检测它是否为无穷大。函数返回`TRUE`，表示数值为无穷大。

在示例2中，我们创建了一个非无穷大的数值`y`，然后使用`is.infinite()`函数检测它是否为无穷大。函数返回`FALSE`，表示数值不是无穷大。

在示例3中，我们创建了一个数值向量`nums`，其中包含了一些有限数值和无穷大数值。我们使用`sapply()`函数和`is.infinite()`函数来检测向量中的每个数值是否为无穷大。函数返回一个布尔向量，表示每个数值是否为无穷大。在这个例子中，只有第二个和第三个数值为无穷大，所以返回`TRUE`，其他数值不是无穷大，返回`FALSE`。

通过使用`is.infinite()`函数，我们可以方便地检测一个数值是否为无穷大，在数值计算和逻辑判断中进行相应的处理。