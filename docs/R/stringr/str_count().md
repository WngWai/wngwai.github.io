在R语言中，`str_count()`函数是字符串处理包`stringr`中的一个函数，用于计算字符串中指定模式的出现次数。
**函数定义**：
```R
str_count(string, pattern)
```
**参数**：
- `string`：一个字符向量，包含要计算的字符串。

- `pattern`：一个字符向量，包含要匹配的模式。

```R
library(stringr)

# 计算字符串中指定模式的出现次数
count1 <- str_count("Hello World", pattern = "o")
print(count1)  # 输出: 2

count2 <- str_count("Hello World", pattern = "z")
print(count2)  # 输出: 0


```

在上面的示例中，我们首先加载了`stringr`包，然后使用`str_count()`函数计算字符串中指定模式的出现次数。

在第一个示例中，我们计算字符串"Hello World"中模式"o"的出现次数。由于字符串中有两个"o"字符，因此结果为2。

在第二个示例中，我们计算字符串"Hello World"中模式"z"的出现次数。由于字符串中没有"z"字符，因此结果为0。

通过使用`str_count()`函数，您可以方便地计算字符串中指定模式的出现次数，从而用于统计和分析字符串数据。

### 匹配不会重叠
2次而非3次

```R
str_count("abababa", "aba")
#> [1] 2
```

### 字符串向量
当处理字符串向量时，`str_count()` 函数可以用于计算每个字符串中指定模式的出现次数。以下是一个示例：

```R
# 安装并加载tidyverse包
install.packages("tidyverse")
library(tidyverse)

# 创建一个字符串向量
text_vector <- c("apple123", "banana456", "orange789", "grape12345")

# 计数每个字符串中数字的出现次数
count_numbers_vector <- str_count(text_vector, "\\d")

# 显示结果
print(count_numbers_vector)
```

输出结果将是：

```
[1] 3 3 3 5
```

这表示在每个字符串中，数字的出现次数分别为 3、3、3、5。在这个例子中，正则表达式 `\\d` 匹配数字，因此 `str_count()` 返回了每个字符串中数字的出现次数。你可以根据需要调整模式以匹配不同的字符或模式。