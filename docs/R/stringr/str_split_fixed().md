在 R 语言中，`str_split_fixed()` 函数属于 `stringr` 包，用于将字符串拆分为固定数量的部分。这个函数返回一个矩阵，每一列包含拆分后的字符串的一部分。以下是关于 `str_split_fixed()` 函数的基本信息：

正则表达式表示分隔符，将**字符串拆分为固定数量**的部分。

**定义：**
```R
str_split_fixed(string, pattern, n)
```

### 参数介绍：

- **`string`：** 要进行拆分的字符串。

- **`pattern`：** 用**正则表达式表示分隔符**

- **`n`：** **拆分成的数量**。

### 示例：

```R
# 安装并加载tidyverse包
install.packages("tidyverse")
library(tidyverse)

# 使用str_split_fixed将字符串拆分为固定数量的部分
text <- "apple,orange,banana,grape"

# 将字符串拆分为4个部分
result <- str_split_fixed(text, ",", 4)
result1 <- str_split_fixed(text, ",", 3)
result2 <- str_split_fixed(text, ",", 6)

# 显示结果
print(result)
print(result1)
print(result2)
```

### 输出：

在上述示例中，`str_split_fixed()` 函数用于将字符串 "apple,orange,banana,grape" 按照逗号 `,` 拆分为4个部分。输出结果将是一个矩阵，其中每一列包含拆分后的字符串的一部分：

```R
     [,1]    [,2]      [,3]      [,4]
[1,] "apple" "orange" "banana"  "grape"


     [,1]    [,2]     [,3]          
[1,] "apple" "orange" "banana,grape"

     [,1]    [,2]     [,3]     [,4]    [,5] [,6]
[1,] "apple" "orange" "banana" "grape" ""   ""
```

这表示成功将字符串拆分为4个部分，分别是 "apple"、"orange"、"banana" 和 "grape"。