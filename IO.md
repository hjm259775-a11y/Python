# IO

IO流：程序和文件之间数据通道

<img src="C:/Users/xgz24/AppData/Roaming/Typora/typora-user-images/image-20261123214258100.png" alt="image-20261123214258100" style="zoom: 33%;" />

**write：**输出（写）

**read：**输入（读）



## 文件操作



### File对象





*   操作File对象属性及方法

| **操作**              | **说明**                                                    |
| --------------------- | ----------------------------------------------------------- |
| `file = open("路径")` | 建立与这个文件的流                                          |
| `file.closed`         | 返回True表示文件已被关闭，否则返回False。                   |
| `file.mode`           | 返回被打开文件的访问模式。                                  |
| `file.name`           | 返回文件的名称                                              |
| `file.readable()`     | 返回True表示file对象对文件有读的权限，返回False表示无读权限 |
| `file.writable()`     | 返回True表示file对象对文件有写的权限，返回False表示无写权限 |



```py

file = open("D:\\github\\py_node\\test\\nailong.txt")
print(file) # <_io.TextIOWrapper name='D:\\github\\py_node\\test\\nailong.txt' mode='r' encoding='cp936'>
# name:读取模式时，传入的参数为文件的实际路径 如果不存在则会报错
# mode:读写模式，默认为r
# buffer:缓冲区
# encoding：字符集，高频使用utf-8

# 返回文件的访问模式
print(file.mode) # r

file.close() # 关闭文件（关闭流）
file = open("D:\\github\\py_node\\test\\nailong.txt")

# 查看文件是否关闭（流是否关闭）
print(file.closed) # True

# 查看文件名称
print(file.name)

# 判断是否为可读或可写
print(file.readable())  # True
print(file.writable())  # False
```





## 文件读写

| **操作**        | **说明**                                                     |
| --------------- | ------------------------------------------------------------ |
| `read([count])` | 读取文件，返回一个字符串，count参数限制从头读取文件的字符（python3，python2读取字节）数量， |
| `readline()`    | 读取单独一行文件                                             |
| `readlines()`   | 返回文件中的所有行，返回一个列表                             |
| `write()`       | 将任何字符串写入文件，且不会加换行符                         |

### write

**写入文件**

**每次open时都会把本文件清空**

*文件存在时写入内容：*

```py
file = open("D:\\github\\py_node\\test\\nailong.txt","w",encoding="utf-8") # w表示写模式，覆盖写入文件
file.write("liucheng") 

file.write("""
liucheng
123
""") # 这里就是追加
file.close()
```

1.  `open(...)`：打开文件时，先清空原有内容。
2.  `file.write("liucheng")`：写入 `liucheng`。
3.  第二次 `file.write()`：从当前文件指针位置继续写入，而不是重新覆盖第一次写入的内容。





*文件不存在时写入内容：*（会自动创建文件）

```py
file = open("D:\\github\\py_node\\test\\lllll.txt","w",encoding="utf-8")
file.write("liucheng")
file.close()
```



### read

**读取时要考虑文件的指针指向问题，没次open时会初始化指针的位置**

```py
file = open("D:\\github\\py_node\\test\\nailong.txt","r",encoding="utf-8") # r表示读模式

print(file.read(3)) # liu
print(file.read(3)) # che
print(file.read()) # ng 即便这里是读取全部的意思，但是因为指针在这，所以你只能读取指针后的所有字符
```

>   文件不存在时读取文件会直接报错



**整行读取**

```py
file = open("D:\\github\\py_node\\test\\nailong.txt","r",encoding="utf-8")

# 每次读入一行
print(file.readline()) # 
print(file.readline()) # liucheng
print(file.readline()) # 123

# 将指针到最后的所有行按列表格式打出
print(file.readlines()) # ['\n', 'nailong'] 
```

>   
>
>   liucheng
>   123
>
>   
>
>   nailong



## 文件读写模式



**打开文件的模式：**

| **字符** | **含义**                                                     |
| -------- | ------------------------------------------------------------ |
| `r`      | （默认）以只读模式打开文件，并将文件指针指向文件头；如果文件不存在会报错 |
| `w`      | 以只写模式打开文件，并将文件指针指向文件头；如果文件存在则将其内容清空，如果文件不存在则创建 |
| `a`      | 以只读追加可写模式打开文件，并将文件指针指向文件尾部；如果文件不存在则创建 |
| `+`      | 在r、w、a基础上添加其读写功能，如r+：可读可写，w+可读可写，a+追加及可读可写 |
| `b`      | 二进制模式，读写二进制文件（默认是t，表示文本），需要与上面几种模式搭配使用，如ab，wb，rb，ab+，wb+，rb+ |



**操作指针的函数**

| **函数**  | **说明**                       |
| --------- | ------------------------------ |
| `seek(n)` | 将文件指针移动到指定字节的位置 |
| `tell()`  | 获取当前文件指针所在字节位置   |

```py
file = open("D:\\github\\py_node\\test\\nailong.txt","w",encoding="utf-8",buffering=1)
file.write("liucheng") 
print(file.tell()) # 8
file.seek(5)
print(file.tell()) # 5
file.write("sunhanhua")
file.close() 
# 变成liuchsunhanhua了
```









**可读可写（读方式打开的）**（这就导致了要是文件不存在会以读的方式运行，也就是报错）

```py
file = open("D:\\github\\py_node\\test\\nailong.txt","r+",encoding="utf-8")
file.write("liucheng") # r+ 不会清空原文件内容，而是从文件开头开始覆盖写入(覆盖多少写多少，其他的也不变)(123456789变成liucheng9)
file.close()
```



**追加模式**

```py
file = open("D:\\github\\py_node\\test\\nailong.txt","a",encoding="utf-8")
file.write("\nsunhanhua") # 在文件最末尾换行添加sunhanhua
file.close()
```



**追加模式的可读可写**

```py
file = open("D:\\github\\py_node\\test\\nailong.txt","a+",encoding="utf-8")
file.write("lisi")
print(file.read())  # 追加时只能写入不能读取 注意指针问题指针处于文件末尾
file.close()
```



**二进制模式的读写**

```py
file = open("D:\\github\\py_node\\test\\nailong.txt","wb+")
file.write(b"sunhanhua") # 以二进制形式传入
file.close()

file = open("D:\\github\\py_node\\test\\nailong.txt","rb+")
print(file.read()) # b'sunhanhua'
file.close()
```









## 缓冲区

**为了减少程序与文件之间的交互次数，程序会在自己的区域开辟一个空间叫缓冲区，当close或者缓冲区满了之后，就会把它一次性推向文件，只有一次交互**



*   open的缓冲区buffering参数问题：

​	`-1`：默认缓冲

​	`0`：自行扩展 --- 二进制时使用

​	`1`：行缓冲 --- 见到换行符时刷新缓冲区

​	`> 1`：固定缓冲区大小



**默认缓冲区：**（等缓冲区满了或手动刷新才写入文件）

```py
file = open("./5.IO/test4_file.txt", "w", encoding="utf-8")
file.write("liucheng")
input("暂停程序，查看文件是否写入:按回车继续")
file.flush()  # 手动刷新缓冲区
file.close()  # 关闭流释放资源并刷新缓冲区
```





**行缓冲区：**（行缓冲区遇到换行符 `\n` 就会自动刷新。）

```py
file = open("D:\\github\\py_node\\test\\nailong.txt","a+",encoding="utf-8",buffering=1)
file.write("username:") 
input("暂停程序，查看文件，是否写入:按回车继续")
file.write("zhangsan\n")  #换行符自动刷新缓冲区，这个时候看文件就是username:zhangsan
input("暂停程序，查看文件，是否写入:按回车继续")
file.write("password")
input("暂停程序，查看文件，是否写入:按回车继续")
file.flush()  #手动刷新缓冲区
file.close()  # 关闭流释放资源并刷新缓冲区
print("程序终止")
```





# with

**简化IO的读写操作**



```py
# 读
with open("D:\\github\\py_node\\test\\nailong.txt","r",encoding="utf-8") as file:
    print(file.read())

# 写
with open("D:\\github\\py_node\\test\\nailong.txt","w",encoding="utf-8") as file:
    file.write("xibababalubila")

# with中不止可以open一个文件，open多个以实现复制相同内容至别的文件
with open("D:\\github\\py_node\\test\\nailong.txt","r",encoding="utf-8") as f1,open("D:\\github\\py_node\\test\\nailong1hao.txt","w",encoding="utf-8") as f2:
    f2.write(f1.read())
```





































