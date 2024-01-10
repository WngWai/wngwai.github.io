`infer` 包是一款现代化的统计推断包，它提供了一套统一的语法来执行**假设检验和置信区间估计**，特别注重**随机模拟和置换测试**。


## infer::prop_test()

^8af298

![500](attachments/Pasted%20image%2020231227154219.png)

### 列表内容
`prop_test()` 函数的输出是一个包含检验结果的列表，通常包括以下组件：
- `statistic`: 检验统计量的值。
- chisq_df：?
- `p_value`: 检验的 p 值。
- `alternative`: 指定的备择假设类型。
- lower_ci：?
- upper_ci：?
- `estimate`: 样本中成功事件的比例估计。
- `null.value`: 在零假设下的比例值。

- `method`: 所使用检验的方法描述。

`prop_test()` 函数主要用来进行**比例的假设检验**，它可以用来检验一个样本比例是否等于某个指定的值（单样本比例检验），或者比较两个独立样本的比例（两个样本比例的检验）。

函数定义通常如下：
```R
prop_test(x, success = NULL, p = NULL, alternative = c("two-sided", "greater", "less"), ...)
```

- `x`: 一个因子、逻辑、整数或数值向量。在两个比例进行比较时，`x` 是一个因子，代表分组变量。

- `response`：如果x是一个数据框，这里需要指定对象。
```R
prop_test(data_q4, response = have_children,success = "Yes") # Yes作为成功事件
```


- `success`: 用来指定哪个水平作为“成功”的事件。在两个比例进行比较时，`success` 是一个字符向量，长度为 1。

- `p`: 零假设下的比例值。在两个比例进行比较时，`p` 不需要指定。

- `alternative`: 一个字符字符串，指定备择假设的类型。可以是 `"two-sided"`、`"greater"` 或 `"less"`。

- `...`: 其他可能的参数，例如数据集（使用 `data` 参数）。

### 举例
假设我们有一组数据，记录了100个人中是否吸烟的情况，其中有70个人吸烟。我们可以使用prop_test()函数来进行比例检验，判断吸烟者在总体中的比例是否显著不同于一个特定的比例。

首先，我们需要将数据转换为二项式数据，即将吸烟者记为1，非吸烟者记为0。然后，我们可以使用prop_test()函数进行比例检验。

```R
library(infer)

# 创建数据
smokers <- rep(1, 70)
nonsmokers <- rep(0, 30)
data <- c(smokers, nonsmokers)

# 进行比例检验
prop_test(data, ~ response == 1, null = 0.5, alternative = "twosided")
```

在上述示例中，response参数指定了二项式数据中表示吸烟者的变量。我们使用formula语法`~ response == 1`来指定**response变量为1表示吸烟者**。

在prop_test()函数中，我们还需要指定null参数来表示我们要检验的比例值，这里我们假设为0.5。alternative参数用于指定检验的方向，这里我们选择"twosided"表示双侧检验。

函数的输出结果将提供比例检验的统计量和p值等信息，用于评估吸烟者在总体中的比例是否显著不同于0.5。

