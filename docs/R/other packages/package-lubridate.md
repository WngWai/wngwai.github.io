
## lubridate::mdy()

^c21a07

**将日期字符串解析为日期对象**。

**定义：**
```r
lubridate::mdy(date_string)
```

**参数介绍：**
- `date_string`：日期字符串，格式为 "**Month Day, Year**"，例如 "January 1, 2022"。

**举例：**
```r
library(lubridate)

# 使用 mdy() 解析日期字符串
date <- mdy("January 1, 2022")

# 打印结果
print(date)
```

**输出：**
```
[1] "2022-01-01"
```

在这个例子中，`mdy()` 函数用于将日期字符串 "January 1, 2022" 解析为日期对象。结果是一个包含日期信息的对象，可以在 R 中进行日期相关的操作。