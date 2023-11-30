在R语言中，`str_extract()`函数是字符串处理包`stringr`中的一个函数，用于从**字符串中提取与指定模式匹配的部分**。

匹配到就输出，后面类似的内容不管。

**函数定义**：
```R
str_extract(string, pattern)
```

**参数**：

- `string`：字符串集，包含要从中提取部分的字符串。

- `pattern`：查找目标字符串，包含要**匹配的模式**。

下面是一个常见用法的示例：
```R
library(stringr)

# 从字符串中提取与指定模式匹配的部分
extract1 <- str_extract("Hello World", pattern = "[aeiou]")
print(extract1)  # 输出: "e"

extract1 <- str_extract("Hello World e e e", pattern = "[aeiou]")
print(extract1)  # 输出: "e"

extract2 <- str_extract("Hello World", pattern = "\\d+")
print(extract2)  # 输出: character(0)

extract3 <- str_extract("Hell3 World45", pattern = "\\d+")
print(extract2)  # 输出: [1] "3"

```

在上面的示例中，我们首先加载了`stringr`包，然后使用`str_extract()`函数从字符串中提取与指定模式匹配的部分。

在第一个示例中，我们提取字符串"Hello World"中与模式"[aeiou]"匹配的部分。该模式表示匹配任何一个元音字母，因此结果为"e"，即字符串中的第一个元音字母。

在第二个示例中，我们提取字符串"Hello World"中与模式"\\d+"匹配的部分。该模式表示匹配一个或多个数字，但是在字符串中没有数字，因此结果为空字符向量（`character(0)`）。

通过使用`str_extract()`函数，您可以方便地从字符串中提取与指定模式匹配的部分，从而进行数据提取和处理等操作。
