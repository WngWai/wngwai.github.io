函数用于**筛选数据框中满足指定条件的行**。它可以根据给定的逻辑条件来选择数据框中的观测值。
```R
filter(data, ...)
```

- **.data**: 数据框或数据表，表示要筛选的数据源。

- **...**: 逻辑条件，用于指定要筛选的行。条件可以是一个或多个，它们将被连接起来形成筛选表达式。
筛选表达式可以使用以下逻辑运算符：
- **\==**: 等于。
- **!=**: 不等于。
- **>**: 大于。
- **\<**: 小于。
- **>=**: 大于等于。
- **\<=**: 小于等于。
- **!**: 非。
- **&**: 逻辑与。
- **|**: 逻辑或。

1. 选择年龄大于30的观测：
```R
filtered_data <- filter(data, age > 30)
```

2. 选择性别为女性且收入大于50000的观测：
```R
filtered_data <- filter(data, gender == "Female" & income > 50000)

filtered_data <- filter(data, gender == "Female", income > 50000)
```

3. 选择城市为"New York"或"Los Angeles"的观测：
```R
filtered_data <- filter(data, city %in% c("New York", "Los Angeles"))
```

4. 选择注册日期在特定时间范围内的观测：
```R
filtered_data <- filter(data, registration_date >= "2022-01-01" & registration_date <= "2022-12-31")
```

通过组合不同的条件，可以灵活地筛选出符合特定要求的数据框中的行。
需要注意的是，`filter()`函数返回一个新的数据框，其中包含满足筛选条件的行。原始数据框不会受到影响，除非将结果分配给一个新的变量或覆盖原始数据框。


### 真的没有python好用
```R
property_names <- property_name$property_region

lj_top30 <- dplyr::filter(lj, property_region %in% property_names)
```

错误示范
```R
lj_top30 <- dplyr::filter(lj, property_region == property_names$property_region)
```
不能用**等于号**，否则只返回固定数值的行数；
不能在filter函数中**加额外df**，指定df$column会显示报错！


https://blog.csdn.net/weixin_39366714/article/details/126578371扩展
filter_all
if
at

