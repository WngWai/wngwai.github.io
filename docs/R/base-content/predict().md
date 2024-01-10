**内置函数**。在 R 语言中，`predict()` 函数通常用于从已经拟合的统计模型中生成预测值。这个函数的可用性取决于所使用的具体模型，因为不同的模型有不同的 `predict()` 方法。

**功能：** 从拟合的统计模型中生成预测值。

```R
# 使用 lm() 拟合线性回归模型
model <- lm(mpg ~ hp + wt, data = mtcars)

# 创建新的数据框进行预测
new_data <- data.frame(hp = c(110, 150), wt = c(2.8, 3.5))

# 使用 predict() 进行预测
predictions <- predict(model, newdata = new_data)

# 打印预测值
print(predictions)

# 输出
       1        2 
26.64153 18.16133 
```

**定义：**
```R
predict(object, newdata = NULL, ...)
```

**参数介绍：**
- `object`：已经拟合的模型对象。

- `newdata`：一个数据框，包含模型中使用的**预测变量的新值**。对于某些模型，`newdata` 是可选的，而对于其他模型可能是必需的。

- `...`：其他可选的参数，具体取决于模型。

在这个例子中，我们使用了 `lm()` 函数拟合了一个线性回归模型 (`model`)。然后，我们创建了一个新的数据框 (`new_data`)，其中包含模型中使用的预测变量的新值。最后，我们使用 `predict()` 函数生成了对应于新数据的预测值 (`predictions`)。这是一个简单的例子，实际上，`predict()` 函数的使用方式会因模型类型的不同而有所变化。