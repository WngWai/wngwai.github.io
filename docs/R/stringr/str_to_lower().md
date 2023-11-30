`str_to_lower()`函数属于`stringr`包，用于将字符串转换为小写形式。以下是关于`str_to_lower()`函数的一些基本信息：

### `str_to_lower`函数概述：

**功能：** **将字符串转换为小写形式**。

**所属包：** `str_to_lower`函数属于`stringr`包，可以通过`tidyverse`加载。

**定义：**
```R
str_to_lower(string)
```

### 参数介绍：

- **`string`：** 要转换为小写的字符向量、字符串或因子。

### 示例：

```R
# 安装并加载tidyverse包
install.packages("tidyverse")
library(tidyverse)

# 使用str_to_lower将字符串转换为小写
str_to_lower("Hello, World!")
```

### 输出：

在上述示例中，`str_to_lower()`函数用于将字符串 "Hello, World!" 转换为小写形式。这个函数没有返回一个新的字符串，而是直接输出转换后的结果。在这个例子中，输出结果将是：

```
[1] "hello, world!"
```

这表示字符串 "Hello, World!" 被成功转换为小写形式。你可以用不同的字符串替换示例中的输入来进行测试。