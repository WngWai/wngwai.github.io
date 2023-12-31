您可以使用多个参数来指定半连接的行为。以下是`semi_join()`函数中常用参数的详细介绍和示例：
```R
semi_join(x, y, by=NULL)
```
- `x`、`y`：要连接的两个数据框（或数据表）。
- `by`：指定用于连接的共享变量的名称，可以是一个字符向量或变量名。如果两个数据框中的变量名称相同，则可以省略此参数，默认NULL。

```R
library(dplyr)

df1 <- data.frame(ID = c(1, 2, 3, 4),
                  value1 = c("A", "B", "C", "D"))

df2 <- data.frame(ID = c(2, 3, 5, 6),
                  value2 = c("X", "Y", "Z", "W"))

semi_joined_df <- semi_join(df1, df2, by = "ID")

print(semi_joined_df)
```

输出：
```
  ID value1
1  2      B
2  3      C
```

在上述示例中，我们有两个数据框：`df1`和`df2`。它们都包含一个名为"ID"的共享变量。使用`semi_join()`函数，我们基于"ID"列对两个数据框进行半连接。
半连接操作会保留左侧数据框（`df1`）中与右侧数据框（`df2`）中匹配行的数据，并且只返回左侧数据框中的所有列。如果某个ID在右侧数据框中不存在，则对应的行将被过滤掉。
在上述示例中，只有ID为2和3的行在两个数据框中都有匹配，因此只有这些行被保留在结果数据框`semi_joined_df`中。

### 半连接和左连接的区别
半连接（semi-join）和左连接（left join）是关系型数据库中的两种连接操作，用于将两个表格按照指定的条件进行关联。它们之间的区别在于返回的结果集的不同。

- 左连接（left join）：左连接返回的结果集包含左侧表格的所有行，并将右侧表格中满足连接条件的匹配行合并到结果中。如果右侧表格中没有与左侧表格匹配的行，相应位置上的值将显示为 NULL 或缺失值。左连接保留了左侧表格的所有行，无论是否存在匹配。

- 半连接（semi-join）：半连接操作返回的结果集只包含左侧表格中满足连接条件的行，并且不会返回右侧表格的任何数据。它只关心左侧表格中的匹配行是否存在于右侧表格中，而不关心右侧表格中的具体值。如果左侧表格中的某个键值在右侧表格中存在至少一次匹配，则该行将包含在结果集中。


### 筛选主键的方式
代码还是有些问题，特别是count()的使用。

```R
- 筛选非主键信息
data %>% 
  group_by(col1, col2) %>% 
  count() %>% 
  filter(n >= 2) %>% 
  semi_join(data, by = 'ID')

-- 筛选主键信息
data %>% 
  group_by(col1, col2) %>% 
  count() %>% 
  filter(n >= 2) %>% 
  anti_join(data, by = 'ID')
```