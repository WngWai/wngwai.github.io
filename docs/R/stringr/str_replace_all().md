在 R 语言中，`str_replace_all()` 函数属于 `stringr` 包，用于替换字符串中满足正则表达式模式的所有匹配项。以下是关于 `str_replace_all()` 函数的基本信息：

### `str_replace_all` 函数概述：

**功能：** **替换字符串中满足正则表达式模式的所有匹配项**。

**所属包：** `str_replace_all()` 函数属于 `stringr` 包，可以通过 `tidyverse` 加载。

**定义：**
```R
str_replace_all(string, pattern, replacement)
```

### 参数介绍：

- **`string`：** 要进行替换的字符串。

- **`pattern`：** 一个正则表达式模式，用于匹配要替换的内容。

- **`replacement`：** 替换的内容。

### 示例：

```R
# 安装并加载tidyverse包
install.packages("tidyverse")
library(tidyverse)

# 使用str_replace_all替换字符串中的数字
text <- "abc123def456ghi789"

# 替换所有数字
result <- str_replace_all(text, "\\d", "X")

# 显示结果
print(result)
```

### 输出：

在上述示例中，`str_replace_all()` 函数用于替换字符串 "abc123def456ghi789" 中所有数字。输出结果将是：

```
[1] "abcXXXdefXXXghiXXX"
```

这表示成功替换了字符串中的所有数字为 "X"。与 `str_replace()` 不同，`str_replace_all()` 会替换所有匹配项，而不仅仅是第一个。