在R语言中，`str_view()` 函数属于 `stringr` 包，用于查看字符串中指定模式的第一个匹配项。以下是关于 `str_view()` 函数的基本信息：

![Pasted image 20231123193620](attachments/Pasted%20image%2020231123193620.png)

```R
library(stringr)

string <- "Hello, my name is John. Nice to meet you."
pattern <- "John"

str_view(string, pattern)

# 输出
[1] │ Hello, my name is <John>. Nice to meet you.
```

```R
library(stringr)
v <- c("Hello", "World", "I", "am", "here")
pattern <- "e"
str_view(v, pattern)

# 输出：
[1] │ H<e>llo
[5] │ h<e>r<e>
```
str_view()函数是R语言中stringr包提供的一个函数，用于查看字符串中与正则表达式匹配的部分。

**定义：**
```R
str_view(string, pattern, match = TRUE, html = FALSE,
  use_escapes = FALSE)
```

参数介绍：
- string: 要查看的字符串。

- pattern: 正则表达式模式。

- match: 

`TRUE`, the  **default**, shows only elements that match the pattern.
`NA` shows all elements.
`FALSE` shows only elements that don't match the pattern.

- ...: 其他参数。

html
 
use_escapes



