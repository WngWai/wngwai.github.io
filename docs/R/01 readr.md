### 读取数据文件
[read_csv()](readr/read_csv().md) 读取csv文件

[read_excel()](readr/read_excel().md) 读取excel文件

---
### 写入数据文件
[write_csv()](readr/write_csv().md)写入csv文件

数据读取和解析：
- `read_csv()`: 读取逗号分隔的CSV文件。
- `read_tsv()`: 读取制表符分隔的文本文件。
- `read_delim()`: 读取指定分隔符的文本文件。
- `read_fwf()`: 读取固定宽度格式的文本文件。
- `read_table()`: 读取空格分隔的文本文件。
- `read_lines()`: 逐行读取文本文件。
- `parse_datetime()`: 解析日期和时间字符串为`POSIXct`对象。

数据写入：
- `write_csv()`: 将数据写入逗号分隔的CSV文件。
- `write_tsv()`: 将数据写入制表符分隔的文本文件。
- `write_delim()`: 将数据写入指定分隔符的文本文件。

数据处理和转换：
- `parse_number()`: 将字符型数据解析为数值型数据。
- `parse_factor()`: 将字符型数据解析为因子型数据。
- `parse_logical()`: 将字符型数据解析为逻辑型数据。
- `parse_date()`: 将字符型数据解析为日期型数据。
- `parse_time()`: 将字符型数据解析为时间型数据。

其他：
- `locale()`: 设置解析数据时的本地化选项。
- `guess_encoding()`: 猜测文件的字符编码。
- `cols()`: 指定要读取的列及其类型。
- `spec()`: 创建或修改数据读取规格。
