在 R 语言中，`str_sub()` 函数属于 `stringr` 包，用于**提取或替换字符串中的子串**。
```R
library(stringr)
# 构造一个字符串向量
c <- c("hello world", "I am a string", "helo-word", "you are_you")
# 用str_sub()函数截取字符串向量
str_sub(c, 1, 5)

输出：
[1] "hello" "I am " "helo-" "you a"
```
对字符串向量也适用！

**定义：**
```r
stringr::str_sub(string, start = 1, end = -1)
```

**参数介绍：**
- `string`：要操作的字符串。

- `start`：子串的起始位置，可以是正整数或负整数。正整数表示从字符串的起始位置开始，负整数表示从字符串的末尾位置开始。

- `end`：子串的结束位置，可以是正整数或负整数。正整数表示从字符串的起始位置开始，负整数表示从字符串的末尾位置开始。

**功能：**
提取字符串中指定位置范围的子串。

**举例：**
```r
library(stringr)

# 使用 str_sub() 提取字符串的子串
result <- str_sub("hello world", start = 1, end = 5)

# 打印结果
print(result)
```

**输出：**
```
[1] "hello"
```

在这个例子中，`str_sub()` 函数被用于提取字符串 "hello world" 中位置从 1 到 5 的子串，即 "hello"。这个函数的使用方式允许从字符串的起始位置或末尾位置开始提取子串。

