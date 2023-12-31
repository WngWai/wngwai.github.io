R中的一个函数，用于统计数据框或数据表中**每个唯一值的出现次数**。它返回一个**新的数据框**，其中包含唯一值及其对应的计数。
```R
count(data, ..., wt = NULL, sort = FALSE)
```
- `data`：要统计计数的数据框或数据表。
- `...`：用于指定要计数的变量，可以是一个或多个变量。
- `wt`：可选的权重向量，用于指定每个观察值的权重。
- `sort`：一个逻辑值，用于**确定是否按计数值对结果进行排序**。默认值为`FALSE`，即不排序。

下面是一个使用`count()`函数的示例：
```R
library(dplyr)

df <- data.frame(category = c("A", "B", "A", "C", "C", "B"))

counts <- count(df, category)

print(counts)
```
输出：
```R
  category n
1        A 2
2        B 2
3        C 2
```

在上述示例中，我们有一个数据框`df`，包含了一个名为"category"的变量。使用`count()`函数，我们统计了"category"变量中每个唯一值的出现次数。
在结果数据框`counts`中，每行表示一个唯一值及其对应的计数。例如，"A"出现了2次，"B"出现了2次，"C"出现了2次。
`count()`函数对于了解数据中不同类别或因子的分布情况非常有用，可以快速计算每个类别的频数。
