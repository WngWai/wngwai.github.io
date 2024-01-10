在 R 语言中，`str_to_title()` 是 `stringr` 包中的函数，用于**将字符串的每个单词的首字母大写**。

**定义：**
```r
stringr::str_to_title(string, locale = "en")
```

**参数介绍：**
- `string`：要转换的字符串。 

	**空格、逗号、句号、-** 隔开字符都被当作单词！**下划线**不行！

- `locale`：可选，指定转换的区域设置。默认为 **"en"（英语）**。

**举例：**
```r
library(stringr)
c <- "hello world, I am a string,helo-word. you are_you."
str_to_title(c)
```

**输出：**
```
[1] "Hello World, I Am A String,Helo-Word. You Are_you."
```
