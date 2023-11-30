在R语言中，`str_c()`函数是字符串处理包`stringr`中的一个函数，用于**将多个字符串连接成一个字符串**。

**函数定义**：
```R
str_c(..., sep = "", collapse = NULL)
```

**参数**：

- `...`：一个或多个字符向量，包含要连接的字符串。

- `sep`：一个字符串，用于指定连接字符串之间的分隔符。默认为空字符串。

字符串向量之间？

- `collapse`：字符串间连接用到这个指定支付串。一个字符串，用于**指定连接多个字符串后的结果**。如果设置为`NULL`（默认值），则返回一个**字符串向量**。如果提供了一个非空字符串，则返回一个**单个的连接字符串**。

字符串向量内的字符串之间？

下面是一个常见用法的示例：

```R
library(stringr)

# 连接两个字符串
result1 <- str_c("Hello", "World")
print(result1)  # 输出: "HelloWorld"

# 连接多个字符串，并用空格分隔
result2 <- str_c("Hello", "World", sep = " ")
print(result2)  # 输出: "Hello World"
```


```R
# 连接多个字符串，并用逗号分隔，返回单个连接字符串
result3 <- str_c("apple", "banana", "orange", sep = ", ", collapse = NULL)
print(result3)  # 输出: "apple, banana, orange"

# 连接多个字符串，并用逗号分隔，返回一个字符串向量
result4 <- str_c("apple", "banana", "orange", sep = ", ", collapse = ", ")
print(result4)  # 输出: "apple, banana, orange"
```


```R
# 向量的循环传递
str_c("prefix-", c("a", "b", "c"), "-suffix")
#> [1] "prefix-a-suffix" "prefix-b-suffix" "prefix-c-suffix"

# 缺失值的传递性
x <- c("abc", NA)
str_c("|-", x, "-|")
#> [1] "|-abc-|" NA

str_c("|-", str_replace_na(x), "-|")
#> [1] "|-abc-|" "|-NA-|"
```

