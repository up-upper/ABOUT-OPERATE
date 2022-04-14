# 简单的shell编程

## 编写shell脚本

![image-20220414235940682](picture/image-20220414235940682-16499519825791.png)

新建一个后缀为sh的文件

使用vi进入shell编译器

i开始编译模式

```shell
#!/bin/bash
echo "hello world!"
```

## 运行shell脚本的方法

（修改权限）才有执行的权限。

![image-20220415000012615](picture/image-20220415000012615-16499520139002.png)

## shell注释

![image-20220415000058026](picture/image-20220415000058026-16499520592183.png)

**单行**    *#+注释内容*

**多行**    *:<<!  注释内容  !*    (这是最常用的多行注释格式)，但其实多行注释中的！可以是任意的字符，只不过这里两个字符要求前后一致。举例如下，echo “hello world”一整句为注释内容，不会执行。但由于使用字符可能会给后面理解代码带来麻烦，所以通常使用！

```shell
#!/bin/bash
:<<a
echo "hello world"
a
```

## shell变量

![image-20220414231353705-164994923488111](picture/image-20220414231353705-164994923488111-16499521130894.png)

### 1、定义变量

#### a、普通变量

![image-20220414195210104](picture/image-20220414195210104-16499521463975.png)

数字不加引号，其他默认加双引号；

```shell
#!/bin/bash
number=10   #方式一
echo $number   #$表示取出变量的值

a='$number'   #方式二
echo $a

b="$number"   #方式三
echo $b
```

输出结果：

```shell
10
$number  #原样赋值
10
```

#### b、命令变量

![image-20220414215510688-16499445115787](picture/image-20220414215510688-16499445115787-16499521665596.png)

```shell
#!/bin/bash
c=`date`   #date是获取当前时间的函数，注意这里是反引号
echo $c

d=$(date)
echo $d
```

输出结果：

```shell
都为当前系统的时间
```

### 使用变量

![image-20220414215622727-16499445837258](picture/image-20220414215622727-16499445837258-16499521878807.png)

```shell
result="现在的时间为${d}"
echo "${result}"
```

输出结果：

![image-20220414231005272](picture/image-20220414231005272-16499522127828.png)

### 只读变量

用readonly标识，在这种情况下该变量不允许被修改，被修改时会报错。

```shell
readonly result
result="aaa"
```

此时执行会报错

![image-20220414231141936](picture/image-20220414231141936-16499522288399.png)

### 删除变量

用unset

```shell
unset result
echo "${result}"
```





