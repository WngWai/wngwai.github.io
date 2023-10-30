函数是R语言中的一个内置函数，用于**将对象转换为数值型**（numeric）。下面是关于`as.numeric()`函数的详解和示例：

**函数介绍：**
`as.numeric()`函数用于将对象转换为数值型。如果对象可以转换为数值型，则返回转换后的数值型对象；如果无法转换，则返回`NA`。
该函数常用于将字符型、因子型等非数值型数据转换为数值型。

**函数语法：**
```R
as.numeric(x)
```
参数`x`代表要转换的对象，可以是任何R语言中的数据类型，包括向量、矩阵、数据框等。

**函数示例：**

示例1：将字符型向量转换为数值型

```R
# 创建一个字符型向量
x <- c("1", "2", "3")

# 转换为数值型向量
y <- as.numeric(x)
y
# 输出: 1 2 3

# 检查转换后的对象是否为数值型
is.numeric(y)
# 输出: TRUE
```

示例2：将因子型向量转换为数值型

```R
# 创建一个因子型向量
x <- factor(c("1", "2", "3"))

# 转换为数值型向量
y <- as.numeric(x)
y
# 输出: 1 2 3

# 检查转换后的对象是否为数值型
is.numeric(y)
# 输出: TRUE
```

示例3：将逻辑型向量转换为数值型

```R
# 创建一个逻辑型向量
x <- c(TRUE, FALSE, TRUE)

# 转换为数值型向量
y <- as.numeric(x)
y
# 输出: 1 0 1

# 检查转换后的对象是否为数值型
is.numeric(y)
# 输出: TRUE
```

通过调用`as.numeric()`函数，我们可以将非数值型对象转换为数值型，以便进行数值型数据的分析和计算。注意，在转换时，输入对象的每个元素在转换过程中要能够被解析为数值，否则会被转换为`NA`。