`stringr` 包中的函数主要涉及字符串的提取、匹配、替换、拆分等操作。能用于字符串，一般就能用于字符串向量！

letters是R自带的小写26个字母字符串向量，chr[1:26] "a" "b" ... "z"

[scan()](../readr/scan().md)扫描读取

[writeLines()](stringr/writeLines().md)将字符串写入文件

[identical()](stringr/identical().md)两个内容相比较
## 字符串常用内容
**转义**符号：`\`

"\\"" # or '"'

'\\'' # or "'"

### 创建字符串
[str_dup()](stringr/str_dup().md) 复制字符串。

### 属性

[str_length](stringr/str_length.md)计算字符串的**长度**

[str_count()](stringr/str_count().md)根据**正则**，对字符串中出现匹配的内容进行**不重复的计数**

提取

[stringr：：word](stringr：：word().md) 根据**分隔符**，将字符串划分为单词，并可以选择提取的单词位置

[str_extract()](stringr/str_extract().md)根据正则，输出匹配上的第一个内容。可以检测字符串中**是否含有某个元素**

[str_extract_all](stringr/str_extract_all.md输出满足要求的所有内容，**含有多少个元素**

[str_sub()](stringr/str_sub().md) 根据指定**开始和起始位置**，提取字符串字串

[str_subset()](stringr/str_subset().md)根据**正则**，提取匹配上**能够包含**的字串，如ab，匹配abc、abe

### 常规操作
#### 增

[str_c()](stringr/str_c().md)有两个维度的指定，建议详看函数举例，seq：字符串+向量，collapse向量内的字符串元素

[str_flatten()](stringr/str_flatten().md)指定**分隔符**，将**字符串向量**连接成一个**单一的字符串**

[str_flatten_comma()](stringr/str_flatten_comma().md)默认为**逗号**，连接字符串

[str_glue()](stringr/str_glue().md) 将**变量的值**插入到字符串模板中，生成新的字符串

[str_glue_data()](stringr/str_glue_data().md)将**df中的列向量**插入到字符串模板中

[str_pad()](stringr/str_pad().md)用**特定字符**填充字符串的**两侧**。
 
#### 删

[str_trim()](stringr/str_trim().md)**移除**字符串开头和结尾的**空格**

[str_remove()](stringr/str_remove().md)从字符串中**移除匹配的文本**

#### 改
- **排序**

[str_sort()](stringr/str_sort().md)对字符向量进行排序，如按照美式英语，返回排序后的向量

[str_order()](stringr/str_order().md)按**字母**顺序排序，返回排序后的**元素在原始向量中的索引**

- **替换/转换**

[str_replace()](stringr/str_replace().md) 根据正则，替换**第一个匹配项**

[str_replace_all()](stringr/str_replace_all().md)根据正则，替换**所有匹配项**

[str_to_lower()](stringr/str_to_lower().md)将**所有字母小写**

str_to_upper()将**所有字母大写**

[str_to_title()](stringr/str_to_title().md)将**每个单词的首字母大写**，**空格、逗号、句号、-** 隔开的字符都算作单词

[str_conv()](stringr/str_conv().md)将字符串按**指定格式转码**
  
- **字符串拆分：**  

[str_wrap()](stringr/str_wrap().md)**指定的列宽度**内将字符串拆分成**多行**，且每行开头可以添加指定内容

[str_split()](stringr/str_split().md) 根据**正则识别分隔符**，拆分为子字符串

[str_split_fixed()](stringr/str_split_fixed().md)根据**正则识别分隔符**，**拆分到数量为n的子字符串**

[str_trunc()](stringr/str_trunc().md)截断字符串到指定的长度

#### 查

- **匹配检测**

[str_view()](stringr/str_view().md)根据正则，显示**匹配上的字符整串**或**没有匹配上**的字符串

str_view_all()没有这个

[str_match()](stringr/str_match().md) 根据正则，查找字符串，以**矩阵**的形式返回

[str_locate()](stringr/str_locate().md)返回字符串中根据匹配模式匹配到的**子集的起始位置**

[str_locate_all()](stringr/str_locate_all().md)返回字符串中**所有**匹配模式的起始位置。

[str_detect()](stringr/str_detect().md)根据正则匹配，输出**逻辑值**，结合sum、mean函数效果更佳

### 通配符
在正则表达式中，有许多特殊的匹配符号用于指定模式的匹配规则。以下是一些常见的匹配符号及其含义：

- `.`：匹配**任意单个字符**，除了**换行符**。

- `?`：匹配前面的元素**零次或一次**。问好，要么有、要么没有！

- `*`：匹配前面的**元素零次或多次**。乘0为0，零次或多次

- `+`：匹配前面的**元素一次或多次**。加1或多次

- `^`：以某元素开始，**开头匹配**。

- `$`：以某元素结束，**结尾匹配**。`^apple$`指定apple

- `{n}`：匹配前面的元素**恰好 n 次**。

- `{n,}`：匹配前面的元素至少 n 次。

- `{n,m}`：匹配前面的元素至少 n 次，但不超过 m 次。

- `[]`：匹配括号**内的任意一个字符**。例如，`[abc]` 匹配字符 "a"、"b" 或 "c"。

- `[^]`：匹配**不在括号内的任意一个字符**。例如，`[^abc]` 匹配除了字符 "a"、"b" 和 "c" 之外的任意字符。

- `|`：**匹配两个或多个模式之一**。例如，`apple|banana` 匹配 "apple" 或 "banana"。区别[]，**可以比单个字符长**

- `()`：**捕获匹配的子组**。满足就行

- `\`：用于转义**特殊字符**。需要注意的是，正则表达式中的特殊字符在R语言中常常需要进行转义，即使用**双反斜杠（\\）** 进行表示。例如，要匹配一个字面上的**问号字符**，可以使用`\\?`。

	`\d`： 匹配任意一个**数字字符**，相当于`[0-9]`。

	`\D`：匹配任意一个非数字字符，相当于`[^0-9]`。
	
	`\w`：匹配任意一个**字母、数字或下划线字符**，相当于`[a-zA-Z0-9_]`。
	
	`\W`：匹配任意一个**非字母、非数字、非下划线字**符，相当于`[^a-zA-Z0-9_]`。
	
	`\s`：匹配任意一个**空白字符**，包括空格、制表符、换行符等。
	
	`\S`：匹配任意一个非空白字符


`[aeiou]`至少包含一个元音字母的所有单词

`^[^aeiou]+$`仅包含辅音字母（非元音字母）的所有单词


