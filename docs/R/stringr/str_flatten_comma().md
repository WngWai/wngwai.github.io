str_flatten_comma()函数的功能是**将字符串向量（character vector）中的元素使用`逗号`连接起来，并返回一个新的字符串**。

```r
str_flatten_comma(string, last = NULL, na.rm = FALSE)
```
参数介绍：
- x: 需要连接的字符串向量。


```R
x <- c("A", "B", "C", "D")
result <- str_flatten_comma(x)

输出：
"A, B, C, D"
```



、