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
# name:传入的参数为文件的实际路径 如果不存在则会报错
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



### write











### read









## 文件读写模式









## 缓冲区













