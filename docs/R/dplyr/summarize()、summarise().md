 结果只保留**分组列数据**和**汇总统计的数据列**！
 
 是 R 语言中 `dplyr` 包提供的一个函数，用于对数据框（data frame）中的**列进行汇总统计操作**，生成汇总结果。

 `summarize()` 函数会返回一个新的数据框，其中包含汇总统计的结果。汇总结果的**每个统计指标都作为新列存在**，列名由用户指定。原始数据框不会被修改。

```R
summarize(.data, new_column = expression, ...)
```

`.data` 表示要进行操作的数据框；

`new_column` 是要创建的**新列**的名称；

`expression` 是用于计算新列值的**表达式**；
除了基本的统计函数（例如 `mean()`、`max()`、`min()`），在 `summarize()` 函数中还可以使用其他各种函数来进行汇总统计，甚至进行更复杂的操作。用户可以根据需要自定义表达式来生成新的汇总列。
1. `sum()`: 计算数值型变量的总和。
2. `mean()`: 计算数值型变量的平均值。
3. `median()`: 计算数值型变量的中位数。
4. `min()`: 计算数值型变量的最小值。
5. `max()`: 计算数值型变量的最大值。
6. `n()` 或 `n_distinct()`: 计算分组后的观测数量或唯一值的数量。
7. `first()`: 获取分组内的第一个观测值。
8. `last()`: 获取分组内的最后一个观测值。
9. `sd()`: 计算数值型变量的标准差。
10. `var()`: 计算数值型变量的方差。
11. `quantile()`: 计算数值型变量的分位数。
12. `summarise_all()`: 对所有变量应用相同的聚合函数。
13. `summarise_at()`: 对指定的变量应用聚合函数。

`...` 表示其他要进行汇总统计的列。


```R
library(dplyr)

# 准备数据
data <- data.frame(
  group = c("A", "A", "B", "B", "B"),
  value = c(1, 2, 3, 4, 5)
)

# 对数据框进行聚合操作
summary_data <- data %>% 
  group_by(group) %>% 
  summarise(mean_value = mean(value), 
            max_value = max(value))

# 查看聚合结果
print(summary_data)
```

输出：
```R
# A tibble: 2 × 3
  group mean_value max_value
  <chr>      <dbl>     <dbl>
1 A            1.5         2
2 B            4           5
```

在上面的示例中，我们首先创建了一个数据框`data`，其中包含两列：`group`和`value`。然后，我们使用`summarise()`函数对数据框进行聚合操作。通过使用`group_by()`函数指定按照`group`列进行分组，然后使用`summarise()`函数指定需要计算的汇总函数和变量。在示例中，我们计算了`value`列在每个组中的平均值和最大值，并将结果存储在`summary_data`变量中。

在聚合结果中，`group`列表示组的标识，`mean_value`列表示每个组中`value`列的平均值，`max_value`列表示每个组中`value`列的最大值。

通过使用`summarise()`函数，您可以根据需要对数据框进行各种聚合操作，如计算平均值、总和、最大值、最小值等。您可以根据实际情况指定不同的汇总函数和变量来生成所需的摘要统计信息。

### ...具体参数扩展
1. 使用内置函数进行求和：
   ```R
   summarize(total_sales = sum(sales))
   ```
   上述代码将计算数据框中`sales`列的总和，并创建一个名为`total_sales`的新列，其中包含结果。

2. 使用多个汇总函数：
   ```R
   summarize(total_sales = sum(sales), average_price = mean(price), max_quantity = max(quantity))
   ```
   上述代码将同时计算总销售额、平均价格和最大数量，并创建相应的新列。

3. 使用条件函数进行计数：
   ```R
   summarize(high_sales = sum(ifelse(sales > 1000, 1, 0)))
   ```
   上述代码将计算`sales`列中大于1000的销售记录数，并创建一个名为`high_sales`的新列。

4. 使用自定义函数进行计算：
   ```R
   summarize(custom_stat = my_function(column1, column2))
   ```
   上述代码使用自定义函数`my_function()`对`column1`和`column2`进行计算，并将结果存储在名为`custom_stat`的新列中。

5. 通过分组进行汇总：
   ```R
   group_by(category) %>%
   summarize(total_sales = sum(sales))
   ```
   上述代码首先使用`group_by()`函数按`category`列分组数据，然后使用`summarize()`函数计算每个组的总销售额。

这些示例展示了`summarize()`函数中参数的用法。您可以根据需要组合使用内置函数、条件函数、自定义函数和分组来实现不同的汇总操作。

### NA缺失值导致的问题
如果在`summarize()`函数中使用`mean()`函数计算列的平均值时，最终结果显示为NA，可能有以下几种原因：
R语言对缺失值的处理结果仍为缺失值！
1. 缺失值（NA）存在：如果在`flights`数据框中的`dep_delay`列中存在缺失值（NA），那么计算平均值时会忽略这些缺失值，并将结果设为NA。在这种情况下，您可以使用`na.rm = TRUE`参数来忽略缺失值进行计算，例如：`mean(dep_delay, na.rm = TRUE)`。
2. 整列都是缺失值：如果`dep_delay`列中的所有值都是缺失值（NA），那么计算平均值时结果将是NA，因为没有可用的非缺失值进行计算。
3. 数据类型不匹配：`dep_delay`列的数据类型可能不是数值型（numeric），而是字符型（character）或因子型（factor）。在这种情况下，无法计算平均值，并且结果将为NA。您可以使用`as.numeric()`函数将列转换为数值型：`mean(as.numeric(dep_delay))`。