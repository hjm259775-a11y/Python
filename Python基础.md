# Python基础



## 基础语法



太基础了，不写小标题了

注释：

```py
# 注释
"""
注释
"""
'''
注释
'''
```





*   常见数据类型

1.  整型 int
2.  浮点型 float
3.  字符串型 str
4.  布尔型 bool 值只有两个 True/False
5.  复数型 complex
6.   后续章节会提到 容器 list/dict/tuple/set





**显示变量类型**

type()

```
int1 = 0o20
print(int1)
print(type(int1)) ————————————————————————————————————type(int1)会显示出int1的类型

float1 = 2.3e-2
print(float1)
print(type(float1))
```





**字符转ASCII码**

ord()，字符转ASCII码

```
str1 = "a"
print(ord(str1)) # 97
print(type(ord(str1))) #int，甚至还转了类型
```





**类型转换**

int(): 将字符串转换为整型

float(): 将字符串转换为浮点型

bool(): 转换为bool型

str():将其他类型转换为字签串

```
test1 = "10"
test2 = "1.2"
test3 = "True"
print(type(int(test1))) #int
print(type(float(test2))) #float
print(type(bool(test3))) #bool
```







**输出变量**

**格式化**

```py
name = "liucheng"
age = 20
print(f"我的名字是{name},年龄是{age}") # f==>format格式化

name = "liucheng"
age = 20
print(f"我的名字是%s,年龄是%.2f" % (name,age)) 
```





**输入变量** 

```
test = input("请输入一个整数:") ——————————————赋给了test
print(test)
```



```
test = input("请输入一个整数:")
print(f"输入的内容是{test},类型为{type(test)}") # str ———————————————————输入语句获取的所有数据类型都为str
print(f"输入的内容是{test},类型为{type(int(test))}") # int

test = int(input("请输入一个整数:")) ————————————————————————————————————想像这样进行数值匹配，就保证你输入的类型和转换的一致
print(f"输入的内容是{test},类型为{type(test)}") # int
```





## 运算符



### 算数运算符

`+ - * /`

`%`取余

`//`整除

`**`幂次方

```
print(3/2) # 1.5  --> int/float=float
print(3//2) # 1 
print(3//2) # 9
```







### 关系运算符



`< <= >=`
`==` 判断两个对象的数值是否相等
`!=` 判断两个对象的数值是否不等



```
res1 = 97
res2 = 97.0
res3 = "97"
res4 = 'a'
res5 = ord('a')
print(res1 == res2) #t
print(res1 == res3) #f
print(res1 == res4) #f
print(res1 == res5) #t
```





### 逻辑运算符



| 运算符 | 含义 |
| :----: | :--- |
|  and   | 与   |
|   or   | 或   |
|  not   | 非   |

逻辑运算的“短路”逻辑：与运篡第一个表达式为假在，则后续不闭判断，或运算一样







### 赋值运算符



赋值运算

`=`

复合赋值：对自身进行操作
`+=  -=  *=  /=  %=  //=  **=`



### 身份运算符



`is`  判断两个对象的引用是否相同 <==> 判断两个对象的内存地址是否为同一地址

`is not`  判断两个对象的引用是否相同



id()显示对象的内存地址

```
a = 10000000000000
b = 10000000000000
print(id(a))
print(id(b))
print(a is b) # True --> Python 为了省内存、跑得快，提前把数字做好了，存在内存里。只要你用这些数字，它就指给你同一个地址

arr1 = [1,2,3]
arr2 = [1,2,3]
print(id(arr1))
print(id(arr2))
print(arr1 is arr2) # False
```









### 成员运算符

```
str = "shitou"
print("hit" in str) # True
```





### 位运算符









### 三目运算符



```
age = 16
# True if 逻辑判断表达式 else False
jieguo = "成年" if age > 18 else "未成年"
print(jieguo)
```





判断闰年：

```
year = int(input("请输入年份"))
jieguo = "yes" if (year%4 == 0 and year%100 != 0) or year%400 == 0 else "no"
print(jieguo)
```





## if分支



测试单分支结构（当然，这个逻辑是错的）

```
age = 18
if age >= 18:
    print("成年") # 缩进(tab)
print("未成年") # 向前缩进(Shift + Tab)
```



测试多分支

```

age = 18
if age >= 18:
    print("成年")
else:
    print("未成年")
```





多次判断elif 统计成绩等级 <60:D  60~70:C  70~80:B  80~100:A

```
score = 40

if score >= 80:
    print("A")
elif score >= 70 and score < 80:
    print("B")
elif score >= 60 and score < 70:
    print("C")
else:
    print("D")
```







## 循环



### **while**

**（py没有i++）**

```
str = "hello"
i = 0;
while i<=5:
    print(str)
    i+=1
```

```
i = 0
sum = 0
while i<=100:
    sum+=i
    i+=1
print(sum)
```

```
i = 0
sum = 0
while i<=100:
    i+=1
    if i%10==5:
        continue
    sum+=i
print(sum)
```





### **for**

先了解下range函数：

​	range(x,y,z):

​		x：起始值，包含，可以省略，如果省略默认值为0

​		y：结束值，不包含，不可省略

​		z：步长，可以省略，默认值为1

比如range（3）就是0，1，2（因为是[0,3)）

**如果起始值比结束值大，步长必须写负数，否则循环一次都不会执行。**

```
sum = 0
for i in range(101):
    sum += i
print(sum)
```

```
for i in range(-10,0,2):
    print(i)

for i in range(10,0,-2):
    print(i)
```



### for-else结构

```
for 循环变量 in range():
    循环体
else:
    这里写的内容是for循环正常执行完毕后执行的内容（就是正常执行完for后要执行一下）
```



举例：

```
for i in range(0,10):
    if(i==5):
        continue
else: 
    print("shuchu") # 有输出

for i in range(0,10):
    if(i==5):
        break # 可以看出，终止循环直接跳出去，不会执行else
else: 
    print("shuchu") # 无输出
```







**练习：**一个自然数与3的和是5的倍数，与3的差是6的倍数，这个自然数最小是多少？

```
for i in range(0,10000,1):
    if((i+3)%5==0 and (i-3)%6==0 ):
        print(i)
        break
```







**练习：**在400~500之间求一个数，他被2除余1，被5除余3，被8除余1，这个数是多少？

```py
for i in range(400,501,1):
    if(i%2==1 and i%5==3 and i%8==1):
        print(i)
```





**练习：**两数交换

```
a,b = b,a
print(f"a:{a}")
print(f"b:{b}")
```





**练习：**输出5*5的星号矩阵

```
for i in range(0,5,1):
    for j in range(0,5,1):
        print("* ",end="") ——————————————可以把默认输出的换行去掉
    print() —————————————————————————————这就是换行
```





## 容器

*   用于存储数据

*   用于多个数据的计算和处理

*   内存中具有特定结构的空间



**线性表：**

本质就是内存中的一块连续的存储空间

除了第一个和最后一个元素，每个元素都有一个前驱元素和一个后继元素

### 列表

就是线性表的一种体现，在其他语言中叫做数组

**使用[]表示列表**

```
ter1 = [] ————————方法一
ter2 = list() ————方法二
print(ter1) ————————————————————输出[]
print(type(ter2)) ——————————————输出list
```



*   列表中存储的数据可以为任意类型
*   有序————自然顺序，元素存储先后顺序（和c/c++一样，从0开始计数。索引区间为`0 ~ n-1`或`-n ~ -1`）
*   可以重复

```
ter = [1,1,1,1,2.4,"xgz",[1,2,3],False]
print(ter)

输出：
[1, 1, 1, 1, 2.4, 'xgz', [1, 2, 3], False]
<class 'list'>
```



```
ter = [10,20,30,40,50]
print(ter[0])
print(len(ter)) ——————————————————输出列表的个数
print(ter[len(ter)-1]) ———————————列表最后一位
print(ter[-1]) ———————————————————50
print(ter[-5]) ———————————————————10
```









### 元组







### 字典









### 集合













### 字符串













































