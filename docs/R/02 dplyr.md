## 数据的基础处理
### 筛选行/列
[filter()](dplyr/filter().md) 处理数据框数据（df），筛选满足条件的**行**

[select()](dplyr/select().md) 按照**指定列**，形成新的数据框

[select_if()](dplyr/select_if().md)选择满足**特定条件的列**
### 对行/列数据进行操作
[arrange()](dplyr/arrange().md) 对df中行数据按**指定列中数据进行重新排序**

[order()](base-content/order().md) 返回排序的**索引值**，内置排序函数

[min_rank()](dplyr/min_rank().md) 最小值**排序序号**

[sort()](base-content/sort().md) 对元素进行排序，内置函数


[mutate()](dplyr/mutate().md) **创建或修改**新的列（变量）

[transmute()](dplyr/transmute().md) 只**保留新列**


[lag()](dplyr/lag().md) 和[lead()](dplyr/lead().md)**偏移**函数，后移和前移

[distinct()](dplyr/distinct().md) **去除重复观测值**

## 分组统计
[group_by()](dplyr/group_by().md) 指定列进行**分组**，分组后再summarize会**保留**分组列

[ungroup()](dplyr/ungroup().md) **取消**分组，在使用管道符进行参数传递中使用的是同一个源数据，所以要及时撤销分组操作！

- 聚类
	[summarize()、summarise()](dplyr/summarize()、summarise().md) **统计分析**列数据

	[slice_max()](dplyr/slice_max().md)指定最大值的观测行

	slice_min()


[n()](dplyr/n().md) 计算**行数**

[count()](dplyr/count().md)计算**唯一值**出现**次数**

[n_distinct()](dplyr/n_distinct().md)计算**唯一值数量**，注意唯一值数量指种类，跟上面的唯一值次数指频数不同

## 处理关系数据
[tribble()](dplyr/tribble().md) 创建**小规模的示例数据框**，大规模用df数据框

[inner_join()](dplyr/inner_join().md) 内连接

[left_join()](dplyr/left_join().md)左连接

right_join()右连接

[full_join()](dplyr/full_join().md) 全连接

[semi_join()](dplyr/semi_join().md)半连接，目的筛选**左表数据**。以右表数据作为标准，筛选左表中存在于右表中的数据，并**不会返回右表中任何数据**。右有左也有的数据。

[anti_join()](dplyr/anti_join().md)反连接，目的是筛选左表数据，跟半连接相反，筛选右表没有的数据，返回在第一个数据框中存在而在第二个数据框中不存在的行。右无，左有的数据。

[merge()](base-content/merge().md) 内置函数，不建议用

## 抽样
[slice_sample()](dplyr/slice_sample().md) 从df中进行随机抽样

[sample_n()](dplyr/sample_n().md)从数据集中随机抽取观察值

[sample_frac()](dplyr/sample_frac().md)随机抽取指定比例的观察值
