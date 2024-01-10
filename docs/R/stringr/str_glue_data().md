 `str_glue_data()`将**数据框中的列值插入到字符串模板中**。
 
```r
# 创建一个数据框
data <- data.frame(
  name = c("John", "Jane", "Bob"),
  age = c(30, 25, 35)
)

# 使用 str_glue_data() 函数将数据框的列值插入到字符串模板中
result <- str_glue_data(data, "My name is {name} and I am {age} years old.")

输出：
[1] "My name is John and I am 30 years old."
[2] "My name is Jane and I am 25 years old."
[3] "My name is Bob and I am 35 years old."

```

**定义：**
```r
stringr::str_glue_data(data, ..., .sep = "")
```

**参数介绍：**
- `data`：数据框。

- `...`：要插入到模板中的变量。

- `.sep`：可选，要在字符串之间插入的分隔符，默认为空字符串。


在这个例子中，`str_glue_data()` 函数被用于将数据框 `data` 中的列值插入到字符串模板中，生成包含不同行信息的多个字符串。此函数是 `stringr` 包中用于字符串插值的功能之一。感谢纠正，希望这能解决你的疑问。