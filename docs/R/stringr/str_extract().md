在R语言中，`str_extract()`函数提取匹配上的第一个内容，匹配到就输出，后面相同的内容不管。

```R
library(stringr)

# 从字符串中提取与指定模式匹配的部分
extract1 <- str_extract("Hello World", pattern = "[aeiou]")
print(extract1) 
输出: "e"

extract1 <- str_extract("Hello World e e e", pattern = "[aeiou]")
print(extract1) 
输出: "e"

extract2 <- str_extract("Hello World", pattern = "\\d+")
print(extract2)  
输出： NA  # 空字符向量（`character(0)`） 

extract3 <- str_extract("Hell3 World45", pattern = "\\d+")
print(extract2)  
输出: [1] "3"
```

**函数定义**：
```R
str_extract(string, pattern)
```

**参数**：

- `string`：字符串集，包含要从中提取部分的字符串。

- `pattern`：查找目标字符串，包含要**匹配的模式**。
