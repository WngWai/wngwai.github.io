在R语言中，`reorder()`函数用于**重新排序一个因子变量（或字符向量）**，以便**根据另一个变量的值进行排序**。它返回一个重新排序后的因子变量。
**函数定义**：
```R
reorder(x, ..., fun = mean)
```
**参数**：
- `x`：一个因子变量（或字符向量），需要重新排序。
- `...`：其他参数，用于指定用于排序的其他变量。
- `fun`：一个函数，用于指定如何计算排序变量的排序值。默认为`mean`，表示使用**平均值**进行排序。

```R
# 创建一个数据框
data <- data.frame(
  category = c("A", "B", "C", "D"),
  value = c(10, 20, 15, 25)
)

# 使用reorder()函数重新排序因子变量
data$category <- reorder(data$category, data$value)

print(data)
```

在上面的示例中，我们创建了一个包含分类变量`category`和数值变量`value`的数据框。
然后，我们使用`reorder()`函数重新排序了`category`因子变量，根据`value`变量的值进行排序。
在这个示例中，`reorder()`函数默认使用`mean`函数计算排序值，即根据每个`category`值对应的`value`的平均值进行排序。
打印输出的结果如下：
```
  category value
1        A    10
2        C    15
3        B    20
4        D    25
```
可以看到，`category`变量被重新排序，按照`value`变量的值从小到大进行排序。
`reorder()`函数对于创建基于其他变量排序的图表非常有用，例如基于某个指标值的堆叠条形图或线图。
您可以根据需要使用其他函数来计算排序值，并修改`...`参数以指定其他用于排序的变量。


也能实现df数据的重复排布
```R
property_name$property_region <- reorder(property_name$property_region , property_name$sum_property )
```