`across()` 函数属于 `dplyr` 包中的一部分，用于在 `dplyr` 中进行列操作。该函数通常与 `mutate()` 或 `summarize()` 等函数一起使用，以同时应用相同的变换或统计函数于多个列。以下是关于 `across()` 函数的基本信息：

可以根据**指定的列**，对多个列进行操作，例如转换、筛选、重命名等。

### `across` 函数概述：

**功能：** 在多个列上应用相同的变换或统计函数。

**所属包：** `across()` 函数属于 `dplyr` 包。

**定义：**
```R
across(.cols, .fns = NULL, .names = NULL, .names_sep = "_", .cols_select = NULL, .vars = NULL, .fn = NULL, .options = NULL)
```

### 参数介绍：

- **`.cols`：** 指定要**应用变换或函数的列**。可以使用 `select()` 中的语法或 `tidyselect` 中的选择器。

- **`.fns`：** 一个**函数列表**，包含要应用的变换或统计函数。

- **`.names`：** **生成新列名称的规则**。可以使用 `{}` 中的 `.fn` 来指定生成名称的方式。默认为`NULL`，表示使用默认命名规则。

- **`.names_sep`：** 用于连接列名前缀和后缀的分隔符。

- **`.cols_select`：** 选择列的选项，可以使用 `all_of()`、`starts_with()` 等。

- **`.vars`：** 要匹配的列，可以使用 `vars()`。

- **`.fn`：** 一个函数，用于在选择的列上应用变换。

- **`.options`：** 一个包含选项的列表，用于控制变换行为。


1，生成新的列表
```R
# 安装并加载dplyr包
install.packages("dplyr")
library(dplyr)

# 创建一个数据框
data <- data.frame(
  A = c(1, 2, 3),
  B = c(4, 5, 6),
  C = c(7, 8, 9)
)

# 使用across在多列上应用变换
result <- data %>%
  mutate(across(c(A, B), ~ . * 2, .names = "new_{.col}"))

# 显示结果
print(result)
```

### 输出：

在上述示例中，`across()` 函数用于在列 A 和 B 上应用变换，将每个元素乘以2，并生成新的列。输出结果将是：

```
  A B C new_A new_B 
1 1 4 7     2     8 
2 2 5 8     4    10
3 3 6 9     6    12
```

这表示成功在列 A 和 B 上应用了变换，并生成了新的列。

2，替换旧列表
```R
library(dplyr)

# 创建一个示例数据框
df <- data.frame(A = c(1, 2, 3),
                 B = c(4, 5, 6))

# 使用across()函数将A列的值加1，并替换原始列
df <- df %>% 
  mutate(across(A, ~ . + 1))

# 打印结果
print(df)
```

输出：
```
  A B
1 2 4
2 3 5
3 4 6
```


### 同时修改列属性
同时修改为因子类型
```R
library(dplyr)

df_ym <- df_ym %>%
  mutate(across(c(Gender, Broadband.Access., Have.Children.), as.factor))

```


