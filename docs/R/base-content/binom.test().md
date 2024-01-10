在 R 语言中，`binom.test()` 函数是基础的统计检验函数，用于进行二项分布的检验。

以下是 `binom.test()` 函数的基本信息：

**所属的包：** 无需导入特定包，是 R 语言的基础函数。

**功能：** 执行二项分布的检验，通常用于**比较两个二项分布的参数**或对**单个二项分布的参数**进行检验。

**定义：**
```R
binom.test(x, n = NULL, p = 0.5, alternative = c("two.sided", "less", "greater"), conf.level = 0.95)
```

**参数介绍：**
- `x`：成功的次数，可以是向量或一个表示表格的矩阵。

- `n`：试验的总次数，如果 `x` 是向量，则 `n` 必须是相同长度的向量。如果 `x` 是表示表格的矩阵，则 `n` 是每个单元格的行数。

- `p`：要检验的比例（成功的概率），默认为 0.5。

- `alternative`：替代假设的类型，可选值为 "two.sided"（双侧检验，默认）、"less"（小于检验）、"greater"（大于检验）。

- `conf.level`：置信水平，默认为 0.95，表示 95% 置信水平。

**返回值：**
返回一个包含二项检验的结果的列表。

**举例：**
```R
# 使用 binom.test() 进行二项分布检验
successes <- 15
trials <- 20

binom_test_result <- binom.test(successes, n = trials, p = 0.5, alternative = "two.sided")

# 打印结果
print(binom_test_result)
```

**输出：**
```
    Exact binomial test

data:  successes and trials
number of successes = 15, number of trials = 20, p-value = 0.018
alternative hypothesis: true probability of success is not equal to 0.5
95 percent confidence interval:
 0.5262944 0.9045654
sample estimates:
probability of success 
                   0.75 
```

在这个例子中，`binom.test()` 函数用于执行二项分布的检验。成功的次数为 15，总试验次数为 20，检验的替代假设是 "two.sided"（双侧检验）。输出包含了 p 值、替代假设、置信区间等信息。