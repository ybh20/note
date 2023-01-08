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

#### 1.3 源码、反码、补码

1. 二进制的最高位是符号位，0表示正数，1表示负数
2. 正数的源码、反码、补码都一样
3. 负数的反码 = 它的源码符号位不变，其他位取反
4. 负数的补码 = 反码 + 1
5. 0 的反码、补码都是 0
6. 在计算机运行的时候，都是以**补码的方式运算**的

#### 1.3 位运算，按位与&，按位或|，按位异或^

- 按位与 &：两位全为1，结果为1，否则为0
- 按位或 |：两位有一个为1，结果为1，否则为0
- 按位异或 ^：两位一个为0，一个为1，结果为1，否则为0

#### 1.3 算术左移 <<，算术右移 >>

​	算术左移 << ：符号位不变，低位补 0

​	算术右移 >> ：低位溢出，符号位不变，并用符号位补溢出的高位

### 1.4 流程控制

​	在程序运行过程中，流程控制决定程序是如何执行的。

#### 	1、顺序控制

​		程序从上往下逐行执行，没有任何的判断和跳转

#### 	2、分支控制

​		**1、单分支**

​			基本语法

```go
if 条件表达式 {
    // 代码块
}
```

​		**2、双分支**

​			基本语法

```go
if 条件表达式 {
    // 代码块
} else {
    // 代码块
}
```

​		**3、多分枝**

```go
if 条件表达式1 {
    // 代码块
} else if 条件表达式2 {
    // 代码块
} else if 条件表达式3 {
    // 代码快
} else {
    // 代码块
}
```

```go
// switch 分支结构
/*
	switch穿透-fallthrough，如果在case语句后增加fallthrough，则会继续执行下一个case，只会穿透一层
*/
```

### 1.5 函数

​	为完成某一功能的代码块。在go中，函数分为：自定义函数，系统函数。

​	基本语法：

- ```go
  func 函数名(形参列表) (返回值类型……) {
      // 函数体
      return 返回值列表……
  } 
  
  /*
  	注意：
  	如果有多个返回值，返回值类型之间则用逗号分隔。如果只有一个返回值，则可以省略返回值类型的括号
  */
  ```

#### 	1.5.1 函数的调用机制

- 在调用一个函数时，会给该函数分配一个新的空间，编译器会通过自身的处理让这个新的空间 和其它的栈的空间区分开来

- 在每个函数对应的栈中，数据空间是独立的，不会混淆

- 当一个函数调用完毕(执行完毕)后，程序会销毁这个函数对应的栈空间。

#### 1.5.2 init函数

- 每一个源文件中都可以包含一个init函数，该函数会在main函数执行之前被调用。
- 通常可以在init函数中完成一些初始化工作

#### 1.5.3匿名函数

1. 匿名函数的调用方式
   1. 在定义匿名函数的时候直接调用
   2. 将匿名函数赋值给一个变量

#### 1.5.4 函数中的defer

- 被defer标记的语句会被依次压入栈中，待函数执行完之后按照后进先出的方式依次执行

#### 1.5.5 值类型和引用类型

1. **值类型：**基本数据类型 int…… float…、bool、string、数据、结构体struct
2. **引用类型：**指针、切片slice、map、管道chan、interface等都是引用类型

### 1.6 内置函数

#### 	1.6.1 字符串函数

1. len()：统计字符串的长度，按字节计算，字母和数字占一个字节，汉字占三个字节。

   ```go
   str1 := "hello"
   fmt.Println("str1 len=", len(str1))
   ```

2. arr := []rune(str)：字符串遍历

   ```go
   str2 := []rune("hello，世界")
   for i := 0; i < len(str2); i++ {
   	fmt.Printf("%c", str2[i])
   }
   ```

3. n, err := strconv.Atoi("12345")：字符串转整数，n 是转换成功后的值，err 是转换失败的提示

   ```go
   n, err := strconv.Atoi("12345")
   if err != nil {
       fmt.Println(err)
   } else {
       fmt.Println(n)
   }
   ```

4. num := strconv.Itoa(12345)：整数转字符串

   ```go
   num := strconv.Itoa(12345)
   fmt.Printf("%v, %T", num, num)
   ```

5. bytes := []byte("hello go")：字符串转byte

   ```go
   bytes := []byte("hello go")
   fmt.Println(bytes)
   ```

6. str3 := string([]byte{97, 98, 99})：byte转字符串

   ```go
   str3 := string([]byte{97, 98, 99})
   fmt.Println(str3)
   ```

7. str4 := strconv.FormatInt(123, 2)：十进制转对应的2, 8, 16进制，返回一个字符串值

   ```go
   str4 := strconv.FormatInt(64, 8)
   fmt.Println(str4)
   ```

8. strings.Contains("hello", "e")：查找字符串中是否包含指定字串，返回一个布尔值

   ```go
   flag := strings.Contains("hello", "e")
   fmt.Println(flag)
   ```

9. strings.Count(str1, str2)：统计字串str2，在str1中出现的次数

   ```go
   str := strings.Count("hello", "e")
   fmt.Println(str)
   ```

10. strings.EqualFold(str1, str2) 和 == ：字符串比较，前者不区分大小写。

   ```go
   str6 := strings.EqualFold("hello", "HELLO")
   str7 := "hello" == "HELLO"
   fmt.Println(str6, str7)
   ```

11. strings.Index(str1, str2)：查找str2在str1中第一次出现的位置

    ```go
    index := strings.Index("hello", "e")
    fmt.Println("index =", index)
    ```

12. strings.LastIndex(str1, str2)：查找str2在str1中最后一次出现的位置

    ```go
    lastIndex := strings.LastIndex("helloe", "e")
    fmt.Println("lastIndex =", lastIndex)
    ```

13. strings.Replace(str, str1, str2, n)：字符串替换，用str2替换在str中存在的str1，n可以指定替换的个数，如果n=-1 表示全部替换。

    ```go
    str8 := strings.Replace("鸡你太美，鸡你实在是太没", "没", "美", 1)
    fmt.Println("str8 =", str8)
    ```

14. stings.Split(str, char)：字符串分割，用char将str分隔成一个数组

    ```go
    arr := strings.Split("hello，world，jack", "，")
    fmt.Println("arr =", arr)
    ```

15. strings.ToLower() 大写转小写 和 strings.ToUpper() 小写转大写

    ```go
    fmt.Println("ToLower =", strings.ToLower("GOLANG"))
    fmt.Println("ToUpper =", strings.ToUpper("golang"))
    ```

16. strings.TrimSpace(str)：去掉str两边的空格

    ```go
    str9 := strings.TrimSpace(" hello world jack ")
    fmt.Println(str9)
    ```

17. strings.Trim(str, chars)：去掉str两边的chars

    ```go
    str10 := strings.Trim("!hello world jack ", "! ")
    fmt.Println(str10)
    ```

18. strings.TrimLeft(str, chars)：去掉str左边的chars

19. strings.TrimRight(str, chars)：去掉str右边的chars

20. strings.HasPrefix(str1, str2)：判断str1是否以str2开头

21. strings.HasSuffix(str1, str2)：判断str1是否以str2结尾

#### 1.6.2 时间与日期函数

​	使用时间与日期函数需要先导入 time 包

1. time.Now()：获取当前日期
   1. time.Now().Year()：获取年份
   2. int(time.Now().Month())：获取月份，获取到的是英文的月份，可以用 int() 强转成数字的方式
   3. time.Now().Day()：获取当前月的第几天
   4. time.Now().hour()：获取小时
   5. time.Now().Minute()：获取分钟
   6. time.Now().Second()：获取秒数
   
2. time.Now().Format("2006-01-02 15:04:05")：日期格式化

3. time.Sleep(time.时间常量)：休眠

   ```go
   // 时间常量
   const (
   	Nanosecond  Duration = 1						// 纳秒
   	Microsecond          = 1000 * Nanosecond		 // 微秒
   	Millisecond          = 1000 * Microsecond		 // 毫秒
   	Second               = 1000 * Millisecond		 // 秒
   	Minute               = 60 * Second				// 分钟
   	Hour                 = 60 * Minute				// 小时
   )
   ```

4. time.Now().Unix() 和 time.Now().UnixNano()：获取1970年1月1日到现在的时间戳，前者获取的是秒，后者是纳秒

   ```go
   time.Now().Unix()
   time.Now().UnixNano()
   ```

#### 1.6.3 内置函数

1. len()：统计长度
2. new(数据类型)：用来分配内存，一般是值类型，返回的是指针
3. make：用来分配内存，一般是引用类型，返回的是指针

### 1.7  错误处理

1. go语言并不支持传统的 try……catch……finally 这种处理

2. go中引入的处理方式是：defer，panic，recover

3. 使用方式：go中抛出一个panic异常，然后在defer中通过recover捕获，然后正常处理

   ```go
   defer func() {
   	err := recover()
   	if err != nil {
   		fmt.Println(err)
   	}
   }()
   num1 := 10
   num2 := 0
   result := num1 / num2
   fmt.Println(result)
   ```

4. **自定义异常处理**

   - 使用 errors.New() 和 panic 内置函数

   - errors.New("错误说明") 会返回一个error类型的值，表示一个错误

   - panic内置函数，接收一个interface()类型的值作为参数。可以接受error类型的变量，输出错误信息，并推出程序。

     ```go
     func equalName(name string) (err error) {
     	if name != "嘿嘿嘿" {
     		return errors.New("名字不匹配……")
     	}
     	return nil
     }
     
     func main() {
         err := equalName("哈哈哈")
     	if err != nil {
     		fmt.Println(err)
     	}
     }
     ```


### 1.8 数组与切片

#### 1.8.1	数组介绍

​	数组可以存放多个同一数据类型的数据，在go中数组是值类型

1. 使用方式

   ```go
   // 一
   var arr [长度]数据类型 = [长度]数据类型 {1,2,3,4,5}
   // 二
   var arr = [长度]数据类型 {1,2,3,4,5}
   // 三
   var arr = [...]数据类型 {1,2,3,4,5}
   // 四
   var arr = [3]string{0:"tom", 1:"jack", 2:"marry"}
   ```

2. 数组的第一个元素的地址，就是数组的首地址

3. 数组的遍历

   ```go
   // 1、for循环
   var arr [3]int = [3]int {1,2,3}
   
   for i := 0; i < len(arr); i++ {
       fmt.println(arr[i])
   }
   
   // 2、for - range
   for index, value := range arr {
       fmt.println(index, value)
   }
   // 1、index 返回的是数组的下标
   // 2、value 返回的是下标对应的值
   // 3、如果不想使用下标，可以使用 _ 替换掉index切片
   ```


#### 1.8.2	切片

- ```go
  // 切片的定义
  
  // 1、定义一个切片，然后让切片去引用一个已经创建好的数组
  var arr = [...]int {}
  var sliceName = arr
  
  // 2、通过 make 来创建切片
  var slice []int = make([]int, len, size)
  
  // 3、
  var slice []int = []int {1,2,3}
  ```

- append(slice, v1, v2, ...) 将元素追加到slice切片的末尾。若它有足够的容量，其目标就会重新切片以容纳新的元素。否则，就会分配一个新的基本数组。append返回更新后的切片，因此必须存储追加后的结果。

- copy(slice1, slice2) 将slice2切片的元素复制到slice1切片中。

#### 1.8.3 二维数组

- ```go
  // 声明
  var arr [几行][几列]int
  
  // 初始化
  var arr [3][3]int = [3][3]int {{1,2,3}, {1,2,3}, {1,2,3}}
  ```

### 1.9 map

- ```go
  // map的定义方式
  // 方式一
  var map1 map[string]string
  map1 = make(map[string]string, 10)
  map1["name"] = "张三"
  
  // 方式二
  map2 := make(map[string]string)
  map2["name"] = "李四"
  
  // 方式三
  map3 := map[string]string{
      "name" : "王二",
  }
  
  // 删除元素
  delete(map3, name)
  
  // 查找元素
  value, flag := map3["name"]
  
  // 遍历
  for k, v := range map3 {
      fmt.Println(k, v)
  }
  ```

### 1.10 结构体

- ```go
  // 结构体的定义
  type Student struct {
  	Name string
  	Age int
  	Sex string
  }
  
  // 创建结构体实例
  // 方式一
  var stu Student
  stu.Name = "张三"
  stu.Age = 19
  stu.Sex = "男"
  
  // 方式二
  var stu = Student{"李四", 20, "男"}
  
  // 方式三
  var stu *Student = new(Student)
  (*stu).Name = "王五"
  (*stu).Age = 20
  (*stu).Sex = "男"
  // 我们发现这种通过指针的方式相对于前面两种方式比较麻烦，后来go给我们提供了简化的方式
  stu.Name = "小花"
  // 其实底层还是给我们转换成了 (*stu).Name = "小花"
  
  // 方式四
  var stu *Student = &Student{}
  stu.Name = "小红"
  
  // 结构体之间的相互转换
  type Student struct {
      Name string
  }
  
  type Person struct {
      Name string
  }
  
  func main() {
      var s Student = Student{"张三"}
      var p Person = Person{"张三"}
      p = Person(s)
  } 
  
  // 方法的引入
  type Cat struct {
      Name string
  }
  
  func (c Cat) show() {
      fmt.Println(c)
  }
  
  func main() {
      // 方法的调用
      var c Cat
      c.show()
  }
  ```

  

