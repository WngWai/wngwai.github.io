在R语言中，`scan()`函数是用于**从文件或用户输入中读取数据的基本函数之一**。它允许您逐行读取数据，并将其存储在R对象中。

**函数定义**：
```R
scan(file = "", what = double(), nmax = -1, n = -1, sep = "", quiet = FALSE, fill = FALSE, strip.white = FALSE, skip = 0, multi.line = TRUE, comment.char = "", allowEscapes = FALSE, flush = FALSE, encoding = getOption("encoding"), skipNul = FALSE)
```

**参数**：
- `file`：一个包含数据的文件名或URL，如果为空字符串或未指定，则从标准输入读取数据。

- `what`：一个用于指定**读取数据的类型**的R对象。默认为`double()`，即读取数值类型。
what = character()，输出解释为字符型数据，而不是默认的数值型数据

- `nmax`：控制读取的最大元素数量，默认为-1表示读取所有元素。

- `n`：控制读取的行数，默认为-1表示读取所有行。

- `sep`：指定数据的**分隔符**，默认为**空格**字符。

- `quiet`：一个逻辑值，控制是否显示读取进度信息。默认为`FALSE`，即显示进度信息。

- `fill`：一个逻辑值，控制是否填充不完整的行。默认为`FALSE`，即不填充不完整的行。

- `strip.white`：一个逻辑值，控制是否去除元素周围的额外空白字符。默认为`FALSE`，即不去除额外空白字符。

- `skip`：一个整数值，跳过读取的起始行数。默认为0，即不跳过任何行。

- `multi.line`：一个逻辑值，控制是否允许跨行读取数据。默认为`TRUE`，即允许跨行读取数据。

- `comment.char`：一个字符，用于指定注释符号。默认为空字符串，表示没有注释符号。

- `allowEscapes`：一个逻辑值，控制是否允许在字符串中使用转义字符。默认为`FALSE`，即不允许使用转义字符。

- `flush`：一个逻辑值，控制是否刷新输入缓冲区。默认为`FALSE`，即不刷新输入缓冲区。

- `encoding`：一个字符，用于指定文件的编码方式。默认为`getOption("encoding")`，即使用系统默认编码方式。

- `skipNul`：一个逻辑值，控制是否跳过空字符。默认为`FALSE`，即不跳过空字符。

下面是一个示例：

```R
# 从文件中读取数据
data <- scan("data.txt", what = character())

# 从用户输入中读取数据
data <- scan(file = "", what = character())
```

在上面的示例中，我们使用`scan()`函数从文件或用户输入中读取数据。在第一个示例中，我们从名为"data.txt"的文件中读取数据，并将其存储在`data`对象中。在第二个示例中，我们从用户输入中读取数据，并将其存储在`data`对象中。

通过使用适当的参数配置，您可以根据需要灵活地使用`scan()`函数来读取数据。
