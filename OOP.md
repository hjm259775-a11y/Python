# OOP

**面向对象编程思想**



**特性：**

-   代码复用
-   可扩展性



==**例如：**==

-   张三打开了505教室门
-   李四打开了506教室门

**面向过程：**

根据业务功能编写 C 程序实现功能，两条程序完成。

**面向对象：**

通过泛化的过程，扩大思考范围，将具有共同属性和行为的事物抽象成类。

**分成两类：**

**人类**

-   属性：姓名
-   行为：开门

**门类**

-   属性：门号
-   行为：被打开



==**示例：**==

思考：张三把5吨重的大象装进海尔冰箱分几步？

**人类：**

-   属性：`name`
-   行为：`take_elephant` / `open_door` / `close_door`

**大象类：**

-   属性：`weight`
-   行为：被人拿起 / 装进冰箱

**冰箱类：**

-   属性：`singe`（原图标注）
-   行为：被打开 / 被关闭 / 装大象



==**类：**==

将公共属性和行为封装的一种数据类型。

类中包含两个重要的成员：

-   属性（变量）
-   行为（功能 / 方法 / 函数）

==**对象：**==

-   理解：类中的某一个具体个体。

-   抽象 → 具体。

    

**核心概念总结**

| 概念     | 说明                                   |
| -------- | -------------------------------------- |
| OOP      | 面向对象编程思想                       |
| 面向过程 | 根据业务功能编写程序实现功能           |
| 面向对象 | 将事物抽象成类，通过类组织属性和行为   |
| 类       | 将公共属性和行为封装的一种数据类型     |
| 属性     | 变量，用于描述事物的特征               |
| 行为     | 功能、方法、函数，用于描述事物能做什么 |
| 对象     | 类中的一个具体个体                     |

  





## 类和对象

==**类：**==

将公共属性和行为封装的一种数据类型。

类中包含两个重要的成员：

-   属性（变量）
-   行为（功能 / 方法 / 函数）

==**对象：**==

-   理解：类中的某一个具体个体。

-   抽象 → 具体。

    

### 创建类

```py
class 类名:
class 类名():
```



```py
class lei:
    name = 'zhangsan' # 属性

    def kaimen(self): # 行为
        print(f"{self.name}打开了门")
```

>   注意：self 的本质
>
>   -   `self` 不是 Python 的关键字，而是一种约定俗成的参数名称。
>   -   `self` 代表调用当前类的属性。
>   -   `self` 是实例方法的第一个形参。
>   -   通过对象调用实例方法时，Python 会自动传入该对象，不需要手动传递。





### 调用



```py
class lei:
    name = 'zhangsan'

    def kaimen(self):
        print(f"{self.name}打开了门")


shili = lei() # 将要操作的类用变量装起来，避免在堆中创建对象，默认值永远都是张三的问题（起个代号）
shili.name = 'liucheng' # 将shili这个对象里的name改成liucheng
shili.kaimen() # 会输出liucheng打开了门

p1 = lei()
p1.name = "huangyueying"
p1.kaimen() # 输出huangyueying打开了门
```





冷知识：输出id(Person)和输出id(Person()) 

*   输出id(Person)：类定义时类本身的地址

*   输出id(Person())：创建对象后的对象地址

其实无关紧要，所以我没用特殊格式







## 构造函数

**构造方法：**

-   创建对象时，为其属性赋初值（初始化属性的意思）
-   **创建对象时，执行其构造函数**
-   **如果没有显式的写出构造方法，则系统会提供一个默认的无参构造方法**
-   如果显式的写出了任何一个构造方法，则系统将不会提供默认的无参构造方法

>    创建对象时执行的是类中的 `__init__` 函数





**无参构造函数：**

````py
class lei:
    username = None
    password = None

    def __init__(self): # 无参构造函数
        print("构造函数")

    def shuchu(self):
        print(f"mingzi:{self.username},mima:{self.password}")

duixiang = lei() # 输出“构造函数”
duixiang.shuchu() # mingzi:None,mima:None
````





**有参构造函数：**

```py
class lei:
    username = None
    password = None

    def __init__(self,username,password): # 有参构造函数
        self.username = username # 加了self代表当前对象的变量，不加self的是参数
        self.password = password
        print("构造函数")

    def shuchu(self):
        print(f"mingzi:{self.username},mima:{self.password}")

duixiang = lei("liucheng",123) # 输出“构造函数”
duixiang.shuchu() # mingzi:liucheng,mima:123
```

>   **self关键字**
>
>   -   定义在类中的函数，必须增加参数self，参数self不需要传递参数。
>   -   作用只在于在函数内部调用类中的成员变量。
>   -   `self` 表示当前对象。其实就相当于`lei()`，这么想就行了，当然，要是越想越绕那还是不想了



>   `__init__()` **就相当于给新创建的对象提供了一个自动初始化的机会。**













​      