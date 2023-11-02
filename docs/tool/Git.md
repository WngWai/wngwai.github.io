# 关于Rtudio从Github中克隆仓库和同步文件的流程简介

## 一、在Rstudio中克隆Github上的项目
### 1，登录Github账号：

[https://github.com/login](https://github.com/login)
![Pasted image 20231102143038](attachments/Pasted%20image%2020231102143038.png)
 

### 2，找到作业仓库

### （1）确保自己已经链接到老师给的作业仓库；

### （2）登录个人账号后在个人仓库找到作业仓库，前缀基本一样：
![Pasted image 20231102143045](attachments/Pasted%20image%2020231102143045.png)

![Pasted image 20231102143058](attachments/Pasted%20image%2020231102143058.png)

### 3，复制个人作业仓库HTTPS（**URL地址**）
![Pasted image 20231102142630](attachments/Pasted%20image%2020231102142630.png) 

### 4，打开个人Rstudio软件
按照File->New Project->Version Control->Git的顺序打开克隆Github仓库的界面：
![Pasted image 20231102143112](attachments/Pasted%20image%2020231102143112.png)

![Pasted image 20231102143117](attachments/Pasted%20image%2020231102143117.png)

![Pasted image 20231102143127](attachments/Pasted%20image%2020231102143127.png)



### 5，将Github中的个人作业仓库内容克隆到本地
粘贴上面复制的个人作业仓库的URL地址，点击creatproject创建R项目，这样就可以将Github中的个人作业仓库内容克隆到本地了！

注意：需要保证自己连接到外网，之前群里分享的fastgithub软件只能连接到Github网页。

![Pasted image 20231102143142](attachments/Pasted%20image%2020231102143142.png)

![Pasted image 20231102143202](attachments/Pasted%20image%2020231102143202.png)


## 二、设置Rstudio的**Git选项卡**
实现Rstudio文件与Github仓库文件同步

### 1，Rstudio软件中没有看到Git选项卡：

需要先装Git软件，在QQ群里查找对应Git安装程序，或登录https://git-scm.com/下载。

注意：Git安装的**文件目录**需要记住，后面要用。

![Pasted image 20231102143226](attachments/Pasted%20image%2020231102143226.png)

![Pasted image 20231102143240](attachments/Pasted%20image%2020231102143240.png)

![Pasted image 20231102143252](attachments/Pasted%20image%2020231102143252.png)
### 2，在Rstudio中配置Git环境：

按照Tool->Global Options...->Git/SVN的顺序找到Rsudio中的Git选项。一般安装完Git后，Rstudio应该会自动链接到git.exe程序，如果没有，从之前安装的Git的文件目录中按图中途径手动添加。

![Pasted image 20231102143302](attachments/Pasted%20image%2020231102143302.png)

![Pasted image 20231102143311](attachments/Pasted%20image%2020231102143311.png)

顺带创建SSH key（远程连接服务钥匙？），复制，下一步备用。

![Pasted image 20231102143330](attachments/Pasted%20image%2020231102143330.png)

![Pasted image 20231102143338](attachments/Pasted%20image%2020231102143338.png)


### 3，实现Rstudion与Github的关联
通过一、1中登录Github账号，找到SSH，配置远程连接。

![Pasted image 20231102143353](attachments/Pasted%20image%2020231102143353.png)

![Pasted image 20231102143401](attachments/Pasted%20image%2020231102143401.png)

![Pasted image 20231102143413](attachments/Pasted%20image%2020231102143413.png)

输入之前复制的SHH key，点击添加，配置完成，实现Rstudio跟个人的Github关联。

![Pasted image 20231102143426](attachments/Pasted%20image%2020231102143426.png)

![Pasted image 20231102143433](attachments/Pasted%20image%2020231102143433.png)


## 三、在Rstudio中实现本地克隆文件与GitHub中对应仓库文件的同步
### 1，在本地作业文件中添加debug.Rmd和对应的pdf文件（pdf文件导出详见群中吴qi同学分享的指南）。
对比Github中的原仓库文件，原仓库文件没有改动。

![Pasted image 20231102143458](attachments/Pasted%20image%2020231102143458.png)

![Pasted image 20231102143506](attachments/Pasted%20image%2020231102143506.png)

### 2，将修改的文件进行缓存  
![Pasted image 20231102143516](attachments/Pasted%20image%2020231102143516.png)

![Pasted image 20231102143527](attachments/Pasted%20image%2020231102143527.png)
### 3，将缓存区文件内容提交到GitHub中连接的远程仓库

#### （1）可以看到commit后GitHub对应仓库中文件没有更新。

 ![Pasted image 20231102142818](attachments/Pasted%20image%2020231102142818.jpg)

#### （2）看History，提交记录中是有提交信息的。
![Pasted image 20231102143538](attachments/Pasted%20image%2020231102143538.png)


#### （3）将缓存文件push到GitHub的远程仓库中
注意：要保证能连到外网。

![Pasted image 20231102143548](attachments/Pasted%20image%2020231102143548.png)

![Pasted image 20231102143607](attachments/Pasted%20image%2020231102143607.png)

刷新，再看远程仓库就有文件。commit提交的信息均有显示。

![Pasted image 20231102143614](attachments/Pasted%20image%2020231102143614.png)