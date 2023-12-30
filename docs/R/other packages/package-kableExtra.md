



## kable_styling()

^cf2b37

kable()的结果
![Pasted image 20231227124326](attachments/Pasted%20image%2020231227124326.png)

kable() %>% kable_styling()
![Pasted image 20231227124351](attachments/Pasted%20image%2020231227124351.png)

在 R 语言中，`kable_styling()` 函数通常与 `kable()` 函数一起使用，**用于添加表格的样式**。这个函数属于 `knitr` 包的扩展包 `kableExtra`。

以下是 `kable_styling()` 函数的基本信息：

**所属包：** `kableExtra`

**定义：**
```r
kableExtra::kable_styling(kable_input, ...)
```

**参数介绍：**
- `kable_input`：`kable()` 函数的输出，即希望添加样式的表格。
- `...`：其他设置参数，用于指定表格的样式。

**功能：**
为使用 `kable()` 函数创建的表格添加样式。

**举例：**
```r
library(knitr)
library(kableExtra)

# 创建一个简单的数据框
data <- data.frame(
  Name = c("Alice", "Bob", "Charlie"),
  Age = c(25, 30, 22),
  Score = c(95, 89, 75)
)

# 使用 kable() 函数创建表格
kable_table <- kable(data, format = "html", caption = "Sample Table")

# 使用 kable_styling() 添加样式
styled_table <- kable_styling(kable_table, full_width = FALSE, bootstrap_options = "striped")

# 打印结果
print(styled_table)
```

在这个例子中，首先使用 `kable()` 函数创建一个简单的表格，然后使用 `kable_styling()` 函数添加样式。`full_width = FALSE` 表示表格不占满整个宽度，`bootstrap_options = "striped"` 表示使用 Bootstrap 的条纹样式。输出是一个带有样式的 HTML 表格。