在 R 语言中，`as.integer()` 函数是基础的 R 函数，用于将对象转换为整数型。

以下是 `as.integer()` 函数的基本信息：

**所属的包：** 无需导入特定包，是 R 语言的基础函数。

**功能：** 将对象转换为整数型。

**定义：**
```R
as.integer(x)
```

**参数介绍：**
- `x`：要转换为整数型的对象，可以是向量、列表、数据框等。

**返回值：**
返回一个整数型的对象。

**举例：**
```R
# 使用 as.integer() 将数值向量转换为整数型
num_vector <- c(1.5, 2.8, 3.2)
int_vector <- as.integer(num_vector)

# 打印结果
print(int_vector)
```

**输出：**
```
[1] 1 2 3
```

在这个例子中，`as.integer(num_vector)` 将数值向量 `num_vector` 转换为整数型向量 `int_vector`。小数部分被截断，得到整数型的结果。