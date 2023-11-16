在R语言中，`format()`函数用于**格式化数值或日期时间对象的显示方式**。

**函数定义**：
```R
format(x, ...)
```

**参数**：
- `x`：要格式化的数值、日期时间对象或其他可转换为字符的对象。
- `...`：可选参数，用于指定格式化的选项。

**示例**：
以下是使用`format()`函数格式化数值和日期时间的示例：

```R
# 格式化数值
num <- 12345.6789
formatted_num <- format(num, digits = 2, scientific = FALSE)
print(formatted_num)

# 格式化日期时间
date <- as.Date("2021-09-30")
formatted_date <- format(date, format = "%Y-%m-%d")
print(formatted_date)
```

在上述示例中，我们首先定义了一个数值`num`和一个日期`date`。

然后，我们使用`format()`函数对数值`num`进行格式化，指定了显示2位小数，并关闭科学计数法。格式化后的结果保存在`formatted_num`中，并打印出来。

接着，我们使用`format()`函数对日期`date`进行格式化，指定了日期的格式为年-月-日（%Y-%m-%d）。格式化后的结果保存在`formatted_date`中，并打印出来。

以下是打印出的内容：

```
[1] "12345.68"
[1] "2021-09-30"
```

在上述输出中，我们可以看到数值`num`被格式化为带有两位小数的字符串，而日期`date`被格式化为"年-月-日"的形式。

```R
# 示例因子
factor_vector <- factor(c("A", "B", "A", "C", "B", "C"))

# 获取因子的水平数量
num_levels <- nlevels(factor_vector)

# 打印因子的水平数量
print(num_levels)

### 结果
[1] 3
```