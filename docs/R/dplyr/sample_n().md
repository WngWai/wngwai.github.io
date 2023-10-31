用于从数据集中随机抽取观察值。
1. `sample_n()`: 从数据集中随机抽取指定数量的观察值。
语法:
```R
sample_n(data, size, replace = FALSE, weight = NULL)
```
参数说明:
- `data`: 输入的数据集。
- `size`: 需要抽样的观察值数量。
- `replace`: 是否进行有放回抽样，如果为`TRUE`，则允许重复抽取同一个观察值；如果为`FALSE`，则不允许重复抽取同一个观察值，默认为`FALSE`。
- `weight`: 可选参数，用于指定每个观察值的抽样权重，即每个观察值被抽取的概率。

示例用法:
```R
library(dplyr)

# 从mtcars数据集中随机抽取5个观察值
sample_n(mtcars, 5)
```

