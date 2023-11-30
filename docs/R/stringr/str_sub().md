在 R 语言中，`str_subset()` 函数属于 `stringr` 包，用于从字符向量中筛选出包含指定模式的元素。以下是关于 `str_subset()` 函数的基本信息：

### `str_subset` 函数概述：

**功能：** 从字符向量中筛选出包含指定模式的元素。

**所属包：** `str_subset()` 函数属于 `stringr` 包，可以通过 `tidyverse` 加载。

**定义：**
```R
str_subset(string, pattern)
```

### 参数介绍：

- **`string`：** 要进行筛选的字符向量。

- **`pattern`：** 一个正则表达式模式，用于匹配要筛选的内容。

### 示例：

```R
# 安装并加载tidyverse包
install.packages("tidyverse")
library(tidyverse)

# 使用str_subset筛选包含数字的元素
text_vector <- c("apple", "123orange", "banana456", "grape")

# 筛选包含数字的元素
result <- str_subset(text_vector, "\\d")

# 显示结果
print(result)
```

### 输出：

在上述示例中，`str_subset()` 函数用于从字符向量中筛选出包含数字的元素。输出结果将是一个新的字符向量，其中包含原始向量中包含数字的元素：

```
[1] "123orange" "banana456"
```

这表示成功筛选出了包含数字的元素。如果需要筛选不包含指定模式的元素，可以使用 `str_subset()` 的反函数 `str_which()`。