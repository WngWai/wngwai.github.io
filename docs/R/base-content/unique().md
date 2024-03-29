在 R 语言中，`unique()` 函数是基础的 R 函数，用于**提取向量或因子中的唯一元素**。它不属于特定的包，而是 R 语言的基本函数，可以在不导入其他包的情况下直接使用。

**功能：** 提取向量或因子中的唯一元素。

```R
# 创建一个向量
vec <- c(1, 2, 3, 1, 2, 4, 5)

# 使用 unique() 提取唯一元素
unique_elements <- unique(vec)

# 打印结果
print(unique_elements)

# 输出：
[1] 1 2 3 4 5
```

**定义：**
```R
unique(x, incomparables = FALSE, fromLast = FALSE)
```

**参数介绍：**
- `x`：要提取唯一元素的向量或因子。
- `incomparables`：一个逻辑值或向量，指定在比较元素时是否应将某些值视为不可比较的。默认为 `FALSE`。
- `fromLast`：一个逻辑值，指示是否从向量的末尾开始查找唯一元素。默认为 `FALSE`。

在这个例子中，`unique(vec)` 提取了向量 `vec` 中的唯一元素，并返回一个只包含这些唯一元素的向量。在结果中，重复的元素被去除，只保留了唯一的元素。