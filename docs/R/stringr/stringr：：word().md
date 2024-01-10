在 R 语言中，`stringr::word()` 函数用于提取文本中的单词。从文本中**提取指定位置的单词**。

```r
library(stringr)

# 使用 word() 函数提取字符串中的单词
result <- word("This is a sentence.", start = 2, end = 4)

# 打印结果
print(result)

输出
[1] "is"  "a"   "sentence."
```

**定义：**
```r
stringr::word(string, start = 1, end = start, sep = "\\s+")
```

**参数介绍：**
- `string`：要操作的字符串或字符向量。

- `start`：要提取的**单词的起始**位置。

- `end`：要提取的单词的**结束**位置。

- `sep`：**分隔符**，分隔单词的正则表达式模式，默认为空格。


在这个例子中，`stringr::word()` 函数被用于从字符串 "This is a sentence." 中提取位置从 2 到 4 的单词。默认情况下，`sep` 参数使用正则表达式模式 "\\s+"，表示使用空格作为单词的分隔符。