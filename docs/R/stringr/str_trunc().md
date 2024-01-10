在 R 语言的 `stringr` 包中，`str_trunc()` 函数用于**截断字符串到指定的长度**。

```r
# 使用 str_trunc() 函数截断字符串
result <- str_trunc("This is a long sentence.", width = 10)

输出：
[1] "This is..."
```

**定义：**
```r
stringr::str_trunc(string, width, side = c("right", "left", "center"), ellipsis = "...")
```

**参数介绍：**

- `string`：要截断的字符串。

- `width`：要截断的宽度，即最终字符串的字符数。

- `side`：可选，指定截断的位置。可以是 "**right**"（默认，从右边截断），"left"（从左边截断）或 "center"（从中间截断）。

- `ellipsis`：可选，当截断字符串时要添加的省略号，默认为 "..."。

在这个例子中，`str_trunc()` 函数被用于将字符串 "This is a long sentence." 截断到宽度为 10，省略号 "..." 被添加到字符串的末尾。默认情况下，截断是从右边开始的。