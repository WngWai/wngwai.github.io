不含列表列的数据框显示
![Pasted image 20231012195027](attachments/Pasted%20image%2020231012195027.png)

含列表列的数据框显示：

glimpse()
![Pasted image 20240107124937](attachments/Pasted%20image%2020240107124937.png)

str()会将列表列详细展开
![Pasted image 20240107124942](attachments/Pasted%20image%2020240107124942.png)

```R
'data.frame':   150 obs. of  5 variables:
 $ Sepal.Length: num  5.1 4.9 4.7 4.6 5 5.4 4.6 5 4.4 4.9 ...
 $ Sepal.Width : num  3.5 3 3.2 3.1 3.6 3.9 3.4 3.4 2.9 3.1 ...
 $ Petal.Length: num  1.4 1.4 1.3 1.5 1.4 1.7 1.4 1.5 1.4 1.5 ...
 $ Petal.Width : num  0.2 0.2 0.2 0.2 0.2 0.4 0.3 0.2 0.2 0.1 ...
 $ Species     : Factor w/ 3 levels "setosa","versicolor",..: 1 1 1 1 1 1 1 1 1 1 ...
```


