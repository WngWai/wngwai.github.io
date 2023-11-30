在R语言中，`str_pad()` 函数属于 `stringr` 包，用于在字符串的左侧或右侧填充特定字符，以达到指定的宽度。以下是关于 `str_pad()` 函数的基本信息：

### `str_pad` 函数概述：

**功能：** 在字符串的左侧或右侧填充特定字符，以达到指定的宽度。

**所属包：** `str_pad()` 函数属于 `stringr` 包，可以通过 `tidyverse` 加载。

**定义：**
```R
str_pad(string, width, side = c("left", "right"), pad = " ")
```

### 参数介绍：

- **`string`：** 要填充的字符串。

- **`width`：** 最终字符串的宽度。

- **`side`：** 指定填充的位置，可以是 `"left"`（左侧填充，默认）或 `"right"`（右侧填充）。

- **`pad`：** 用于填充的字符，默认是空格。

### 示例：

```R
# 安装并加载tidyverse包
install.packages("tidyverse")
library(tidyverse)

# 使用str_pad填充字符串
text <- "123"

# 在左侧填充0，使得宽度达到5
padded_text_left <- str_pad(text, width = 5, side = "left", pad = "0")

# 在右侧填充空格，使得宽度达到7
padded_text_right <- str_pad(text, width = 7, side = "right")

# 显示结果
cat("Left-padded text:", padded_text_left, "\n")
cat("Right-padded text:", padded_text_right, "\n")
```

### 输出：

在上述示例中，`str_pad()` 函数被用于在字符串 "123" 的左侧和右侧进行填充。输出结果将是：

```
Left-padded text: 00123 
Right-padded text: 123    
```

这表示成功在字符串的左侧填充了0，使得宽度达到5，以及在右侧填充了空格，使得宽度达到7。你可以根据需要更改填充的字符和宽度。