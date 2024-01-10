函数在`dplyr`包中用于**去除数据框或数据组中的重复观测**。它接受以下参数：

**功能：** 用于在数据框中根据指定的列去重，返回唯一的行。

```R
# 使用 dplyr 包
library(dplyr)

# 创建一个示例数据框
data <- data.frame(
  ID = c(1, 2, 3, 1, 2),
  Name = c("Alice", "Bob", "Charlie", "Alice", "Bob"),
  Age = c(25, 30, 22, 25, 30)
)

# 使用 distinct() 去重
result <- distinct(data, ID, .keep_all = TRUE)

# 打印结果
print(result)

# 输出：
  ID   Name Age
1  1  Alice  25
2  2    Bob  30
3  3 Charlie  22

# 使用 distinct() 去重
result <- distinct(data, ID, .keep_all = FALSE)

# 打印结果
print(result)

# 输出：
  ID
1  1
2  2
3  3
```

**定义：**
```R
distinct(.data, ..., .keep_all = FALSE)
```

**参数介绍：**
- `.data`：要处理的数据框。
- `...`：要根据去重的列，可以指定多个列。
- `.keep_all`：一个逻辑值，指示是否保留所有列，默认为 `FALSE`，表示**只保留去重的列**。TRUE，表示还保存其他列

在这个例子中，`distinct(data, ID, .keep_all = TRUE)` 使用 `dplyr` 包的 `distinct()` 函数，根据列 `ID` 进行去重，并保留所有列。结果是一个新的数据框，其中包含唯一的行。



