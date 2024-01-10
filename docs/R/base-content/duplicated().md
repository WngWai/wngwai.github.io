在 R 语言中，`duplicated()` 函数是基础的 R 函数，用于标识向量或数据框中的重复元素。这个函数也不属于特定的包，而是 R 语言的基本函数，可以在不导入其他包的情况下直接使用。

**功能：** **标识向量或数据框中的重复元素**。

```R
# 创建一个向量
vec <- c(1, 2, 3, 1, 2, 4, 5)

# 使用 duplicated() 查找重复元素
duplicated_elements <- duplicated(vec)

# 打印结果
print(duplicated_elements)

# 输出：
[1] FALSE FALSE FALSE  TRUE  TRUE FALSE FALSE
```

**定义：**
```R
duplicated(x, incomparables = FALSE, fromLast = FALSE)
```

**参数介绍：**
- `x`：要检查重复元素的向量或数据框。
- `incomparables`：一个逻辑值或向量，指定在比较元素时是否应将某些值视为不可比较的。默认为 `FALSE`。
- `fromLast`：一个逻辑值，指示是否从向量的末尾开始查找重复元素。默认为 `FALSE`。

**返回值：**
返回一个逻辑向量，长度与输入向量相同，其中 `TRUE` 表示重复元素，`FALSE` 表示非重复元素。

在这个例子中，`duplicated(vec)` 返回一个逻辑向量，其中 `TRUE` 表示输入向量 `vec` 中的重复元素，而 `FALSE` 表示非重复元素。通过查看输出，可以看到在向量中哪些元素是重复的。