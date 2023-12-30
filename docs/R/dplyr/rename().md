在 R 语言中，`rename()` 函数有于修改数据框列名，用新列明替代旧列名

**所属包：** `dplyr`

**定义：**
```r
dplyr::rename(data, new_column_name = old_column_name)
```

**参数介绍：**
- `data`：数据框或数据表。
- `new_column_name`：要重命名的新列名。
- `old_column_name`：要被替换的旧列名。

**功能：**
在数据框或数据表中，将指定的列名从旧列名改为新列名。

**举例：**
```r
library(dplyr)

# 创建一个数据框
df <- data.frame(A = c(1, 2, 3), B = c(4, 5, 6))

# 使用 rename() 重命名列 B 为 NewB
df <- rename(df, NewB = B)

# 打印结果
print(df)
```

**输出：**
```
  A NewB
1 1    4
2 2    5
3 3    6
```

在这个例子中，`rename()` 函数用于将数据框 `df` 中的列 `B` 重命名为 `NewB`。

