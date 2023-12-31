在R语言中，`sprintf()`函数不是`dplyr`包中的函数，而是R的基础函数之一，用于格式化输出字符串。以下是关于`sprintf()`函数的一些基本信息：

**功能：** 格式化输出字符串。

**所属包：** `sprintf`函数属于R的基础函数，无需额外安装包。

**定义：**
```R
sprintf(fmt, ...)
```

### 参数介绍：

- **`fmt`：** 格式字符串，定义了输出的格式。

- **`...`：** 用于替换格式字符串中占位符的值。

%s 字符串

%.0f 数值，点后面是保留小数位数

### 示例：

```R
# 使用sprintf格式化输出字符串
result <- sprintf("Hello, %s! Today is %s.", "John", Sys.Date())

# 显示结果
print(result)
```

### 输出：

在上述示例中，`sprintf()`函数用于格式化输出字符串，将占位符 `%s` 替换为相应的值。输出结果将是：

```
[1] "Hello, John! Today is 2023-11-17."
```

这样，占位符被替换为实际的值，得到了格式化后的字符串。需要注意的是，`sprintf()`函数在实际应用中经常用于构建复杂的输出格式。

### 百分号怎么加\%
在R中，你可以使用百分号的转义序列来显示百分号。以下是修正后的代码：

```R
# 假设 z_α2 已经定义
z_α2 <- 25/20

# 计算 p
p <- 1 - round(2 * pnorm(z_α2, lower.tail = FALSE), 4)

# 使用转义序列显示百分号
sprintf("The confidence level: %s%%", p)
```

在这个例子中，`%s%%` 是一个转义序列，其中 `%s` 表示字符串的位置，`%%` 表示一个百分号。这样，`sprintf` 函数会将 `p` 的值插入到字符串中，并在百分号之后显示百分号。

### \%\%在字符串中必须这么表达，以及多个输出变量时！
在字符中表示百分号也得这么加，否则报错，如95\%\%
```R
sprintf("The 95%% confidence intervals for the mean age:[%.2f, %.2f]", age_low_limit, age_up_limit)
```