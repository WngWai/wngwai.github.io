
## skim()
^4ba0bb
得到三张更详细的统计表：
1，
![Pasted image 20231227125312](attachments/Pasted%20image%2020231227125312.png)

2，
![Pasted image 20231227125256](attachments/Pasted%20image%2020231227125256.png)

3，
![Pasted image 20231227125205](attachments/Pasted%20image%2020231227125205.png)


`skim()` 函数属于 `skimr` 包，用于生成**数据框的摘要统计信息**。以下是关于 `skim()` 函数的基本信息：

### `skim` 函数概述：

**功能：** 生成数据框的摘要统计信息。

**所属包：** `skim()` 函数属于 `skimr` 包。

**定义：**
```R
skim(x, ...)
```

### 参数介绍：

- **`x`：** 要摘要的数据框、数据集或变量。

- **`...`：** 其他参数，用于设置摘要的选项。

### 示例：

```R
# 安装并加载skimr包
install.packages("skimr")
library(skimr)

# 生成数据框
data <- data.frame(
  ID = 1:10,
  Age = c(25, 30, 22, 35, 28, 40, 33, 29, 26, 31),
  Salary = c(50000, 60000, 45000, 70000, 55000, 80000, 65000, 58000, 52000, 61000),
  Gender = c("Male", "Female", "Male", "Male", "Female", "Male", "Female", "Female", "Male", "Female")
)

# 生成数据摘要
summary_result <- skim(data)

# 显示摘要信息
print(summary_result)

```






