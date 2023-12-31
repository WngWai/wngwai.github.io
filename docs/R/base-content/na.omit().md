在R语言中，`na.omit()`函数用于**删除包含缺失值（NA）的观测行**。它返回一个新的数据框或向量，其中不包含任何缺失值。
```R
na.omit(object)
```
其中，`object`是要处理的数据对象，可以是数据框、矩阵或向量。
- 对于数据框和矩阵：
  - `na.omit()`函数将删除包含任何缺失值的观测行，并返回一个新的数据框或矩阵，其中不包含缺失值。
  - 缺失值可以是`NA`或`NaN`。
  - 如果数据框或矩阵中的某一列（变量）包含缺失值，那么该列中对应的观测行将被删除。

    ```R
    # 创建一个包含缺失值的数据框
    df <- data.frame(A = c(1, 2, NA, 4), B = c(NA, 2, 3, 4))
    
    # 删除包含缺失值的观测行
    new_df <- na.omit(df)
    
    # 打印新的数据框
    print(new_df)
    ```

 输出：

 ```r
      A B
    2 2 2
    4 4 4
 ```

- 对于向量：
  - `na.omit()`函数将删除向量中的任何缺失值，并返回一个新的向量，其中不包含缺失值。
  - 缺失值可以是`NA`或`NaN`。

    ```R
    # 创建一个包含缺失值的向量
    vec <- c(1, 2, NA, 4, NaN)
    
    # 删除缺失值
    new_vec <- na.omit(vec)
    
    # 打印新的向量
    print(new_vec)
    ```

    输出：

    ```
    [1] 1 2 4
    ```

总结起来，`na.omit()`函数用于删除包含缺失值的观测行或向量元素，以便进行数据清洗和分析。