
在`dplyr`包中， 从数据集中随机抽取指定比例的观察值。
```R
sample_frac(data, size, replace = FALSE, weight = NULL)
```
参数说明:
- `data`: 输入的数据集。
- `size`: 需要抽样的观察值比例，取值范围为0到1之间。
- `replace`: 是否进行有放回抽样，如果为`TRUE`，则允许重复抽取同一个观察值；如果为`FALSE`，则不允许重复抽取同一个观察值，默认为`FALSE`。
- `weight`: 可选参数，用于指定每个观察值的抽样权重，即每个观察值被抽取的概率。
示例用法:
```R
library(dplyr)

# 从mtcars数据集中随机抽取30%的观察值
sample_frac(mtcars, 0.3)
```

上述示例展示了如何在`dplyr`包中使用`sample_n()`和`sample_frac()`函数进行抽样操作。根据具体的需求，可以根据数据集的大小和抽样比例来调整抽样函数的参数。