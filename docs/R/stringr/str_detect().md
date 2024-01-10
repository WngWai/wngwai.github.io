在R语言中，`str_detect()`函数是字符串处理包`stringr`中的一个函数，用于**检测字符串中是否存在指定的模式**。

```R
library(stringr)

# 检测字符串中是否存在指定模式
result1 <- str_detect("Hello World", pattern = "o")
print(result1)  # 输出: TRUE

result2 <- str_detect("Hello World", pattern = "z")
print(result2)  # 输出: FALSE


# 字符串向量
x <- c("apple", "banana", "pear")
str_detect(x, "e")
#> [1] TRUE FALSE TRUE


# 找出至少包含一个元音字母的所有单词，然后取反
no_vowels_1 <- !str_detect(words, "[aeiou]")
# 找出仅包含辅音字母（非元音字母）的所有单词
no_vowels_2 <- str_detect(words, "^[^aeiou]+$")
identical(no_vowels_1, no_vowels_2)
#> [1] TRUE
```

**函数定义**：
```R
str_detect(string, pattern)
```
**参数**：
- `string`：一个字符向量，包含要检测的字符串。

- `pattern`：一个字符向量，包含要匹配的模式。



在上面的示例中，我们首先加载了`stringr`包，然后使用`str_detect()`函数检测字符串中是否存在指定的模式。

在第一个示例中，我们检测字符串"Hello World"中是否存在模式"o"。由于字符串中有两个"o"字符，因此结果为`TRUE`。

在第二个示例中，我们检测字符串"Hello World"中是否存在模式"z"。由于字符串中没有"z"字符，因此结果为`FALSE`。

通过使用`str_detect()`函数，您可以方便地检测字符串中是否存在指定的模式，从而进行模式匹配和条件判断等操作。

### str_detect()的妙用
其中words是字符串向量。只要涉及到布尔值的筛选都能用到！
```R
words[str_detect(words, "x$")]
#> [1] "box" "sex" "six" "tax"
str_subset(words, "x$")
#> [1] "box" "sex" "six" "tax"

df %>%
  filter(str_detect(words, "x$"))

```