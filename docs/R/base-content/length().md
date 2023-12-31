在R语言中，`length()`函数用于获取对象的长度，即对象中元素的个数。
```R
length(object)
```
- `object`：要计算长度的对象，可以是向量、列表、矩阵、数据框等。

1. 获取向量的长度：
```R
my_vector <- c(1, 2, 3, 4, 5)
length(my_vector)
```
输出结果为 `5`，表示向量 `my_vector` 中有 5 个元素。

2. 获取列表的长度：
```R
my_list <- list(a = 1, b = 2, c = 3)
length(my_list)
```
输出结果为 `3`，表示列表 `my_list` 中有 3 个元素。

3. 获取矩阵的长度：
```R
my_matrix <- matrix(1:6, nrow = 2)
length(my_matrix)
```
输出结果为 `6`，表示矩阵 `my_matrix` 中有 6 个元素。

4. 获取数据框的长度（行数）：
```R
my_df <- data.frame(a = 1:3, b = c("x", "y", "z"))
length(my_df)
```
输出结果为 `3`，表示数据框 `my_df` 中有 3 行。

`length()`函数对于确定对象的大小和维度非常有用。它适用于各种类型的对象，并且可以帮助您在处理数据时获取有关对象结构的信息。

### NA值（缺失值）影响，sum(is.na())
当使用`length()`函数计算一个向量的长度时，如果向量中包含缺失值（NA），则该缺失值将被计算在内。
下面是一个示例来说明这一点：
```R
# 创建一个包含缺失值的向量
vec <- c(1, 2, NA, 4, NA)

# 计算向量的长度
len <- length(vec)

# 输出结果
print(len)
```
输出结果为：
```
[1] 5
```

在上述示例中，向量`vec`包含了两个缺失值（NA）。然而，使用`length()`函数计算向量的长度时，缺失值会被视为有效值，并被计算在内，因此向量的长度为5。
如果你想忽略缺失值，只计算有效值的数量，可以使用`sum(!is.na(vec))`来计算非缺失值的个数。例如：
```R
# 计算非缺失值的个数
valid_len <- sum(!is.na(vec))

# 输出结果
print(valid_len)
```
输出结果为：
```
[1] 3
```
在上述示例中，使用`sum(!is.na(vec))`计算了向量`vec`中非缺失值的个数，结果为3。这样可以排除缺失值，只计算有效值的数量。