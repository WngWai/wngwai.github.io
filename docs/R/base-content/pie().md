在R语言中，`pie()`函数是用于绘制**饼图**的基本函数之一。它可以根据**指定的数值**生成相应比例的扇形，并可通过参数进行进一步的自定义。
**函数定义**：
```R
pie(x, labels = names(x), clockwise = FALSE, init.angle = if(clockwise) 90 else 0, density = NULL, angle = 45, col = NULL, border = NULL, main = NULL)
```
**参数**：
- `x`：一个数值向量，表示**每个扇形的大小**。
- `labels`：一个字符向量，表示**每个扇形的标签**。默认为`names(x)`，即使用`x`向量的**元素名作为标签**。
- `cex`：调整标签大小。
- `clockwise`：一个逻辑值，控制饼图绘制的方向。默认为`FALSE`，即逆时针方向。
- `init.angle`：一个数值，表示饼图的初始角度。默认为0度（或90度，如果`clockwise`为`TRUE`）。
- `density`：一个数值向量，表示扇形的填充密度。默认为`NULL`，即无填充。
- `angle`：一个数值，表示标签的倾斜角度。默认为45度。
- `col`：一个颜色向量，表示扇形的填充颜色。
- `border`：一个颜色向量，表示扇形的边界颜色。
- `main`：一个字符，表示饼图的标题。

```R
ratio <- c(24.2, 21.9, 7.6, 5.2,4.3,3.2,2.6,2.6,1.8,1.8,24.8)
disease <- c("Heart disease", "Cancer","injuries", "CPD",
             "Stroke",'Type2 diabetes',"AD","Suicide",
             "IP","Chronic liver disease","Other")

pie(ratio, labels=disease,
    radius = 1.0,clockwise=T,
    main = "Male individuals")
```
![Pasted image 20231017144628](attachments/Pasted%20image%2020231017144628.png)


在上面的示例中，我们首先创建了一个包含数值和类别的向量。然后，我们使用`pie()`函数根据这些数值绘制了相应比例的饼图。

在这个示例中，`values`向量表示每个扇形的大小，`categories`向量表示每个扇形的标签。通过设置`labels`参数为`categories`，我们将类别名称作为标签显示在饼图中。`main`参数用于设置饼图的标题。

通过使用适当的参数配置，您可以根据需要自定义饼图的外观、标签、颜色等元素。

需要注意的是，`pie()`函数是基本的饼图绘制函数，它提供了一些简单的自定义选项。如果您需要更高级的自定义和更多选项，可以考虑使用专门的绘图包，如`ggplot2`。


```R
pie(decoration_count$sum_decoration, paste(decoration_count$decoration, label_decoration, "%"), radius = 1.0, clockwise=T, main = "房屋装修情况", cex = 0.8)
```
paste()将装修标签和百分比标签和%号连接在一起
![Pasted image 20231019080018](attachments/Pasted%20image%2020231019080018.png)