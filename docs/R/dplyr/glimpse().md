在R语言中，`glimpse()`函数通常是由tidyverse包中的`dplyr`包提供的，用于查看数据框（data frame）的简要摘要信息。
**函数定义**：
```R
glimpse(x, width = NULL, ...)

```
**参数**：
- `x`：要查看摘要信息的数据框。
- `width`：可选参数，用于指定**输出的宽度**。默认情况下，输出**适应于屏幕**。
- `...`：其他参数，用于传递给底层的`print()`函数。


```R
library(dplyr)

# 准备数据
data <- iris

# 查看数据框摘要信息
glimpse(data)
```
![[Pasted image 20231012195044.png]]


在上面的示例中，我们使用`iris`数据集作为示例数据框。然后，我们使用`glimpse()`函数查看数据框的简要摘要信息。函数会显示数据框的列名、数据类型和前几行的值，以及其他有关数据框结构的相关信息。

在输出结果中，您将看到每列的名称、数据类型和前几行的值。数字表示数值型变量，字符表示字符型变量，而因子表示分类变量。此外，还会显示数据框的行数和列数。

使用`glimpse()`函数可以快速了解数据框的结构和内容，有助于进行数据清洗和分析。请注意，`glimpse()`函数通常与其他`dplyr`包中的函数一起使用，用于数据处理和操作。