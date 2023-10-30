在R语言中，`rm()`函数是一个内置函数，用于删除对象。
**函数定义**：
```R
rm(list = ls(), envir = as.environment(pos = 1), inherits = FALSE)
```
**参数**：
- `list`：要删除的对象的名称或名称的向量。默认为当前环境中的所有对象，使用`ls()`函数获取对象列表。
- `envir`：要删除对象的环境。默认为当前环境，使用`as.environment(pos = 1)`获取当前环境。
- `inherits`：一个逻辑值，表示是否删除继承自指定对象的对象。默认为`FALSE`，即只删除指定的对象。

1. 删除单个对象：
```R
# 创建一个对象
x <- 10

# 删除对象
rm(x)

# 尝试访问已删除的对象
print(x)
```
输出：
```
Error: object 'x' not found
```
在上面的示例中，我们首先创建了一个名为`x`的对象，并将其赋值为10。然后，我们使用`rm()`函数删除了对象`x`。最后，我们尝试访问已删除的对象`x`，会收到一个错误消息，提示找不到对象。

2. 删除多个对象：
```R
# 创建多个对象
x <- 10
y <- 20
z <- 30

# 删除多个对象
rm(list = c("x", "y"))

# 尝试访问已删除的对象
print(x)
print(y)
print(z)
```
输出：
```
Error: object 'x' not found
Error: object 'y' not found
[1] 30
```
在上面的示例中，我们创建了三个对象`x`、`y`和`z`，并给它们分别赋值。然后，我们使用`rm()`函数删除了对象`x`和`y`。最后，我们尝试访问已删除的对象`x`和`y`，会收到两个错误消息，但仍可以访问未删除的对象`z`。

通过使用`rm()`函数，您可以删除单个或多个对象。可以使用`list`参数指定要删除的对象名称，也可以使用`envir`参数指定要删除对象的环境。默认情况下，只删除指定的对象，不删除继承自指定对象的对象。