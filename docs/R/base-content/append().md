`append()`函数，用于**向向量或列表中添加元素**。

以下是`append()`函数的定义：

```R
append(x, values, after = length(x))
```

参数说明：
- `x`：要添加元素的向量或列表。
- `values`：要添加的元素或要添加的值的向量。
- `after`：可选参数，指定在哪个位置之后添加元素。默认为向量或列表的末尾。

下面是使用`append()`函数向向量和列表中添加元素的示例：

```R
# 向向量中添加元素
vec <- c(1, 2, 3)
new_vec <- append(vec, 4)
print(new_vec)

# 向列表中添加元素
my_list <- list("apple", "banana", "orange")
new_list <- append(my_list, "grape")
print(new_list)
```

在上述示例中，我们分别使用`append()`函数向向量`vec`和列表`my_list`中添加元素。

对于向量，我们将元素4添加到向量`vec`中，将结果保存在`new_vec`中，并打印出结果。

对于列表，我们将元素"grape"添加到列表`my_list`中，将结果保存在`new_list`中，并打印出结果。

请注意，`append()`函数将返回一个新的向量或列表，而不会修改原始的向量或列表。