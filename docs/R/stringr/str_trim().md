`str_trim()`函数是`stringr`包中的一个函数，用于移除字符串开头和结尾的空格。以下是关于`str_trim()`函数的一些基本信息：

### `str_trim`函数概述：

**功能：** 移除字符串开头和结尾的空格。

**所属包：** `str_trim`函数属于`stringr`包，可以通过`tidyverse`加载。

**定义：**
```R
str_trim(string, side = c("both", "left", "right"))
```

### 参数介绍：

- **`string`：** 要处理的字符向量、字符串或因子。

- **`side`：** 字符串两侧要移除的空格的位置。可选值有`"both"`（默认，表示两侧都移除）、`"left"`（表示只移除左侧）、`"right"`（表示只移除右侧）。

### 示例：

```R
# 安装并加载tidyverse包
install.packages("tidyverse")
library(tidyverse)

# 使用str_trim移除字符串开头和结尾的空格
text <- "   Hello, World!   "
trimmed_text <- str_trim(text)

# 显示处理后的文本
cat(trimmed_text)
```

### 输出：

在上述示例中，`str_trim()`函数用于移除字符串 "   Hello, World!   " 开头和结尾的空格。输出结果将是：

```
Hello, World!
```

这表示字符串已经被成功处理，开头和结尾的空格已被移除。你可以尝试不同的字符串和参数来进行测试。