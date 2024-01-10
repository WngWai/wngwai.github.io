在 R 语言中，`stringr` 包中的 `str_glue()` 函数用于**将变量的值插入到字符串模板中，生成新的字符串**。

```r
library(stringr)

# 使用 str_glue() 函数生成新的字符串
name <- "John"
age <- 30
result <- str_glue("My name is {name} and I am {age} years old.")

# 打印结果
print(result)


输出：
[1] "My name is John and I am 30 years old."

```

**定义：**
```r
stringr::str_glue(..., .sep = "", .envir = parent.frame(), .open = "{", .close = "}")
```

**参数介绍：**
- `...`：字符串模板，其中用花括号 `{}` 括起来的部分表示**要插入的变量**。

```python
# 类似python中的
"插入的内容{}".format(i)
```


- `.sep`：连接多个字符串模板时使用的分隔符，默认为空字符串。

- `.envir`：用于解析变量的环境，默认为父环境。

- `.open`：打开花括号的字符串，默认为 `{`。

- `.close`：关闭花括号的字符串，默认为 `}`。



在这个例子中，`str_glue()` 函数将变量 `name` 和 `age` 的值插入到字符串模板中，生成新的字符串 "My name is John and I am 30 years old."。花括号 `{}` 中的部分会被变量的值替换。