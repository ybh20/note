# GO

### 1.1	go

go语言是一门静态编译型的语言，而不是动态解释型的。go语言的编译速度非常快，明显要快过其他同类型语言，比如 c 和 c++。

### 1.2	变量

变量的定义方式

![image-20221024184359882](C:\Users\86131\AppData\Roaming\Typora\typora-user-images\image-20221024184359882.png)

加号的基本使用

![image-20221026183255689](C:\Users\86131\AppData\Roaming\Typora\typora-user-images\image-20221026183255689.png)

### 1.3	数据类型

![image-20221026185606055](C:\Users\86131\AppData\Roaming\Typora\typora-user-images\image-20221026185606055.png)

#### 1.3.1	字符串类型

**字符串就是一串固定长度的字符连接起来的字符序列。**Go的字符串是由单个字节连接起来的。

基本使用：

![image-20221029193950760](C:\Users\86131\AppData\Roaming\Typora\typora-user-images\image-20221029193950760.png)

#### 1.3.2	布尔类型

1）布尔类型数据只允许取 true 和 false 两个值

2）布尔类型只占用1个字节

3）布尔类型适用于逻辑运算，用于程序流程控制

#### 1.3	基本数据类型转换

go在不同类型的变量之间赋值时需要**显示转换**。也就是说go中数据类型**不能自动转换。**

基本语法：

![image-20221030175526868](C:\Users\86131\AppData\Roaming\Typora\typora-user-images\image-20221030175526868.png)

注意事项：

1. 被转换的是**变量储存的值**，变量本身的数据类型并没有变化。
2. 在转换中，将一个大的转换成小的时，当大的数据类型存储的值超过小的数据类型能存储的范围时，编译时不会报错，只是转换后的结果是按溢出处理，和我们期望的结果不一样。

#### 1.3	基本数据类型转和string的转换

1. 方式一：fmt.Sprintf()

   ![image-20221030183530329](C:\Users\86131\AppData\Roaming\Typora\typora-user-images\image-20221030183530329.png)

   方式二：使用 strconv 包的函数
