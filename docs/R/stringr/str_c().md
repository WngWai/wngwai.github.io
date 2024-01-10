在R语言中，`str_c()`函数是字符串处理包`stringr`中的一个函数，用于**将多个字符串连接起来**。

```R
# 加载 stringr 包
library(stringr)

# 基本字符串连接
str_c("Hello", "World") # 输出 "HelloWorld"
str_c("Hello", "World"，sep = "") # 输出 "HelloWorld"

# 使用分隔符连接字符串
str_c("Hello", "World", sep = " ") # 输出 "Hello World"



# 连接多个字符串
vector <- c("apple", "banana", "cherry")
str_c(vector, sep = "-") # 输出 [1] "apple"  "banana" "cherry"

# 连接多个字符串
vector <- c("apple", "banana", "cherry")
str_c("前面", vector, "后面", sep = "-") # [1] "前面-apple-后面"  "前面-banana-后面" "前面-cherry-后面"



# 将字符串向量连接成单个字符串
vector <- c("apple", "banana", "cherry")
str_c(vector, collapse = ", ") # 输出 "apple, banana, cherry"



# 结合使用 sep 和 collapse
days <- c("Monday", "Tuesday", "Wednesday")
str_c(days, sep = " & ", collapse = " | ") # 输出 "Monday | Tuesday | Wednesday"

# 结合使用 sep 和 collapse
days <- c("Monday", "Tuesday", "Wednesday")
str_c("前面", days, "后面", sep = " & ", collapse = " | ")
# [1] "前面 & Monday & 后面 | 前面 & Tuesday & 后面 | 前面 & Wednesday & 后面"



# 连接数字和字符串（数字会自动转换成字符串）
str_c("The answer is ", 42) # 输出 "The answer is 42"
```


**函数定义**：
```R
str_c(..., sep = "", collapse = NULL)
```

**参数**：

- `...`：一个或多个字符串向量。你可以传递任意数量的字符串向量给 `str_c()`，它们将会按顺序被连接。

- `sep`：分隔符，用于**分隔要连接的字符串**。默认为空字符串 `""`，表示没有分隔符。

字符串元素+连接的对象

- `collapse`：如果不是 `NULL`，则会将结果向量**折叠成一个单一的字符串**，使用 `collapse` 参数指定的值作为分隔符。

将字符串向量中的元素合并为一个字符串


