# 文件管理命令

### 【cat】

作用：用于连接文件并打印到标准输出的设备上

> 主要参数：
>
> **-n 或 --number**：对输出的所有行进行编号。
>
> **-b 或 --number-nonblank**：和 -n 相似，空白行不编号。
>
> **-s 或 --squeeze-blank**：**压缩空行**，有连续两行以上的空白行，就代换为一行的空白行。
>
> **-v 或 --show-nonprinting**：使用 ^ 和 M- 符号，除了 LFD 和 TAB 之外。
>
> **-E 或 --show-ends** : 在每行结束处显示 $。
>
> **-T 或 --show-tabs**: 将 TAB 字符显示为 ^I。
>
> **-A, --show-all**：等价于 -vET。
>
> **-e：**等价于"-vE"选项；
>
> **-t：**等价于"-vT"选项；

示例：

1.显示文件：

```shell
cat 文件名  #可加命令输出行号更加美观：cat -n 文件名
```

2.文件内容连接：

```shell
cat  textfile1 > textfile2   #将文档1中的内容全部输出到文档2中，直接覆盖

cat  textfile1 >> textfile2  #将文档1中的内容全部附加到文档2中

#可加 -n 加上编号后输出 -b 空白行不编号

cat /dev/null > /etc/test.txt #将test文档内容清空
```

3.制作镜像：

```shell
cat /dev/fd0 > OUTFILE  #/dev/fd0 为设备 OUTFILE为文件名
```

相反的，如果想把 image file 写到软盘，输入：

```shell
cat IMG_FILE > /dev/fd0 #IMG_FILE为镜像文件，后者为设备
```



### 【rm】

作用：用于删除文件

> 主要参数：
>
> - -i 删除前逐一询问确认。**（一般不用）**
> - -f 即使原档案属性设为唯读，亦直接删除，无需逐一确认。
> - -r 将目录及以下之档案亦逐一删除。

示例：

```shell
rm  文件名 #删除文件

rm -r  目录名 #删除目录
```

​	以上会有询问：是否删除，如果想强制删除如下：

```shell
rm -f 文件名 #删除文件

rm -rf 目录名 #删除目录
```



> tips:如果想批量删除一些同名的文件，可以使用 * 通配符进行匹配删除
>
> 比如有许多文件：a1 a2 a3
>
> **rm -f a***



### 【cp】

作用：用于拷贝文件或者目录

> 主要参数：
>
> - -a：此选项通常在复制目录时使用，它保留链接、文件属性，并复制目录下的所有内容。其作用等于dpr参数组合。
> - -d：复制时保留链接。这里所说的链接相当于Windows系统中的快捷方式。
> - -f：覆盖已经存在的目标文件而不给出提示。
> - -i：与-f选项相反，在覆盖目标文件之前给出提示，要求用户确认是否覆盖，回答"y"时目标文件将被覆盖。
> - -p：除复制文件的内容外，还把修改时间和访问权限也复制到新文件中。
> - -r：若给出的源文件是一个目录文件，此时将复制该目录下所有的子目录和文件。
> - -l：不复制文件，只是生成链接文件。



```shell
cp 文件名 目标地址 #拷贝一个文件

cp -a 目录名 目标地址 #拷贝一个目录
```



### 【touch】

作用：创建空文件，或者改变文件的时间戳属性

> 主要参数：
>
> - a 改变档案的读取时间记录。
> - m 改变档案的修改时间记录。
> - c 假如目的档案不存在，不会建立新的档案。与 --no-create 的效果一样。
> - f 不使用，是为了与其他 unix 系统的相容性而保留。
> - r 使用参考档的时间记录，与 --file 的效果一样。
> - d 设定时间与日期，可以使用各种不同的格式。
> - t 设定档案的时间记录，格式与 date 指令相同。
> - --no-create 不会建立新档案。
> - --help 列出指令格式。
> - --version 列出版本讯息。

示例：

```shell
$ touch testfile                #修改文件时间属性为当前系统时间  
$ ls -l testfile                #查看文件的时间属性  
#修改后文件的时间属性为当前系统时间  
-rw-r--r-- 1 hdd hdd 55 2011-08-22 19:53 testfile  

$touch t1 	#如果文件不存在，会创建t1文件
```

