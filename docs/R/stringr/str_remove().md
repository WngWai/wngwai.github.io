在 R 语言的 `stringr` 包中，`str_remove()` 函数用于**从字符串中移除匹配的文本**。

```r
# 使用 str_remove() 函数移除字符串中的匹配文本
result <- str_remove("hello world", "llo")

输出：
[1] "he world"
```

**定义：**
```r
stringr::str_remove(string, pattern)
```

**参数介绍：**
- `string`：要操作的字符串或字符向量。

- `pattern`：一个正则表达式模式，用于匹配要移除的文本。



在这个例子中，`str_remove()` 函数将字符串 "hello world" 中匹配正则表达式模式 "llo" 的文本移除，结果是 "he world"。

请注意，`str_remove()` 只移除第一个匹配项。如果你希望移除所有匹配项，可以使用 `str_remove_all()` 函数。