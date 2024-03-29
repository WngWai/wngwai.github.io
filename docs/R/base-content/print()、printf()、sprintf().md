在R语言中，print()、printf()和sprintf()是三个不同的函数，用于输出结果或对象的值。

- print()函数用于在控制台上**打印结果或对象的值**。它是R中最常用的输出函数之一，通常可以省略，因为当输入对象时，它会自动打印结果。例如：

```R
x <- 10
print(x)  # 打印 x 的值
```

- printf()函数用于**格式化输出结果**。它可以在控制台上打印格式化的结果。printf()函数类似于C语言中的printf()函数，可以使用格式控制字符串来指定输出格式，如字符串、整数、浮点数等。例如：

```R
x <- 10
printf("The value of x is %d", x)  # 打印格式化的结果
```

- sprintf()函数用于**将格式化的结果保存为一个`字符串`**。它可以将格式化的结果赋值给一个变量，以便进一步**处理**或输出。sprintf()函数类似于C语言中的sprintf()函数。例如：

```R
x <- 10
result <- sprintf("The value of x is %d", x)  # 将格式化的结果保存为一个字符串
print(result)  # 打印结果
```

总结来说，print()函数用于打印结果或对象的值，printf()函数用于格式化输出结果，而sprintf()函数用于将格式化的结果保存为一个字符串。

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