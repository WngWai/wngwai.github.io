在R语言中，`str_subset()`函数是字符串处理包`stringr`中的一个函数，用于**从字符向量中选择匹配指定模式的子集**。

```R
library(stringr)

# 从字符向量中选择匹配指定模式的子集
subset1 <- str_subset(c("apple", "banana", "orange"), pattern = "a")
print(subset1)  

输出: "apple" "banana"

subset2 <- str_subset(c("apple", "banana", "orange"), pattern = "z")
print(subset2)  

输出: character(0)

```

**函数定义**：
```R
str_subset(string, pattern)
```

**参数**：

- `string`：一个字符向量，包含要选择子集的字符串。

- `pattern`：一个字符向量，包含要匹配的模式。


在上面的示例中，我们首先加载了`stringr`包，然后使用`str_subset()`函数从字符向量中选择匹配指定模式的子集。

在第一个示例中，我们选择字符向量中匹配模式"a"的子集。由于在字符向量中有两个元素包含字母"a"（"apple"和"banana"），因此结果为"apple"和"banana"。

在第二个示例中，我们选择字符向量中匹配模式"z"的子集。由于字符向量中没有元素包含字母"z"，因此结果为空向量（`character(0)`）。

通过使用`str_subset()`函数，您可以方便地从字符向量中选择匹配指定模式的子集，从而进行数据筛选和提取等操作。

