`str_split()` 函数属于 `stringr` 包，用于将字符串按照指定的分隔符拆分成子串。以下是关于 `str_split()` 函数的一些基本信息：

### `str_split` 函数概述：

**功能：** 将字符串按照**指定的分隔符**拆分成子串。

**所属包：** `str_split` 函数属于 `stringr` 包，可以通过 `tidyverse` 加载。

**定义：**
```R
str_split(string, pattern, n = Inf, simplify = FALSE)
```

### 参数介绍：

- **`string`：** 要拆分的字符向量、字符串或因子。

- **`pattern`：** 用于指定分隔符的正则表达式。

"[,\\s.]+"表示使用逗号、空格和句号作为分隔符将字符串拆分为多个部分，其中 `[,]` 匹配逗号，`\\s` 匹配空格，`.` 匹配句号，`+` 表示匹配一个或多个

- **`n`：** 一个整数，指定最多拆分出多少个子串。默认为 `Inf`，表示尽可能多地拆分。

- **`simplify`：** 一个逻辑值，指定是否简化结果矩阵。如果为 `TRUE`，则结果为字符矩阵，否则为列表。默认为 `FALSE`。

### 示例：

```R
# 安装并加载tidyverse包
install.packages("tidyverse")
library(tidyverse)

# 使用str_split拆分字符串
text <- "apple,orange,banana"
split_result <- str_split(text, ",")

# 显示拆分结果
print(split_result)
```

### 输出：

在上述示例中，`str_split()` 函数使用逗号 `,` 作为分隔符将字符串 "apple,orange,banana" 拆分成子串。输出结果将是一个列表，每个元素都是一个字符向量：

```
[[1]]
[1] "apple"   "orange"  "banana"
```

这表示字符串被成功拆分成了三个子串。你可以尝试不同的字符串和分隔符来进行测试。