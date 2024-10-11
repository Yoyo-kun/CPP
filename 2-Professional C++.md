# ***C++ 高级编程***

***

如果只想学习高级方法，那么就请看第 9 章的零规则，就可以知道，前面的努力很大程度上都只是在为了迁就一些较为落后的代码语法。前面的很重要，但是部分确实是在逐渐被淘汰的！！！

2.7 和 8.1 / 3 的区别，记住比较两个浮点数的大小仅关注极小误差量！！！

## ***第一部分 —— 专业 C++ 简介***

***

## **第1章 —— C++ 和标准库速成**

***

### **1.1	C++ 基础知识**

****

#### **1.1	小程序 “hello world”**

****

```c++
// helloworld.cpp
#include <iostream>

int main()
{
	std::cout << "Hello, World!" << std::endl;

	return 0;
}
```

##### 1.注释

> - 单行注释，使用    **//**    符；
> - 多行注释，使用    **/*    */**    符；

***

##### 2.预处理指令

> - 生成一个 C++ 程序共有三步：
>
>   > - 首先，代码在预处理器中运行，预处理器会识别代码中的 **元信息*(meta-information)***;
>   >
>   > - 其次，代码被编译或转换为计算机可识别的目标文件；
>   >
>   > - 最后，独立的目标文件被连接在一起变成一个目标文件；
>
> - 预处理指令以    **#**    字符开始；
>
> - **include** 指令告诉预处理器：提取    **`<iostream>`**    头文件中的所有内容并提供给当前文件；
>
>   > - 头文件，最常见的用途是定义在其他位置的函数，**函数声明**会通知编译器如何调用这个函数，并声明函数中参数的个数和类型，以及函数的返回类型。而函数定义包含这个函数的实际代码；
>   > - 在 C++ 中，**声明**通常放在扩展名为    **`.h`**    的文件中，称为头文件；
>   > - 在 C++ 中，**定义**通常包含在扩展名为    **`.cpp`**    的文件中，称为源文件；
>   > - **`<iostream>`**    头文件声明了 C++ 如何提供输入输出机制，如果程序没有包含这个头文件，甚至无法执行器仅需要完成的输入输出文本；
>
> - 注意：
>
>   > - 在 C 中，标准库头文件以    **`.h`**    结尾，如    **`<stdio.h>`**    ，不使用名称空间；
>   >
>   > - 在 C++ 中，标准库头文件以    **`.h`**    结尾，如    **`<iostream>`**    ,所有文件都在 **`std`** 名称空间和 **`std`** 的子名称空间中定义；
>   >
>   > - C 中的标准库头文件在 C++ 中依然存在，但是使用以下两个版本：
>   >
>   >   1. 不使用    **`.h`**    后缀，改用前缀    **`c`**；
>   >
>   >      > 这是新版本，也是推荐使用的版本。这些版本将一切放在     **`std`**    名称空间中，如    **`<cstdio>`**；
>   >
>   >   2. 使用    **`.h`**    后缀；
>   >
>   >      > 这是旧版本，这些版本不使用名称空间，如    **`<stdio.h>`**；
>
> - 常见预处理指令
>
>   > - ```C++
>   >   #include [filename]
>   >   // 将指定的文件插入代码指令虽在的位置；
>   >   // 几乎总是用来包含头文件，是代码可使用在其他位置定义的功能；
>   >   ```
>   >
>   > - ```c++
>   >   #define [key] [value]
>   >   // 每个指定的 key 都被替换为指定的 value；
>   >   // 在 C 中，常用来定义常数值或宏；
>   >   // 在 C++ 中，提供了常数和大多数宏类型的更好机制，此外，宏的使用具有一定风险，故谨慎使用；
>   >   ```
>   >
>   > - ```c++
>   >   #ifdef [key]
>   >   #endif
>   >                                                   
>   >   #ifndef [key]
>   >   #endif
>   >   // ifdef("if defined") 块或 ifndef("if not defined") 块中的代码被有条件地包含或者舍弃；
>   >   // 上述保留或舍弃取决于是否使用 #define 定义了指令的 key；
>   >   ```
>   >
>   > - ```C++
>   >   pragma [xyz]
>   >   // xyz 因编译器而异；
>   >   // 如果在预处理期间执行到这一指令通常会显示一条警告或错误信息；
>   >   ```
>   >
>   > - 下面是使用预处理指令避免重复包含的示例：
>   >
>   >   - ```c++
>   >     #ifndef MYHEADER_H
>   >     #define MYHEADER_H
>   >     // ... the contents of this header file
>   >     #endif
>   >     ```
>   >
>   >   - ```c++
>   >     #pragma once
>   >     // ... the contents of this header file
>   >     ```
>   >
>   >   - 上述两段代码起到的效果相同；

***

##### **3.main()** 函数

> - main()    函数是程序的入口。
>
> - main()    函数返回一个    int    值以指示程序的最终执行状态。
>
> - main()    函数中，可忽略显式的    **`return`**    语句，此时，会自动返回    0；
>
> - main()    函数只有两种参数设置：
>
>   1. ```c++
>      int main()
>      ```
>
>   2. ```c++
>      int main(int argc, char* argv[])
>      ```
>
>      > **`argc`**    给出了传递给程序的实参数目，**`argv`**    包含了这些参数；
>      >
>      > 注意：
>      >
>      > ​	**`argv[0]`**    可能是程序的名称，也可能是空字符串，但不应依赖它，相反，应当使用特定于平台的功能来检索程序名。重要是记住，实际参数从索引    1    开始；

***

##### 4.输入输出流

> 可以将输出流想象为针对数据的**洗衣滑槽*(chute)***；
>
> > 放入其中的任何内容都可以被正确地输出
>
> 1. **`std::cout`** 
>
>    > 对应用户控制台或标准输出的滑槽；
>    >
>    > <<	用于将信息放入滑槽中；
>    >
>    > ```c++
>    > #include <iostream>
>    > int main()
>    > {
>    > 	std::cout << "There are " << 219 << " ways."
>    > 
>    > 		return 0;
>    > }
>    > ```
>    >
>    
>2. **`std::cerr`**
> 
>   > 对应输出错误信息的滑槽；
>    >
>    > ```c++
>    > #include <iostream>
>    > int main()
>    > {
>    > 	std::cerr << "Not right!";
>    > 	// 用于对错误信息的输出；
>    > 	return 0;
>    > }
>    > ```
>    >
>    
> 3. **`std::endl`**
>
>    > 用于表示序列的结尾，相当于 \n
>   >
>    > 此外常见的转义字符有：
>    >
>    > ​	\n	换行
>    >
>    > ​	\r	回车
>    >
>    > ​	\t	制表符
>    >
>    > ​	\\\	反斜杠字符
>    >
>    > ​	\\\"	引号
> 
> 4. **`std::cin`**
>
>    > 用于接收用户的输入，最简单的方法就是在输入流中使用    >>    运算符；
>   >
>    > ```c++
>    > #include <iostream>
>    > int main()
>    > {
>    > 	int value;
>    > 	std::cin >> value;
>    > 	// 由于永远不知道用户会输入什么类型的数据，因此需慎重对待用户的输入；
>    > 
>    > 	return 0;
>    > }
>    > ```
>    >
>    > 注意：
>    >
>    > ​	在 C 中使用的    printf()    和    scanf()    未提供类型安全，虽然，在 C++ 中仍然使用    printf()，但，仍建议改用流库，更安全；

***

#### **1.2	名称空间**

****

##### 1.名称空间

​	名称空间，用于处理不同代码之间的名称冲突问题；

> 例如，用户自己编辑了一段代码，其中有一个名为    foo()    的函数，但是，有一天，用户决定使用第三方库中，其中也有一个函数名为    foo()，这时编辑器无法自行判断你的代码要使用哪个版本的的    foo()    函数，库名称无法改变，而改变自己代码中函数名称又十分麻烦；
>
> 
>
> 上述情况，可以使用名称空间来解决，使用名称空间来指定定义名称的环境，为某段代码加入名称空间可使用    namespace    块将其包含其中。例如，可在    namespaces.h    声明函数示例：
>
> ```c++
> // namespace.h
> namespace mycode
> {
> 	void foo();
> }
> // 可以看到，这里的 mycode 实际上是 namespace 类的一个实例化
> ```
>
> 在名称空间中还可以实现方法或函数，例如，foo()    函数可在    namespaces.cpp    中实现，下给出示例：
>
> ```c++
> // namespaces.cpp
> #include <iostream>
> #include "namespaces.h"
> 
> void mycode::foo()
> {
> 	std::cout << "foo() named in the mycode namespace." << std::endl;
> }
> ```
>
> 或者：
>
> ```c++
> #include <iostream>
> #include "namespaces.h"
> 
> namespace mycode
> {
> 	void foo()
> 	{
> 		std::cout << "foo() called in the mycode namespace." << std::endl;
> 	}
> }
> ```
>
> 这样，就能够将用户书写的    foo()    函数与第三方库的    foo()    函数区分，使用以下调用方式：
>
> ```c++
> mycode::foo();
> // 其中，    ::    符称为作用域解析运算符；
> // mycode    名称空间中的任何代码都可以调用该名称空间中的其他代码，而不需要显式地说明该名称空间；
> 
> // 如果出现名称空间过长的情况，可使用以下方法：
> namespace mynamespace = namespace_top::namespace_middle::naespace_bottom;
> mynamespaces::foo();
> // 即，使用同名来化简
> ```

****

#####     **2.`using`**    指令：

>  - 可以避免预先指明命名空间，使得代码清晰并且易于阅读；
>
>  - 该指令通知编译器，后面的代码将使用指定名称空间中的名称；
>
>    > 例如：
>    >
>    > ```c++
>    > #include "namespaces.h"
>    > using namespace mycode
>    > 
>    > int main()
>    > {
>    > 	foo();
>    > 
>    > 	return 0;
>    > }
>    > ```
>    >
>    > 虽然，一个源文件中可以包含多条    **`using`**    指令，但是这种方法虽然便捷，但是注意不要过度使用！
>    >
>    > **注意：**
>    >
>    > ​	**极端情况下，如果你使用了已知的所有名称空间，实际上，就是完全取消了名称空间；**
>    >
>    > ​	**如果使用了两个同名的名称空间，将再次出现名称冲突问题；**
>    >
>    > ​	**此外，应当知晓每段代码在哪个名称空间中运行，这样就不会无意中调用错误版本的函数；**
>
>  - **注意：切勿在头文件中使用    `using`    指令或    `using`    声明！**

###### 	1.头文件中使用可能导致的问题

>  > 1. **不允许在头文件中使用    `using`    指令，否则，可能会出现引入头文件的源文件中的全局命名空间被改变，从而可能引发命名冲突。**
>  >
>  >    > 例如：
>  >    >
>  >    > ```c++
>  >    > // 在头文件中避免这样的使用
>  >    > // project_1.h
>  >    > 
>  >    > using namespace std;
>  >    > // 可能会出现引入头文件的源文件中的全局命名空间被改变，从而可能引发命名冲突
>  >    > ```
>  >
>  > 2. **使用    `using`    声明引入头文件的源文件中的特定名称，作用于每个引入文件，同样可能也会导致命名冲突。**
>  >
>  >    > 例如：
>  >    >
>  >    > ```c++
>  >    > // 在头文件中避免这样的使用
>  >    > // project_1.h
>  >    > 
>  >    > using std::cout;
>  >    > // 作用于每个引入文件，同样可能也会导致命名冲突
>  >    > ```

###### 	**2.解决方案：**

>   1. *使用权限定名称**
>
>       > ```c++
>       > // 全限定名称示例
>       > 
>       > namespace_name::entity_name
>       > // 即，在每次声明和定义函数的时候，都指明其命名空间
>       > ```
>
>   2. **在头文件中使用命名空间别名**
>
>       >   `````C++
>       >   // example.h
>       >   #ifndef EXAMPLE_H
>       >   #define EXAMPLE_H
>       >   
>       >   namespace mynamespace
>       >   {
>       >   	void myFunction();
>       >   	// 使用命名空间别名
>       >   }
>       >   
>       >   #endif 
>       >   `````
>
>   3. **限制使用 using 的范围**
>
>       >   `````C++
>       >   // example.h
>       >   #ifndef EXAMPLE_H
>       >   #define EXAMPLE_H
>       >   
>       >   namespace mynamespace
>       >   {
>       >   	using std::cout;
>       >   	// 在特定的命名空间中使用using
>       >   
>       >   	void myFunction();
>       >   }
>       >   
>       >   #endif 
>       >   `````

#### **1.3	字面量**

##### 1.字面量

字面量用于在代码中编写数字或字符串。C++ 支持大量标准字面量，可以使用以下字面量表示指定数字(列出的示例都表示数字 123)：

> - 十进制字面量	123
> - 八进制字面量	0173
> - 十六进制字面量	0x7B
> - 二进制字面量	0b1111011

##### 2.其他字面量：

> - 浮点值	如：3.14f
> - 双精度浮点值	如：3.14
> - 单个字符	如：'a'
> - 以零结尾的字符数组	如："character array"

##### 3.自定义自变量类型

> 自定义自变量类型，这是一种高级功能；

##### 4.数字分隔符

​	数字分隔符,可以在数值字面量中使用数字分隔符，数字分隔符是一个单引号，例如：

> - 23'456'789
> - 0.123'456f

##### 5.十六进制浮点字面量

​	此外，C++17还增加了对十六进制浮点字面量的支持，例如：

> - 0x3.ABCp-10
> - 0Xb.cp121

****

#### **1.4	变量**

> 在 C++ 中，可以在任何位置声明变量，并且可以在声明一个变量所在行之后任意位置使用该变量。声明变量时可不指定值，这些未初始化的变量通常会被赋予一个半随机值，这个值取决于当前内存的内容(这是许多    bug    的来源)。在 C++ 中，也可以声明变量时为变量指定初始值。下面给出两种风格的变量声明方式，使用的都是代表整数的    int    类型：
>
> ```c++
> int unintializedInt;
> int initializedInt = 7;
> cout << uninitializedInt << " is a random value" << endl;
> cout << initializedInt << " was assigned an initial value" << endl;
> ```
>
> 注意：
>
> > 当代码使用未初始化的变量时，多数编译器会给出警告或报错信息。当访问未初始化的变量时，某些 C++ 环境可能会报告运行时错误。

##### 1.整型 & size_t：

> ```c++
> // (signed) int					正整数或负整数，范围取决于编译器
> // 通常占 4 字节
> int i = -7;
> signed int i = -6;
> signed i = -5;
> 
> // (signed) short (int)			短整型整数
> // 通常占 2 字节
> short s = 13;
> short int s = 14;
> signed short s = 15;
> signed short int s = 16;
> 
> // (signed) long (int)			长整型整数
> // 通常占 4 字节
> long l = -7L;	// L 可省略
> 
> // (signed) long long (int)		超长整型整数，范围取决于编辑器，但不低于长整数
> // 通常占 8 字节
> long long ll = 14LL;	// LL 可省略
> 
> // unsigned (int / short int / long int / long long int)
> // 对前面的类型加以限制，使其值 >= 0
> unsigned int i = 2U;
> unsigned j = 5U;
> unsigned short s = 23U;
> unsigned long l = 5400UL;
> unsigned long long = 140ULL;
> // 每个值的后缀单词都可以省略
> ```
>
> **关于 size_t 的使用优点**：
>
> ```C++
> // 必须要引入以下头文件才可以使用：
> #include <cstddef>
> ```
>
> 1. **无符号性质：** `size_t` 是无符号整数类型，因此它只表示非负整数值。这有助于避免与负数相关的问题，特别是在处理数组索引和对象大小时。使用 `int` 可能导致符号错误，例如负索引或溢出。
> 2. **平台独立性：** `size_t` 的大小足够大，可以容纳系统中最大可能的对象大小。在不同平台上，`int` 的大小可能会有所不同，因此在需要确保跨平台一致性时，使用 `size_t` 更为合适。
> 3. **与标准库的一致性：** C++标准库和STL广泛使用 `size_t`，因此在与标准库交互时，使用 `size_t` 使得代码更一致，更容易集成。
> 4. **提高代码清晰度：** 使用 `size_t` 作为大小和索引的类型，可以提高代码的可读性和表达能力。它传达了程序员的意图，即该值用于表示大小或索引，而不是一般性的整数。

##### 2.**浮点型：**

> ```c++
> // float						浮点型数字
> // 通常占 4 字节
> float f = 7.2f;
> 
> // double						双精度浮点型数字
> // 通常占 8 字节
> double d = 7.2;
> 
> // long double					长双精度浮点型数字
> // 通常占 8、12、16 等字节，取决于编译器和平台
> long double d = 16.78L;
> ```

##### 3.**字符型：**

> ```c++
> // char							单个字符
> // 通常占 1 字节
> char ch = 'm';
> 
> // chat16_t						单个 16 位字符
> // 占 16 位字节
> char16_t c16 = u'm';	// u 可省略
> 
> // chat32_t						单个 32 位字符
> // 占 32 位字节
> char32_t c32 = U'm';	// U 可省略
> 
> // wchar_t						单个宽字符
> // 大小取决于编译器
> wchar_t w = L'm';
> 
> // 后面三种类型主要用于处理 Unicode 字符
> // Unicode 是一种字符编码标准，为每个字符都分配了一个唯一的数字码点，以便在计算机中进行统一字符表示
> ```

##### 4.**布尔类型：**

> ```c++
> // bool							布尔类型，取值为 true 或 false
> // 占 1 字节
> bool b = true;
> ```

##### 5.**单字节：(需引入 `<cstddef>` 头文件)**

> ```c++
> // std::byte							单个字节
> // 在 C++17 之前，字符或无符号字符用于表示一个字节，但那些类型使得像在处理字符。std::byte 却能指明意图，即内存中的单个字节
> // std::byte 的初始化需要使用单元素列表进行直接列表初始化
> std::byte b{ 42 };
> // 相当于是：00101010
> 
> std::byte buffer[1024];
> // 处理网络数据，读写字节流等
> 
> std::byte data[256];
> // 读取或写入字节数据到文件或设备
> 
> std::byte flags = std::byte{ 0x0F };
> // 00001111 in binary
> 
> std::byte b{ 42 };
> std::byte mask{ 0xF0 };
> std::byte result = b & mask;
> // 相当于 按位与 
> ```

##### 6.类型转换：

>   C++ 提供**三种**方式来显式地转换变量类型：
>
>   ```c++
>   float myFloat = 3.14f;
>   ```
>
>   1. 来自于 C，并且依然被广泛使用，但实际上，**不推荐**使用：
>
>       > ```c++
>       > int i_1 = (int)myFloat;
>       > ```
>
>   2. 初看上去肯自然，但**很少使用**：
>
>       > ```c++
>       > int i_2 = int(myFloat);
>       > ```
>
>   3. 最复杂，却最整洁，也是**推荐**的方法，静态类型转换：
>
>       >   ```c++
>       >   int i_3 = static_cast<int>(myFloat);
>       >   ```

**注意：**

> - 得到的整数是去掉小数部分的浮点部分。在某些环境中，可自动执行类型转换或强制执行类型转换，例如，short    可自动转换为    long,因为    long    代表精度更高的相同数据类型；
>
> ```c++
> long someLong = someShort;
> ```
>
> - 当自动类型转换变量的类型时，应当了解潜在的数据丢失情况，例如，float    类型转化为    int    类型会丢失掉一部分信息(数字的小数部分)。如果，将一个    float    类型赋给    int    类型而不显示执行类型转换，多数编译器会给出警告信息，如果确信左边的类型和右边的类型完全兼容，那么隐式地转换完全没有问题；

##### 7.**获取类型及大小：**

> ```c++
> std::cout << typeid(element).name();
> // 为 type_info 类型   
> 
> 或者
> 
> #include <typeindex>	// 必需 <typeindex>
> std::cout << std::type_index(typeid(element)).name();
> // 为与 type_info 类似的类，但提供了比 type_info 更好的比较和哈希功能
> 
> // 类型大小
> sizeof()	// 获取内存所占比特数
> size()		// 获取元素个数
> strlen()	// 仅获取 C-string 字符串有效个数，不包括 NUL
> ```

##### 8.**此外：**

> C++ 没有提供基本的字符串类型，但是作为标准库的一部分提供了字符串的标准实现；

****

#### **1.5	运算符**

> 在 C++ 中，运算符可以是一元的(操作一个表达式)、二元的(操作两个表达式)、三元的(操作三个表达式)。

##### 1.**一元运算符：**

> ```c++
> =
> // 赋值符号
> 
> ++
> --
> // 上述两自加加、自减减，仅对变量有效，对常量无效
> ```

##### 2.**二元运算符：**

> ```c++
> +
> -
> *
> /
> // 加、减、乘、除
> 
> %
> // mod，取余运算
> 
> +=
> -=
> *=
> /=
> %=
> // 简写
> 
> &
> |
> <<
> >>
> ^
> // 按位与、按位或、左移、右移、按位异或
> 
> &=
> |=
> <<=
> >>=
> ^=
> // 简写
> ```

##### 3.**三元运算符(条件运算符)：**

> C++ 中有一个接收三个参数的运算符，称为三元运算符。可将其作为“如果【某事发生了】，那么【执行某个操作】；否则，【执行其他操作】”的条件表达式的简写。
>
> ```c++
> condition ? expression_if_true : expression_if_false;
> ```
>
> 条件运算符的优点是几乎可以在任何环境中使用，而且是直接将结果用在代码中，而非执行代码块，这使得它是一个运算符，而非条件语句。

#### **1.6	类型**

> 在 C++ 中，可使用基本类型(int、bool 等)创建更复杂的自定义类型。一旦熟悉 C++ 程序，就会很少使用从 C 中沿袭来的技巧，因为类更强大。虽然如此，但是还是有必要学会以下两种创建类型的方法：

##### 1.**枚举类型：**

> 整数代表某个数字序列中的值，枚举类型允许用户定义自己的序列，这样声明的变量就只能使用这个序列中的值；
>
> - **const    表示法：**
>
>   > ```c++
>   > // 当希望获取某些不变量的值的时候，使用以下方式并不是很好
>   > // 以国际象棋为例，int 表示所有棋子
>   > const int PieceTypeKing = 0;
>   > const int PieceTypeQueen = 1;
>   > const int PieceTypeRook = 2;
>   > const int PieceTypePawn = 3;
>   > // etc.
>   > int myPiece = PieceTypeKing;
>   > // 这种表示虽然正确，但是存在一定风险，因为，棋子是一个 int，如果另一个程序增加棋子的值，就可以让 King 变成 Queen，这实质上没有意义。更糟糕的是，有人可能将某个棋子的值设置成为 -1，而这个值并没有对应的常量
>   > ```
>
> - **枚举表示法：**
>
>   > ```c++
>   > // 利用以下代码生成一个新类型 PieceType
>   > enum PieceType
>   > {
>   > 	PieceTypeKing,	// 不显式设定，默认为 0
>   > 	PieceTypeQueen,	// 不显式设定，默认为 1
>   > 	PieceTypeRook,	// 不显式设定，默认为 2
>   > 	PieceTypePawn	// 不显式设定，默认为 3
>   > };
>   > PieceType myPiece;
>   > myPiece = PieceTypeQueen;
>   > cout << myPiece;
>   > // 正常输出一个整型值
>   > 
>   > myPiece = 0;
>   > cout << myPiece;
>   > // 出现类型不匹配报错
>   > ```
>   >
>   > 由于实质上，enum    类型是一个整型值，但是由于它本身并不是    int    类型，所以能降低风险；
>   >
>   > 关于枚举类型语法：
>   >
>   > ```c++
>   > enum PieceType
>   > {
>   > 	PieceTypeKing = 1,	// 设定为 1
>   > 	PieceTypeQueen,		// 为前驱 +1，为 2
>   > 	PieceTypeRook = 10,	// 设定为 10
>   > 	PieceTypePawn		// 为前驱 +1，为 11
>   > };
>   > // 即，某位置的值若未被设定，则，其值为前驱值 +1
>   > ```

##### 2.**强类型枚举：**

> - 上面给出的枚举并不是强类型的，这意味着并非是类型安全的，它们总被解释为整形数据，因此可以比较完全不同的枚举类型的枚举值；
>
>   > 意思是说，虽然无法参与整型运算，但是，本质上，又被解释为整形变量，所以，可以参与到整型变量比较，这同样是一种不安全；
>
> - 强类型的 enum class 枚举解决了这些问题，例如，下面定义前述的 PieceType 枚举类型的安全版本：
>
>   > ```c++
>   > enum class PieceType
>   > {
>   > 	King = 1,
>   > 	Queen,
>   > 	Rook = 10,
>   > 	Pawn
>   > };
>   > ```
>
> - 对于 enum class，枚举值名不会超出封闭的作用域，这代表总要使用作用域解析操作符：
>
>   > ```c++
>   > PieceType piece = PieceType::King;
>   > ```
>   >
>   > 这也意味着，枚举值可以指定更简短的名称，因为有作用域的限定，每次都要作用域解析；
>   >
>   > 因此，避免了枚举值自动类型转换为整数：
>   >
>   > ```c++
>   > // 以下代码是不合法的
>   > if (PieceType == 2) {...}
>   > ```
>   >
>   > 此外，默认情况下，枚举值的基本类型是整型，但是可以采用以下方法加以改变：
>   >
>   > ```c++
>   > enum class PieceType : unsigned long
>   > {
>   > 	King = 1,
>   > 	Queen,
>   > 	Rook = 10,
>   > 	Pawn
>   > };
>   > ```
>
> - **注意：**
>
>   > 建议用类型安全的 enum class 枚举来代替类型不安全的 enum 枚举；

##### 3.**结构(struct)：**

> ```c++
> // employeestruct.h
> // 在头文件中声明结构体 Employee
> struct Employee
> {
> 	char firstInitial;
> 	char lastInitial;
> 	int employeeNumber;
> 	int salary;
> };
> ```
>
> ```c++
> // employee.cpp
> // 在头文件中实现结构体 Employee
> #include <iostream>
> #include "employeestruct.h"
> using namespace std;
> 
> int main()
> {
> 	Employee anEmployee;
> 	anEmployee.firstInitial = 'M';
> 	anEmployee.lastInitial = 'G';
> 	anEmployee.employeeNumber = 42;
> 	anEmployee.salary = 80000;
> 
> 	cout << "Employee: " << anEmployee.firstInitial << anEmployee.lastInitial << emdl;
> 	cout << "Number: " << anEmployee.employeeNumber << endl;
> 	cout << "Salary: $" << anEmployee.salary << endl;
> 
> 	return 0;
> }
> ```

****

#### **1.7	条件语句**

##### 1.**if / else 语句**

> ```c++
> if (condition)
> {
> 	...
> }
> else if (condition)
> {
> 	...
> }
> else
> {
> 	...
> }
> ```
>
> 0/false	  都被视为 	false；
>
> 非0/true	都被视为 	true；



##### 2.**if 语句的初始化器**

> ```c++
> if (<initializer>; <conditional_expression>) { <body> }
> ```
>
> **`<initializer>`** 中引入的任何变量只能在**`<conditional_expression>`** 和 **`<body>`** 中可用，此类变量在 if 语句外不可用，是匿名变量；
>
> 示例：
>
> > ```c++
> > if (Employee employee = GetEmployee(); employee.salary > 1000) { ... }
> > ```

##### 3.**switch 语句**

> switch 是另一种根据表达式值执行操作的语法。在 C++ 中，switch 语句的表达式必须是整型、能转化为整形的类型、枚举类型或强类型枚举，必须与一个常量比较，每个常量值代表一种“**情况*(case)***”，如果表达式与这种情况匹配，随后的代码将会被执行，直到遇到 **`break`** 语句为止。此外，还提供 **`default`** 情况，如果没有其他情况与表达式匹配，表达式值将与 **`default`** 情况匹配；
>
> 示例：
>
> ```c++
> switch (menuItem)
> {
> case OpenMenuItem:
> 	// Code to open a file
> 	break;
> case SaveMenuItem:
> 	// Code to save a file
> 	break;
> default:
> 	// Code to give an error message
> 	break;
> }
> 
> // 转化为相应的 if/else 语句
> if (menuItem == OpenMenuItem)
> {
> 	// Code to open a file
> }
> else if (menuItem == SaveMenuItem)
> {
> 	// Code to save a file
> }
> else
> {
> 	// Code to give an error message
> }
> ```
>
> 如果要基于多个表达式的多个值(而非对表达式进行一些检测)执行操作 ，通常使用 switch 语句。此时，switch 语句可以避免级联使用 if-else 语句。
>
> **注意：**
>
> > 一旦找到与 switch 条件匹配的 case 表达式，就执行其后的语句，知道遇到 break 语句为止。即使遇到另一个 case 表达式，执行也会继续，这种语法称为 fallthrough；
> >
> > ``` c++
> > switch (backgroundColor)
> > {
> > case Color::DarkBlue:
> > case Color::Black:
> >  	// Code to execute for both a dark blue or black background color
> >   	break;
> > case Color::Red:
> >   	// Code to excute for a red background color
> >   	break;
> > }
> > ```
> >
> > 如果是无意忘记 break 语句，fallthough 将成为 bug 的来源，因此如果在 switch 语句中，检测到 fallthough，编译器将会生成警告信息，除非像上例那样 case 为空。
> >
> > 此外，可以通过使用 **`[[fallthougn]]`** 特殊性，来告诉编辑器某个 fall though 是有意为之的；
> >
> > ```c++
> > switch (backgroundColor)
> > {
> > case Color::DarkBlue:
> >   	doSomethingForDarkBlue();
> >   	[[fallthough]];
> > case Color::Black:
> >   	// Code to execute for both a dark blue or black background color
> >   	doSomethingForBlackOrDarkBlue();
> >   	break;
> > case Color::Red:
> > case Color::Green:
> >   	// Code to excute for a red or green background color
> >   	break;
> > }
> > ```

##### 4.**switch 语句的初始化器**

> ```c++
> switch (<initializer>, <expression>) { <body> }
> ```
>
> 与 if 语句一致，**`<initializer>`** 中引入的任何变量只能在**`<conditional_expression>`** 和 **`<body>`** 中可用，它们在 switch 语句外不可用；

##### 5.**条件运算符**

> 略，详见三元运算符；

****

#### **1.8	逻辑比较运算符**

> **逻辑比较运算符(conditional operator)：**
>
> ```c++
> <
> >
> <=
> >=
> ==
> !=
> !
> &&
> ||
> ```
>
> - 在 C++ 中，对表达式求值时，会采用短路逻辑，即，一旦发现最终结果可以确定，就不再对后面的表达式求值；
>
> - 短路的做法对性能有好处：在使用逻辑短路时，可将代价更低的测试放在前面，以避免执行代价更高的测试。通过逻辑短路还可以避免在指针上下文中，避免指针无效时执行表达式的一部分的情况；

****

#### **1.9	函数**

> - 对于大型程序来说，将所有代码都放到 main() 函数中是无法管理的。为了使程序便于理解，需要将代码分解为简单明了的程序。
>
> - 在 C++ 中，为了让其他代码能够使用某个函数，首先，应当声明该函数。如果函数在某个特定的文件内部被使用，通常会在源文件中声明并定义这个函数。如果函数是供其他模块或文件使用的，通常在**头文件**中声明函数，并在源文件中定义函数。
>
> - 函数声明通常被称为**“函数原型”**或**“函数头”**，以强调这代表函数的访问方式，而不是具体代码，术语**“函数签名”**指将函数名和参数列表与形参列表组合在一起，但没有返回值。
>
> - 当没有与函数声明匹配的函数定义时，在编译过程中，会出现**链接阶段**错误；
>
> - 注意：与 C 不同，在 C++ 中没有形参的函数仅需要一个空的参数列表，不需要使用 void 指出此处没有形参；然而，如果没有返回值，那么仍需要 void 来指明这一点；
>
>   1. **函数返回类型的推断：**
>
>      > C++14 允许要求编辑器自动推出函数的返回值，要使用这个功能，需要把 **`auto`** 指定为返回类型；
>      >
>      > ```c++
>      > auto addnumber(int number1, int number2)
>      > {
>      > 	return number1 + number2;
>      > }
>      > ```
>      >
>      > 注意：函数中可有多个 **`return`** 语句，但是它们应解析为**相同的类型**。这种函数甚至可以包含**递归调用**(调用自身)，但函数中的第一个 **`return`** 语句必须时非递归调用的；
>
>   2. **当前函数的名称：**
>
>      > 每个函数都有一个预定义的局部变量 **`_ _func_ _`**，其中包括当前函数的名称。这个变量的一个用途是用于日志记录：
>      >
>      > ```c++
>      > int addNumbers(int number1, int number2)
>      > {
>      > 	std::cout << "Entering function " << __func__ << std::endl;
>      >  	// 左右两边各两个下划线，用于包括当前函数的名称
>      >  	// __func__ 为 const char[] 类型
>      >  	// __func__ 是编译器提供的宏，在编译时展开，而不是在运行时展开，这使得它在程序执行期间不会产生额外的运行开销，主要用于调试和日志记录，以便在运行时了解代码的执行流程，而不会影响实际的程序性能
>      > 	return number1 + number2;
>      > }
>      > ```

****

#### **1.10	C 风格的数组**

> 注意：在 C++ 中，尽量**避免**使用这种 C 风格的数组，而改用**标准库**功能，例如：**`std::array`** 和 **`std::vector`**；

##### 1.**一维数组：**

> 数组具有一系列值，所有值的**类型相同**，每个值都可以根据它在数组中的位置进行访问。在 C++ 中声明数组时，必须声明**数组大小**。数组大小不能用变量表示——必须用**常量**或**常量表示式*****(coonstexpr)*** 表示数组大小；
>
> ```
> int myArray[3];
> myArray[0] = 0;
> myArray[1] = 0;
> myArray[2] = 0;
> // Index 的起点始终是 0
> ```
>
> - **不使用循环的初始化机制：**
>
> ```c++
> int myArray[3] = { 0 };
> int myArray[3] = {};
> // 都起到将所有列表中元素置零的作用
> 
> int myArray[] = { 1, 2, 3, 4 };
> // 自动推导出列表长度，并初始化每个位置的值
> 
> int myArray[3] = { 2 };
> // 将数组第一个元素置为 2，其余置为 0
> 
> int myArray[3] = { 1, 2 };
> // 将数组第一个元素置为 1，将数组第二个元素置为 2，其余置为 0
> ```
>
> - **获取数组大小(元素个数)：**
>
>   > ```c++
>   > // 遇到数组长度等，都使用 size_t 的方式来描述大小！！！
>   > 
>   > #include <array>	// 必须 <array>
>   > unsigned int arraySize = std::size(myArray);
>   > // 使用 unsigned int 接收数组大小
>   > std::cout << std::size(myArray);
>   > 
>   > 或者：
>   > 
>   > unsigned int arraySize = sizeof(myArray) / sizeof(myArray[0]);
>   > ```

##### 2.**二维数组：**

> ```c++
> char ticTacToeBoard[3][3];
> ```

##### 3.**三维数组、更高维数组：**

> 难以描绘，极少使用；

****

#### **1.11	```std::array```**

> 在 C++ 中，有一种**大小固定**的特殊容器 **`std::array`**，这种容器在 **`<array>`** 头文件中定义。它详细用法在之后学习，但基本就是对 C 风格的数组进行**简单包装**：
>
> **用 `std::array` 代替 C 风格的数组优点：**
>
> > 1. 它总是知道**自身大小**；
> > 2. **不会自动转化为指针**，从而避免了某些类型的 bug；
> > 3. 具有**迭代器**，可以方便地遍历元素；
> >
> > **示例：**
> >
> > ```c++
> > std::array<int, 3> arr = { 9, 8, 7 }; 
> > std::cout << "Array size = " << arr.size() << std::endl;
> > std::cout << "2nd element = " << arr[1] << std::endl;
> > ```
> >
> > **注意：**
> >
> > > **C 风格和 std::array 的数组**都具有**固定的大小**，在编译过程中不会改变；
> > >
> > > 如果希望数组的大小是动态的，推荐使用 ```std::vector```，在 vector 中添加新元素时，vector 会自动增加其大小；

****

#### **1.12	```std::vector```**

> - 标准库提供了多个不同的**非固定大小容器**，可用于存储信息。**`std::vector`** 就是其中的一个示例。它在 **`<vector>`** 头文件中被声明，用一种更灵活更安全的机制取代 C 中的数组概念。用户不必担心内存的管理，因为 vector 将自动分配足够的内存来存放元素。vector 是动态的，意味着可以在运行时添加和删除元素,而且它的用法十分简单，示例：
>
> ```c++
> // Create a vector of integers
> std::vector<int> myVector = (11, 12);
> 
> // Add some more integers to the vector using push_back()
> myVector.push_back(33);
> myVector.push_back(44);
> 
> // Delete some more integer to the vector using pop_back()
> // 删除最后一个元素
> myVector.pop_back();
> 
> // 删除中间元素，后面元素顺位向前移动，使用 erase()
> myVector.erase(myVector.begin());	// 删除索引为 0 元素
> myVector.erase(myVector.begin() + 2) // 删除索引为 2 元素
> 
> // Access elements
> std::cout << "1st element: " << myVector[0] << endl;
> ```
>
> - vector 中尖括号用来指定模板函数，与之前的 **`std::array`** 一样，vector 时一个泛类容器，几乎可以容纳任何类型的对象；但是必须使用简括号指定要在 vector 中存放的对象类型；
>
> - 为向 vector 中添加元素，可以使用 push_back() 方法；
>
> - 为访问 vector 中各个元素，可使用类似于数组的语法，即，operator[]；

****

#### **1.13	结构化绑定**

> **结构化绑定*(structured budings)***，允许声明多个变量，这些变量使用数组、结构、**`std::pair`** 关键词或 **`std::tuple`** 中的元素来初始化。它允许你以一种简洁的方式从复合类型(例上面所提的**`std::pair`** 或  **`std::tuple`**)或结构体中提取成员，并将其绑定到命名变量上。结构化绑定的主要目的是提高代码的可读性和简洁性，特别是在处理复杂数据结构时；
>
> ```c++
> // 基本语法：
> auto [var1, var2, ...] = expression;
> ```
>
> 使用特点：
>
> > - 假定有以下数组：
> >
> > ```c++
> > std::array<int, 3> values = { 11, 22, 33 };
> > ```
> >
> > - 可声明三个变量 x、y、z，使用其后数组中的三个值进行初始化。注意，必须为结构化绑定使用 auto 关键字(例，不能用 int 替代 auto)：
> >
> > ```c++
> > auto [x, y, z] = values;
> > ```
> >
> > - 注意：使用结构化绑定声明的变量数量必须与右侧表达式中的值数量匹配；
> >
> > - 此外，如果所有非静态成员都是公有的，也可以将结构化绑定用于结构；
> >
> > - 使用结构化绑定优点，示例：
> >
> >   > 1. 简化**`std::pair`** 、  **`std::tuple`** 或结构体使用，无需显式地访问元素索引或成员变量;
> >   >
> >   >    > ```c++
> >   >    > std::tuple<int, double, std::string> myTuple = std::make_tuple(42, 3.14, "Hello");
> >   >    > auto [a, b, c] = myTuple;
> >   >    > ```
> >   >
> >   > 2. 提高代码可读性，直观显示内容；
> >   >
> >   >    > ```c++
> >   >    > struct Point
> >   >    > {
> >   >    > 	double mX;
> >   >    > 	double mY;
> >   >    > 	double mZ;
> >   >    > };
> >   >    > Point point;
> >   >    > point.mX = 1.0;
> >   >    > point.mY = 2.0;
> >   >    > point.mZ = 3.0;
> >   >    > auto [x, y, z] = point;
> >   >    > ```
> >   >
> >   > 3. 减少错误风险，减少手动索引或访问机构提而引起的错误；
> >   >
> >   >    > ```c++
> >   >    > std::pair<int, std::string> myPair = std::make_pair(42, "Hello");
> >   >    > auto [num, text] = myPair;
> >   >    > ```

****

#### **1.14	循环**

> 在 C++ 中，提供了 4 种循环结构：

##### 	1.**while 循环**

> ```c++
> while (condition_expr)
> {
> 	...
> }
> // 在循环中使用 break 关键字立即跳出循环并执行之后程序
> // 在循环中使用 continue 关键字可返回循环顶部并对 while 表达式重新求值
> // 这两种风格都不提倡使用，因为它们会使程序的执行产生无规则的跳转，应该慎用
> ```

##### 	2.**do/while 循环**

> ```c++
> do
> {
> 	...
> } while (condition_expr);
> // 使得程序至少执行一次
> ```

##### 	3.**for 循环**

> ```c++
> for (init_state; loop_conditon; iter_expr)
> {
> 	...
> }
> ```

##### 	4.**基于区间的 for 循环*(Range-Based for Loop)***

> 这种循环类似于 Python，允许方便地迭代容器中的元素。这种循环可用于 C 风格的数组、初始化列表等，也可用于具有返回迭代器的 begin() 和 end() 函数的类型，例如， **`std::array`** 、 **`std::vector`** 等其他所有标准库容器；
>
> 示例：
>
> ```c++
> std::array<int, 4> arr = { 1, 2, 3, 4 };
> for (int i : arr)
> {
> 	std::cout << i << std::endl;
> }
> ```

****

#### **1.15	初始化列表**

> 初始化列表在  **`initializer_list`**  头文件中定义；利用初始化列表，可以轻松地编写能接收**可变数量参数**的函数。  **`initializer_list`**  类是一个模板，要求在尖括号之间指定列表中的元素类型，这类似于指定 vector 中存储的对象类型；
>
> 示例：
>
> > ```c++
> > #include <initializer_list>
> > using namespace std;
> > 
> > // 定义可变数量参数累加函数
> > int makeSun(initializer_list<int> lst)
> > {
> > 	int total = 0;
> > 	for (int value : lst)
> > 	{
> > 		total += value;
> > 	}
> > 
> > 	return total;
> > }
> > 
> > int a = makeSun({ 1, 2, 3 });
> > int b = makeSun({ 10, 20, 30, 40, 50, 60 });
> > 
> > // 初始化列表是类型安全的，会定义列表中允许的类型。对于此处的 makeSun() 函数，初始化列表所有元素必须都是整数。
> > // 尝试使用 double 数值进行调用，将会导致编译器生成错误或警告
> > int c = makeSun({ 1, 2, 3.0 });
> > ```

****

#### **1.16	小结**

> 至此，C++ 程序设计的基本要点已经复习完成，这些是很简单的内容；

****

### **1.2    深入研究 C++**

****

#### **2.1	C++ 中的字符串**

> 在 C++ 中使用字符串有三种方法。

##### 1.**C 风格的字符串**

> 将字符看成字符数组；

##### 2.**C++ 风格的字符串**

> 将字符串封装到一种易于使用的 string 类型中，需要引入 **`<string>`** 头文件；
>
> ```c++
> // C++ 中 string 的用法与基本类型几乎相同
> // 与 I/O 流一样，string 类型位于 std 名称空间
> std::string myString = "Hello, World!";
> std::cout << "The value of myString is " << myString << std::endl;
> std::cout << "The second letter is " << myString[1] << std::endl;
> ```

##### 3.**非标准的普通类**

> 略，详见第二章；

****

#### **2.2	指针和动态内存**

> 动态内存允许所创建的程序具有在编译时大小可变的数据，大多数复杂程序都会以某种方式使用动态内存；

##### 1.**堆栈和堆**

> 在 C++ 的内存中，分为两部分：**堆栈** 和 **堆**。
>
> - **堆栈**
>
>   > **堆栈**就像一副扑克牌，当前顶部的牌代表程序当前的作用域，通常时当前正在执行的函数；当前函数中声明的所有变量将占用顶部**堆栈帧**(也就是最上面的那张牌)的内存。如果当前函数(将其称为 foo())调用了另一个函数 bar()，就会翻开一张新牌，这样 bar() 就会拥有自己的**堆栈帧**供其运行。任何从 foo() 传递给 bar() 的参数都会从 foo() **堆栈帧**复制到 bar() **堆栈帧**；
>   >
>   > **堆栈帧**很好，因为它为每个函数提供了独立的内存空间。如果在 foo() **堆栈帧** 中声明了一个变量，那么除非专门要求，否则调用 bar() 函数不会更改该变量。此外，foo() 函数执行完毕时，**堆栈帧** 就会消失，该函数声明的所有变量都不会再占用内存。堆栈上的分配内存的变量**不需要**程序员**释放内存(删除)**，这个过程是自动完成的；
>
> - **堆**
>
>   > **堆**是与当前函数与堆栈帧完全没有关系的内存区域。如果想在函数调用结束后仍保存其中声明的变量，可以将变量放到堆中。堆的结构并不复杂，可以将堆当作一个堆位。程序可在任何时候向堆中添加新位或修改堆中已有的位。**必须确保释放(删除)**在堆中分配的任何内存，这个过程不会自动完成，除非使用了智能指针；

##### 2.**使用指针**

> - **在数据类型后加 `*`** ，将使之变为其类型的指针，但声明时，如果未初始化那么它可能指向一个随机的位置，而这时，这个指针很可能使得程序崩溃；所以，**必须要在同时证明和初始化指针**，如果不希望立即分配地址，则可以将它们**初始化为空指针 nullptr**；
>
>   > ```c++
>   > int* myIntegerPointer = nullptr;
>   > ```
>
> - nullptr 是一个**特殊默认值**，可以在布尔表达式中被转化为 false;
>
> - 使用 **new 操作符 **分配内存：
>
>   > ```c++
>   > myIntegerPointer = new int;
>   > ```
>
> - **指针的解除引用**
>
>   > ```c++
>   > * myIntegerPointer = 8;
>   > // 这并不是将 myIntegerPointer 的值设定为 8，而是将 myIntegerPointer 指向的内存设为 int 类型的整型 8
>   > // 而如果真不是解除引用，而是调整 myIntegerPointer 为 8 则很有可能是一个随机无用的内存单元，最终导致程序崩溃
>   > ```
>   >
>   > 可将解除引用看成沿着指针箭头方向寻找堆中实际的值；
>   >
>   > **使用完 new 动态分配后的内存，需要使用 delete 操作符进行释放内存，为防止在释放指针指向的内存后再使用指针，建议把指针设置为 nullptr;**
>   >
>   > ```c++
>   > delete myIntegerPointer;
>   > myIntegerPointer = nullptr;
>   > ```
>   >
>   > **警告：**
>   >
>   > > **在解除引用前指针必须有效！对 NULL 或未初始化的指针解除引用会导致不可确定的行为**，程序可能崩溃，也可能继续运行，但可能会给出奇怪的结果；
>
> - 指针并被总是指向堆内存，可声明一个指向堆栈中变量甚至指向其他指针的指针。为让指针指向某个变量，**需要使用“取”址运算符 &**；
>
>   > ```c++
>   > int i = 8;
>   > int* myIntegerPointer = &i;
>   > ```
>
> - 在 C++ 中，使用特殊语法来处理指向结构的指针。从技术角度上说，如果指针指向某个结构体，可以先**用 * 对指针进行解除引用，然后使用普通的 . 语法来访问结构中的字段**，以一个名为 getEmployee() 的函数作为示例：
>
>   > ```c++
>   > Employee* anEmployee = getEmployee();
>   > // getEmployee() 是对 Employee 结构(类)的封装
>   > std::cout << (*anEmployee).salary << endl;
>   > ```
>
> - 除此以外，还可以**使用 -> 运算符同时对指针进行解引用并访问字段**：
>
>   > ```
>   > Employee* amEmployee = getEmployee();
>   > std::cout << anEmployee->salary << std::endl;
>   > ```
>
> - **注意：**
>
>   > 记住前面所提到的短路逻辑，示例：
>   >
>   > ```c++
>   > bool isValidSalary = (anEmployee && anEmployee->salary > 0);
>   > ```
>   >
>   > 还可以用以下详细的方式复写：
>   >
>   > ```
>   > bool isValidSalary = (anEmlpoyee != nullptr && anEmployee->salary > 0);
>   > ```
>   >
>   > 这样，**可以使得仅当 anEmployee 指针有效的时候，才可对其进行解除引用以获取薪水。如果它是一个空指针，则逻辑运算短路，不再解除引用 anEmployee 指针**；

##### 3.**动态分配的数组**

> 堆也可以用于动态分配数组。**使用 new[] 操作符给数组分配内存**；
>
> ![image-20240204093145571](https://s2.loli.net/2024/02/09/xEkmeJX9yhDoYid.png)
>
> 示例：
>
> > ```c++
> > int arraySize = 8;
> > int* myVariableSizeArray = new int[arraySize];
> > ```
> >
> > 指针变量仍在堆栈中，但动态创建的数组在堆中；
> >
> > 完成这个数组后，应该将其堆中删除，这样其他变量就可以使用这块内存，在 C++ 中，可使用 **`delete[]`** 操作符完成：
> >
> > ```c++
> > delete[] myVariableSizeArray;
> > myVariableSizeArray = nullptr;
> > ```
> >
> > **注意：**
> >
> > > 避免使用 C 中的 malloc() 和 free()，而使用 new 和 delete，或者使用 new[] 和 delete[];
> > >
> > > **`delete`** 后的方括号表明所删除的是一个数组；
>
> **注意：**
>
> > - 在 C++ 中，每次调用 **`new`** 时，都必须相应地调用 delete；
> >
> > - 在 C++ 中，每次调用 **`new []`** 时，必须相应地调用 **`delete []`**，以避免内存泄漏；
> >
> > - 如果未调用 **`delete`** 或 **`delete []`**，或者调用不匹配，会导致内存泄漏。之后会详细讨论内存泄漏；

##### 4.**空指针常量**

> 在 C++11 之前，常量 NULL 用于表示空指针。将 NULL 定义为常量 0，会导致一些问题，下面给出示例：
>
> ```c++
> void func(char* str)
> {
> 	std::cout << "char* version" << std::endl;
> }
> void func(int i)
> {
> 	std::cout << "int version" << std::endl;
> }
> 
> int main()
> {
> 	func(NULL);
> 
> 	return 0;
> }
> ```
>
> 在上述情况，由于使用的 NULL 指针等价于整数 0，所以调用的是 func 的整数版本，而非指针版本；
>
> 可引入真正的**空指针常量 nullptr** 来解决这个问题，给出代码：
>
> ```
> int main()
> {
> 	func(nullptr);
> 
> 	return 0;
> }
> ```

##### 5.**智能指针**

> 为避免常见的内存错误，应使用智能指针代替通常的 C 风格的 “裸” 指针，智能指针对象在**超出作用域**时(例如，在函数执行完毕后)，会**自动释放内存**，在 C++ 中，有两个最重要的智能指针；
>
> **智能指针有时被视为右值引用，一般通过 std::move() 进行右值引用化。**
>
> ```c++
> // 详见后面关于雇员记录系统设计的内容
> std::unique_ptr<Employee>& Database::addEmployee(const std::string& firstName,
>    	const std::string& lastName)
> {
>  	auto theEmployee = std::make_unique<Employee>(firstName, lastName);
>  	theEmployee->setEmployeeNumber(mNextEmployeeNumber++);
>  	theEmployee->hire();
>  	mEmployees.push_back(std::move(theEmployee));
> 
>  	return mEmployees[mEmployees.size() - 1];
> }
> 
> std::unique_ptr<Employee> Database::getEmployee(int employeeNumber)
> {
>  	for (auto& employee : mEmployees)
>  	{
>    		if (employee->getEmployeeNumber() == employeeNumber)
>    		{
>    			return std::move(employee);
>    		}
>  	}
>  	throw std::logic_error("No employee found.");
> }
> 
> std::unique_ptr<Employee> Database::getEmployee(const std::string& firstName,
>    	const std::string& lastName)
> {
>  	for (auto& employee : mEmployees)
>  	{
>    		if (employee->getFirstName() == firstName && employee->getLastName() == lastName)
>    		{
>    			return std::move(employee);
>    		}
>  	}
>  	throw std::logic_error("No employee found.");
> }
> ```
>
> 

###### 1.std::unique_ptr		

> - **`std::make_unique<elementType>()`**	
> - **数组，允许：	`std::make_unique<elementType[]>(listSize)`**
> - **`std::unique_ptr<elementType> elementName (new elementType);`**
> - **数组，允许：	`std::unique_ptr<elementType[]> elementName (new elementType[listSize]);`**
> - **`std::unique_ptr `** 类似于普通指针，但在它超出作用域或者被删除时，会自动释放内存或资源。**`std::unique_ptr`** 只属于它指向的对象。它的优点是：内存和资源始终被释放，即使执行返回语句或抛出异常(见稍后的讨论)。这极大地简化了代码，例如，如果有一个函数有多个返回语句，可以不必记着每个返回语句前释放资源。
>
> - 要创建 **`std::unique_ptr`**，应当使用 **`std::make_unique<>()`**，例如，不要编写以下代码：
>
> > ```c++
> > Employee* anEmployee = new Employee;
> > // ...
> > delete anEmployee;
> > ```
>
> - 而应当编写以下代码：
>
> > ```c++
> > auto anEmployee = std::make_enique<Employee>();
> > 
> > // 关于 () 内参数设定，示例：
> > class MyClass
> > {
> > public:
> >  	MyClass(int value1, double value2);
> >  	// Other members...
> > };
> > auto myObject = std::make_unique<MyClass>(42, 3.14);
> > ```
>
> - 注意，这样一来，将不再需要调用 delete，因为这将自动完成。本章后面的类型推断将详细讲解 auto 关键字(这里先不详细说明)。这里只需要了解，auto 关键字告诉编译器自动推断变量的类型，因此你不必手动指定完整类型；
>
> - std::unique_ptr 是一个通用的智能指针，他可以指向任意类型的内存，所以，它本质上是一个模板。模板需要尖括号来指定模板类型参数。在尖括号中必须指定 unique_ptr 要指向的内存类型。模板详见第12章、第22章，而智能指针在本书开头介绍，可见，事实上，它们使用起来很简单；
>
> - make_unique() 在 C++14 中被引入，如果用户编译器与 C++14 不兼容，可使用如下形式的 unique_ptr(注意，现在必须将 Employee 类型指定两次)：
>
>   > ```c++
>   > std::unique_ptr<Employee> anEmployee (new Employee);
>   > ```
>
> - 可以像普通指针那样使用 anEmployee 智能指针，例如：
>
>   > ```c++
>   > if (anEmployee)
>   > {
>   > 	std::cout << "Salary: " << anEmployee->salary << std::endl;
>   > }
>   > ```
>
> - 此外，**unique_ptr** 也可以储存 C 风格的数组，下例创建了一个包含 10 个 Employee 示例的数组，将其存储在 **unique_ptr** 中，并显示如何访问数组中的元素：
>
>   > ```c++
>   > auto employees = std::make_unique<Employee[]>(10);
>   > std::cout << "Salary: " << employees[0].salary << std::endl;
>   > 
>   > // 使用 C 风格的不兼容处理
>   > std::unique_ptr<Employee[]> employees(new Employee[10]);
>   > ```
>
>   - 辨析：
>
>     > 1. 上面的代码使用 **`anEmployee->salary`** 而非**`anEmployee.salary`**，是因为**`anEmployee`** 是一个指向 **`Employee`** 对象的 **`unique_ptr`**，而不是直接的对象，-> 的作用是解引用并访问成员，. 的作用是访问成员；
>     >
>     > 2. 下面的代码使用**` employees[0].salary`** 而非 **` employees[0]->salary`** ，因为，**`employees`** 是一个指向动态分配数组的 **`std::unique_ptr`** ，可见，[] 符能起到解引用的作用，. 的作用认识访问成员；

###### 	2.**std::shared_ptr**

>- **`std::make_shared<elementType>()`**		
>- **数组，不允许：	`std::make_shared<elementType[]>(listSize)`**
>- **`std::shared_ptr<elementType> elementName (new elementType);`**
>- **数组，仅允许：	`std::shared_ptr<elementType[]> elementName (new elementType[listSize]);`**
>- **`std::shared_ptr`** 允许数据的分布式“所有权”，每次指定 **`std::shared_ptr`** 时，都递增一个引用计数，指出数据又多出了一位“拥有者”。当它超出作用域时，就递减引用计数，当引用计数为 0 时，就表示数据不再拥有任何拥有者，于是释放指针引用的对象；
>
>- 要创建 **`std::shared_ptr`**，应当使用 **`std::make_shared<>()`**，它与**`std::make_unique<>()`**:
>
>> ```c++
>> auto anEmployee = std::make_unique<Employee>();
>> if (anEmployee)
>> {
>> 	std::cout << "Salary: " << anEmployee->salary << std::endl;
>> }
>> ```
>
>- 从 C++17 开始，也可以将数组存储在 **`std::shared_ptr`** 中，而旧版的 C++ 是不允许的。但注意，此时不能使用 C++17 中的 **`make_shared<>()`**，示例：
>
>> ```
>> std::shared_ptr<Employee[]> employees(new Employee[10]);
>> std::cout << "Salary: " << employees[0].salary << std::endl;
>> ```

​	第七章将详细阐述内存管理和智能指针，但由于 **std::unique_ptr** 和 **std::shared_ptr** 的基本用法十分简单，所以，在这里阐述；

###### 	3.**注意**

> - **普通的裸指针仅允许在不涉及所有权时使用，否则默认使用  `std::unique_ptr`；**
>
> - **如果有需要共享所有权，就使用  `std::shared_ptr`；**
>
> - **如果知道 `auto_ptr`，应当忘记它，因为 C++ 11/14 不赞成使用它，而 C++17 已经废弃它；**
>
> - **如果第二种表示法：`std::XXX_ptr<elementType> elementName (new elementType);`中构造函数抛出异常，那么就会出现内存泄漏**

****

#### **2.3	const 的多种用法**

> 可以使用 auto 来去除 const 函数性质

##### 1.**使用 const 定义常量**

> - 在 C 中，通常使用预处理器的 #define 机制来声明一个符号名称，其值在程序执行时不会改变；
>
> - 在 C++ 中，鼓励使用 const 代替 #define 定义常量，使用 const 定义常量就像定义变量一样，只是编译器保证代码不会改变这个值；
>
> - 示例：
>
>   > ```
>   > const int versionNumberMajor = 2;
>   > const int versionNumberMinor = 1;
>   > const std::string productName = "Super Hyper Net Modulator";
>   > ```

##### 2.**使用 const 保护参数**

> - 在 C++ 中，可将非 const 变量转换为 const 变量，这可以提供一定保护，防止其他代码修改变量。如果程序试图改变参数的值，编译不会完成；
>
> - 示例：
>
>   > ```c++
>   > void mysteryFunction(const std::string* someString)
>   > {
>   > 	*someString = "Test";
>   > 	// Will not complie
>   > }
>   > 
>   > int main()
>   > {
>   > 	std::string myString = "The string";
>   > 	mysteryFunction(&myString);
>   > 
>   > 	return 0;
>   > }
>   > ```

****

#### **2.4	引用**

>- C++ 允许使用给已有变量定义另一个名称：
>
> > ```c++
> > int x = 42;
> > int& xReference = x;
> > std::cout << xReference;
> > 
> > // 对比上下两者的不同
> > int* xPointer = &x;
> > std::cout << *xPointer;
> > ```
> >
> > 给类型附加 &，则指示相应的变量是引用。在幕后他是一个指向原始变量的指针；

##### **1.按引用传递**

> 区别于值传递(制作副本)，不会改变原始变量的值；
>
> 按引用传递参数是引用而非指针，在执行函数时，会改变原始变量的值；
>
> ```c++
> // 传值版本
> void addOne(int i)
> {
> 	i++;
> 	// Has no real effect because this is a copy of the original
> }
> 
> // 传引用版本
> void addOne(int& i)
> {
> 	i++;
> 	// Actually change the original variable
> }
> ```
>
> 注意：
>
> > 对于两个版本的 addOne() 函数：
> >
> > 当前者传入字面量时，是可行的；
> >
> > 当后者传入字面量时，会导致编译错误；
> >
> > ```
> > addOne(3);
> > // 这对后者来说需要改变 3 的值，显然是不可能的
> > // 此外，还可以通过右值引用来解决，这将在之后讨论
> > ```
>
> 此外，在 C++11 之前推荐使用这种非 const 引用，但 C++11 开始，再也不这么做了，因为存在了 move 语义(之后讨论)；

##### **2.按 const 引用传递**

> 由于制作副本，代价较大，所以，使用不改变值的引用传递，示例：
>
> ```c++
> void printString(const std::string& myString)
> {
> 	std::cout << myString << std::endl;
> }
> 
> int main()
> {
> 	std::string someString = "Hello World";
> 	printString(someString);
> 	printString("Hello World");	// Passing literals works
> 
> 	return 0;
> }
> ```

##### **3.注意**

> 如需要给函数传递对象，最好按 const 引用(而非值)传递，这样可以防止多余复制；
>
> 如果需要修改对象，则为其传递非 const 引用；

****

#### **2.5	异常 & <stdexcept>**

> - **C++是一种非常灵活的语言，但并不是非常安全**，编译器通编写改变随机内存地址或尝试除以 0  的代码(计算机无法处理无穷大的数值)。**异常就是试图增加一点安全性的语言特性；**
>
> - 异常是一种无法预料的情形，例如如果编写一个获取web页面的函数 ，就有几件事可能出错，包含页面的 Internet 主机可能被关闭，页面可能是空白的，或者连接可能会丢失。处理这种情况的一种方法是从函数返回特定的值，如 nullptr 或其他错误代码。异常提供了处理此类问题的更好方法；
>
> - 一场伴随着一些新的术语。当某段代码检测到异常时就会抛出一个异常，另一段代码会捕捉这个异常并执行恰当的操作。 下例给出一个名为 divideNumber() 的函数，如果调用者传递给分母的值为0，就会抛出一个异常。使用 **`std::invalid_arugment`** 时需要**` <stdexcept>`**:
>
>   > ```c++
>   > double divideNumbers(double numerator, double denominator)
>   > {
>   > 	if (denominator == 0)
>   >  	{
>   >    		throw std::invalid_argument("Denominator cannot be 0.");
>   >    		// 此处为抛出异常
>   >    		// 详细内容将在异常章节讲述
>   >  	}
>   >  	return numerator / denominator;
>   > }
>   > ```
>   >
>   > **当执行 throw 行时，程序会立即结束而且不会返回值。**如果调用者将函数调用放到 try / catch块中就可以辅助捕获异常并进行处理，示例：
>   >
>   > ``` c++
>   > try
>   > {
>   > 	std::cout << divideNumbers(2.5, 0.5) << std::endl;
>   > 	std::cout << divideNumbers(2.3, 0) << std::endl;
>   > 	std::cout << divideNumbers(4.5, 2.5) << std::endl;
>   > }
>   > catch (const std::invalid_argument& exception)
>   > {
>   > 	std::cout << "Expression caught: " << exception.what() << std::endl;
>   > }
>   > ```
>   >
>   > - **第一次调用 divideNumbers() 成功执行，结果会输出给用户；**
>   >
>   > - **第二次调用 divideNumbers() 会抛出一个异常，不会返回值，唯一的输出是捕获异常时输出的错误信息；**
>   >
>   > - **第三次调用 根本不会执行，因为第二次调用抛出了一个异常，导致程序跳转到 catch 块；**
>   >
>   >   > ```c++
>   >   > 5
>   >   > Expression caught : Denominator cannot be 0.
>   >   > ```
>
> - **C++ 的异常非常灵活，为了正确使用异常，需要理解抛出异常时堆栈变量的行为，必须正确捕获并处理必要的异常**。前面的示例中使用了内建的 **`std::invalid_argument `**类型，但最好根据所抛出的具体错误编写自己的异常类型。最后，C++ 编译器并不强制要求捕获可能发生的所有异常。如果代码从不捕获任何异常，但有异常抛出，程序自身会捕获异常并终止。第14章将进一步讨论异常的这些更复杂方面；

#### **2.6	类型推断**

> - **类型推断允许编译器自动推断出表达式的类型。类型推断有两个关键词 auto 和 decltype;**

##### 1.**关键字 auto**

> **多种完全不同的含义：**
>
> - 推断函数的返回类型如前所述结构化绑定，如前所述；
>
> - 推断表达式的类型，如前所述；
>
> - 推断非类型模板参数的类型，见第12章；
>
> - decltype(auto)，见第12章；
>
> - 其他函数语法，见第12章。
>
> - 通用 Lambda 表达式，见第18章；
>
>   > - auto 可用于告诉编译器在编译时自动推断变量的类型。下面的代码演示了在这种情况下关键字 auto 最简单的用法： 
>   >
>   >   > ```c++
>   >   > auto x =123;
>   >   > // x will be of type int 
>   >   > ```
>   >   >
>   >   > 在这个示例中输入 auto 和输入 int 的效果没有区别，但 auto 对于较复杂的类型会更有用。假定 getFoo() 函数有一个复杂的返回类型。如果希望把调用该函数的结果赋予一个变量,就可以输入该复杂类型，也可以简单的使用 auto 让编译器推断出该类型：
>   >   >
>   >   > ```c++
>   >   > auto result = getFoo();
>   >   > ```
>   >   >
>   >   > 这样，你可以方便地更改函数的返回类型，而不需要更新代码中调用该函数的所有位置；
>   >
>   > - 但使用 auto 去除了引用和 const 限定符号。假设有以下函数：
>   >
>   >   > ``` c++
>   >   > #include <string>
>   >   > 
>   >   > const std::string message = "Test";
>   >   > 
>   >   > const std::string& foo()
>   >   > {
>   >   > 	return message;
>   >   > }
>   >   > ```
>   >   >
>   >   > 可以调用 Foo()，把结果存储在一个变量中，将该变量的类型指定为auto，如下所示：
>   >   >
>   >   > ```c++
>   >   > auto f1 = foo();
>   >   > ```
>   >   >
>   >   > 因为 auto 去除了引用和 const 限定符，且 f1 是 string 类型，所以建立一个副本。如果希望 f1 是一个 const 引用，就可以明确将它建立为一个引用，并标记为 const 如下所示：
>   >   >
>   >   > ```c++
>   >   > const auto& f2 = foo();
>   >   > 
>   >   > // 补充
>   >   > std::cout << typeid(element).name();
>   >   > // 为 type_info 类型   
>   >   > 
>   >   > 或者
>   >   > 
>   >   > #include <typeindex>	// 必需 <typeindex>
>   >   > std::cout << std::type_index(typeid(element)).name();
>   >   > // 为与 type_info 类似的类，但提供了比 type_info 更好的比较和哈希功能
>   >   > ```
>   >
>   > - **注意**：
>   >
>   >   > **始终要记住，auto 去除了引用和 const 限定符，从而会创建副本！如果不需要副本，可使用 auto& 或 const auto&；** 

##### 2.**关键字 decltype**

> **关键词 decltype 把表达式作为实参，计算出该表达式的类型**，示例：
>
> ```c++
> int x = 123;
> decltype(x) y = 456;
> ```
>
> 在这个示例中，**编译器会推断出 y 的类型是 int，因为这是 x 的类型；**
>
> **auto 与 decltype 的区别在于，decltype 未除引用和 const 限定符。再来分析返回 const string引用的 foo() 函数。按照如下方式使用 decltype 定义 f2，导致 f2 的类型为 const string&，从而不生成副本：**
>
> ```c++
> decltype(foo()) f2 = foo();
> ```
>
> 刚开始不会觉得 decltype 有多大价值。但**在模板环境中，decltype 会变得十分强大**，详见第12 和第 22 章；

****

### **1.3    作为面向对象语言的 C++**

>   - 如果你是一位 C 程序员，可能会认为本章讲述的内容到目前为止只是传统 C 语言的补充最好顾名思义，C++语言在很多方面只是“更好的C”。这种观点忽略了一个重点：与 C 不同 C++ 是一种面向对象的语言；
>   - **面向对象程序设计 *(OPP)*** 是一种完全不同的、更趋自然的编码方式。如果习惯使用过程语言，如 C 或者 Pascal，不要担心。第五章的讲述将观念转换到面向对象范型所需的所有背景知识。如果你已经了解OPP的理论，下面的内容将帮助你加速了解 (或者回顾) 基本的 C++ 对象语法；

#### **3.1	定义类**

> - **类定义了对象的特征。在 C++ 中，类通常在头文件 (.h) 中声明，在对应的源文件 (.cpp) 中定义其并 非内联 方式和静态数据成员；**
>
> - 下面示例定义了一个基本的**机票类**，这个类可根据飞行的里程数以及顾客是不是“精英超级奖励计划”的成员计算票价。这个定义**首先声明一个类名**，在大括号内声明了类的数据成员(属性)以及方法(行为)。 每个数据成员以及方法都具有特定的访问级别：**public**、**protected** 或 **private**。这些标记可按任意顺序出现，也可重复使用。**public 成员可在类的外部访问，private 成员不能在类的外部访问，推荐把所有的数据成员都声明为 private,在需要时，可通过 public 读取器和设置器来访问它们。**  **这样，就很容易改变数据的表达方式，同时使 public 接口保持不变。**关于 protected 的用法，将在第 5 和 10 章中介绍“继承”时讲解。
>
>   > ```c++
>   > // AirlineTicket.h
>   > #pragma once
>   > #include <string>
>   > 
>   > class AirlineTicket
>   > {
>   > public:
>   >  	// 构造类
>   >  	AirlineTicket();
>   > 
>   >  	// 析构类
>   >  	~AirlineTicket();
>   > 
>   >  	double calculatePriceInDollars() const;
>   > 
>   >  	const std::string& getPassengerName() const;
>   >  	void setPassageName(const std::string& name);
>   > 
>   >  	int getNumberOfMiles() const;
>   >  	void setNumberOfMiles(const int miles);
>   > 
>   >  	bool hasEliteSuperRewardsStatus() const;
>   >  	void setHasEliteSuperRewardsStatus(const bool status);
>   > private:
>   >  	std::string mPassengerName;
>   >  	int mNumberOfMiles;
>   >  	bool mHasEliteSuperRewardsStatus;
>   > };
>   > 
>   > // 约定：在类的每个数据成员之前加上小写字母 m, 如 mPassengefName
>   > ```
>   >
>   > **注意：**
>   >
>   > > **为遵循 const 正确性原则，最好将不改变对象的任何数据成员的成员函数声明为 const。相对于非 const 成员函数“修改器”，这些成员函数也称为 “检测器”。**
>   >
>   > - **构造函数的初始化：**
>   >
>   > 1. **更推荐的**，使用**构造函数初始化器*****(constructor initializer)***
>   >
>   >    > ```c++
>   >    > // 构造函数
>   >    > // AirlineTicket.h
>   >    > // 推荐使用构造函数初始化器
>   >    > AirlineTicket::AirlineTicket()
>   >    >  	: mPassengerName("Unknown Passenger")
>   >    >  	, mNumberOfMiles(0)
>   >    >  	, mHasEliteSuperRewardsStatus(false)
>   >    > {
>   >    > }
>   >    > ```
>   >
>   > 2. **将初始化任务放在构造函数体内**
>   >
>   >    > ```c++
>   >    > // AirlineTicket.h
>   >    > AirlineTicket::AirlineTicket()
>   >    > {
>   >    > 	//Initialize data member
>   >    > 	mPassengerName = "Unknown Passsenger";
>   >    > 	mNumberOfMiles = 0;
>   >    > 	mHasEliteSuperRewardsStatus = false;
>   >    > }
>   >    > ```
>   >
>   > - 如果构造函数只是初始化数据成员，而不做其他事情，实际上就没必要使用构造函数，因为可在类定义中直接初始化数据成员。例如，不编写 AirlineTicket 构造函数，而是修改类定义中数据成员的定义，如下所示：  
>   >
>   >   > ```c++
>   >   > // AirlineTicket.h
>   >   > private:
>   >   > 	std::string nPassengerName = "Unknown Passenger";
>   >   > 	int mNumberOfMiles = 0;
>   >   > 	bool mHasEliteSuperRewardsStatus = false;
>   >   > ```
>   >   >
>   >   > 如果类还需要执行其他的一些初始化类型，如打开文件、分配内存等，则需要编写构造函数进行处理；
>   >
>   > - **析构函数**
>   >
>   >   > 如下所示，为 AirlineTicket 类的析构函数：
>   >   >
>   >   > ```c++
>   >   > AirlineTicket::~AirlineTicket()
>   >   > {
>   >   >  	// Nothing much to do in terms of cleanup
>   >   > }
>   >   > ```
>   >   >
>   >   > 这个析构函数什么都不做，因此可以从类中删除，这里之所以需要显示它，是为了更好了解析构函数的语法；如果需要执行一些清理，如关闭文件、释放内存等，则需要使用析构函数；
>   >
>   > - **AirlinTicket 的其他类方法**
>   >
>   >   > ```c++
>   >   > // AirlineTicket.cpp
>   >   > double AirlineTicket::calculatePriceInDollars() const
>   >   > {
>   >   >  	if (hasEliteSuperRewardsStatus())
>   >   >  	{
>   >   >    		// Elite Super Rewards customers fly for free
>   >   >    		return 0;
>   >   >  	}
>   >   >  	// The cost of the ticket is the number of mile times 0.1.
>   >   >  	// Real airlines probably have a more complicated formula!
>   >   >  	return getNumberOfMiles() * 0.1;
>   >   > }
>   >   > 
>   >   > const std::string& AirlineTicket::getPassengerName() const
>   >   > {
>   >   >  	return mPassengerName;
>   >   > }
>   >   > 
>   >   > void AirlineTicket::setPassengerName(const std::string& name)
>   >   > {
>   >   >  	mPassengerName = name;
>   >   > }
>   >   > 
>   >   > int AirlineTicket::getNumberOfMiles() const
>   >   > {
>   >   >  	return mNumberOfMiles;
>   >   > }
>   >   > 
>   >   > void AirlineTicket::setNumberOfMiles(const int miles)
>   >   > {
>   >   >  	mNumberOfMiles = miles;
>   >   > }
>   >   > 
>   >   > bool AirlineTicket::hasEliteSuperRewardsStatus() const
>   >   > {
>   >   >  	return mHasEliteSuperRewardsStatus;
>   >   > }
>   >   > 
>   >   > void AirlineTicket::setHasEliteSuperRewardsStatus(const bool status)
>   >   > {
>   >   >  	mHasEliteSuperRewardsStatus = status;
>   >   > }
>   >   > ```

#### **3.2	使用类**

> 下面示例程序给出了如何使用 AirlineTicket 类。这个示例创建的两个 AirlineTicket 对象分别给予堆栈和堆：
>
> ```c++
> // testAirlineTicket.cpp
> 
> // Stack-based(堆栈) AirlineTicket
> // 优点：
> //    1.简单直观，不需要动态内存管理。
> // 缺点：
> //    1.对象的生命周期受限于其所在的作用域，一旦超出作用域，对象将被销毁。
> AirlineTicket myTicket;
> myTicket.setPassengerName("Sherman T. Socketwrench");
> myTicket.setNumberOfMiles(700);
> double cost = myTicket.calculatePriceInDollars();
> std::cout << "This ticket will cost $" << cost << std::endl;
> /*--------------------------------------------------------------------------*/
> 
> // Heap-based(堆) AirlineTicket with smart pointer
> // 推荐，使用
> // 优点：
> //    1.动态分配的内存由 std::unique_ptr 管理，无需手动释放内存。
> //    2.可以更灵活地控制对象的生命周期
> // 缺点：
> //    1.相对于栈上创建，略微复杂
> auto myTicket2 = std::make_unique<AirlineTicket>();
> myTicket2->setPassengerName("Laudimore M. Hallidue");
> myTicket2->setNumberOfMiles(2000);
> myTicket2->setHasEliteSuperRewardsStatus(true);
> double cost2 = myTicket2->calculatePriceInDollars();
> std::cout << "This other ticket will cost $" << cost2 << std::endl;
> // No need to delete myTicket2, happens automatically
> /*--------------------------------------------------------------------------*/
> 
> // Heap-based AirlineTicket without smart pointer (not recommended)
> // 不推荐，也不要使用
> // 优点：
> //    1.可以手动控制对象的生命周期。
> // 缺点：
> //    1.容易出现内存泄漏或释放已删除的内存，因为没有智能指针进行内存管理。
> //    2.必须手动调用 delete 来释放内存，容易出现忘记释放或者释放多次的问题。
> AirlineTicket* myTicket3 = new AirlineTicket();
> // ... Use ticket 3
> delete myTicket3;
> ```

****

### **1.4    统一初始化**

##### **1.结构与类的初始化**

> ##### **在 C++之前，初始化类型并非总是统一的。例如，考虑下面的两个定义，其中一个作为结构，另一个作为类，示例：**
>
> ```c++
> struct CircleStruct
> {
> 	int x, y;
> 	double radius;
> };
> 
> class CircleClass
> {
> public:
> 	// 使用成员初始化列表可以提高性能
> 	CircleClass(int x, int y, double radius)
>    		: mX(x), mY(y), mRadius(radius)
>    	{
> 
>    	}
> 	/*
> 	CircleClass(int x = 1, int y = 1, double radius = 3)
> 		: mX(x), mY(y), mRadius(radius)
> 		{
> 		// 这样实现默认值填充
> 		}
> 		*/
> private:
> 	int mX, mY;
> 	double mRadius;
> };
> 
> // 复写 Circle 类，使之更符合现代 C++ 关于默认初始变量设置的通常做法
> 
> class CircleClass
> {
> public:
>  	Circle() = default;
> 	// 使用成员初始化列表可以提高性能
> 	CircleClass(int x, int y, double radius)
>    		: mX(x), mY(y), mRadius(radius)
>    	{
> 
>    	}
> 
> private:
> 	int mX = 1;
>  	int mY = 1;
> 	double mRadius = 3;
> };
> ```
>
> **在 C++11 之前，CircleStruct 类型变量和CircleClass 类型变量的初始化是不同的，对于结构版本，可使用 {…} 语法。然而，对于类版本，需要使用函数符号 (…) 调用构造函数。  ：**  
>
> > ```c++
> > CircleStruct myCirclel = { 10, 10, 2.5 };
> > CircleClass myCircle2(10, 10, 2.5);
> > ```
>
> **自 C++11 以后，允许一律使用 {... }语法初始化类型，如下所示：**  
>
> > ```c++
> > CircleStruct myCircle3 = {10, 10, 2.5};
> > CircleClass myCircle4 = {10, 10, 2.5};
> > ```
> >
> > **定义 myCircle4 时将自动调用 CircleClass 的构造函数。甚至等号也是可选的，因此下面的代码与前面的代码等价：**
> >
> > ```c++
> > CircleStruct myCircle5{10, 10, 2.5};
> > CircleClass myCircle6{10, 10, 2.5};
> > ```
>
> **统一初始化并不局限于结构和类**，**它可以用于初始化 C++ 中的任何内容**，示例：
>
> > ``` c++
> > // 均将变量初始化为 3
> > int a = 3;
> > int b(3);
> > int c = {3};
> > int d{3};
> > ```

##### 2.**默认统一初始化**：

> ```c++
> // 示例
> 
> // 对于基本整型
> char、int	->		0
> ptr			->		nullprt
> 
> // 为此只需要指定一系列空大括号
> int e{};	// Uniform initialization，e will be 0
> ```

##### 3.**阻止窄化 *(narrowing)* **

​	**一般情况下，C++ 隐式地执行窄化，但存在部分编译器报错，部分不报错的情况，为解决不统一问题**，示例：

> ```c++
> void func(int i)
> {/*...*/
> }
> 
> int main()
> {
> 	int x = 3.14;
> 	func(3.14);
> 	// 上面两种情况窄化，将 3.14 截取成为 3
> 	// 对于窄化，部分编译器报错，部分不报
> 	// 但是，使用 统一初始化 则都会生成编译错误
> }
> 
> // 替换为：
> 
> void func(int i)
> { /* ... */
> }
> 
> int main()
> {
> 	int x = { 3.14 }; 	// Error because narrowing
> 	func({ 3.14 }); 		// Error because narrowing
> }
> ```

##### **4.其他类型的统一初始化**

> **动态分配的数组的统一初始化：**
>
> > ```c++
> > int* pArray = new int[4]{0, 1, 2, 3};
> > ```
>
> **构造函数初始化器的统一初始化：**
>
> > ```c++
> > class Myclass
> > {
> > public:
> > 	Myclass(): mArray{ 0, 1, 2, 3 }
> > 	{
> > 
> > 	}
> > 
> > private:
> > 	int Array[4];
> > }
> > ```
>
> **此外，统一初始化还可以用于标准库容器，之后讨论；**

##### 5.两种统一初始化的初始化列表

> - **复制列表初始化：	T obj = {arg1, arg2, ...};**
>
> - **直接初始化：	    T obj {arg1, arg2, ...}**
>
>   > 在 C++17 后，与 **auto** 结合有以下结果：
>   >
>   > ```c++
>   > 
>   > ```
> 
>  > 注意：
>  >
>  > 1. **对于复制列表初始化，放在大括号中的初始化器的所有元素都必须使用相同的类型**。例如，以下代码无法编译： 
>  >
>  >    > ``` c++
>  >    > auto b = {11, 12.33};	// Compilation error
>  >    > ```
>  >
>  > 2. **区分结构化绑定；**
> 
> **在早期版本 (C++11/14) 中，复制初始化列表和直接列表初始化会推导出 std::initializer_list<>:**
> 
> > ```c++
> > // Copy list initialization
> > auto a = {11}; 		// initializer_list<int>
> > auto b = {11, 22}; 	// initializer_list<int>
> > 
> > // Direct list initialization
> > auto c {11}; 		// initial!zer_list<int>
> > auto d {11, 22}; 	// initializer_list<int>
> > ```

****

### **1.5    标准库**

> **C++ 具有标准库，其中包含许多有用的类，在代码中可方便地使用这些类。使用标准库中类的好处是不需要重新创建某些类，也不需要浪费时间去实现系统已经自动实现的内容。另一好处是标准库中的类己经过成千上万用户的严格测试和验证。标准库中类的性能也比较高，因此使用这些类比使用自己的类效率更高。**
>
> 标准库中可用的功能非常多。第 16~20 章将详细讲述标准库。**当开始使用 C++时，最好立刻了解标准库可以做什么。**如果你是一位 C 程序员，这一点尤其重要。作为 C 程序员，你使用 C++时可能会以 C 的方式解决问题。然而使用 C++ 的标准库类可以更方便、安全地解决问题。
>
> 本章前面己经介绍了标准库中的一些类，例如 **std::string、std::array、std::vector、std::unique_ptr** 和**std::shared_ptr** 第 16~20 章将介绍更多的类。

****

### **1.6    第一个有用的 C++ 程序**

****

#### **6.1	雇员记录系统**

> 管理公司雇员记录的程序应该灵活并具有有效的功能，这个程序包含的功能有：
>
> - 添加雇员
> - 解雇雇员
> - 雇员晋升
> - 查看所有雇员，包括过去和现在的雇员
> - 查看所有当前雇员
> - 查看所有之前雇员
>
> 程序的代码分为三部分：Employee 类封装了单个雇员的信息，Database 类管理公司的所有雇员，单独的用户界面提供程序的接口；

****

#### **6.2	Employee 类**

> Employee 类维护了某个雇员的的全部信息，该类的方法提供了查询以及修改信息的途径。Employee 类还知道如何在控制台显示自身。此外，还存在调整雇员薪水和就业状态的方法。

****

###### 	1.Employee.h

> **注意：使用以下约定：给常量加前缀 k(小写字母)。这源于德语单词 Konstant, 意思是“顾问”  ；**
>
> ```c++
> /*第一行包括 #pragma once，以防止文件被包含多次。
> 此外还包括 string 功能。*/
> #pragma once
> #include <string>
> // 不推荐，也不要将这个参量定义于头文件命名空间外，因为当引入到实现文件后，文件之间耦合性可能增加，可能引起错误
> // const int kDefaultStartingSalary = 30000;
> 
> /*代码还声明后面的代码(包括在大括号中)将位于Records名称空间。
> 为使用特定代码，整个程序都会用到 Rewards 名称空间；*/
> namespace Records
> {
>  	/*下面的常量代表新雇员的默认起薪，位于 Records 名称空间。
>  	Records 名称空间中的其他代码可以将这个常量作为 kDefhultStartingSalary 访问。
>  	在其他位置，必须通过 Records::kDefaultStartingSalary 来引用它。*/
>  	// 这里在命名空间内定义这个参量，使得 kDefaultStartingSalary 作用域限定于命名空间域，避免耦合
>  	const int kDefaultStartingSalary = 30000;
> 
>  	class Employee
>  	{
>    	public:
>    		Employee() = default;
>    		Employee(const std::string& firstName,
>    			const std::string& lastNmae);
>    		void promote(int raiseAmount = 1000);
>    		void demote(int demeritAmount = 1000);
>    		void hire();			// Hires or rehires the employee
>    		void fire();			// Dissmisses the employee
>    		void display() const;	 // Output employee info to console
> 
>    		// Getters and setters
>    		void setFirstName(const std::string& firstName);
>    		const std::string& getFirstName() const;
> 
>    		void setLastName(const std::string& lastName);
>    		const std::string& getLastName() const;
> 
>    		void setEmployeeNumber(int employeeNumber);
>    		int getEmployeeNumber() const;
> 
>    		void setSalary(int newSalary);
>    		int getSalary() const;
> 
>    		bool isHired() const;
> 
>    		/*最后将数据成员声明为 private, 这样其他部分的代码将无法直接修改它们。
>    		获取器和设置器提供了修改或查询这些值的唯一公有途径。
>    		数据成员也在这里(而非构造函数中)进行初始化。*/
>    	private:
>    		std::string mFirstName;
>    		std::string mLastName;
>    		int mEmployeeNumber = -1;		   // 雇员编号而非雇员数量
>    		int mSalary = kDefaultStartingSalary;	// 默认起始薪资
>    		bool mHired = false;			   // 受雇状态
>  	};
> }
> ```

###### **2.Employee.cpp**

​								**注意，整型参数的默认值不显示在源文件中；**

> ```c++
> #include <iostream>
> #include "Employee.h"
> 
> // using namespace std;
> // 课本上这样讲了，但是这事实上引入 std 名称空间是一种不好的实践，尤其是在头文件中
> // 下面给出更好的做法，引入所需要的标识符：
> using std::cout;
> using std::endl;
> 
> namespace Records
> {
>  	/*构造函数接收姓名，只设置相应的数据成员；*/
>  	Employee::Employee(const std::string& firstName,
>    		const std::string& lastName)
>    		: mFirstName(firstName), mLastName(lastName)
>  	{
> 
>  	}
> 
>  	/*promote() 和 demote() 方法只是用一些新值调用 setSalary() 方法。
>    	注意，整型参数的默认值不显示在源文件中；
> 		 它们只能出现在函数声明中，不能出现在函数定义中。*/
>  	void Employee::promote(int raiseAmount)
>  	{
>    		setSalary(getSalary() + raiseAmount);
>  	}
>  	void Employee::demote(int demoteAmount)
>  	{
>    		setSalary(getSalary() - demoteAmount);
>  	}
> 
>  	/*hire() 和 fire() 方法正确设置了 mHired 数据成员*/
>  	void Employee::hire()
>  	{
>    		mHired = true;
>  	}
>  	void Employee::fire()
>  	{
>    		mHired = false;
>  	}
> 
>  	/*display()方法使用控制台输出流显示当前雇员的信息。
>  	由于这段代码是 Employee 类的一部分，因此可直谈访问数据成员(如 mSalary), 而不需要使用 getSalaryo获取器。
>  	然而，使用获取器和设置器(当存在时)是一种好的风格，甚至在类的内部也是如此。*/
>  	void Employee::display() const
>  	{
>    		cout << "Employee: " << getLastName() << ", " << getFirstName() << endl;
>    		cout << "-------------------------" << endl;
>    		cout << (isHired() ? "Current Employee" : "Former Employee") << endl;
>    		cout << "Employee Number : " << getEmployeeNumber() << endl;
>    		cout << "Salary: $" << getSalary() << endl;
>    		cout << std::endl;
>  	}
> 
>  	/*许多获取器和设置器执行获取值以及设置值的任务。
>  	即使这些方法看起来微不足道，但是使用这些微不足道的获取器和设置器，仍然优于将数据成员设置为 public。
>  	可能想在 setSalary() 方法中执行边界检查，它们也能简化调试，因为可在其中设置断点，在检索或设置值时检查它们。
>  	另一个原因是决定修改类中存储数据的方式时，只需要修改这些获取器和设置器。*/
>  	// Getters and setters
>  	void Employee::setFirstName(const std::string& firstName)
>  	{
>    		mFirstName = firstName;
>  	}
>  	const std::string& getFirstName() const
>  	{
>    		return mFirstName;
>  	}
> 
>  	void Employee::setLastName(const std::string& lastName)
>  	{
>    		mLastName = lastName;
>  	}
>  	const std::string& getLastName() const
>  	{
>    		return mLastName;
>  	}
> 
>  	void Employee::setEmployeeNumber(int employeeNumber)
>  	{
>    		mEmployeeNumber = employeeNumber;
>  	}
>  	int Employee::getEmployeeNumber() const
>  	{
>    		return mEmployeeNumber;
>  	}
> 
>  	void Employee::setSalary(int newSalary)
>  	{
>    		mSalary = newSalary;
>  	}
>  	int Employee::getSalary() const
>  	{
>    		return mSalary;
>  	}
> 
>  	bool Employee::isHired() const
>  	{
>    		return mHired;
>  	}
> }
> ```

****

###### **3.EmployeeTest.cpp**

> ```c++
> #include <iostream>
> #include "Employee.h"
> using namespace std;
> using namespace Records;
> int main()
> {
> 	cout << "Testing the Employee class." << endl;
> 	Employee emp;
> 	emp.setFirstName("John");
> 	emp.setLastName("Doe");
> 	emp.setEmployeeNumber(71);
> 	emp.setSalary(50000);
> 	emp.promote();
> 	emp.promote(50);
> 	emp.hire();
> 	emp.display();
> 	return 0;
> }
> ```
>
> 以上为书中给出的测试文件书写方法，但下面给出我认为更好的方法：
>
> ```c++
> #include <iostream>
> #include "Employee.h"
> using std::cout;
> using std::endl;
> 
> int main()
> {
>  	using namespace Records; 					// 这里选择性地引入 Records 命名空间
> 	// 因为是对这个文件的测试所以引入了，但一般大型工程中不使用
>  	cout << "Testing the Employee class." << endl;
> 
>  	Employee emp;
>  	emp.setFirstName("John");
>  	emp.setLastName("Doe");
>  	emp.setEmployeeNumber(71);
>  	emp.setSalary(50000);
>  	emp.promote();
>  	emp.promote(50);
>  	emp.hire();
>  	emp.display();
> 
>  	return 0;
> }
> 
> // 乃至使用以下的方式：
> 
> #include <iostream>
> #include "Employee.h"
> using std::cout;
> using std::endl;
> 
> int main()
> {
>  	using namespace Records;
>  	cout << "Testing the Employee class." << endl;
> 
>  	auto emp = std::make_unique<Employee>();
>  	emp->setFirstName("John");
>  	emp->setLastName("Doe");
>  	emp->setEmployeeNumber(71);
>  	emp->setSalary(50000);
>  	emp->promote();
>  	emp->promote(50);
>  	emp->hire();
>  	emp->display();
> 
>  	return 0;
> }
> ```
>
> - 当确信 Employee 类可正常运行后，应删除这个文件，或将这个文件注释掉，这样就不会编译具有多个 main() 函数的代码;
> - 一种测试各个类的方法是使用单元测试，详见第 26 章中的讨论;

****

#### **6.3	Database 类**

> Database 类使用标准库中的 std::vector 类来存储 Employee 对象

****

##### **1.Database.h**

> ```c++
> /*由于数据库会自动给新雇员指定一个雇员号，因此定义一个常量作为编号的开始*/
> #pragma once
> #include <iostream>
> #include <vector>
> #include "Employee.h"
> 
> namespace Records
> {
>  	const int kFirstEmployeeNumber = 1000;
>  	/*数据库可根据提供的姓名方便地添加一个新雇员。为方便起见，这个方法返回一个新雇员的引用。
>  	外部代码也可通过调用 getEmployee() 方法来获得雇员的引用。
>  	为这个方法声明了两个版本，一个允许按雇员号进行检索，另一个要求提供雇员的姓名。*/
>  	class Database
>  	{
>  	public:
>    		std::shared_ptr<Employee>& addEmployee(const std::string& firstName,
>    			const std::string& lastName);
>    		std::shared_ptr<Employee>& getEmployee(int employeeNumber);
>    		std::shared_ptr<Employee>& getEmployee(const std::string& firstName,
>    			const std::string& lastName);
> 		/*由于数据库是所有雇员记录的中心存储库，因此具有输出所有雇员、当前在职雇员以及己离职雇员的方法。*/
>    		void displayAll() const;
>    		void displayCurrent() const;
>    		void displayFormer() const;
> 
>    		/*mEmployees 包含 Employee 对象。
>    		数据成员 mNextEmployeeNumber 跟踪新雇员的雇员号，使用 kFirstEmployeeNumber 常量进行初始化*/
>  	private:
>    		// std::vector<std::make_unique<Employee>()> mEmployee;
>    		// 上是最一开始写错的版本，下面给出正确版本
>    		std::vector<std::shared_ptr<Employee>> mEmployees;
>    		int mNextEmployeeNumber = kFirstEmployeeNumber;
>  	};
> }
> ```

****

##### **2.Database.cpp**

> ```c++
> /*addEmployeeo方法创建一个新的 Employee 对象，在其中填充信息并将其添加到 vector 中。
> 注意当使用了这个方法后，数据成员 mNextEmployeeNumber 的值会递增，因此下一个雇员将获得新编号*/
> 
> #include <iostream>
> #include <stdexcept>
> #include "Database.h"
> 
> using std::cout;
> using std::endl;
> 
> namespace Records
> {
>  	std::shared_ptr<Employee>& Database::addEmployee(const std::string& firstName,
>    		const std::string& lastName)
>  	{
>    		auto theEmployee = std::make_shared<Employee>(firstName, lastName);
>    		theEmployee->setEmployeeNumber(mNextEmployeeNumber++);
>    		theEmployee->hire();
>    		mEmployees.push_back(theEmployee);
> 
>    		return mEmployees[mEmployees.size() - 1];
>  	}
> 
>  	std::shared_ptr<Employee>& Database::getEmployee(int employeeNumber)
>  	{
>    		for (auto& employee : mEmployees)
>    		{
>    			if (employee->getEmployeeNumber() == employeeNumber)
>    			{
>    				return employee;
>    			}
>    		}
>    		throw std::logic_error("No employee found.");
>  	}
> 
>  	std::shared_ptr<Employee>& Database::getEmployee(const std::string& firstName,
>    		const std::string& lastName)
>  	{
>    		for (auto& employee : mEmployees)
>    		{
>    			if (employee->getFirstName() == firstName && employee->getLastName() == lastName)
>    			{
>    				return employee;
>    			}
>    		}
>    		throw std::logic_error("No employee found.");
>  	}
> 
>  	void Database::displayAll() const
>  	{
>    		for (const auto& employee : mEmployees)
>    		{
>    			employee->display();
>    		}
>  	}
> 
>  	void Database::displayCurrent() const
>  	{
>    		for (const auto& employee : mEmployees)
>    		{
>    			if (employee->isHired() == true)
>    			{
>    				employee->display();
>    			}
>    		}
>  	}
> 
>  	void Database::displayFormer() const
>  	{
>    		for (const auto& employee : mEmployees)
>    		{
>    			if (employee->isHired() == false)
>    			{
>    				employee->display();
>    			}
>    		}
>  	}
> }
> ```

##### **3.DatabaseTest.cpp**

> ```c++
> /*用于数据库基本功能的简单测试*/
> #include <iostream>
> #include "Database.h"
> 
> using std::cout;
> using std::endl;
> 
> int main()
> {
> 	Records::Database myDB;
> 	auto& emp1 = myDB.addEmployee("Greg", "Wallis");
> 	emp1->fire();
> 	auto& emp2 = myDB.addEmployee("Marc", "White");
> 	emp2->setSalary(100000);
> 	auto& emp3 = myDB.addEmployee("John", "Doe");
> 	emp3->setSalary(10000);
> 	emp3->promote();
> 	cout << "all employees: " << endl << endl;
> 	myDB.displayAll();
> 	cout << endl << "current employees: " << endl << endl;
> 	myDB.displayCurrent();
> 	cout << endl << "former employees: " << endl << endl;
> 	myDB.displayFormer();
> 
> 	return 0;
> }
> ```

****

##### **4.std::unique_ptr**版本

> ```c++
> // Database.h
> #pragma once
> #include <iostream>
> #include <vector>
> #include "Employee.h"
> 
> namespace Records
> {
>  	const int kFirstEmployeeNumber = 1000;
>  	class Database
>  	{
>  	public:
>    		std::unique_ptr<Employee>& addEmployee(const std::string& firstName,
>    			const std::string& lastName);
>    		std::unique_ptr<Employee> getEmployee(int employeeNumber);
>    		std::unique_ptr<Employee> getEmployee(const std::string& firstName,
>    			const std::string& lastName);
> 
>    		void displayAll() const;
>    		void displayCurrent() const;
>    		void displayFormer() const;
> 
>  	private:
>    		std::vector<std::unique_ptr<Employee>> mEmployees;
>    		int mNextEmployeeNumber = kFirstEmployeeNumber;
>  	};
> }
> 
> /*-----------------------------------------------------------------------------------*/
> // Database.cpp
> #include <iostream>
> #include <stdexcept>
> #include "Database.h"
> 
> using std::cout;
> using std::endl;
> 
> namespace Records
> {
>  	std::unique_ptr<Employee>& Database::addEmployee(const std::string& firstName,
>    		const std::string& lastName)
>  	{
>    		auto theEmployee = std::make_unique<Employee>(firstName, lastName);
>    		theEmployee->setEmployeeNumber(mNextEmployeeNumber++);
>    		theEmployee->hire();
>    		mEmployees.push_back(std::move(theEmployee));
> 
>    		return mEmployees[mEmployees.size() - 1];
>  	}
> 
>  	std::unique_ptr<Employee> Database::getEmployee(int employeeNumber)
>  	{
>    		for (auto& employee : mEmployees)
>    		{
>    			if (employee->getEmployeeNumber() == employeeNumber)
>    			{
>    				return std::move(employee);
>    			}
>    		}
>    		throw std::logic_error("No employee found.");
>  	}
> 
>  	std::unique_ptr<Employee> Database::getEmployee(const std::string& firstName,
>    		const std::string& lastName)
>  	{
>    		for (auto& employee : mEmployees)
>    		{
>    			if (employee->getFirstName() == firstName && employee->getLastName() == lastName)
>    			{
>    				return std::move(employee);
>    			}
>    		}
>    		throw std::logic_error("No employee found.");
>  	}
> 
>  	void Database::displayAll() const
>  	{
>    		for (const auto& employee : mEmployees)
>    		{
>    			employee->display();
>    		}
>  	}
> 
>  	void Database::displayCurrent() const
>  	{
>    		for (const auto& employee : mEmployees)
>    		{
>    			if (employee->isHired() == true)
>    			{
>    				employee->display();
>    			}
>    		}
>  	}
> 
>  	void Database::displayFormer() const
>  	{
>    		for (const auto& employee : mEmployees)
>    		{
>    			if (employee->isHired() == false)
>    			{
>    				employee->display();
>    			}
>    		}
>  	}
> }
> 
> /*-----------------------------------------------------------------------------------*/
> // DatabaseTest.cpp
> #include <iostream>
> #include "Database.h"
> 
> using std::cout;
> using std::endl;
> 
> int main()
> {
> 	Records::Database myDB;
> 	auto& emp1 = myDB.addEmployee("Greg", "Wallis");
> 	emp1->fire();
> 	auto& emp2 = myDB.addEmployee("Marc", "White");
> 	emp2->setSalary(100000);
> 	auto& emp3 = myDB.addEmployee("John", "Doe");
> 	emp3->setSalary(10000);
> 	emp3->promote();
> 	cout << "all employees: " << endl << endl;
> 	myDB.displayAll();
> 	cout << endl << "current employees: " << endl << endl;
> 	myDB.displayCurrent();
> 	cout << endl << "former employees: " << endl << endl;
> 	myDB.displayFormer();
> 
> 	return 0;
> }
> ```

****

#### **6.4	用户界面*(UI)***

> **程序的最后一部分是基于菜单的用户界面，可让用户方便地使用雇员数据库。main()函数是一个显示菜单的循环，执行被选中的操作，然后重新开始循环。对于大多数的操作都定义了独立的函数。对于显示雇员之类的简单操作，则将实际代码放在对应的情况(case)中。**

> ```c++
> // Display.cpp
> #include <iostream>
> #include <stdexcept>
> #include <exception>
> #include <limits>           // 用于清除输入缓冲区
> #include "Database.h"
> 
> using std::cout;
> using std::endl;
> using std::string;
> 
> int displayMenu();
> void doHire(Records::Database& db);
> void doFire(Records::Database& db);
> void doPromote(Records::Database& db);
> void doDemote(Records::Database& db);
> 
> int main()
> {
>  	Records::Database employeeDB;
>  	bool done = false;
>  	while (!done)
>  	{
>    		int selection = displayMenu();
>    		switch (selection)
>    		{
>    		case 0:
>    			done = true;
>    			break;
>    		case 1:
>    			doHire(employeeDB);
>    			break;
>    		case 2:
>    			doFire(employeeDB);
>    			break;
>    		case 3:
>    			doPromote(employeeDB);
>    			break;
>    		case 4:
>    			employeeDB.displayAll();
>    			break;
>    		case 5:
>    			employeeDB.displayCurrent();
>    			break;
>    		case 6:
>    			employeeDB.displayFormer();
>    			break;
>    		default:
>    			std::cerr << "Unknown command." << endl;
>    			break;
>    		}
>  	}
> 
>  	return 0;
> }
> 
> /* displayMenu() 函数输出菜单获取用户输入。
> 在此假定用户能够“正确地输入”，当需要一个数字时就输入一个数字，这一点很重要。
> 在阅读了第 13 章有关 I / O 的内容后，你就会知道如何防止输入错误信息*/
> int displayMenu()
> {
>  	int selection;
>  	cout << endl;
>  	cout << "Employee Database" << endl;
>  	cout << "-----------------" << endl;
>  	cout << "1) Hire a new employee" << endl;
>  	cout << "2) Fire an employee" << endl;
>  	cout << "3) Promote an employee" << endl;
>  	cout << "4) List all employees" << endl;
>  	cout << "5) List all current employee" << endl;
>  	cout << "6) List all former employee" << endl;
>  	cout << "0) Quit" << endl;
>  	cout << "--->   ";
> 
>  	// 循环，直到得到有效的输入
>  	while (true)
>  	{
>    		// 尝试读取用户输入
>    		try
>    		{
>    			std::cin >> selection;
> 
>    			// 检查输入流的状态
>    			if (std::cin.fail())
>    			{
>    				throw std::invalid_argument("Invalid input. Please enter a number.");
>    			}
> 
>    			// 如果程序能够执行到这里，说明输入是有效的
>    			break;
>    		}
>    		catch (const std::invalid_argument& exception)
>    		{
>    			std::cerr << "Error: " << exception.what() << endl;
> 
>    			// 清除错误状态
>    			std::cin.clear();
> 
>    			// 忽略缓冲区中的无效字符，直到遇到换行符
>    			std::cin.ignore(std::numeric_limits<std::streamsize>::max(), '\n');
>    		}
>  	}
> 
>  	return selection;
> }
> 
> /* doHire() 函数获取用户输入的新雇员的姓名，并通知数据库添加这个雇员*/
> void doHire(Records::Database& db)
> {
>  	string firstName;
>  	string lastName;
> 
>  	cout << "First name? input: ";
>  	std::cin >> firstName;
> 
>  	cout << "Last name? input: ";
>  	std::cin >> lastName;
> 
>  	db.addEmployee(firstName, lastName);
> }
> 
> /* doFire() 、doPromote() 以及 doDemote() 函数都要求数据库根据雇员号找到雇员，然后使用 Employee 对象的 public 方法进行修改*/
> void doFire(Records::Database& db)
> {
>  	int employeeNumber;
> 
>  	cout << "Employee number? input: ";
>  	std::cin >> employeeNumber;
> 
>  	// 将 try 遇到的问题抛出，并继续执行程序
>  	try
>  	{
>    		std::unique_ptr<Records::Employee> emp = db.getEmployee(employeeNumber);
>    		emp->fire();
>    		cout << "Employee " << employeeNumber << " terminated." << endl;
>  	}
>  	catch (const std::logic_error& exception)
>  	{
>    		std::cerr << "Unable to terminate employee: " << exception.what() << endl;
>  	}
> }
> 
> void doPromote(Records::Database& db)
> {
>  	int employeeNumber;
>  	int raiseAmount;
> 
>  	cout << "Employee number? input: ";
>  	std::cin >> employeeNumber;
> 
>  	cout << "How much of a raise? input: ";
>  	std::cin >> raiseAmount;
> 
>  	try
>  	{
>    		std::unique_ptr<Records::Employee> emp = db.getEmployee(employeeNumber);
>    		emp->promote(raiseAmount);
>  	}
>  	catch (const std::logic_error& exception)
>  	{
>    		std::cerr << "Unable to promote employee: " << exception.what() << endl;
>  	}
> }
> 
> void doDemote(Records::Database& db)
> {
>  	int employeeNumber;
>  	int demeritAmount;
> 
>  	cout << "Employee number? input: ";
>  	std::cin >> employeeNumber;
> 
>  	cout << "How much of a demerit? input: ";
>  	std::cin >> demeritAmount;
> 
>  	try
>  	{
>    		std::unique_ptr<Records::Employee> emp = db.getEmployee(employeeNumber);
>    		emp->demote(demeritAmount);
>  	}
>  	catch (const std::logic_error& exception)
>  	{
>    		std::cerr << "Unable to promote employee: " << exception.what() << endl;
>  	}
> }
> ```

****

#### **6.5	评估程序**

> 前面的程序涵盖了许多主题，从最简单的到较复杂的都有。可采用多种方法扩展这个程序。例如，用户界面(UI)没有公开 Database 或 Employee 类的全前功能。可修改 UL 以包含这些特性。还可修改 Database 类，以从 mEmployees 中删除被解雇的雇员。
>
> 如果不理解程序的某些部分，参考前面的内容以回顾这些主题。如果仍不甚明了，最好的学习方法是编写代码并查看结果。例如，如果不确定如何使用条件运算符，可编写一个简单的 main()函数进行测试。  

> ```c++
> // Employee.h
> #pragma once
> #include <string>
> 
> namespace Records
> {
>  	const int kDefaultStartingSalary = 30000;
> 
>  	class Employee
>  	{
>  	public:
>    		Employee() = default;
>    		Employee(const std::string& firstName,
>    			const std::string& lastNmae);
>    		void promote(int raiseAmount = 1000);
>    		void demote(int demeritAmount = 1000);
>    		void hire();			// Hires or rehires the employee
>    		void fire();			// Dissmisses the employee
>    		void display() const;	 // Output employee info to console
> 
>    		// Getters and setters
>    		void setFirstName(const std::string& firstName);
>    		const std::string& getFirstName() const;
> 
>    		void setLastName(const std::string& lastName);
>    		const std::string& getLastName() const;
> 
>    		void setEmployeeNumber(int employeeNumber);
>    		int getEmployeeNumber() const;
> 
>    		void setSalary(int newSalary);
>    		int getSalary() const;
> 
>    		bool isHired() const;
> 
>  	private:
>    		std::string mFirstName;
>    		std::string mLastName;
>    		int mEmployeeNumber = -1;		   // 雇员编号而非雇员数量
>    		int mSalary = kDefaultStartingSalary;	// 默认起始薪资
>    		bool mHired = false;			   // 受雇状态
>  	};
> }
> 
> /*--------------------------------------------分隔符---------------------------------------------------*/
> 
> // Employee.cpp
> #include <iostream>
> #include "Employee.h"
> 
> using std::cout;
> using std::endl;
> 
> namespace Records
> {
>  	Employee::Employee(const std::string& firstName,
>    		const std::string& lastName)
>    		: mFirstName(firstName), mLastName(lastName)
>  	{
> 
>  	}
> 
>  	void Employee::promote(int raiseAmount)
>  	{
>    		setSalary(getSalary() + raiseAmount);
>  	}
>  	void Employee::demote(int demeritAmount)
>  	{
>    		setSalary(getSalary() - demeritAmount);
>  	}
> 
>  	void Employee::hire()
>  	{
>    		mHired = true;
>  	}
>  	void Employee::fire()
>  	{
>    		mHired = false;
>  	}
> 
>  	void Employee::display() const
>  	{
>    		cout << "Employee: " << getLastName() << ", " << getFirstName() << endl;
>    		cout << "-------------------------" << endl;
>    		cout << (isHired() ? "Current Employee" : "Former Employee") << endl;
>    		cout << "Employee Number : " << getEmployeeNumber() << endl;
>    		cout << "Salary: $" << getSalary() << endl;
>    		cout << std::endl;
>  	}
> 
>  	void Employee::setFirstName(const std::string& firstName)
>  	{
>    		mFirstName = firstName;
>  	}
>  	const std::string& Employee::getFirstName() const
>  	{
>    		return mFirstName;
>  	}
> 
>  	void Employee::setLastName(const std::string& lastName)
>  	{
>    		mLastName = lastName;
>  	}
>  	const std::string& Employee::getLastName() const
>  	{
>    		return mLastName;
>  	}
> 
>  	void Employee::setEmployeeNumber(int employeeNumber)
>  	{
>    		mEmployeeNumber = employeeNumber;
>  	}
>  	int Employee::getEmployeeNumber() const
>  	{
>    		return mEmployeeNumber;
>  	}
> 
>  	void Employee::setSalary(int newSalary)
>  	{
>    		mSalary = newSalary;
>  	}
>  	int Employee::getSalary() const
>  	{
>    		return mSalary;
>  	}
> 
>  	bool Employee::isHired() const
>  	{
>    		return mHired;
>  	}
> }
> 
> /*--------------------------------------------分隔符---------------------------------------------------*/
> 
> // Database.h
> #pragma once
> #include <iostream>
> #include <vector>
> #include "Employee.h"
> 
> namespace Records
> {
>  	const int kFirstEmployeeNumber = 1000;
>  	class Database
>  	{
>  	public:
>    		std::unique_ptr<Employee>& addEmployee(const std::string& firstName,
>    			const std::string& lastName);
>    		std::unique_ptr<Employee>& getEmployee(int employeeNumber);
>    		std::unique_ptr<Employee>& getEmployee(const std::string& firstName,
>    			const std::string& lastName);
>    		void removeEmployee(const std::string& firstName,
>    			const std::string& lastName);
>    		void removeEmployee(int employeeNumber);
>    		void removeUnhiredEmployee();
>    		void displayAll() const;
>    		void displayCurrent() const;
>    		void displayFormer() const;
> 
>  	private:
>    		std::vector<std::unique_ptr<Employee>> mEmployees;
>    		int mNextEmployeeNumber = kFirstEmployeeNumber;
>  	};
> }
> 
> /*--------------------------------------------分隔符---------------------------------------------------*/
> 
> // Database.cpp
> #include <iostream>
> #include <stdexcept>
> #include "Database.h"
> 
> using std::cout;
> using std::endl;
> 
> namespace Records
> {
>  	std::unique_ptr<Employee>& Database::addEmployee(const std::string& firstName,
>    		const std::string& lastName)
>  	{
>    		auto theEmployee = std::make_unique<Employee>(firstName, lastName);
>    		theEmployee->setEmployeeNumber(mNextEmployeeNumber++);
>    		theEmployee->hire();
>    		mEmployees.push_back(std::move(theEmployee));
> 
>    		return mEmployees[mEmployees.size() - 1];
>  	}
> 
>  	std::unique_ptr<Employee>& Database::getEmployee(int employeeNumber)
>  	{
>    		if (!mEmployees.empty())
>    		{
>    			for (auto& employee : mEmployees)
>    			{
>    				if (employee->getEmployeeNumber() == employeeNumber)
>    				{
>    					return employee;
>    				}
>    			}
>    			throw std::logic_error("No employee found.");
>    		}
>    		else
>    		{
>    			std::cerr << "No employees in the database." << std::endl;
>    			// 返回一个空指针或者抛出异常，具体取决于你的需求
>    			throw std::logic_error("No employees in the database.");
>    		}
>  	}
> 
> 
> 	std::unique_ptr<Employee>& Database::getEmployee(const std::string& firstName,
>  		const std::string& lastName)
> 	{
>  		if (!mEmployees.empty())
>  		{
>    			for (auto& employee : mEmployees)
>    			{
>    				if (employee->getFirstName() == firstName && employee->getLastName() == lastName)
>    				{
>    					return employee;
>    				}
>    			}
>    			throw std::logic_error("No employee found.");
>  		}
>  		else
>  		{
>    			std::cerr << "No employees in the database." << std::endl;
>    			// 返回一个空指针或者抛出异常，具体取决于你的需求
>    			throw std::logic_error("No employees in the database.");
>  		}
> 	}
> 
> 
>  	//void Database::removeEmployee(const std::string& firstName,
>  	//                              const std::string& lastName) 
>  	//{
>  	//    auto item = std::find(mEmployees.begin(), mEmployees.end(), getEmployee(firstName, lastName));
>  	//    if (item != mEmployees.end() || ((*mEmployees.end())->getFirstName() == firstName && (*mEmployees.end())->getFirstName() == lastName))
>  	//    {
>  	//        mEmployees.erase(item);
>  	//    }
>  	//    else 
>  	//    {
>  	//        std::cerr << "Element not found." << std::endl;
>  	//    }
>  	//}
> 
>  	//void Database::removeEmployee(int employeeNumber)
>  	//{
>  	//    auto item = std::find(mEmployees.begin(), mEmployees.end(), getEmployee(employeeNumber));
>  	//        if ((*item)->getEmployeeNumber() == employeeNumber)
>  	//        {
>  	//            mEmployees.erase(item);
>  	//        }
>  	//}
> 
>  	void Database::removeEmployee(const std::string& firstName, const std::string& lastName)
>  	{
>    		if (!mEmployees.empty())
>    		{
>    			mEmployees.erase(
>    				std::remove_if(mEmployees.begin(), mEmployees.end(), [&firstName, &lastName](const auto& employee) {
>    					return employee->getFirstName() == firstName && employee->getLastName() == lastName;
>    					}),
>    				mEmployees.end()
>    			);
>    			cout << "This employee is removed" << endl;
>    		}
>    		else
>    		{
>    			std::cerr << "No employees in the database." << std::endl;
>    		}
>  	}
> 
>  	void Database::removeEmployee(int employeeNumber)
>  	{
>    		if (!mEmployees.empty())
>    		{
>    			mEmployees.erase(
>    				std::remove_if(mEmployees.begin(), mEmployees.end(), [employeeNumber](const auto& employee) {
>    					return employee->getEmployeeNumber() == employeeNumber;
>    					}),
>    				mEmployees.end()
>    			);
>    			cout << "This employee is removed" << endl;
>    		}
>    		else
>    		{
>    			std::cerr << "No employees in the database." << std::endl;
>    		}
>  	}
> 
> 
>  	void Database::removeUnhiredEmployee()
>  	{
>    		if (!mEmployees.empty())
>    		{
>    			mEmployees.erase
>    			(std::remove_if(mEmployees.begin(),
>    				mEmployees.end(),
>    				[](const auto& employee)
>    				{
>    					return !employee->isHired(); // 移除所有未雇佣的员工
>    				}),
>    				mEmployees.end()
>    			);
>    			cout << "Fired employees are removed" << endl;
>    		}
>    		else
>    		{
>    			std::cerr << "No employees in the database." << std::endl;
>    		}
>  	}
> 
>  	void Database::displayAll() const
>  	{
>    		if (!mEmployees.empty())
>    		{
>    			for (const auto& employee : mEmployees)
>    			{
>    				employee->display();
>    			}
>    			cout << "All employees are printed above" << endl;
>    		}
>    		else
>    		{
>    			std::cerr << "No employees in the database." << std::endl;
>    		}
>  	}
> 
>  	void Database::displayCurrent() const
>  	{
>    		if (!mEmployees.empty())
>    		{
>    			for (const auto& employee : mEmployees)
>    			{
>    				if (employee->isHired() == true)
>    				{
>    					employee->display();
>    				}
>    			}
>    			cout << "Current employees are printed above" << endl;
>    		}
>    		else
>    		{
>    			std::cerr << "No employees in the database." << std::endl;
>    		}
>  	}
> 
>  	void Database::displayFormer() const
>  	{
>    		if (!mEmployees.empty())
>    		{
>    			for (const auto& employee : mEmployees)
>    			{
>    				if (employee->isHired() == false)
>    				{
>    					employee->display();
>    				}
>    			}
>    			cout << "Former employees are printed above" << endl;
>    		}
>    		else
>    		{
>    			std::cerr << "No employees in the database." << std::endl;
>    		}
>  	}
> }
> 
> /*--------------------------------------------分隔符---------------------------------------------------*/
> 
> // UItest.cpp
> #include <iostream>
> #include <stdexcept>
> #include <exception>
> #include <limits>           // 用于清除输入缓冲区
> #include "Database.h"
> 
> using std::cout;
> using std::endl;
> using std::string;
> 
> int displayMenu();
> void doHire(Records::Database& db);
> void doFire(Records::Database& db);
> void doPromote(Records::Database& db);
> void doDemote(Records::Database& db);
> 
> int main()
> {
>  	Records::Database employeeDB;
>  	bool done = false;
>  	while (!done)
>  	{
>    		int selection = displayMenu();
>    		switch (selection)
>    		{
>    		case 0:
>    			done = true;
>    			break;
>    		case 1:
>    			doHire(employeeDB);
>    			break;
>    		case 2:
>    			doFire(employeeDB);
>    			break;
>    		case 3:
>    			doPromote(employeeDB);
>    			break;
>    		case 4:
>    			employeeDB.displayAll();
>    			break;
>    		case 5:
>    			employeeDB.displayCurrent();
>    			break;
>    		case 6:
>    			employeeDB.displayFormer();
>    			break;
>    		case 7:
>    			employeeDB.removeUnhiredEmployee();
>    			break;
>    		default:
>    			std::cerr << "Unknown command." << endl;
>    			break;
>    		}
>  	}
> 
>  	return 0;
> }
> 
> /* displayMenu() 函数输出菜单获取用户输入。
> 在此假定用户能够“正确地输入”，当需要一个数字时就输入一个数字，这一点很重要。
> 在阅读了第 13 章有关 I / O 的内容后，你就会知道如何防止输入错误信息*/
> int displayMenu()
> {
>  	int selection;
>  	cout << endl;
>  	cout << "Employee Database" << endl;
>  	cout << "-----------------" << endl;
>  	cout << "1) Hire a new employee" << endl;
>  	cout << "2) Fire an employee" << endl;
>  	cout << "3) Promote an employee" << endl;
>  	cout << "4) List all employees" << endl;
>  	cout << "5) List all current employee" << endl;
>  	cout << "6) List all former employee" << endl;
>  	cout << "7) Remove all unhired employees" << endl;
>  	cout << "0) Quit" << endl;
>  	cout << "--->   ";
> 
>  	// 循环，直到得到有效的输入
>  	while (true)
>  	{
>    		// 尝试读取用户输入
>    		try
>    		{
>    			std::cin >> selection;
> 
>    			// 检查输入流的状态
>    			if (std::cin.fail())
>    			{
>    				throw std::invalid_argument("Invalid input. Please enter a number.");
>    			}
> 
>    			// 如果程序能够执行到这里，说明输入是有效的
>    			break;
>    		}
>    		catch (const std::invalid_argument& exception)
>    		{
>    			std::cerr << "Error: " << exception.what() << endl;
> 
>    			// 清除错误状态
>    			std::cin.clear();
> 
>    			// 忽略缓冲区中的无效字符，直到遇到换行符
>    			std::cin.ignore(std::numeric_limits<std::streamsize>::max(), '\n');
>    		}
>  	}
> 
>  	return selection;
> }
> 
> /* doHire() 函数获取用户输入的新雇员的姓名，并通知数据库添加这个雇员*/
> void doHire(Records::Database& db)
> {
>  	string firstName;
>  	string lastName;
> 
>  	cout << "First name? input: ";
>  	std::cin >> firstName;
> 
>  	cout << "Last name? input: ";
>  	std::cin >> lastName;
> 
>  	db.addEmployee(firstName, lastName);
> }
> 
> /* doFire() 、doPromote() 以及 doDemote() 函数都要求数据库根据雇员号找到雇员，然后使用 Employee 对象的 public 方法进行修改*/
> void doFire(Records::Database& db)
> {
>  	int employeeNumber;
> 
>  	cout << "Employee number? input: ";
>  	std::cin >> employeeNumber;
> 
>  	// 将 try 遇到的问题抛出，并继续执行程序
>  	try
>  	{
>    		if (db.getEmployee(employeeNumber)->isHired())
>    		{
>    			db.getEmployee(employeeNumber)->fire();
>    			cout << "Employee " << employeeNumber << "is terminated." << endl;
>    		}
>    		else
>    		{
>    			std::cerr << "Employee has been fired" << endl;
>    		}
>  	}
>  	catch (const std::logic_error& exception)
>  	{
>    		std::cerr << "Unable to terminate employee: " << exception.what() << endl;
>  	}
> }
> 
> void doPromote(Records::Database& db)
> {
>  	int employeeNumber;
>  	int raiseAmount;
> 
>  	cout << "Employee number? input: ";
>  	std::cin >> employeeNumber;
> 
>  	cout << "How much of a raise? input: ";
>  	std::cin >> raiseAmount;
> 
>  	try
>  	{
>    		if (db.getEmployee(employeeNumber)->isHired())
>    		{
>    			db.getEmployee(employeeNumber)->promote(raiseAmount);
>    			cout << "Employee " << employeeNumber << "is promoted." << endl;
>    		}
>    		else
>    		{
>    			std::cerr << "Employee has been fired" << endl;
>    		}
>  	}
>  	catch (const std::logic_error& exception)
>  	{
>    		std::cerr << "Unable to promote employee: " << exception.what() << endl;
>  	}
> }
> 
> void doDemote(Records::Database& db)
> {
>  	int employeeNumber;
>  	int demeritAmount;
> 
>  	cout << "Employee number? input: ";
>  	std::cin >> employeeNumber;
> 
>  	cout << "How much of a demerit? input: ";
>  	std::cin >> demeritAmount;
> 
>  	try
>  	{
>    		db.getEmployee(employeeNumber)->demote(demeritAmount);
>  	}
>  	catch (const std::logic_error& exception)
>  	{
>    		std::cerr << "Unable to promote employee: " << exception.what() << endl;
>  	}
> }
> ```

****

### **1.7    本章小结**

****

>   - 我上面所书写的代码并不是按照书上的格式写的，我使用了智能指针来实现这个工程，而不是书上说书写的 Employee 类的 vector，而是它的智能指针的 vector； 
>   - 现在已经了解了 C++的基本知识，为成为专业 C++程序员做好了准备。在开始深入学习本书后面的 C++ 语言知识时，可查阅本章以回顾需要复习的内容。为了回顾那些被遗忘的概念，只需要查看本章的一些示例代码。
>   - 编写的每个程序都必须以这样或那样的方式使用字符串。为此，下一章将深入讲解如何在 C++ 中处理字符串。

****

## 第2章 —— 使用 string 和 string_view

****

> 你编写的每个应用程序都会使用某种类型的字符串。**使用老式 C 语言时，没有太多选择，只能使用普通的以 null 结尾的字符数组来表示字符串。遗憾的是，这种表示方式会导致很多问题，例如会导致安全攻击的缓冲区溢出。C++标准库包含了一个安全易用的 substring 类，这个类没有这些缺点；**  

### 2.1动态字符串

> 在将字符串当成一等对象支持的语言中，字符串有很多有吸引人的特性，例如可扩展至任意大小，或能提取或替换子字符串。**在其他语言(如 C 语言)中，字符串几乎就像后加入的功能；C 语言中并没有真正好用的 string数据类型，只有固定的字节数组。“字符串库”只不过是一组非常原始的函数，甚至没有边界检查的功能。C++ 提供了 string 类型作为一等数据类型。**

****

#### 1.1C风格的字符串

> - 在 C 语言中，字符串表示为字符的数组。**字符串中的最后一个字符是 null 字符('\0')**, 这样，操作字符串的代码就知道字符串在哪里**结束**。
>
> - **官方将这个 null 字符定义为 NUL, 这个拼写中只有一个 L, 而不是两个 L，NUL和 NULL 指针是两回事。**
>
> - 尽管 C++提供了更好的字符串抽象，但**理解 C 语言中使用的字符串技术非常重要**，因为在 C++程序设计中仍可能使用这些技术。**最常见的一种情况是 C++程序调用某个第三方库中(作为操作系统接口的一部分)用 C 语言编写的接口。**  
>
> - 目前，程序员最容易犯的错误是忘记为 **'\0'** 分配空间。例如，**字符串 "hello" 看上去有 5 个字符长，但是实际在内存上需要 6 个字符空间才能保存这个字符串的值**。
>
> - **C++ 中包含一些来自 C 语言的字符串操作函数，它们被定义在 <cstring> 中定义，通常，这些函数不直接操作内存分配。**例如，strcpy() 函数有两个字符串参数。这个函数将第二个字符串赋值到第一个字符串，而不考虑第二个字符串能否恰当地填入第一个字符串中。**下面代码试图在 strcpy() 函数之上构建一个包装器，这个包装器能够分配正确数量的内存并返回结果，而不是接受一个已经分配好的字符串。这个函数通过 strlen() 函数获取字符串的长度。**调用者则负责释放 copyString() 分配的空间：
>
>   > ```c++
>   > char* copyString(cnost char* str)
>   > {
>   > 	char* result = new char[strlen(str)];	// BUG !!! OFF BY ONE !
>   >  	strcpy(result, str);
>   >  	return result;
>   > }
>   > ```
>
> - **cpoyString() 函数的代码这样写是不正确的。**strlen() 函数返回字符串长度，而不是保存这个字符串所需的内存量。对于字符串 "hello"，strlen() 返回的是 5，而不是 6。**为字符串分配内存的正确方式是在实际字符所需空间 +1。一开始看到到处都要加 1 可能会感到有点奇怪，但这是其工作方式，所以在使用 C 风格的字符串时要注意记住这一点。**正确的实现代码如下：
>
>   > ```c++
>   > char* copyString(cnost char* str)
>   > {
>   > 	char* result = new char[strlen(str) + 1];
>   >  	strcpy(result, str);
>   >  	return result;
>   > }
>   > ```
>
> - **要记住 strlen() 只返回字符串中实际字符数目的一种方式是：考虑如果为一个由几个其他字符串构成的字符串分配空间，应该怎么做。**例如，如果函数接收 3 个字符串参数，并返回一个由这 3 个字符串串联而成的字符串，那么这个返回的字符串应该有多大？**为精确分配足够空间，空间的大小应该是 3 个字符串的长度相加，然后加上 1 留给尾部的 '\0' 字符。**如果 strlen() 的字符串长度包含 strcpy() 和 strcat() 函数执行这个操作。strcat()中的 cat 表示串联：
>
>   > ```c++
>   > char* appendStrings(const char* str1, const char* str2, cosnt char* str3)
>   > {
>   > 	char* result = new str[strlen(str1) + strlen(str2) + strlen(str3) + 1];
>   >  	strcopy(result, str1);
>   >  	strcat(result, str2);
>   >  	strcat(reslut, str3);
>   > 
>   >  	return result;
>   > }
>   > ```
>
> - C 和 C++中的 sizeof() 操作符可用于获得给定数据类型或变量的大小。例如，sizeof(char)返回 1, 因为字符的大小是 1 字节。**但在 C 风格的字符串中，sizeof() 和 strlen() 是不同的，绝对不要通过 sizeof() 获得字符串的大小。它根据 C 风格的字符串的存储方式来返回不同大小。如果 C 风格的字符串存储为 char[]，则 sizeof() 返回字符串使用的实际内存，包括’\0’字符。**例如：
>
>   > **存储为 char[] 下的 C 风格字符串：**
>   >
>   > ```c++
>   > char text1[] = "abcdef";
>   > size_t s1 = sizeof(text1);		// is 7
>   > size_t s2 = strlen(text1);		// is 6
>   > size_t s0 = sizeof(&text1);		// is situation as sizeof(text2) below
>   > 
>   > // 这里返回的是这个数组的长度
>   > 
>   > /*
>   > 优点：
>   > 	占用的内存大小是在编译时确定的，sizeof() 可以直接获取数组的大小。
>   > 	适用于需要修改字符串内容的场景，因为数组是可修改的。
>   > 缺点：
>   > 	占用的内存空间较大，因为数组的大小包括了字符串内容和额外的 null 终止符。
>   > 	不适用于常量字符串，因为数组的内容可修改
>   > */
>   > ```
>   >
>   > **存储为 char* 下的 C 风格字符串：**
>   >
>   > ```c++
>   > const char* text2 = "abcdef";
>   > size_t s3 = sizeof(text2);		// is platform-dependent
>   > size_t s4 = strlen(text2);		// is 6
>   > 
>   > // 在 32 位模式下编译时，s3 的值为 4；
>   > // 在 64 位模式下编译时，s4 的值位 8；
>   > // 原因是因为这返回的是 指针 const char* 的大小
>   > 
>   > std::cout << (text1 == text2) << "    " << (std::strcmp(text2, text1) == 0) << std::endl;	// 返回 0
>   > 
>   > // 这说明这完全不一样的两种东西
>   > 
>   > /*
>   > 优点：
>   > 	占用的内存大小是在编译时确定，sizeof() 得到的是指针大小，不受字符串内容影响。
>   > 	适用于常量字符串，因为字符串内容是不可修改的。
>   > 	占用的内存空间相对较小，因为只有指针的大小。
>   > 缺点：
>   > 	不适用于需要修改字符串内容的场景，因为字符串是常量。
>   > */
>   > 
>   > char* ptr = new char[7];
>   > strcpy_s(ptr, 7, "abcdef");
>   > ```
>
> - **警告：**
>
>   > **在 Microsoft Visual Studio 中使用 C 风格的字符串函数时，编译器可能会给出安全相关的警告甚至错误，说明这些函数已经被废弃了**。**使用其他 C 标准库函数可以避免这些警告**，例如 **strcpy_s()**和 **strcat_s()**, 这些函数是**“安全 C 库”(ISO/IEC TR24731)标准**的一部分。然而，**最好的解决方案是切换到 C++的 string 类，本章后面的"C++ std::string 类” 小节会讨论这个类**；

****

#### 1.2字符串字面量*(string literal)*

****

##### 1.**字面量池和不同类型定义方式**

> - **注意，C++ 程序中编写的字符串要用引号包围。**例如，下面的代码输出字符串 "hello"，这段代码中包含这个字符串本身，而不是一个包含这个字符串的变量：
>
> > ```c++
> > std::cout << "hello" << std::endl;
> > ```
>
> - **与字符串字面量关联的真正内存位于内存的只读部分。通过这种方式，编辑器可重用等价字面量的引用，从而优化内存的使用。**也就是说，即使一个程序使用了 500 次 "hello" 字符串字面量，编译器也只在内存中创建一个 "hello" 实例。**这种技术被称为字面量池 *(literal pooling)***；
> - 字符串字面量可赋值给变量，但因为字符串字面量位于内存的只读部分，且使用了字面量池，所以这样做会产生风险——也就是说，**字符串的字面量类型为 “n 个 const char 的数组”**，但是显然为了兼容较老的不支持 const 的代码，**大部分编译器不会强制程序将字符串字面量赋值给 const char* 类型的变量**。但是，如果试图修改字符串，一般情况下，这种行为是没有定义的，会使得程序崩溃；但也可能能够使得程序继续执行，却又一些很莫名其妙的副作用；可能不加通告地忽略修改行为；可能修改行为是有效的，这完全取决于编译器。
> - **下面的行为是未定义的：**
>
> > ```c++
> > char* ptr = "hello"; 	// Assign the string literal to a variable.
> > ptr[1] = 'a'; 			// Undefined behavior!
> > ```
>
> - **但是，更好的代码习惯是更好的：**
>
> > ```c++
> > const char* ptr = "hello"; 	// Assign the string literal to a variable.
> > ptr[1] = 'a'; 				// Error! Attempts to write to read-only memory
> > ```
>
> - **此外，使用 array 方式存储能够实现修改，也就是说，这时的 C 风格字符串并不在字面量池中，而是可以进行修改的：**
>
> > ```c++
> > char arr[] = "hello"; // Compiler takes care of creating appropriate sized
> > // character array arr.
> > arr[1] = 'a'; 		  // The contents can be modified.
> > ```

##### 2.**原始字符串字面量** *(raw string literal)*

> - **原始字符串字面量是可横跨多行代码的字符串字面量，不需要转义嵌入的双引号**，像 **'\t'** 和 **'\n'** 这种转义序列不按照转义序列的方式处理，**而是按照普通文本的方式处理**。转义字符在第 1 章讨论过了。如果像下面这样编写普通的字符串字面量，那么会收到一个编译器错误，因为字符串包含了未转义的双引号：
>
> > ```c++
> > const char* str = "Hello "World"!";	// Error!
> > ```
>
> - **对于普通字符串，必须转义双引号，如下所示：**
>
> > ```c++
> > const char* str = "Hello \"World\"!";
> > ```
>
> - **对于原始字符串字面量，就不需要转义双引号了:**
>
> > ```c++
> > // 格式：
> > // R"(......)"
> > const char* str = R"(Hello "World"!)";
> > ```
>
> - **换行转义：**
>
> > ```c++
> > const char* str = "Line 1\nLine 2";
> > ```
>
> - **原始字符串字面量换行，直接 Enter 换行，与之前效果一样：**
>
> > ```
> > const char* str = R"(Line 1
> > Line2)";
> > ```
>
> - **注意：**
>
>   > 原始字符串字面量会忽略掉转义序列，但是与转义序列情况中 **"a"b"c"** 一样的错误情况，原始字符串也会出现如下情况，不能在字符串中嵌入 **)”**，示例：
>   >
>   > ```c++
>   > const char* str = R"(Embedded )" characters)"; 	// Error!
>   > ```
>   >
>   > **如果要需要嵌入 )"，则需要使用拓展的原始字符串字面量语法：**
>   >
>   > ```c++
>   > // 格式：
>   > // R"d-char-sequence(r-char-sequence)d-char-sequence)-"
>   > // d-char-sequence 可以是任意小于 16 个字符的分割符序列
>   > // r-char-sequence 是要输出的字符串代码
>   > const char* str = R"-(Embedded)" character)-";
>   > const char* str = R"10101(Embedded)" character)10101";
>   > // Embedded)" character 两行代码输出一致
>   > ```
>   >
>   > **在操作数据库查询字符串、正则表达式和文件路径时，原始字符串字面量可以令程序编写更加方便。第 19 章将会讨论正则表达式；**

****

#### 1.3C++ std::string 类

> **C++ 提供了一个得到极大改善的字符串概念，并作为标准库的一部分提供这个字符串的实现。在 C++ 中，std::string 是一个类，(实际上是 basic_string 模板类的一个实例)，这个类支持 <cstring> 中提供的许多功能，还能自动管理内存分配。string 类在 std 名称空间的 <string> 头文件中定义，之前已经多次使用到 string 类了，下面深入学习：**

##### 1.C 风格的字符串有什么问题

>**为理解 C++ string 类的必要性，需要考虑 C 风格字符串的优势和劣势：**
>
>**优势：**
>
>- 很简单，**底层使用基本的字符类型和数组结构**，注意，C 数组是与指针强相关的，可以将 C 数组看作为指向数组第一个元素的指针，它具有数组指针的双重性；
>- 轻量级，如果使用得当只会占用所需内存；
>- 很低级，因此可以按操作原始内存方式轻松操作和赋值字符串；
>- 能够很好地被 C 语言程序员理解——为什么还要学习新事物？
>
>**劣势：**
>
>- 为模拟一等字符串数据类型，需要付出很多努力；
>- 使用难度大，而且很容易产生难以找到的内存 bug；
>- 没有利用 C++ 的面向对象的特性；
>- 要求程序员了解底层的表达方式；
>
>尤其注意，事实上，C 风格字符串的优点同样注定地导致了它的缺点；
>
>上面的列表实际很精心被提出来的，从而能够让我们思考应该有更好的方式。如后面所述，C++ 的 string 类解决了字符串的所有问题，并且证明了 **C 字符串相比一等数据类型的那些优势事实上是极其不恰当**的。

##### 2.使用 string 类

>尽管 string 是一个类，但是几乎总可以将 string 当成内建类型使用，事实上，把 string 想象为简单类型更容易发挥它的特性。通过运算符重载的神奇作用，C++ 的 string 使用起来比 C 字符串简单容易很多。例如，给 string 重定义 + 运算符，以表示“字符串串联”。示例如下，将得到 1234：
>
>+重载
>
>```C++
>string A("12" "21");
>// string 的传入"",中间如果是空白符，则连接在一起，例：("12" "21")会连接在一起相当于 "1221"
>string B("34");
>string C;
>C = A + B;
>```
>
>+=重载
>
>```C++
>string A("12");
>string B("34");
>A += B;
>```
>
>此外，C 风格的字符串不能很好地执行 == 比较：
>
>假如有以下两个字符串：
>
>```C++
>char* a = "12";
>char b[] = "12";
>
>// 按照如下方式比较总得到的结果是 false，因为它比较的是指针的值，而不是字符串的内容
>if (a == b)
>
>// 要比较 C 字符串要使用如下代码：
>if (strcmp(a, b) == 0)
>```
>
>此外，C 字符串也无法通过 <、 >、 <=、 >= 的比较，因此仍需要通过 strcmp()  根据字符串字典的顺序返回 -1、0、1 的值进行判断，这样将会使得代码很笨拙而且很容易出错；
>
>而在 C++ 中这些比较运算符，operate==、opertae!= 和 operate< 等都被重载了，这些运算符可以操作真正的字符串字符，这样只需要通过运算符就可以完成基本操作，单独的字符可以通过运算符 operate[] 访问示例如下：
>
>```C++
>std::string myString = "hello";
>myString += ", there";
>std::string myOtherString = mystring;
>if (myString == myOtherString)
>{
>	myOtherString[0] = 'H';
>}
>
>std::cout << myString << std::endl;
>std::cout << myOtherString << std::endl;
>
>// 以上代码输出：
>hello, there
>Hello, there
>```
>
>注意，从上述代码中，我们还 能够看出，**string 类能够自动处理内存需求被再次分配和调整大小，因此不会出现内存溢出的情况，这使得对字符串的处理变得更安全方便**；所有的这些 string 类对象都创建为堆栈变量。尽管 string 类可定需要完成大量分配内存和调整大小的工作，但是 string 类的析构函数会在 string 对象离开作用域的时候清理内存；
>
>**另外需要注意的是，运算符总能以预期的方式方式工作。**例如， = 运算符复制字符串(这种复制不是复制指针，因此改变被复制指针不会对复制者有任何影响)，这是最有可能预期的操作。如果习惯使用基于数组的字符串，那么这种方式可能会带来全新的体验，也可能令你感到迷惑，不用担心，一旦学会信任 string 类总能做出正确的行为，那么代码就会变得很简单了；
>
>为达到兼容目的，**还可以应用 string 类中的 c_str() 方法返回 C 风格字符串的 const 字符指针。不过，一旦 string 执行任何内存重分配或 string 对象被销毁了，那么这个 cosnt 指针就永久失效了**。因此，当使用这个操作时需要谨慎明白这种指针丢失风险；所以，应当在使用结果之前调用这个方法，以便它能够准确地反映 string 的当前内容，并且永远不要从函数中返回在基于堆栈的 string 上调用 c_str() 的结果。
>
>此外，**还有一个 data() 方法，在 C++14 以及更早的版本中，始终与 c_str() 一样返回 const char* 。从 C++ 17 开始，在非 const 字符上调用时， data() 方法将返回 char***；
>
>除此以外，可以查看这本书的附录 B，查看可在 string 类对象上执行的所受对象操作；

##### 3.std::string 字面量

> **源代码中的字符串字面量通常被解释为 const char***。**使用用户定义的标准字面量 s 可以把字符串字面量解释为 std::string**，例如：
>
> ```c++
> auto string1 = "Hello World";
> auto stirng2 = "Hello World"s;
> 
> // 用户定义的标准字面量 s 需要 using namespace std::string_literals;
> // 或者需要 using namespace std;
> ```

##### 4.高级数值转换

> **std 名称空间包含很多辅助函数，以便完成数值和字符串之间的转换。下面的函数可用于将数值转换为字符串。所有的这些函数都负责内存分配，它们会创建一个新的 string 对象并返回。**
>
> - **string to_string(int val);**
> - **string to_string(unsigned val);**
> - **stirng to_string(long val);**
> - **string to_string(unsigned long val);**
> - **string to_string(long long val);**
> - **string to_string(unsigned long long val);**
> - **string to_string(float val);**
> - **string to_string(double val);**
> - **string to_string(long double val);**
>
> 这些函数的使用简单直观，例如，下面示例中将 long double 值转化为字符串:
>
> ```C++
> long double d = 3.14L;
> string s = to_string(d);
> ```
>
> 下面同样是定义在 std 名称空间中的函数，其中，**str 表示将要进行转换的字符串；idx 是一个指针，这个指针将接收第一个未完成转换的字符的索引；base 表示转换过程中使用的进制**。idx 可以是空指针，如果是空指针则被忽略。
>
> 如果不能执行任何转换，这些函数将抛出 invalid_argument 异常；
>
> 如果转换的值超出返回类型的范围，则抛出 out_of_range 异常；
>
> - **int stoi(const string& str, size_t* idx = 0, int base = 10);**
>
> - **long stoi(const string& str, size_t* idx = 0, int base = 10);**
>
> - **unsigned long stol(const string& str, size_t* idx = 0, int base = 0);**
>
> - **long long stoll(const string& str, size_t* idx = 0, int base = 0);**
>
> - **unsigned long long stoull(const string& str, size_t* idx = 0, int base = 0);**
>
> - **float stof(const string& str, size_t* idx = 0);**
>
> - **double stod(const string& str, size_t* idx = 0);**
>
> - **long double stold(const string& str, size_t* idx = 0);**
>
>   **上面的使用时要加 std:，下面的不需要。**
>
> - **int strtoi(const string& str, size_t* idx = 0, int base = 10);**
>
> - **long strtoi(const string& str, size_t* idx = 0, int base = 10);**
>
> - **unsigned long strtol(const string& str, size_t* idx = 0, int base = 0);**
>
> - **long long strtoll(const string& str, size_t* idx = 0, int base = 0);**
>
> - **unsigned long long strtoull(const string& str, size_t* idx = 0, int base = 0);**
>
> - **float strtof(const string& str, size_t* idx = 0);**
>
> - **double strtod(const string& str, size_t* idx = 0);**
>
> - **long double strtold(const string& str, size_t* idx = 0);**
>
> 示例：
>
> ``` C++
> const std::string toParse = "	123USB";
> size_t index = 0;
> int value = std::stoi(toParse, &index);
> std::cout << "Parsed value: " << value << std::endl;
> std::cout << "First non-parsed character: " << "''" << toParse[index] << "'" << std::endl;
> ```
>
> 输出如下：
>
> ```C++
> Parsed value: 123
> First non-parsed character: 'U'
> ```

##### 5.低级数值转换

> 使用思路就是：用 s.data() 获取起始指针，利用 s.data() + s.size() 或者 s.data() + s.strlen() 获取终止指针，然后都是将值传递给相应需要的需要得到的变量中；

> **C++17 也提供了许多低级数值转换函数，这些都在 <charconv> 头文件中定义。这些函数不执行内存分配，而使用由调用者分配的缓存区。另外，对它们进行优化，以实现高性能，并独立于本地化(有关本地化的内容，详见第 19 章)。最终结果是，与其他更高级的数值转换函数相比，这些函数的运行速度要快几个数量级。如果性能要求高，需要进行独立于本地化的转换，则应当使用这些函数；例如，在数值数据与人类可读格式(如 JSON、XML 等)之间进行序列化/反序列化；**
>
> 要将**整数转化为字符**使用下面一组函数，这里，**IntegerT** 可以是**任意有符号或无符号的整数类型或字符类型**，**结果的类型**是 **to_chars_result** ：
>
> **to_chars_result to_chars(char* first, char* last,IntegerT value, int base = 10);**
>
> **to_chars_result 类型定义如下：**
>
> ```c++
> struct to_chars_result
> {
> 	char* ptr;
> 	errc ec;
> }
> 
> // 如果转换成功，那么 ptr 成员等于写入字符的下一位置(one-past-the-end)的指针；
> // 如果转换失败，即： ec == errc::value_too_large，则 ptr 成员等于 last;
> ```
>
> 示例：
>
> ```c++
> #include <iostream>
> #include <string>
> #include <charconv>
> 
> using std::cout;
> using std::endl;
> using std::string;
> 
> int main()
> {
>  	string out(10, ' ');
>  	auto result = std::to_chars(out.data(), out.data() + out.size(), 12345);
>  	if (result.ec == std::errc())
>  	{
>    		cout << "Converted value: " << out << endl;
>  	}
>  	else {
>    		std::cerr << "Conversion error" << std::endl;
>  	}
> 
>  	return 0;
> }
> 
> // 使用结构化绑定可以将其写为：
> std::string out(10, '');
> auto [ptr, ec] = std::to_chars(out.data(), out.data() + out.size(), 12345);
> if (result.ec == std::cerr()) { ... }
> ```
>
> **类似的，以下为浮点型的转换函数：**
>
> **to_chars_result to_chars(char* first, char* last, FloatT value);**
>
> **to_chars_result to_chars(char* first, char* last, FloatT value, chars_format fomat);**
>
> **to_chars_result to_chars(char* first, char* last, FloatT value, chars_format fomat, int precision);**
>
> 这里，FloatT 可以是 float、double 或 long double。可使用 chars_format 标志的组合来指定格式：
>
> **chars_format 类型定义如下：**
>
> ```c++
> enum class chars_format
> {
> 	scientific;						// Style: (-)d.ddde±dd
>  fixed;							// Style: (-)ddd.dd
>  hex;							// Style: (-)h.hhhp±d (Note: no 0x)
>  general = fixed | scientific	  // See the following staff
> };
> ```
>
> **默认格式是 chars_format::general, 这将导致 to_chars()将浮点值转换为 (-)ddd.ddd 形式的十进制表示形式，或(.)d.ddde土dd 形式的十进制指数表示形式，得到最短的表示形式，小数点前至少有一位数字(如果存在)。如果指定了格式，但未指定精度，将为给定格式自动确定最简短的表示形式，最大精度为 6 个数字**；
>
> **对于相反的转换，即将字符序列转换为数值，可使用下面的一组函数：**
>
> **from_chars_result from_chars(const char* first, const char* last, IntegerT& value, int base = 10);**
>
> **from_chars_result from_chars(const char* first, const char* last. FloatT& value, chars_format format = chars_format::general);**
>
> **from_chars_result 类型定义：**
>
> ```c++
> struct from_chars_result
> {
> 	const char* ptr;
> 	errc ec;
> };
> ```
>
> **结果类型的 ptr 成员是指向未转换的第一个字符的指针；如果所有字符都成功转换，则它等于 last。如果所有字符都未转换，则 ptr 等于 first, 错误代码的值将为 errc::invalid_argument。如果解析后的值过大，无法由给定类型表示，则错误代码的值将是 errc::result_out_range。注意，from_chars()不会忽略任何前导空白。**
>
> ```  c++
> // 手动移动指针到第一个非空白字符
> while (std::isspace(*str))
> {
>  	++str;
> }
> // 使用这种方法来移到要使用的数字前
> 
> // 示例如何使用：
> #include <iostream>
> #include <charconv>
> 
> int main() {
>  	const char* str = "123.456";
>  	double value;
> 
>  	// 使用 std::from_chars 进行字符串到浮点数的转换
>  	auto result = std::from_chars(str, str + std::strlen(str), value);
> 
>  	if (result.ec == std::errc())
>  	{
>    		// 转换成功
>    		std::cout << "Converted value: " << value << std::endl;
>  	}
>  	else
>  	{
>    		// 转换失败
>    		std::cerr << "Conversion error" << std::endl;
>  	}
> 
>  	return 0;
> }
> ```

****

#### 1.4std::string_view 类

> 在 C++17 之前，为了接收只读字符串而选择怎样的形参类型始终是个问题：
>
> - 如果选择 `const char*`，那么用户在使用 std::string 的话，就必须调用其上的 c_str() 或 data() 来获取 const char *，更糟糕的是，函数将失去 std::string 的良好面向对象性和良好的辅助方法。
>
> - 我们这样想的话为什么不使用 `const string&` ？这种情况，需要始终使用 std::string。比如，如果传递一个字符串字面量，编译器将不加通告地创建一个临时字符串对象(其中包含字符串字面量的副本)，并将该对象传递给函数，因此会增加一些开销。
>
> - 在 C++ 中，**字符串字面量(如 `"hello"`)是以字符数组的形式存在的**，**类型为 `const char[N]`**，其中 N 是字符串的长度。当将字符串字面量传递给接受 `const std::string&` 的函数时，由于函数参数是引用，编译器会尝试将字符串字面量**隐式地转换**为 `std::string` 对象。
>
>   **为了进行这种转换，`std::string` 类型有一个接受 `const char*` 的构造函数。因此，编译器会创建一个临时的 `std::string` 对象，将字符串字面量的内容复制到该对象中，然后将这个临时对象传递给函数。**
>
>   这种隐式的转换可能会引入一些性能开销，因为它涉及到内存分配和复制操作。如果函数只是需要读取字符串而不修改它，使用 `const std::string&` 可能会显得不够高效。
>
> - 因此，人们有时会为此编写函数的 const char* 和 const string& 两个函数接收版本，这显然不够优雅。
>
> - **在 C++17 中，通过引入 std::string_view 类解决了所有这些问题，std::string_view 类 std::basic_string_view类模板的实例化，在 <string_view> 头文件中定义。string_view 基本上就是 const string& 的简单替代品，但不会产生开销。它从不复制字符串，string_view 支持与 std::string 类似的接口。一个例外是缺少 c_str(), 但 data() 是可用的。另外，string_view 确实添加了 remove_prefix(size_t) 和 remove_suffix(size_t) 方法；前者将起始指针前移给定的偏移量来收缩字符串，后者则将结尾指针倒退给定的偏移量来收缩字符串。**
>
> - **具体操作上就是用 std::string_view() 构造函数 替代 const std::string& 样式的传参方式，来减小开支，因为`std::string_view()` 构造函数并不会引起额外的动态内存分配或拷贝，因为它只是一个视图，不拥有字符串的所有权。这个构造函数创建了一个空的 `std::string_view` 对象，但并不分配内存或复制字符串。**
>
> > ```c++
> > std::string_view myString = "Hello, World!";
> > // 移除末尾的前7个字符
> > myString.remove_suffix(7);
> > std::cout << "After removing suffix: " << myString << std::endl;
> > ```
>
> - 注意，**无法连接一个 string 和一个 string_view 类型**，下面的代码将无法编译：
>
> > ```c++
> > string str = "Hello";
> > string_view sv = " world";
> > auto result = str + sv;
> > 
> > // 最后一行改为：
> > auto result = str + sv.data();
> > ```
>
> - 如果知道如何使用 std::string, 那么使用 string_view 将变得十分简单，如下面的代码片段所示。extractExtension() 函数提取给定文件名的扩展名并返回：
>
> > ```c++
> > string_view extractExtension(string_view fileName)
> > {
> >  	return fileName.substr(fileName.rfind('.'));
> > }
> > ```
>
> - 该函数可用于所有不同类型的字符串：
>
> > ```c++
> > string fileName = R"(c:\temp\my file.ext)";
> > cout << "C++ string: " << extractExtension(fileName) << endl;
> > const char* cString = R"(c:\temp\my file.ext)";
> > cout « "C string: " << extractExtension(cString) << endl;
> > cout « "Literal: " « extractExtension(R"(c:\temp\my file.ext)") << endl;
> > ```
>
> - **注意，通常按值传递 string_views, 因为它们的复制成本极低**。
> - **复制成本极低原因：它们只包含指向字符串的指针以及字符串的长度。**  
> - 在对 extractExtension() 的所有这些调用中，并非进行单次复制。**extractExtension() 函数的 fileName 参数只是指针和长度**，该函数的返回类型也是如此。这都十分高效。
>
> **string_view 构造函数的使用：**
>
> - 它可以接收任意原始缓存区和长度，这可用于从字符串缓冲区(并非以 NUL 终止) 构建 string_view。如果确实有一个以 NUL 终止的字符串缓冲区，但是如果已经知道了字符串长度，构造函数不必再统计字符串数目
>
> > ```c++
> > size_t length = 3;
> > const char* cString = R"(c:\temp\my file.ext)";
> > cout << std::string_view(cString, length) << endl;
> > cout << std::string(cString, length) << endl;
> > 
> > // 使用 string_view 更高效
> > ```
>
> - 总结起来就是，string_view 比 string 强的地方就是，它不用再进行隐式的 string 类型构造，因为 C 风格字符串和 string 字面量 会进行隐式转换，复制构造，这里会有开销差距。
> - 我上面说了，既然没有隐式构造，那么我们的返回值是 string_view 那么就不能被当作 string 参量看待也就是我接下来举出的例子说明的事情：
>
> > ```c++
> > void handleExtension(const string& extension) { ... }
> > 
> > // 没有隐式转换存在，不能使用以下方式调用函数：
> > handleExtension(extractExtension("my file.ext"));
> > 
> > // 可选用以下方法：
> > // 1.显式转换	explitcit ctor
> > handleExtension(string(extractExtension("my file.ext")));
> > // 2.data() 方法
> > handleExtension(extractExtension("my file.ext").data());
> > 
> > /* 注意，即使原本的传入参数应该为 const string& 类型，但是 C 风格的字符串会首先隐式地调用 string 构造函数，然后再调用 const string& 构造函数，以完成代码 */
> > handleExtension(C - String);
> > ```
>
> **注意：在每当使用只读字符串作为参数时，可以使用 std::string_view 代替 const char* 或 const string&。**
>
> **std::string_view 字面量：**
>
> - 可使用标准的用户定义的字面量 sv，将字符串字面量解释为 std::string_view，例如：
>
>   > ```c++
>   > auto sv = "My string_view"sv;
>   > ```
>
> - 标准的用户定义的字面量 sv 需要 using namespace std::string_view_literals; 或 using namespace std;

**总结：**

> 自动调用隐式构造函数的情况：
>
> ```c++
> char* --->string_view			可行
> string--->string_view			可行
> string_view--->string_view	可行
> 
> char* --->string				可行
> string--->string				可行
> string_view--->string			不可行
> 
> ...---> char* 都不可行
> // 以上的左侧是实际参数，右边是函数期待的参数，可行代表可以运行，不可行代表不接受
> ```
>
> 字面量在不告知的情况下，是 const char* 类型或者说是 const char[] 类型；

****

#### 1.5非标准字符串

> **许多 C++程序员都不使用 C++风格的字符串，这有几个原因。**一些程序员只是不知道有 string 类型，因为它并不总是 C++ 规范的一部分。其他程序员发现，C++ string 没有提供他们需要的行为，所以开发了自己的字符串类型。也许最常见的原因是，开发框架和操作系统有自己的表达字符串的方式，例如 Micros。仕 MFC 中的CString 类。它常用于向后兼容或解决遗留的问题。在 C++ 中启动新项目时，提前确定团队如何表示字符串是非常重要的。务必注意以下几点：
>
> 1. 不应当选取 C 风格的字符串表示。
> 2. 可对自己所用框架中的可用字符串进行标准化，如 MFC、QT 内置的字符串功能。
> 3. 如果为字符串使用 std::string，应当使用 std::string_view 将只读字符串作为参数传递给函数；否则，看一下框架是否支持类似于它的类。

****

### 2.2本章小结

> 一句话，用 string，传只读字符串用 string_view。

****

## 第3章 —— 编码风格

****

> 编写具有风格的代码才算真正掌握了编码；
>
> 简单地改变代码风格可以极大改变代码的外观；
>
> 不同种程序员的 C++ 代码风格有着本质的区别；

### 3.1良好外观的重要性

> 编写文体上“良好” 的代码很费时，而编写出功能分离、注释充分、结构清晰的相同程序需要更长时间，那么就有一个问题这值吗？显然，既然提出那么结果必然是值得的；

****

#### 1.1事先考虑

> 实际中如果没有良好的编码风格会有以下问题：
>
> 1. 对于新手不友好；
> 2. 几乎无法代码维护，代价极大；
> 3. 难以复用代码实现；

****

#### 1.2良好风格的元素

> 良好代码的共通原则：
>
> - 文档
> - 分解
> - 命名
> - 语言的使用
> - 格式

****

###  3.2为代码编写文档

> 在编程环境下，文档通常指源文件中的注释。当编写相关代码时，注释用来说明你当时的想法。这里给出的信息应当是不能轻易从代码中看出来的。

****

#### 2.1使用注释的原因

> 使用注释明显能够提高效率、易于理解代码等优点，下面给出全部使用注释的原因：
>
> 1. 说明用途的注释：
>
>    > **使用注释的原因之一是说明客户如何与代码交互。通常而言，开发人员应当能够根据函数名、返回值的类型以及参数的类型和名称来推断函数的功能。**但是，代码本身不能解释一切。有时， 一个函数需要一些先置条件或后置条件，而这些需要在注释中解释。函数可能抛出的异常也应当在注释中解释。在笔者看来，只有当注释能提供有用的信息时才添加注释。因此，应由开发人员确定函数是否需要添加注释。经验丰富的程序员能可靠地确定这一点，但经验不足的开发人员则未必能做出正确的决策。**因此，一些公司制定规则，要求头文件中每个公有访问的函数或方法都应该带有解释其行为的注释。某些组织喜欢将注释规范化，明确列出每个方法的目的、参数、返回值以及可能抛出的异常。**  
>    >
>    > 示例：
>    >
>    > ```c++
>    > /*通过注释，可用自然语言陈述在代码中无法陈述的内容。例如，在 C++中无法说明：数据库对象的saveRecord()方法只能在 openDatabaseo方法之后调用，否则将抛出异常。但可以使用注释提示这一限制，如下所示：*/
>    > 
>    > /*
>    > * This method throws a ,,DatabaseNotOpenedExceptionH
>    > * if the openDatabase() method has not been called yet.
>    > */
>    > int saveRecord(Record& record);
>    > ```
>    >
>    > ```c++
>    > /*C++语言强制要求指定方法的返回类型，但是无法说明返回值实际代表了什么。例如，saveRecord() 方法的声明可能指出这个方法返回 int 类型(这是一种不良的设计决策，见下一节的讨论)，但是阅读这个声明的客户不知道 int 的含义。注释可解释其含义：*/
>    > 
>    > /*
>    > * Returns: int
>    > * An integer representing the ID of the saved record.
>    > * Throws:
>    > * DatabaseNotOpenedException if the openDatabase() method has not
>    > * been called yet.
>    > */
>    > int saveRecord(Record& record);
>    > ```
>    >
>    > ```c++
>    > /*如前所述，有些公司要求用正式方式记录有关函数的所有信息。下例演示了遵守这个原则的 saveRecord()方法：*/
>    > 
>    > /*
>    > * saveRecord( )
>    > * Saves the given record to the database.
>    > * Parameters:
>    > * Records record: the record to save to the database.
>    > * Returns: int
>    > * An integer representing the ID of the saved record.
>    > * Throws:
>    > * DatabaseNotOpenedException if the openDatabase() method has not
>    > * been called yet.
>    > */
>    > int saveRecord(Record& record);
>    > 
>    > /* 但不建议使用这种风格的注释。前两行完全无用，因为函数名的含义不言自明。对形参的解释也不能添加任何附加信息。*/
>    > ```
>    >
>    > ```c++
>    > /*更好的设计方式是返回 RecordID 而非普通的 int 类型，那样的话，就不需要为返回类型添加注释。RecordID 只是 int 的类型别名(见第 11 章)，但传达的信息更多。唯一必须保留的注释是异常。因此，建议使用如下 saveRecord() 方法：*/
>    > 
>    > 
>    > /*
>    > * Throws:
>    > * DatabaseNotOpenedException if the openDatabase() method has not
>    > * been called yet.
>    > */
>    > RecordID saveRecord(Record& record);
>    > ```
>    >
>    > ```c++
>    > /*有时函数的参数和返回值是泛型，可用来传递任何类型的信息。在此情况下应该清楚地用文档说明所传递的确切类型。例如，Windows 的消息处理程序接收两个参数 LPARAM 和 WPARAM, 返回 LRESUUT。这些参数和返回值可以传递任何内容，但是不能改变它们的类型。使用类型转换，可以用它们传递简单的整数，或者传递指向某个对象的指针。文档应该是这样的：*/
>    > 
>    > /* Parameters:
>    > * WPARAM wParam: (WPARAM)(int): An integer representing...
>    > * LPARAM IParam: (LPARAM)(string*): A string pointer representing...
>    > * Returns: (LRESULT)(Record*)
>    > * nullptr in case of an error, otherwise a pointer to a Record object
>    > * representing ...
>    > */
>    > ```
>
> 2. 用来说明复杂代码的注释
>
>    > 在专业领域中，代码的算法往往复杂、深奥，很难理解。
>    >
>    > ```c++
>    > /*
>    >  * 实现插入排序算法。该算法将数组分为两部分——有序部分和无序部分。
>    >  * 每个元素，从位置1开始，都会被检查。数组中早于当前位置的元素都在有序部分，
>    >  * 因此算法会将每个元素向右移动，直到找到正确的位置以插入当前元素。
>    >  * 当算法完成对最后一个元素的操作时，整个数组都已排序。
>    >  */
>    > void sort(int inArray[], size_t inSize)
>    > {
>    > 	// 从位置1开始，检查每个元素。
>    > 	for (size_t i = 1; i < inSize; i++)
>    > 	{
>    > 		// 循环不变式：
>    > 		// 在范围0到i-1(包括i-1)的所有元素都是有序的。
>    > 		int element = inArray[i];
>    > 		// j 标记在有序部分中，element 将要插入的位置之后。
>    > 		size_t j = i - 1;
>    > 		// 只要有序数组中的当前槽位的值大于 element，将值向右移动以为插入 element 腾出位置
>    > 		//(因此称为 "插入排序")。
>    > 		while (j >= 0 && inArray[j] > element) {
>    > 			inArray[j + 1] = inArray[j];
>    > 			j--;
>    > 		}
>    > 		// 此时有序数组中的当前位置不大于 element，因此这是 element 的新位置。
>    > 		inArray[j + 1] = element;
>    > 	}
>    > }
>    > ```
>    >
>    > 新代码有所增长，但通过注释，使得不熟悉代码的读者也能理解这段代码；
>
> 3. 传递元信息的注释
>
>    >使用注释的另一个原因高于代码层次提供信息，元信息提供代码的详细信息，但是不涉及代码的特定行为。例如，某组织可能想使用元信息跟踪每个方法的原始作者。还可以使用元信息引用外部文档或其他代码；
>    >
>    >下例给出了元信息的几个实例，包括文件的作者、创建日期、提供的特性。此外还包括表示元数据的行内注释，例如对应某行代码的 bug 
>    >
>    >编号，提醒以后重新访问时代码中某个可能的问题。
>    >
>    >
>    >
>    >```c++
>    >/*
>    >* Author: marcg
>    >* Date: 110412
>    >* Feature: PRD version 3, Feature 5.10
>    >*/
>    >
>    >RecordID saveRecord(Records record)
>    >{
>    > 	if (!mDatabaseOpen)
>    >	{
>    > 		throw DatabaseNotOpenedException();
>    > 	}
>    >	RecordID id = getDB()->saveRecord(record);
>    >	if (id == -1) return -1; // Added to address bug #142 - jsmith 110428
>    >	record.setld(id); // TODO: What if setld() throws an exception? - akshayr 110501
>    >}
>    >/*
>    >* Date   | Change
>    >*--------+-------------------------------------------
>    >* 110413 |REQ #005: <marcg> Do not normalize values.
>    >* 110417 | REQ #006: <marcg> use nullptr instead of NULL.
>    >*/
>    >```
>    >
>    >**警告：**
>    >**使用第 24 章讲述的源代码控制方案(也应当使用该方案)， 前几个示例中就不必使用所有元信息(TODO 注释除外)。 源代码控制方案提供了带注释的修改历史，包括修改日期、修改人、对每个修改的注释(假定使用正确)，以及对修改请求和 bug 报告的引用。应 当使用描述性注释，分别签入(check-in)、提交每个修改请求或 bug修复。有了这样的系统，你不必手动跟踪元信息。**
>    >
>    >**另一种元信息类型是版权声明。有些公司要求在每个源文件的开头添加此类版权信息。**
>    >
>    >**注释很容易走向极端。最好与团队成员讨论哪种类型的注释最有用，并制定约定。例如，如果团队的某个成员使用 TODO 注释表明代码仍然需要加工，但是其他人不知道这个约定，这段代码就可能被忽略。**
>    >
>    >具体略过了，看课本吧，这太麻烦了，不是我想学的东西；

****

2.2注释的风格

> 1. 错误：每行均注释，完全没必要，可以写很多，但是要保证有用；
> 2. 正确：前置注释，某些源代码控制系统，例如(Subversion(SVN))甚至可以帮忙填写元数据；
>    - 最近的修改日期
>    - 原始作者
>    - 前面所讲的修改日志
>    - 文件给出的功能
>    - 版权信息
>    - 文件或类的简要说明
>    - 未完成的功能
>    - 已知的 bug
> 3. 固定格式的注释，关于 Doxygen 的学习之后再说。
> 4. 特殊注释：
>    - 注释之前，思考是否可以通过修改代码来避免注释，如：重命名变量、函数与类、重新排列代码步骤的顺序，引入完好命名的中间变量；
>    - 他人难以察觉的微妙之处应当注释；
>    - 不要在代码中加入姓名缩写，源代码控制解决方案会自动跟踪这些信息；
>    - 如果处理不太明显的 API，应当再解释 API 的地方对 API 文档进行引用；
>    - 更新代码时，记得更新注释；
>    - 如果使用注释将某个函数分为多节，那么考虑这个函数是否可以被分为多个更小的函数；
> 5. 自文档化代码
>    - 编写良好的代码并非总是需要充裕的注释，优秀的代码本身就容易阅读。
>    - 如果给每行代码都加入注释，考虑是否可重写这些代码，以更好地配合注释内容。
>    - 例如给函数、参数、变量等使用描述性名称。
>    - 合理使用 const, 也就是说，如果不准备修改变量，就将其标记为 const 
>    - 重新排列函数中步骤的顺序，使人更容易理解其作用。
>    - 引入命名良好的中间变量，使算法更易懂。

****

### 3.3分解(decomposition)

> 分解指将代码分为小段；
>
> 当有新要求或修订 bug 时，会对现有的代码进行少量修改，计算机术语 cruft 便是指的逐渐积累少量代码使得曾经优雅的代码编程一堆补丁和特例；

****

#### 3.1通过重构(refactoring)分解

> 增强抽象的技术：
>
> - 封装字段：私有化字段，使用 get() 方法、set() 方法；
> - 让类型通用：创建更通用类型，便于共享代码；
>
> 分割代码使其更合理的技术：
>
> - 提取方法：将一个大方法的部分提取成为便于理解的方法；
> - 提取类：将现有类的部分代码转移到新类中；
>
> 增强代码名称和位置的技巧：
>
> - 移动方法或字段：移动到更合适的类或源文件中；
> - 重命名方法或字段：使之名称更符合其含义；
> - 上移(pull up)：在 OOP 中，移到基类；
> - 下移(push down)：在 OOP 中，移到派生类；
>
> 详细见课本内容，这对我目前意义不大。

****

#### 3.2通过设计来分解

> 略。

****

#### 3.3本书的分解

> 略。

****

### 3.4命名

> 编译器的几个命名规则：
>
> - 名称不以数字开头；
>
> - 包含两个下划线的名称(例如 my__name) 是保留名称，不应当使用；
>
>   > C++标准(例如C++17)规定了使用双下划线开头或结尾的标识符是保留给实现的。这意味着用户代码不应该在标识符的开头或结尾使用双下划线，以免与实现的标识符冲突。
>
> - 以下划线开头(例如 _Name 或 __Name) 是保留名称，不应该使用；

****

#### 4.1选择恰当的名称

> ![image-20240204084416838](https://s2.loli.net/2024/02/09/kzXxCPVmv7t5yrK.png)
>
> 如上。

****

#### 4.2命名约定

> 1. 计数器：【i、j】【row、column】【outerLoopIndex、innerLoopIndex】
> 2. 前缀：使用前缀会使得相关代码难以维护，例如，如果某个成员变量从静态变为非静态，这意味着所有用到这个名称的地方都要修改。这通常非常耗时，因此大多数程序员不会重命名这个变量。随着代码的演变,变量的声明变了，但是名称没有变。结果是名称给出了虚假的语义，实际上这个语义是错误的。  
>
> ![image-20240204084721064](https://s2.loli.net/2024/02/09/mIYiPr5blEetgpk.png)
>
> 3. 匈牙利表示法是关于变量和数据成员的命名约定，在 Microsc仕 Windows 程序员中很流行。其基本思想是使用更详细的前缀而不是一个字母(例如 m)表示附加信息。下面这行代码显示了匈牙利表示法的用法：
>
>    ```c++
>    char* pszName; // psz means "pointer to a null-terminated string"
>    ```
>
>    术语“匈牙利表示法”源于其发明者 Charles Simonyi 是匈牙利人。也有人认为这准确地反映了一个事实：使用匈牙利表示法的程序好像是用外语编写的。为此，一些程序员不喜欢匈牙利表示法。本书使用前缀，而不使用匈牙利表示法。合理命名的变量不需要前缀以外的附加上下文信息，例如，用 mName 命名数据成员就足够了。
>
> 4. get() 和 set()
>
> 5. 大小写，统一即可
>
> 6. 把常量放到名称空间
>
>    > 假定编写一个带图形用户界面的程序。这个程序有几个菜单，包括 File、 Edit 和 Help。用常量代表每个菜单的 ID。kHelp 是代表 Help 菜单 ID 的一个好名字。
>    >
>    > 名称 kHelp一直运行良好，直到有一天在主窗口上添加了一个 Help 按钮。还需要一个常量来代表 Help 按钮的 ID, 但是 kHelp 已经被使用了。
>    >
>    > 在此情况下,建议将常量放到不同的名称空间中，名称空间参见第 1 章。可以创建两个名称空间: Menu 和 Button。
>    >
>    > 每个名称空间中都有一个 kHelp 常量，其用法为 Menu::kHelp 和 Button::kHelpo 
>    >
>    > 另一个更好的方法是使用枚举器，参见第 1 章。

****

### 3.5使用具有风格的语言特征

> ```c++
> i++ + ++i;
> a[i] = ++i;
> 
> 第一行完全没有标准，结果取决于平台；
> 第二行在 C++ 17 中是确定的：i先递增，再在 a[i] 中用作索引；
> ```
>
> 但它们的共同特点就是：丑陋。

****

#### 5.1使用常量

> ```c++
> #include <cmath>
> 
> double result = 2.71828 * 5.0;
> std::cout << "Result: " << result << std::endl;
> 
> // 推荐的方式，使用常量 M_E
> result = M_E * 5.0;
> std::cout << "Result: " << result << std::endl;
> ```

****

#### 5.2使用引用代替指针

> **C++程序员通常开始学的是 C。在 C 中，指针是按引用传递的唯一机制**，多年来一直运行良好。在某些情况下仍然需要指针，但在许多情况下可以用引用代替指针。如果开始学习的是 C, 可能认为引用实际上没有给C++语言增加新的功能，只是引入了一种新的语法，其功能己经由指针提供。  
>
> **用引用替换指针有许多好处。**首先，**引用比指针安全**，因为**引用不会直接处理内存地址，也不会是 nullptr**。其次，**引用在文体上比指针好**，因为引**用使用与堆栈变量相同的语法，没有使用 * 和&等符号**。引用易于使用，因此将引用加入风格中没有任何问题。遗憾的是，某些程序员认为，如果在函数调用中看到&，被调用的函数将改变对象；如果没有看到&，对象一定是按值传递。而使用引用，就无法判断函数是否将改变对象，除非看到函数原型。这种思维方式是错误的。用指针传递未必意味着对象将改变，因为参数可能是 const T。**传递指针或引用是否会修改对象，都取决于函数原型是否使用了 const T* 、T*、constT&或 T&。因此，只有查看函数原型，才能判断函数是否改变对象**。  
>
> **使用引用的另一个好处是它明确了内存的所有权。如果一个程序员编写了一个方法，另一个程序员传递给它一个对象的引用，很明显可以读取并修改这个对象，但是无法轻易地释放对象的内存。如果传递的是一个指针，就不那么明显。需要删除对象来清理内存吗？还是调用者需要这样做？处理内存的较好方法是使用第 1 章介绍的智能指针.**  

****

#### 5.3使用自定义异常

> C++可以很方便地忽略异常，这一语言的语法没有强制处理异常，可以很方便地用传统的机制(例如返回nullptr 或者设置错误标志)编写容错程序。
>
> 异常提供了更丰富的错误处理机制，自定义异常允许根据需要进行取舍。例如，Web 浏览器的自定义异常类型包含的字段可指定包含错误的页面、错误发生时的网络状态和附加的环境信息。  
>
> 第 14 章将详细讲述 C++中的异常 。

****

### 3.6格式

> 一句话，统一的就是好的。

****

#### 6.1关于大括号对齐的争论

> ```c++
> Staff
> {
> 	...
> }
> ```
>
> 我都是这样用的；

****

#### 6.2关于空格和圆括号的争论

> ```c++
> function();
> if ()
> for ()
> ```
>
> 函数不空格，判定循环语句空格；

****

#### 6.3空格和制表符

> 没啥说的；

****

### 3.7风格的挑战

> 许多程序员在项目开始时都保证他们将做好每件事。只要变量或参数永远不变，就将其标记为 const。所有变量都具有清楚的、简明的、容易阅读的名称。每个开发人员都将左大括号放在后续行，采用标准文本编辑器,并遵循关于制表符和空格的约定。
>
> 维持这种层次的格式一致非常困难，原因有很多**。当涉及 const 时，有些程序员不知道如何用它。总会遇到不支持 const 的旧代码或库函数。好的程序员会使用 const_cast 暂时取消变量的 const 属性，但缺少经验的程序员会取消来自调用函数的 const 属性，结果，程序从不使用 const。**
>
> 有时，标准化的格式会与程序员的个人口味和偏好发生冲突。或许团队文化无法强制使用严格的风格准则。此类情况下，必须判断哪些元素需要标准化(例如变量名称和制表符)，哪些元素可以由个人决定其风格(或许空格和注释格式可以这样)。甚至可以获取或编写脚本，自动纠正格式 bug, 或将格式问题与代码错误一起标记。一些开发环境，例如 Microsoft Visual C++ 2013, 支持根据指定的规则自动格式化代码，这样就很容易编写出始终遵循指定规则的代码

****

### 3.8本章小结

> 一句话，风格好就是NB。

****

## 第二部分 —— 专业的 C++ 软件设计

****

## 第4章 —— 设计专业的 C++ 程序

****

### 4.1程序设计概述

> 设计文档的常见布局基本类似，包括两个主要部分：
>
> (1) 将总的程序分为子系统，包括子系统之间的界面和依赖关系、子系统之间的数据流、每个子系统的输入输出和通用线程模型。
>
> (2) 每个子系统的详情，包括类的细分、类的层次结构、数据结构、算法、具体的线程模型和错误处理的细节。
>
> 就是 UML 图，这里就不仔细说了。

****

### 4.2程序设计的重要性

> 总结，UML。

****

### 4.3C++ 设计的特点

> 在使用 C++进行设计时，需要考虑 C++语言的一些性质：
>
> - C++具有庞大的功能集。它几乎是 C 语言的完整超集，此外还有类、对象、运算符重载、异常、模板和其他功能。由于该语言非常庞大，使设计成为一项令人生畏的任务。
>
> - C++是一门面向对象语言。这意味着设计应该包含类层次结构、类接口和对象交互。这种设计类型与传统的 C 和其他过程式语言的设计竞全不同。第 5 章重点介绍 C++面向对象设计。
>
> - C++有许多设计通用的、可重用代码的工具。除了基本的类和继承之外，还可以使用其他语言工具进行高效的设计，如模板和运算符重载。第 6 章将详细讨论可重用代码的设计技术。
>
> - C++提供了一个有用的标准库，包含字符串类、I/O 工具、许多常见的数据结构和算法。所有这些都便于 C++代码的编写。
>
> - C++语言提供了许多设计模式或解决问题的通用方法。
>
> **因此，优秀的设计难能可贵，获取这样的设计需要实践。不要期望一夜之间成长为专家，掌握 C++设计比C++编码更难。**  

****

### 4.4C++ 设计的两个原则

> - **抽象，接口化**
> - **重用，方法化**

****

#### 4.1抽象

>忽略本质，只在意接口、输入、输出，只看结果；
>
>接口并不决定底层实现，改变实现并不需要改变接口；
>
>象棋棋盘示例:
>
>```c++
>class ChessBoard
>{
>public:
>	// This example omits constructors, destructor, and assignment operator.
>	void setPieceAt(size_t x, size_t y, ChessPiece* piece);
>	ChessPiece* getPieceAt(size_t x, size_t y);
>	bool isEmpty(size_t x, size_t y) const;
>private:
>	// This example omits data members.
>};
>```

****

#### 4.2重用

>对已存在代码的使用；
>
>去除特殊化，泛化代码；
>
>任何棋类棋盘示例：
>
>```c++
>template <typename PieceType>
>class GameBoard
>{
>public:
>	// This example omits constructors, destructor, and assignment operator.
>	void setPieceAt(size_t x, size_t y, PieceType* piece);
>	PieceType* getPieceAt(size_t x, size_t y);
>	bool isEmpty(size_t x, size_t y) const;
>private:
>	// This example omits data members.
>};
>```
>
>例如，假定要设计一个国际象棋程序：使用一个 EirorLogger 对象将不同组件发生的所有错误都按顺序写入一个日志文件。当试着设计 EirorLogger 类时，你意识到只想在一个程序中有一个ErrorLogger 实例。还要使程序的多个组件都能使用这个 ErrorLogger 实例，即所有组件都想要使用同一个 ErrorLogger 服务。**实现此类服务机制的一个标准策略是使用注入依赖(dendency injection)**。**使用注入依赖时，为每个服务创建一个接口，并将组件需要的接口注入组件。因此，此时良好的设计应当使用“依赖注入”模式**。**你必须熟悉这些模式和技术，根据特定设计问题选择正确的解决方案。在 C++ 中，还可以使用更多技术和模式。详细讲述设计模式和技术超出了本书的范围，如果读者对此感兴趣，可以参阅附录 B 给出的建议。**

****

### 4.5重用代码

>注意：重用代码并不意味着复制和粘贴已有的代码，但实际含义刚好相反：重用代码，但不重复代码；

****

#### 5.1关于术语的说明

>在分析代码重用优缺点前，有必要指出所涉及的术语，并将重用代码分类。有三种可以重用的代码：
>
>- **过去编写的代码；**
>- **同事编写的代码；**
>- **当前组织或公司以外的第三方编写的代码；**
>
>所使用的代码可通过以下几种方法来构建：
>
>- **独立的函数或类**，当重用自己或同事的代码时，通常会遇到这种类型；
>- **库，库是用于完成特定任务(例如解析 XML)或者针对特定领域(如密码系统)的代码集合**。在库中经常可以找到其他许多功能，如线程和同步支持、网络和图像。
>- **框架(Framework)，框架是代码的集合，围绕框架设计程序**。例如，微软基础类(Microsoft Foundation Classes, MFC)提供了在 Microsoft Windows 中创建用户界面应用程序的框架。框架通常指定了程序的结构。
>
>**注意：**
>
>​	**程序使用库，但会适应框架。库提供了特定功能，而框架是程序设计和结构的基础。**
>
>**应用程序编码接口(API)是另一个经常出现的术语。API 是库或为特定目的而提供的接口。例如，程序员会经常提到套接字 API，这是指套接字联网库的公开接口，而不是库本身**。
>
>**注意：**
>
>​	**尽管人们将库以及 API 互换使用，但是两者不是等价的。库指的是“实现”，而 API 指的是 “库的公开接口”。**
>
>为简洁起见，本章剩余部分用术语“库”表示任何可重用的代码，它事实上可能是库、框架或是同时编写的随机函数集合。

****

#### 5.2决定是否重用代码

>**重用代码的优点：**
>
>- **节省时间和成本；**
>- **不需要额外的设计；**
>- **不需要调试；**
>- **代码安全性更高；**
>- **库会持续改进；**
>
>**重用代码的缺点：**
>
>- **需要花费时间了解接口和正确使用方法；**
>- **代码功能未必完全吻合；**
>- **代码支持问题可能遇到问题；**
>- **代码使用许可问题；**
>- **跨平台可移植性问题；**
>- **对代码质量与安全性的信任问题；**
>- **版本更新可能会出现致命问题；**
>- **使用纯粹二进制库时，将编辑器升级为新版本会导致问题；**
>
>**熟悉了重用代码的术语和优缺点后，就可以决定是否重用代码。**通常，这个决定是显而易见的。例如，如果想要用 C++ 在 Microsoft Windows 上编写图形用户界面(GUI), 应该使用 MFC(Microsoft Foundation Class)或Qt 等框架。你可能不知道如何在 Windows 上编写创建 GUI 的底层代码，更重要的是不想浪费时间去学习。在此情况下使用框架可以节省数年的时间。
>
>然而，有时情况并不明显。例如，如果不熟悉某个库或框架，并且只需要其中某个简单的数据结构，那就不值得花时间去学习整个框架来重用某个只需要花费数天就能编写出来的组件。
>
>总之，这个决定是根据特定的需求做出的选择。通常是在自己编写代码所花时间和查找库并了解如何使用库来解决问题所使用时间之间的权衡。应该针对具体情况，仔细考虑前面列出的优缺点，并判断哪些因素是最重要的。最后，可随时改变想法，如果正确处理了抽象，这并不需要太多的工作量。

****

#### 5.3重用代码的策略

> 当使用库、框架以及同事或自己的代码时，应该记住一些指导方针：
>
> 1. **理解功能和限制限制因素**
>    - 花点时间熟悉代码，对于理解其功能和限制因素而言都很重要。可从文档、公开的接口或 API 开始，理想情况下，这样做足以理解代码的使用方式。然而，如果库未将接口和实现明确分离，可能还要研究源代码。此外，还可与其他使用过这些代码或能解释这些代码的程序员交流。
> 2. **理解性能**
>    - 了解库或其他代码提供的性能保障很重要。即使某个程序对性能不敏感，也应该确保使用的代码在具体的使用中性能不会太糟。  
> 3. **大 O 表示法**
>    -   程序员经常使用大0 表示法(Big-0 Notation)讨论并记录算法和库的性能。  **注意：大 O 表示法仅适用于速度依赖于输入的算法，不适用于没有输入或者运行时间随机的算法。实际上,大多数算法的运行时间都取决于输入，因此这个限制并不重要。**  
>
> ![image-20240209135140519](https://s2.loli.net/2024/02/09/7mJ5GWPqA8NdDuQ.png)
>
> 4. **理解性能的几点提示**
>
>    - 略，见书。
>    - 总结一句就是，你不测试就永远不知道这个库到底性能高不高。
>
> 5. **理解平台限制**
>
>    - 在开始使用库代码之前，一定要理解运行库的平台。这看上去是显而易见的，但即使是那些号称跨平台的库，在不同的平台上也会有微妙差别；此外，平台不仅包括不同的操作系统，还包括同一操作系统的不同版本。  不要以为库一定会向前或先后兼容；
>
> 6. **理解许可证和支持**  
>
>    - 使用第三方的库常会带来复杂的许可证问题。为使用第三方供应商提供的库，有时必须支付许可证费用。还可能有其他的许可限制，包括出口限制。此外，开放源代码库有时会要求与其有关的任何代码都公开源代码；
>
> 7. **了解在哪里寻求帮助**  
>
>    - 首先参考库自带的文档。如果库被广泛使用，如标准库或 MFC, 就应该能找到与此主题相关的优秀书籍。实际上，本书的第 1A21 章都讲述标准库。如果某个特定问题在手册或产品文档中没有提及，可搜索 Web。在选择的搜索引擎中输入问题来寻找讨论这个库的 Web 页面。例如，当查找短语 "introduction to C++ Standard Library” 时，会找到与 C++和标准
>
>      库有关的数百个站点。此外，许多站点包含关于特定主题的新闻组或论坛，可注册并寻找答案。
>
> 8. **原型**
>
>    - 当首次使用某个新库或框架时，最好编写一个快速原型。测试代码是熟悉库功能的最好方法。应该考虑在程序设计之前测试库，这样就可以熟悉库的功能和限制。这种实际检验还可判断库的性能特征。即使原型应用程序与最终应用程序没有任何相似之处，花费在原型上的时间也不会浪费。不要觉得编写实际应用程序的原型很难，可编写一个虚拟程序来测试想使用的库功能，这样做是为了让自己熟悉库。

****

#### 5.4绑定第三方应用程序

> 项目可能包含多个应用程序。或许需要 Web 服务器前端来支持新的电子商务基础设施。可将第三方应用程序(例如 Web 服务器)与软件绑定。**这种方法将代码重用发挥到了极致，因为重用了整个应用程序**。当然，使用库的那些忠告和指导方针也适用于绑定第三方应用程序，应该特别注意自己的决定所涉及的法律和许可证问题。
>
> **注意：**
>
> ​	**将第三方应用程序与分发的软件绑定之前，应当请教专门处理知识产权问题的法律专家。**

****

#### 5.5开放源代码库

> 开放源代码库是一种日益流行的可重用代码类型。**开放源代码(open-source)通常意味着任何人都可以查看源代码。**关于分发软件时包含源代码，有正式的定义和法规，但最重要的是，任何人(包括你)都能查看开放源代码软件的源代码。注意开放源代码不仅适用于库，实际上最著名的开放源代码产品可能是 Android 操作系统。Linux 操作系统是另一个著名的开放源代码操作系统。Google Chrome 和 Mozilla Firefbx 是两个开放源代码的著名 Web 浏览器。  

****

#### 5.6C++ 标准库

> **C++程序员使用的最重要的库就是 C++标准库。**  
>
> **C++ 提供了比 C 更好的字符串以及 I/O 支持。尽管 C 风格的字符串和 I/O 例程在 C++中仍然有效，但应该避免使用它们，而是使用 C++字符串(详见第 2章)和 I/O 流(详见第 13 章)。**  
>
> **设计标准库时优先考虑的是功能、性能和正交性(orthogonality)。使用标准库可获得巨大好处。可回顾在链表或平衡二叉树实现中跟踪指针错误，或者调试不能正确排序的排序算法，如果能够正确使用标准库，几乎不需要再编写这类代码。第 16 21 章将提供有关标准库功能的信息；**

****

### 4.6设计一个国际象棋程序

> 本节通过一个简单的国际象棋程序系统介绍 C++程序的设计方法。为提供完整示例，某些步骤用到了后面几章讲述的概念。为了解设计过程的概况，可现在就阅读这个示例，也可以在学完后面章节后返回头来学习；

****

#### 6.1需求

> **在开始设计前，应该弄清楚对于程序功能和性能的需求。理想情况下，这些需求应该是以需求规范(requirements specification)形式给出的文档。**国际象棋程序的需求应该包含下列类型的规范，当然实际的需求规范应该比下面的内容更详细，条目更多：  
>
> - 程序支持标准的国际象棋规则。  
> - 程序提供基于文本的界面。  
>   - 程序以纯文本形式提供棋盘和棋子。  
>   - 玩家通过输入代表位置的数字在棋盘上移动棋子。  

****

#### 6.2设计步骤

> 1. 将程序分割为子系统；
>
> ![image-20240209140908334](https://s2.loli.net/2024/02/09/qbDRgpxnCzajXHt.png)
>
> ![image-20240209141005292](https://s2.loli.net/2024/02/09/rjV8JxOfXuDvcnk.png)
>
> 2. 选择线程模型；
>
> 3. 指定每个子系统的类层次结构；
>
> ![image-20240209141103026](https://s2.loli.net/2024/02/09/fO4uYkTSscHUZzA.png)
>
> ![image-20240209141119716](https://s2.loli.net/2024/02/09/gpsT2wZOGFe3tRl.png)
>
> 4. 指定每个子系统的类、数据结构、算法和模式；
>
> ![image-20240209141142275](https://s2.loli.net/2024/02/09/5S8QorDW7spEtPF.png)
>
> ![image-20240209141207029](https://s2.loli.net/2024/02/09/ti56uaqJngcwSpR.png)
>
> 5. 为每个子系统指定错误处理；
>
> ![image-20240209141229352](https://s2.loli.net/2024/02/09/J9yieATowx4p3mg.png)

****

### 4.7本章小结

> 本章介绍了专业的 C++设计方法。软件设计是任何编程项目中重要的第一步。你还学习了使得设计变得困难的一些 C++特性，包括 C++关注的面向对象、庞大的功能集和标准库、编写通用代码的工具。这些信息可让程序员更好地处理 C++设计；
>
> 本章介绍了两个设计主题：抽象和重用。抽象(或将接口与实现分离)的概念贯穿全书，所有的设计工作都应该以此为指导方针。重用的概念(无论是代码还是设计)在实际项目和本书中经常会出现。C++设计应该包含代码的重用(以库或框架的形式)以及思想和设计的重用(以技术和模式的形式)。 应该尽可能编写可重用的代码。此外还要记住权衡重用的优缺点和重用代码的特定方针，包括理解功能和限制、性能、许可证、支持模式、平台限制、原型和帮助资源。你还学习了性能分析和大 O 表示法。现在你已经理解了设计的重要性和基本的设计主题，并做好了学习本书第 Ⅱ 部分其余章节的准备。第 5 章将讲述在设计中使用 C++面向对象特性的策略；

****

## 第5章 —— 面向对象设计

> 本章讨论对象之间的不同关系，包括创建面向对象程序时可能遇到的陷阱，还将学习抽象原则如何与对象联系起来；
>
> 思考过程式编程或面向对象编程时，要记住的重要一点是：面向对象编程只是以不同的方式看待程序；

****

### 5.1过程化的思考方式

> 过程语言(例如 C) 将代码分割为小块，每个小块(理论上)完成单一的任务。如果在 C 中没有过程，所有代码都会集中在 main() 中。代码将会难以阅读，同事会恼火，这还是最轻的；
>
> 过程式编程思想，在大型应用程序中很难满足线性序列事件发生的条件，此外，过程思想对数据的表示没有任何说明。

****

### 5.2面向对象思想

> 与基于“程序做什么”的面向过程的编程不同，面向对象思想提出了另一种看待问题的方法：“模拟哪些实际的对象？”

****

#### 2.1类

> 类，将对象及其定义区分开来；
>
> 类，用来封装定义对象分类的信息；
>
> 类，通过特征将类实例化；
>
> 类与对象 <--类比--> 类型与对象

****

#### 2.2组件

> 本质上，组件与类相似，但是组件更小，更具体；

****

#### 2.3属性

> 属性，将一个对象与其他对象区分开来；
>
> 类的属性，由所有的类成员共享，而类的所有对象都有对象属性，但具有自身特定的值；

****

#### 2.4行为

> 行为，回答 “对象做什么？” 和 “能对对象作什么？”；
>
> 因此，许多功能性的代码从过程转移到类，通过建立某些行为的对象并定义对象的交互方式，OPP 以更丰富的机制将代码和代码的操作的数据联系起来。类的行为由类的方法实现；

****

#### 2.5综合考虑

> ![image-20240209150140169](https://s2.loli.net/2024/02/09/ZjrdzEie8GoLB7A.png)
>
> 不扯淡，学会 UML 就明白了；

****

### 5.3生活在对象世界里

> 彻底采用 OPP 范式 和 仅仅使用对象代表数据和功能的良好封装都不是佳境；
>
> 理想方法往往介于这两者之间；

****

#### 3.1过度使用对象

> 事无巨细地都转化为对象，这是要警惕的，因为完全没必要；

****

#### 3.2过于通用的对象

> 能包含太多种类对象的类，也是完全没有必要的，因为它自身几乎不含有任何信息，如 data、Media等；

****

### 5.4对象之间的关系

> 不同类具有共同的特征，至少看起来彼此有联系；
>
> 面向对象的语言提供了许多机制来处理对象之间的这种关系；
>
> 其中，主要有两种关系：“有一个(has a)” 和 “是一个(is a)”；

****

#### 4.1“有一个”关系

> “有一个”关系或聚合关系的模式是：A有一个B，或者A 包含一个B。在此类关系种，可以认为某个对象是另一个对象的一部分。

****

#### 4.2“是一个”关系(继承)

> “是一个”关系是面向对象编程中非常常见的的基本概念，因此有许多名称，包括派生(deriving)、子类(subclass)、扩展(extending)和继承(inheriting)。类模拟了现实世界包含具有属性和行为的对象这一事实，继承模拟了这些对象通常以层次方式来组织这一事实。“是一个”正说明了这种层次关系。
>
> 基本上，继承的模式是：A是一个B，或者A实际上与B非常相似——这可能比较棘手。
>
> A是B(的一种)，但是反过来B却不都是A；
>
> 当类之间具有“是一个”关系时，目标之一就是将通用功能放入基类(base class)，其他类可扩展基类。如果所有子类都有相似或完全相同的代码，就应该考虑将一些代码或全部代码放入基类。这样，可以在一个地方完成所需的改动，将来的子类可“免费”获取这些共享的功能。
>
> 1. **继承技术**
>
>    前面的示例非正式地讲述了继承中使用的一些技术。当生成子类时，程序员有多种方法将某个类与其父类(parent class)、基类或者超类(superclass)区分开来。可使用多种方法生成子类，生成子类实际上就是完成语句 A is a B that...的过程。
>
>    **添加功能：**
>
>    **派生类可在基类的基础上添加功能。**
>
>    **替换功能：**
>
>    **派生类可完全替代或重写父类的行为。当然，如果对基类的所有功能都进行替换，就可能意味着采用继承的方式根本就不正确，除非基类是一个抽象基类。抽象基类会强制每个子类实现未在抽象基类中实现的所有方法。无法为抽象基类创建实例，第 10 章将介绍抽象类。此处，略。**
>
>    **添加属性：**
>
>    **除了从基类继承属性以外，派生类还可添加新属性。**
>
>    **替换属性：**
>
>    **与重写方法类似，C++ 提供了重写属性的方法。然而，这样做通常是不合适的，因为这会隐藏基类的属性，例如，基类可谓具有特定名称的属性指定一个值，而派生类可给该属性指定另一个值。有关“隐藏”的内容，详见第 9 章。不要把替换属性的概念与子类具有不同属性值的概念混淆。**
>
> 2. **多态性和代码重用**
>
>    多态性(Polymorphism)指具有标准属性和方法的对象可互换使用。类定义就像对象和与之交互的代码之间的契约。根据定义，一个对象必须支持其类的属性和行为；
>
>    这个概念可以推广到基类。即，当 A 是 B 时，那么 A 对象必然支持 B 类的属性和行为；
>
>    多态性是面向对象编程的两点，因为多态性真正利用了继承所提供的功能。即，当 A 是 B 时，那么当遍历 B 执行某个特定操作，即使因为归属于不同的 A 但是都是 B，所以这一特定操作即使被重写，依旧会执行相应的特定改写后动作。这就是亮点——代码只告诉让 B 执行某个特定操作，但是不需要知道是哪种 A，即可根据自己的特定改写后代码执行此操作，不必告诉需要如何执行此操作；
>
>    除多态性外，使用继承还有一个原因，通常是为了复用，为了避免做重复的工作，而使得两个独立的类之间产生关联；

****

#### 4.3“有一个” 与 “是一个” 的区别

> 在现实中，“是一个” 与 “有一个” 两者是很好区分的，但是在代码中，有时候却显得不是那么明显；
>
> - 比如，在考虑一个标准哈希表时，每个键(数字)对应有一个值(量)，且当为一个已有值的键添加第二个值的时候，第一个值就会消失。
>
> - 因此，不难想象，如果创建一个类似哈希表但允许一个键有多个值的数据结构的用法(比如，保险公司一个家庭可能有多个名称对应同一个 ID)。这种数据结构非常类似于哈希表，因此可用某种方式使用哈希表功能。哈希表的键只能由一个值，但是这个值可以是任意类型的。除字符串外，这个值还可以是一个包含多键值的集合(例如，数组或列表)。当像已有 ID 添加新成员时，可将其添加入集合中。(示例见课本 p88)
>
> - 使用集合而不是字符串有些繁琐，需要大量重复代码。因此，最好再一个单独的类中封装多值功能，可将这个类叫做 MultiHush 。MultiHush 类的运行与 Hashtable 类似，只是背后将每个值存储为字符串的集合，而不是单个字符串。很明显，MultiHush 与 Hashtable 有某种联系，因为它依然可以使用哈希表存储数据。不明显的是，这是“是一个” 关系 还是 “有一个” 关系？
> - 先考虑 “是一个” 关系，假定 MultiHush 是 Hashtable 的派生类，它必须重写在表中添加任何项的行为，从而既可创建集合添加新元素又可检索已有集合并添加新元素。此外，还必须重写检索值的行为。例如，可将给定键的所有值集中到一个字符串中。这好像是一种相当合理的设计。即使**派生类重写了基类的所有方法**，也**仍可在派生类中使用原始行为**，从而使用基类的行为。  
> - 再考虑 “有一个” 关系，MultiHush 属于自己的类，但是包含了 Hushtable 对象，这个类的接口可能与 Hashtable 非常相似，但并不需要相同。在幕后，当用户向 MultiHash 添加项时，会将这个项封装到一个集合并送入 Hashtable 对象。  
>
> ![image-20240218121232851](https://s2.loli.net/2024/02/18/UfmhM759GdNRJby.png)
>
> - 那么，哪个方案是正确的？没有明确的答案，笔者的一个朋友认为这是“有一个”关系，他编写了一个MultiHash 类供产品使用。主要原因是允许修改公开的接口，而不必考虑维护哈希表的功能。例如，将图 5.7 中的 get 方法改成 getAlL 以清楚表明将获取 MultiHash 中某个特定键的所有值。此外，在“有一个”关系中，不需要担心哈希表的功能会渗透。例如，如果 Hashtable 类提供了获取值的总数的方法，只 MultiHash 不重写这个方法，就可以用这个方法报告集合的项数。  
>
> ![image-20240218121948463](https://s2.loli.net/2024/02/18/giRbqMPjYKXTlZS.png)
>
> ![image-20240218122011286](https://s2.loli.net/2024/02/18/92n1mzrV6N3PUhv.png)
>
> - 反对“是一个”关系的理由在这种情况下非常有力。LSP(Liskov Substitution Principle, 里氏替换原则)可帮助从“是一个”和“有一个”关系中选择。这个原则指出，你应当能在不改变行为的情况下，用派生类替代基类。将这个原则应用于本例，则表明应当是“有一个”关系，因为你无法在以前使用 Hashtable 的地方使用MultiHash 否则，行为就会改变。例如，Hashtable 的 insert。方法会删除映射中同一个键的旧值，而 MultiHash 不会删除此类值。
> - 因此，推荐使用 “有一个” 关系，而不是 “是一个” 关系。
> - 注意，这里使用 Hashtable 和 MultiHash 说明了“有一个”和“是一个”关系的不同之处。在代码中，建议使用标准 Hashtable 类，而不是自己写 一个。C++ 标准库中提供了 unordered m 类，用来代替 Hashtable, 此外还提供了 unordered_multimap 类，用来代替 MultiHash 类。第 17 章将讨论这两个标准类。  

****

#### 4.4not-a 关系

> 当考虑类之间的关系时，应该考虑类之间是否真的存在关系。不要把对面向对象设计的热情全部转换为许多不必要的类/子类关系。  
>
> 当实际事物之间存在明显关系，而代码中没有实际关系时，问题就出现了。0PP(面向对象)层次结构需要模拟功能关系，而不是人为制造关系。图 5-8 显示的关系作为概念集或层次结构是有意义的，但在代码中并不能代表有意义的关系。  
>
> ![屏幕截图 2024-02-18 124133](https://s2.loli.net/2024/02/18/cgRlI9OmYr3K5Tb.png)避免不必要继承的最好方法是首先给出大概的设计。为每个类和派生类写出计划设置的属性和行为。如果发现某个类没有自己特定的属性或方法，或者某个类的所有属性和方法都被派生类重写，只要这个类不是前面提到的抽象基类，就应该重新考虑设计。

****

#### 4.5层次结构

> 类根据层次使得各个派生共性更系统化，另外强调，根据不同划分方式，会得到不同的派生方式，得到不同的层次结构。因此，要点——在代码中，需要平衡现实关系和共享功能关系。
>
> 即使在现实中的两种事物紧密联系，但是在代码中也可能没有任何关系，因为它们没有共享功能。
>
> 优秀的面向对象层次结构优点：
>
> - 使用类之间存在有意义的功能关系；
> - 将共同的功能放入基类，从而支持代码重用；
> - 避免子类过多地重写父类的功能，除非父类是一个抽象类；

****

#### 4.6多重继承

> 到目前为止，所有示例都是单一继承链，换句话说，是一种类似于森林的结构。但这不是必需的，在多重渲染中，一个类可以又多个基类。
>
> ![image-20240218131129845](https://s2.loli.net/2024/02/18/fSncVWwZ2PKdCTY.png)
>
> 考虑用户界面环境，假定用户可单击某张图片。这个对象好像既是按钮又是图片，因此其实现同时继承了 Image 类和 Button 类，如图 5.12所示。
>
> ![image-20240218131236153](https://s2.loli.net/2024/02/18/sWDZKbBpfygvmqE.png)
>
> 某些情况下多重继承可能很有用，但必须记住它也有很多缺点。许多程序员不喜欢多重继承，C++明确支持这种关系，而 Java 语言根本不予支持，除非通过多个接口来继承(抽象基类)。批评多重继承是有原因的：
>
> - 首先，用图形表示多重继承十分复杂。如图 5-11 所示，当存在多重继承和交叉线时，即使简单的类图也会变得非常复杂。类层次结构旨在让程序员更方便地理解代码之间的关系。而在多重继承中，类可有多个彼此没有关系的父类。将这么多类加入对象的代码中，能跟踪发生了什么吗？
> - 其次，多重继承会破坏清晰的层次结构。  
> - 最后，多重继承的实现很复杂。  
>
> 其他语言取消多重继承的原因是：通常可以避免使用多重继承。在控制某种项目设计时，重新考虑层次结构，通常可以避免引入多重继承。

****

#### 4.7混入类

> **混入(mix-in) 类** 代表类之间的另一种关系。在 C++中，混入类的语法类似于多重继承，但语义完全不同。混入类回答“**这个类还可以做什么**”这个问题，**答案经常以 “-able” 结尾**。**使用混入类，可向类中添加功能，而不需要保证是完全的“是一个”关系。**可将它当作一种**分享(share-with)关系**。  
>
> 混入类经常在用户界面中使用。可以说 Image 能够单击(Clickable), 而不需要说 PictureButton 类既是 Image又是 Button。桌面上的文件夹图标可以是一张可拖动(Draggable)、可单击(Clickable)的图片(Image)。软件开发人员总是喜欢弄一大堆有趣的形容词。  
>
> 当考虑类而不是代码的差异时，混入类和基类的区别还有很多。因为范围有限，混入类通常比多重层次结构容易理解。Pettable 混入类只是在己有类中添加了一个行为，Clickable 混入类或许仅添加了“按下鼠标”和 “释放鼠标”行为。此外，混入类很少会有庞大的层次结构，因此不会出现功能的交叉混乱。第 28 章将详细介绍混入类。  

****

### 5.5抽象

> 第 4 章讲述了抽象的概念一将实现与访问方式分离的概念。前面说过，抽象是一种优秀的思想，也是面向对象设计的基础。  

****

#### 5.1接口与实现

> **抽象的关键在于有效分离接口与实现。**实现是用来完成任务的代码，接口是其他用户使用代码的方式。在 C 中，描述库函数的头文件是接口，在面向对象编程中，类的接口是公有属性和方法的集合。优秀的接口只包含共有行为，类的属性/变量绝不应该公有，但是可以通过公有方法公开，这些方法被称为获取器和设置器。

****

#### 5.2决定公开的接口

> 编写接口又很多理由。在编写代码前，甚至在决定要公开的功能之前，必须理解接口的目的。
>
> 当设计类时，其他程序员如何与你的对象交互是一个问题。**在 C++中，类的属性和方法可以是公有的(public)、受保护的(protected)和私有的(private)**。 将属性或行为设置为 **public 意味着其他代码可以访问它们。protected 意味着其他代码不能访问这个属性或行为，但子类可以访问。private 是最严格的控制，意味着不仅其他代码不能访问这个属性或行为，子类也不能访问，只有自身可以将属性转化为行为，然后根据行为来体现属性，最后只能使用自身来实现类的功能**。注意，**访问修饰符在类级别而非对象级别发挥作用。例如,这意味着类的方法可访问同一个类的其他对象的私有属性或私有方法。**  
>
> **应用程序编程接口(API)**
>
> API 是一种外部可见机制，用于在其他环境中扩展产品或者使用其功能。如果说内部的接口是契约，那么API 更接近于雕刻在石头上的法律。一旦用户开始使用你的 API, 哪怕他们不是公司的员工，他们也不希望 API发生改变，除非加入帮助他们的新功能。在交给用户使用之前，应该关心 API 的设计，并与用户进行商谈。  
>
> 设计 API 时主要考虑易用性和灵活性。由于接口的目标用户并不熟悉产品内部的运行方式，因此学习使用API 是一个循序渐进的过程。毕竟，公司向用户公开这些 API 的目的是想让用户使用 API。如果使用难度太大, API 就是失败的。灵活性常与此对立，产品可能有许多不同的用途，我们希望用户能使用产品提供的所有功能。然而，如果一个 API 让用户做产品可做的任何事，那么它肯定会过于复杂。   
>
> 正如编程格言所说，“好的 API 使容易的情况变得更容易，使艰难的情况变得容易”。也就是说，API 应该很容易使用。大多数程序员想要做的事情就是访问。然而，**API 应该允许更高级的用法**，因此在罕见的复杂情况和常见的简单情况之间做出折中是可以接受的。
>
> **工具类或库**
>
> **通常，程序员的任务是设计某些特定的功能，供应用程序中的其他部分使用，这可能是一个随机数库或日志类**。在此情况下比较容易确定接口，因为要公开大多数功能或全部功能，**理想情况下不应该给出与实现有关的内容。**通用性是需要考虑的重要问题，由于类或库是通用的，因此在设计中应该考虑设置可能的用例集。
>
> **子系统接口**
>
> **你可能设计程序中两个主要子系统之间的接口，例如访问数据库的机制。**在此情况下，将接口与实现分离异常重要，其他程序员可能会在你的实现完成之前依靠你的接口编写他们的实现。当处理子系统时，首先考虑子系统的主要目的是什么。一旦定义子系统的主要任务，就可以考虑子系统的具体用法以及如何将它展示给代码的其他部分。试着从他人的角度考虑问题，而不要身陷实现的细节而不能自拔。
>
> **组件接口**
>
> **我们定义的大多数接口可能都小于子系统接口或 API。组件是在其他代码中会用到的类。**这些情况下，当接口逐渐增大，变得难以控制时，就可能会出现问题。哪怕这些接口是供自己使用的，也要当成不是。与子系统接口类似，此时应该考虑每个类的主要目的，不要公开对这个目的没有贡献的功能。
>
> **在设计接口时，应该考虑将来的需求。你会在这个设计上花费数年时间吗？如果是这样，就可能需要使用插件架构，从而留出扩展空间。能够确定人们使用接口的目的与当初设计的目的相同吗？与他们交流，以更好地理解他们的使用情况。否则以后就要重写接口，或者更糟糕的是，以后可能需要不时地添加新功能，使接口变得凌乱不堪。要小心！如果将来的用途不明，就不要设计包含一切的日志类，因为这样做会不必要地将设计、实现和公有接口复杂化 。**

****

#### 5.3设计成功的抽象

> 经验和重复是良好抽象的基础。只有经历过多年编写代码和使用抽象，才能真正地设计良好的接口。也可通过标准设计模式，重用己有的、设计优秀的抽象代码，利用他人多年编写和使用抽象的经验。当遇到其他抽象时，试着记住什么可行，什么不可行。
>
> 良好的抽象意味着接口只有公有行为。所有代码都应该在实现文件而不是类定义文件中。这意味着包含类定义的接口文件是稳定的，不会改变。与此对应的技术称为私有实现习语或 pimpl idiom, 详见第 9 章。    
>
> 小心单一类的抽象。如果编写的代码非常深奥，应该考虑用其他类配合主接口。例如，如果公开一个完成数据处理的接口，那么还要考虑编写一个结果对象，从而提供一种简单的方法来查看并说明结果。  
>
> **始终将属性转换为方法。**换句话说，不要让外部代码直接操作类的数据。不要让一些粗心或怀有恶意的程序员把兔子对象的高度设置为负数，为此可对“设置高度”方法进行边界检查。  

****

### 5.6本章小结

> 层次清晰化，属性方法化，使用 “有一个” 而非 “是一个”，“是一个” 关系变多，会使得基类的概念模糊，耦合性过大)；

****

## 第6章 —— 设计可重用代码

> 在程序中，重用库和其他代码是一项重要的设计策略。然而，这只是重用策略的一半，另外一半是设计并编写在程序中的可重用代码。你可能己经发现，设计良好的库和设计不当的库之间存在显著差别。设计良好的库用起来很舒服，而设计糟糕的库会让人觉得非常难受，以至于放弃使用，自己编写代码。**无论是编写供其他程序员使用的库，还是仅仅设计某个类层次结构，在设计代码时都应该考虑重用。你永远不知道后续项目什么时候会用到相似的功能段。**  
>
> 第 4 章介绍了重用的设计主题，并阐述了如何通过在设计中整合库和其他代码来应用这个主题。**本章讨论重用的另一方面：设计可重用代码。**这一内容建立在第 5 章介绍的面向对象设计原则基础之上，并引入了新的策略和指导方针。

****

### 6.1重用哲学

> 应该设计自己和其他程序员都可以重用的代码。这条规则不仅是用于专供其他程序员使用的库或框架，还适用于程序中用到的类、子系统和组件。
>
> 牢记格言：
>
> - 编写一次，经常使用；
> - 尽量避免代码重复；
> - DRY(Don't Repeat Yourself)；
>
> 原因如下：
>
> - 代码不大可能只在一个程序中使用，代码总会被重用；
> - 重用设计可节省时间和金钱，减少过多重复性工作；
> - 团队中的其他程序员必须能够使用你编写的代码，因为大部分工程都不可能独自完成，因此，重用设计可以称为协作编程；
> - 缺乏重用性会导致代码重复，代码重复会导致维护困难，因为一旦发现 bug 那么就必须在所有地方都进行改变，这很容易出错；
> - 你自己是主要受益人，因为经验丰富的程序员永远不会扔掉代码，随着时间推移，他们会创建个人工具库，你永远不会事先知道要在什么时候使用到类似的代码；
>
> 警告：
>
> ​	公司员工设计或编写代码时，通常拥有知识产权的时公司而不是员工本人。当员工终止劳动合同时，保留设计或代码的副本通常是违法的；

****

### 6.2如何设计可重用代码

> 可重用代码目标：
>
> 1. 代码必须通用，太过特定的组件很难被重用；
> 2. 代码应当易于使用，而不需要花费大量时间理解他们的接口或功能；
>
> 将库“递交”给客户的方法也很重要。可以源代码形式递交，这样客户只需要将源代码整合到他们的项目中。另一种选择是递交一个静态库，客户可以将该库连接到他们的应用程序中，也可以给 Windows 客户递交一个动态链接库(DLL)，给 Linux 客户递交一个共享对象(.so)。这些递交方式会对编写库的方式施加额外限定；
>
> 注意：
>
> **本章用术语 “客户”代表使用接口的程序员。**不要将客户与使用程序的 “用户”混淆。本章还使用了短语“客户代码”，这代表使用接口的代码。
>
> 重中之重：
>
> 重用代码的本质是——抽象；
>
> 抽象将代码分为接口和实现，因此设计可重用代码会关注这两个关键领域；实现代码，是重用的实现；只要理解代码接口，即可使用；

****

#### 2.1使用抽象

> 抽象的优点：
>
> - 通过分离实现和接口，首先，使得客户只需要明白接口的用途就可以使用代码；而程序员在维护时，不需要修改接口，因此不需要征求客户的同意，只需改变代码本身就可以；如果使用动态链接库(DLL)，甚至不需要重新生成可执行文件；
>
> - 总之，获得好处的是因为作为库的编写者，可在接口明确指定希望的交互方式和支持方式的功能；接口与实现的明确分离可以杜绝用户以不希望的方式使用库，而这些方式可能导致意料之外的行为和 bug。
>
> - 当在设计界面时，不要向客户公开实现细节；
>
> - **有时为将某个接口返回的信息传递给其他接口，库要求客户代码保存这些信息。这一信息有时叫作句柄(handle), 经常用来跟踪某些特定的实例，这些实例调用时的状态需要被记住。如果库的设计需要句柄，不要公开句柄的内部情况。可将句柄放入某个不透明类，程序员不能“直接访问这个类的内部数据成员，也不能通过公有的获取器或设置器来访问”。**
>
>   > 这种设计决策有以下目的和优势：
>   >
>   > 1. **封装内部实现：** 将句柄放入一个不透明类中，允许库在内部更改实现细节而不会影响客户代码。客户代码只需要与句柄进行交互，而不需要了解其内部结构。
>   > 2. **隐藏实现细节：** 隐藏句柄的内部情况可以防止客户代码直接访问或修改句柄的状态。这种信息隐藏有助于维护库的一致性和稳定性，因为客户代码无法非法地操作句柄。
>   > 3. **提高安全性：** 不透明类的使用可以提高安全性，防止客户代码意外地破坏库内部的状态。通过限制对内部成员的访问，可以减少潜在的错误和不当操作。
>
> - 不要要求客户代码改变句柄内部的变量。一个不良设计的示例是，一个库为了启用错误日志，要求设置某个结构的特定成员，而这个结构所在的句柄本来应该是不透明的

****

#### 2.2构建理想的重用代码

> 1. **避免组合不相干的概念或者逻辑上独立的概念，当设计组件时，应该关注单个任务或一组任务，即“高聚合”， 也称为 SRP(Single Responsibility Principle,单一责任原则)。** 不要将无关概念组合在一起，例如随机数生成器和 XML 解析器。  
>
>    **即使设计的代码并不是专门用来重用的，也应该记住这一策略。**整个程序本身很少会被重用，但是程序的片段或子系统可直接组合到其他应用程序中，也可以在稍作变动后用于大致相同的环境。因此，设计程序时，应将逻辑独立的功能放到不同的组件中，以便在其他程序中使用。其中的每个组件都应当有明确定义的责任。
>
>    **这个编程策略模拟了现实中可互换的独立部分的设计原则。**例如，可编写一个 Car 类，在其中放入引擎的所有属性和行为。但引擎是独立组件，未与小汽车的其他部分绑定。可将引擎从一辆小汽车卸下，安装在另一辆小汽车中。**合理的设计是添加一个 Engine 类，其中包含与引擎相关的所有功能。此后，Car 实例将包含 Engine实例。**
>
>    **将程序分为逻辑子系统  ，将子系统设计为可单独重用的分立组件，即“低耦合”。** 每个子系统都应该遵循抽象原则。将每个子系统当作微型库，必须为其提供稳定的、便于使用的接口。即使你是使用这个微型库的唯一程序员，设计良好的接口和从逻辑上分离不同功能的实现也是有益的。  
>
>     **用类层次结构分离逻辑概念，除了将程序分为逻辑子系统以外，在类级别上应该避免将无关概念组合在一起。**  **总结：组织内部高聚合，组件之间低耦合；**
>
>    用聚合分离逻辑概念。第 5 章讨论的聚合(Aggregation)模拟了“有一个”关系：为完成特定功能，对象会包含其他对象。当不适合使用继承方法时，可以使用聚合分离没有关系的功能或者有关系但独立的功能。
>
>    例如，假定要编写一个 Family 类来存储家庭成员。显然，树数据结构是存储这些信息的理想结构。不应该把树数据结构的代码整合到 Family 类中，而是应该编写一个单独的 Tree 类。然后 Family 类可以包含并使用 Tree实例。用面向对象的术语来说，Family 有一个 Tree。通过这种方法，可以在其他程序中方便地重用树数据结构。
>
>    消除用户界面的依赖性
>
>    如果是一个操作数据的库，就需要将数据操作与用户界面分离开来。这意味着对于这些类型的库，不应该假定哪种类型的用户界面会使用库，因此不应该使用 cout、cerr、cin、stdout、stderr 或 stdin, 因为如果在图形用户界面的环境下使用库，这些概念将没有意义。例如，基于 Windows GUI 的应用程序通常不会有任何形式的控制台 I/O。即使库只用于基于 GUI 的程序，也不应该向最终用户弹出任何类型的消息窗口或者其他类型的提示，这是客户代码需要做的事情。这种类型的依赖不仅降低了重用性，还阻止了客户代码正确响应错误以及在后台自动处理错误。
>
> 以下是一些实现这一目标的常见策略：
>
> 1. **使用回调函数：** 允许客户代码提供回调函数，这些函数用于处理特定事件或错误。例如，库可以定义一些回调函数，如处理错误、进度更新或异步操作完成等。客户代码负责实现这些回调函数，以便在适当的时候进行响应。
> 2. **定义接口或抽象类：** 将用户界面相关的操作定义为接口或抽象类，使得客户代码可以根据自己的需要实现这些接口。这种方式使得库不依赖于具体的用户界面实现，而只依赖于接口。
> 3. **使用事件机制：** 如果库支持事件，客户代码可以注册感兴趣的事件处理器。这样，库可以触发事件，而客户代码则负责处理这些事件，例如更新界面或处理错误。
> 4. **提供配置选项：** 允许客户代码通过配置选项来自定义库的行为，而不是在库中直接使用特定的用户界面元素。例如，客户代码可以通过设置配置选项来指定日志输出的目标，而不是直接使用 cout 或者其他特定的输出流。
> 5. **避免直接的用户界面代码：** 在库中避免直接调用与用户界面相关的库或函数。将这些调用封装在特定的接口或者类中，使得用户界面的具体实现对于库来说是可替换的。
> 6. **提供适配器模式：** 如果必须在库中处理用户界面相关的逻辑，可以考虑使用适配器模式。通过定义一个接口，允许不同的用户界面实现提供适配器，以便库可以与不同的用户界面进行交互。
>
> 第 4 章介绍的 Model-View-Controner(MVC)范型是一种将数据存储和数据显示分开的著名设计模式。在这种范型中，模型可放在库中，客户代码可提供视图和控制器。
>
> 2.**对泛型数据结构和算法使用模板：**  
>
> ​	**C++模板的概念允许以类型或类的形式创建泛型结构。**例如，假定为整型数组编写了代码。如果以后要使用 double 数组，就需要重写并复制所有代码。模板的概念将类型变成一个需要指定的参数，这样就可以创建一个适用于任何类型的代码体。模板允许编写适用于任何类型的数据结构和算法。
>
> 最简单的示例是std::vector类,这个类是C++标准库的一部分。为创建整型的 vector, 可编写 std::vector<int>;,为创建 double 类型的 vector, 可编写 std::vector<double>。模板编程通常功能强大，但非常复杂。幸运的是，可以创建简单的、使用类型作为参数的模板用例。第 12 和 22 章讲述编写自定义模板的技巧，本节讨论模板的一些重要设计特征。
>
> **只要有可能，就应该设计泛型(而不是局限于某个特定程序的)数据结构和算法。**不要编写只存储 book 对象的平衡二叉树结构，要使用泛型，这样就可以存储任何类型的对象。通过这种方法，可将其用于书店、音乐商店、操作系统或需要平衡二叉树的任何地方。这个策略是标准库的基础。标准库提供可用于任何类型的泛型数据结构和算法。
>
> **模板优于其他泛型程序设计的原因：**
>
> 1. void* (用于不指定类型的指针)，类型不安全，，欸有类型检测，无论删除还是转换都存在一定风险；
> 2. 为特定类编写数据结构，通过多态性(统一操作作用于不同对象，行为不同)，这个类的所有子类都可以存储在这个结构中。Java 将这种方法发挥到极致，指定所有的类都从 Object 类直接或间接派生。**早期 Java 版本的容器存储 Object, 因此可以存储任何类型的对象。然而，这种方法也不是真正类型安全的。从容器中删除某个对象时，必须记得其真实的类型，并向下转换(down-cast)为合适的类型。向下转换意味着转换为类层次结构中更具体的类，即沿着类层次结构“向下”转换。**  
>
> **模板并不是完美的：**
>
> 1. 首先，语法较为迷惑；
> 2. 其次，模板要求相同类型的数据节后，在一个结构中只能存储相同的数据类型。这就是说，一个模板创建出的数据结构，只能用于存储同种类型。这种限制是由模板的类型安全性质决定的。从 C++17开始，可以采用一种标准方式来绕过这种“相同类型”限制。可编写数据结构来存储 std::variant 或 std::any 对象。std::any 对象可存储任意类型的值，std::variant对象可存储所选类型的值。第 20 章将详细介绍这两种对象以及它们的变体。  
>
> 模板与继承的区别：
>
> 1. **如果打算为不同的类型提供相同的功能，则使用模板。**例如，如果要编写一个适用于任何类型的泛型排序算法，应该使用模板。如果要创建一个可以存储任何类型的容器，应该使用模板。关键的概念在于模板化的结构或算法会以相同方式处理所有类型。但是，如有必要，可给特定的类型特殊化模板，以区别对待这些类型。模板特殊化参见第 12 章  
> 2. **当需要提供相关类型的不同行为时，应该使用继承。**例如，如果要提供两个不同但类似的容器，例如队列和优先队列，应该使用继承；
> 3. 把二者结合起来。可以编写一个模板基类，此后从中派生一个模板化的类。(这也就叫做抽象，抽象出来这个，然后给出接口)第 12 章将详细讲述模板语法；
>
> **提供适当的检测和安全措施：**
>
> 第一种方法是按契约设计，这表示函数或类的文档是契约，详细描述客户代码的作用以及函数或类的作用。按契约设计有三个重要方面：前置条件(precondition)、后置条件(postcondition)和不变量(invariant)。前置条件列出为调用函数或方法，客户代码必须满足的条件。后置条件列出完成执行后，函数或方法必须满足的条件。最后，不变量列出在函数或方法执行期间，必须一直满足的条件；
>
> > 这种方法常用于标准库。例如，std::vector 定义了一个契约，以使用数组记号获取 vector 中的某个元素。契约指定，vector 不进行边界检查，这是客户代码的责任。也就是说，使用数组记号从 vector 获取元素的前置条件对于给定索引是有效的。这样可提高客户代码的性能，因为客户代码知道其索引在指定范围内。vector 还定义了 at()方法，用来获取进行边界检查的特定元素。所以客户代码可以选择是使用不带边界检查的数组记号，还是使用带有边界检查的 at()方法。  
>
> 第二种方法是以尽可能安全的方式设计函数和类。这个指导方针的最主要特征就是在代码中执行错误检测。例如，如果随机数生成器要求一个处于指定范围的种子，不要相信用户一定会正确地传递一个有效的种子。应该检测传递过来的值，如果无效，就拒绝调用。前面讨论的 at() 方法是另一个考虑安全的示例。如果用户提供了无效索引，该方法将抛出异常。  
>
> 有些技巧和语言特征有助于编写安全代码，有助于在程序中加入检测和安全措施。**首先，可返回错误代码或特定的值(例如 fhlse 或 nullptr), 或者抛出异常，以提醒客户代码发生了错误，第 14 章将详细讲述异常。****其次,为编写安全代码，可使用智能指针管理动态分配的内存等资源。从概念上说，智能指针是指向动态分配的资源的指针，当超出作用域时会自动释放资源。**第 1 章讨论过智能指针。
>
> **扩展性:**
>
> 设计的类应当具有扩展性，可通过从这些类派生其他类来扩展它们。不过，设计好的类应当不再修改；也就是说，其行为应当是可扩展的，而不必修改其实现。这称为开放/关闭原则(Open/Closed Principle, OCP)。
>
>   例如，假设开始实现绘图应用程序。第一个版本只支持绘制正方形，设计中包含两个类：Square() 和 Renderer0 前者包含正方形的定义，如边长；后者负责绘制正方形。得到的代码如下：
>
> ```c++
> class Square
> {
> 	// Details not important for this example.
> };
> 
> class Renderer
> {
> public:
> 	void render(const vector<Square>& squares);
> };
> 
> void Renderer::render(const vector<Square>& squares)
> {
> 	for (auto& square : squares)
> 	{
> 		// Render this square object.
> 	}
> }
> ```
>
> 接下来，添加对绘制圆的支持，因此创建 Circle 类：
>
> ```c++
> class Circle
> {
> 	// Details not important for this example.
> };
> ```
>
> 下面给出一种愚蠢的 render() 解决方案:
>
> ```c++
> void Renderer::render(const vector<Square>& squares,
> 	const vector<Circle>& circles)
> {
> 	for (auto& square : squares)
> 	{
> 		// Render this square object.
> 	}
> 	for (auto& circle : circles)
> 	{
> 		// Render this circle object.
> 	}
> }
> ```
>
> 此时的设计应当使用继承，虽然稍微超前，但是仍然给出，只需要理解其中的精妙，只需要知道 Square 从 Shape 类中派生即可：
>
> ```c++
> class Square : public Shape {};
> ```
>
> 下面使用继承语法的设计：
>
> ```c++
> class Shape
> {
> public:
> 	virtual void render() = 0;
> };
> 
> class Square : public Shape
> {
> public:
> 	virtual void render() override { /* Render square */ }
> 	// Other members not important for this example.
> };
> 
> class Circle : public Shape
> {
> public:
> 	virtual void render() override { /* Render circle */ }
> 	// Other members not important for this example.
> };
> 
> class Renderer
> {
> public:
> 	void render(const vector<shared_ptr<Shape>>& objects);
> };
> 
> void Renderer::render(const vector<shared_ptr<Shape>>& objects)
> {
> 	for (auto& object : objects)
> 	{
> 		object->render();
> 	}
> }
> /*看到这里没有这个多态，实在是优美，利用抽象把多态给搞出来，再利用抽象把将有特点的类从基类中派生出来，注意到没有 auto* 的使用，这是不是特别引人入胜，一下子把很多需要说的东西给解决了，而且是类型安全的，而且使用 const & 的常量引用方式，只能说结构实在是清晰*/
> 
> // 因为后面介绍了 DIP 这种比较高级的方式，下面给出这种写法(看后面，已经觉得这种方式不是很好了，下面有鲁棒的)：
> #include <iostream>
> 
> // 渲染器接口
> class Renderer
> {
> public:
> 	virtual void renderShape() = 0;
> };
> 
> // 具体的方形渲染器
> class SquareRenderer : public Renderer
> {
> public:
> 	virtual void renderShape() override
> 	{
> 		std::cout << "Rendering square." << std::endl;
> 		// 具体的方形渲染逻辑
> 	}
> };
> 
> // 具体的圆形渲染器
> class CircleRenderer : public Renderer
> {
> public:
> 	virtual void renderShape() override
> 	{
> 		std::cout << "Rendering circle." << std::endl;
> 		// 具体的圆形渲染逻辑
> 	}
> };
> 
> class Shape
> {
> public:
> 	// 通过渲染器接口实现依赖反转
> 	Shape(Renderer* renderer) : renderer(renderer) {}
> 
> 	// 渲染形状的方法
> 	void render()
> 	{
> 		renderer->renderShape();
> 	}
> 
> private:
> 	Renderer* renderer;
> };
> 
> int main()
> {
> 	// 创建具体的渲染器实例
> 	SquareRenderer squareRenderer;
> 	CircleRenderer circleRenderer;
> 
> 	// 创建具体的形状实例，并传入相应的渲染器
> 	Shape square(&squareRenderer);
> 	Shape circle(&circleRenderer);
> 
> 	// 渲染形状
> 	square.render();  // 输出：Rendering square.
> 	circle.render();  // 输出：Rendering circle.
> 
> 	return 0;
> }
> /*这样看上去是不是更 NB 了？这样使得依赖注入了*/
> /*我想强调的是：依赖注入(DIP)实现的是对功能的多态化处理，将类与类的功能分开，是向实现功能的特定类进行派生类注入，然后实现同一操作的多态化。所以，给出下面更好的方法。*/
> 
> // 理论角度上，下面这种方式也是可行的：
> #include <iostream>
> 
> // 渲染器接口
> class Shape
> {
> public:
> 	virtual void renderShape() = 0;
> };
> 
> // 具体的方形渲染器
> class Square : public Shape
> {
> public:
> 	virtual void renderShape() override
> 	{
> 		std::cout << "Rendering square." << std::endl;
> 		// 具体的方形渲染逻辑
> 	}
> };
> 
> // 具体的圆形渲染器
> class Circle : public Shape
> {
> public:
> 	virtual void renderShape() override
> 	{
> 		std::cout << "Rendering circle." << std::endl;
> 		// 具体的圆形渲染逻辑
> 	}
> };
> 
> class Render
> {
> public:
> 	// 通过渲染器接口实现依赖反转
> 	Render(Shape* shape) : shape(shape) {}
> 
> 	// 渲染形状的方法
> 	void render()
> 	{
> 		shape->renderShape();
> 	}
> 
> private:
> 	Shape* shape;
> };
> 
> /*这里我们看到了两种依赖方式：
> 	1.Shape 类依赖于 Renderer 接口(派生类为渲染器)：
> 优点：Shape 类可以直接依赖于渲染器接口，更加直观。添加新的形状时，只需创建一个新的实现了 Renderer 接口的类，而不需要修改 Shape 类。
> 缺点：Shape 类需要知道渲染器的存在，这可能在一些情况下被视为 Shape 类的责任过重，不够单一。
> 
> 	2.Render 类依赖于 Shape 接口(派生类为图形)：
> 优点：在这种情况下，Shape 类并不关心具体的渲染器是什么，只关心渲染的形状。这种设计更加符合单一责任原则，因为每个类都有一个清晰的责任。
> 缺点：可能存在大量的渲染器类，每个都需要实现 renderShape() 方法。这种情况下，添加新的形状可能需要创建一个新的渲染器类。
> 
> 在实际应用中，选择哪种方法通常取决于具体的系统需求和设计目标。
> 如果系统中存在多种形状和多种渲染器，并且它们的变化原因不同，那么第一种方法可能更为合适。
> 如果系统中形状的变化和渲染器的变化相对独立，那么第二种方法可能更为直观和灵活。
> 嗯，事实上，第二种更符合最上面没有 DIP 化的形式，但是明显第一种也是可行的。虽然，我也认为第一种是极其不合适的，因为它作为 Shape 类太过“随便”了！仿佛是个图形都可以触发，这显得很轻浮，可以到处沾花惹草，也就是换成人话说，耦合性太强，责任太强。真的不如后面的第二个向 Render 中注入 Shape 的方式；
> */
> ```
>
> 现在，设想一下，我们要添加一个新形状类型，那么只需要对基类 Shape 进行派生就可以了，而不需要对 render() 方法进行修改，这完全是多态的体现，这是一种动态的多态，也叫运行时多态。(PS: 另外一种静态多态，多被体现为函数的复写)。因此我们可以说，多态是拓展是开放的，对修改是关闭的。
>
> 我来解释一下，什么叫做 OPC:
>
> 开放：开放对新派生类的扩充，对其属性和行为的规范；
>
> 关闭：关闭对行为(可重用代码)的修改，利用抽象派生实现；

****

#### 2.3设计有用的接口

> 没有优美的接口，实现再美好，都是扯淡。
>
> 良好接口有利于重用。
>
> 创新从实现上入手，不要对接口又什么创新想法，那只会变得很蠢；
>
> 回到 C++, 开发的接口应该遵循 C++程序员熟悉的标准。例如，C++程序员希望构造函数初始化对象，析构函数清理对象。当设计类时，应该遵循这个标准。如果要求程序员调用initialize。方法初始化对象，调用 cleanup。方法清理对象，而不是将这些功能放在构造函数和析构函数中，就会让所有用户感到迷惑。因为这个类与其他 C++类的行为不同，程序员需要花费更长的时间学习如何使用这个类，并可能由于忘记调用initialize。或 cleanup。方法而出错。  
>
> **注意：**
>
> ​	**设计从使用者角度进行考虑；**
>
> 运算符重载可以作为一种帮助为对象开发易于使用的接口的语言特性；但不要使用过度，那样很笨拙，而且反人性，之后会详细讨论；
>
> **不要省略必需的功能：**
>
> **该策略分为两部分：**
>
> - 尽量包括用户所有的可能行为，虽然不可能完美，但是代码本身就没有完美，只有优雅；
> - 在实现中尽量包含多的功能，不要要求客户端代码指定在实现中已经知道的信息(例如，库需要一个临时文件，不要让库的客户指定路径，他们应当不必担心库使用什么文件，应该用其他方法决定合适的临时文件路径)；	
>
> **走向极端：**
>
> 部分程序员认为需要完美，比如曾经的我，但是现在我们认识到，优雅比完美更好。上面两个策略任何一个走向极端都是糟糕的事情，那会使得接口混乱至极；
>
> 从本质上说，设计简洁接口的思想看似简单，但是那是主观的规则，实践起来其实相当困难；这个规则基本上是主观的：由你决定什么是必需的，什么不是。当然，当这个判断出错时，客户一定会通知你。  
>
> **提供文档和注释：**
>
> 这不是当前的重点，我一带而过，这部分单独学习；
>
> 无论接口多么便于使用，都应该提供使用文档。如果不告诉程序员如何使用，不能期望他们会正确使用库。应该将库或代码称为供其他程序员使用的产品。产品应该带有说明其正确用法的文档。
>
> 提供接口文档有两种方法：接口自身内部的注释和外部的文档。应该尽量提供这两种文档。大多数公开的API 只提供外部文档：许多标准 UNIX 和 Windows 头文件中都缺少注释。在 UNIX 中，文档形式通常是名为man pages 的在线手册。在 Windows 中，集成开发环境通常附带文档。
>
> 虽然多数 API 和库都取消了接口本身的注释，但我们认为，这种形式的文档才是最重要的。绝不应该给出一个只包含代码的“裸”头文件。即使注释与外部文档完全相同，具有友好注释的头文件也比只有代码的头文件看上去舒服，即使最优秀的程序员也希望经常看到书面语言。
>
> 有些程序员使用工具将注释自动转换为文档，第 3 章详细讨论了这一技术。(但我还是没学)
>
> **无论提供注释、外部文档还是二者都提供，文档都应该描述库的行为而不是实现。行为包括输入、输出、错误条件和处理、预定用法和性能保障。**例如，描述生成单个随机数的调用的文档应该说明这个调用不需要参数，返回一个预先指定范围的整数，还应该列出当出现问题时可能抛出的所有异常。文档不应该详细解释实际生成数字的线性同余算法，在接口注释中提供太多的实现细节可能是接口开发中最常见的错误。适用于库维护者(而不是客户)的注释会破坏接口和实现的良好分离，许多开发人员都见到过这种情况。当然，内部的实现也应该有文档记录，只是不要把它作为接口的一部分公开。第 3 章详细讨论了如何在代码中恰当地使用注释。  
>
> **设计通用接口：**
>
> **提供执行相同功能的多种方法：**
>
> 例如：std::vector 提供了两种方法来访问特定索引处的元素。可使用at()方法，该方法执行边界检查；也可使用 operator口方法，该方法不执行边界检查。如果知道索引是有效的，那么使用 operator口方法更合适，这样可省去使用 at()方法时的边界检查开销；
>
> 注意，这一策略应该当作接口设计中“整洁”规则的例外。有些情况下这个例外是恰当的，但大多数情况下应该遵循“整洁”规则；
>
> **提供定制：**
>
> 为增强接口的灵活性，可提供定制。定制可以很简单，如允许用户打开或关闭错误日志。定制的基本前提是向每个客户提供相同的基本功能，但给予用户稍加调整的能力。
>
> 通过函数指针和模板参数，可提供更强的定制。例如，可允许客户设置自己的错误处理例程。
>
> **标准库将定制策略发挥到极致，允许客户为容器指定自己的内存分配器。如果要使用这些特性，就必须编写一个遵循标准库指导方针和符合接口要求的内存分配器对象。**标准库中的每个容器都将分配器作为模板参数，第 21 章将详细讲述。
>
> **协调通用性和使用性：** 
>
> 通用意味着复杂，使用意味着简洁，统一这两者即可得到想要的优雅接口；
>
> 太通用，太模板化，不利于使用；太简介，不一定能够完全满足需求；
>
> 但它们并不是互斥的；
>
> **提供多个接口：**
>
> 为在提供足够功能的同时，使用这种方法，提供多个独立的接口，这样可以使得复杂度极大降低。也就是说，实现虽然差不多，但是，使用不同接口，进行功能定制；**这称为接口隔离原则(Interface Segregation Principle, ISP)。**例如，编写的通用网络库可以具有两个独立的方向：一个为游戏提供网络接口，另一个为超文本传输协议(HTTP, 一种网络浏览协议)提供网络接口。 
>
> **让常用功能易于使用：** 
>
> 当提供通用接口时，某些功能的使用频率会高于其他功能。应该让常用功能易于使用，同时仍提供高级功能选项。例如，多语言设置，给定一种语言作为默认语言，其余仍可设置使用；

****

#### 2.4 SOLID 原则

> 常使用易记的首字母缩写词 SOLID 来指代面向对象设计的基本原则。表 6 汇总了 SOLID 原则。其中的大多数原则都在本章讨论过；对于本章未讨论的原则，则指明相关的章号。 
>
> ![image-20240220042235720](https://s2.loli.net/2024/02/20/xD5CHUStYdi4F2w.png)
>
> 原则如下：
>
> S：内部高聚合，之间低耦合；
>
> O：多态+继承实现对象开放，多态+复用实现功能修改关闭；
>
> L：用于区分“有一个”和“是一个”，意思是说，当选择进行“是一个”的派生时，派生类的行为应当与其基类保持一致，如果程序能够保持一致，那么认为应该继续认为选择“是一个”的关系(因为关系为“是一个”，所以当进行使用时，保持前后行为的一致性，功能没有特殊性的前提下，这样的行为不会引起歧义，而且这样做还可以使得多态性得以增强，因为行为是一致的，因为如果一旦复写方法，那么就有可能存在定义上的偏差，这种偏差随着积累可能会很突兀，而且继承之下，潜在的基类属性也会一并继承，这种渗透事实上很糟糕)；如果不能保证的话，也就是派生类的行为与基类不一致时，应该舍弃“是一个”的派生关系，而转为“有一个”的包含关系(因为要包含对行为的修改，用有一个部分再进行修改的方式去写逻辑上更清晰。这种凡是则更加灵活，不会出现复写方法时的逻辑混乱问题)；
>
> I：接口兼顾通用、实用，通过独立接口实现接口特异化，高效；
>
> D：高层模块不应该依赖于底层模块，两者都应该依赖于抽象。抽象不应该依赖于细节，细节应该依赖于抽象。
>
> 1. **高层模块(抽象)定义接口，低层模块实现接口。**
> 2. **具体实现依赖于抽象，而不是抽象依赖于具体实现。**
> 3. **使用接口或抽象类来定义高层模块的行为，而不是依赖于具体的实现类。**
>
> 示例：
>
> ```c++
> #include <iostream>
> 
> // 定义抽象接口
> class Report 
> {
> public:
> 	virtual std::string generate() = 0;
> 	virtual ~Report() {}  // 增加虚析构函数以正确释放资源
> };
> 
> // 具体实现类
> class PDFReport : public Report 
> {
> public:
> 	std::string generate() override 
>     {
> 		// 生成 PDF 报告的具体实现
> 		return "PDF Report";
> 	}
> };
> 
> class HTMLReport : public Report 
> {
> public:
> 	std::string generate() override 
>     {
> 		// 生成 HTML 报告的具体实现
> 		return "HTML Report";
> 	}
> };
> 
> // 高层模块使用抽象接口
> class ReportGenerator 
> {
> private:
> 	Report* report;
> 
> public:
> 	// 通过构造函数注入依赖
> 	ReportGenerator(Report* report) : report(report) {}
> 
> 	~ReportGenerator() 
>     {
> 		delete report;  // 释放资源
> 	}
> 
> 	void generateReport() 
>     {
> 		// 生成报告
> 		std::string result = report->generate();
> 		std::cout << "Generated Report: " << result << std::endl;
> 	}
> };
> 
> // 在使用时，可以通过传入不同的 Report 实现来生成不同类型的报告
> int main() 
> {
> 	Report* pdfReport = new PDFReport();
> 	Report* htmlReport = new HTMLReport();
> 
> 	ReportGenerator pdfReportGenerator(pdfReport);
> 	pdfReportGenerator.generateReport();
> 
> 	ReportGenerator htmlReportGenerator(htmlReport);
> 	htmlReportGenerator.generateReport();
> 
> 	return 0;
> }
> 
> /*和上面的图形类似，这是在说，我的每个派生类要有一个抽象的拥有共同属性的基类，然后，每个积累包含有自己函数名相同但是实现内容不同的函数(多态的实现),然后对于高一级的应用，因为虽然是想对派生类进行操作，但是考虑到复用和不依赖关系，则使用注入基类的方式，来实现多态的实现*/
> ```
>
> 优点如下：
>
> 1. **松耦合：** 依赖注入通过在对象的构造函数、方法参数或者属性中注入依赖，降低了组件之间的耦合度。这使得各个组件可以更独立地开发、测试和维护，而不容易受到彼此的变化影响。
> 2. **可测试性：** 通过依赖注入，可以轻松地替换实际依赖的实现，使用模拟对象或者测试替身。这样，在单元测试中，我们可以注入模拟对象，更方便地对组件进行隔离测试，而不受到真实依赖的影响。
> 3. **可维护性：** 依赖注入使得代码的结构更清晰，依赖关系更明确。这有助于理解和维护代码，因为每个组件的依赖都是显式的，而不是隐藏在组件内部。
> 4. **灵活性：** 通过依赖注入，可以在运行时动态地替换依赖的实现。这为系统提供了更大的灵活性，使得在不修改现有代码的情况下，可以更容易地切换或升级依赖的版本或实现。
> 5. **可扩展性：** 依赖注入使系统更容易扩展，因为新增的组件可以通过依赖注入的方式接入系统，而不需要修改现有代码。

****

### 6.3本章小结

> SOLID！！！

****

## 第三部分 —— 专业的 C++ 编码方法

****

## 第7章 —— 内存管理

> C++ 十分灵活，为了保证这一点，是对程序员采取不干预策略的，即，C++假定程序员知道自己在做什么，即使程序员没有意识到自己做错了什么，也就是说它允许采用一些可能出错的领域。总之，C++ 为了灵活性，而牺牲了部分安全性。内存的分配和管理是 C++ 编程中最容易出错的一个领域，接下来，我们将对它的内存幕后工作原理进行了解，以写出高质量 C++ 程序。
>
> 本章讨论底层内存处理，因为专业的 C++ 程序员将遇到此类代码。**但在现代 C++  中，应尽可能避免底层内存操作。**例如：
>
> - **不应使用动态分配内存的 C 风格数组，而应使用标准库容器，例如 vector, 它会自动处理所有内存分配操作。**  
> - **不应使用裸指针，而应使用智能指针，例如 unique_ptr 和 shared_ptr, 它们会自动释放不再需要的底层资源，例如内存。**  
>
> **基本上，应尝试避免在代码中调用内存分配例程，例如new/new[]和 delete/delete[]。当然，这并不总是可行的，在现有的代码中，很可能并非如此，所以专业 C++程序员仍需要了解内存在幕后的工作原理。**  
>
> **警告：**
>
> **在现代 C++中，应尽可能避免底层内存操作，而使用现代结构，例如容器和智能指针。**

****

### 7.1使用动态内存

> 内存是计算机的低级组件，遗憾的是，即使在 C++这样的高级语言中也仍要面对内存的问题。**很多程序员只是对动态内存有基本的了解。他们回避使用动态内存的数据结构，或通过试错法让程序能正常工作。**扎实理解 C++动态内存的工作原理对于成为一名专业的 C++程序员至关重要。  

****

#### 1.1如何描绘内存

> **堆栈(Stack)和堆(Heap)是计算机内存中用于存储数据的两个主要区域**，它们有一些关键的区别：
>
> 1. **分配方式：**
>    - **堆栈：** 数据在堆栈上分配，以一种后进先出(LIFO)的方式进行管理。当一个函数被调用时，其局部变量和函数调用信息被压入堆栈，函数执行结束时，这些数据从堆栈中弹出。这样的分配和释放是自动进行的。
>    - **堆：** 堆上的内存分配和释放是手动进行的。在堆上分配内存需要明确的请求和释放过程。通常使用`new`(C++)或`malloc`(C语言)来在堆上分配内存，而使用`delete`(C++)或`free`(C语言)来释放堆上的内存。
> 2. **大小：**
>    - **堆栈：** 通常较小，其大小受限于系统设置的栈大小。堆栈主要用于存储函数调用和局部变量等较小的数据。
>    - **堆：** 可以比较大，通常受限于系统总体内存大小。堆主要用于存储动态分配的数据，例如通过`new`或`malloc`分配的对象。
> 3. **生存期：**
>    - **堆栈：** 数据的生存期与其所在函数的执行周期相关。当函数执行结束时，堆栈上的数据被自动释放。
>    - **堆：** 数据的生存期可以长于其分配它的函数执行周期，因为堆上的数据需要手动释放。
> 4. **管理：**
>    - **堆栈：** 由编译器自动管理，无需手动干预。
>    - **堆：** 开发人员需要手动管理内存，确保在不再需要时释放分配的内存，以防止内存泄漏。
>
> ```c++
> #include <iostream>
> 
> int main() 
> {
> 	int* ptr = new int; // 在堆上分配内存
> 
> 	// 假设这里有一些代码，然后我们忘记释放 ptr 指向的内存
> 
> 	// 当 main 函数结束时，ptr 指针变量会被销毁，但指向的堆内存没有被释放
> 	return 0; // 内存泄漏发生
> }
> 
> // 对就是这样使得这个指针丢失，然后那个堆上内存没释放的
> ```
>
> **警告：**
>
> **作为经验法则，每次声明一个指针变量时，务必立即用适当的指针或 nullptr 进行初始化！**
>
> 下一个例子展示了指针既可以在堆栈中，也可在堆中：
>
> ```c++
> int** handle = nullptr;
> // (int*)* handle = nullptr;
> // 这样就很好理解，指向 int 型指针的指针 handle 了
> // handle 是在堆栈中的
> handle = new int*;
> // 给它分配出来一个 指向 int 型变量指针 的空间
> *handle = new int;
> // 对 handle 进行解引用，也就是得到了当初 handle 所指空间中的那个 指向 int 型变量的指针，再为它分配空间
> ```
>
> 1. `int** handle = nullptr;`：声明了一个指向指针的指针变量 `handle`，并将其初始化为 `nullptr`，即空指针。`int**` 表示指向 `int` 类型指针的指针。
> 2. `handle = new int*;`：在堆上分配了一个 `int*` 类型的内存，并将其地址赋给 `handle`。这个 `int*` 类型指针用来存储 `int` 类型的地址。
> 3. `*handle = new int;`：在堆上分配了一个 `int` 类型的内存，并将其地址存储在 `handle` 指向的位置(`*handle`)。现在，`handle` 指向的是一个 `int*` 类型的指针，而这个指针指向的是一个动态分配的 `int` 类型的内存。
>
> ![image-20240220143956527](https://s2.loli.net/2024/02/20/mzW2pFlAqbTriDt.png)

****

#### 1.2分配和释放

> 1. 使用 new 和 delete
>
>    > 由于堆栈和栈的区别，那么就代表着可能在指针失效，而其所指空间未释放，这叫做内存泄漏。
>    >
>    > 经验：
>    >
>    > - 一个 new 对应后面一个 delete;
>    > - ptr = nullptr 将上述 一个 new 和 一个 delelte 包裹起来；
>    >
>    > ```c++
>    > int* prt = nullptr;
>    > ptr = new int;
>    > ...
>    > delete ptr;
>    > ptr = nullptr;
>    > ```
>
> 2. 关于 malloc() 函数
>
>    > 虽然 C++  中也存在 malloc()，但应该避免使用它，new 相比 malloc() 的主要好处式：new 不仅分配内存，还构建对象；例如：
>    >
>    > ```c++
>    > Foo* myFoo = (Foo*)malloc(sizeof(Foo));
>    > // 只分配空间，不创建对象
>    > Foo* myOtherFoo = new Foo();
>    > // 分配空间，也创建对象
>    > ```
>    >
>    > 执行这些代码行后，myFoo 和 myOtherFoo 将指向堆中足以保存 Foo 对象的内存区域。通过这两个指针可访问 Foo 的数据成员和方法。不同之处在于，myFoo 指向的 Foo 对象不是一个正常的对象，因为这个对象从未构建。malloco函数只负责留出一块一定大小的内存。它不知道或关心对象本身。相反，调用 new 不仅会分配正确大小的内存，还会调用相应的构造函数以构建对象。
>
> 3. 当内存分配失败时
>
>    > 很多程序员会假设 new 总是会成功。他们的理由是，如果 new 失败了，则意味着内存量非常低，情况就非常糟糕了。这是一个无法预知的状态，因为不知道程序在这种情况下可能做什么。
>    >
>    > 默认情况下，如果 new 失败了，程序会终止。在许多程序中，这种行为是可以接受的。当 new 因为没有足以满足请求的内存而抛出异常失败时，程序退出。第 14 章将讲解如何在内存不足的情况下正常地恢复。
>    >
>    > 
>    >
>    > 也有不抛出异常的 new 版本。相反，它会返回 nullptr, 这类似于 C 语言中 malloc()的行为。使用这个版本的语法如下所示：
>    >
>    > ```c++
>    > int* ptr = new(nothrow) int;
>    > ```
>    >
>    > 当然，仍然要面对与抛出异常的版本同样的问题——如果结果是 nullptr, 怎么办？编译器不要求检查结果，因此 new 的 nothrow 版本可能导致除了抛出异常的版本遇到的 bug 之外的其他 bug。下面给出示例：
>    >
>    > ```c++
>    > #include <iostream>
>    > #include <new>
>    > 
>    > int main() 
>    > {
>    > 	int* ptr = new(std::nothrow) int;
>    > 	if (ptr == nullptr) 
>    >     {
>    > 		// 处理内存分配失败的情况
>    > 		std::cerr << "Memory allocation failed!" << std::endl;
>    > 	}
>    > 	else 
>    >     {
>    > 		// 继续执行程序
>    > 		*ptr = 42;
>    > 		// 其他代码依赖于 ptr 不为空
>    > 		std::cout << "Value at ptr: " << *ptr << std::endl; // 这里依赖于 ptr 不为空
>    > 		delete ptr; // 注意：确保在不再需要时释放内存
>    > 	}
>    > 
>    > 	// 其他代码，继续依赖于 ptr 不为空
>    > 	int result = *ptr; // 这里依赖于 ptr 不为空，但实际上 ptr 是空指针
>    > 	// 这里的解引用，如果是 nullptr 的话，是错误的
>    > 
>    > 	std::cout << "Result: " << result << std::endl;
>    > 
>    > 	return 0;
>    > }
>    > ```
>    >
>    > 因此，建议使用标准版本的 new。如果内存不足的恢复对程序非常重要，请参阅第 14 章，该章给出了需要的所有工具。

****

#### 1.3数组

> 数组将多个同一类型的变量封装在一个通过索引访问的变量中。
>
> 1. 基本类型的数组
>
>    - 大小不变。区分动态数组和动态分配的数组。
>    - **在 C++ 中有一个继承自 C 的函数 realloc()。不要使用它！**在 C 中，realloc() 用于改变数组的大小，采用的方式是分配新大小的新内存块，然后将所有旧数据内存块复制到新位置，再删除就内存块。在 C++ 中这是极为危险的，因为用户定义的对象不能很好地适应按位复制。
>
> 2. 对象的数组
>
>    - ```c++
>      class Simple
>      {
>      public:
>      	Simple() { std::cout << "Simple constructor called!" << std::endl; }
>      	~Simple() { std::cout << "Simple destructor called!" << std::endl; }
>      };
>      // 给出这个类，后面会用
>      ```
>
>    - 与 简单类型 的数组没什么区别。
>
>    - 通过 new[N]分配 N 个对象的数组时，实际上分配了 N 个连续的内存块，每一块足以容纳单个对象。使用 new[] 时，每个对象的无参构造函数(= default)会自动调用。这样，通过 new[] 分配对象数组时，会返回一个指向数组的指针，这个数组中的所有对象都被初始化了。  
>
>    - 当然在数组元素是对象的时候，才调用析构函数。
>
> 3. 删除数组
>
>    - 和上面说的一样，先用 delete，再将指针指向 nullptr。
>
>    - new <---> delete;
>
>    - new [] <---> delete []
>
>    - 总是使得上面这两个对应。
>
>    - ```c++
>      // 为指向 Simple指针 的数组分配空间，来存储 Simple指针
>      const size_t size = 4;
>      Simple** mySimplePtrArray = new Simple * [size];
>                                                      
>      // Allocate an object for each pointer.
>      for (size_t i = 0; i < size; i++)
>      {
>      	mySimplePtrArray[i] = new Simple();
>      }
>      // Use mySimplePtrArray...
>                                                      
>      // Delete each allocated object.
>      for (size_t i = 0; i < size; i++)
>      {
>      	delete mySimplePtrArray[i];
>      }
>                                                      
>      // Delete the array itself.
>      delete[] mySimplePtrArray;
>      mySimplePtrArray = nullptr;
>      ```
>
>    - 注意：
>
>      **在现代 C++中，应避免使用 C 风格的裸指针。**所以，不要在 C 风格的数组中保存旧式的普通指针，而应在现代的标准库容器中保存智能指针。本章后面讨论这些智能指针，并且会在适当时候自动释放与其关联的内存。
>
> 4. 多维堆栈数组【array[] []】
>
>    - 额，复杂，随便吧，反正我不用，书上也没讲得很仔细。
>    - 就是区分数组的级数吧，就是：array[0] 和 array[0] [0] 的区别。
>
> 5. 多维堆数组【new array[] []】
>
>    - 如果需要在运行时确定多维数组的维数，可以使用堆数组。正如动态分配的一维数组是通过指针访问一样,动态分配的多维数组也通过指针访问。唯一的区别在于，在二维数组中，需要使用指针的指针：在 N 维数组中，需要使用 N 级指针。下面这种声明并动态分配多维数组的方式初看上去是正确的： 
>
>      ``` c++
>      char** board = new char[i][j];
>      ```
>
>    - **这段代码无法成功编译，因为堆数组和堆栈数组的工作方式不一样。多维数组的内存布局是不连续的，所以为基于堆栈的多维数组分配足够内存的方法是不正确的。**
>
>    - **可以首先为堆数组的第一个下标分配一个连续的数组。**
>
>    - **该数组的每个元素实际上是指向另一个数组的指针，另一个数组保存的是第二个下标维度的元素。**  
>
>    - 上述代码只能分配第一层指针，还必须显式地分配第二层指针，如下：
>
>      ![image-20240222224018635](https://s2.loli.net/2024/02/22/JfB6puZXbN1OV8m.png)
>
>      ```c++
>      char** allocateCharacterBoard(size_t xDimension, size_t yDimension)
>      {
>      	char** myArray = new char* [xDimension];
>      	for (size_t i = 0; i < xDimension; i++)
>      	{
>      		myArray[i] = new char[yDimension];
>      	}
>      	return myArray;
>      }
>      ```
>
>    - 释放多维堆数组的内存，也必须类似与分配数组时的代码：
>
>      ```c++
>      void releaseCharacterBoard(char** myArray, size_t xDimension)
>      {
>      	for (size_t = 0; i < xDimension; i++)
>      	{
>      		delete[] myArray[i];
>      	}
>      	delete[] myArray;
>      }
>      ```

> 知道了使用数组的细节后，我们就知道了 C 风格的数组是多么不应该受欢迎。因为这种数组完全没有提供任何安全性。这里解释它们是因为可能在旧代码中会遇到。在新代码中，应该用 C++ 的标准库容器，例如 std::array、std::vector 等。例如，用  vector<T> 表示一维动态数组，用 vector<vector<T>>表示二维动态数组等。当然，直接使用诸如 vector<vector<T>>的数据结构仍然是繁杂的，构建时尤其如此。**如果应用程序中需要 N 维动态数组，建议编写帮助类，以方便使用接口。**例如，要使用行长相等的二维数据，应当考虑编写(也可以重用) Matrix <T> 或 Table <T> 类模板，该模板在内部使用 vector<vector<T>> 数据结构。有关编写类模板的信息，请参阅第 12 章。
>
> 警告：
>
> ​	不要 TM 闲的蛋疼使用 C 风格。
>
> ​	可是，我真贱死了......C 语言好像用的地方真不少，可是我就是更喜欢 C++，因为它太优雅了，什么 Python，真垃圾，真疯了。

****

#### 1.4使用指针

> 因为指针很容易被滥用，所以名声不佳。因为指针只是一个内存地址，所以理论上可以手动修改那个地址,甚至像下面这行代码一样做一些很可怕的事情：
>
> ```c++
> char* scaryPointer = (char* )7;
> ```
>
> 为什么可怕？因为它在一个地址为 7 的地方，构建了一个 char 类型指针，这个地方可能时内存随机垃圾，或其他应用程序中使用的内存。如果开始使用为通过 new 分配的内存区域，那么最终将损坏与对象相关联的内存，或者破坏堆管理相关的内存，使得程序无法正常工作。这种故障可体现在几个方面：例如，可表现为无效结果，因为数据已损坏，或因为访问不存在的内存或写入受保护的内存而引发硬件异常。重则得到错误结果，轻则出现严重错误，导致操作系统或 C++运行时库终止程序。  
>
> 指针理解方式：
>
> - 数学头脑下：看作地址，将其理解为 内存位置的数字；
> - 空间表示法下：看作一个“箭头”，一个间接层，告诉程序“看向那个地方”；
> - 通过 * 运算符解除对一个指针的引用时，实际上让程序在内存中更深一步，即，从地址角度看指针：把解除引用想象为跳到与那个指针表示的地址相对应的内存。使用 图形视图 时，每次解引用都对应从针尾到针头的过程；
> - 通过 & 运算符取一个位置的地址时，在内存中添加了一个间接层，即，从地址的角度看：程序只不过是表示那个位置的数值，这个数值可保存为指针形式。在 图形视图 中，& 运算符创建了一个新箭头，其头部终止于表达式表示的位置，其尾部可以保存为一个指针。
>
> 指针的类型转换：
>
> - 指针的类型事实上是比较弱的，这是什么意思？意思是说，例如，指向 XML 文档的指针和指向 整数 的指针大小完全相同。这就可能造成错误转换。
>
> - 编译器允许通过使用 C 风格的类型转换将任意指针类型方便地转换为任意类型：
>
>   ```c++
>   Document* documentPtr = getDocument();
>   char* myCharPtr = (char*)documentPtr;
>   ```
>
>   静态类型转换的安全性更高。编译器将拒绝执行不同数据类型的指针的静态类型转换：
>
>   ```c++
>   Document* documentPtr = getDocument();
>   char* myCharPtr = static_cast<char*>(documentPtr);	// Bug! Won't compile!
>   ```
>
>   静态类型转换的安全性体现在：两个完全无关的指针不能被转换；而两个指针值之间如果存在“是一个”，也就是继承关系，那么这种转换是可以执行的。然而，在继承层次中完成转换的更安全方式是动态类型转换。那么这里就不扯淡了，之后再详细说明。

****

### 7.2数组-指针的对偶性

> 正如我们所看到的，尤其在 C 中，我们会混淆(准确说，不是混淆，而是看作相同的事物)数组和指针。它们在功能和用法上，存在着重叠性。在堆上分配的数组通过指向该数组中第一个元素的指针来引用。基于堆栈的指针通过数组语法 ([]) 和普通的变量声明来引用。然而，它们之间的关系不止于此，见下。

****

#### 2.1数组就是指针

> 通过指针不仅能指向基于堆的数组，也可以通过指针语法来访问基于堆栈的数组的元素。数组的地址就是第一个元素(索引 0 )的地址。
>
> 上面这段话说明了——数组上的每个元素都能用它的指针寻访到。
>
> ```c++
> int myIntArray[10] = {};
> int* myIntPtr = myIntArray;
> 
> // Access the array through the pointer.
> myIntPtr[4] = 5;
> ```
>
> 向函数传递数组时，通过指针引用用基于堆栈的数组的能力非常有用。下面的函数以指针的方式接收一个整数数组。请注意，调用者需要显式地传入数组的大小，因为指针没有包含于大小有关的信息。事实上，任何形式的 C++ 数组，不论是不是指针，都没有内涵大小信息。这是应使用现代容器(例如，标准库中提供的容器)的另一个原因：
>
> ```c++
> void doubleInts(int* theArray, size_t size)
> {
>  	for (size_t i = 0; i < size; i++)
>  	{
>    		theArray[i] *= 2;
>  	}
> }
> 
> 等价于：
> 
> void doubleInts(int theArray[], size_t size)
> {
>  	for (size_t i = 0; i < size; i++)
>  	{
>    		theArray[i] *= 2;
>  	}
> }
> 
> 都代表输入整数数组
> ```
>
> **请记住，指针本身就意味着传引用，但传引用不代表着就是指针：**
>
> ```c++
> // 对于一维数组存在以下三种方式：
> size_t arrSize = 4;
> int* heapArray = new int[arrSize] { 1, 5, 3, 4 };
> doublelnts(heapArray, arrSize);
> delete[] heapArray;
> heapArray = nullptr;
> int stackArray[] = { 5, 7, 9, 11 };
> arrSize = std::size(stackArray); 	// Since C++17, requires <array>
> // arrSize = sizeof(stackArray) / sizeof(stackArray[0]); 	// Pre-C++17, see Chi
> doublelnts(stackArray, arrSize);
> doublelnts(&stackArray[0], arrSize);
> 
> /*在函数原型中，theArray的后面方括号中数字被忽略，原因在于只强调是数组(指针)，其他都不关心。下面的 3 个版本是等价的：*/
> void doublelnts(int* theArray, size_t size);
> void doublelnts(int theArray[], size_t size);
> void doublelnts(int theArray[2], size_t size);
> /* 在 C 和 C++ 中，函数参数中的数组声明经常会退化(decay)为指向数组第一个元素的指针，这种退化让人可能一开始很难接收，可是不要这样去想，因为最后一种可能会引起人疑问的用法，只有有毛病的人才会用，完全是无用功，仅此而已*/
> ```
>
> 其背后机理在于，传入的参数是一个指针(如果传入的是数组，那么就会将其指针化)。
>
> 可“按引用”给函数传递长度已知的基于堆栈的数组，但其语法并不明显。它不适用于基于堆的数组。例如，下面示例中的 doubleIntsStack() 仅接收大小为 4 的基于堆栈的数组：
>
> **引用(Reference):**
>
> - 引用是一个别名，一旦引用被初始化，它就一直引用同一个对象。
> - 引用在声明时必须初始化，之后不能再引用其他对象。
> - 引用本身没有"重新绑定"的语法，因此无法修改引用指向的对象。
> - 引用无法直接进行内存管理的操作，如释放内存。
>
> ```c++
> int x = 42;
> int& ref = x; // ref 是 x 的引用
> ```
>
>
> 在C++中，引用和指针是两种不同的语言特性，它们有着不同的语法和语义。
>
> 1. 引用(Reference):
>    - 引用是一个别名，一旦引用被初始化，它就一直引用同一个对象。
>    - 引用在声明时必须初始化，之后不能再引用其他对象。
>    - 引用本身没有"重新绑定"的语法，因此无法修改引用指向的对象。
>    - 引用无法直接进行内存管理的操作，如释放内存。
>
> ```c++
> cppCopy codeint x = 42;
> int& ref = x; // ref 是 x 的引用
> ```
>
> 2. 指针(Pointer):
>
>    - 指针是一个变量，用来存储某个对象的地址。
>
>    - 指针可以在初始化后指向不同的对象，可以通过赋值修改指针所指的对象。
>
>    - 指针提供了直接的内存管理操作，例如使用 `delete` 或 `free` 释放内存。
>
> ```c++
> int* ptr = new int(42); // ptr 是指向动态分配的整数的指针
> delete ptr; // 释放内存
> ```
>
> ```c++
> // 传引用
> void doubleIntsStack(int(&theArray)[4]);
> // 传指针
> void doubleIntsStack(int theArray[4]);
> 
> /*一定有人想知道这两者为啥不一样，我一开始也感觉这不就是一样吗，但是，仔细观察，理解定义就可以知道——传引用意味着一切都不变；传指针则意味着可以透过这个间接层作用于原本位置的元素。是不是这样一说，就很清楚了：前者是作为一个整体传入的；后者是传入一个地址来用于穿透到原始数据位置的*/
> 
> // 传引用
> void doubleIntsStack(int(&theArray)[4]);
> /* 至于为什么可以起到限定数组大小的作用：
> 	首先看括号内(&theArray)，传入了一个数组的引用；
> 	然后限定这个传引用数组的大小为 4；
> 	然后这个数组，作为一个整体被视为参数引用式传入；
> */
> 
> // 传引用
> void doubleIntsStack(int& (theArray[4]);
> /* 首先，将(theArray[4])传入，这是将第五个元素引用式传入，后来退化为第五个元素的指针传入；
> */
> ```
>
> ```c++
> // 作为防御性编程的一种保险手段，使用以下方法限定引用式传入数组长度：
> void function(int(&theArray)[N]);
> // N 为限定长度
> ```
>
> ```c++
> // 模板尝试：
> template<size_t N>
> void doubleIntsStack(int(&theArray)[N])
> {
> 	for (size_t i = 0; i < N; i++)
> 	{
> 		theArray[i] *= 2;
> 	}
> }
> ```

****

#### 2.2并非所有指针都是数组

> 额，没什么说的，就是标题所代表的意思，指针只有确定是有效的才能访问它的值，虽然可以很勉强地理解为数组，但是不要这样做，这样可能会导致 bug.
>
> 警告：
>
> ​	通过指针可自动引用数组，但并非所有指针都是数组；

****

### 7.3低级内存操作

> 额，这东西就了解就行，因为啊，C++ 之所以是 C++ 就是不需要像 C 那样考虑那样底层的事情，通过构造和析构从理论来说，内存管理就被隐藏在类中得到极大的可用性的实现。

****

#### 3.1指针运算

> ```c++
> int* myArray = new int[8];
> myArray[2] = 33;	<===等价于 == = > *(myArray + 2) = 3
> // 这一开始似乎很不合理，但是看多，就没啥了
> ```
>
> 宽字符串将在第 19 章讨论，但此时不必了解其细节。此处只需要了解宽字符串支持 Unicode 字符来扩大表示范围(如表示日语字符串)。wchar_t 类型是字符类型，可容纳此类 Unicode 字符，而且通常比 char(1字节)更大。要告知编译器一个字符串字面量是宽字符串字面量，可加上前缀 L 。假设有以下宽字符串：
>
> ```c++
> const wchar_t* myString = L"Hello，World";
> ```
>
> 假设还有一个函数，这个函数接收一个宽字符串，然后返回一个新字符串，新字符串是输入字符串的大写版本：
>
> ```c++
> wchar_t* toCaps(const wchar_t* inString);
> ```
>
> 将 myString 传入这个函数，可将 myString 大写化。不过，如果只想大写化 myString 的一部分，可以通过指针运算引用这个字符串后面的一部分。下面的代码给指针加7, 对宽字符串中的 “World” 部分调用 toCaps(),但 wchar_t 通常超过 1 个字节。
>
> ```c++
> toCaps(myString + 7);
> ```
>
> 指针运算的另一个有用应用是减法运算。将一个指针减去另一个同类型的指针，得到的是两个指针之间指针指向的类型的元素个数，而不是两个指针之间字节数的绝对值。

****

#### 3.2自定义内存管理

> 在 99%的情况下(有人可能会说在 100%的情况下)，C++中内置的内存分配设施是足够使用的。new 和delete 在后台完成了所有相关工作：分配正确大小的内存块、管理可用的内存区域列表以及释放内存时将内存块释放回可用内存列表。
>
> 资源非常紧张时，或在非常特殊的情况下，例如管理共享内存时，实现自定义的内存管理是一个可行的方案。不必担心，实际没有听起来那样可怕。基本上，自己管理内存通常意味着编写一些分配大块内存，并在需要的情况下使用大块内存中片段的类。 
>
> 为什么这种方法更好？自行管理内存可能减少开销。当使用 new 分配内存时，程序还需要预留少量的空间来记录分配了多少内存。这样，当调用 delete 时，可以释放正确数量的内存。对于大多数对象，这个开销比实际分配的内存小得多，所以差别不大。然而，对于很小的对象或分配了大量对象的程序来说，这个开销的影响可能会很大。
>
> 当自行管理内存时，可事先了解每个对象的大小，因此可避免每个对象的开销。对于大量小对象而言，这个差别可能会很大。第 15 章将讲解自定义内存管理的语法。
>
> 对于上面内容，一句话，扯淡。。。

****

#### 3.3垃圾回收

> 看不懂，什么东西，不关心，略过先。

****

#### 3.4对象池

> 略过。

****

### 7.4智能指针

> > 所以，思考智能指针的心理应该被视为 “一个带着编号的房产证”，这样我们就很容易理解所谓“所有权”的问题：
> >
> > - unique_ptr 指针，相当于私有房产的房产证，房产证只限家人有；
> >
> >   - **创建房产证和房子：auto mySimpleSmartPtr = std::make_unique<Simple>();**
> >
> >   - **返回房屋的钥匙【房产证依旧有效】：mySimpleSmartPtr.get()**
> >
> >   - **拆迁换房：**
> >
> >     **mySimpleSmartPtr.reset();	mySimpleSmartPtr.reset(new Simple);**
> >
> >   - **获取房屋钥匙并且销毁房产证【房产证不再具有法律效益】：mySimpleSmartPtr.release()**
> >
> >   - **unique_ptr 代表唯一拥有权**
> >
> >   - **房产证转移户主：move(mySimpleSmartPtr)**
> >
> >   - **自定义拆迁方法 ：std::unique_ptr<int, decltype(free)*> myIntSmartPtr(malloc_int(), free);**
> >
> > - **shared_ptr 指针，相当于公共场所的复数人拥有的房产证，公共的房产证可以相关负责人拥有**；
> >
> >   - **创建房产证和房子：auto mySimpleSmartPtr = std::make_shared<Simple>();**
> >
> >   - **返回房屋的钥匙【房产证依旧有效】：mySimpleSmartPtr.get()**
> >
> >   - **拆迁换房：**
> >
> >     **mySimpleSmartPtr.reset();	mySimpleSmartPtr.reset(new Simple);**
> >
> >   - **无法 获取房屋钥匙并且销毁房产证【房产证不再具有法律效益】：mySimpleSmartPtr.release()**
> >
> >   - **房产证中的所有人数量：mySimpleSmartPtr.use_count()**
> >
> >   - **房产证转义户主：move(mySimpleSmartPtr)**
> >
> >   - **自定义拆迁方法 ：std::shared_ptr<int> myIntSmartPtr(malloc_int(42), free);**
>
> 手动管理动态内存分配缺点：
>
> - 指针丢失
> - 忘记释放内存
> - 多次释放内存
>
> 智能指针优点：
>
> - 避免内存泄漏
> - 避免多次释放，但是可能会出现循环引用，即两个或多个对象之间相互持有对方的 `shared_ptr`，导致它们的引用计数永远不会减为零，对象永远不会被销毁的情况
>
> 智能指针特性：
>
> - 可通过模板为任何指针类型编写类型安全的智能指针类
>
> - 可使用运算重载为智能指针对象提供一个接口，使得智能指针对象的使用和普通指针一样。确切地讲，可重载 * 和 -> 运算符，使得客户代码解除对智能指针对象的引用的方式和解除对普通指针的引用相同。
>
> - 使用类似于 Python 的 “引用计数” 方法来跟踪指针资源的所有者，这样实现对资源的完全利用，以及利用完全后的释放。
>
>   ****
>
> - **使用智能指针需要引入 头文件 <memory>.**
>
> - **将 unique_ptr 视作默认智能指针，只有真正需要共享资源时再使用 shared_ptr.**
>
> - **永远不要把资源分配结果指定给普通指针。永远不要将资源分配结果指定给普通指针。无论使用哪种资源分配方法，都应当立即将资源指针存储在智能指针 unique_ptr 或 shared_ptr 中，或使用其他 RAII 类。**RAII 代表 Resource Acquisition Is Initialization(资源获取即初始化)。 RAII 类获取某个资源的所有权，并在适当的时候进行释放。第 28 章将讨论这种设计技术。  

****

#### 4.1unique_ptr

> 1. **创建：auto mySimpleSmartPtr = std::make_unique<Simple>();**
>
> 2. **返回裸指针：mySimpleSmartPtr.get()**
>
> 3. **利用 reset() 方法可释放 unique_ptr 的底层指针，并使用 reset() 根据需要将其改为另一个指针：**
>
>    **mySimpleSmartPtr.reset();	mySimpleSmartPtr.reset(new Simple);**
>
> 4. **断开 unique_ptr 和 底层指针的连接：mySimpleSmartPtr.release()**
>
> 5. **unique_ptr 代表唯一拥有权，因此无法复制它！**
>
> 6. **使用 std::move() 方法进行移动语义：move(mySimpleSmartPtr)**
>
> 7. **自定义 deleter ：std::unique_ptr<int, decltype(free)*> myIntSmartPtr(malloc_int(), free);**

> 1. **创建 unique_ptrs**
>
>    考虑下面函数，这个函数在堆上分配了一个 Simple 对象，但是不释放这个对象，故意产生内存泄漏：
>
>    ```c++
>    void leaky()
>    {
>    	Simple* mySimplePtr = new Simple();
>    	mySimplePtr->go();
>    }
>    ```
>
>    有时，可能接下来你考虑了要内存释放，可是写出以下代码：
>
>    ```c++
>    void leaky()
>    {
>    	Simple* mySimplePtr = new Simple();
>    	mySimplePtr->go();
>    	delete mySimplePtr;
>    }
>    ```
>
>    在正常情况下，这样的代码当然没什么问题，可是，一旦在调用 go() 方法时，抛出了一个异常，那么将永远不会调用 delete，从而导致了内存泄漏。
>
>    而使用了 unique_ptr 时，会将这两种情况都规避掉：
>
>    ```c++
>    #include <memory>
>    
>    void leaky()
>    {
>    	auto mySimpleSmartPtr = std::make_unique<Simple>();
>    	// 注意，不使用 std::make_unique<Simple()>(); 
>    	// 注意，将创建好的类当作类型处理
>    	// 尤其注意：类  <==>  (自定义的)类型   </=> 构造函数
>    	mySimpleSmartPtr->go();
>    	// 或写作 (*mySimpleSmartPtr).go()
>    }
>    ```
>
>    当实例 mySimpleSmartPtr 离开作用域(函数结束或弹出异常)，不需要显式地删除，会自动调用其析构函数进行释放对象；
>
>    **这段代码使用 C++14 中的 make_unique()和 auto 关键字，所以只需要指定指针的类型，本例中是 Simple。如果 Simple 构造函数需要参数，就把它们放在 make_unique() 调用的圆括号中。**  
>
>    在 C++ 17 之前，必须使用 make_unique()，一是因为只能将类型指定一次，二是出于安全考虑！考虑下面函数，对 foo() 函数的调用：
>
>    ```c++
>    foo(std::unique_ptr<Simple>(new Simple()), std::unique_ptr<Bar>(new Bar(data())));
>    
>    /*这种形式的初始化是直接使用 new 运算符创建对象，并将其所有权转交给 std::unique_ptr。如果在这个过程中发生了异常(例如构造函数抛出异常)，那么 std::unique_ptr 将无法获取对动态分配内存的控制权，从而导致内存泄漏。*/
>    ```
>
>    由于这种方式容易造成内存泄漏，所以不要使用，不是迫不得已绝对不要用！
>
>    **注意：**
>
>    ​	**始终使用 make_unique() 来创建 unique_ptr.**
>
> 2. **使用 unique_ptrs**
>
>    **NB 之处在于：不用学习多少语法，就能享受很多好处。**
>
>    **利用 get() 方法可用于直接访问底层指针。**这可将指针传递给需要普通指针的函数。例如，加入具有以下函数：
>
>    ```c++
>    void processData(Simple* simple);
>    ```
>
>    可采用以下方法进行调用：
>
>    ```c++
>    auto mySimpleSmartPtr = std::make_unique<Simple>();
>    processData(mySimpleSmartPtr.get());
>    /* 为什么这里是 .get() ？
>    	我在之前有这样的疑问，但是这样解释——我不是要对 mySimpleSmartPtr 所指对象进行取值运算，也就是 (*mySimpleSmartPtr).get()；而是将 mySimpleSmartPtr 看做一个整体或者说看成一个类，这个类内自带有的方法是将自己的智能指针转化为裸指针的方法 .get()
>    */
>    ```
>
>    **利用 reset() 方法可释放 unique_ptr 的底层指针，并使用 reset() 根据需要将其改为另一个指针。**例如：
>
>    ```C++
>    // Free resourse and set to nullptr
>    mySimpleSmartPtr.reset();
>    
>    // Free resourse and set to a new Simple instance
>    mySimpleSmartPtr.reset(new Simple);
>    ```
>
>    **利用 release() 方法可断开 unique_ptr 和 底层指针 的连接。** release() 方法返回资源的底层指针，然后将智能指针设置为 nullptr.实际上，智能指针失去对资源的所有权，负责在你用完资源时释放资源。例如：
>
>    ```c++
>    // Release ownership
>    Simple* simple = mySimpleSmartPtr.release();
>    
>    // 此时 mySimpleSmartPtr 不再拥有资源的所有权
>    // 需要手动释放资源，否则可能会发生内存泄漏
>    // Use the simple pointer
>    delete simple;
>    simple = nullptr;
>    ```
>
>    **利用 std::move() 实现移动语义**，实例：
>
>    ```c++
>    class Foo
>    {
>    public:
>    	Foo(unique_ptr<int> data/*可以在这里设定默认值*/) : mData(std::move(data)) {};
>    private:
>    	unique_ptr<int> mData;
>    };
>    
>    auto myIntSmartPtr = make_unique<int>(42);
>    Foo f(std::move(myIntSmartPtr));
>    
>    /* 我来复习一下，成员初始化列表执行：首先 auto myIntSmartPtr = make_unique<int>(42); 给了一个被初始化为 42 的整数型智能指针。然后 Foo f(std::move(myIntSmartPtr)); ，也就是说 std::move(myIntSmartPtr) 先被给了 unique_ptr<int> data ，接下来由于成员初始化列表，再把值给 mData(std::move(data)) ，最后赋给 private 中的mData, 然后执行后面的初始化构造程序*/
>    ```
>
> 3. **unique_ptr 和 C 风格数组**
>
>    unique_ptr 适用于存储动态分配的旧式 C 风格数组。下例创建了一个 unique_ptr 来保存动态分配的、包含 10 个整数的 C 风格数组：
>
>    ```c++
>    auto myVariableSizedArray = make_unique<int[]]>(10);
>    ```
>
>    即使可使用 unique_ptr 存储动态分配的 C 风格数组，也建议改用标准库容器，例如 std::array 和 std::vector 等。
>
> 4. **自定义 deleter**
>
>    默认情况下，unique_ptr 使用标准的 new 和 delete 运算符来分配和释放内存。可将此行改为：
>
>    ```c++
>    int* malloc_int(int value)
>    {
>    	int* p = (*int)malloc(sizeof(int));
>    	*p = value;
>    	return p;
>    }
>                                                                            
>    int main()
>    {
>    	std::unique_ptr<int, decltype(free)*> myIntSmartPtr(malloc_int(42), free);
>    	return 0;
>    }
>                                                                            
>    // 模板类型参数自定义 deleter：
>    std::unique_ptr<T, Deleter> myPtr(new T, myCustomDeleter);
>    // T 是智能指针所管理资源的类型。
>    // Deleter 是一个类型，用于指定自定义的 deleter，可以是函数指针、函数对象等。
>    // myCustomDeleter 是一个实例，用于执行实际的资源释放操作。
>    // decltype(free)* 是一个表达式，用于获取 free 函数的类型，然后再声明一个指向该类型的函数指针。
>    // decltype(free): decltype 是一个C++关键字，用于获取一个表达式的类型而不实际计算其值。在这里，decltype(free) 获取了 free 函数的类型。
>    // decltype(free)*: 加上 *，表示声明一个指针，该指针指向 decltype(free) 所获得的函数类型。
>    // 这部分告诉编译器：我们正在声明一个指针，该指针指向 free 函数的类型。
>    ```
>
>    这段代码使用 malloc_int() 给整数分配内存。unique_ptr 调用标准的 free() 函数来释放内存。如前所述，在 C++ 中不应该使用 malloc()，而应该用 new。**然而，unique_ptr 的这项特性时很有用的，因为还可管理其他类型的资源而不仅是内存。例如，当 unique_ptr 离开作用域时，可自动关闭文件或网络套接字以及岐然任何资源。**
>
>    **自定义 `deleter` 主要是为了让 `std::unique_ptr` 能够管理除了内存之外的其他资源，例如文件句柄、数据库连接、网络套接字等。通过使用自定义的 `deleter` 函数，你可以确保在释放 `std::unique_ptr` 持有的资源时执行特定的清理操作。**
>
>    ```c++
>    #include <iostream>
>    #include <memory>
>                                                                            
>    // 虚拟文件类
>    class VirtualFile {
>    public:
>    	VirtualFile(const std::string& filename) : filename(filename) {
>    		std::cout << "Opening file: " << filename << std::endl;
>    	}
>                                                                            
>    	~VirtualFile() {
>    		std::cout << "Closing file: " << filename << std::endl;
>    	}
>                                                                            
>    	void write(const std::string& data) {
>    		std::cout << "Writing to file: " << filename << std::endl;
>    		// 写入操作
>    	}
>                                                                            
>    private:
>    	std::string filename;
>    };
>                                                                            
>    // 自定义 deleter 函数
>    void closeVirtualFile(VirtualFile* file)
>    {
>    	if (file)
>    	{
>    		delete file;
>    	}
>    }
>                                                                            
>    int main() {
>    	// 使用自定义 deleter 的 unique_ptr
>    	std::unique_ptr<VirtualFile, decltype(&closeVirtualFile)> filePtr(new VirtualFile("example.txt"), &closeVirtualFile);
>                                                                            
>    	// 使用文件句柄进行操作
>    	filePtr->write("Hello, World!");
>                                                                            
>    	// unique_ptr 离开作用域时，closeVirtualFile 将被调用
>    	return 0;
>    }
>    ```
>
>    但是，unique_ptr 的自定义 deleter 的语法有些费解。需要将自定义 deleter 的类型指定为模板类型参数。在本例中，decltype(free) 用于返回 free() 类型。模板类型参数应当是函数指针的类型，因此另外附加一个 * ，如 decltype(free)*。使用shared_ptr 的自定义 deleter 就容易多了，下面将讨论这点。

****

#### 4.2shared_ptr

> 1. **创建：auto mySimpleSmartPtr = std::make_shared<Simple>();**
>
> 2. **返回裸指针：mySimpleSmartPtr.get()**
>
> 3. **利用 reset() 方法可释放 shared_ptr 的底层指针，并使用 reset() 根据需要将其改为另一个指针：**
>
>    **mySimpleSmartPtr.reset();	mySimpleSmartPtr.reset(new Simple);**
>
> 4. **没有这种断开 shared_ptr 和 底层指针的连接的用法：mySimpleSmartPtr.release()**
>
> 5. **shared_ptr 的引用计数方法：mySimpleSmartPtr.use_count()**
>
> 6. **使用 std::move() 方法进行移动语义：move(mySimpleSmartPtr)**
>
> 7. **自定义 deleter ：std::shared_ptr<int> myIntSmartPtr(malloc_int(42), free);**

> shared_ptr 与 unique_ptr 类似。
>
> **.get() 方法：**
>
> ```c++
> #include <iostream>
> #include <memory>
> 
> int main() 
> {
> 	std::shared_ptr<int> sharedPtr = std::make_shared<int>(42);
> 
> 	int* rawPtr = sharedPtr.get(); // 获取裸指针
> 
> 	// 使用 rawPtr 操作资源，但要注意生命周期
> 	// 不要对裸指针进行 delete 和 new 操作，这应当由智能指针自动进行，否则可能错误
> 	std::cout << "Value through rawPtr: " << *rawPtr << std::endl;
> 
> 	// sharedPtr 离开作用域，资源会被正确释放
> 	return 0;
> }
> ```
>
> **其余方法略。**
>
> **.use_count	引用计数获取方法：**
>
> ```c++
> // 实现资源共享
> #include <iostream>
> #include <memory>
> 
> int main() 
> {
> 	// 创建一个 shared_ptr，引用计数为1
> 	std::shared_ptr<int> ptr1 = std::make_shared<int>(42);
> 	std::cout << "ptr1 use count: " << ptr1.use_count() << std::endl;
> 
> 	// 复制构造一个 shared_ptr，引用计数增加为2
> 	std::shared_ptr<int> ptr2 = ptr1;
> 	std::cout << "ptr1 use count: " << ptr1.use_count() << std::endl;
> 	std::cout << "ptr2 use count: " << ptr2.use_count() << std::endl;
> 
> 	// 通过拷贝赋值操作符，引用计数继续增加为3
> 	std::shared_ptr<int> ptr3;
> 	ptr3 = ptr1;
> 	std::cout << "ptr1 use count: " << ptr1.use_count() << std::endl;
> 	std::cout << "ptr3 use count: " << ptr3.use_count() << std::endl;
> 
> 	// 当 shared_ptr 被销毁时，引用计数减少
> 	// 在 ptr2、ptr3 离开作用域时，引用计数减为1，然后在 ptr1 离开作用域时，引用计数降为0，资源被释放
> 	return 0;
> }
> ```
>
> **对比不可复制的 unique_ptr:**
>
> ```c++
> #include <iostream>
> #include <memory>
> 
> int main()
> {
> 	// 创建一个 unique_ptr
> 	std::unique_ptr<int> uniquePtr1 = std::make_unique<int>(42);
> 
> 	// 尝试复制，会导致编译错误
> 	// std::unique_ptr<int> uniquePtr2 = uniquePtr1; // 错误！
> 
> 	return 0;
> }
> ```
>
> **自定义 deleter:**
>
> ```C++
> // Implementation of malloc_int() as before.
> shared_ptr<int> myIntSmartPtr(malloc_int(42), free);
> ```
>
> 下面示例使用 shared_ptr 存储文件指针。当 shared_ptr 脱离作用域时，会调用 CloseFile() 函数来自动关闭文件指针。回顾一下， C++ 由可操作文件的面向对象的类(详细在第 13 章)。这些类在脱离作用域会自动关闭文件。这个例子使用了旧式 C 语言的 fopen() 和 fclose() 函数，只是为了演示 shared_ptr 除了管理纯粹的内存之外还可以用于其他目的。
>
> ```C++
> void CloseFile(FILE* filePtr)
> {
> 	if (filePtr == nullptr)
> 	{
> 		return;
> 	}
> 	fclose(filePtr);
> 	std::cout << "File closed!" << std::endl;
> }
> 
> int main()
> {
> 	FILE* f = fopen("data.txt", "w");
> 	shared_ptr<FILE> filePtr(f, CloseFile);
> 	if (filePtr = nullptr)
> 	{
> 		std::cerr << "Error opening file." << std::endl;
> 	}
> 	else
> 	{
> 		std::cout << "File opened." << std::endl;
> 		// Use filePtr
> 	}
> 
> 	return 0;
> }
> ```
>
> 1. **强制类型转化 shared_ptr：**
>    可用于强制转换的 shared_ptr 的函数是：
>
>    - const_pointer_cast()
>    - dynamic_pointer_cast()
>    - static_pointer_cast()
>    - reinterpret_pointer_cast()
>
>    它们的行为和工作方式类似于非智能指针转换函数:
>
>    - const_cast()
>    - dynamic_cast()
>    - static_cast()
>    - reinterpret_cast()
>
>    这里先不讲了，到第 11 章再仔细讨论这些方法。
>
> 2. **引用计数的必要性：**
>
>    作为一般概念，引用计数(reference counting)用于追踪正在使用的某个类的实例或特定对象的个数。引用计数的智能指针跟踪为引用一个真实指针(或某个对象)而建立的智能指针的数目。**通过这种方法，智能指针可以避免双重删除。**
>
>    双重删除的问题很容易出现。考虑到前面引入的 Simple 类，这个类只是打印出创建或销毁一个对象的消息。如果要创建两个标准的 shared_ptrs，并将它们都指向同一个 Simple 对象，如下面代码所示：
>
>    ```C++
>    // 在销毁时，两个智能指针将尝试删除同一个对象
>    // 但是，创建此对象只调用了一次构造函数，但是要调用两次析构函数
>    // 根据编译器，这段代码可能导致崩溃！
>    void doubleDelete()
>    {
>    	Simple* mySimple = new Simple();
>    	std::shared_ptr<Simple> smartPtr1(mySimple);
>    	std::shared_ptr<Simple> smartPtr2(mySimple);
>    }
>    
>    // 如果没有崩溃，那么输出：
>    Simple constructor called！
>    Simple destructor called！
>    Simple destructor called！
>    
>    // 上述情况对于 unique_ptr 也是一样的
>    // 但是 unique_ptr 难以提供出类似于 shared_ptr 的解决方案
>    // 也就是说，它不允许复制，也就不允许复制构造函数的存在
>    ```
>
>    所以，对于这种情况，应当使用:
>
>    ```c++
>    void doubleShare()
>    {
>    	// 创建一个 shared_ptr 对象，管理动态分配的 Simple 对象
>    	std::shared_ptr<Simple> smartPtr1 = std::make_shared<Simple>();
>    
>    	// 通过拷贝构造函数创建另一个 shared_ptr，共享同一个 Simple 对象的所有权
>    	std::shared_ptr<Simple> smartPtr2 = smartPtr1;
>    	// 或者使用拷贝构造函数：
>    	// std::shared_ptr<Simple> smartPtr2(smartPtr1);
>    	// 两者都是复制 原智能指针
>    
>    	// 在这里，smartPtr1 和 smartPtr2 共享对同一个 Simple 对象的所有权
>    	// 当它们离开作用域时，将正确地释放 Simple 对象的内存
>    }
>    
>    // 输出：
>    Simple constructor called!
>    Simple destructor called!
>    ```
>
>    **之前，一直说共享所有权，但可能并不太明确，我在这里给出通常发挥作用的场景：**
>
>    1. **多个对象需要访问和共享同一块资源：** 如果有多个对象需要使用相同的资源，而不是每个对象都拥有独立的资源副本，那么 `shared_ptr` 是一种合适的选择。这种情况下，通过增加引用计数，可以确保资源在最后一个持有者释放它时才被销毁。
>
>       ```c++
>       cppCopy codeclass Resource
>       {
>       	// Resource class definition
>       };
>       
>       std::shared_ptr<Resource> sharedResource1 = std::make_shared<Resource>();
>       std::shared_ptr<Resource> sharedResource2 = sharedResource1;  // 共享所有权
>       ```
>
>    2. **观察者模式：** 当一个对象(被观察者)的状态变化需要通知多个其他对象(观察者)时，使用 `shared_ptr` 可以确保观察者不会在被观察者销毁后继续引用它。
>
>       ```c++
>       #include <iostream>
>       #include <vector>
>       #include <memory>
>       
>       class Observer
>       {
>       public:
>       	void update()
>       	{
>       		// 实现更新逻辑
>       		std::cout << "Observer updated" << std::endl;
>       	}
>       };
>       
>       class Subject
>       {
>       private:
>       	std::vector<std::shared_ptr<Observer>> observers;
>       
>       public:
>       	void addObserver(std::shared_ptr<Observer> observer)
>       	{
>       		// 添加观察者到列表
>       		observers.push_back(observer);
>       	}
>       
>       	void notifyObservers()
>       	{
>       		// 通知所有观察者
>       		for (const auto& observer : observers)
>       		{
>       			observer->update();
>       		}
>       	}
>       };
>       
>       int main()
>       {
>       	// 创建被观察者对象
>       	std::shared_ptr<Subject> subject = std::make_shared<Subject>();
>       
>       	// 创建观察者对象
>       	std::shared_ptr<Observer> observer1 = std::make_shared<Observer>();
>       
>       	// 共享所有权，observer2和observer1指向相同的对象
>       	std::shared_ptr<Observer> observer2 = observer1;
>       
>       	// 注册观察者到被观察者
>       	subject->addObserver(observer1);
>       	subject->addObserver(observer2);	// 这句话事实上是多余的，因为上面它们是同一个智能指针。
>       
>       	// 通知所有观察者
>       	subject->notifyObservers();
>       
>       	return 0;
>       }
>       ```
>       
>    3. **复杂资源管理：** 当资源的生命周期不仅仅由一个对象的作用域决定，而是由多个对象协同管理时，`shared_ptr` 可以确保资源在所有引用都不再需要时才被释放。
>
>       ```c++
>       cppCopy codeclass ComplexResource
>       {
>       	// ComplexResource class definition
>       };
>                               
>       class ResourceManager
>       {
>       private:
>       	std::shared_ptr<ComplexResource> sharedResource;
>                               
>       public:
>       	void initialize()
>       	{
>       		sharedResource = std::make_shared<ComplexResource>();
>       	}
>                               
>       	void useResource()
>       	{
>       		// 使用资源的逻辑
>       	}
>                               
>       	// 其他复杂的资源管理逻辑
>       };
>                               
>       ResourceManager manager1;
>       ResourceManager manager2 = manager1;  // 共享所有权
>       ```
>
>    这些场景中，`shared_ptr` 提供了一种方便且相对安全的方式来处理共享资源的所有权。但请注意，过度使用共享所有权可能导致循环引用，因此需要谨慎设计和管理。在某些情况下，还可以使用 `std::weak_ptr` 作为 `shared_ptr` 的辅助，以避免循环引用问题。
>
> 3. 别名
>
>    shared_ptr 支持所谓的别名。这允许一个 shared_ptr 与另一个 shared_ptr 共享一个指针(拥有的指针)，但指向不同的对象(存储的指针)。例如，这可用于使用一个 shared_ptr 指向一个对象的成员，同时拥有该对象本身，例如：
>
>    ```C++
>    class Foo
>    {
>    public:
>    	Foo(int value) : mData(value) {}
>    	int mData;
>    }
>                            
>    auto foo = make_shared<Foo>(42);
>    auto aliasing = shared_ptr<int>(foo, &foo->mData);
>    ```
>
>    我喜欢 chatGPT 的这种比喻，很好：
>
>    > 当我们说 `foo` 和 `aliasing` 共享同一个对象的所有权时，我们可以把这个对象比喻成一个大房子，而 `foo` 和 `aliasing` 就是两个不同的人共同拥有这个房子的一种方式。
>    >
>    > - `foo` 有一把大钥匙，可以打开这个房子的门，而这个房子是 `Foo` 类型的。
>    > - `aliasing` 也有一把特殊的钥匙，可以打开同一个房子的门，但是这个钥匙是专门打开房子里某个小房间(`mData`)的。
>    >
>    > 虽然它们都能打开同一个房子，但是它们所关心的部分是不同的。`foo` 关心整个房子(`Foo` 对象)，而 `aliasing` 关心房子里的一个小房间(`mData` 成员)。
>    >
>    > 那么，这里的比喻中，“共享同一个对象的所有权”表示这两个人都有权力进入这个房子，而它们所关心的部分不同，一个关心整个房子，另一个关心房子里的一个小房间。
>
>    仅当两个 shared_ptr (foo 和 aliasing) 都销毁时，才销毁 Foo 对象；
>
>    “拥有的指针” 用于引用计数；当对指针解引用或调用它的 get() 时，将返回“存储的指针”。存储的指针用于大多数操作，如比较运算符。可以使用 owner_before() 方法 或 std::owner_less 类，基于拥有的指针执行比较。在某些情况下(例如在 std::set 中存储 shared_ptr)，这很有用。第 17 章将详细讨论 set 容器；

****

#### 4.3weak_ptr

> - **获取 shared_ptr 的资源所有权，也就是将资源、状态等都可以拿来调用；**
>
> - **是一种引用，但是引用时又不造成原指针对象的引用计数增加。当然，引用计数不增加也说明了它不是创建了 shared_ptr 的副本，而是获取的它的引用权限，也仅仅是获取了引用权限，但是是一种弱弱的引用，很暧昧的那种。**
>
>   > **上面这句话我想强调一点：获取引用权限，但不获取所有权。**
>   >
>   > **套在循环链表【拥有头结点】中是说：头节点拥有首元节点，首元结点拥有后继结点，... ，后继节点可以获取头结点的引用权限【进而使用头结点的相关内容】；**
>   >
>   > **套在树结构上：根有孩子，孩子有它的孩子，... ，孩子可以使用双亲结点的引用权限【进而得到一种探查到双亲的能力】**
>   >
>   > **这里我们看出，“有一个” 关系的维系指针【间接层】 是 要强于 “能知道” 的维系指针的；**
>
> - **它跳出作用域时，并不会销毁原本的指针，因为上面都说了没有引用计数增加，也就是说它对原指针是否销毁不产生什么影响。**

> **在 C++ 中还有一个类与 shared_ptr 模板有关，那就是 weak_ptr。weak_ptr 可包括有 shared_ptr 管理的资源的引用。 weak_ptr 不拥有这个资源，所以不能阻止 shared_ptr 释放资源。weak_ptr 销毁时(例如离开作用域时)，不会销毁它指向的资源；然而，它可以用于判断资源是否已经被关联的 shared_ptr 释放了。weak_ptr 的构造函数要求将一个 shared_ptr 或另一个 weak_ptr 作为参数。为了访问 weak_ptr 中保护的指针，需要将 weak_ptr 转换为 shared_ptr。**这有两种方法：
>
> 1. **使用 weak_ptr 实例的 lock()方法，这个方法返回一个 shared_ptr。**如果同时释放了与 weak_ptr 关联的 shared_ptr, 返回的 shared_ptr 是 nullptr。
> 2. **创建一个新的 shared_ptr 实例，将 weak_ptr 作为 shared_ptr 构造函数的参数。**如果释放了与 weak_ptr 关联的 shared_ptr，将抛出 std::bad_weak_ptr 异常。
>
> 下例演示了 weak_ptr 的用法：
>
> ```c++
> #include <iostream>
> #include <memory>
> 
> class Simple
> {
> public:
> 	Simple() { std::cout << "Simple constructor called!" << std::endl; }
> 	~Simple() { std::cout << "Simple destructor called." << std::endl; }
> };
> 
> void useResource(std::weak_ptr<Simple>& weakSimple)
> {
> 	auto resource = weakSimple.lock();
> 	if (resource)
> 	{
> 		std::cout << "Resource still alive." << std::endl;
> 	}
> 	else
> 	{
> 		std::cout << "Resource has been freed!" << std::endl;
> 	}
> }
> 
> int main()
> {
> 	auto sharedSimple = std::make_shared<Simple>();
> 	std::weak_ptr<Simple> weakSimple(sharedSimple);
> 
> 	// Try to use the weak_ptr.
> 	useResource(weakSimple);
> 
> 	// Reset the shared_ptr.
> 	// Since there is only 1 shared_ptr to the Simple resource, this will
> 	// free the resource, even though is still a weak_ptr alive.
> 	sharedSimple.reset();
> 
> 	// Try to use the weak_ptr a second time.
> 	useResource(weakSimple);
> 
> 	return 0;
> }
> 
> // 上述代码的输出为：
> Simple constructor called!
> Resource still alive.
> Simple destructor called.
> Resource has been freed!
> ```
>
> `std::weak_ptr` 在工程实践中有几个重要的用途：
>
> 1. **避免循环引用：** 一个常见的问题是循环引用，即两个或多个对象之间相互持有对方的 `shared_ptr`，导致它们的引用计数永远不会减为零，对象永远不会被销毁。使用 `std::weak_ptr` 可以打破这种循环引用，避免内存泄漏。
>
>    ```c++
>    cppCopy codeclass Node
>    {
>    public:
>    	std::shared_ptr<Node> next;
>    };
>    
>    std::shared_ptr<Node> node1 = std::make_shared<Node>();
>    std::shared_ptr<Node> node2 = std::make_shared<Node>();
>    
>    node1->next = node2;
>    node2->next = node1;  // 循环引用
>    
>    // 解决方案：将其中一个改为 weak_ptr
>    node1->next = node2;
>    node2->next = std::weak_ptr<Node>(node1);  // 将其中一个改为 weak_ptr
>    
>    1.node1 的后继指向 node2；
>    2.node2 的后继指向 node1；
>    3.如果两者均为
>    ```
>
> 2. **避免 `shared_ptr` 所有权影响对象生命周期：** `std::weak_ptr` 不会增加对象的引用计数，因此它不会影响对象的生命周期。当对象的最后一个 `shared_ptr` 被释放时，即使有相关的 `weak_ptr`，对象也会被正确销毁。
>
>    ```c++
>    cppCopy codestd::shared_ptr<int> sharedPtr = std::make_shared<int>(42);
>    std::weak_ptr<int> weakPtr = sharedPtr;
>    
>    sharedPtr.reset();  // 释放最后一个 shared_ptr
>    // 在这里，weakPtr.lock() 会返回一个空的 shared_ptr，因为对象已被销毁
>    ```
>
> 3. **延迟初始化或加载：** 在某些情况下，对象的创建或加载可能是昂贵的操作。使用 `std::weak_ptr` 可以实现延迟初始化或加载，只有在需要的时候才创建或加载对象。
>
>    ```c++
>    cppCopy codeclass ResourceManager
>    {
>    private:
>    	std::weak_ptr<Resource> cachedResource;
>    
>    public:
>    	std::shared_ptr<Resource> getResource()
>    	{
>    		std::shared_ptr<Resource> resource = cachedResource.lock();
>    		if (!resource)
>    		{
>    			// 如果资源不存在，则创建一个新的
>    			resource = std::make_shared<Resource>();
>    			cachedResource = resource;
>    		}
>    		return resource;
>    	}
>    };
>    ```
>
> 4. **观察者模式：** 在观察者模式中，通常有一个被观察者和多个观察者。被观察者持有观察者的指针，而观察者持有被观察者的指针。使用 `std::weak_ptr` 可以避免观察者持有被观察者的强引用，从而防止循环引用。
>
>    ```c++
>    cppCopy codeclass Observer;
>                                                                            
>    class Subject
>    {
>    public:
>    	void addObserver(std::weak_ptr<Observer> observer);
>    	void notifyObservers();
>    };
>                                                                            
>    class Observer
>    {
>    public:
>    	// ...
>    };
>    ```
>
>    5. 缓存或资源管理：** 在某些情况下，你可能想要对对象的生命周期进行一些控制，但又不希望通过强引用导致对象一直存活。使用 `std::weak_ptr` 可以在需要时获取一个强引用，而不会影响对象的生命周期。
>
>    ```c++
>    cppCopy codeclass ResourceManager
>    {
>    private:
>    	std::weak_ptr<Resource> cachedResource;
>                                                                            
>    public:
>    	std::shared_ptr<Resource> getResource()
>    	{
>    		std::shared_ptr<Resource> resource = cachedResource.lock();
>    		if (!resource)
>    		{
>    			// 如果资源不存在，则创建一个新的
>    			resource = std::make_shared<Resource>();
>    			cachedResource = resource;
>    		}
>    		return resource;
>    	}
>    };
>    ```
>
> 
>
> 总的来说，`std::weak_ptr` 用于处理 `std::shared_ptr` 的循环引用问题，并提供一种不影响对象生命周期的方式来引用对象。
>
> 给出一个数据结构中的示例：
>
> ```c++
> #include <iostream>
> #include <memory>
> #include <vector>
> 
> class TreeNode;
> 
> // 具体下方的这种用法见下面会有不太全面的解释：
> class TreeNode : public std::enable_shared_from_this<TreeNode>
> {
> private:
> 	int data;
> 	// 这里的双亲结点使用 弱(引用)指针，使得对双亲结点的引用不再计数
> 	std::weak_ptr<TreeNode> parent;
> 	std::vector<std::shared_ptr<TreeNode>> children;
> 
> public:
> 	TreeNode(int val) : data(val) {}
> 
> 	// 设置父节点
> 	void setParent(std::shared_ptr<TreeNode> parentNode)
> 	{
> 		parent = parentNode;
> 	}
> 
> 	// 添加子节点
> 	void addChild(std::shared_ptr<TreeNode> childNode)
> 	{
> 		children.push_back(childNode);
> 		childNode->setParent(shared_from_this());
> 	}
> 
> 	// 获取父节点
> 	std::shared_ptr<TreeNode> getParent()
> 	{
> 		return parent.lock();
> 	}
> 
> 	// 获取节点数据
> 	int getData()
> 	{
> 		return data;
> 	}
> 
> 	// 获取子节点列表
> 	const std::vector<std::shared_ptr<TreeNode>>& getChildren() const
> 	{
> 		return children;
> 	}
> };
> 
> int main()
> {
> 	// 创建树形结构
> 	auto root = std::make_shared<TreeNode>(1);
> 	auto child1 = std::make_shared<TreeNode>(2);
> 	auto child2 = std::make_shared<TreeNode>(3);
> 
> 	root->addChild(child1);
> 	root->addChild(child2);
> 
> 	// 上述代码可以用以下代码替代：
> 	// child1->setParent(root);
> 	// child2->setParent(root);
> 
> 	// 获取子节点的父节点
> 	for (const auto& child : root->getChildren())
> 	{
> 		std::shared_ptr<TreeNode> parent = child->getParent();
> 		if (parent)
> 		{
> 			std::cout << "子节点 " << child->getData() << " 的父节点是 " << parent->getData() << std::endl;
> 		}
> 		else
> 		{
> 			std::cout << "子节点 " << child->getData() << " 没有父节点。" << std::endl;
> 		}
> 	}
> 
> 	return 0;
> }
> ```

****

#### 4.4移动语义

> shared_ptr、unique_ptr 和 weak_ptr 都支持移动语义，使得它们特别高效。第 9 章将详细讲解移动语义，此处不详细叙述。这里只需要了解，从函数返回此类指针也很高效。例如，可编写以下函数 create(),并像在 main() 函数中演示的那样使用这个函数：
>
> ```C++
> class Simple 
> {
> 	// Simple class definition...
> };
> 
> std::unique_ptr<Simple> create()
> {
> 	auto ptr = std::make_unique<Simple>();
> 	// Do something with ptr...
> 	return ptr;
> }
> 
> int main()
> {
> 	// 对于临时对象的所有权转移不需要 std::move
> 	std::unique_ptr<Simple> mySmartPtr1 = create();
> 	auto mySmartPtr2 = create();
> 
> 	return 0;
> }
> 
> // 区别
> std::unique_ptr<Simple> create(std::unique_ptr<Simple> ptr)
> {
> 	// 在这里对 ptr 进行一些操作...
> 	return ptr; // 返回 ptr，发生所有权的转移
> }
> 
> int main()
> {
> 	std::unique_ptr<Simple> mySmartPtr1 = std::make_unique<Simple>();
> 
> 	// 传递 mySmartPtr1 给 create 函数，并接收返回值
> 	std::unique_ptr<Simple> mySmartPtr2 = create(std::move(mySmartPtr1));
> 
> 	return 0;
> }
> ```

****

#### 4.5enable_shared_from_this

> std::enable_shared_from_this 混入类 允许对象上的方法给自身安全地返回 shared_ptr 或 weak_ptr。第 28 章将讨论混合类，这里先不详述。enable_shared_from_this 混合类给类添加了以下两个方法：
>
> - shared_form_this() : 返回一个 shared_ptr，它共享对象的所有权。
> - weak_from_this() : 返回一个 weak_ptr，它跟踪对象的所有权。
>
> 这是一项高级功能，此处不做详述，下面的代码简单地演示了它的用法：
>
> ```C++
> class Foo : public std::enable_shared_form_this<Foo>
> {
> public:
> 	std::shared_ptr<Foo> getPointer()
> 	{
> 		return shared_from_this();
> 	}
> };
> 
> int main()
> {
> 	auto ptr1 = std::make_shared<Foo>();
> 	auto ptr2 = ptr->getPointer();
> }
> ```
>
> 注意，仅当对象的指针已经储存在 shared_ptr 时，才能使用对象上的 shared_from_this()。意思如下：
>
> ```c++
> #include <memory>
> 
> class MyClass : public std::enable_shared_from_this<MyClass>
> {
> public:
> 	std::shared_ptr<MyClass> getShared()
> 	{
> 		return shared_from_this();
> 	}
> };
> 
> int main()
> {
> 	// 在栈上创建对象，不由 shared_ptr 管理
> 	MyClass myObject;
> 
> 	// 尝试调用 shared_from_this()，这是不安全的
> 	// std::shared_ptr<MyClass> sharedPtr = myObject.getShared(); // 这行代码会导致运行时错误
> 
> 	// 在堆上创建对象，由 shared_ptr 管理
> 	std::shared_ptr<MyClass> sharedPtr = std::make_shared<MyClass>();
> 	// 写成下面的方式更好：
> 	// auto sharedPtr = std::make_shared<MyClass>();
> 
> 	// 调用 shared_from_this()，这是安全的
> 	std::shared_ptr<MyClass> sharedPtr2 = sharedPtr->getShared();
> 
> 	return 0;
> }
> ```
> 
>这就让我们有了一个疑问为什么要大费周章地使用 enable_shared_from_this?一定很令人疑惑吧？因为貌似我们可以复写上面的代码如下：
> 
>```C++
> class Foo
> {
> public:
> 	shared_ptr<Foo> getPointer()
> 	{
> 		return shared_ptr<Foo>(this);
> 	}
> }
> 
> int main()
> {
> 	MyClass myObject;
> 	auto sharedPtr = std::make_shared<MyClass>();
> 
> 	std::shared_ptr<MyClass> sharedPtr2 = sharedPtr->getShared();
> 
> 	return 0;
> }
> 
> // 这样写貌似才是一种自然的写法，但是注意：我们在之前说过的重复删除错误
> // 为了提醒，我把那段代码再贴过来：
> void doubleDelete()
> {
> 	Simple* mySimple = new Simple();
> 	std::shared_ptr<Simple> smartPtr1(mySimple);
> 	std::shared_ptr<Simple> smartPtr2(mySimple);
> }
> // 这样我们可以看出 Foo 类内成员函数 getPointer() 返回的是一个临时的 shared_ptr<Foo>，它使用传递给构造函数的裸指针(this)来创建一个 shared_ptr，我们就遇到了双重析构问题。
> // 有两个完全独立的 shared_ptr(ptrl 和 ptr2)指向同 一对象，在超出作用域时，它们都会尝试删除该对象。
> // 所以，使用 enable_shared_from_this 的里有就有了，用于返回一个临时的原智能指针副本，而不是一个单纯的临时智能指针。
> ```

****

#### 4.6旧的、过时的/取消的 auto_ptr

> 知道有这疙瘩事，就行了。
>
> 没犯病的话，别用。
>
> 应该风险挺高的吧？毕竟要是放到多态里，编译器自己确定指针的类型，简直风险高到离谱吧？

****

### 7.5常见的内存陷阱

> 一句话，错误往往很微妙，但有常见类型的问题是可以检测和解决的。

****

#### 5.1分配不足的字符串

> 与 C 风格字符串相关的最常见问题是分配不足。大多数情况下，都是因为程序员没有分配尾部的'(T终止字符。当程序员假设某个固定的最大大小时，也会发生字符串分配不足的情况。基本的内置 C 风格字符串函数不会针对固定的大小操作一而是有多少写多少，如果超出字符串的末尾，就写入未分配的内存。  
>
> 以下代码演示了字符串分配不足的情况。它从网络连接读取数据，然后写入一个 C 风格的字符串。这个过程在一个循环中完成，因为网络连接一次只接收少量的数据。在每个循环中调用 getMoreData()。函数，这个函数返回一个指向动态分配内存的指针。当 getMoreData() 返回 nullptr 时，表示己收到所有数据。strcat() 是一个C 函数，它把第二个参数的C 风格字符串连接到第一个参数的 C 风格字符串的尾部。它要求目标缓存区足够大。
>
> ```c++
> char buffer[1024] = { 0 }; // Allocate a whole bunch of memory.
> 
> while (true)
> {
> 	char* nextChunk = getMoreData();
> 	if (nextChunk == nullptr)
> 	{
> 		break;
> 	}
>  	else
>  	{
> 		strcat(buffer, nextChunk); // BUG! No guarantees against buffer overrun!
> 		delete[] nextChunk;
> 	}
> }
> ```
>
> 有三种方法解决这个问题，按优解级排序：
>
> - 使用 string；
> - 使用动态的堆存储追加长度；
> - 创建另一个版本的 getMoreData()，这个版本接收一个最大计数值(包括 '\0' 字符)，返回的字符不多于这个值；然后跟踪剩余的空间数以及缓冲区中当前的位置；

****

#### 5.2访问内存越界

> 本章前面提到，指针只不过是一个内存地址，因此指针可能指向内存中的任何一个位置。这种情况很容易出现。例如，考虑一个 C 风格的字符串，它不小心丢失了 (V终止字符。下面这个函数试图将字符串填满 m 字符，但实际上可能会继续在字符串后面填充 m：
>
> ```c++
> void fillWithM(char* inStr)
> {
> 	int i = 0;
> 	while (inStr[i] != '\0')
>  	{
> 		inStr[i] = 'm';
> 		i++；
> 	}
> }
> ```
>
> **注意：如果把不正确的终止字符串传入这个函数，那么内存的重要部分被改写而导致程序崩溃只是时间问题。考虑到如果程序中与对象关联的内存突然被 m 改写那么会发生什么？这很糟糕！！！**
>
> **写入数组尾部的内存而产生的 bug 被称为 缓冲区溢出错误。这种 bug 已经被一些高危的恶意程序使用，例如病毒和蠕虫。狡猾的黑客可利用改写部分内存的能力，来将代码注入正在运行的程序中。【我们看到它也不完全是废物，也可以用于别的地方】**
>
> **许多内存检测工具也能检测缓存区溢出。使用像 C++ string 和 vector 这样的高级结构有助于避免产生一些和 C 风格字符串和数组相关的 bug.**
>
> **其实就一句话，用 string 和 vector。**

****

#### 5.3内存泄漏

> **C 和 C++ 编程中遇到的另一个令人沮丧的问题是找到和修复内存泄漏。**程序终于开始工作，看上去能给出正确结果。然后，随着程序的运行，吞掉的内存越来越多。这是因为程序有内存泄漏。**通过智能指针避免内存泄漏是解决这个问题的首选方法。**
>
> 分配了内存，但没有释放，就会发生内存泄漏。起初，这听上来好像是粗心编程的结果，应该很容易避免。毕竟，如果在编写的每个类中，每个 new 都对应一个 delete，那么应该不会出现内存泄漏，对不对？实际上，绝对不会这样简单啊！在下面的代码中，Simple 类编写正确，释放了每一处分配的内存。
>
> 当调用 doSomething() 函数时，outSimplePtr 指针修改为指向另一个 Simple 对象，但是没有释放原来 Simple 对象。为演示内存泄漏，doSomething() 函数故意没有删除旧的对象。一旦失去对象的指针，就几乎不可能删除它了。
>
> ```C++
> class Simple
> {
> public:
>  	Simple() { mIntPtr = new int; }
>  	~Simple() { delete mIntPtr; }
>  	void setValue(int value) { *mIntPtr = value; }
> 
> private:
>  	int* mIntPtr;
> };
> 
> void doSomthing(Simple*& outSimplePtr)
> {
>  	outSimplePtr = new Simple();
> }
> 
> int main()
> {
>  	// Allocate a Simple object.
>  	Simple* simplePtr = new Simple();
>  	dosomething(simplePtr);
>  	// Only Clean up the second object.
>  	delete simplePtr;
> 
>  	return 0;
> }
> ```
>
> 警告：
>
> ​	记住，上述代码仅用于演示！在生产环境的代码中，应当使 mIntPtr 和 simplePtr 成为 unique_ptr，使 outSimplePtr 成为 unique_ptr 的引用。如下：
>
> ```c++
> #include <memory>
> 
> class Simple
> {
> public:
>  	Simple() { mIntPtr = std::make_unique<int>(); }
>  	void setValue(int value) { *mIntPtr = value; }
> 
> private:
>  	std::unique_ptr<int> mIntPtr;
> };
> 
> void doSomething(std::unique_ptr<Simple>& outSimplePtr)
> {
>  	outSimplePtr = std::make_unique<Simple>();
> }
> 
> int main()
> {
>  	auto simplePtr = std::make_unique<Simple>();
>  	doSomthing(simplePtr);
> 
>  	return 0;
> }
> ```
>
> 上例中的内存泄漏可能来自程序员之间的沟通不畅或糟糕的代码文档。 doSomething() 的调用者可能没有意识到该变量是通过传引用的，因此，没有理由期望该指针会重新赋值。如果他们没有注意到这个参数是一个指针的非 const 引用，就可能怀疑会发生奇怪的事情，但是 doSomething() 周围并没有说明这个行为的注释。
>
> 暂时略过 MFC 部分，之后专门学。

****

#### 5.4双重删除和无效指针

> **通过 delete 释放某个指针关联的内存时，这个内存就可以被其他程序使用了。然而，无法禁止再次使用这个指针，这个指针就成为了悬空指针(dangling pointer)。双重释放也是如此，由于可能已被分配另一对象内存，所以可能会被删掉，崩溃。**
>
> ```c++
> #include <iostream>
> 
> int* createInt()
> {
>  	int* ptr = new int(42);
>  	return ptr;
> }
> 
> int main()
> {
>  	int* myPointer = createInt();  // 创建一个动态分配的整数，并将其地址赋给指针
> 
>  	// 假设在某个时刻释放了指针所指向的内存
>  	delete myPointer;
> 
>  	// 在这之后，myPointer成为悬空指针，因为它仍然包含已释放的内存地址
> 
>  	// 错误的使用悬空指针
>  	std::cout << *myPointer << std::endl;  // 这里可能导致未定义行为
>  	// 错误双重释放
>  	// delete myPointer;
> 
>  	return 0;
> }
> 
> ```
>
> 双重删除和使用已释放的内存都是很难追查的问题，因为症状可能不会立即显现。如果双重删除在较短的时间内发生，程序可能产生未定义的行为，因为关联的内存可能不会那么快重用。同样，如果删除的对象在删除后立即使用，这个对象很有可能仍然完好无缺。
>
> 当然，无法保证这种行为会继续出现。一旦删除对象，内存分配器就没有义务保存任何对象。即使程序能正常工作，使用已删除的对象也是极糟糕的编程风格。  
>
> 多内存泄漏检测程序(例如 Visual C++和 Valgrind), 也会检测双重删除和已释放对象的使用。  
>
> 如果不按推荐的方式使用智能指针而是使用普通指针，至少在释放指针关联的内存后，将指针设置为nullptro 这样能防止不小心两次删除同一个指针和使用无效的指针。注意，在 nullptr 指针上调用 delete 是允许的，只是这样没有任何效果。

****

### 7.6本章小节

> 总结起来：
>
> - 引入 <memory>，用 智能指针；
> - 引入 <string>，用 string；
> - 引入 <vector>，用 vector；

****

## 第8章 —— 熟悉类和对象

> 作为面向对象语言，C++ 提供了使用对象和定义对象的工具，称为类。
>
> 编写没有类的 C++ 程序就像去巴黎吃麦当劳一样。
>
> 类是 C++ 中最基本、最有用的特性。
>
> **本章讲述与类和对象的使用有关的基本概念，包括编写类定义、定义方法、在堆和堆栈中使用对象，以及编写构造函数、默认构造函数、编译器生成的构造函数、构造函数初始化器(称为 ctor-initialize())、复制构造函数、构造函数初始化列表、析构函数和赋值运算符。**即使已经熟悉了类和对象，也应该大致了解一下本章的内容，因为本章包含了各种细节信息，其中一些你可能并不熟悉。  

****

### 8.1电子表格示例介绍

> 本章和第 9 章将列举一个可运行的、简单的电子表格示例。电子表格是一种二维的 “单元格” 网格，每个单元格包含一个数字或字符串。专业的电子表格(例如 Microsoft Excel) 提供了执行数学计算的功能，例如，对一组单元格的值求和。这里的电子表格示例不想抢占 Mircosoft 的市场，只是用来说明类和对象。
>
> 这个电子表格使用了两个基本类：Spreadsheet 和 SpreadsheetCell。每个 Spreadsheet 对象都包括了若干 SpreadsheetCell 对象。此外，SpreadsheetApplication 类管理 Spreadsheet 集合。本章重点介绍 SpreadsheetCell，第 9 章开发 Spreadsheet 和 SpreadsheetApplication 类。
>
> 注意：
>
> ​	为循序渐进地讲解概念，本章显示了几个不同版本的 SpreadsheetCell 类。因此，本章关于类的各种尝试并非总是说明编写类的 “最佳” 方法。特别是早期的示例省略了一些通常会包含但还没有介绍重要的特性。

****

### 8.2编写类

> **编写类时，需要指定行为或方法(应用于类的对象)，还需要指定属性和数据成员(每个对象都会包含)。编写类有两个要素：定义类本身和定义类的方法。**

****

#### 2.1类定义

> 下面开始尝试编写一个简单的 SpreadsheetCell 类，其中每个单元格都只存储一个数字：
>
> ```C++
> class SpreadsheetCell
> {
> public:
> 	void setValue(double inValue);
> 	double getValue() const;
> 
> private:
> 	double mValue;
> };
> ```
>
> 每个类定义都以关键字 class 和 类名 开始。类定义是一条 C++ 语句，因此必须用分号结束。如果类定义结束时，不使用分号，编译器将给出几个错误，这些错误十分模糊，似乎与缺少分号毫不相干。
>
> 类定义所在的文件通常根据类命名。例如， SpreadsheetCell 类定义可放在 SpreadsheetCell.h 文件中。这并不是一条强制规则，可用自己喜欢的名称命名文件。
>
> 1. **类的成员：**
>
>    **类可以有许多成员，可以是：成员函数(方法、构造函数或者析构函数)，成员变量(也成为数据成员)、成员枚举、类型别名和嵌套类等。**
>
>    下面两行声明了类支持的方法，这类似于函数原型：
>
>    ```c++
>    void setValue(double inValue);
>    double getValue() const;
>    ```
>
>    **需要指出：最好将不改变对象的成员函数声明为 const。**
>
>    下面这行声明了类的数据成员，看上去有点像变量的声明。
>
>    ```c++
>    double mValue;
>    ```
>
>    类定义的成员函数和数据成员，但它们只作用于类的特定实例，也就是对象。这条规则的唯一例外就是静态成员，参见第九章。类定义概念，对象包含实际的位。因此，每个对象都会包含自己的 mValue 变量值。成员函数的实现被所有对象共享，类可以包含任意数量的成员函数和数据成员。成员函数和数据成员不能同名。  
>
> 2. 访问控制：
>
>    > 类中的每个方法和成员都可用三种访问说明符(access specifiers)之一来说明：public、protected 或 private。访问说明符将应用于其后声明的所有成员，直到遇到另一个访问说明符。在 SpreadsheetCell 类中，setValue() 和 getValue() 方法是公有访问的，而 mValue 数据成员是私有访问的。
>    >
>    > 类的默认访问说明符是：private，即在第一个访问说明符之前声明的所有成员的访问都是私有的。例如，将 public 访问说明符转移到 setValue() 方法声明的下方， setValue() 方法就会称为私有访问而不是公有访问。
>    >
>    > ```C++
>    > class SpreadsheetCell
>    > {
>    > 	void setValue(double inValue);	// now has private access
>    > 
>    > public:
>    > 	double getValue() const;
>    > 
>    > private:
>    > 	double mValue;
>    > };
>    > ```
>    >
>    > 与类相似，C++ 中的结构(struct)也可拥有方法。实际上，唯一的区别就是结构的默认访问说明符是：public，而类的默认是：private。例如，SpreadsheetCell 类可以用就够重写，如下所示：
>    >
>    > ```C++
>    > struct SpreadsheetCell
>    > {
>    > 	void setValue(double inValue);
>    > 	doubel getValue() const;
>    > 
>    > private:
>    > 	double mValue;
>    > };
>    > ```
>    >
>    > 如果只需要一组可供公共访问的数据成员，没有方法或方法数量极少，习惯上用 struct 替代 class。一个简单的 struct 的示例是用于存储点坐标的结构体：
>    >
>    > ```C++
>    > struct Point
>    > {
>    > 	double x;
>    > 	double y;
>    > };
>    > ```
>    >
>    > **下表给出了三种访问说明符的含义：**
>    >
>    > **私密性强到弱：	private > protected > public**
>    >
>    > **友元可以破坏这种私密性，使得 上述成员都可访问；**
>    >
>    > ![image-20240225032900275](https://s2.loli.net/2024/02/25/Lvo4ErQOS3s5RFb.png)
>
> 3. 声明顺序：
>
>    可使用任何顺序声明成员和访问控制说明符：C++ 没有施加任何限制，例如 成员函数在数据成员之前，或者 public 在 private 之前。此外，可重复使用访问说明符。这没什么说的。
>
> 4. 类内成员初始化器：
>
>    可直接在类定义中初始化成员变量。例如，默认情况下，在 SpreadsheetCell 类定义中直接将 mValue 初始化为 0，如下所示：
>
>    ```C++
>    class SpreadsheetCell
>    {
>    	// Remainder of the class definition omitted for brevity.
>    private:
>    	double mValue;
>    };
>    ```

****

#### 2.2定义方法

> 前面的 SpreadsheetCell 类的定义足以创建类的对象。然而，如果试图调用 setValue() 或 getValue() 方法，链接器将发出警告，因为方法没有实现定义。这是因为类定义指明了方法的原型，但是没有定义方法的是实现。与编写独立的函数的原型和定义类似，必须编写方法的原型和定义。注意，类定义必须在方法定义之前。通常类定义在头文件中，方法定义在包含头文件的源文件中。下面是 SpreadsheetCell 类中两个方法的定义：
>
> ```c++
> #include "SpreadsheetCell"
> 
> void SpreadsheetCell::setValue(double inValue)
> {
> 	mValue = inValue;
> }
> 
> void SpreadsheetCell::getValue() const
> {
> 	return mValue;
> }
> ```
>
> 注意：每个方法名前都出现了类名和两个冒号(作用域解析运算符(scope resolution operator))。在此环境中，这个语法告诉编辑器，要定义的 setValue() 方法是 SpreadsheetCell 类的一部分。此外还要注意，定义方法时，不要重复使用访问说明符。
>
> 注意：
>
> > 如果使用 Microsoft Visual C++ IDE，会发现默认情况下，所有源文件都以 #include "stdafx.h" 开始。
> >
> > 在 Visual C++ 项目中，默认情况下，每个文件都应该以这一行开始，自己包含的文件必须在这一行后面。如果将自己包含的文件放在 stdafx.h 之前，这一行就会失效，编译器会给出各种错误。对预编译的头文件概念的说明超出了这本书的范围，更多看关于预编译头文件的 Microsoft 文档。
>
> 1. 访问数据元素
>
>    类的非静态方法，例如 setValue() 和 getValue()，总是在类的特定对象上执行。在类的方法体中，可以访问对象所属类的所有数据成员。在前面的 setValue() 定义中，无论哪种对象调用这个方法，下面这行代码都会改变 mValue 变量的值：
>
>    ```c++
>    mValue = inValue；
>    ```
>
>    如果两个不同的对象调用 setValue()，这行代码(对每个对象执行一次)会改变两个不同对象内的变量值。
>
> 2. 调用其他方法
>
>    内部的某个方法可调用其他方法，考虑扩展后的 SpreadsheetCell 类。实际的电子表格应用程序允许在单元格中保存文本数据和数字。试图将文本单元格解释为数字时，电子表格会试着将文本转换为数字。如果这个文本不能代表一个有效的值，单元格的值会被忽略。在这个程序中，非数字的字符串会生成值为 0 的单元格。为让 SpreadsheetCell 支持文本数据，下面对类定义进行修改：
>
>    ```c++
>    #include <string>
>    #include <string_view>
>    
>    class SpreadsheetCell
>    {
>    public:
>    	void setValue(double inValue);
>    	double getValue() const;
>    	void setString(std::string_view inString);
>    	std::string getString() const;
>    
>    private:
>    	std::string doubleToString(const double& inValue) const;
>    	double stringToDouble(std::string_view inString) const;
>    	double mValue;
>    };
>    ```
>
>    这个类版本只能存储 double 数据。如果客户将数据设置为 string，数据就会转换为 double。如果文本不是有效数字，就将 double 值设置为 0.0。这个类定义显示了两个设置并获取单元格文本的新方法，还有两个新的用于将 double 转换为 string、将 string 转换为 double 的私有帮助方法。下面是这些方法的实现：
>
>    ```c++
>    #include "SpreadsheetCell.h"
>    
>    void SpreadsheetCell::setValue(double inValue)
>    {
>    	mValue = inValue;
>    }
>    
>    double SpreadsheetCell::getValue() const
>    {
>    	return mValue;
>    }
>    
>    void SpreadsheetCell::setString(std::string_view inString)
>    {
>    	mValue = stringToDouble(inString);
>    }
>    
>    std::string SpreadsheetCell::getString() const
>    {
>    	return doubleToString(mValue);
>    }
>    // 不要用 std::string_view 作为返回值，一般情况下都不好。
>    // 因为 std::string_view 是 一个对 【现有的】 string 的引用
>    // 而一般情况下，我们都是在函数内部得到的一个局部 string 变量，在执行完函数后就销毁了，没法再引用了
>    // 这种情况下，使用之后学习的 RVO,也就是 Return Value Optimization,返回值优化，也称为 复制省略
>    
>    std::string SpreadsheetCell::doubleToString(const double& inValue) const
>    {
>    	return std::to_string(inValue);
>    }
>    
>    double SpreadsheetCell::stringToDouble(std::string_view inString) const
>    {
>    	return strtod(inString.data(), nullptr);
>    }
>    ```
>
>    注意：
>
>    ​	doubleToString() 方法的这种实现方式，例如，将值 6.1 转换为 6.100000。但由于这是一个私有帮助方法，因此不必修改任何客户代码即可实现该实现。
>
> 3. this 指针
>
>    每个普通方法调用都会传递一个指向对象的指针，这就是称为 “隐藏” 参数的 this 指针，使用这个指针可访问数据成员或调用方法，也可将其传递给其他方法或函数。有时还用它来消除名称的歧义。例如，可使用 value 而不是 mValue 作为 SpreadsheetCell 类的数据成员，用 value 而不是 inValue 作为 setValue() 方法的参数。在此情景下，setValue() 如下所示：
>
>    ```c++
>    void SpreadsheetCell::setValue(double value)
>    {
>    	value = value;	// Ambiguous!
>    }
>    ```
>
>    明显上述代码存在歧义，而这个歧义一般情况下，会编译成功，而且不会有任何警告或错误信息，但得到的结果绝对不是我们所期望看到的。
>
>    未避免歧义，就可以使用 this 指针：
>
>    ```C++
>    void SpreadsheetCell::setValue(double value)
>    {
>    	this->value = value;
>    }
>                                                                            
>    // 然而，如果遵循第 3 章所讲述的命名规则，那么永远不会遇到这样的问题
>    ```
>
>    如果方法的某个对象调用了某个函数(或方法)，而这个函数采用指向对象的指针作为参数，就可以使用 this 指针调用这个函数。例如，假定编写了一个独立的 printCell() 函数(不是方法)，如下所示：
>
>    ```  C++
>    void printCell(const SpreadsheetCell& cell)
>    {
>    	std::cout << cell.getCell() << std::endl;
>    }
>    ```
>
>    如果想要用 setValue() 调用 printCell()，就必须将 *this 指针作为参数传给 printCell()，这个指针指向 setValue() 操作的 SpreadsheetCell 对象。
>
>    ```C++
>    void SpreadsheetCell::setValue(double value)
>    {
>    	this->value = value;
>    	printCell(*this);		// 对 this 指针解引用 得到 this 指针所指对象，得到方法的操作对象
>    	// 从某种角度说，this 指针相当于是一种间接的传引用方法
>    }
>    ```
>
>    注意：
>
>    ​	上述问题将在之后被重载运算符取代，因为更简洁方便：重载 << 后，即可使用下面的行输出 SpreadsheetCell：
>
>    ```c++
>    std::cout << *this << std::endl;
>    ```

****

#### 2.3使用对象

> 以前面的 SpreadsheetCell 类为例，它事实上没有创建任何类，而是建筑它的蓝图。但是绘制蓝图并没有创建任何对象，对象必须依据蓝图在后面进行创建。
>
> 但是使用类就代表着，存在两种方式的使用：在堆栈中和在堆中使用。
>
> 1. 堆栈中的对象：
>
>    下面的代码在堆栈中创建并使用了 SpreadsheetCell 对象：
>
>    ```C++
>    SpreadsheetCell myCell, anotherCell;
>    myCellsetValue(6);
>    anotherCell.setValue("3.2");
>    std::cout << "cell 1 : " << myCell.getValue() << std::endl;
>    std::cout << "cell 2 : " << anotherCell.getValue() << std::endl;
>    
>    // 输出为：
>    cell 1 : 6
>    cell 2 : 3.2
>    ```
>
> 2. 堆中的对象：
>
>    - 使用 new 方法动态分配对象：
>
>      `````c++
>      SpreadsheetCell* myCellp = new ShpreadsheetCell();
>      myCellp->setValue(3.7);
>      std::cout << "cell 1 : " << myCellp->getValue() << " " << myCellp->getString() << std::endl;
>      delete myCellp;
>      myCellp = nullptr;
>      `````
>
>      ```C++
>      ->      <==>		().
>      ```
>
>    - 使用 智能指针 分配对象：
>
>      就如同必须释放对中分配的其他内存一样，也必须使用 delete 释放对象所占据的内存，为避免发生内存错误，强烈建议使用智能指针：
>
>      ```C++
>      auto myCellp = make_nuique<SpreadsheetCell>();
>      // Equivalent to:
>      // unique_ptr<SpreadsheetCell> myCell(new SpreadsheetCell());
>      myCellp->setVale(3.7);
>      std::cout << "cell 1 : " << myCellp->getValue() << " " << myCellp->getValue() << std::endl;
>      ```
>
>      警告：
>
>      - 如果用 new 为某个对象分配内存，那么使用完对象后，要用 delete 销毁对象，或者使用智能指针自动管理内存。
>
>      - 如果没有使用智能指针，当删除指针所指的对象时，最好将指针重置为 null。 这并非强制要求，但这样做可以防止在删除对象后意外使用这个指针，以便于调试。  

****

### 8.3对象的生命周期

> **对象的生命周期涉及三个活动：**
>
> 1. **创建**
> 2. **销毁**
> 3. **赋值**
>
> 理解对象什么时候被创建、销毁、赋值，以及如何定制这些行为很重要。
>
> **下面的自动生成的 拷贝构造函数 和 复制赋值运算符 均为浅拷贝，深拷贝需要自行构造。**

****

#### 3.1创建对象

> 1. **分配内存空间：** 首先，需要为对象分配内存空间。这包括对象的数据成员、虚表指针(对于包含虚函数的类)，以及可能的填充字节。
> 2. **调用构造函数：** 执行对象的构造函数，进行对象的初始化。构造函数负责设置对象的数据成员，确保对象处于有效的初始状态。
> 3. **执行成员初始化列表：** 如果在类的构造函数中使用了成员初始化列表，那么在构造函数体执行之前，成员初始化列表中的初始化操作会被执行。
> 4. **执行构造函数体：** 构造函数体中的代码会按照书写顺序被执行，可以包括其他的初始化逻辑和操作。

> 在声明对象(如果是在堆栈中)或使用 new、new[] 或智能指针显式分配空间时，就会创建对象。当创建对象时，会同时内嵌的对象。例如：
>
> ```C++ 
> #include <string>
> class MyCalss
> {
> private:
> std::string mName;
> };
> 
> int main()
> {
> MyClass obj;
> 
> return 0;
> }
> ```
>
> 在 main() 函数中，创建 MyClass 对象时，同时创建内嵌的 string 对象，当包含它的对象被销毁时，string 也被销毁。
>
> 在声明变量时，最好给它们赋初始化值 。例如，通常应该将 int 变量初始化为 0；
>
> ```C++
> int x = 0;
> ```
>
> 与此类似，也应该初始化对象。声明并编写一个名为构造函数的方法，可以提供这一功能，在构造函数中可以执行对象的初始化任务。无论任何时候创建对象，都会执行其构造函数。
>
> **注意：**
>
> ​	**C++ 程序员有时将构造函数称为 ctor;**
>
> 1. **编写构造函数**
>
>    从语法上，构造函数是与类同名的方法。构造函数没有返回类型，可以有也可以没有参数，没有参数的构造函数称为默认构造函数。可以是无参构造函数，也可以让所有参数都使用默认值。许多情况下，都必须提供默认构造函数，如果不提供，就会导致编译器错误，默认构造函数将在稍后讨论。
>
>    下面试着在 SpreadsheetCell 类中添加一个构造函数：
>
>    ```C++
>    class SpreadsheetCell
>    {
>    public:
>    	SpreadsheetCell(double initialValue);
>    	// Remainder of the class definition omitted for brevity
>    };
>    ```
>
>    必须提供普通方式的实现一样，也必须提供构造函数的实现：
>
>    ```C++
>    SpreadsheetCell::SpreadsheetCell(double initialValue)
>    {
>    	setValue(initialValue);
>    }
>    ```
>
>    SpreadsheetCell 构造函数是 SpreadsheetCell 类的一个成员，因此 C++ 在构造函数的名称之前要求正常的 SpreadsheetCell:: 作用域解析。由于构造函数本身的名称也是 SpreadsheetCell，因此代码的 SpreadsheetCell::SpreadsheetCell 结尾看起来有点很好笑。这个现实只是简单地调用了 setValue() 方法。
>
> 2. **使用构造函数**
>
>    构造函数用来创建并初始化其值。在基于堆栈和堆进行分配时可以使用构造函数。
>
>    - **在堆栈中分配 SpreadsheetCell 对象时，可这样使用构造函数：**
>
>      ```C++
>      SpreadsheetCell myCell(5), anotherCell(4);
>      std::cout << "cell 1 : " << myCell.getValue() << std::endl;
>      std::cout << "cell 2 : " << another.getValue() << std::endl;
>      
>      // 注意！不要显式地调用 SpreadsheetCell 构造函数。例如，不要使用下面的做法：
>      SpreadsheetCell myCell.SpreadsheetCell(5);		// Will Not Compile!
>      
>      // 同样，在后来也不能调用构造函数。下面的代码也是不正确的：
>      SpreadsheetCell myCell;
>      myCell.SpreadsheetCell(5);		// Will Not Compile!
>      ```
>
>    - 在堆中使用构造函数
>
>      当动态分配 SpreadsheetCell 对象时，可这样使用构造函数：
>
>      ```C++
>      auto smartCellp = make_unique<SpreadsheetCell>(4);
>      // ... do something with the cell, no need to delete the smart pointer.
>                                                      
>      // Or with raw pointers, without smart pointers (not recommended)
>      SpreadsheetCell* myCellp = new SpreadsheetCell(5);
>      SpreadsheetCell* anotherCellp = nullptr;
>      anotherCellp = new SpreadsheetCell(4);
>      // ... do something with the cells
>      delete myCellp;
>      myCellp = nullptr;
>      delete anotherCellp;
>      anotherCellp = nullptr;
>                                                      
>      // 注意可以声明一个指向 SpreadsheetCell 对象的指针，而不立即调用构造函数。堆栈中对象在声明时会调用构造函数
>      ```
>
>      无论在堆栈中(在函数中)还是在类中(作为类的数据成员)声明指针，如果没有立即初始化指针，都应该像前面声明 anotherCellp 时一样，先将其初始化为 nullptr。如果不赋予 nullptr 值，指针就是未定义。意外地使用未定义的指针可能会导致无法预料的、难以诊断的内存问题。如果将指针初始化为 nullptr，在大多数操作环境下使用这个指针，都会引起内存访问错误，而不是难以预料的结果。
>
>      同样，要记得使用 new 动态分配的对象使用 delete，或者使用智能指针。
>
> 3. **提供多个构造函数**
>
>    在一个类中可提供多个构造函数。所有构造函数的名称相同(类名)，但不同的构造函数具有不同数量的参数或者不同的参数类型。**在 C++ 中，如果多个函数具有相同的名称，那么当调用时编译器会选择参数类型匹配的那个函数。这叫做重载，第 9 章将详细讨论。**
>
>    在 SpreadsheetCell 类中，编写两个构造函数是有益的：一个采用 double 初始值，另一个采用 string 初始值。下面的类型一具有两个构造函数：
>
>    ```C++
>    class SpreadsheetCell
>    {
>    public:
>    	SpreadsheetCell(double initialValue);
>    	SpreadsheetCell(std::string_view initialValue);
>    	// Remainder of the class definition omitted for brevity.
>    };
>    
>    SpreadsheetCell::SpreadsheetCell(std::string_view initialValue)
>    {
>    	setString(initialValue);
>    }
>    
>    // 下面是使用两个不同构造函数的代码：
>    SpreadsheetCell aThirdCell("test");		// Uses std::string_view ctor
>    SpreadsheetCell aFourthCell(4.4);		// Uses double-arg ctor
>    auto aFifthCellp = make_unique<SpreadsheetCell>("5.5");
>    std::cout << "aThirdCell : " << aThirdCell.getValue() << std::endl;
>    std::cout << "aFourthCell : " << aFourthCell.getValue() << std::endl;
>    std::cout << "aFifthCellp : " << aFifthCellp->getValue() << std::endl;
>    ```
>
>    有一种很诱人的想法就是在构造函数中调用执行另一个构造函数，例如：
>
>    ```C++
>    SpreadsheetCell::SpreadsheetCell(std::string_view iinitialValue)
>    {
>    	SpreadsheetCell(stringToDouble(initialValue));
>    }
>    ```
>
>    这样看上去很合理，但是实际上，结果并不会像预期的那样显示的调用 SpreadsheetCell 构造函数实际上是新创建了一个 SpreadsheetCell 类型的临时未命名对象，而并不是像预期那样调用构造函数来初始化对象。
>
>    然而，由此出发 C++ 支持委托构造函数 (delegating constructors)，允许构造函数初始化器调用同一个类的其他构造函数进行初始化，这将在之后说明。
>
> 4. **默认构造函数**
>
>    默认构造函数没有参数，也称无参构造，是一种防御性编程，防止对未定义的数据元素进行调用的一种防范措施。
>
>    **什么时候需要默认构造函数？**
>
>    考虑一下对象数组。**创建对象数组需要完成两个任务：为所有对象分配内存连续的空间，为每个对象调用默认构造函数。C++ 没有提供任何语法，来让创建的数组的代码直接调用不同的构造函数。**例如，如果没有定义 SpreadsheetCell 类的默认构造函数，下面代码将无法编译：
>
>    ```C++
>    SpreadsheetCell cell[3];
>    SpreadsheetCell* myCell = new SpreadsheetCell[10];		// All Falls
>    ```
>
>    对于基于堆栈的数组，可使用下面的初始化器，绕过这个限制：
>
>    ```C++
>    SpreadsheetCell cell[3] = {SpreadsheetCell(0), SpreadsheetCell(23), SpreadsheetCell(41)};
>    ```
>
>    但是，很明显，这并不是一种很优雅的解决方法，因为每个数组都需要手动输入。显然，采用构建默认构造函数的方法，来自动创建数组的方式更加高效。
>
>    **PS：如果想在标准库容器内(例如 std::vector)中存储类，那么同样需要默认构造函数。**
>
>    在其他类中创建对象时，也可以使用默认构造函数，本节中 “5. 构造函数初始化器” 中将讲解。
>
>    **如何编写默认构造函数？**
>
>    下面时具有默认构造函数的 SpreadsheetCell 类的部分定义：
>
>    ```C++
>    class SpreadsheetCell
>    {
>    public:
>    	SpreadsheetCell();
>    	// Remainder of the class definition omitted for brevity.
>    };
>    ```
>
>    下面代码实现了默认构造函数：
>
>    `````C++
>    SpreadsheetCell::SpreadsheetCell()
>    {
>    	mValue = 0;
>    }
>    `````
>
>    如果 mValue 使用类内的初始化方式，则可以省略这个默认构造函数的一条语句：
>
>    ```C++
>    SpreadsheetCell::SpreadsheetCell()
>    {
>    
>    }
>    ```
>
>    可在堆栈中使用默认构造函数：
>
>    ```C++
>    SpreadsheetCell myCell;
>    myCell.setValue(6);
>    std::cout << "cell 1 : " << myCell.getCell() << std::endl;
>    
>    // 可能希望有人在堆栈中能够这样创建 默认构造函数：
>    SpreadsheetCell myCell();
>    // 但是，这种方式虽然能够编译，但是它后面的行将无法编译。
>    ```
>
>    **警告：**
>
>    ​	**切勿在创建对象时，直接使用默认构造函数；而是使用类名，让类自动调用其构造函数，这两种逻辑很不同。**
>
>    对于堆中的对象，可以这样使用默认构造函数：
>
>    ```C++
>    auto smartCellp = make_unique<SpreadsheetCell>(4);
>    // Or with a raw pointer (not recommended)
>    SpreadsheetCell* myCellp = new SpreadsheetCell;
>    // Or 
>    // SpreadsheetCell* myCellp = new SpreadsheetCell;
>    // ... use myCellp
>    delete myCellp;
>    myCellp = nullptr;
>    ```
>
>    **编译器生成的默认构造函数：**
>
>    本章的第一个 SpreadsheetCell 类定义如下所示：
>
>    ```C++
>    class SpreadsheetCell
>    {
>    public:
>    	void setValue(double inValue);
>    	double getValue() const;
>    
>    private:
>    	double mValue;
>    };
>    ```
>
>    这个类定义中没有声明任何默认构造函数，但以下代码仍可以正常运行：
>
>    ```C++
>    SpreadsheetCell myCell;
>    myCell.setValue(8);
>    // 当然，这是一种无参构造
>    ```
>
>    对比：
>
>    **如果这样类内仅有显式的含参构造，但是没有显式声明默认构造：**
>
>    ```C++
>    class SpreadsheetCell
>    {
>    public:
>    	SpreadsheetCell(double inValue);	// No default constructor
>    	// Remainder of the class definition omitted for brevity.
>    };
>    ```
>
>    而使用这种定义，下面代码将无法编译：
>
>    ```C++
>    SpreadsheetCell myCell;
>    myCell.setValue(6);
>    ```
>
>    为什么会这样呢？原因在于：**如果没有指定任何构造函数，编译器即会生成无参构造函数。**
>
>    类所有对象成员都可以调用编译器生成的默认构造函数，但不会初始化语言的原始类型，例如 int 和 double。
>
>    **如果显式地声明了默认构造函数或其他构造函数，编译器就不会再自动生成默认构造函数。**
>
>    **注意：**
>
>    ​	**默认构造函数与无参构造函数是一回事。术语 “默认构造函数” 不仅仅是说如果没有声明任何构造函数就会自动生成一个构造函数；而且如果没有参数，构造函数就采用默认值。**
>
>    **显式的默认构造函数：**
>
>    ​	为了避免手动地编写默认构造函数，C++ 现在支持显式的默认构造函数 (explicitly defaulted constructor)。可按如下方法编写类的定义，而不需要在实现文件中实现默认构造函数：
>
>    ```C++
>    class SpreadsheetCell
>    {
>    public:
>    	SpreadsheetCell() = default;		// 显式声明自动生成的默认构造函数
>    	SpreadsheetCell(double initialValue);
>    	SpreadsheetCell(std::string_view initialValue);
>    	// Remainder of the calss definition omitted for brevity.
>    };
>    ```
>
>    **显式删除构造函数：**
>
>    **C++ 还支持显式删除构造函数 (explicitly delete constructors)。例如，可定义一个只有静态方法的类(具体参见第 9 章) ，这个类没有任何构造函数，也不想让编译器生成默认构造函数。**在此情况下，可以显式地删除默认构造函数：
>
>    ```C++
>    class MyClass
>    {
>    public:
>    	MyClass() = delete;
>    }
>    ```
>
>    **目的：不希望存在默认构造函数；如果构建，即报错；**
>
> 5. **构造函数初始化**
>
>    本章到目前为止都是在讨论：**构造函数内初始化数据成员**；
>
>    但 C++ 提供了另一种在构造函数中初始化数据成员的方法，叫做 构造函数初始化器 或 ctor-initializer。下面的代码提供了 ctor-initializer 语法重写了没有参数的 SpreadsheetCell 构造函数：
>
>    ```C++
>    // 早古方法：
>    SpreadsheetCell::SpreadsheetCell(double initialValue)
>    {
>    	setValue(initialValue);
>    }
>    
>    // 构造函数初始化器
>    SpreadsheetCell::SpreadsheetCell(double initialValue) : mValue(initialValue)
>    {
>    
>    }
>    ```
>
>    **构造函数初始化器的结构：**
>
>    ​	**以冒号开始，以逗号分割；**
>
>    **使用 ctor-initializer 初始化数据成员与在构造函数体内初始化数据成员不同**：
>
>    ​	**当 C++创建某个对象时，必须在调用构造函数前创建对象的所有数据成员。**如果数据成员本身就是对象，那么在创建这些数据成员时，必须其调用构造函数。**在构造函数体内给某个对象赋值时，并没有真正创建这个对象，而只是改变对象的值。ctor-initializer 允许在创建数据成员时赋初值，这样做比在后面赋值效率高。**
>
>    如果类的数据成员是具有默认构造的类的对象，则不必再 ctor-initializer 中显式地初始化对象。例如：
>
>    ```C++
>    class MyClass
>    {
>    public:
>    
>    	MyClass()
>    	{
>    		// 其他初始化逻辑
>    	}
>    
>    private:
>    	std::string myString;  // std::string 默认构造函数将初始化为空字符串
>    };
>    /*对于类的数据成员，如果你没有在构造函数的初始化列表中为其提供初始值，而该类具有默认构造函数，那么默认构造函数会在对象创建时对成员进行初始化。*/
>    ```
>
>    **如果类的数据成员是没有默认构造函数的类的对象，则必须再 ctor-initializer；**
>
>    下面我们关注一下：
>
>    ​	如果类的数据成员是没有默认构造函数的类的对象，则必须在 ctor-initailizer 中显式初始化对象。例如，考虑下面的 SpreadsheetCell 类：
>
>    ```C++
>    class SpreadsheetCell
>    {
>    public:
>    	SpreadsheetCell(double d);
>    };
>    ```
>
>    SomeClass 构造函数的构造和实现如下：
>
>    ```C++
>    class SomeClass
>    {
>    public:
>    	SomeClass();
>    
>    private:
>    	SpreadsheetCell mCell;
>    };
>    
>    SomeClass::SomeClass() {}
>    ```
>
>    然而，这个实现无法成功完成编译代码。编译器不知道如何初始化 SomeClass 类的 mCell 数据成员，因为这个函数没有默认构造函数。
>
>    解决方案是在 ctor-initializer 中初始化 mCell 数据成员，示例如下：
>
>    ```C++
>    SomeClass::SomeClass() : mCell(1.0) {}
>    ```
>
>    注意：
>
>    ​	ctor-initializer 允许在创建数据成员时，执行初始化。
>
>    某些程序员喜欢在构造函数中提供初始值(即使这样做效率不高)。然而，某些数据类型必须在 ctor-initializer 中或使用类内初始器进行初始化。如下图所示：
>
>    ![image-20240226103931273](https://s2.loli.net/2024/02/26/X2YDxTJpBOiyEwf.png)
>
>    关于 ctor-initializer 要特别要注意，数据成员的初始化顺序为：按照它们在类定义中出现的顺序，而不是 ctor-initializer 中顺序。考虑下面的两个不同顺序造成的编译正确和错误的差异：
>
>    ```C++
>    // 正确顺序：
>    class Foo
>    {
>    public:
>    	Foo(double value);
>    
>    private:
>    	double mValue;
>    };
>    
>    Foo::Foo(double value) : mValue(value)
>    {
>    	std::cout << "Foo::mValue = " << mValue << std::endl;
>    }
>    
>    class MyCalss
>    {
>    public:
>    	MyClass(double value);
>    
>    private:
>    	double mValue;
>    	Foo mFoo;
>    };
>    
>    MyClass::MyClass(double value) : mValue(value), mFoo(mValue)
>    {
>    	std::cout << "MyClass::mValue = " << mValue << std::endl;
>    }
>    // 首先，看 private 中的数据成员，这决定了初始化赋值的顺序：先 mValue, 再 mFoo;
>    // 其次，看 MyClass 的初始化器，将 mValue 初始化为 value， 然后将 mValue 传递给 mFoo 类型，进而调用其含参构造函数
>    ```
>
>    ```C++
>    // 错误顺序：
>    class Foo
>    {
>    public:
>    	Foo(double value);
>    
>    private:
>    	double mValue;
>    };
>    
>    Foo::Foo(double value) : mValue(value)
>    {
>    	std::cout << "Foo::mValue = " << mValue << std::endl;
>    }
>    
>    class MyCalss
>    {
>    public:
>    	MyClass(double value);
>    
>    private:
>    	Foo mFoo;
>    	double mValue;
>    };
>    
>    MyClass::MyClass(double value) : mValue(value), mFoo(mValue)
>    {
>    	std::cout << "MyClass::mValue = " << mValue << std::endl;
>    }
>    // 首先，看 private 中的数据成员，这决定了初始化赋值的顺序：先 mFoo, 再 mValue;
>    // 其次，看 MyClass 的初始化器，希望初始化 mFoo, 但是传入参数为未赋值量，因此出现编译错误
>    ```
>
>    **警告：**
>
>    ​	**使用 ctor-initializer 初始化数据成员的顺序如下：按类定义中声明的顺序而不是 ctor-initializer 列表中的顺序。**
>
> 6. **复制构造函数**
>
>    通过传入 const 引用的形式，来对特定对象进行复制构造，其基本格式如下：
>
>    ```C++
>    classname::classname(const classname& src) : m1(src.m1), m2(src.m2), ..., mn(src.mn) {}
>    // src 是 source 的意思，即源对象
>    ```
>
>    因此，多数情况下，不需要亲自编写构造函数。
>
>    **什么时候调用复制构造函数**？
>
>    **隐式的复制构造函数：**
>
>    C++ 的默认传参方式是 值传递。这意味着函数或方法接受某个值或对象的副本。因此无论什么时候给函数或方法传递一个对象，编译器都会调用新对象的复制构造函数进行初始化。例如，假设以下 printString() 函数接收一个按值传入 string 参数：
>
>    ```C++
>    // 就是匿名对象或者匿名类型都是它的默认复制构造函数进行构造的
>    void printString(string inString)
>    {
>    	std::cout << inStirng << std::endl;
>    }
>    ```
>
>    回顾一下，string 实际上是一个类，而不是内置类型。
>
>    **显式的复制构造函数：**
>
>    ```C++
>    SpreadsheetCell myCell1(4);
>    SpreadsheetCell myCell2(myCell1);
>    ```
>
>    **不使用复制构造的按引用传递引用：**
>
>    提高效率而已。
>
>    **将复制构造函数定义为显式默认或显式删除**：
>
>    ```C++
>    SpreadsheetCell(const SpreadsheetCell& src) = default;
>    // 将复制构造函数设置为默认复制构造
>    ```
>
>    ```C++
>    SpreadsheetCell(const SpreadsheetCell& src) = delete;
>    // 将复制构造函数删除，达到禁止按 值传递 的作用，只能进行按引用传入
>    // 同样地，无法复制，使得对象作为函数 返回值
>    ```
>
>    这样的设计可能有以下几个目的：
>
>    1. **防止意外的对象拷贝：** 有时候，对象的拷贝可能是不希望的，特别是当对象包含资源管理的成员(例如动态分配的内存、文件句柄等)时。禁止拷贝构造函数可以确保在编译时防止这种不希望的拷贝。
>    2. **强调对象的唯一性：** 有些类可能被设计成具有独特性，例如单例模式，禁止拷贝构造函数可以强调这种独特性，确保只有一个实例存在。
>    3. **提高性能：** 某些情况下，通过禁止按值传递可以鼓励使用引用传递，避免了不必要的拷贝操作，提高了性能。
>
>    **注意：**
>
>    ​	**删除拷贝构造函数可能会限制类的使用方式，因此在实际应用中需要谨慎使用。在某些情况下，可以考虑使用移动语义(Move Semantics)和移动构造函数，以实现高效的对象传递和返回，而不是完全禁止值传递。**
>
> 7. **初始化列表构造函数 <initializer_list>**
>
>    **初始化列表构造函数(initializer-list constructors) 将 std::initializer_list<T> 作为第一个参数，并没有任何其他参数(或者其他参数具有默认值)。在使用 std::iinitializer_list<T> 模板之前，必须要包含 <initializer_list> 头文件。下面的类演示了这种用法。该类只接受 initializer_list<T> ，元素个数应该为偶数，否则抛出。****
>
>    ```C++
>    #include <iostream>
>    #include <vector>
>    #include <stdexcept>
>    #include <initializer_list> 
>    
>    using namespace std;
>    
>    class EvenSequence
>    {
>    public:
>    	// 构造函数，接受一个双精度浮点数的初始化列表
>    	EvenSequence(initializer_list<double> args)
>    	{
>    		// 如果初始化列表的大小不是偶数，抛出异常
>    		if (args.size() % 2 != 0)
>    		{
>    			throw invalid_argument("初始化列表应包含偶数个元素。");
>    		}
>    
>    		// 为序列预分配足够的空间
>    		mSequence.reserve(args.size());
>    
>    		// 遍历初始化列表，将元素添加到序列中
>    		for (const auto& value : args)
>    		{
>    			mSequence.push_back(value);
>    		}
>    	}
>    
>    	// 打印序列的内容，dump 倾倒 的意思
>    	void dump() const
>    	{
>    		for (const auto& value : mSequence)
>    		{
>    			cout << value << ", ";
>    		}
>    		cout << endl;
>    	}
>    
>    private:
>    	// 存储双精度浮点数的序列
>    	vector<double> mSequence;
>    };
>    
>    int main()
>    {
>    	// 创建一个包含偶数个元素的序列对象
>    	EvenSequence sequence1 = { 1.0, 2.0, 3.0, 4.0 };
>    
>    	// 打印序列内容
>    	sequence1.dump();
>    
>    	try
>    	{
>    		// 尝试创建一个包含奇数个元素的序列对象，将抛出异常
>    		EvenSequence sequence2 = { 1.0, 2.0, 3.0 };
>    	}
>    	catch (const exception& e)
>    	{
>    		// 捕获异常并打印错误消息
>    		cout << "异常捕获: " << e.what() << endl;
>    	}
>    
>    	return 0;
>    }
>    
>    // 输出：
>    1, 2, 3, 4,
>    异常捕获: 初始化列表应包含偶数个元素。
>    ```
>
>    **标准库完全支持初始化列表构造函数**，例如：
>
>    ```C++
>    std::vector<std::string> myVec = { "String 1", "String 2", "String 3" };
>    
>    // 如果不使用初始化构造免责可以通过库内方法进行初始化：
>    std::vector<std::string> myVec;
>    myVec.push_back("String 1");
>    myVec.push_back("String 2");
>    myVec.push_back("String 3");
>    ```
>
>    **初始化列表不限于构造函数，还可用于普通函数，如第1章 所述。**
>
> 8. **委托构造函数**
>
>    委托构造函数 (delegating constructors) 允许构造函数调用同一个类的其他构造函数。然而，这个调用不能放在构造函数体，而必须放在构造函数初始化器中，而且必须是列表中唯一的初始化器。下面给出了一个示例：
>
>    ```C++
>    SpreadsheetCell::SpreadsheetCell(std::string_view initialValue)
>    	: SpreadsheetCell(stringToDouble(intialValue))
>    {
>    
>    }
>    ```
>
>    当调用这个 std::string_view 构造函数(委托构造函数)时，首先将调用委托给目标构造函数，也就是 double 构造函数。当目标构造函数返回是，再执行委托构造函数。
>
>    当使用委托构造函数时，要注意避免出现构造函数的递归。例如：
>
>    ```C++
>    class MyClass
>    {
>    	MyClass(char c) : MyClass(1.2) { }
>    	MyClass(double d) : MyClass('m') { }
>    };
>    // 第一个构造函数委托第二个构造函数，第二个构造函数又委托第一个构造函数。
>    // C++ 没有定义这种代码的行为，这完全取决于编译器。
>    ```
>
> 9. **总结编译器生成的构造函数**
>
>    **编译器为每个类自动生成没有参数的构造函数和复制构造函数。然而，编译器自动生成的构造函数取决于你自己定义的构造函数，对应规则如下：**
>
>    ![image-20240226134735142](https://s2.loli.net/2024/02/26/rVSMPiFjDExesdO.png)
>
>    **注意：默认构造函数和复制构造函数之间缺少对称性。**
>
>    - **只要没有显式定义复制构造函数，编译器就会自动生成一个。**
>
>    - **只要定义了任何构造函数，编译器就不会生成默认构造函数。**
>      - **复制构造函数也是构造函数。**
>      - **可以通过构造函数定义为显示默认或显式删除来影响自动生成的默认构造函数和默认复制构造函数。**
>
>    **注意：**
>
>    - **构造函数的最后一种是移动构造函数，用于实现移动语义，移动语义，可用于某些情况下提高性能，详见第 9 章。**

****

#### 3.2销毁对象

> 当销毁对象时，会发生两件事：
>
> - **调用对象的析构函数；**
> - **释放对象占用的内存；**
>
> **在析构函数中可以执行对象的清理，例如，释放动态分配的内存或关闭文件句柄。如果没有声明析构函数，编译器将自动生成一个，析构函数会逐一销毁成员，然后删除对象。第9章的 9.2 节将介绍如何编写析构函数。**
>
> 当堆栈中的对象超出作用域时，意味着当前的函数、方法或其他执行代码块结束，对象会被销毁。换句话说，当代码遇到结束大括号时，这个大括号中所有创建在堆栈中的对象都会被销毁。下面的程序显示了这个行为：
>
> ```C++
> int main()
> {
> 	SpreadsheetCell myCell(5);
> 	if (myCell.getValue() == 5)
> 	{
> 		SpreadsheetCell anotherCell(6);
> 	}
> 	// anotherCell is destroyed as this block ends.
> 
> 	std::cout << "myCell : " << myCell.getValue() << std::endl;
> 
> 	return 0;
> }
> // myCell is destroyed as this block ends.
> ```
>
> 堆栈中对象的销毁顺序与声明顺序(和构建顺序)相反。例如，在下面的代码片段中，myCell2 在 anotherCell2 之前分配，因此 anotherCell2 在 myCell2 之前销毁(注意在程序中，可以使用大括号在任意点开始新的代码块)：
>
> ```C++
> {
> 	SpreadsheetCell myCell2(4);
> 	SpreadsheetCell anotherCell2(5);
> 	// myCell2 constructed before anotherCell2
> }
> // anotherCell2 destroyed before myCell2
> ```
>
> **如果某个对象是其他对象的数据成员，这一顺序也使用。数据成员的初始化顺序是它们在类中声明的顺序。因此，按对象的销毁顺序与创建顺序相反这一规则，数据成员对象的销毁顺序与其在类中声明的顺序相反。**
>
> ```C++
> {
> 	SpreadsheetCell* cellPtr1 = new SpreadsheetCell;
> 	SpreadsheetCell* cellPtr2 = new SpreadsheetCell;
> 	std::cout << "cellPtr1 : " << cellPtr1->getValue() << std::endl;
> 	delete cellPtr1;
> 	return 0;
> }
> // cellPtr2 is NOT destroyed because delete was not called on it.
> ```
>
> **注意：**
>
> ​	**析构函数的生成和调用在C++中是由系统自动管理的，通常不需要显式地删除。**

****

#### 3.3对象赋值

> 就像 string 变量可以给 另一个 string 变量赋值一样，在 C++ 内也可将一个对象的值赋给另一个对象。例如：
>
> ```C++
> SpreadsheetCell myCell(5), anotherCell;
> anotherCell = myCell;
> ```
>
> **注意：**
>
> ​	**赋值不是复制，复制只发生在构造函数中，赋值发生在上述情况。**
>
> **C++ 为所有类提供了执行赋值的方法。这个方法叫作 赋值运算符(assignment operator)，名称是 operator=，因此实际上为类重载了 = 运算符。自动默认构造这种赋值运算符。上例中，调用了 anotherCell 的赋值运算符，参数为 myCell。**
>
> **注意：**
>
> ​	**本章所讲的赋值运算符有时也称为复制赋值运算符(copy assignment operator)，因为在赋值后，左边和右边都继续存在。之所以要这样区分，是因为由移动赋值运算符(move assignment operator)。为提高性能，当赋值结束后右边的对象会被销毁。移动赋值运算符将在第9章。**
>
> ​	**如果没有编写自己的赋值运算符，C++ 将自动生成一个，从而允许将对象赋给另一个对象，默认的 C++ 赋值行为几乎与默认复制行为相同：以递归方式用源对象的每个数据成员并赋值给目标对象。**
>
> 1. **声明赋值预算符**
>
>    下面是 SpreadsheetCell 类的赋值运算符：
>
>    ```C++
>    class SpreadsheetCell
>    {
>    public:
>    	SpreadsheetCell& operator=(const SpreadsheetCell& rhs);
>    	// Remainder of the class definition omitted for brevity.
>    	// 在此情况下，将源文件称为 rhs，代表等号的“右边”(可为其指定其他任何名称)
>    };
>    ```
>
>    赋值运算符与复制构造函数类似，采用了源文件的 const 引用。调用赋值运算符的对象在等号的左边。
>
>    与复制构造函数不同的是，赋值运算符返回 SpreadsheetCell 对象的引用。原因是赋值可以链接在一起，如下所示：
>
>    ```C++
>    myCell = anotherCell = aThirdCell;
>    ```
>
>    执行这一行时，首先给 anotherCell 调用赋值运算符，aThirdCell 是“右边”的参数。随后给 myCell 调用赋值运算符。然而，此时 anotherCell 并不是参数。右边的值是将 aThirdCell 赋值给 anotherCell 时赋值运算符的返回值。如果赋值运算符不返回结果，myCell 将无法赋值。
>
>    为什么 mCell 的赋值运算符不能将 anotherCell 当作参数？就是说，为什么上述代码是那样的执行顺序？原因是等号实际上是方法调用的缩写，而完整函数是如下：
>
>    ```C++
>    myCell.operator=(anotherCell.operator=(aThirdCell));
>    ```
>
>    现在可以看到， anotherCell 调用的 operator= 必须返回一个值，这个值会传递给 myCell 调用的 operator=。正确的返回值是 anotherCell 本身，这样它就可以赋值给 myCell 的源对象。然而，直接返回 anotherCell 的效率不高，因此返回对 anotherCell 的引用。
>
>    **警告：**
>
>    ​	**实际上可以让赋值运算符返回任意类型，包括 void。然而，应该返回被调用对象的引用。**
>
> 2. **定义赋值运算符**
>
>    赋值运算符的实现与复制构造函数类似，但是存在重大区别。首先，复制构造函数只有才初始化时才调用，此时目标对象还没有有效的值。赋值运算符可以改写对象的当前值。在为对象动态分配内存之前，可以不考虑这个问题，第9章将讨论这些问题。其次，在C++ 中允许将对象的值赋给自己，例如：
>
>    ```C++
>    SpreadsheetCell cell(4);
>    cell = cell;	// Self-assignment
>    ```
>
>    赋值运算符不应该阻止自赋值。在 SpreadsheetCell 类中，这并不重要，因为它的唯一数据成员是基本类型 double。但当类具有动态分配的内存或其他资源时，必须将自赋值考虑在内。详细见 第9章。为组织此类情况发生，赋值运算符通常在方法开始时检测自赋值，如果发现自赋值，则立即返回。
>
>    ```C++
>    SpreadsheetCell& SpreadsheetCell::operator=(const SpreadsheetCell& rhs)
>    {
>    	if (this == &rhs)
>    	{
>    		return *this;
>    	}
>    	// 自赋值检查
>    	mValue = rhs.mValue;
>    	return *this;
>    }
>    
>    // 注意：即使这里是返回引用也不会形成参数之间的共值。
>    // 原因在于，即使返回传引用但还是在这个 operator= 的框架之下进行的赋值方法操作内对自身类内数据成员进行赋值。
>    	// 之所以这里会有疑问，是因为有以下情况：
>    int main()
>    {
>    	SpreadsheetCell* aCellp = new SpreadsheetCell(5);
>    	SpreadsheetCell* bCellp = new SpreadsheetCell;
>    
>    	bCellp->setValue(3);
>    	std::cout << aCellp->getValue() << std::endl;
>    	std::cout << bCellp->getValue() << std::endl;
>    	delete bCellp;
>    	bCellp = aCellp;
>    	std::cout << aCellp->getValue() << std::endl;
>    	std::cout << bCellp->getValue() << std::endl;
>    	bCellp->setValue(12);
>    	std::cout << aCellp->getValue() << std::endl;
>    	std::cout << bCellp->getValue() << std::endl;
>    
>    	delete aCellp;
>    	aCellp = nullptr; // 将指针设置为 nullptr，避免后续误用
>    
>    	return 0;
>    }
>    
>    // 输出：
>    5
>    3
>    5
>    5
>    12
>    12
>    
>    // 很明显，你是混淆了 Python 中的 a = b; a copy b; a deepcopy b;的三种情况。
>    	// a = b 在 Python 中，是一种指针拷贝；
>    		// a copy b 在 Python 中，是一种浅拷贝；
>    	// a deepcopy 在 Python 中，是一种深拷贝；
>    ```
>
>    **注意：**
>
>    ​	**此处显示 SpreadsheetCell 赋值运算符只是为了演示目的。实际上，这种情况下，由于默认的由编译器生成的运算符已经足以满足要求，本可以省去这里的赋值运算符；它只是对所有数据成员进行 member-wise 赋值。然而在某些情况下，默认赋值运算符的功能不足。第 9 章将讲述这些情况。**
>
> 3. **显式地默认或删除赋值运算符**
>
>    ```C++
>     SpreadsheetCell& SpreadsheetCell::operator=(const SpreadsheetCell& rhs) = default;
>    ```
>
>     ```C++
>    SpreadsheetCell& SpreadsheetCell::operator=(const SpreadsheetCell& rhs) = delete;
>     ```

****

#### 3.4编译器生成的赋值构造函数和复制赋值运算符

>在 C++11 中，如果类具有用户声明的复制赋值构造函数或析构函数，那么已经不赞成生成复制构造函数。如果在此类情况下仍然需要编译器生成的复制构造函数，可以显式指定 default：
>
>```C++
>MyClass(const MyClass& src) = default;
>```
>
>同样，在 C++11 中，如果类具有用户声明的复制赋值构造函数或析构函数，也不赞成生成复制赋值运算符。如果在此类情况下仍然需要编译器生成的复制赋值运算符，可以显式指定 default：
>
>```C++
>MyClass& operator=(const MyClass& rhs) = default;
>```

****

#### 3.5复制和赋值

> 在堆栈中，其实赋值和复制都差不多。基本上，声明时会使用复制构造函数，赋值语句会使用赋值运算。考虑下面代码：
>
> ```C++
> SpreadsheetCell myCell(5);
> SpreadsheetCell anotherCell(myCell);
> // anotherCell 由复制构造函数创建
> 
> SpreadsheetCell aThirdCell = myCell;
> // aThirdCell 也是由复制构造函数创建的，因为这条语法是一个声明，不会调用到 operator=.
> // 相当于下面代码的另一个版本：
> SpreadsheetCell aThirdCell(myCell);
> 
> // 但是，考虑以下代码：
> anotherCell = myCell;
> // 此时，anotherCell 已经构建，此时会调用 operator=
> ```
>
> **总结：**
>
> - **声明时，只可能是 调用复制构造函数；**
>
> - **当对象已创建则 调用复制赋值运算符；**
>
> 1. **按值返回对象**
>
>    当函数或方法返回对象时，有时很难看出究竟执行了怎样的复制和赋值。例如，SpreadsheetCell::getString() 的实现如下：
>
>    ```C++
>    std::string SpreadsheetCell::getString() const
>    {
>    	return doubleToString(mValue);
>    }
>    ```
>
>    现在考虑以下代码：
>
>    ```C++
>    SpreadsheetCell myCell(5);
>    string s1;
>    s1 = myCell.getString();
>    ```
>
>    当 getString() 返回 mString 时，编译器实际上调用了 **string 复制构造函数**，创建了一个未命名的临时字符串对象将结果，赋给 s1 时，会调用 **s1 的赋值运算符**，将这个临时字符串作为参数。然后，这个临时的字符串对象那个被销毁。因此，这行简单的代码会首先执行复制构造函数和复制构造对象(分别对 myCell.getString() 和 s1)。然而，编辑器可实现(有时需要实现)返回值优化(Return Value Optimization, RVO)，在返回值时优化掉成本高的复制构造函数，RVO 也被称为 复制省略(copy elision).
>
>    了解上述内容后，考虑之后的代码：
>
>    ```C++
>    SpreadsheeetCell myCell3(5);
>    string s2 = myCell3.getString();
>    ```
>
>    在此情况下，getString() 返回时，创建了一个临时的未命名字符串对象。但是现在调用的时复制构造函数而不是赋值赋值运算符。
>
>    通过移动语义(move semantics)，编译器可使用移动构造函数而不是复制构造函数，从 getStirng() 返回该字符串，这样做更高效。第 9 章将讨论移动语义。
>
>    如果忘记这些事情发生的顺序，或忘记调用哪个构造函数或运算符，只要在代码中临时包含帮助输出或调用调试器逐步调用代码，就能很容易找到答案。
>
> 2. **复制构造函数和对象成员**
>
>    还应注意构造函数中赋值和调用赋值构造函数的不同之处。如果某个对象包含其他对象，编译器生成的复制构造函数会递归调用每个被包含对象的复制构造函数。当编写自己的复制构造函数时，可使用前面所示的 ctor-initializer 提供相同的语义。如果在 ctor-initializer 中省略某个数据成员，在执行构造函数体内的diamagnetic之前，编译器将对该对象执行默认的初始化(为对象调用默认构造函数)。这样，在执行构造函数体时，所有数据成员都已初始化。
>
>    例如，可这样编写复制构造函数：
>
>    ```C++
>    SpreadsheetCell::SpreadsheetCell(const SpreadsheetCell& src)
>    {
>    	mVale = src.mValue;
>    }
>    ```
>
>    复制构造函数的函数体内对数据成员赋值时，使用的是赋值运算符而不是复制构造符，因为他们已经初始化了，就像前面讲述的那样。
>
>    如果编写如下代码复制构造函数，则使用复制构造函数初始化 mValue：
>
>    ```C++
>    SpreadsheetCell::SpreadsheetCell(const SpreadsheetCell& src)
>    	: mValue(src.mValue)
>    {
>                                                                            
>    }
>    ```
>

****

### 8.4本章小结

> 本章讲述了 C++ 为面向对象的基本工具：类和对象。首先回顾编写类和使用对象的基本语法，包含访问控制。然后讲述了对象的生命周期；什么时候构建、销毁、和赋值，这些操作会调用哪些方法。本章包含构造函数的语法细节，包括 ctor-initializer 和初始化列表构造函数，此外还介绍了复制赋值运算符的概念。本章还明确指出在什么情况下，编译器会自动生成什么样的构造函数，并解释了没有参数的默认构造函数。
>
> 对于某些人来说，本章基本只是回顾，对另一些人来说，通过本章可更好地了解 C++ 中面向对象编程世界。无论如何，我们都已经认识到了 类和对象，可以通过下一章获取更多技巧。

****

## 第9章 —— 精通类与对象

> 第8章讲述了类和对象，这一章将讲述其精妙之处——如何操纵并利用 C++ 语言中最复杂的特性，以编写安全、有效、有用的类。本章的许多概念会出现在 C++ 高级编程中，特别是 标准库。

****

### 9.1友元

> C++ 允许某个类将其他类、其他类的成员函数或非成员函数声明为 友元(friend)，友元可以访问类的 protected、private 数据成员和方法。例如，假设有两个类 Foo 和 Bar。可将 Bar 类指定为 Foo 类的友元，如下例所示：
>
> ```C++
> class Foo
> {
> 	friend class Bar;	// 认为 Bar 是 friend，但是不代表 Bar 也认定 Foo 为 friend
> };
> ```
>
> 现在，**Bar 类的所有成员可访问 Foo 类的 private、protected 数据成员和方法。**
>
> 也可将 Bar 类的一个特定方法作为友元。假设 Bar 类拥有一个 processFoo(const Foo& foo) 方法，下面的语法将该方法成为 Foo 类的友元：
>
> ```C++
> class Foo
> {
> 	friend void Bar::processFoo(const Foo& foo);
> };
> ```
>
> 独立函数也可以成为类的友元。例如，假设要编写一个函数，将 Foo 对象的所有数据转储到控制台。你可能希望将这个函数放在 Foo 类之外，以模拟外部审计，但该函数应当可以访问 Foo 对象的内部数据成员，对其进行适当检查。下面是 Foo 类定义和 dumpFoo() 友元函数：
>
> ```C++
> class Foo
> {
> 	friend void dumpFoo(const Foo& foo);
> };
> ```
>
> 类中的 friend 声明用作函数的原型。不需要在别处编写原型(当然，如果你那样做，也无害处)。
>
> 下面是函数定义：
>
> ```C++
> void dumpFoo(const Foo& foo)
> {
> 	// Dump all data of foo to the console, including
> 	// private and protected data members.
> 	// 该函数可以获取了访问 dumpFoo 的 成员 
> }
> ```
>
> 你编写的函数与其他函数类似，只是可以用这个函数直接访问 Foo 类的 private 和 protected 数据成员。在函数定义中不需要重复使用 friend 关键字。
>
> **注意类需要知道其他哪些类、方法或函数希望成为友元；类、方法或函数不能将自身声明为其他类的友元并访问这些类的非公有名称。**
>
> friend 类和方法很容易被滥用；友元可以违反封装原则，将类的内部暴露给其他类或函数。因此，只有在特定的情况下才应该使用它们，本章将穿插介绍一些用例。

****

### 9.2对象的动态内存分配

> 为解决在程序实际运行前，并不知道需要多少内存的问题；那么就要动态地分配内存。类也不例外，有时不知道某个对象需要多少内存，在这种情况下，就要动态内存分配。但是，对于类而言，它的构建、复制、析构、赋值等就面临内存泄漏的严重问题，这种情况就需要我们对析构、复制、赋值函数进行重新构造。

****

#### 2.1Spreadsheet 类

>与 SpreadsheetCell 类 类似，Spreadsheet 类将在本章中不断被完善。因此我们将在不断尝试中，说明编写类的最佳方法。
>
>Spreadsheet 的最初版本只是一个 Spreadsheet 类的二维数组，其中具有设置和获取 SpreadsheetCell 中特定的类的最佳方式，其中具有设置和获取 Spreadsheet 中特定位置单元格的方法。尽管大多数电子表格应用程序为了指定单元格，会在一个方向上使用字母，但此处的 Spreadsheet 类在两个方向上均使用数字(仅为说明应该如何构建类)，下面为一个简单定义：
>
>```C++
>#include <cstddef>
>#include "SpreadsheetCell.h"
>
>class Spreadsheet
>{
>public:
>	SpreadsheetCell(size_t width, size_t height);
>	void setCellAt(size_t x, size_t y, const SpreadsheetCell& cell);
>	SpreadsheetCell& getCellAt(size_t x, size_t y);
>
>private:
>	bool inRange(size_t value, size_t upper) const;
>	size_t mWidth = 0;
>	size_t mHeight = 0;
>	SpreadsheetCell** mCells = nullptr;
>};
>
>/* 注意：这里仍然使用的是 SpreadsheetCell 的普通指针。这一方法将贯穿整个第 9 章，目的是说明因果关系，以及金额是如何在类中处理动态内存分配问题。在产品中，应该使用标准的 C++ 容器，例如：std::vector 的嵌套可极大地简化 Spreadsheet 类的实现，但是目前还没学习该如何使用裸指针正确处理动态内存，这如果不讲，当遇到旧代码可能会手足无措，那么接下来还是至少能够看懂这些代码的，所以还要讲。*/
>// 但是，在现代 C++ 中，绝对不要使用裸指针！！！
>// 因为，裸指针不仅语法复杂，而且内存泄漏、指针悬空出现得十分隐蔽。
>```
>
>为什么不直接包含一个 Spreadsheet 二维数组，而是一个 Spreadsheet 的二阶指针？
>
>> 因为， Spreadsheet 对象的尺寸可能不同，如果给定二维数组，那么将失去调整宽度和高度的动态分配的灵活性。【在这里我们也知道，指针具有更高的灵活性，但是也继承了更多在内存则责任，安全性堪忧】，注意在 C++  中，不可能之编写 new SpreadsheetCell[mWidth] [mHeight],这与 Java 不同【这里为什么这样说，不能 new 出来一个二维数组，请看前面的第 7 章使用指针部分，哪里有关于这一点的详细说明】：
>
>> ```c++
>> Spreadsheet::Spreadsheet(size_t width, size_t height)
>> 	: mWidth(width), mHeight(height)
>> {
>>  	mCells = new SpreadsheetCell * [mWidth];
>>  	for (size_t i = 0; i < mWidth; i++)
>>  	{
>>    		mCells[i] = new Spreadsheet[mHeight];
>>  	}
>> }
>> ```
>
>堆栈为名为 s1 的 Spreadsheet 对象分配的内存，如图 9-1 所示，宽度为 4，高度为 3；
>
>![image-20240228142230920](https://s2.loli.net/2024/02/28/qzRuvh6VMH19dfY.png)
>
>设置和获取方法的实现简单明了：
>
>```C++ 
>void Spreadsheet::setCellAt(size_t x, size_t y, const SpreadsheetCell& cell)
>{
> 	if (!inRange(x, mWidth) || !inRange(y, mHeight))
> 	{
> 		throw std::out_of_range("");
> 	}
>
> 	mCell[x][y] = cell;
>}
>
>SpreadsheetCell& Spreadsheet::getCellAt(size_t x, size_t y)
>{
> 	if (!inRange(x, mWidth) || !inRange(y, mHeight))
> 	{
> 		throw std::out_of_range("")
> 	}
>
> 	return mCell[x][y];
>}
>
>// 上述代码使用了辅助方法 inRange() 检测 x 和 y  是否有效。试图通过索引范围外的数组元素将导致程序故障
>// 这个示例也是用了第 1 章提及，并将在第 14 章详细讲述的异常
>```
>
>这时，我们看到实际上两个方法 setCellAt() 和 getCellAt() 中，有相当部分的代码是重复的，我们在第 6 章学过，要不惜一切地重用代码：
>
>```C++
>// 依照复用的原则，那么定义 verifyCoordinate() 方法而非辅助方法 inRange()；
>void verifyCoodination(size_t x, size_t y) const;
>
>// 实现该类检查指定坐标，如果坐标无效，则抛出异常：
>void Spreadsheet::verifyCoordinate(size_t x, size_t y) const
>{
> 	if (x >= mWidth || y >= mHeight)
> 	{
> 		throw std::out_of_range("");
> 	}
>}
>
>// 重写 setCellAt() 和 getCellAt() 方法：
>void Spreadsheet::setCellAt(size_t x, size_t y, const SpreadsheetCell& cell)
>{
> 	verifyCoordinate(x, y);
>
> 	mCell[x][y] = cell;
>}
>
>SpreadsheetCell& Spreadsheet::getCellAt(size_t x, size_t y)
>{
> 	verifyCoordinate(x, y);
>
> 	return mCell[x][y];
>}
>```

****

#### 2.2使用析构函数释放内存

> 如果不再需要动态分配的内存，就必须释放它们。如果为对象动态分配了内存，就在析构函数中释放内存。当销毁对象时，编译器确保调用析构函数。下面是带有析构函数的 Spreadsheet 类定义。  
>
> ```C++
> class Spreadsheet
> {
> public:
> 	Spreadsheet(size_t width, size_t height);
> 	~Spreadsheet();
> 	// Code omitted for brevity
> };
> ```
>
> **析构函数与类(和构造函数)同名，名称前面有一个波浪号(~)。析构函数没有参数，并且只能有一个析构函数，为析构函数隐式地标记 noexcept，因为它们不应当抛出异常。**
>

**注意：**

> ​	**可使用 noexpect 标记函数，指示不会抛出异常。例如：**
>
> ```C++
> void myNonThrowingFunction() noexcept { /* ... */ }
> ```
> 
> **析构函数隐式地使用 noexcept，因此不必专门添加这个关键字。******如果 noexcept 函数真的抛出了异常，程序将终止。**有关 noexcept 的更多信息，以及为什么必须避免析构函数抛出异常的信息，详细参见第 14 章。
> 
> 下面为析构函数 ~Spreadsheet() 进行实现：
> 
> ```C++
>Spreadsheet::~Spreadsheet()
> {
>	for (size_t i = 0; i < mWidth, i++)
> 	{
>  		delete[] mCells[i];
>   		// 释放一阶指针创建的二阶指针创建的数组资源
>	}
> 
> 	delete[] mCells;
> 	// 释放一阶指针创建的数组资源
>	mCells = nullptr;
> }
>```
> 
>析构函数释放在构造函数中分配的内存。当然，并没有规则要求在析构函数中释放内存。在析构函数中可以编写任何代码，但最好让析构函数只释放内存或清理其他资源。

****

#### 2.3处理复制和赋值

> 回顾第 8 章，如果没有自行编写复制构造函数或赋值运算符，C++ 将自动生成。编译器生成的方法递归调用对象数据成员的复制构造函数或赋值构造函数。然而对于基本类型，如 int、double 和 指针，只是提供表层(或按位)复制或赋值；只是将数据成员从元对象中直接复制或复制到目标对象。当为对象动态分配内存时，这样做会引发问题。例如，在下面的代码中，当 s1 传递给函数 printSpreadsheet() 时，复制了电子表格 s1 以初始化 s：
>
> ```C++
> #include "Spreadsheet.h"
> void printspreadsheet(Spreadsheet s)		// 复制步骤发生在这里，这是隐式匿名的
> {
> 	// Code omitted for brevity.
> }
> 
> int main()
> {
> 	Spreadsheet s1(4, 3);
> 	printSpreadsheet(s1);
> 
> 	return 0;
> }
> ```
>
> Spreadsheet 包含一个指针变量: mCells。 Spreadsheet 的表层复制向目标对象提供了一个 mCells 指针的副本,但没有复制底层数据【只复制浅层量，即，二阶指针创建的一阶指针数组】。最终结果是 s 和 s1 都有一个指向同一数据的指针，如图 9.2 所示。  
>
> ![image-20240228144529144](https://s2.loli.net/2024/02/28/1AGY8lFnkiBr7JQ.png)
>
> 如果 s 修改了 mCells 所指的内容，这一改动也会在 s1 中表现出来。更糟糕的是，当函数 printSpreadsheet() 退出时，会调用 s 的析构函数【匿名函数自动调用析构函数，释放二阶指针所指空间】，释放 mCells 所指的内存。图 9-3 显示了这一状况 :
>
> ![image-20240228144729062](https://s2.loli.net/2024/02/28/LGFtNBimkceVr8M.png)
>
> 现在 s1 拥有的指针所指的内存不再有效，这称为悬空指针(dangling pointer)。令人难以置信的是，当使用赋值时，情况会变得更糟。假定编写以下代码：
>
> ```C++
> Spreadsheet s1(2, 2), s2(4, 3);
> s1 = s2;
> ```
>
> 在第一行后，当创建两个对象时，内存的布局如图 9-4 所示：
>
> ![image-20240228150434487](https://s2.loli.net/2024/02/28/THZzqK9hO2UtoA8.png)
>
> 当执行赋值语句后，内存布局如 9-5 所示：
>
> ![image-20240228150527146](https://s2.loli.net/2024/02/28/GbieDx7p61Sw3kd.png)
>
> 现在，不仅 s1 和 s2 中的 mCell 指向同一内存，而且 s1 前面所指的内存被遗弃。这称为内存泄漏。这就是在赋值运算中进行自定义的深层复制的原因了。
>
> **可以看出，依赖 C++ 默认的复制构造函数 或 赋值运算符 对于堆上的对象而言并不是健全的。**
>
> 警告：
>
> ​	无论什么时候，在类中动态分配内存后，应该编写自己的复制构造函数和赋值运算符，以提供深层次的内存复制。
>
> 1. **Spreadsheet 类的复制构造函数**
>
>    下面是 Spreadsheet 类中复制构造函数的声明：
>
>    ```C++
>    class Spreadsheet
>    {
>    public:
>    	Spreadsheet(const Spreadsheet& src);
>    };
>    ```
>
>    下面是复制构造函数的定义：
>
>    ```C++
>    Spreadsheet::Spreadsheet(const Spreadsheet& src)
>    	: Spreadsheet(src.mWidth, src.mHeight)
>    {
>    	for (size_t i = 0; i < mWidth; i++)
>    	{
>    		for (size_t j = 0; j < mHeight; j++)
>    		{
>    			mCells[i][j] = src.mCells[i][j];
>    		}
>    	}
>    }
>    ```
>
>    注意使用了委托构造函数。把这个复制构造函数的 ctor-initializer(构造函数初始化器)首先委托给非复制构造函数，以分配适当的内存量。复制构造函数此后复制实际值。总之，对 mCells 动态分配的二维数组进行了深层复制。
>
> 2. **Spreadsheet 类的赋值运算符**
>
>    下面是包含赋值运算符的 Spreadsheet 类定义：
>
>    ```C++
>    class Spreadsheet
>    {
>    public:
>    	Spreadsheet& operator=(const Spreadsheet& rhs);
>    	// Code omitted for brevity.
>    }
>    ```
>
>    下面是一个不成熟的实现：
>
>    ```C++
>    Spreadsheet& Spreadsheet::operator=(const Spreadsheet& rhs)
>    {
>    	// Check for self-assignment
>    	if (this == &rhs)
>    	{
>    		return *this;
>    	}
>    
>    	// Free the old memeory
>    	for (size_t i = 0; i < mWidth; i++)
>    	{
>    		delete[] mCells[i];
>    	}
>    	delete[] mCells;
>    	mCells = nullptr;
>    
>    	// Allocate new memory
>    	mWidth = rhs.mWidth;
>    	mHeight = rhs.mHeight;
>    
>    	mCells = new SpreadsheetCell * [mWidth];
>    	for (size_t i = 0; i < mWidth; i++)
>    	{
>    		mCells[i] = new SpreadsheetCell[mHeight];
>    	}
>    
>    	// Copy the data
>    	for (size_t i = 0; i < mWidth; i++)
>    	{
>    		for (size_t j = 0; j < mHeight; j++)
>    		{
>    			mCells[i][j] = rhs.mCells[i][j];
>    		}
>    	}
>    
>    	return *this;
>    };
>    ```
>
>    **这个方法存有不少问题，有不少地方会出错。this 对象可能进入无效状态。例如，假设成功释放了内存，合理设置了 mWidth 和 mHeight, 但分配内存的循环抛出了异常。如果发生这种情况，将不再执行该方法的剩余部分，而是从该方法中退出。此时，Spreadsheet 实例受损，它的 mWidth 和 mHeight 数据成员声明了指定大小，但 mCells 数据成员不具有适当的内存量。基本上，该代码不能安全地处理异常！**
>
>    **我们需要一种全有或全无的机制；要么全部成功，要么该对象保持不变。为实施这样一个能安全处理异常的赋值运算符，建议使用“复制和交换”惯用语法。这里将非成员函数 swap() 实现为 Spreadsheet 类的友元。如果不使用非成员函数 swap(), 那么可以给类添加 swap() 方法。但是，建议你练习将 swap() 实现为非成员函数，这样一来，各种标准库算法都可使用它。下面是包含 赋值运算符 和 swap 的函数的 Spreadsheet 类的定义**：
>
>    ```C++
>    class Spreadsheet
>    {
>    public:
>    	Spreadsheet& operator=(const Spreadsheet& rhs);
>    	friend void swap(Spreadsheet& first, Spreadsheet& second) const;
>    };
>    ```
>
>    要实现能安全处理异常的 “复制和交换” 惯用语法，要求 swap() 函数永不抛出异常，因此将其标记为 noexcept。swap() 函数的实现使用标准库中提供的 std::swap() 工具函数 (在头文件 <utility> 中定义)，交换每个数据成员:
>
>    ```C++
>    void swap(Spreadsheet& first, Spreadsheet& second) const
>    {
>    	using std::swap;
>    
>    	swap(first.mWidth, second.mWidth);
>    	swap(first.mHeight, second.mHeight);
>    	swap(first.mCells, second.mCells);
>    }
>    ```
>
>    现在就有了能安全处理异常的 swap() 函数，它可用来实现赋值运算符：
>
>    ```C++
>    Spreadsheet& Spreadsheet::operator=(const Spreadsheet& rhs)
>    {
>    	// Check for self-assignment
>    	if (this = &rhs)
>    	{
>    		return *this;
>    	}
>    
>    	Spreadsheet temp(rhs);	// Do all the work in a temporary instance
>    	swap(*this, temp);
>    	return *this;
>    }
>    ```
>
>    该实现使用“复制和交换”惯用语法。为提高效率，有时也为了正确性，赋值运算符的第一行检查自赋值。
>    
>    接下来，对右边进行复制，称为 temp。然后用这个副本替代*this。这个模式可确保“稳健地”安全处理异常(strong exception safety)。这意味着如果发生任何异常，当前的 Spreadsheet 对象保持不变。
>    
>    这通过三个阶段来实现：
>    
>    -   第一个阶段创建一个临时副本。这不修改当前 Spreadsheet 对象的状态，因此，如果在这个阶段发生异常，不会出现问题。
>    -   第二个阶段使用 swap()函数，将创建的临时副本与当前对象交换。swap() 永远不会抛出异常。
>    -   第三个阶段销毁临时对象(由于发生了交换，现在包含原始对象)以清理任何内存。
>    
>    注意：
>    
>    除复制外，C++ 还支持移动语义，移动语义需要移动构造函数和移动赋值运算符。在某些情况下，它们可以用来增强性能，稍后的章节“使用移动语义处理移动” 将对此进行详细讨论。
>
> 3. **禁止赋值和按值传递**
>    在类中动态分配内存时，如果只想禁止其他人复制对象或者为对象赋值，只需要显式地将 opemtok和复制构造函数标记为 delete。通过这种方法，当其他任何人按值传递对象时、从函数或方法返回对象时，或者为对象赋值时，编译器都会报错。下面的 Spreadsheet 类定义禁止赋值并按值传递：  
>
>    ```C++
>    class Spreadsheet
>    {
>    public:
>    	Spreadsheet(size_t width, size_t height);
>    	Spreadsheet(const Spreadsheet& src) = delete;
>    	~Spreadsheet();
>                            
>    	Spreadsheet& operator=(const Spreadsheet& rhs) = delete;
>    	// Code omitted for brevity
>    };
>    ```
>
>    不需要提供 delete 复制构造函数和复制运算符的实现。链接器永远不会查看它们，因为编译器不允许代码调用它们。当代码复制 Spreadsheet 对象或者对 Spreadsheet 对象的赋值时，编译器将给出：
>
>    ```C++
>    'Spreadsheet &Spreadsheet::operator =(const Spreadsheet &)' : attempting to reference a deleted function
>    ```
>
>    **注意：**
>
>    ​	**如果编译器不支持显式地删除成员函数，那么可以把复制构造函数和赋值运算符标记为 private，且不提供任何实现，从而禁用复制和赋值。**

****

#### 2.4使用移动语义处理移动

>   对象的移动语义(move semantics)需要实现移动构造函数(move constructor)和移动赋值符(move assignment operator)。如果源对象是操作结束后被销毁的临时对象，编译器就会使用这两个方法。移动构造函数和移动赋值运算符将数据成员从源对象移动到新对象，然后使得源对象处于有效但不确定的状态。通常会将源代码的数据成员重置为空值。这样做实际上将内存和其他资源的所有权从一个对象移动到另一个对象上，这两个方法基本上只是对成员变量进行表层复制(shallow copy)，然后转换已分配内存和其他资源的所有权，从而阻止悬空指针和内存泄漏。
>
>   **在实现移动语义前，需要学习右值(rvalue) 和 右值引用(rvalue reference)；**
>
>   1. **右值引用**
>
>       左值(lvalue)：已分配地址(可获取其指针)的名称量。此外，所有不是左值的量都是右值(rvalue)。
>
>       **右值引用是对右值(rvlaue)的引用。特别地，这是一个当右值是临时对象时才适用的概念。右值引用的目的是在涉及临时对象时提供可选用的特定函数。由于知道临时对象会被销毁，通过右值引用，某些涉及复制大量值的操作可通过简单地复制指向这些值的指针来实现。**  
>
>       **函数可将 && 作为参数说明的一部分(例如 type && name), 以指定右值引用参数。**通常，临时对象被当作 const type& , 但当函数重载使用了右值引用时，可以解析临时对象，用于该函数重载。下面的示例说明了这一点。代码首先定义了两个handleMessage() 函数，一个接收左值引用，另一个接收右值引用:
>
>       ```C++
>       // lvalue reference parameter
>       void handleMessage(std::string& message)
>       {
>       	std::cout << "handleMessage with lvalue reference: " << message << std::endl;
>       }
>
>       // rvalue reference parameter
>       void handleMessage(std::string&& message)
>       {
>       	std::cout << "handleMessage with rvalue reference: " << message << std::endl;
>       }
>       ```
>
>       **可使用具有名称的变量作为参数调用 handleMessage() 函数：**
>
>       ```C++
>       std::string a = "Hello";
>       std::string b = "World";
>       handleMessage(a);	// Calls handleMessage(string& value)
>       // 由于 a 是一个命名变量，调用 handleMessageo函数时，该函数接收一个左值引用。handleMessage() 函数通过其引用参数所执行的任何更改来更改 a 的值
>       ```
>
>       **注意：还可以用表达式作为参数来调用 handleMessage() 函数：**
>
>       ```C++
>       handleMessage(a + b);
>       // 此时无法使用接收左值引用作为参数的 handleMessage()函数，因为表达式 a+b 的结果是临时的，这不是一个左值。在此情况下，会调用右值引用版本。由于参数是一个临时值，handleMessage。函数调用结束后，会丢失通过引用参数所做的任何更改。
>       ```
>
>       **字面量也可作为 handleMessage() 调用的参数，此时同样会调用右值引用版本，因为字面量不能作为左值(但字面量可作为 const 引用形参的对应实参传递)。**  
>
>       ```C++
>       handleMessage("Hello World");	// Calls handleMessage(std::string&& value)
>       ```
>
>       **如果删除接收左值引用的 handleMessage。函数，使用有名称的变量调用 handleMessage() 函数 (例如handleMessage(b)), 会导致编译错误，因为右值引用参数 (string&& message) 永远不会与左值(b)绑定。如下所示，可使用 std::move()将左值转换为右值，强迫编译器调用 handleMessage() 函数的右值引用版本：**  
>
>       ```C++
>       handleMessage(std::move(b));	// Calls handleMessage(std::string&& value)
>       ```
>
>       重申一下，有名称的变量是左值，因此在 handleMessage() 函数中，右值引用参数 message 本身是一个左值，原因是它具有名称！如果希望将这个左值引用参数，作为右值传递【注意，不是复制】给另一个函数，则需要使用 std::move()，将左值转换为右值。例如，假设要添加以下函数使用右值引用参数：
>
>       ```C++
>       void helper(std::string&& message)
>       {
>       }
>       ```
>
>       如果按照如下方法调用，则无法编译：
>
>       ```C++
>       void handleMessage(std::string&& message)
>       {
>       	helper(message);
>       }
>       ```
>
>       helper() 函数需要使用右值引用，而 handleMessage() 函数传递 message，message 具有名称，因此是左值，导致编译错误。正确的方式是使用 std::move():
>
>       ```C++
>       void handleMessage(std::string&& message)
>       {
>       	helper(std::move(message));
>       }
>       ```
>
>       **警告：**
>
>       ​	**有名称的右值引用，如右值引用参数，本身就是左值，因为它具有名称！**
>
>       右值引用并不局限于函数的参数。可声明右值引用类型的变量，并对其赋值，尽管这一用法并不常见。考虑下面的代码，在 C++ 中这是不合法的：
>
>       ```C++
>       int& i = 2;			// Invalid:reference to a constant
>       int a = 2, b = 3;
>       int& j = a + b;		// Invalid:reference to a temporary
>       ```
>
>       使用右值引用后，下面的代码完全合法：
>
>       ```C++
>       int&& i = 2;
>       int a = 2, b = 3;
>       int&& j = a + b;
>
>       // 但是，单独使用右值引用的情况是十分少见的
>       ```
>
>   2. **实现移动语义**
>
>       移动语义是通过右值引用实现的。为了对类增加移动语义，需要实现移动构造函数和移动赋值运算符。移动构造函数和移动赋值运算符应使用 noexcept 限定符标记，这告诉编译器，它们不会抛出任何异常。这对于与标准库兼容非常重要，因为如果实现了移动语义，与标准库的完全兼容只会移动存储的对象，且确保不抛出异常。下面的 Spreadsheet 类定义包含一个移动构造函数和一个移动赋值运算符。也引入了两个辅助方法 cleanup。和 moveFrom()。前者在析构函数和移动赋值运算符中调用。后者用于把成员变量从源对象移动到目标对象，接着重置源对象。
>
>       ```C++
>       class Spreadsheet
>       {
>       public:
>       	Spreadsheet(Spreadsheet&& src) noexcept;	// Move constructor
>       	Spreadsheet& operator=(Spreadsheet&& rhs) noexcept;	// Move assign
>       
>       private:
>       	void cleanup() noexcept;
>       	void moveFrom(Spreadsheet& src) noexcept;
>       	// Remaining code omitted for brevity
>       };
>       ```
>
>       实现代码如下所示：
>
>       ```C++
>       void Spreadsheet::cleanup() noexcept
>       {
>       	for (size_t i = 0; i < mWidth; i++)
>       	{
>       		delete[] mCells[i];
>       	}
>       	delete[] mCells;
>       	mCells = nullptr;
>       
>       	mWidth = mHeight = 0;
>       }
>       
>       void Spreadsheet::moveForm(Spreadsheet& src) noexcept
>       {
>       	// Shallow copy(浅复制) of data
>       	// 通过浅复制将指针总输入的源函数 src 拷贝到 *this 对象中
>       	mWidth = src.mWidth;
>       	mHeight = src.mHeight;
>       	mCells = nullptr;
>       
>       	// Reset the source object, because ownership has been moved!
>       	src.mWidth = 0;
>       	src.mHeight = 0;
>       	src.mCells = nullptr;
>       }
>       
>       // Move constructor
>       Spreadsheet::Spreadsheet(Spreadsheet&& src) noexcpet
>       {
>       	moveForm(src);
>       }
>       
>       // Move assignment operator
>       Spreadsheet& Spreadsheet::operator=(Spreadsheet&& src) noexcept
>       {
>       	// check for self-assignment
>       	if (this == &rhs)
>       	{
>       		return *this;
>       	}
>       
>       	//  free the old memory
>       	cleanup();
>       
>       	moveFrom(rhs);
>       
>       	return *this;
>       }
>       ```
>
>       **移动构造函数和移动赋值运算符都将 mCells 的内存所有权从源对象移动到新对象，这两个方法将源对象的 mCells 指针设置为空指针，以防源对象的析构函数释放这块内存，因为新的对象现在拥有了这块内存。**
>
>       **很明显，只有你知道将销毁源对象时，移动语义才有用。**
>
>       例如，就像普通的构造函数或复制赋值运算符一样，**可显式将移动构造函数和/或移动赋值运算符设置为默认或将其删除，如第 8 章所述。**
>
>       **仅当类没有用户声明的复制构造函数、复制赋值运算符、移动赋值运算符或析构函数时，编译器才会为类自动生成默认的移动构造函数。仅当类没有用户声明的复制构造函数、移动构造函数、复制赋值运算符或析构函数时，才会为类生成默认的移动赋值运算符。**  
>
>       ```C++
>       #include <iostream>
>       #include <utility>
>       
>       class MyClass 
>       {
>       public:
>       	// 普通构造函数
>       	MyClass(int value) : data_(new int(value)) 
>           {
>       		std::cout << "普通构造函数被调用\n";
>       	}
>       
>       	// 移动构造函数
>       	MyClass(MyClass&& other) noexcept : data_(other.data_) 
>           {
>       		other.data_ = nullptr; // 移动后将源对象的指针置为nullptr
>       		std::cout << "移动构造函数被调用\n";
>       	}
>       
>       	// 其他成员函数和数据成员的定义...
>       
>       private:
>       	int* data_;
>       
>       	// 其他私有成员函数和数据成员的定义...
>       };
>       
>       int main() 
>       {
>       	// 调用普通构造函数
>       	MyClass obj1(42);
>       
>       	// 调用移动构造函数
>       	MyClass obj2 = std::move(obj1);
>       
>       	return 0;
>       }
>       // 这里就知道什么时候时普通构造什么时候是复制构造函数了
>       ```
>
>       **注意：**
>
>       **如果类中动态分配了内存，则通常应当实现析构函数、复制构造函数、移动构造函数、复制赋值运算符和移动赋值运算符，这称为 “5 规则”(Rule of Five)。**
>
>       **移动对象数据成员：**
>
>       ​	**moveFrom() 方法对三个数据成员直接赋值，因为这些成员都是基本类型。如果对象还将其他对象作为数据成员，则应当使用 std::move()移动这些对象。**假设 Spreadsheet 类有一个名为 mName 的 std::string 数据成员。接着采用以下方式实现 moveFrom()方法：  
>
>       ```C++
>       void Spreadsheet::moveFrom(Spreadsheet& src) noexcept
>       {
>       	// Move object data members
>       	mName = std::move(src.mName);
>       	// 这里是说，如果有其他的类作为此类的成员，那么就调用它的移动构造函数进行转移
>       
>       	// Move primitive
>       	// Shallow copy of data
>       	mWidth = src.mWidth;
>       	mHeight = src.mHeight;
>       	mCells = src.mCells;
>       
>       	// Reset the source object, because onwership has been move!
>       	src.mWidth = 0;
>       	src.mHeight = 0;
>       	src.mCells = nullptr;
>       }
>       ```
>
>       用交换方式实现移动构造函数和移动赋值运算符：
>
>       ​	前面的移动构造函数和移动赋值运算符的实现都使用了 moveFrom() 辅助方法，该辅助方法通过执行浅表复制来移动所有数据成员。**在此实现中，如果给 Spreadsheet 类添加新的数据成员，则必须修改 swap() 函数和 moveFrom() 方法。如果忘了更新其中的一个，则会引入 bug。为避免此类 bug, 可使用默认构造函数和 swap() 函数，编写移动构造函数和移动赋值运算符**。
>
>       **首先给 Spreadsheet 类添加默认构造函数。不应当让类的用户使用这个默认构造函数，故将其标记为 private**：  
>
>       ```C++
>       class Spreadsheet
>       {
>       private:
>       	Spreadsheet() = dafault;
>       	// Remaining code omitted for brevity
>       };
>       ```
>
>       接下来，可删除 cleanup() 和 moveFrom() 辅助方法，将 cleanup() 方法中的代码移入析构函数。此后，可按如下方式实现移动构造函数和移动赋值运算符:
>
>       ```C++
>       Spreadsheet::Spreadsheet(Spreadsheet&& src) noexcept
>       	: Spreadsheet()
>       {
>       	swap(*this, src);
>       }
>       
>       Spreadsheet& Spreadsheet::operator=(Spreadsheet&& rhs) noexcept
>       {
>       	Spreadsheet temp(std::move(rhs));
>       	swap(*this, temp);
>       	return *this;
>       }
>       ```
>
>       移动构造函数首先委托给默认构造函数。此后，对默认构造的 *this 与给定的源对象进行交换。移动赋值运算符首先使用 std::move(rhs), 创建一个本地 Spreadsheet 实例，然后将这个本地 Spreadsheet 实例与 *this 交换。与前面使用 moveFrom() 的实现相比，使用默认构造函数和 swap() 函数实现移动构造函数和移动赋值运算符的效率稍微差一些。但这种做法也有优点，它需要的代码较少，将数据成员添加到类时，需要的代码较少，也不太可能引入 bug, 因为只需要更新 swap() 实现，加入新的数据成员即可。
>
>   3. **测试 Spreadsheet 移动运算**
>
>       可使用以下代码来测试 Spreadsheet 移动构造函数和移动复制赋值运算符：
>
>       ```C++
>       Spreadsheet createObject()
>       {
>       	return Spreadsheet(3, 2);
>       }
>
>       int main()
>       {
>       	vector<Spreadsheet> vec;
>       	for (int i = 0; i < 2; i++)
>       	{
>       		std::cout << "Iteration " << i << std::endl;
>       		vec.push_back(Spreadsheet(100, 100));
>       		std::cout << std::endl;
>       	}
>
>       	Spreadsheet s(2, 3);
>       	s = createObject();
>
>       	Spreadsheet s2(5, 6);
>       	s2 = s;
>
>       	return 0;
>       }
>
>       // 输出：
>       Iteration 0
>       Normal constructor
>       Move constructor
>
>       Iteration 1
>       Normal constructor
>       Move constructor
>       Move constructor
>
>       Normal constructor
>       Normal constructor
>       Move assignment operator
>       Normal constructor
>       Copy assignment operator
>       Normal constructor
>       Copy constructor
>       ```
>
>       第一章 引入了 vector。vector 的大小会动态增长以容纳新对象，为此，可分配较大的内存块，然后将对象复制到(或移动到)较大、新的 vector。如果编译器发下来移动构造函数，那么就移动而不深拷贝。
>
>       上述的内容具体解释见课本，太复杂了，我这里不赘述。真是烦死了这个构造。
>
>       我这里就强调一点：怎么看到底是移动还是普通——就是看它的右侧的源对象是否要被销毁，或者说是不是一个“字面量”。
>
>   4. **使用移动语义实现交换函数**
>
>       考虑到交换两对象的 swap() 函数，这是另一个使用移动语义提供性能的示例。下面的 swapCopy() 实现没有使用移动语义：
>
>       ```C++ 
>       void swapCopy(T& a, T& b)
>       {
>       	T temp(a);
>       	a = b;
>       	b = temp;
>       }
>       ```
>
>       这一实现是极其影响性能的，使用 std::move() 语义进行复写，可以极大提高性能：
>
>       ```C++  
>       void swapCopy(T& a, T& b)
>       {
>       	T temp(std::move(a));
>       	a = std::move(b);
>       	b = std; :move(temp);
>       }
>       ```
>
>       这正是标准库的 std::swap() 的实现方法。

****

#### 2.5零规则

>   上述的五大特殊成员函数：
>
>   1. 析构函数
>   2. 复制构造函数
>   3. 移动构造函数
>   4. 复制赋值运算符
>   5. 移动赋值运算符
>
>   都不要用！！！！！！！！！！！！！！！！！！！！
>
>   用标准库！！！！！！！！！！！！！！！！！！！！
>
>   所以，之前就是在扯淡？比如，使用 vector<vector<SpreadsheetCell>> 替代 Spreadsheet**，该 vector 会自动处理内存，而且很高效。

****

### 9.3与方法有关的更多内容

>C++ 为方法提供许多选择，本章将详细讲述。

****

#### 3.1静态方法

>**静态方法和普通方法的对比**：
>
>- **静态方法：**
> - 被声明为`static`的方法是属于类而不是类的实例的。它们可以通过类名调用，而不需要创建类的实例。
> - 静态方法不能直接访问非静态成员或成员函数，因为它们不与类的实例相关联，但可以访问类的 private 和 protected 静态数据成员。如果同一类型的其他对象对静态方法可见(例如传入了对象的指针或引用)，那么静态方法也可访问其他对象的 private 和 protected 非静态数据成员。
> - 静态方法内部不能使用`this`指针，因为它们没有实例上下文。
> - 静态方法可以被类的所有实例共享，也可以被类本身调用。
>- **普通方法：**
> - 普通方法是类的实例的一部分，需要通过类的实例(对象)来调用。
> - 可以访问和修改实例的非静态成员，可以使用`this`指针来引用当前实例。
> - 普通方法与类的实例相关联，可以访问和修改实例的状态。
>
>**必要性和使用场景**：
>
>1. **静态方法的必要性：**
>
>  - **共享资源或功能：** 静态方法通常用于实现与类本身相关的功能，而不是与实例相关的功能。例如，计算类的总数或提供与类相关的全局设置。
>  - **工具函数：** 静态方法可以用作类的工具函数，提供一些通用的操作，而不需要创建类的实例。
>  - **避免创建实例：** 如果某个方法与类的状态无关，而只与类的行为有关，可以将其声明为静态方法，以避免不必要的实例创建。
>
>2. **普通方法的必要性：**
>
>  - **操作实例状态：** 如果方法需要访问或修改实例的状态，那么它应该是普通方法。普通方法可以使用`this`指针来引用当前实例。
>  - **对象特定的行为：** 如果方法的行为与实例的状态密切相关，且需要在多个地方使用，那么它可能是一个普通方法。
>  - **面向对象编程：** 普通方法是面向对象编程中的重要概念，它们强调了对象的封装性和行为。通过普通方法，类的实例可以表现出个体性和特定的行为。
>
>  示例：
>
>  ```c++
>class SpreadsheetCell
>{
> 	// Omitted for brevity
>private:
> 	static std::string doubleToString(double inValue);
> 	static doubel stringToDouble(std::string_view inString);
>}
>  ```
>
>  将这两个函数定义为 public，就可以在代码外使用它们，这时其实这种方法就有些类似于 命名空间 了。
>
>  ```C++
>string str = SpreadsheetCell::doubleToString(5.0);
>  ```

****

#### 3.2const 方法与 mutable

**const** **方法 ： **

>即，约定这些方法不改变任何数据成员，仅此而已。
>
>只要记住，不想改变传入的数据，就既使用 const type& 又使用 const 定义方法，这样就好。

**mutable 方法 ：**

>有些编码从逻辑上是一种 const 方法，但是实际上它内部要进行一种“统计”或者说一种另外的对于用户来说毫无影响的某种操作。这时，我们会发现无论我们改变什么都不会被编译器允许，因为方法被定义为了 const ，但是总不能因为这种改动而去除 const 关键字，这样是不优雅的，而是采用将这种改动的成员变量定义为 mutable，这样对这样的成员进行的修改，将在编译器对 const 方法处理时忽略掉。
>
>如下示例,对某种方法使用次数进行统计：
>
>```C++
>class SpreadsheetCell
>{
>	// Omitted for brevity
>private:
>	double mValue = 0;
>	mutable size_t mNumAccess = 0;
>};
>
>double SpreadsheetCell::getValue() const
>{
>	mNumAccess++;
>	return mNumAccess;
>}
>
>double SpreadsheetCell::getString() const
>{
>	mNumberAccess++;
>	return doubleToString(mValue);
>}
>```

****

#### 3.3方法重载

> 保持函数名不变，改动函数输入和输出类型，而使得编译器在面对不同的传入传出，做出不同的行为，这叫 重载解析(overload resolution)。但是，如果传入传出值不能完全确定出使用哪个重载函数，那么编译器就无从判断。
>
> 1.**基于 const 的重载**
>
> 通常情况下，const 版本 和 非 const 版本 的实现是一样的，为避免代码重复，可使用 Scott Meyer 的 cosnt_cast() 模式。例如，，Spreadsheet 类中有 getCellAt() 方法，该方法返回 SpreadsheetCell 的非 const 引用。可添加 const 重载版本，它返回 SpreadsheetCell 的 const 引用：
>
> ```C++
> class Spreadsheet
> {
> public:
>  	SpreadsheetCell& getCellAt(size_t x, size_t y);
>  	const SpreadsheetCell& getCellAt(size_t x, size_t y);
> };
> ```
>
> const getCellAt() 正常写，下面说明如何实现 Scott Meyer 的 const_cast 模式：
>
> ```C++
> cosnt SpreadsheetCell& Spreadsheet::getCellAt(size_t x, size_t y)
> {
>  	verifyCoordinate(x, y);
>  	return mCells[x][y];
> }
> 
> SpreadsheetCell& Spreadsheet::getCellAt(size_t x, size_t y)
> {
>  	return const_cast<SpreadsheetCell&>(std::as_const(*this).getCellAt(x, y));
>  	// 以下代码也可以，上述代码需要 C++17 才能实现 as_const
>  	return const_cast<SpreadsheetCell&>(static_cast<const Spreadsheet&>(*this).getCellAt(x, y));
> }
> // 这种 const_cast 语法类似于静态类型转换，也就是 static_cast 
> ```
>
> 这里貌似使用 const_cast() 模式的优势并不明显，但是想象一下随着 cosnt 方法实现的内容逐步增多，这样做能够节省很多代码空间。
>
> ```C++
> Spreadsheet sheet1(5, 6);
> SpreadsheetCell& cell = sheet1.getCellAt(1, 1);
> 
> const Spreadsheet sheet2(5, 6);
> const SpreadhsheetCell& cell2 = sheet2.getCellAt(1, 1);
> ```
>
> 2. **显式删除重载**
>
>    重载方法可以被显式地删除，可以用这种方法对具有某种特定参数的成员函数进行禁止调用。例如：
>
>    ```C++
>    class MyClass
>    {
>    public:
>    	void foo(int i);
>    };
>    ```
>
>    可以用以下代码对 foo() 代码进行调用：
>
>    ```C++
>    MyClass c;
>    c.foo(123);
>    c.foo(1.23);	// 这里进行了隐式的类型转换
>    ```
>
>    下面定义方法则可以禁止这种隐式类型转换：
>
>    ```C++
>    class MyClass
>    {
>    public:
>    	void foo(int i);
>    	void foo(int i) = delete;
>    };
>    ```
>
>    这样上述隐式转换将被报错。

****

#### 3.4内联方法

>C++ 提供这样一种能力：**函数或方法的调用不应再生成的代码中实现，就像调用独立的代码块那样，编译器应将方法体或函数体直接插入到调用方法或函数的位置。这个过程叫做内联(inline)**，具有这一行为的函数或方法被称为内联函数或内联方法。
>
>注意：
>
>**内联比使用 #define 宏安全！**
>
>可在方法或函数定义名称前使用 inline 关键字，将某个方法或函数定义为内联的。例如，要让 SpreadsheetCell 类的访问方法成为内联的，可以这样定义：
>
>```C++
>inline double SpreadsheetCell::getValue() const
>{
>	mNumAccess++;
>	return mValue;
>}
>
>inline std::string SpreadsheetCell::getString() const
>{
>	mNumAccess++;
>	return doubleToString(mValue);
>}
>```
>
>这是提示编译器，用实际的方法体替换对 getValue() 和 getString() 的调用，而不是生成代码进行函数调用。注意， inline 关键字只是提示 编译器，如果编译器认为这样做会降低性能，那么就会忽略掉该关键字。
>
>注意，在所有调用了内联函数或内联方法的源文件中，内敛方法或内联函数的定义必须有效。考虑到这个问题如果没有看到函数定义，那么编译器就无法完成函数体替换。因此——如果编写了内联函数或内联方法，就应该将定义与原型一起放在头文件中。
>
>注意：
>
>**高级 C++ 编译器不要求将内联方法放在头文件中。**例如，Microsoft Visual C++ 支持连接时代码生成(LTCG)，会自动将较小的函数内联，即使这些函数没有声明为内联函数或者没有在头文件中定义，同样也如此。**可以利用这一点，不需要将定义放在头文件中，这样可以保证接口整洁，因为在接口文件中看不到任何实现细节。示例如下：**
>
>```C++
>// MathUtils.h
>#pragma once
>
>class MathUtils
>{
>public:
>	// 内联函数的声明
>	int square(int x);
>};
>
>// MathUtils.cpp
>// 内联函数的定义(放在头文件中)
>inline int MathUtils::square(int x)
>{
>	return x * x;
>}
>```
>
>**另一种定义内联的方法**：
>
>```C++
>class Spreadsheetcell
>{
>public:
>	// Omitted for brevity
>	double getValue() const
>	{
>		mNumAccesses++;
>		return mValue;
>	}
>	std::string getString() const
>	{
>		mNumAccesses++;
>		return doubleToString(mValue);
>	}
>	// Omitted for brevity
>};
>```
>
>注意：
>
>​	如果使用调试器单步调试内联函数的调用，某些高级 C++ 调试器会跳到内联函数实际的源代码处，这就好似依旧是在进行函数调用的假象【内联不是调用，内联函数的使用可能会增加最终的编译文件大小。内联函数的主要优势在于提高程序的执行效率，因为它避免了函数调用的开销，直接将函数体的代码插入到调用点。】但实际上是内联的。
>
>但是，请记住，inline 关键字是一种对编译器的请求，而不是绝对的要求，所以，如果这种使用能够使得效率增高且不会过分代码膨胀，才会进行内联处理。

****

#### 3.5默认参数

>   在 C++ 中，默认参数(defaut arguments) 与方法重载类似，在原型中，可以为函数或方法的参数指定默认值。
>
>   注意，任何默认构造函数能做到的，使用方法重载都可以做到，然而这种默认构造方法确实是应当使用得心应手的机制。

****

### 9.4不同的数据成员类型【部分内容不太明白】

>   C++为数据成员提供了多种选择。除了在类中简单地声明**数据成员**外，还可创建**静态数据成员(类的所有对象共享)**、**静态常量数据成员**、**引用数据成员**、**常量引用数据成员和其他成员**。本节解释这些不同类型的数据成员。  

****

#### 4.1静态数据成员

>   使用机制基本和静态成员函数一样。
>
>   有时让类的所有对象都包含某个变量的副本是没必要的。数据成员可能只对类有意义，而每个对象都拥有其副本是不合适的，**使用 static 关键字**。  
>
>   下面是 Spreadsheet 类的定义，其中包含了新的静态数据成员 sCounter：
>
>   ```C++
>   class Spreadsheet
>   {
>   	// Omitted for brevity 
>   private:
>   	static size_t sCounter;
>   };
>   ```
>
>   不仅要在**类定义中列出 static 类成员，还需要在源文件中为其分配内存，通常是定义类方法的那个源文件**。**在此还可初始化静态成员，但注意与普通的变量和数据成员不同，默认情况下它们会初始化为 0**。static 指针会初始化为 nullptr 下面是为 sCounter 分配空间并初始化为 0 的代码：  
>
>   ```C++
>   size_t Spreadsheet::sCounter;
>   ```
>
>   静态数据成员默认情况下初始化为 0, 但如果需要，可将它们显式地初始化为 0, 所下所示:
>
>   ```C++
>   size_t Spreadsheet::sCounter = 0;
>   ```
>
>   这行代码在函数或方法外部，与声明全局变量非常类似，只是使用作用域解析 Spreadsheet::指出这是Spreadsheet 类的一部分。【这也就是和上面说的一样，和静态方法类似的原因】
>
>   1. **内联方法**
>
>      从 C++17 开始，就可以使用 inline 来声明静态数据成员，这样做的好处就是不用在源文件中为其分配空间，示例如下：
>
>      ```C++
>      class Spreadsheet
>      {
>      	// Omitted for brevity
>      private:
>      	static inline size_t sCounter = 0;
>      };
>      // 注意，有了 inline 关键字，那么就不要在源文件中再次定义
>      ```
>
>   2. **在类方法内访问静态数据成员**
>
>      在类方法内部，可以像使用普通数据成员一样使用静态数据成员。例如，为 Spreadsheet 类创建一个 mId 成员，并在 Spreadsheet 构造函数中用 sCounter 成员初始化它。下面是包含了 mId 成员的 Spreadsheet 类定义：
>
>      ```C++
>      class Spreadsheet
>      {
>      public:
>      	// Omitted for brevity
>      	size_t getId() const;
>      
>      private:
>      	static size_t sCounter;
>      	size_t mId;
>      };
>      ```
>
>      下面是 Spreadsheet 构造函数的实现，在此赋予初始 ID：
>
>      ```C++
>      Spreadsheet::Spreadsheet(size_t width, size_t height)
>      	: mId(sCounter++), mWidth(width), mHeight(height)
>      {
>      	mCells = new SpreadsheetCell * [mWidth];
>      	for (size_t i = 0; i < mWidth; i++)
>      	{
>      		mCells[i] = new SpreadsheetCell[mHeight];
>      	}
>      }
>      ```
>
>      可以看出，构造函数可以访问 sCounter ,这就像是一个普通成员，在复制构造函数中，也要指定新的 ID，由于Spreadsheet 复制构造函数委托给非复制构造函数(会自动创建新的 ID), 因此这可以自动进行处理。  
>
>      在赋值运算符中不应该复制 ID。一旦给某个对象指定 ID, 就不应该再改变。建议把 mId 设置为 const 数据成员。
>
>   3. **在方法外访问静态数据成员**
>
>      **访问控制限定符适用于静态数据成员：sCounter 是私有的，因此不能在类方法之外访问。如果 sCounter 是公有的，就可在类方法外访问**，具体方法是用::作用域解析运算符指出这个变量是 Spreadsheet 类的一部分：
>
>      ```C++
>      int c = Spreadsheet::sCounter;
>      ```
>
>      然而，建议不要使用公有数据成员(9.42 节讨论的静态常量数据成员属于例外)。**应该提供公有的 get/set 方法来授予访问权限。如果要访问静态数据成员，应该实现静态的 get/set 方法。**

****

#### 4.2静态常量数据成员

>   **类中的数据成员可声明为 const, 意味着在创建并初始化后，数据成员的值不能再改变。如果某个常量只适用于类，应该使用静态常量(static const 或 const static)数据成员，而不是全局常量。**可在类定义中定义和初始化整型和枚举类型的静态常量数据成员，而不需要将其指定为内联变量。例如，你可能想指定电子表格的最大高度和宽度。如果用户想要创建的电子表格的高度或宽度大于最大值，就改用最大值。可将最大高度和宽度设置为 Spreadsheet **类的 static const 成员**：  
>
>   ```C++
>   class Spreadsheet
>   {
>   public:
>    	// Omitted for brevity
>    	static const size__t kMaxHeight = 100;
>    	static const size_t kMaxWidth = 100;
>    	// kMaxHeight 和 kMaxWidth 是公有的，因此可在程序的任何位置访问它们，就像它们是全局变量一样，只是语法略有不同。必须用作用域解析运算符::指出该变量是 Spreadsheet 类的一部分
>    	// 同时使用 static 和 const 并且在类定义时初始化值，可以简化在源文件中的相关操作(内联)
>   };
>   ```
>
>   可在构造函数中使用这些新常量，如下面的代码片段所示：  
>
>   ```C++
>   #include <algorithm>
>   
>   Spreadsheet::Spreadsheet(size_t width, size_t height)
>   	: mId(sCounter++)
>   	, mWidth(std::min(width, kMaxWidth)) // std::min() requires <algorithm>
>   	, mHeight(std::min(height, kMaxHeight)) // 用于返回两者中较小值
>    	// 并抛出异常，但不会调用相应类的析构函数
>   {
>   	mCells = new Spreadsheetcell * [mWidth];
>   	for (size_t i = 0; i < mWidth; i++)
>    	{
>   		mCells[i] = new Spreadsheetcell[mHeight];
>   	}
>   }
>   ```
>
>   注意：当 高度或宽度超出最大值时，除了自动使用最大高度或宽度外，也可以抛出异常。然而，在构造函数中抛出异常时，不会调用析构函数，因此需要谨慎处理。第 14 章将对此进行详细解释。
>
>   注意：非静态数据成员也可声明为 const。例如，mId 数据成员就可声明为 const。因为不能给 const 数据成员赋值，所以需要在类内初始化器或 ctor-initializer 中初始化它们。这意味着根据使用情形，可能无法为具有非静态常量数据成员的类提供赋值运算符。如果属于这种情况，通常将赋值运算符标记为 deleted。

****

#### 4.3引用数据成员

>   Spreadsheets 和 SpreadsheetCells 很好，但这两个类本身并不能组成非常有用的应用程序。为了用代码控制整个电子表格程序，可将这两个类一起放入 SpreadsheetApplication 类。
>
>   这个类的实现在此并不重要。现在考虑这个架构存在的问题：电子表格如何与应用程序通信？应用程序存储了一组电子表格, 因此可与电子表格通信。与此类似,每个电子表格都应存储应用程序对象的引用。**Spreadsheet类必须知道 SpreadsheetApplication 类，SpreadsheetApplication 类也必须知道 Spreadsheet 类**【这种知道某种程度上类似于双链表的逻辑】。这是一个**循环引用问题**，无法用普通的#include 解决。解决方案是在其中一个头文件中使用前置声明。下面是新的使用了前置声明的 Spreadsheet 类定义，用来通知编译器关于 SpreadsheetApplication 类的信息。第 11 章解释前置声明的另一个优势：可缩短编译和链接时间。
>
>   ```C++
>   class SpreadsheetApplication; // forward declaration
>   class Spreadsheet
>   {
>   public:
>   	Spreadsheet(size_t width, size__t height, SpreadsheetApplication& theApp);
>   	// Code omitted for brevity.
>   private:
>    	// Code omitted for brevity.
>    	SpreadsheetApplication& mTheApp;
>   };
>   ```
>
>   这个定义将一个 SpreadsheetApplication 引用作为数据成员添加进来。在此情况下建议使用引用而不是指针，因为 Spreadsheet 总要引用一个 SpreadsheetApplication, 而指针则无法保证这一点。
>
>   注意存储对应用程序的引用，仅是为了演示把引用作为数据成员的用法。不建议以这种方式把 Spreadsheet和 SpreadsheetApplication 类组合在一起，而应改用 MVC(模型-视图-控制器)范型(见第 4 章)。
>
>   **在构造函数中，每个 Spreadsheet 都得到了一个应用程序引用。**如果不引用某些事物，引用将无法存在，因此在构造函数的 ctor-initializer 中必须给 mTheApp 指定一个值。
>
>   ```C++
>   Spreadsheet::Spreadsheet(size_t width, size_t height, SpreadsheetApplication& theApp)
>   	: mid(sCounter++)
>   	, mWidth(std::min(width, kMaxWidth))
>   	, mHeight(std::min(height, kMaxHeight))
>   	, mTheApp(theApp)
>   {
>   	// Code omitted for brevity.
>   }
>   ```
>
>   在复制构造函数中，必须初始化这个引用成员【指针不能保证这个对象的存在】。由于 Spreadsheet 复制构造函数委托给非复制构造函数(初始化引用成员)，因此这将自动处理。
>
>   **记住，在初始化一个引用后，不能改变它引用的对象，因此不可能在赋值运算符中对引用赋值。这意味着根据使用情形，可能无法为具有引用数据成员的类提供赋值运算符。如果属于这种情况，通常将赋值运算符标记为 deleted。**

****

#### 4.4常量引用数据成员

>   就像普通引用可引用常量对象一样，引用成员也可引用常量对象。例如，为让 Spreadsheet 只包含应用程序对象的常量引用，只需要在类定义中将 mTheApp 声明为常量引用：  
>
>   ```C++
>   class Spreadsheet
>   {
>   public:
>   	Spreadsheet(size_t width, size_t height,
>   		const SpreadsheetApplication& theApp);
>   	// Code omitted for brevity.
>   private:
>   	// Code omitted for brevity,
>   	const SpreadsheetApplication& mTheApp;
>   };
>   ```
>
>   常量引用和非常量引用之间存在一个重要差别。常量引用 SpreadsheetApplication 数据成员只能用于调用 SpreadsheetApplication 对象上的常量方法。如果试图通过常量引用调用非常量方法，编译器会报错。
>
>   还可创建静态引用成员或静态常量引用成员，但一般不需要这么做。

****

### 9.5嵌套类

>   类定义不仅可包含成员函数和数据成员，还可编写嵌套类和嵌套结构、声明 typedef 或者创建枚举类型。类中声明的一切内容都具有类作用域。如果声明的内容是公有的，那么可在类外使用 ClassName::作用域解析语法访问。
>
>   可在类的定义中提供另一个类定义。例如，假定 SpreadsheetCell 类实际上是 Spreadsheet 类的一部分，因此不妨将 SpreadsheetCell 重命名为 Cell。可将二者定义为:
>
>   ```C++
>   class Spreadsheet
>   {
>   public:
>   	class Cell
>   	{
>   	public:
>   		Cell() = default;
>   		Cell(double initialvalue);
>   		// Omitted for brevity
>   	};
>   	Spreadsheet(size_t width, size_t height, const SpreadsheetApplication& theApp);
>   	// Remainder of Spreadsheet declarations omitted for brevity
>   };
>   ```
>
>   现在 Cell 类定义位于 Spreadsheet 类内部，因此在 Spreadsheet 类外引用 Cell 必须用 Spreadsheet::作用域限定名称，即使在方法定义时也是如此。例如，Cell 的 double 构造函数应如下所示：  
>
>   ```C++
>   Spreadsheet::Cell::Cell(double initialvalue)
>   	: mValue(initialvalue)
>   {
>   
>   }
>   ```
>
>   甚至在 Spreadsheet 类中方法的返回类型(不是参数)也必须使用这一语法:
>
>   ```C++
>   Spreadsheet::Cell& Spreadsheet::getCellAt(size_t x, size_t y)
>   {
>   	verifyCoordinate(x, y);
>   	return mCells[x][y];
>   }
>   ```
>
>   如果在 Spreadsheet 类中直接完整定义嵌套的 Cell 类，将使 Spreadsheet 类的定义略显臃肿。为缓解这一点,只需要在 Spreadsheet 中为 Cell 添加前置声明，然后独立地定义 Cell 类，如下所示：
>
>   ```C++
>   class Spreadsheet
>   (
>   public:
>   	class Cell;
>   	Spreadsheet(size_t width, size_t height, const SpreadsheetApplications theApp);
>   	// Remainder of Spreadsheet declarations omitted for brevity
>   };
>   
>   class Spreadsheet::Cell
>   {
>   public:
>   	Cell() = default;
>   	Cell(double initialvalue);
>   	// Omitted for brevity
>   };
>   
>   // 这样拆分定义有利于增强可读性
>   ```
>
>   普通的访问控制也适用于嵌套类定义。如果声明了一个 private 或 protected 嵌套类，这个类只能在外围类(outer class, 即包含它的类)中使用。
>
>   **嵌套的类有权访问外围类中的所有 private 或 protected 成员；**
>
>   **而外围类却只能访问嵌套类中的 public 成员。**  

****

### 9.6类内的枚举类型

>   如果想在类内定义很多常量，应该使用枚举类型而不是一组 #define.例如，可在 SpreadsheetCell 类中支持单元格颜色，如下所示：
>
>   ```C++
>   class SpreadsheetCell
>   {
>   public:
>    	// Omitted for brevity
>    	enum class Color { Red = 1, Green, Blue, Yellow };
>    	void setColor(Color color);
>    	Color gerColor() const;
>   
>   private:
>    	// Omitted for brevity
>    	Color mColor = Color::Red;
>   };
>   ```
>
>   setColor() 和 getColor() 方法的实现简单明了：
>
>   ```C++
>   void SpreadsheetCell::setColor(Color color)
>   {
>    	mColor = color;
>   }
>   
>   SpreadsheetCell::Color SpreadsheetCell::getColor() const
>   {
>    	return mColor;
>   }
>   ```
>
>   可通过下面的方法使用这些新方法：
>
>   ```C++
>   SpreadsheetCell myCell(5);
>   myCell.setColor(SpreadsheetCelll::Color::Blue);
>   auto color = myColor.getColor();
>   ```

****

### 9.7运算符重载

>   需要在对象上执行操作，例如，相加、比较、将对象输入文件或从文件中读取。对电子表格而言，只有能执行算术运算(例如将整行单元格相加)才算真正有用。

****

#### 7.1示例：为 SpreadsheetCell 实现加法

>   1. **使用 add() 方法**
>
>       ```C++
>       class SpreadsheeetCell
>       {
>       public:
>       	// Omitted for brevity
>       	SpreadsheetCell add(const Spreadsheet& cell) const;
>       	// Omitted for brevity
>       };
>       
>       SpreadsheetCell SpreadsheetCell::add(const SpreadsheetCell& cell) const
>       {
>       	return SpreadsheetCell(getValue() + cell.getValue());
>       }
>       ```
>
>       ```C++
>       SpreadsheetCell myCell(4), anotherCell(5);
>       SpreadsheetCell aThirdCell = myCell.add(anotherCell);
>       ```
>
>   2. **加法运算符的重载方法**
>       用加号相加两个单元格会比较方便，就像相加两个 int 和 double 值那样，如下所示：
>
>       ```C++
>       Spreadsheet myCell(4), anotherCell(5);
>       Spreadsheet aThirdCell = myCell + anotherCell;
>       ```
>
>       C++ 允许编写自己的加号版本，以正确地处理类，称为 加运算符，为此可以编写一个名为 operator+ 的方法，如下所示：
>
>       ```C++
>       class SpreadsheetCell
>       {
>       public:
>       	// Omitted for brevity
>       	SpreadsheetCell add(const Spreadsheet& cell) const;
>       	// Omitted for brevity
>       };
>       ```
>
>       注意：
>
>       ​	在 operator+ 和加号之间可以使用空格，例如，可用 operator + 代替 operator+。这一点对所有运算符都成立。
>
>       ```C++
>       // 该方法与 add() 方法的实现一致
>       SpreadsheetCell SpreadsheetCell::operator+(const SpreadsheetCell& cell) const
>       {
>       	return SpreadsheetCell(getValue() + cell.getValue());
>       }
>       ```
>
>       现在可以使用两个加号将两个单元格相加，就像之前那样。
>
>       这种语法需要花点工夫去适应。不要过于担心这个奇怪的方法名称 opemto+ 这只是一个名称，就像 fbo或 add 一样。理解此处实际发生的事情有助于理解其余的语法。当 C++编译器分析一个程序，遇到运算符(例如， +、-、=或 <<)时，就会试着查找名为 operate+、operator-、operator= 或 operator<< , 且具有适当参数的函数或方法。  
>
>       运算符重载是函数重载的一种形式，函数重载对函数的返回类型并没有要求。
>
>       **隐式转换：**
>
>       令人震惊的是，一旦编写像前面那样的 operator+，就不仅仅可以实现两个单元格的相加，还可以将单元格和 string_view、double 或 int 值相加。
>
>       ```C++
>       SpreadsheetCell myCell(4), aThirdCell;
>       string str = "hello";
>       aThirdCell = myCell + string_view(str);
>       aThirdCell = myCell + 5.6;
>       aThirdCell = myCell + 4;
>       ```
>
>       上面的代码之所以可运行，是因为编译器会试着查找合适的 operator+, 而不是只查找指定类型的那个 operator+ 为找到 operator+，编译器还试图查找合适的类型转换，构造函数会对有问题的类型进行适当的转换。在上例中，当编译器看到 SpreadsheetCell 试图与 double 值相加时,发现了用 double 值作为参数的 SpreadsheetCell构造函数，就会构建一个临时的 SpreadsheetCell 对象，传递给 operator+。与此类似，当编译器看到试图将SpreadsheetCell 与 string_view 相加的行时，会调用把 string_view 作为参数的 SpreadsheetCell 构造函数，创建一个临时 SpreadsheetCell 对象，传递给 operator+.
>
>       隐式转换会带来方便，但是同样可能带来隐患，例如，使得 operator+ 失去原本意义。可使用 explicit 关键字标记构造函数，禁止将 string_view 隐式转换为 SpreadsheetCell：
>
>       ```C++
>       class Spreadsheet
>       {
>       public:
>       	SpreadsheetCell() = default;
>       	SpreadsheetCell(double initialValue);
>       	explicit SpreadsheetCell(std::string_view initialValue);
>       	// Remainder omitted for brevity
>       };
>                                                                                   
>       /* explicit 关键字只在类定义内使用，只适用于只有一个参数的构造函数，例如单参构造函数或为参数提供默认值的多参构造函数。*/
>       ```
>
>       由于必须创建临时对象，隐式使用构造函数的效率不高。为避免与 double 值相加时隐式地使用构造函数，可编写第二个 operator+, 如下所示：  
>
>       ```C++
>       SpreadsheetCell SpreadsheetCell::operator+(double rhs) const
>       {
>       	return SpreadsheetCell(getValue() + rhs);
>       }
>       ```
>
>   3. **全局 operator+**
>
>       隐式转换允许使用 operator^方法将 SpreadsheetCell 对象与 int 和 double 值相加。然而，这个运算符不具有互换性，如下所示：  
>
>       ```C++
>       aThirdCell = myCell + 4; // Works fine
>       aThirdCell = myCell + 5.6; // Works fine.
>       aThirdCell = 4 + myCell; // FAILS TO COMPILE!
>       aThirdCell = 5.6 + myCell; // FAILS TO COMPILE!
>                                                                                   
>       /*当 Spreadsheetcell 对象在运算符的左边时，隐式转换正常运行，但在右边时无法运行。加法是可互换的，因此这里存在错误。问题在于必须在 SpreadsheetCell 对象上调用 operator+方法，对象必须在 operato什的左边。这是 C++语言定义的方式，因此使用 operator+ 方法无法让上面的代码运行。*/
>       ```
>
>       然而，如果用不局限于某个特定对象的全局 operator+ 函数替换类内的 opemto什方法，上面的代码就可以运行，函数如下所示：  
>
>       ```C++
>       SpreadsheetCell operator+(const SpreadsheetCell& Ihs,
>       	const SpreadsheetCell& rhs)
>       {
>       	return SpreadsheetCell(Ihs.getValue() + rhs.getValue());
>       }
>       ```
>
>       需要在头文件中声明运算符:
>
>       ```C++
>       class SpreadsheetCell
>       {
>       	// Omitted for brevity
>       };
>                                                                                   
>       SpreadsheetCell operator+(const SpreadsheetCell& Ihs, const SpreadsheetCell& rhs);
>       ```
>
>       这样，下面的 4 个加法运算都可按预期运行：  
>
>       ```C++
>       aThirdCell = myCell + 4; // Works fine.
>       aThirdCell = myCell + 5.6; // Works fine.
>       aThirdCell = 4 + myCell; // Works fine.
>       aThirdCell = 5.6 + myCell; // Works fine.
>       ```
>
>       那么，如果编写以下代码，会发生什么情况呢？  
>
>       ```C++
>       aThirdCell = 4.5 + 5.5;
>       ```
>
>       这段代码可编译并运行，但并没有调用前面编写的 opeator+ 。这段代码将普通的 double 型数值 4.5 和 5.5相加，得到了下面所示的中间语句： 
>
>       ```C++
>       aThirdCell = 10;
>       ```
>
>       为了让赋值操作继续,运算符右边应该是 SpreadsheetCell 对象。编译器找到并非显式由用户定义的用 double 值作为参数的构造函数，然后用这个构造函数隐式地将 double 值转换为一个临时 SpreadsheetCell 对象，最后调用赋值运算符。
>
>       注意：
>
>       在 C++中，不能更改运算符的优先级。例如，*和/始终在+和- 之前计算。对于用户定义的运算符，唯一能做的只是在确定运算的优先级后指定实现。C++也不允许发明新的运算符号，不允许更改运算符的实参个数。

****

#### 7.2重载算术运算符

>   +、-、*、/ 略
>
>   +=、-=、*=、/=
>
>   ```C++
>   class Spreadsheetcell
>   {
>   public:
>   	// Omitted for brevity
>   	SpreadsheetCell& operator+=(const Spreadsheetcell& rhs);
>   	SpreadsheetCell& operator-=(const Spreadsheetcell& rhs);
>   	SpreadsheetCell& operator*=(const Spreadsheetcell& rhs);
>   	SpreadsheetCell& operator/=(const Spreadsheetcell& rhs);
>   	// Omitted for brevity
>   };
>   
>   Spreadsheetcell& Spreadsheetcell::operator+=(const Spreadsheetcell& rhs)
>   {
>   	set(getValue() + rhs.getValue());
>   	return *this;
>   }
>   ```
>
>   如果既有某个运算符的普通版本，又有简写版本，建议你基于简写版本实现普通版本，以避免代码重复。例如:
>
>   ```C++
>   Spreadsheetcell operator+(const SpreadsheetCell& Ihs, const Spreadsheetcell& rhs)
>   {
>    	auto result(Ihs); // Local copy
>    	result += rhs; // Forward to op=() version
>    	return result;
>   }
>   ```
>

#### 7.3重载比较运算符

>   

```C++
bool operator<op>(const Spreadsheetcell& Ihs, const Spreadsheetcell& rhs);
```

**注意：**

**前面重载的运算符使用 getValue()返回一个 double 值。大多数时候，最好不要对浮点数执行相等或不相等测试。应该使用 e 测试(epsilon test), 但这一内容超出了本书的讨论范围.**

当类中的数据成员较多时，比较每个数据成员可能比较痛苦。然而，当实现了== 和 <之后，可以根据这两个运算符编写其他比较运算符。例如，下面的 operator>=定义使用了 operator<:

```C++
bool operator>=(const Spreadsheetcell& Ihs, const Spreadsheetcell& rhs)
{
	return !(Ihs < rhs);
}
```

****

#### 7.4创建具有运算符重载的类型

>    这在之后再说，几乎所有的运算符均可以重载。这在 STL(标准库中) 极为有用。

****

### 9.8创建稳定的接口

>   理解了在 C++中编写类的所有语法后，回顾第 5 章和第 6 章的设计原则会对此有所帮助。在 C++中，类是主要的抽象单元，应将抽象原则应用到类，尽可能分离接口和实现。确切地讲，应该将所有数据成员设置为private, 并提供相应的 getter 和 setter 方法。这就是 SpreadsheetCell 类的实现方式：将 mValue 设置为 private, set() ,getValue(), getString() 。用于设置或获取这些值。
>
>   **使用接口类和实现类 ：**  
>
>   即使提前进行估算并采用最佳设计原则，C++语言本质上对抽象原则也不友好。**其语法要求将 public 接口和 private(或 protected)数据成员及方法放在一个类定义中，从而将类的某些内部实现细节向客户公开**。**这种做法的缺点在于，如果不得不在类中加入新的非公有方法或数据成员，所有的客户代码都必须重新编译，对于较大项目而言这是负担**。  
>
>   **有个好消息：可创建清晰的接口，并隐藏所有实现细节，从而得到稳定的接口。**
>
>   **还有个坏消息：这样做有点繁杂。**
>
>   **基本原则是为想编写的每个类都定义两个类：接口类和实现类。**  
>
>   -   **实现类与已编写的类相同(假定没有采用这种方法)，接口类给出了与实现类一样的 public 方法，但只有一个数据成员：指向实现类对象的一个指针**。
>
>   -   **这称为 pimpl idiom(private implementation idiom, 私有实现习语)或 bridge 模式，接口类方法的实现只是调用实现类对象的等价方法**。
>   -   **这样做的结果是无论实现如何改变，都不会影响 public 接口类，从而降低了重新编译的必要性。当实现改变(只有实现改变)时，使用接口类的客户不需要重新编译**。
>
>   -   **注意只有在单个数据成员是实现类的指针时，这个习语才有效。如果它是 按值传递 的数据成员，在实现类的定义改变时，客户代码必须重新编译。**  
>
>   为将这种方法应用到 Spreadsheet 类，需要定义如下 public 接口类 Spreadsheet：
>
>   ```C++
>   #include "SpreadsheetCell.h"
>   #include <memory>
>   
>   // forward declarations
>   class SpreadsheetApplication;
>   
>   class Spreadsheet
>   {
>   public:
>   	Spreadsheet(const SpreadsheetApplication& theApp,
>   		size_t width = kMaxWidth,
>   		size_t height = kMaxHeight);
>   	Spreadsheet(const Spreadsheet& src);
>   	~Spreadsheet();
>   
>   	Spreadsheet& operator=(const Spreadsheet& rhs);
>   
>   	void setCellAt(size_t x, size_t y, const SpreadsheetCell& cell);
>   	SpreadsheetCell& getCellAt(size_t x, size_t y);
>   
>   	size_t getId() const;
>   
>   	static const size_t kMaxHeight = 100;
>   	static const size_t kMaxWidth = 100;
>   
>   	// 友元函数
>   	friend void swap(Spreadsheet& first, Spreadsheet& second) noexcept;
>   
>   private:
>   	// 实现类，是 private 的嵌套类，用于限定访问权限
>   	// 这里可能会有点疑惑，就是前面对嵌套类到底是干嘛的的疑问，明明我可以在外面进行直接定义，我干嘛在这里的内部定义？
>   	// 可以说，嵌套类的左右就是去限定一种访问方式的，在外部是无法不通过 外层类而获取内层类的内容的。
>   	// 同时，如果是作为 private 类进行存在，那么就无法通过外部类对其内部进行访问，实现了一种保护，以及底层的不可见
>   	// 所以，嵌套类作为一种声明，不是一个数据成员，而下方指向这个数据成员的的智能指针才是真正的数据成员
>   	class Impl;
>   
>   	// 实现类的智能指针
>   	std::unique_ptr<Impl> mImpl;
>   };
>   
>   /*实现类 Impl 是一个 private 嵌套类，因为只有 Spreadsheet 需要了解这个实现类。Spreadsheet 现在只包含一
>   个数据成员：指向 Impl 实例的指针。public 方法与旧式的 Spreadsheet 相同*/
>   
>   /*-------------------------------------------------------------------------------------------------------*/
>   #include "Spreadsheet.h"
>   #include "SpreadsheetImpl.h"
>   #include <utility>
>   
>   Spreadsheet::Spreadsheet(const SpreadsheetApplication& theApp, size_t width, size_t height)
>   {
>   	mImpl = std::make_unique<Impl>(theApp, width, height);
>   }
>   
>   Spreadsheet::Spreadsheet(const Spreadsheet& src)
>   {
>   	mImpl = std::make_unique<Impl>(*src.mImpl);
>   }
>   
>   Spreadsheet::~Spreadsheet() = default;
>   
>   void Spreadsheet::setCellAt(size_t x, size_t y, const SpreadsheetCell& cell)
>   {
>   	mImpl->setCellAt(x, y, cell);
>   }
>   
>   SpreadsheetCell& Spreadsheet::getCellAt(size_t x, size_t y)
>   {
>   	return mImpl->getCellAt(x, y);
>   }
>   
>   size_t Spreadsheet::getId() const
>   {
>   	return mImpl->getId();
>   }
>   
>   Spreadsheet& Spreadsheet::operator=(const Spreadsheet& rhs)
>   {
>   	*mImpl = *rhs.mImpl;
>   	return *this;
>   }
>   
>   void swap(Spreadsheet& first, Spreadsheet& second) noexcept
>   {
>   	using std::swap;
>   
>   	swap(first.mImpl, second.mImpl);
>   }
>   
>   /*-------------------------------------------------------------------------------------------------------*/
>   #pragma once
>   
>   #include <cstddef>
>   #include "Spreadsheet.h"
>   #include "SpreadsheetCell.h"
>   
>   class Spreadsheet::Impl
>   {
>   public:
>   	Impl(const SpreadsheetApplication& theApp,
>   		size_t width,
>   		size_t height);
>   	Impl(const Impl& src);
>   	~Impl();
>   	Impl& operator=(const Impl& rhs);
>   
>   	void setCellAt(size_t x, size_t y, const SpreadsheetCell& cell);
>   	SpreadsheetCell& getCellAt(size_t x, size_t y);
>   
>   	size_t getId() const;
>   
>   private:
>   	void verifyCoordinate(size_t x, size_t y) const;
>   	void swap(Impl& other) noexcept;
>   
>   	size_t mId = 0;
>   	size_t mWidth = 0;
>   	size_t mHeight = 0;
>   	SpreadsheetCell** mCells = nullptr;
>   
>   	const SpreadsheetApplication& mTheApp;
>   
>   	static size_t sCounter;
>   };
>   
>   /*-------------------------------------------------------------------------------------------------------*/
>   #include "SpreadsheetImpl.h"
>   #include "Spreadsheet.h"
>   #include <stdexcept>
>   #include <utility>
>   #include <algorithm>
>   
>   size_t Spreadsheet::Impl::sCounter;
>   
>   Spreadsheet::Impl::Impl(const SpreadsheetApplication& theApp,
>   	size_t width, size_t height)
>   	: mId(sCounter++)
>   	, mWidth(std::min(width, Spreadsheet::kMaxWidth))
>   	, mHeight(std::min(height, Spreadsheet::kMaxHeight))
>   	, mTheApp(theApp)
>   {
>   	mCells = new SpreadsheetCell * [mWidth];
>   	for (size_t i = 0; i < mWidth; i++)
>   	{
>   		mCells[i] = new SpreadsheetCell[mHeight];
>   	}
>   }
>   
>   Spreadsheet::Impl::~Impl()
>   {
>   	for (size_t i = 0; i < mWidth; i++) {
>   		delete[] mCells[i];
>   	}
>   	delete[] mCells;
>   	mCells = nullptr;
>   }
>   
>   Spreadsheet::Impl::Impl(const Impl& src)
>   	: Impl(src.mTheApp, src.mWidth, src.mHeight)
>   {
>   	// The ctor-initializer of this constructor delegates first to the
>   	// non-copy constructor to allocate the proper amount of memory.
>   
>   	// The next step is to copy the data.
>   	for (size_t i = 0; i < mWidth; i++)
>   	{
>   		for (size_t j = 0; j < mHeight; j++)
>   		{
>   			mCells[i][j] = src.mCells[i][j];
>   		}
>   	}
>   }
>   
>   void Spreadsheet::Impl::verifyCoordinate(size_t x, size_t y) const
>   {
>   	if (x >= mWidth || y >= mHeight)
>   	{
>   		throw std::out_of_range("");
>   	}
>   }
>   
>   void Spreadsheet::Impl::setCellAt(size_t x, size_t y, const SpreadsheetCell& cell)
>   {
>   	verifyCoordinate(x, y);
>   	mCells[x][y] = cell;
>   }
>   
>   SpreadsheetCell& Spreadsheet::Impl::getCellAt(size_t x, size_t y)
>   {
>   	verifyCoordinate(x, y);
>   	return mCells[x][y];
>   }
>   
>   void Spreadsheet::Impl::swap(Impl& other) noexcept
>   {
>   	using std::swap;
>   
>   	swap(mWidth, other.mWidth);
>   	swap(mHeight, other.mHeight);
>   	swap(mCells, other.mCells);
>   }
>   
>   Spreadsheet::Impl& Spreadsheet::Impl::operator=(const Impl& rhs)
>   {
>   	// check for self-assignment
>   	if (this == &rhs) {
>   		return *this;
>   	}
>   
>   	// Copy-and-swap idiom
>   	Impl temp(rhs); // Do all the work in a temporary instance
>   	swap(temp); // Commit the work with only non-throwing operations
>   	return *this;
>   }
>   
>   size_t Spreadsheet::Impl::getId() const
>   {
>   	return mId;
>   }
>   ```
>
>   **嵌套的 Spreadsheet::Impl 类的接口与原来的 Spreadsheet 类的接口完全相同。**但由于 Impl 是 Spreadsheet 的private 嵌套类，因此不能有以下全局友元函数 swap(), 该函数交换两个 Spreadsheet::Impl 对象：
>
>   ```C++
>   friend void swap(Spreadsheet::Impl& first, Spreadsheet::Impl& second) noexcept;
>   ```
>
>   相反，为 Spreadsheet::Impl 类定义 private swapo方法，如下所示:
>
>   ```C++
>   void swap(Impl& other) noexcept;
>   ```
>
>   实现方式十分简单，但需要记住，这是一个嵌套类，因此需要指定 Spreadsheet::Impl::swap(), 而非仅仅指定 Impl::swap()。其他成员同样如此。要了解细节，可查看前面介绍嵌套类的部分，下面是 swapo方法:
>
>   ```C++
>   void Spreadsheet::Impl::swap(Impl& other) noexcept
>   {
>   	using std::swap;
>   	swap(mWidth, other.mWidth);
>   	swap(mHeight, other.mHeight);
>   	swap(mCells, other.mCells);
>   }
>   ```
>
>   注意，Spreadsheet 类有一个指向实现类的 unique_ptr, Spreadsheet 类需要一个用户声明的析构函数。我们不需要对这个析构函数进行任何处理，可在文件中设置= defalut 如下所示：
>
>   ```C++
>   Spreadsheet::-Spreadsheet() = default;
>   ```
>
>   这说明不仅可在类定义中，也可在实现文件中给特殊成员函数设置=defhult。
>
>   Spreadsheet 方法(例如setCell()和 getCellAt())的实现只是将请求传递给底层的 Impl 对象:
>
>   ```C++
>   void Spreadsheet::setCellAt(size_t x, size_t y, const SpreadsheetCell& cell)
>   {
>   	mImpl->setCellAt(x, y, cell);
>   }
>   SpreadsheetCell& Spreadsheet::getCellAt(size_t x, size_t y)
>   (
>   	return mImpl->getCellAt(x, y);
>   }
>   ```
>
>   Spreadsheet 的构造函数必须创建一个新的 Impl 实例来完成这个任务  :
>
>   ```C++
>   Spreadsheet::Spreadsheet(const SpreadsheetApplication& theApp,
>   	size_t width, size_t height)
>   {
>   	// 利用智能指针分配空间
>   	mImpl = std::make_unique<Impl>(theApp, width, height);
>   }
>   
>   Spreadsheet::Spreadsheet(const Spreadsheet& src)
>   {
>   	mImpl = std::make_unique<Impl>(*src.mImpl);
>   }
>   ```
>
>   解释一下上面的代码：
>
>   1.  `const Spreadsheets src` 是函数参数,表示传入一个 `const` 引用类型的 `Spreadsheet` 对象作为数据源。
>   2.  `mImpl` 是当前对象的一个数据成员,类型为 `std::unique_ptr<Impl>`。`std::unique_ptr` 是 C++11 引入的智能指针,用于自动管理动态分配的内存。
>   3.  `std::make_unique<Impl>(*src.mImpl)` 利用 `std:;make_unique` 在堆上创建一个新的 `Impl` 实例,并使用 `src.mImpl` 所指向的对象的值来初始化这个新实例。
>   4.  将新创建的 `Impl` 实例的所有权转移给 `mImpl`。
>
>   剩下的代码就不讲了，没什么意思。
>
>   **总结一下：在 Spreadsheet 中使用嵌套类，将 Impl private 类只能由 Spreadsheet 类获取，然后，再为 Spreadsheet 声明构造函数和析构函数，新的 Spreadsheet 的构造函数的目的是调用 Impl 的构造函数，然后，我们思考该如何对 Impl 进行构造和析构，其实本质上和 Spreadsheet 类之前的一模一样，我们可以将 Impl 类看作是代理，将 Spreadsheet 类的需求通过这样一根智能指针进行传递，从而在 客户和类之间形成一个过渡层。过渡层的传递方式就是，先用 Spreadsheet 中存一个 Impl 的指针用于初始化和访问权限获取，在之后利用的 Impl 本质上就是 Spreadsheet 的实体，而 Spreadsheet 被作为了一个接口类**
>
>   **真正将接口和实现分离的技术功能强大。尽管开始时有点笨拙，但是一旦适应这种技术，就会觉得这么做很自然。然而，在多数工作环境中这并不是常规做法，因此这么做会遇到来自同事的一些阻力。支持这种方法最有力的论据不是将接口分离的美感，而是类的实现改变后大幅缩短构建时间。一个类不使用 pimpl idiom 时，对实现类的更改将触发一个长时间的构建过程。例如，给类定义增加数据成员时，将触发其他所有源文件(包括类定义)的重新构建；而使用 pimpl idiom, 可以修改实现类的定义，只要 public 接口类保持不变，就不会触发长时间的构建过程。**
>
>   **为将实现与接口分离，另一种方法是使用抽象接口以及实现该接口的实现类；抽象接口是只有纯虚方法(pure virtual method)的接口。第 10 章将讨论抽象接口。**

****

### 9.9本章小结

>   没啥说的，就是一句话，上面的**零规则**在那里放着，这些只要能看懂，大致会用就可以了。
>
>   其中，还有一些不是特别理解的，主要是常量引用相关的，但是之后会补上去。以及对 一些为安全而进行的函数书写方式，理解不深，比如 swap() 等。之后注意再复查一遍，仔细想象已经就可以理解了。

****

## 第10章 —— 揭秘继承技术

>   本章主要学习继承，包括：通过继承拓展类、使用继承重用代码、基类和派生类如何交互、使用继承实现多态性、使用多重继承、如何处理继承中的罕见问题。
>
>   如果没有继承，类只是一些具有相关行为和属性被合并在一起的数据结构。而继承是对过程语言的一大改进——通过继承可以是心啊在已有类的基础上创建新类。这样，类就成为了可以宠用和可拓展的组件。
>
>   本章将详细讲述各种继承功能的方法，学习继承的语法，并最大限度地利用继承的一些复杂技术。(本章与多态性相关的部分大量借鉴第 8 章和第 9 章中讲述的电子表格示例，还涉及第 5 章讲述的面向对象的方法论，注意前面的知识。)

****

### 10.1使用继承构建类

>   第 5 章中提到了，“是一个”关系是实际对象在继承层次中的存在模式。
>
>   在编程实践中，如果要基于某个类编写另一个类，或者对某个类进行少量修改，都会涉及这个模式。
>
>   完成上述目标有两个途径：
>
>   1.  一种是将代码从这个类中复制出来，然后粘贴到另一个类，并修改相关代码，就可以创建一个与原始类稍有不同的新类，这种方法会令 OOP 程序员很不爽(高内聚、低耦合。)。而且会出现以下问题：
>       -   修订原始类的 bug 不会同步到新类中，因为两个类包含完全独立的代码；
>       -   编译器不知道这两个类之间的关系，因此不具备多态性——这两个类不是同一事物的不同变种；
>       -   这种方法没有建立真正的“是一个”关系。新类与原始类非常相似只是因为共享了代码，而不是他们“是”同一类对象。
>       -   原始代码可能无法获取，其存在形式可能是预编译的二进制格式，因此不可能复制和粘贴这些代码。
>   2.  另一种方法就是使用继承，如下所讲。

****

#### 1.1扩展类

>   当使用 C++ 编写类定义时，可以告诉编译器，该类继承(或拓展)了一个已有的类。通过这种方式，该类将自动包含原始类的数据成员和方法；原始类称为父类(parent class)、基类或者超类(super class)。拓展已有类可以使该类(现在称为派生类或者子类)只描述与父类所不同的那部分内容。
>
>   在 C++ 中，为拓展一个类，可在定义类时指定要拓展的类。未说明继承的语法，此处使用了名为 Base 和 Derived 的类。首先考虑 Base 类的定义：
>
>   ```C++
>   class Base
>   {
>   public:
>   	void someMethod();
>   protected:
>   	int mProtectedInt;
>   private:
>   	int mPrivateInt;
>   };
>   ```
>
>   如果要构建一个从 Base 类继承的新类 Derived，应该使用下面的语法告诉编译器：Derived 类派生自 Base 类：
>
>   ```C++
>   class Derived : public Base
>   {
>   public:
>   	void someOtherMethod();
>   };
>   ```
>
>   ****
>
>   此处补充关于不同方式继承的知识：
>
>   1.  **`class Derived : public Base`** (公有继承)
>
>       -   基类的`public`成员在派生类中仍然是`public`。
>
>       -   基类的`protected`成员在派生类中仍然是`protected`。
>
>       -   基类的`private`成员不可直接访问(只能通过基类的`public`或`protected`接口访问)。
>
>       使用公有继承时，派生类对象可以像基类对象一样使用基类的`public`成员。
>
>       ```C++
>       class Base 
>       {
>       public:
>       	void foo() { }
>       };
>       
>       class Derived : public Base 
>       {
>           
>       };
>       
>       Derived d;
>       d.foo(); // 可以访问 Base 的 public 成员函数
>       ```
>
>   2.  **`class Derived : Base`** (私有继承，等同于`class Derived : private Base`)
>
>       -   基类的`public`成员在派生类中变为`private`。
>       -   基类的`protected`成员在派生类中变为`private`。
>       -   基类的`private`成员仍然不可直接访问。
>
>       使用私有继承时，派生类对象不能直接访问基类的`public`成员，只有派生类内部可以访问这些成员。
>
>       ```C++
>       class Base
>       {
>       public:
>       	void foo() { }
>       };
>       
>       class Derived : Base
>       {
>       
>       };
>       
>       Derived d;
>       // d.foo(); // 错误：无法访问 Base 的 public 成员函数，因为它变为 private 了
>       ```
>
>   3.  **`class Derived : protected Base`** (保护继承)
>
>       -   基类的`public`成员在派生类中变为`protected`。
>       -   基类的`protected`成员保持`protected`。
>       -   基类的`private`成员仍然不可直接访问。
>
>       保护继承允许派生类及其子类访问基类的`public`和`protected`成员，但外部无法直接访问这些成员。
>
>       ```C++
>       class Base 
>       {
>       public:
>       	void foo() { }
>       };
>                                       
>       class Derived : protected Base 
>       {
>       };
>                                       
>       Derived d;
>       // d.foo(); // 错误：无法从外部访问 foo，因为它变成了 protected
>       ```
>

##### 继承方式的影响：

>   -   **公有继承**：这是最常用的继承方式，它保持基类的接口，使得派生类能够像基类一样使用并暴露这些接口。
>-   **私有继承**：基类的`public`和`protected`成员变为`private`，只有派生类内部可以访问。派生类的外部不能直接访问基类成员，即使它们在基类中是`public`。
>   -   **保护继承**：基类的`public`成员在派生类中变为`protected`，允许派生类及其子类访问这些成员，但外部类不能访问。
>

**注意：**

>   Derived 本身就是一个完整的类，这个类只是刚好共享了 Base 类的特性而已。
>
>   上面先提一下 `public` 关键字，之后将详细阐述。
>
>   ![image-20240907093253020](https://s2.loli.net/2024/09/07/gWdn5rYuhqVlyTM.png)
>   
>   上图表明，通过不同的继承关系可以形成类的不同链条，通常被称为——继承链。
>    
>    ****
>    

##### 1.客户对继承的看法

>   对于客户或者代码其他部分而言，Derived 类型的对象仍然是 Base 对象，因为 Derived 类从 Base 类继承。这意味着 Base 类的所有 public 方法和数据成员，以及 Derived 类的所有 public 方法和数据都时可供使用的。
>
>   在调用某方法时，使用派生类的代码不需要直到是继承链中的哪个类定义了这个方法。例如，下面的代码调用了 Derived 对象的两个方法，而其中一个方法是 Base 类中定义的：
>
>   ```C++ 
>   Derived myDerived;
>   myDerived.someMethod();
>    myDerived.someOtherMethod();
>    ```
>    
>    要注意，继承的运行方向是单向的，这点很重要。(A 派生出 B 的继承成立时，我们可以说 B 是 A，而不能说 A 是 B)
>    
>    上面这一点也就是说，Derived 类与 Base 类具有明确的关系，但是 Base 类并不知道任何与 Derived 类特殊性的任何细节信息。这意味着，Base 类型的对象不支持 Derived 类的 public 方法和数据成员，因为 Base 类不是 Derived 类。如，下面的代码将无法编译，因为 Base 类不包含名为 someOtherMethod 的 public 方法：
>   
>   ```C++
>Base myBase;
>   myBase.someOtherMethod();	// Error! Base doesn't have a someOtherMethod().
>```
>   

**注意：**

>   从其他代码的观点来看，一个对象既属于定义它的类，又属于所有基类。
>
>   指向某个对象的指针或引用可以指向生命类的对象，也可指向其任意派生类的对象。
>
>   这基于了程序相当程度的灵活性，此时需要理解的概念是：指向 Base 对象的指针可以指向 Derived 对象，对于引用也是如此。客户仍然只能访问 Base 类的方法和数据成员，但是通过这种机制任何操作 Base 对象的代码都可以用来操作 Derived 对象。
>   
>   例如，下面代码可以正常编译并运行，尽管看上去类型并不匹配：
>    
>    ```C++
>    Base* base = new Derived();	// Create Derived, store it in Base pointer.
>    ```
>    
>    然而，不能通过 Base 指针调用 Derived 类的方法。下面代码无法运行：
>   
>   ```C++
>base->someOtherMethod();
>   ```
>
>   编译器会报错，因为尽管对象是 Derived 类型，并定义了 someOtherMethod() 方法，但编译器只是将它看作成 Base 类型，而 Base 类型没有定义 someOtherMethod() 方法。

##### 2.从派生类的角度分析继承

>   ##### 
>
>   对于派生类自身而言，其编写方式或行为没有发生改变，仍然可以在派生类中定义方法和数据成员，就像这是一个普通类。前面 Derived 类的定义中声明了一个名为 someOtherMethod() 的方法，因此 Derived 类增加了一个额外的方法，从而拓展了 Base 类。
>
>   派生类可以访问基类中声明的 public、protected 方法和数据成员，就好像这些方法和数据成员是派生类自己的，因为从技术上讲，它们属于派生类。例如，Derived 类中的 someOtherMethod() 方法的实现可以使用在 Base 类中声明的数据成员 mProtectedInt。下面的代码显示了这一实现，访问基类的数据成员和方法与访问派生类中的数据成员和方法并无不同之处。
>   
>   ```C++
>    void Derived::someOtherMethod()
>    {
>    	cout << "I can access base class data member mProtectedInt." << endl;
>    	cout << "Its value is : " << mProtectedInt << endl;
>    }
>    ```
>   
>   第 8 章讲述访问说明符(public、private 和 protected)时，private 和 protected 的区分可能令人感到迷惑，但是现在理解了派生类，这一区别就变得更加清晰了。如果类将数据成员和方法声明为 protected，派生类就可以访问它们；如果声明为 private，派生类就不能访问。
>
>   下面的 someOtherMethod() 实现将无法完成编译，因为派生类尝试访问了基类的 private 数据成员：
>
>   ```C++
>   void Derived::someOtherMethod()
>   {
>    	cout << "I can access base class data member mProtectedInt." << endl;
>    	cout << "Its value is : " << mProtectedInt << endl;
>    	cout << "The value of mPrivateInt is : " << mPrivateInt << endl;	// Error!
>   }
>```
>   
>private 访问说明符可控制派生类与基类的交互方式。
>   
>建议将所有数据成员都默认声明为 private，如果希望任何代码都可以访问这些数据成员，可以通过提供 public 的获取器或者设置器；如果仅希望派生类访问它们，就可以提供受保护的获取器或设置器。
>   
>把数据成员默认设置为 private 的原因是：这样提供最高级别的封装，这意味着可以改变数据的表示方式，而 public 或 protected 接口不变；不直接访问数据成员，这一意味着可以在 public 和 protected 设置器中方便地添加对输入数据的检查。
>   
>方法也应默认设置为 private，只有需要公开的方法才设置 public，只有派生类需要访问的方法才设置为 protected。
>   

**注意：**

>   从派生类的观点看，基类所有的 public，protected 数据成员和方法都是可用的。

##### 3.禁用继承

>   C++ 允许讲类标记为 final，这意味着继承这个类会导致编译错误。
>
>   将类标记为 final 的方法是直接在类名的后面使用 final 关键字。
>
>   例如，下面的 Base 类被标记为 final：
>   
>   ```C++
>    class Base final
>    {
>    	// Omitted for brevity
>    };
>    ```
>    
>   下面的 Derived 类试图从 Base 类继承，但是这会导致编译错误，因为 Base 类被标记为 final。
>   
>```C++
>   class Derived : public Base
>{
>    	// Omitted for brevity
>   };
>   ```

****

#### 1.2重写方法

>   从某一个类继承的主要原因是为了：**添加或者替代功能**。
>
>   Derived 类定义在父类的基础上添加了新功能，提供了额外的 someOtherMethod() 方法，另一方法 someMethod() 方法是从 Base 类继承而来的，这个方法的行为在派生类中与在基类中相同。在许多情况下，可能需要替换或者重写某个方法来修改类的行为。

##### 1.将所有方法都设为 virtual，以防万一

>   在 C++ 中，**重写(override)**方法有一点别扭，因为必须在基类中使用关键字 virtual 声明方法为虚函数才可以在派生类中进行重写。
>
>   virtual 关键字出现在方法声明的开头，下面显示了 Base 类的修改版本：
>
>   ```C++
>class Base
>   {
>   public:
>   	virtual void someMethod();
>    protected:
>    	int mProtectedInt;
>    private:
>    	int mPrivateInt;
>    };
>    ```
>   
>   **virtual 关键字有些微妙之处，所以常常为人诟病，被当作语言设计不当部分。**
>
>   **经验表明，最好将所有的方法都设置为 virtual。**这样就不必担心重写方法是否可以运行，这样做的唯一缺点就是对性能有微弱影响，virtual 关键字会贯穿本章，稍后详见“5.virtual 的真相”部分。
>
>   即使 Derived 类不大可能扩展，可是最好也将这个类的方法设置为 virtual，以防万一，即：
>
>   ```C++
>class Derived : public Base
>   {
>   public:
>   	virtual void someOtherMethod();
>    };
>    ```
>   

**注意：**

>   经验表明，为避免因为遗漏 virtual 关键字引发的问题，可以将所有的方法都设置为 virtual(包括析构函数，但不包括构造函数)。注意，由于编译器生成的析构函数不是默认 virtual 的！！！
>

##### 2.重写方法的语法

>   为了重写某个方法，需要在派生类的定义中重新声明这个方法，就像在基类中声明的那样，并在派生类的实现文件中提供新的定义。例如，Base 类包含了一个 someMethod() 方法，在 Base.cpp 中提供 someMethod() 方法定义如下：
>
>   ```C++
>   void Base::someMethod()
>   {
>    	cout << "This is Base' version of someMethod()." << endl;
>   }
>   ```
>
>   注意在方法定义中不需要重复使用 virtual 关键字。
>
>   如果希望在 Derived 类中提供 someMothod() 的新定义，首先应在 Derived 类定义中添加这个方法，如下所示：
>
>   ```C++
>   class Derived : public Base
>   {
>    public:
>    	virtual void someMethod() override;	// Overrides Base someMethod()
>    	virtual void smoeOtherMethod();
>   };
>   ```
>
>   建议在重写方法的声明末尾添加 override 关键字，override 关键字详见本章后面的内容。
>
>   someMethod() 方法的新定义与 Derived 类的其他方法一并在 Derived.cpp 中给出：
>
>   ```C++
>   void Derived::someMethod()
>   {
>    	cout << "This is Derived's version of someMethod()." << endl;
>   }
>   ```
>
>   一但将方法或者析构函数标记为 virtual，它们在所有的派生类中就一直是 virtual，即使派生类中删除了 virtual 关键字，也是如此。例如，在下面的 Derived 类中，someMethod() 仍然是 virtual，可以被 Derived 的派生类重写，因为在 Base 类中将其标记为了 virtual。
>
>   ```C++
>   class Derived : public Base
>   {
>    public:
>    	void someMethod() override;	// Override Base's someMethod()
>   };
>   ```
>

##### 3.客户对重写方法的看法

>   经过前面的改动后，其他代码仍可用先前的方法调用 someMethod()，可用 Base 或 Derived 类的对象调用这个方法。然而，现在 someMethod() 的行为将根据对象所属类的不同而变化。
>
>   例如，下面的代码与先前一样可以运行，调用 Base 版本的 someMethod()：
>
>   ```C++
>   Base myBase;
>   myBase.someMothod();	// Calls Base's version of someMethod().
>   ```
>
>   这段代码的输出为：
>
>   ```C++
>   This is Base's version of someMethod().
>   ```
>
>   如果声明一个 Derived 类对象，将自动调用派生类版本的 someMethod()：
>
>   ```C++
>   Derived myDerived;
>   myDerived.someMethod();	// Calls Derived's version of someMethod().
>   ```
>
>   这段代码的输出为：
>
>   ```C++
>   This is Derived's version of someMethod().
>   ```
>
>   Derived 类对象的其他方法维持不变。从 Base 类继承的岐然方法仍然保持 Base 类提供的定义，除非在 Derived 类中显式地重写这些方法。
>
>   如前所述，指针或引用可以指向某个类或其派生类的对象，对象本身“知道”自己所属的类，因此只要将这个方法声明为 virtual，就会自动调用对应的方法。例如，如果一个对 Base 对象的引用实际上引用的是 Derived 对象，调用 someMethod() 实际上会调用派生类版本，如下所示。如果在基类中省略了 virtual 关键字，重写功能将无法正确运行。
>
>   ```C++
>   Derived myDerived;
>   Base& ref = myDerived;
>   ref.someMethod();	// Calls Derived's version of someMethod.
>   ```
>
>   记住，即使基类的引用或指针知道这实际上是一个派生类，也无法访问在没有在基类中定义的派生类方法或成员。就是说，下面的代码无法完成编译，因为 Base 引用没有 someOtherMethod() 方法：
>
>   ```C++
>   Derived myDerived;
>   Base& ref = myDerived;
>   myDerived.someOtherMethod();	// This is fine.
>   ref.someOtherMethod();			// Error!
>   ```
>
>   非指针或非引用对象无法正确处理派生类的特征信息。可将 Derived 对象转化为 Base 对象，或将 Derived 对象赋值给 Base 对象，因为 Derived 对象也是 Base 对象。然而，此时这个对象将会遗失派生类的所有信息：
>
>   ```C++
>   Derived myDerived;
>   Base assignedObject = myDerived;	// Assigns a Derived to a Base.
>   assignedObject.someMethod();		// Calls Base's version of someMethod().
>   ```
>
>   这一部分知识看上去有些奇奇怪怪，好像是在进行很诡异的行为，但是可以通过考虑对象在内存中的状态：将 Base 对象当作占据了一块内存的区间，Derived 对象是个稍大一些、稍有不同的区间，但正因为它具有 Base 对象的一切，并且还需要添加、修改一部分东西。对于指向 Derived 对象的引用或指针，这个区间没有变——只是可以用新的方法访问它；然而对于指向 Base 的指针或引用，为了使得这两个区间能够匹配，于是为了适应较小的区间而丢失掉 Derived 类的全部的“独有特征”。
>

**注意：**

>   基类的指针或引用指向派生类对象时，派生类保留其重写方法；
>
>   但是通过类型转换将派生类对象转换为基类对象时，就会丢失其独有特征。
>
>   重写方法和派生类数据的丢失称为截断(slicing)。
>

##### 4.override 关键字

>   有时，可能会偶然创建一个新的虚方法，而不是重写基类的方法。考虑下面的 Base 和 Derived 类，其中 Derived 类正确重写了 someMethod()，但没有使用 override 关键字：
>
>   ```C++
>   class Base
>   {
>    public:
>    	virtual void someMethod(double d);
>   };
>   
>   class Derived : public Base
>   {
>    public:
>    	virtual void someMethod(double d);
>   };
>   ```
>
>   可以通过引用调用 someMethod()，如下所示：
>
>   ```C++ 
>   Derived myDerived;
>   Base& ref = myDerived;
>   ref.someMethod(1.1);	// Calls Derived's version of someMethod().
>   ```
>
>   上述代码能正确地调用 Derived 类重写的 someMethod()。
>
>   现在假定重写 someMethod() 时，使用整数(而不是双精度浮点数)作为参数，如下所示：
>
>   ```C++
>   class Derived : public Base
>   {
>    public:
>    	virtual void someMethod(int i);
>   };
>   ```
>
>   这些代码没有重写 Base 类的 someMethod()，而是创建了一个新的虚方法。
>
>   如果试图想下面代码那样通过引用调用 someMethod()，将调用 Base 类的 someMethod() 而不是 Derived 类中定义的那个方法。(原因就是)
>
>   ```C++
>   Derived myDerived;
>   Base& ref = myDerived;
>   ref.someMethod(1.1);	// Calls Base's version of someMethod().
>   ```
>
>   如果修改了 Base 类但忘记更新所有派生类，就会发生这类问题。例如，或许 Base 类的第一个版本有一个以整数作为参数的 someMethod() 方法。然后在 Derived 派生类中重写了 someMethod 方法，仍以整数作为参数。后来发现 Base 类中的 someMethod() 方法需要一个双精度而不是整数，因此更新了 Base 类中的 someMethod()，此时可能会忘记更新派生类中的 someMethod()，让它们接受双精度而不是整数。这时，由于忘记了这一点，实际上就是创建了一个新的虚方法，而不是重写这个方法：意思就是每个函数重载方法，虽然同名，但是由于参数列表或者返回值不同，而造成基类与派生类之间不完全匹配，就会造成看似是重写，但是实质上是新写了一个虚函数。
>
>   当然，有一个比较好的用来避免上述错误的方法就是：**使用 override 关键字来避免**，如下所示：
>
>   ```C++
>   class Derived : public Base
>   {
>    public:
>    	virtual void someMethod(int i) override;	// Error!
>   };
>   ```
>
>   Derived 类的定义间导致编译错误，因为 override 关键字表明，重写 Base 类的 someMethod() 方法，但 Base 类中的 someMethod() 方法只接收双精度数，而不接收整数。
>
>   同样地，重命名基类的某个方法，但忘记重命名派生类中的方法时，就会因为使用了 override 关键字，而出现“不小心创建了新方法，而不是正确重写方法”的问题。
>

**注意：**

>   **想要重写基类方法，始终在方法上使用 override 关键字！！！**
>

##### 5.virtual 的真相

>   如果方法不是 virtual，也可以试着重写这个方法，但是这样会导致非常微妙的错误！
>
>   ###### 隐藏而不是重写
>
>   下面的代码显示了一个基类和一个派生类，每个类都有一个方法。派生类试图重写基类的方法，但是在基类中没有将这个方法声明为 virtual。
>
>   ```C++
>   class Base
>   {
>    public:
>    	viod go()
>    	{
>    		cout << "go() called on Base." << endl;
>    	}
>   };
>   
>   class Derived : public Base
>   {
>    public:
>    	void go()
>    	{
>    		cout << "go() called on Derived." << endl;
>    	}
>   };
>   ```
>
>   试着用 Derived 对象调用 go() 方法好像没有任何问题。
>
>   ```C++
>   Derived myDerived;
>   myDerived.go();
>   ```
>
>   正如所预料中的那样，这个调用的结果是：
>
>   ```C++
>   go() called on Derived.
>   ```
>
>   然而，由于这个方法不是 virtual，因此实际上没有被重写。恰恰相反，Derived 类创建了一个新的方法，也就是名称为 go()，但是这个方法与 Base 类的 go() 方法完全没有一点关系。为了证明这一点，只需要用 Base 的指针或引用来调用它就可以：
>
>   ```C++
>   Derived myDerived;
>   Base& ref = myDerived;
>   ref.go();
>   ```
>
>   虽然，我们或许理所当然希望输出是：
>
>   ```C++
>   go() called on Derived.
>   ```
>
>   然而，实际上，输出是：
>
>   ```C++
>   go() called on Base.
>   ```
>
>   这是因为 ref 变量是一个 Base 的引用，并考虑到省略了 virtual 关键字。当调用 go() 方法时，只是执行了 Base 类的 go() 方法。由于不是虚方法，不需要考虑派生类是否重写了这个方法，因为两者除了函数名相同，其余并不存在任何代码上的关联。
>

**注意：**

>   如果声明 virtual 关键字，按我的理解就是：告诉编译器，如果出现了这个基类的派生类时，留意是不是有与它方法名相同(且参数列表和返回值都相同)(并用 override 关键字进行结尾，强调重写)的方法，如果有，那么就可以实现重写；如果没有，就直接派生类继承；
>
>   如果不声明 virtual 关键字，按我的理解就是：现在的这个方法，跟继承一点关系都没有，它就是最普通的，不可能被复写。最多被后面派生类的同名函数“遮挡”。
>
>   试图重写非虚方法，将“隐藏/遮挡”基类定义的方法，并且重写的这个方法只能在派生类环境中使用，而不能被带到基类实现“多态”。
>
>   ###### 如何实现 virtual
>
>   为了更好理解“隐藏”和“重写”基类方法的区别，需要了解 virtual 关键字的真正作用。
>
>   **C++ 在编译类时，会创建一个包含类中所有方法的二进制对象。**
>
>   **在非虚情况下，将控制交给正确方法的代码是硬代码，这称为静态绑定(static binding)，也称为(early binding)。**
>
>   **如果方法声明为 virtual，会使用名为 虚表(vtable) 的特定内存区域调用正确的实现。**
>
>   **每一个具有一个或多个虚方法的类都有一张虚表，这种类的每个对象都包含指向虚表的指针，这个虚表包含指向虚方法实现的指针。****
>
>   **通过这种方法，当使用某个对象调用方法时，指针也进入虚表，然后根据实际的对象类型执行版本正确的方法。这称为 动态绑定(dynamic binding)或晚绑定(late binding)。**
>
>   为了更好理解虚表是如何实现方法的重写的，考虑下面的 Base 和 Derived 类：
>
>   ```C++
>   class Base
>   {
>    public:
>    	virtual void func1() {}
>    	virtual void func2() {}
>    	void nonVirtualFunc() {}
>   };
>   
>   class Derived : public Base
>   {
>    public:
>    	virtual void func2() override {}
>    	void nonVirtualFunc() {}
>   };
>   ```
>
>   对于这个示例，考虑下面两个示例：
>
>   ```C++
>   Base myBase;
>   Derived myDerived;
>   ```
>
>   下图展示了这两个示例虚表的高级视图：
>
>   ![image-20240910170345938](https://s2.loli.net/2024/09/10/ldMNkApL9GasKP4.png)
>
>   myBase 对象包含了指向虚表的一个指针，虚表有两项：一项是 func1()，另一项是 func2()。这两项指向 Base::func1() 和 Base::func2() 方法的实现；
>
>   myDerived 对象也包含了指向虚表的一个指针，这个虚表也有两项：一项是 func1()，另一项是 func2()。在没有复写 finc1() 的前提下，myDerived 虚表中的 func1() 也指向 Base::func1()。而 func2() 被复写了，因此 myDerived 虚表中的 func2() 指向了新的位置，也就是 Derived::func2()。
>

**注意：**

>   **两个虚表中都不包括用于 nonVirtualFunc() 方法的项，因为该方法没有被设置为 virtual。**
>

###### 使用 virtual 的理由

>   前面建议将所有方法都声明为 virtual，既然这样，为什么要使用 virtual 关键字呢？编译器不能将所有方法都声明为 virtual 吗？答案是可以的。也正因此，许多人认为 C++ 语言应该将所有的方法都声明为 virtual，另提一嘴，Java 语言就是这样做的。
>
>   有关无所不在地使用 virtual 的争论，以及首先创建该关键字的原因，都与虚表的开销有关。要调用虚方法，程序就需要执行一系列附加操作，即**对指向要执行的适当代码的指针解除应用**。在多数情况下，这样做都会轻微影响性能，但 C++ 的设计者认为，最好让程序员自己决定是否有必要影响这部分性能。如果方法永远不会重写，就没有必要将其声明为 virtual，从而影响性能。
>
>   然而，这种影响对于当今的 CPU 而言，对性能的影响可以用 十亿分之一秒来度量，将来的 CPU 会使时间进一步缩短。在大多数应用程序中，无法察觉出使用虚函数与不使用虚函数间所带来的性能差异，因此，应当遵循建议：将所有方法声明为 virtual，包括析构函数，但不包括构造函数。
>
>   此外，在特定情况下，性能开销确实不小，需要避免。例如，假设 Point 类有一个虚方法。如果另一个数据结构存储着数百万甚至数十亿个 Point 对象，在每个 Point 对象上调用虚方法，将会带来极大的性能开销。此时最好避免在 Point 类中使用虚方法。
>
>   virtual 对于每个对象的内存使用也有轻微影响，除了方法的实现外，每个对象还需要一个指向虚表的指针，这个指针会占用一点空间。绝大多数情况下，这都不是大问题。但是，和上面一样，在 Point 类以及储存了数百万个 Point 对象的容器，此时，附带的内存开销将不容忽视：
>
>   **开销包括：**
>
>   -   **间接调用开销**：调用虚函数需要通过 `vptr` 查找虚表，然后通过虚表中的指针找到实际函数。这意味着每次调用涉及两次内存访问（一次是读取 `vptr`，一次是读取虚表的条目），与普通函数的直接调用相比，存在轻微的性能开销。
>   -   **内联失效**：虚函数不能被编译器内联，因为其具体实现直到运行时才能确定。这意味着虚函数通常比普通函数有更多的调用开销。
>
>   **如何优化：**
>
>   -   如果性能是关键问题，尽量避免在频繁调用的核心循环中使用虚函数。
>   -   使用**静态多态性**（如模板编程）替代虚函数，尤其是在编译时能确定类型的情况下。

###### 虚析构函数的需求

>   即使认为不应将所有方法都声明为 virtual 的程序员，也坚持认为应该至少将析构函数声明为 virtual。原因是：如果析构函数未被声明为 virtual，很容易在销毁对象时不释放内存。唯一允许不把析构函数声明为 virtual 的例外情况就是：**类被标记为 final**。
>
>   例如，派生类使用的内存在构造函数中动态分配，在析构函数中释放。如果不调用析构函数，这块内存将无法释放。类似地，如果派生类具有一些成员，这些成员在类的示例销毁时自动删除，如 std:unique_ptrs，那么如果从未调用析构函数，将不会删除成员。
>
>   如下面的代码所示，如果析构函数不是 virtual，很容易欺骗编译器忽略析构函数的调用：
>
>   ```C++
>   class Base
>   {
>    public:
>    	Base() {}
>    	~Base() {}	// 为声明为 virtual
>   };
>   
>   class Derived : public Base
>   {
>    public:
>    	Derived()
>    	{
>    		mString = new char[30];
>    		cout << "mString allocated." << endl;
>    	}
>   
>    	~Derived()
>    	{
>    		delete[] mString;
>    		cout << "mString deallocated." << endl;
>    	};
>   
>    private:
>    	char* mString;
>   };
>   
>   int main()
>   {
>    	Base* ptr = new Derived();	// mString is allocated here.
>    	delete ptr;					// ~Base() is called, but not ~Derived() because the destructor
>   
>    	return 0;
>   }
>   ```
>
>   输出结果如下，并可以看出程序从未调用 Derived 对象的析构函数：
>
>   ```C++
>   mString allocated.
>   ```
>
>   实际上，在上面的代码中，delete 调用的行为未在标准中定义：它既可以调用基类的析构函数，也可以调用派生类的析构函数。在这种不明确的情形下，C++ 编译器会随意做事，但大多数编译器只会调用基类的析构函数，而非派生类的。
>
>   在 C++ 中，如果你通过一个基类的指针删除一个派生类对象，而基类的析构函数**不是 virtual 的**，则只有基类的析构函数会被调用，派生类的析构函数不会被调用。这会导致派生类中分配的资源(例如动态分配的内存)不会被释放，造成内存泄漏或其它资源泄露的问题。
>
>   如果将基类的析构函数声明为 `virtual`，C++ 会确保通过基类指针删除派生类对象时，**先调用派生类的析构函数**，然后再调用基类的析构函数，正确地完成对象销毁过程。这是一种典型的多态行为，确保了析构函数可以遵循继承关系，执行派生类的清理操作。

**注意：**

>   如果在析构函数中什么都不做，只想把它设置为 virtual，可显式地设置为 "= default"，例如：
>
>   ```C++
>   class Base
>   {
>    public:
>    	virtual ~Base() = default;
>   };
>   ```
>
>   如第八章所述，注意从 C++11 开始，如果类具有用户声明的析构函数，就不赞成再让编译器自动生成复制构造函数和复制赋值运算符。在此类情况下，如果仍然需要编译器生成的复制构造函数或复制赋值运算符，可将它们显式设置为默认。为保持简洁，上述示例没有这么做。
>

**警告：**

>   除非有特殊原因，或者类被标记为 final，否则强烈建议将所有方法(包括析构函数，构造函数除外)声明为 virtual，构造函数不需要，也无法被声明为 virtual，因为在创建对象时，总会明确的指定类。
>

##### 6.禁用重写

>   C++ 允许将方法标记为 final，这意味着无法再派生类中重写这个方法。试图重写 final 修饰的方法将会导致编译错误，考虑如下代码：
>
>   ```C++
>   class Base
>   {
>    public:
>    	virtual ~Base() = default;
>    	virtual void someMethod() final;
>   };
>   ```
>
>   在下面 Derived 类中重写 someMethod() 会导致编译错误，因为 someMethod() 在 Base 类中标记为 final。
>
>   ```C++
>   class Derived : public Base
>   {
>    public:
>    	virtual void someMethod() override;	// Error!
>   };
>   ```

****

### 10.2使用继承重写方法

>   熟悉了继承的基本语法后，下面解释为什么继承是 C++ 语言中的重要特性。
>
>   **继承是利用已有代码的工具，本节给出了使用继承重用代码的实际程序。**

****

#### 2.1WeatherPrediction 类

>   假定要编写一个简单的天气预报程序，同时给出华氏温度和摄氏温度。天气预报可能超出了程序员的研究领域，因此程序员可以使用一个第三方的类库，这个类库依据当前温度和火星与木星之间的距离**(这荒谬吗？不，是有一定道理的……)**来预测天气。为保护预测算法的知识产权，将第三方的包作为已编译的库分发，但是可以看到类的定义。WeatherPrediction 类的定义如下：
>
>   ```C++
>   // Predicts the weather using proven new-age techniques given the current
>   // temperature and the distance from Jupiter to Mars. If these values are
>   // not provided, a guess is still given but it's only 99% accurate.
>   class WeatherPrediction
>   {
>    public:
>    	// Virtual destrutor
>    	virtual ~WeatherPrediction();
>       
>    	// Sets the current temperature in Fahrenheit
>    	virtual void setCurrentTempFahrenheit(int temp);
>       
>    	// Sets the current distance between Jupiter and Mars
>    	virtual void setPositionOfJupiter(int distanceFromMars);
>       
>    	// Gets the prediction for tomorrow's temperature
>    	virtual int getTomorrowTempFahrenheit() const;
>       
>    	// Gets the probability of rain tomorrow. 1 means
>    	// definite rain. 0 means no chance of rain.
>    	virtual double getChanceOfRain() const;
>       
>    	// Displays the result to the user in this format.
>    	// Result : x.xx chance. Temp.xx
>    	virtual void showResult() const;
>       
>    	// Returns a string representation of the temperature
>    	virtual std::string getTemperature() const;
>       
>    private:
>    	int mCurrentTempFahrenheit;
>    	int mDistanceFromMars;
>   };
>   ```
>
>   注意这个类将所有方法都标记为了 virtual，因为这个类假定这些方法可能再派生类中重写。
>
>   这个类解决了大部分问题。然而，与绝大多数情况一样，它与该程序的需求并不完全吻合——首先，所有的温度都以华氏温度给出，程序还需要处理摄氏温度。其次，showResult() 方法的结果显示方式可能并不是程序最想要的。

****

#### 2.2在派生类中添加功能

>   在第 5 章讲述继承时，首先描述的技巧就是添加功能。基本上该程序需要一个类似于 WeatherPrediction 的类，还需要添加一些附属功能。使用继承重用代码便是一个好主意。
>
>   首先，定义一个新类 MyWeatherPrediction，这个类还需要从 WeatherPrediction 类继承得来：
>
>   ```c++
>   #include "WeatherPrediction.h"
>   
>   class MyWeatherPrediction : public WeatherPrediction
>   {
>   
>   };
>   ```
>
>   前面的类定义可以成功编译。MyWeatherPrediction 类已经可以替代 WeatherPrediction 类。这个类可提供相同的功能，但没有新的功能。开始修改时，要在类中添加摄氏温度的信息，这里有点小问题，因为不知道这个类的内部都在做什么。如果所有的内部计算机都是用华氏温度，如何添加对摄氏温度的支持呢？方法之一时采用派生类作为用户(可以使用两种温度)和基类(只理解华氏温度)之间的中间接口。
>
>   支持摄氏温度的第一步是添加新方法，允许客户用摄氏温度(而不是华氏温度)设置当前的温度，从而获取明天以摄氏温度(而不是华氏温度)表示天气预报。还需要包含再摄氏温度和华氏温度之间转换的私有辅助方法。这些方法可以是静态方法，因为它对类的所有示例都相同：
>
>   ```c++
>   #inlcude "WeatherPrediction.h"
>   class MyWeatherPrediction : public WeatherPrediction
>   {
>    public:
>    	virtual void setCurrentTempCelsius(int temp);
>    	virtual int getTomorrowTempCelsius() const;
>   
>    private:
>    	static int convertCelsiusToFahrenheit(int celsius);
>    	static int convertFahrenheitToCelsius(int fahrenheit);
>   };
>   ```
>
>   新方法遵循与父类相同的命名约定。
>
>   记住，从其他代码角度上看，MyWeatherPrediction 对象具有 MyWeatherPrediction 和 WeatherPrediction 类定义的所有功能。采用父类的命名约定可以提供前后一致的接口。
>
>   我们把摄氏温度/华氏温度转换方法的实现如下：
>
>   ```c++
>   int MyWeatherPrediction::convertCelsiusToFahrenheit(int celsius)
>   {
>    	return static_cast<int>((celsius * 9.0 / 5.0) + 32);
>   }
>   
>   int MyWeatherPrediction::convertFahrenheitToCelsius(int fahrenheit)
>   {
>    	return static_cast<int>((fahrenheit - 32) * 5.0 / 9.0);
>   }
>   
>   ```
>
>   另外两个方法更为有趣，为了用摄氏温度设置当前温度，首先需要转换温度，其次将其以父类可以理解的单位传递给父类，进行对父类代码的复用：
>
>   ```c++
>   void MyWeatherPrediction::setCurrentTempCelsius(int temp)
>   {
>    	int fahrenheitTemp = getTomorrowTempFahrenheit();
>    	return convertFahrenheitToCelsius(fahrenHeitTemp);
>   }
>   ```
>
>   可以看出，执行温度转化后，这个方法调用了基类中的已有功能。同样地，getTomorrowTempCelsius() 的实现使用了父类的已有功能，获取华氏温度，但是在返回结果之前将其转换为摄氏温度：
>
>   ```c++
>   int MyWeatherPrediction::getTomorrowTempCelsius() const
>   {
>    	int fahrenheitTemp = getTomorrowTempFahrenheit();
>    	return convertFahrenheitToCelsius(fahrenheitTemp);
>   }
>   ```
>
>   这两个方法都有效地重用了父类，因为它们以某种方式**“封装”**了已有类的功能，并提供了使用这些功能的新接口。
>
>   还可以添加与父类已有功能无关的全新功能。例如，可以添加一个方法，从 Internet 获取其他天气预报，或添加一个方法，根据天气预报给出建议的活动。

****

#### 2.3在派生类中替换功能

>   与派生类相关的另一个主要技巧就是替换已有的功能。WeatherPrediction 类中的 showResult() 方法急需修改。MyWeatherPrediction 类可以重写这个方法，以替换原始实现中的行为：
>
>   ```c++
>   class MyWeatherPrediction : public WeatherPrediction
>   {
>    public:
>    	virtual void setCurrentTempCelsius(int temp);
>    	virtual int getTomorrowTempCelsius() const;
>    	virtual void showResult() const override;
>       
>    private:
>    	static int convertCelsiusToFahrenheit(int celsius);
>    	static int convertFahrenheitToCelsius(int Fahrenheit);
>   };
>   ```
>
>   下面给出了一个对用户友好的新实现：
>   ```C++
>   void MyWeatherPrediction::showResult() const
>   {
>    	cout << "Tomorrow's temperature will be " << getTomorrowTempCelsius() << " degrees Celsius (" << getTomorrowTemoFahrenheit() << " degrees Fahrenheit)." << endl;
>    	cout << "Chance of rain is " << (getChanceOfRain() * 100) << percent << endl;
>    	if (getChanceOfRain() > 0.5)
>    	{
>    		cout << "Bring an umbrella!";
>    	}
>   }
>   ```
>
>   对于使用这个类的客户而言，就像旧版本中的 showResult() 不曾存在一样。只要对象是一个 MyWeatherPrediction 对象，就会调用这个新版本的方法。
>
>   对于这些改动，我们还是强调：**对于其他代码而言，MyWeatherPrediction 首先包含了未修改的所有方法，其次也包含了所有修改后的 MyWeatherPrediction 的所有独特方法。它表现得像一个新类，具有适应更加具体目标的新功能，另外，由于对基类实现了复用，因此并不需要很多代码。**

****

### 10.3利用父类

>   编写派生类时，需要知道父类和派生类之间的交互方式。创建顺序、构造函数链和类型转换都是潜在 Bug 来源。

****

#### 3.1父类构造函数

>   **对象的构造必须同时创建父类和包含其中的对象，也就是和上面说的那样，创建顺序、构造函数链、类型转换都是潜在的问题，这部分在第 8 章有所涉及。**
>
>   为了规范继承中的构造，避免潜在的 Bug，C++ 定义了如下的创建顺序：
>
>   1.   如果某个类具有基类，执行基类的默认构造函数。**除非在 ctor-initializer 中调用了基类构造函数，否则，此时调用这个构造函数而不是默认构造函数。**(我来对后面这句话进行解释：编译器默认调用默认基类的默认构造函数的条件有两个：**派生类继承于父类** 和 **在派生类的 ctor-initializer 中没有显式地说明需要调用父类的某个构造函数。**)
>   2.   类的非静态数据成员按照声明的顺序创建。
>   3.   执行该类的构造函数。
>
>   可递归(嵌套)使用这些规则——如果类有祖父类，祖父类就在父类之前初始化，以此类推，下面的代码显式了创建的顺序。
>
>   通常建议不要在类定义中直接实现方法，如下面的代码所示，为了示例简介，这里我们直接再类定义中实现方法了。代码正确执行时的结果为："123"。
>
>   ```c++
>   class Something
>   {
>   public:
>   	Something() { cout << "2"; }
>   };
>   
>   class Base
>   {
>   	Base() { cout << "1"; }
>   };
>   
>   class Derived : public Base
>   {
>   public:
>   	Derived() { cout << "3"; }
>       
>   private:
>   	Something mDataMember;
>   };
>   
>   int main()
>   {
>   	Derived myDerived;
>   	return 0;
>   }
>   ```
>
>   在 main 函数中，我们看到首先创建了 Derived 类的对象 myDerived，它具有基类 Base，于是调用它的构造函数，输出字符串 "1"；随后，myDerived 的非静态成员按照顺序进行创建，于是调用 Something 构造函数，输出字符串 "2"，最后调用 Derived 构造函数，输出 "3"。
>
>   注意，Base 构造函数是自动调用的。也就是说，C++ 将自动调用父类的默认构造函数(如果存在的话)；如果父类的默认构造函数不存在，或者存在默认构造函数但是希望使用其他构造函数，可在构造函数初始化器(constructor initializer)中想初始化数据成员那样链接构造函数。例如，如下代码显示了没有默认构造函数版本的 Base 类。相关版本的 Derived 必须显式地告诉编译器如何调用 Base 的构造函数，否则代码将无法编译：
>
>   ```c++
>   class Base
>   {
>   public:
>   	// 没有默认构造函数，但是其实一般情况下都会编写一个的
>   	Base(int i);
>   };
>   
>   class Derived : public Base
>   {
>   public:
>   	Derived();
>   };
>   
>   Derived::Derived() : Base(7)
>   {
>   	// Do Derived's other initialization here.
>   }
>   ```
>
>   在上面这段代码中，Derived 构造函数向 Base 构造函数传递了固定值 (7)，如果 Derived 构造函数需要一个参数，也可以传递变量：
>
>   ```c++
>   Derived::Derived(int i) : Base(i) {}
>   ```
>
>   从派生类向基类传递构造函数的参数很常见，毫无问题，但无法传递数据成员。如果这么做，代码可以编译，但是记住在调用基类构造函数后才会初始化数据成员。如果将数据成员作为参数传递给父类构造函数，数据成员不会初始化的。
>
>   **警告：**
>
>   虚方法的行为在构造函数中是不同的，如果派生类重写了基类中的虚方法，从基类构造函数中调用虚方法，就会调用虚方法的基类实现而不是派生类中的重写版本。

****

#### 3.2父类的析构函数

>   由于析构函数没有参数，因此始终可以自动调用父类的析构函数。析构函数的调用顺序刚好与构造函数相反：
>
>   从对称角度上讲，构造函数在盖楼，父类是第一层，派生类是第二层；而析构函数则是拆楼，这时候需要从上往下拆，也就是首先析构派生类，再析构父类。
>
>   根本原因在于：继承可以类比为堆栈(栈，LIFO，Last In First Out)，尤其是析构函数的调用顺序。当一个对象被销毁时，析构函数的调用顺序与构造函数相反。即：
>
>   -   **构造时**，首先调用基类的构造函数，然后再调用派生类的构造函数(基类是"底层"，派生类是"顶层")。
>   -   **析构时**，派生类的析构函数先执行，然后才调用基类的析构函数(相当于从"顶层"开始拆除)。
>
>   这个现象可以类比于堆栈的“后进先出”原理，因为派生类是最后构造的，却是第一个被析构的。
>
>   1.   调用类的析构函数。
>   2.   销毁类的数据成员，与创建的顺序相反。
>   3.   如果有父类，调用父类的析构函数。
>
>   同样地，也可以递归(嵌套)地使用这些规则。链的最底层成员总是第一个被销毁的。下面的代码在前面的示例中加入了析构函数。所有析构函数都声明为 virtual，这一点非常重要，我们前面不久刚刚提到过。代码的执行结果为 "123321"：
>
>   ```c++
>   class Something
>   {
>   public:
>   	Something() { cout << "2"; }
>   	virtual ~Something() { cout << "2"; }
>   };
>   
>   class Base
>   {
>   public:
>   	Base() { cout << "1"; }
>   	virtual ~Base() { cout << "1"; }
>   };
>   
>   class Derived : public Base
>   {
>   public:
>   	Derived() { cout << "3"; }
>   	virtual ~Derived() { cout << "3"; }
>     	
>   private:
>   	Something mDataMember;
>   };
>   ```
>
>   即使前面的析构函数没有声明为 virtual，代码确实可以继续执行。然而，这样却会埋下隐患——**如果代码使用 delete 删除一个实际指向派生类的基类指针，析构函数调用链将被破坏。**例如，下面的代码与前面示例类似，但析构函数不是 virtual，当使用指向 Base 对象的指针访问 Derived 对象并删除对象时，就会出现很危险的问题：
>
>   ```c++
>   Base* ptr = new Derived();
>   delete ptr;
>   ```
>
>   代码输出很短，将会是："1231"，当删除 ptr 变量时，只调用了基类析构函数，也就是 Base 析构函数。原因是析构函数未声明为 virtual，编译器不会主动首先调用 Derived 的析构函数，而是一般只调用基类的析构函数，这一点在前面解释很明显了，详见 **虚析构函数的需求** 的内容。
>
>   也就是，从技术角度上，只需要将 Base 析构函数声明为 virtual，就可以纠正上面的问题。派生类将自动**虚化**。
>
>   因此，仅需要遵循那个被反复提出来的准则：**所有可能需要派生的类，都要将其方法(尤其是所有析构函数)(但不包含构造函数)声明为 virtual。**
>
>   **警告：**
>
>   **将所有析构函数声明为 virtual ！！！编译器生成的默认析构函数不是 virtual ！！！**(原因前面也讲了，虚化是需要一定的性能消耗的，是否消耗的问题在 C++ 标准中认为应当交给程序员自行决定。)因此，应当定义自己(或显式设置为默认)的虚析构函数，至少在父类中应该这样做。
>
>   **警告：**
>
>   与构造函数一样，在析构函数中调用虚方法时，虚方法的行为将有所不同。如果派生类重写了基类中的虚方法，在基类的析构函数中调用该方法，会执行该方法的基类实现，而不是派生类的重写版本。

****

#### 3.3使用父类方法

>   在派生类中重写方法时，将有效地替换原始方法。
>
>   然而，方法的父类版本仍然存在，仍然可以使用这些方法。
>
>   例如，某个重写方法可能除了完成父类实现完成的任务外，还会完成一些其他任务。考虑 WeatherPrediction 类中的 getTemperature() 方法，这个方法返回当前温度的字符串表示：
>
>   ```c++
>   class WeatherPrediction
>   {
>   public:
>   	virtual std::string getTemperature() const;
>   	// Omitted for brevity
>   };
>   ```
>
>   在 MyWeatherPrediction 类中，可按如下方法进行重写方法：
>
>   ```c++
>   class MyWeatherPrediction : public WeatherPrediction
>   {
>   public:
>   	virtual std::string getTemperature() const override;
>   	// Oitted for brevity
>   };
>   ```
>
>   假定派生类要先调用基类的 getTemperature() 方法，然后将 ℉ 添加到 string。为此，编写如下代码：
>
>   ```c++
>   string MyWeatherPrediction::getTemperature() const
>   {
>   	// Note: \u00B0F is the ISO/IEC 10646 representation of the degree symbol.
>   	return getTemperature() + "\u00B0F";	// BUG
>   }
>   ```
>
>   然而，上述代码无法正常运行，根据 C++ 的名称解析规则，首先解析的是局部作用域，然后是类作用域，根据这个顺序，函数中调用的是 MyWeatherPrediction::getTemperature()。其结果是无限递归，直到耗尽堆栈空间(某些编译器在编译时，会发现这种错误并报错)。
>
>   为让代码运行，需要使用作用域解析运算符进行限定，如下所示：
>
>   ```c++
>   string MyWeatherPrediction::getTemperature() const
>   {
>   	// Note: \u00B0F is the ISO/IEC 10646 representation of the degree symbol.
>   	return WeatherPrediction::getTemperature() + "\u00B0F";
>   }
>   ```
>
>   **注意：**
>
>   **Microsoft Visual C++ 支持 __super 关键字(两条下划线)，这个关键字允许编写如下代码：**
>
>   ```c++
>   return __super::getTemperature() + "\u00B0F";
>   ```
>
>   在 C++ 中，调用当前方法的父类版本是一种常见操作。如果存在派生类链，每个派生类都可能想执行基类中已经定义的操作，同时添加自己的附加功能。
>
>   如果你已经建立了程序员的思维一定会问的一个问题是：
>
>   _ _super 可以嵌套吗？
>
>   **不可以嵌套。** `__super` 只能用于直接访问当前类的直接基类。如果有多级继承结构，并且想要访问更上层的基类（比如“祖父类”），`__super` 不能连续调用来访问祖父类的成员。如果需要访问多级继承结构中的更上层基类，需要显式指定基类的名称。
>
>   另一个示例是书本类型的类层次结构。下图显示了这个层次的结构：
>
>   ![image-20240916103354429](https://s2.loli.net/2024/09/16/DLO6PEmnQTWzwcq.png)
>
>   由于层次结构底层的类更具体地指出了书本的类型，获取书本描述信息的方法实际上需要考虑层次结构中的所有层次。为此，可以连续调用父类方法，下面的代码演示了这一模式：
>
>   ```c++
>   class Book
>   {
>   public:
>   	virtual ~Book() = default;
>   	virtual string getDescription() const { return "Book"; }
>   	virtual int getHeight() const { return 120; }
>   };
>   
>   class Paperback : public Book
>   {
>   public:
>   	virtual string getDescription() const override
>   	{
>   		return "Paperback" + Book::getDescription();
>   	}
>   };
>   
>   class Romance : public Paperback
>   {
>   public:
>   	virtual string getDescription() const override
>   	{
>   		return "Romance" + Paperback::getDescription();
>   	}
>   
>   	virtual int getHeight() const override
>   	{
>   		return Paperback::getHeight() / 2;
>   	}
>   };
>   
>   class Technical : public Book
>   {
>   public:
>   	virtual string getDescription() const override
>   	{
>   		return "Technical" + Book::getDescription();
>   	}
>   };
>   
>   int main()
>   {
>   	Romance novel;
>   	Book book;
>   	cout << novel.getDescription() << endl;	// Outputs "Romance Paperback Book"
>   	cout << book.getDescription() << endl;	// Outputs "Book"
>   	cout << novel.getHeight() << endl;	// Outputs "60"
>   	cout << book.getHeight() << endl;	// Outputs "120"
>   }
>   ```
>
>   Book 基类有两个虚方法：getDescription() 和 getHeight()。所有派生类都重写了 getDescription()，只有 Romance 类通过调用父类(Paperback)的 getHeight()，然后将结果除以 2，重写了 getHeight()。Paperback 类没有重写 getHeight()，因此 C++ 会沿着类层次结构向上寻找实现了 getHeight() 的类。在本例中，Paperback::getHeight() 将解析为 Book::getHeight()。

****

#### 3.4向上转型和向下转型

>   **如上所述，对象可转换为父类对象，或者赋值给父类。**
>
>   **如果类型转换或赋值是对某个普通对象执行，会产生截断**：
>
>   ```c++
>   Base myBase = myDerived;	// Slicing!
>   ```
>
>   这种情况下会导致截断，因为赋值结果是 Base 对象，而 Base 对象缺少 Derived 类中定义的附加功能。
>
>   **然而，如果用派生类对基类的指针或引用赋值，则不会产生截断：**
>
>   ```c++
>   Base& myBase = myDerived;	// No slicing!
>   ```
>
>   这是通过基类使用派生类的正确途径，也叫做 **向上转型(upcasting)**，这也是让方法和函数使用类的引用，而不是直接使用类对象的原因。使用引用时，派生类在传递时没有截断。
>
>   **警告：**
>
>   当向上转型时，使用基类指针或引用以避免截断。
>
>   将基类转换为其派生类也叫做 **向下转型(downcasting)**，专业的 C++ 程序员通常不赞成这种转换，因为无法保证对象实际上属于派生了，也因为向下转型是不好的设计，因此尽量不要这样做。例如，考虑下面的代码：
>
>   ```c++
>   void presumptuous(Base* base)	// presumptuous，自以为是的，专横的，冒失的
>   {
>    	Derived* myDerived = static_cast<Derived*>(base);
>    	// Process to access Derived methods on myDerived.
>   }
>   ```
>
>   如果 presumptuous() 的作者还编写了调用 presumptuous() 的代码，那么可能一切正常，因为作者知道这个函数需要 Derived* 类型的参数。然而，如果其他程序员调用 presumptuous()，他们可能传递 Base*。编译时检测无法强制参数类型，因此函数盲目地假定 inBase 实际上是一个指向 Derived 对象的指针。
>
>   向下转型有时是必需的，在可控环境中可充分利用这种转换。然而，如果打算进行向下转型，应该使用 dynamic_cast()，以使用对象内建的类型信息，拒绝没有意义的类型转换。这种内建信息通常驻留在虚表中，这意味着 dynamic_cast() 只能用于具有虚表的对象，即至少有一个虚编号的对象。如果针对某个指针的 dynamic_cast() 失败，这个指针的值就是 nullptr，而不是指向某个无意义的数据。如果针对对象引用的 dynamic_cast() 失败，将抛出 std::bad_cast 异常。**第 11 章将详细讨论类型转换，这里不做展开。**
>
>   前面的示例应该这样编写：
>
>   ```c++
>   void lessPresumptuous(Base* base)
>   {
>    	Derived* myDerived = dynamic_cast<Derived>(base);
>    	if (myDerived != nullptr)
>    	{
>    		// Proceed to access Derived methods on myDericed.
>    	}
>   }
>   ```
>
>   **注意：**
>
>   **向下转型通常可以被认为是一种设计不良的标志。**
>
>   当出现时，你应当考虑如何修改设计，以避免使用向下转型。例如，lessPresumptuous() 函数实际上只能用于 Derived 对象，因此不应当接受 Base 指针，而应接收 Derived 指针。这样就不需要进行向下转型了。如果函数用于从 Base 继承的不同派生类，则应该考虑使用多态性的解决方案，也就是下一小节所要讲的。
>
>   **警告：**
>
>   **仅在必要的情况下才使用向下转型，一定要使用 dynamic_cast()。**

****

### 10.4继承与多态性

>   理解了派生类与父类的关系，就可以用最有力的方式使用继承——**多态性(polymorphism)**。第 5 章说过，多态性可以互换的使用具有共同父类的对象，并用对象替换父类对象。

****

#### 4.1回到电子表格

>   第 8 章和第 9 章使用电子表格程序作为示例来说明面向对象设计。SpreadsheetCell 代表一个数据元素。在前面，这个元素始终存储的是单个双精度值。下面给出了简化的 SpreadsheetCell 类定义。注意，单元格可以是双精度值或字符串，然而这个示例中单元格的当前值总以字符串的形式返回。
>
>   ```c++
>   class SpreadsheetCell
>   {
>    public:
>    	virtual void set(double inDouble);
>    	virtual void set(std::string_view inString);
>    	virtual std::string getString() const;
>       
>    private:
>    	static std::string doubleToString(double inValue);
>    	static double stringToDouble(std::string_view inString);
>    	double mValue;
>   };
>   ```
>
>   在实际的电子表格应用程序中，单元格可以存储不同的数据类型，有时单元格是双精度值，有时是文本。如果单元格需要其他类型，例如公式单元格或日期单元格，该怎么办？下面，我们就将逐步实现具有多态性的电子表格。

****

#### 4.2设计多态性的电子表格单元

>   SpreadsheetCell 类急需改变结构层次。有以下两种可能的设计思路：
>
>   1.   让 SpreadsheetCell 只包含字符串，从而限制其使用范围，在此过程中或许将其重命名为 StringSpreadsheetCell。为处理双精度值，可使用第二个类 DoubleSpreadsheetCell，这个类从 StringSpreadsheetCell 继承，并以自己的方式提供功能。这一个方法希望通过继承重用代码，因为 DoubleSpreadsheetCell 是 StringSpreadsheetCell 的唯一派生类，并利用了 StringSpreadsheetCell 内建的一些功能。这种设计中派生类将重写基类的绝大多数(但不是全部)功能。因为双精度与字符串的处理方式几乎完全不同，而且这种设计思路与最初的 **是一个** 的继承理解也有所背离。下图正是这一设计的结构图，：
>
>   ![image-20240916114553707](https://s2.loli.net/2024/09/16/tHhqsU5ARkweu4L.png)
>
>   2.   将 SpreadsheetCell 作为基类，派生出 StringSpreadsheetCell 和 DoubleSpreadsheetCell 两个子类，这样从其他代码的角度看，它们是可以互换的。谨记，**高内聚，低耦合！**实际上，这也意味着：
>        -   两个派生类都支持由基类定义的同一个接口(方法集)。
>        -   使用 SpreadsheetCell 对象的代码可以调用接口中的任何方法，而不需要知道这个单元格是 StringSpreadsheetCell 还是 DoubleSpreadsheetCell，这一方面实现了多态性，另外一方面也避免了要使用**向下转型**的潜在风险。
>        -   由于虚方法的特殊能力，会根据对象所属的类调用接口中的每个方法的正确示例。
>        -   其他数据结构(例如第 9 章讲述的 Spreadsheet 类)可通过引用父类类型，包含一组多类型的单元格。

****

#### 4.3SpreadsheetCell 基类

>   由于所有电子表格都是 SpreadsheetCell 基类的派生类，因此最好先编写这个类，当设计基类时，**应该考虑派生类之间的关系——也就是要提取各个派生类的共有特性并将其放于父类中**。例如，字符串单元格和双精度值单元格的共同点在于都包含单个数据块。由于数据来自用户，并显示给用户，可把这个值设置为字符串，并作为字符串获取。这些行为就是用来组成基类的共享功能。

##### 1.初次尝试

>   SpreadsheetCell 基类负责定义所有派生类支持的行为。在本例中，所有单元格都是需要加ing值设置为字符串。此外，所有单元格都需要将但钱值返回为字符串。基类定义中声明了这些方法，以及显式设置为默认的虚析构函数，但没有数据成员：
>
>   ```c++
>   class SpreadsheetCell
>   {
>    public:
>    	virtual ~SpreadsheetCell() = default;
>    	virtual void set(std::string_view inString);
>    	virtual std::string getString() const;
>   };
>   ```
>
>   当开始编写这个类的 .cpp 文件时，很快就会遇到问题。由于电子表格单元格的基类不包含 double 也不包含 string，如何实现这个类呢？更宽泛地讲，如何定义这样一个父类，这个父类声明了派生类支持的行为，但是并不定义这些行为的实现。
>
>   可能的方法之一时为这些行为实现 **什么都不做** 的功能。例如，调用 SpreadsheetCell 基类的 set() 方法将没有任何效用，因为基类没有任何成员需要设置。然而这样做，依旧存在问题——**理想情况下，基类不应该有示例。调用 set() 方法应该总是有效的，因为总会基于 DoubleSpreadsheetCell 或 StringSpreadsheetCell 的调用这个方法。**
>
>   **好的解决方案应该强制执行这一限制。**

##### 2.纯虚方法和抽象基类

>   **纯虚方法(pure virtual methods)是在类定义中显式地说明该方法不需要定义。即，如果将某个方法设置为纯虚方法，就是告诉编译器当类中不存在这个方法的定义。**
>
>   **抽象类(abstract class)是具有至少一个纯虚方法的类。即，这个类没有实例(因为纯虚方法的存在使得抽象类的方法不完整。编译器会强制接受这个事实：如果某个类包含一个或多个纯虚方法，就无法构建这个类型的对象。)。**
>
>   **采用专门的语法指定纯虚方法：方法声明后紧接 =0，不需要编写任何额外代码。**
>
>   ```c++
>   class SpreadsheetCell
>   {
>    public:
>    	virtual ~SpreadsheetCell() = default;
>    	virtual void set(std::string_view inString) = 0;
>    	vitual std::string getString() const = 0;
>   };
>   ```
>
>   现在基类成了抽象类，无法创建 SpreadsheetCell 对象，下面的代码将无法编译，并给出诸如 **error C2259: 'SpreadsheetCell' cannot instantiate abstract class** 的错误。
>
>   ```c++
>   SpreadsheetCell cell; // Error! Attempts creating abstract class instance.
>   ```
>
>   然而，一旦实现了 StringSpreadsheetCell 类，下面的代码就可以成功编译，原因在于实例化了抽象基类的派生类：
>
>   ```c++
>   std::unique_ptr<SpreadsheetCell> cell(new StringSpreadsheetCell());
>   ```
>
>   **注意：**
>
>   **抽象类提供了一种禁止其他代码直接实例化对象的方法，而它的派生类可以实例化对象。**
>
>   **注意：**
>
>   **在 SpreadsheetCell 的实现中，并不需要 SpreadsheetCell.cpp 源文件，因为没有要实现的内容。大多数方法都是纯虚方法，在类定义中，将析构函数显式地设置为默认**

****

#### 4.4独立的派生类

>   编写 StringSpreadsheetCell 和 DoubleSpreadsheetCell 类只需要实现父类中定义的功能。因为想让客户实现并使用字符串单元格和双精度单元格，因此**单元格不应该再是抽象的——必须实现从父类继承的所有纯虚方法。**如果派生类没有实现从父类继承的所有纯虚方法，那么派生类也将是抽象的，客户就不能够通过当前的派生类来实例化对象。

##### 1.StringSpreadsheetCell 类定义

>   1.  从 SpreadsheetCell 类继承；
>   2.  重写继承的纯虚方法，此次不再将其设置为 0；
>   3.  为字符串单元格添加一个私有数据成员 mValue，在其中存储实际单元格数据。**这个数据是 std::optional，从 C++17 开始定义在 <optional> 头文件中。optional 类型是一个类模板，因此必须在尖括号之间指定所需的实际类型，如 optional<string>。第 12 章将详细阐述类模板的用法。通过使用 optional 类型，可以确认是否已经设置了单元格的值。这部分具体关于 optional 类型的内容，将在第 20 章讨论，其用法是相当简单的。**
>
>   ```c++
>   class StringSpreadsheetCell : public SpreadsheetCell
>   {
>   public:
>   	virtual void set(std::string_view inString) override;
>   	virtual std::string getString() const override;
>       
>   private:
>   	std::optional<std::string> mValue;
>   };
>   ```

##### 2.StringSpreadsheetCell 的实现

>   StringSpreadsheetCell 的源文件包含方法的实现。
>
>   set() 方法十分简单，因为内部表示已经是一个字符串了。
>
>   getString() 方法必须考虑到 mValue 的类型是 optional，可能不具有值——如果 mValue 不具有值，getString() 将返回一个空字符串。可使用 std::optional 的 value_or() 方法对此进行简化。使用 mValue.value_or("")，如果 mValue 包含实际的值，将返回相应的值，否则返回空值。
>
>   ```c++
>   void StringSpreadsheetCell::set(string_view inString)
>   {
>    	mValue = inString;
>   }
>   
>   string StringSpreadsheetCell::getString() const
>   {
>    	return mValue.value_or("");
>   }
>   ```

##### 3.DoubleSpreadsheetCell 类定义

>   1.  从 SpreadsheetCell 类继承；
>   2.  重写继承的纯虚方法，此次不再将其设置为 0；
>   3.  双精度版本遵循类似的模式，但具有不同的逻辑。除了以 string_view 作为参数的基类的 set() 方法以外，还提供新的 set() 方法以允许用户使用双精度设置其值。两个新的 private static 方法用于转换字符串和双精度值。与 StringSpreadsheetCell 相同，这个类也有一个 mValue 数据成员，此时这个数据成员的类型是 optional<double>。
>
>   ```c++
>   class DoubleSpreadsheetCell : public SpreadsheetCell
>   {
>   public:
>   	virtual void set(double inDouble);
>   	virtual void set(std::string_view inString) override;
>   	virtual std::string getString() const override;
>       
>   private:
>   	static std::string doubleToString(double inValue);
>   	static double stringToDouble(std::string_view inValue);
>       
>   	std::optional<double> mValue;
>   };
>   ```

##### 4.DoubleSpreadsheetCell 的实现

>   以双精度值作为参数的 set() 方法简单明了。string_view 版本使用 private static 方法 stringToDouble()；getString 方法返回存储的双精度值作为字符串；如果未存储任何值，则返回一个空字符串；它使用 std::optional 的 has_value() 来查询 optional 是否具有实际值。如果具有值，则使用 value() 方法来获取：
>
>   ```c++
>   void DoubleSpreadsheetCell::set(double inDouble)
>   {
>    	mValue = inDouble;
>   }
>   
>   void DoubleSpreadsheetCell::set(std::string_view inString)
>   {
>    	mValue = stringToDouble(inString);
>   }
>   
>   string DoubleSpreadsheetCell::getString() const
>   {
>    	return (mValue.has_value() ? (doubleToString(mValue.value())) : (""));
>   }
>   ```
>
>   可以看到，在层次结构中实现了电子表格单元格的主要优点是代码更简单。每个对象都以自我为中心，只执行各自的功能。
>
>   注意，在这里省略了 doubleToString() 和 stringToDouble() 方法的实现，因为第 8 章已经实现了。

****

#### 4.5利用多态性

>   现在 SpreadsheetCell 层次结构具有多态性，客户嗲吗可以利用多态性带来很多好处。
>
>   下面将由这些测试程序来演示多样性的功能：测试程序声明了一个具有 3 个 SpreadsheetCell 指针的矢量，记住由于 Spreadsheet 是一个抽象类，因此不能创建这种类型的对象。然而，仍然可以使用 SpreadsheetCell 的指针或引用，因为它实际上指向的是其中一个派生类。由于是父类型 SpreadsheetCell 的矢量，因此可以任意存储两个派生类。这意味着矢量元素可以是 StringSpreadsheetCell 或 DoubleSpreadsheetCell。
>
>   ```c++
>   vector<unique_ptr<SpreadsheetCell>> cellArray;
>   ```
>
>   矢量的前两个元素指向新建的 StringSpreadsheetCell，第三个元素指向一个新的 DoubleSpreadsheetCell：
>
>   ```c++
>   cellArray.push_back(make_unique<StringSpreadsheetCell>());
>   cellArray.push_back(make_unique<StringSpreadsheetCell>());
>   cellArray.push_back(make_unique<DoubleSpreadsheetCell>());
>   ```
>
>   现在矢量包含了多类型数据，基类声明的任何方法都可以应用到矢量中的对象。
>
>   代码只是使用了 SpreadsheetCell 指针——编译器在编译时不知都对象的实际类型是什么。
>
>   然而，由于这两个类是 SpreadsheetCell 的派生类，因此必须支持 SpreadsheetCell 的方法。
>
>   ```c++
>   cellArray[0]->set("hello");
>   cellArray[1]->set("10");
>   cellArray[2]->set("18");
>   ```
>
>   当调用 getString() 方法时，每个对象都会正确地返回值的字符串表示。重要的(同时也是某种意义上令人震惊的)是，不同对象以不同的方式完成这一任务。StringSpreadsheeCell 返回它存储的值，或返回空字符串。如果包含值，DoubleSpreadsheetCell 首先执行转换；否则返回一个空字符串。程序员不需要知道对象如何做到这一点——只需要知道对象是一个 SpreadsheetCell，因此可以执行此行为：
>
>   ```c++
>   cout << "Vector value are [" << cellArray[0]->getString() << ", " << cellArray[1]->getString() << ", " << cellArray[2]->getString() << "]" << endl;
>   ```

****

#### 4.6考虑将来

>   SpreadsheetCell 层次结构的新实现从面向对象设计的观点来看当然是一个进步。但是，对于实际的电子表格程序来说，这个类层次结构还不够充分，主要有以下几个原因：
>
>   1.  即使不考虑改进设计，现在仍然缺少一个功能：将某个单元格类型转换为其他类型。由于将单元格分为两类,单元格对象的结合变得更松散。为提供将 DoubleSpreadsheetCell 转换为 StringSpreadsheetCell 的功能，应添加一个转换构造函数(或类型构造函数)，这个构造函数类似于复制构造函数，但参数不是对同类对象的引用，而是对同级类对象的引用。另外注意，现在必须声明一个默认构造函数，可将其显式设置为默认，因为一旦自行声明任何构造函数，编译器将停止生成：
>
>   ```c++
>   class StringSpreadsheetCell : public SpreadsheetCell
>   {
>   public:
>   	StringSpreadsheetCell = default;
>   	StringSpreadsheetCell(const DoubleSpreadsheetCell& inDoubleCell);
>   	// Omitted for brevity.
>   };
>   ```
>
>   将转换构造函数实现为如下形式：
>
>   ```c++
>   StringSpreadsheetCell::StringSpreadsheetCell(const DoubleSpreadsheetCell& inDoubleCell)
>   {
>   	mValue = inDoubleCell.getString();
>   }
>   ```
>
>   通过转换构造函数，可以很方便地用 DoubleSpreadsheetCell 创建 StringSpreadsheetCell：
>
>   ```c++
>   DoubleSpreadsheetCell doubleCell;
>   StringSpreadsheetCell stringCell = doubleCell;  // 自动调用转换构造函数
>   ```
>
>   然而，**不要将其与指针或引用的类型转换器混淆，类型转换无法将一个指针或引用转换为同级的另一个指针或引用。**除非按照第 15 章讲述的方法，重载类型转换运算符。
>
>   **警告：**
>
>   在层次结构中，总可以向上转型，有时也可以向下转型。改变类型转换运算符的行为，或者使用 interpret_cast<> 就可以在层次结构中进行类型转换。(但，不推荐这种方法)
>
>   2.   其次，如何为单元格实现运算符重载是一个很有趣的问题，在此有几种可能的解决方案。其中一种方案是：针对每个单元格组合，实现每个运算符的重载版本。由于只有两个派生类，因此这样做并不难。可编写一个operator函数，将两个双精度单元格相加，将两个字符串单元格相加，将双精度单元格与字符串单元格相加。另一种方案是给出一种通用表示，前面的实现己将字符串作为标准化的通用类型表示。通过这种通用表示，一个 operator+ 函数就可以处理所有情况。假定两个单元格相加的结果始终是字符串单元格，那么一个可能的实现如下所示：
>
>   ```c++
>   StringSpreadsheetCell operator+(const StringSpreadsheetCell& lhs,
>   	const StringSpreadsheetCell& rhs)
>   {
>   	StringSpreadsheetCell newCell;
>   	newCell.set(lhs.getString() + rhs.getString());
>   	return newCell;
>   }
>   ```
>
>   只要编译器可将特定的单元格转换为 StringSpreadsheetCell，这个运算符就可以运行。考虑前面的示例，StringSpreadCell 构造函数采用 DoubleSpreadsheetCell 作为参数，如果这是 operator+ 运行的唯一方法，那么编译器将自动执行转换。这意味着下面的代码可以运行，尽管 operator+ 被现实地用于 StringSpreadsheetCell：
>
>   ```c++
>   DoubleSpreadsheetCell myDbl;
>   myDbl.set(8.4);
>   StringSpreadsheetCell result = myDbl + myDbl;
>   // 运算 myDbl + myDbl 会各自生成一个临时的 DoubleSpreadsheetCell 对象
>   // 然后经过转换构造函数，将会自动转换为 StringSpreadsheetCell 对象
>   // 执行 operator+ 函数中的任务
>   // 返回 StringSpreadsheetCell 结果
>   ```
>
>   当然，相加的结果实际上并不是将数字相加，而是将双精度单元格转换为字符串单元格，然后将字符串相加，结果是一个值为 "8.4000008.400000" 的 StringSpreadsheetCell。
>
>   如果对多态性还不确定，可运行这个示例的代码并获取答案。如果只是为了体验这个类的各种特性，前面的示例中的 main() 函数就是一个很好的起点。

****

### 10.5多重继承

>   第 5 章已经讲过，多重继承通常被认为是面向对象编程中一种复杂且不必要的部分。
>
>   接下来请详细讲述，多重继承是否有用，并阐述 C++ 中多重继承的机制。

****

#### 5.1从多个类继承

>   从语法角度来看，定义具有多个父类的类很简单，为此，只需要在声明类时分别列出来基类即可：
>
>   ```c++
>   class Baz : public Foo, public Bar
>   {
>    	// Etc.
>   };
>   ```
>
>   由于列出了多个父类，Baz 对象具有如下特性：
>
>   -   Baz 对象支持 Foo 和 Bar 类的 public 方法，并且包含这两个类的数据成员；
>   -   Baz 类的方法有权访问 Foo 和 Bar 类的 protected 数据成员和方法；
>   -   Baz 对象可以向上转型为 Foo 或 Bar 对象；
>   -   创建新的 Baz 对象将自动调用 Foo 和 Bar 类的默认构造函数，并按照类定义中列出的类顺序进行；
>   -   删除 Baz 对象将自动调用 Foo 和 Bar 类的析构函数，调用顺序与类在类定义中列出的类顺序相反；
>
>   下例显示了一个 DogBird 类，它有两个父类 —— Dog 和 Bird 类，如下图所示：
>
>   ![image-20240917234504801](https://s2.loli.net/2024/09/17/VlrE6owGgajePxW.png)
>
>   很明显，这是一个荒谬之至的示例，但是不应该就这样轻易地认为多重继承本身是荒谬的，这一点是需要注意判断的：
>
>   ```c++
>   class Dog
>   {
>   public:
>   	virtual void bark() { cout << "Woof!" << endl; }
>   };
>   
>   class Bird
>   {
>   public:
>   	virtual void chirp() { cout << "Chirp!" << endl; }
>   };
>   
>   class DogBird : public Dog, public Bird
>   {
>   
>   };
>   ```
>
>   什么时候不荒谬？假设我们设计一个系统，模拟多种载具(比如汽车和船)。有些载具可以同时在陆地和水上行驶，比如两栖车辆。在这个例子中，两栖车辆(AmphibiousVehicle) 合理地继承了 汽车(Car) 和 船(Boat) 的特性，因为这种车辆确实可以同时在陆地和水上移动。多重继承在这种场景下能够帮助我们创建一个具备双重行为的类，这在现实世界中是合理且符合常识的。这样，一个合理的多重继承设计如下：
>
>   ```c++
>   class Car
>   {
>   public:
>   	virtual void drive() { cout << "Driving on the road!" << endl; }
>   };
>   
>   class Boat
>   {
>   public:
>   	virtual void sail() { cout << "Sailing on the water!" << endl; }
>   };
>   
>   // AmphibiousVehicle 是一个既可以作为汽车，也可以作为船的载具
>   class AmphibiousVehicle : public Car, public Boat
>   {
>   public:
>   	void drive() override { cout << "Driving on both road and water!" << endl; }
>   };
>   ```
>
>   使用具有多个父类的类对象与使用具有单个父类的类对象没有什么不同。实际上，客户代码甚至不需要知道这个类有两个父类。需要关心的只是这个类支持的属性和行为。在此情况下，DogBird 对象支持 Dog 和 Bird 类的所有 public 方法。
>
>   ```c++
>   DogBird myConfusedAnimal;
>   myConfusedAnimal.bark();
>   myConfusedAnimal.chirp();
>   ```
>
>   程序的输出如下：
>
>   ```c++
>   Woof!
>   Chirf!
>   ```

****

#### 5.2名称冲突和歧义基类

>   多重继承崩溃的场景并不难想象，下面的示例显示了一些必须要考虑的边缘情况。

##### 1.名称歧义

>   如果 Dog 类和 Bird 类都有一个 eat() 方法，会发生什么？由于 Dog 类和 Bird 类毫不相干，eat() 方法的一个版本无法重写另一个版本 —— 在派生类 DogBird 中这两个方法都存在。
>
>   如果客户不调用 eat() 方法，就不会出现问题。尽管有两个版本的 eat() 方法，但 DogBird 类仍然可以正确编译。然而，如果用户代码试图调用 DogBird 类中的 eat() 方法(参数列表相同时)，编译器将会报错，指出对 eat() 方法的调用存在歧义，编译器不知道该调用哪个版本；另外，如果用户代码试图调用 DogBird 类中的 eat() 方法(参数列表或返回值**不相同**时)，这里又分为三种情况：参数列表不同，调用的参数能够明确匹配某一个基类的 `eat()` 方法，则编译器不会报出歧义错误；参数类型相似或可以转换，导致歧义错误；返回值类型不同**不会**帮助编译器区分函数的重载，也因此可能造成歧义错误。下面的代码存在歧义错误：
>
>   ```c++
>   class Dog
>   {
>    public:
>    	virtual void bark() { cout << "Woof!" << endl; }
>    	virtual void eat() { cout << "The dog ate." << endl; }
>   };
>   
>   class Bird
>   {
>    public:
>    	virtual void chirp() { cout << "Chirp！" << endl; }
>    	virtual void eat() { cout << "The bird ate."; }
>   };
>   
>   class DogBird : public Dog, public Bird
>   {
>       
>   };
>   
>   int main()
>   {
>    	DogBird myConfusedAnimal;
>    	myConfusedAnimal.eat();	// Error! Ambiguous call to method eat()
>       
>    	return 0;
>   }
>   ```
>
>   为了消除歧义，可使用 dynamic_cast() 显式地将对象向上转型(本质上是向编译器隐藏多余的方法版本)，也可以使用歧义消除语法。下面的代码显示了调用 eat() 方法的 Dog 版本的两个方法：
>
>   ```c++
>   dynamic_cast<Dog&>(myConfusedAnimal).eat();	// Calls Dog::eat()
>   myConfusedAnimal.Dog::eat();			   // Calls Dog::eat()
>   ```
>
>   使用与访问父类方法相同的语法(:: 运算符)，派生类的方法本身可以显示地为同名的不同方法消除歧义。例如，DogBird 类可以定义自己的 eat() 方法，从而消除其他代码中的歧义错误。在方法内部，可以判断调用那个父类：
>
>   ```c++
>   class DogBird : public Dog, public Bird
>   {
>    public:
>    	void eat() override;
>   };
>   
>   void DogBird::eat()
>   {
>    	Dog::eat();		// Explicitly call Dog's version of eat()
>   }
>   ```
>
>   另一种防止歧义错误的方式是使用 using 语法显式指定，在 DogBird 类中应继承哪个版本的 eat() 方法，如下面的 DogBird 类定义所示：
>
>   ```c++
>   class DogBird : public Dog, public Bird
>   {
>    public:
>    	using Dog::eat;	// Explicitly inherit Dog's version of eat()
>   };
>   ```

##### 2.歧义基类

>   另一种引起歧义的情况是从同一个类继承两次。例如，如果出于某种原因 Bird 类从 Dog 类继承，DogBird 类的代码将无法编译，因为 Dog 编程了歧义基类。
>
>   ```c++
>   class Dog {};
>   class Bird : public Dog {};
>   class DogBird : public Bird, public Dog {};	// Error!
>   ```
>
>   多数歧义基类的情况或者是由人为的 **what-if** 示例(如前面的示例)引起的，或者是由于类层次结构的混乱引起的。下图显示出前面中的类图，并指出了歧义所在：
>
>   ![image-20240918223823395](https://s2.loli.net/2024/09/18/GJjAFVDsbn8Sxd1.png)
>
>   数据成员也可以引起歧义，如果 Dog 和 Bird 类具有同名的数据成员，当客户代码尝试访问这个成员时，就会发生歧义错误。
>
>   多个父类本身也可能有共同的父类。例如，Bird 和 Dog 类可能都是 Animal 类的派生类，如下图所示：
>
>   ![image-20240918224003144](https://s2.loli.net/2024/09/18/1uoTNM6G7dLI8qx.png)
>
>   C++ 允许这种类型的类层次结构，尽管仍然存在着名称歧义。例如，如果 Animal 类有一个公有方法 sleep()，DogBird 对象将无法调用这个方法，因为编译器不知道调用 Dog 类继承的版本还是 Bird 类继承的版本。
>
>   **使用 菱形类层次结构 的最佳方法是将 最顶部的类设置为 抽象类，将所有方法都设为纯虚方法。**由于类只声明方法而提供定义，在基类中没有方法可以调用，因此在这个层次上就没有歧义。
>
>   下例实现了菱形类层次结构，其中有一个每个派生类都必须定义的纯虚方法 eat()，DogBird 类仍须显式说明使用哪个父类的 eat() 方法，但是 Dog 和 Bird 类引起歧义的原因是：它们具有相同的方法，而不是因为从同一个类继承：
>
>   ```c++
>   class Animal
>   {
>    public:
>    	virtual void eat() = 0;		// 设置为纯虚函数
>   };
>   
>   class Dog : public Animal
>   {
>    public:
>    	virtual void bark() { cout << "Woof!" << endl; }
>    	virtual void eat() override { cout << "The dog ate." << endl; }
>   };
>   
>   class Bird : public Animal
>   {
>    public:
>    	virtual void chirp() { cout << "Chirp!" << endl; }
>    	virtual void eat() override { cout << "The bird ate." << endl; }
>   };
>   
>   class DogBird : public Dog, public Bird
>   {
>    public:
>    	using Dog::eat;
>   };
>   ```
>
>   虚基类是处理菱形类层次结构中顶部类的更好方法，这部分将详细在本章结尾讲述。

##### 3.多重继承的用途

>   **为什么程序员需要在代码中使用多重继承？**
>
>   **因为多重继承最直接的用例就是：定义了一个既 是一个 事物 A，又 是一个 事物 B 的类对象。第 5 章已经说过了，遵循这个模式的实际对象很难恰当地转换为代码。****
>
>   **多重继承最简单有力的用途就是：实现混入(mix-in)类。**混入类详见第 5 章。
>
>   **使用多重继承的另一个原因是模拟基于组件的类。**第 5 章给出了飞机模拟示例，Airplane 类有引擎、机身、控制系统和其他组件。尽管 Airplane 类的典型是将这些组件当作独立的数据成员，但是也可以使用多重继承。飞机类可以从引擎、机身、控制系统继承，从而有效地获得这些组件的行为和属性。
>
>   建议不要使用这些类型的代码，这将 **有一个** 关系与继承混淆了，而继承用于 **是一个** 关系。推荐的解决方案是让 Airplane 类包含 Engine、Fuselage 和 Controls 类型的数据成员。
>
>   在C++实际开发中，多重继承并不是特别常用的手段，尽管它是C++语言提供的功能。相比单一继承，多重继承由于其复杂性和潜在的问题，使用频率较低。以下是一些原因和实际情况：
>
>   -   当一个类通过多条继承路径从同一个基类继承时，可能会引发菱形继承问题。这可能导致歧义和不必要的内存占用。为了避免这种问题，C++引入了**虚拟继承**（`virtual inheritance`），但这也增加了复杂性。
>   -   多重继承容易让类结构变得复杂、难以维护。如果设计不合理，多重继承会使得代码难以理解和调试，特别是在需要跟踪多个基类的行为或相互依赖的情况下。
>
>   -   C++中更常用的设计模式是通过单继承配合**接口类**（通常是纯虚类）来实现多态。这类似于 Java 和 C# 中的接口。例如：
>
>
>      ```cpp
>   class Printable {
>   public:
>   	virtual void print() const = 0; // 纯虚函数
>   };
>      
>   class Shape : public Printable {
>   public:
>   	void print() const override {
>   		// 打印Shape信息
>   	}
>   };
>      ```
>
>      通过这种方式，可以在避免多重继承带来的复杂性的同时实现灵活的多态行为。
>
>   -   C++开发中一个常见的设计原则是**组合优于继承**（Composition over Inheritance）。在需要多个功能时，通常会选择组合（对象包含其他对象的方式）而非多重继承。例如：
>
>
>      ```cpp
>   class Engine { /*...*/ };
>   class Wheels { /*...*/ };
>   
>   class Car {
>   private:
>   	Engine engine;
>   	Wheels wheels;
>   public:
>   	void drive() { /* 使用engine和wheels */ }
>   };
>      ```
>
>      这种方式比多重继承更灵活且容易维护。

##### 多重继承的常见使用场景

>      尽管多重继承很少被使用，但在某些场景下是有用的：
>      - **接口类的多继承**：当多个基类都是纯虚类时，多重继承的复杂性较低，因为这些类仅定义接口，而没有实现细节。例如，类可以同时继承多个接口类而没有歧义问题。
>      - **混入类（Mixin Classes）**：有时会使用轻量级的辅助类来增强某些功能，如日志记录、调试等。此时可以通过多重继承混入这些功能。
>
>      ```cpp
>      class Loggable {
>      public:
>      	void log() { /* 日志功能 */ }
>      };
>   
>      class Debuggable {
>      public:
>      	void debug() { /* 调试功能 */ }
>      };
>   
>      class Application : public Loggable, public Debuggable {
>      	// Application 具有日志和调试功能
>      };
>      ```
>

****

### 10.6有趣而晦涩的继承问题

>   拓展类总是引发多种问题：类的哪些特征可以改变，哪些不能改变？什么是非公共继承？什么是虚基类？下面将详细将上面已经讲过的内容进行详细阐述。

****

#### 6.1修改重写方法的特征

>   **重写某个方法的主要原因是为了修改方法的实现。然而，有时候是为了修改方法的其他特征。**

##### 1.修改方法的返回类型

>   根据经验，重写方法要使用与基类一致的方法声明(或方法原型)。实现可以改变，但原型保持不变。
>
>   然而事实未必总是如此，在 C++ 中，如果原始的返回类型是某个类的指针或引用，重写的方法可将返回类型改为派生类的指针或引用。即：在使用多态时，任何子类的对象应该能够替换其基类的对象，而不会影响程序的正确性。这种类型称为 **协变返回类型(covariant return types)**。如果基类和派生类处于 **平行层次结构(parallel hierachy)**，使用这个特性可以带来便利。**平行层次结构是指：一个类层次结构与另一个类层次结构之间没有相交，但是存在联系。**
>
>   考虑以下樱桃果园模拟程序，可使用两个类层次结构模拟不同但明显相关的实际对象：
>
>   -   第一个是 Cherry 类层次结构，Cherry 基类有一个名为 BingCherry 的派生类；
>   -   于此类似，另一个类层次机构的基类为 ChreeyTree，派生类为 BingCherryTree。
>
>   下图正显示了这两个类层次结构：
>
>   ![image-20240918233547572](https://s2.loli.net/2024/09/18/k17KBW9ebL8jslP.png)
>
>   现在假定 CherryTree 类有一个虚方法 pick()，这个虚方法从樱桃树上获取一个樱桃：
>
>   ```c++
>   Cherry* CherryTree::pick()
>   {
>   	return new Cherry();
>   }
>   ```
>
>   **注意：**
>
>   **为了演示如何更改返回类型，本例未返回智能指针，而是返回普通指针。本节的末尾将解释为什么这样做，当然，调用者应当在智能指针(而非普通指针)中立即存储结构。**
>
>   在 BingCherryTree 派生类中，要重写这个方法，或许冰樱桃在摘下来时需要擦拭(请允许我们这么说)。由于冰樱桃也是樱桃，在下例中，方法的原型保持不变，而方法被重写。BingCherry 指针被自动转换为 Cherry 指针。注意这个实现使用 unique_ptr 来确保 polish() 抛出异常时，没有泄露内存。
>
>   ```c++
>   Cherry* BingCherryTree::pick()
>   {
>   	auto theCherry = std::make_unique<BingCherry>();
>   	theCherry->polish();
>   	return theCherry.release();
>   }
>   ```
>
>   `std::unique_ptr` 是一种 **独占所有权** 的智能指针，意味着它管理的资源只能由一个指针拥有。`release()` 函数的作用是 **释放智能指针对所管理对象的控制权**，但 **不会销毁该对象本身**。也就是说，调用 `release()` 后，`unique_ptr` 不再管理资源，资源的所有权转交给调用者，而智能指针本身变为空指针（`nullptr`）。
>
>   上面这个实现非常好，然而，由于 BingCherryTree 类始终返回 BingCherry 对象，因此可通过修改返回类型，像这个类的潜在用户指明这一点，如下所示：
>
>   ```c++
>   BingCherry* BingCherryTree::pick()
>   {
>   	auto theCherry = std::make_unique<BingCherry>();
>   	theCherry->polish();
>   	return theCherry.release();
>   }
>   ```
>
>   下面是 BingCherryTree::pick 方法的用法：
>
>   ```c++
>   BingCherryTree theTree;
>   std::unique_ptr<Cherry> theCherry(theTree.pick());
>   theCherry->printType();
>   ```
>
>   为判断能否修改重写方法的返回类型，可以考虑已有代码是否能够继续运行，这称为 **里氏替换原则(Liskov Substitution Principle，LSP)**。在上例中，修改返回类型没有问题，因为假定 pick() 方法总是返回 Cherry* 的代码，仍然可以基于 BingCherryTree 版本的 pick() 返回值进行调用。
>
>   不能将返回类型修改为完全不相关的类型，例如 void*。下面的代码无法编译：
>
>   ```c++
>   void* BingCherryTree::pick()
>   {
>   	auto theCherry = std::make_unique<BingCherry>();
>   	theCherry->polish();
>   	return theCherry.release();
>   }
>   ```
>
>   这段代码会导致编译错误，如下所示：
>
>   ```c++
>   'BingCherryTree::pick': overriding virtual function return type differs and is not covariant from 'CherryTree::pick'.
>   ```
>
>   如前所述，这个示例正用普通指针代替智能指针。将 std::unique_ptr 用作返回类型时，这不能用于本例。假设 CherryTree::pick() 返回 unique_ptr<Cherry>，如下所示：
>
>   ```c++
>   std::unique_ptr<Cherry> CherryTree::pick()
>   {
>   	return std::make_unique<Cherry>();
>   }
>   ```
>
>   此时，无法将 BingCherryTree::pick() 方法的返回类型改为 unique_ptr<BingCherry>。下面的代码无法编译：
>
>   ```c++
>   class BingCherryTree : public CherryTree
>   {
>   public:
>   	virtual std::unique_ptr<BingCherry> pick() override;
>   };
>   ```
>
>   原因在于 std::unique_ptr 是类模板，第 12 章将详细讨论类模板。创建 unique_ptr 类模板的两个示例 unique_ptr<Cherry> 和 unique_ptr<BingCherry>，它们是 **完全不同的类型**，尽管 `BingCherry` 是 `Cherry` 的派生类。这两个实例时完全不同的类型，完全无关。无法更改重写方法的返回类型，来返回完全不同的类型。

##### 为什么智能指针不支持协变？

>   -   **模板类型实例化独立性**：模板类型的实例化会产生新的类型，例如 `std::unique_ptr<Cherry>` 和 `std::unique_ptr<BingCherry>` 是两个不同的模板实例，这些类型没有直接的父子继承关系。
>   -   **内存管理复杂性**：`std::unique_ptr` 拥有资源的独占所有权，管理着指针的生命周期。在模板实例不同的情况下，智能指针无法简单地处理不同类型之间的内存管理。假设 `unique_ptr<BingCherry>` 被强制转换为 `unique_ptr<Cherry>`，在删除操作中会导致严重的类型不匹配问题，从而破坏智能指针的内存安全。

##### 2.修改方法的参数

>   **重写（override）时，基类和派生类的方法必须参数列表相同，这样才能正确重写。**
>
>   **如果参数列表不同，编译器会认为你是在定义一个新方法，而不是重写基类的方法。**
>
>   回到本章前面的 Base 和 Derived 类示例，可试着在 Derived 类中使用新的参数列表重写 someMethod() 方法，如下所示：
>
>   ```c++
>   class Base
>   {
>    public:
>    	virtual void someMethod();
>   };
>   
>   class Derived : public Base
>   {
>   public:
>    	virtual void someMethod(int i);		// Compiles, but doesn't override
>    	virtual void someOtherMethod();
>   };
>   ```
>
>   这个方法的实现如下所示：
>
>   ```c++
>   void Derived::someMethod(int i)
>   {
>    	cout << "This is Derived's version of someMethod with argument" << i << "." << endl;
>   }
>   ```
>
>   前面的类定义可以编译，但没有重写 someMethod() 方法。因为参数不同，所创建的是一个只存在于 Derived 类中的新方法。如果需要 someMethod() 方法采用 int 参数，并且只将这个方法应用于 Derived 类对象，前面的代码没有问题。
>
>   但是，实际上，C++ 标准指出，当 Derived 类定义了这个方式是，原始的方法被隐藏，下面的代码无法编译，因为没有参数的 someMethod() 方法不再存在。
>
>   ```c++
>   Derived myDerived;
>   myDerived.someMethod();		// Error! Won't compile because original method is hidden.
>   ```
>
>   如果希望重写基类中的 someMethod() 方法，就应该像前面建议的那样使用 override 关键字。如果在重写方法时发生错误，编译器会报错。
>
>   可使用一种比较晦涩的技术兼顾二者 —— 也就是说，可使用这一技术在派生类中有效地用新的原型 **重写** 某个方法，并继承该方法的基类版本。这一技术使用 using 关键字显式地在派生类中包含这个方法的基类定义：
>
>   ```c++
>   class Base
>   {
>    public:
>    	virtual void someMethod();
>   };
>   
>   class Derived : public Base
>   {
>    public:
>    	using Base::someMethod;		// Explicitly "inherits" the Base version
>    	virtual void someMethod(int i);		// Adds a new version of someMethod
>       	
>    	// 这里的原理就是：首先利用 using 语法进行引入 Base 类中的 someMethod()之后再进行函数重载。
>       
>    	virtual void someOtherMethod();
>   };
>   ```
>
>   **注意：**
>
>   派生类的方法与基类方法同名但参数列表不同的情况很少见，所以尽量也不要写。

****

#### 6.2继承的构造函数

>   上节提到，可以在派生类中使用 using 关键字显式地包含基类中定义的方法。
>
>   这适用于普通类方法，也适用于构造函数，允许在派生类中继承基类的构造函数。考虑下面的 Base 和 Derived 类定义：
>
>   ```c++
>   class Base
>   {
>    public:
>    	virtual ~Base() = default;
>    	Base() = default;
>    	Base(std::string_view str);
>   };
>   
>   class Derived : public Base
>   {
>    public:
>    	Derived(int i);
>   };
>   ```
>
>   对于 Base 类，只能用代码提供的 Base 构造函数创建 Base 对象，要么是默认构造函数，要么是包含 string_view 参数的构造函数。
>
>   对于 Derived 类，只能用代码提供的 Derived 构造函数创建 Derived 对象，这个构造函数需要一个整数作为参数。不能使用 Base 类中使用接收 string_view 的构造函数来创建 Derived 对象。例如：
>
>   ```c++
>   Base base("Hello");		// OK, calls string_view Base ctor
>   Derived derived(1);		// OK, calls integer Derived ctor
>   Derived derived2("Hello");	// Error, Derived does not ingert string_view ctor
>   ```
>
>   如果喜欢使用基于 string_view 的 Base 构造函数构建 Derived 对象，可以在 Derived 类中显式地继承 Base 构造函数，如下所示：
>
>   ```c++
>   class Derived : public Base
>   {
>    public:
>    	using Base::Base;
>    	Dereived(int i);
>   };
>   ```
>
>   using 语句从父类继承除默认构造函数以外的所有其他构造函数，现在可以通过下面的两种方法构建 Derived 对象：
>
>   ```c++
>   Derived derived1(1);	// OK, calls integer Derived ctor
>   Derived derived2("Hello");	// OK, calls inherited string_view Base ctor
>   ```
>
>   Derived 类定义的构造函数可与从 Base 类继承的构造函数有相同的参数列表。**与所有的重写一样，此时 Derived 类的构造函数的优先级高于继承的构造函数。**在下例中，Derived 类使用 using 关键字继承了 Base 类中除默认构造函数外的其他所有构造函数。**然而，由于 Derived 类定义了一个使用浮点数作为参数的构造函数，从 Base 类继承的使用浮点数作为参数的构造函数被重写。**
>
>   ```c++
>   class Base
>   {
>    pubilc:
>    	virtual ~Base() = default;
>    	Base() = default;
>    	Base(std::string_view str);
>    	Base(float f);
>   };
>   
>   class Derived : public Base
>   {
>    public:
>    	using Base::Base;
>    	Derived(float f);	// Overrides inherited float Base ctor
>   };
>   ```
>
>   根据这个定义，可以用下面的代码创建 Derived 对象：
>
>   ```c++
>   Derived derived1("Hello");	// OK, calls inherited string_view Base ctor
>   Derived derived2(1.23f);	// OK, calls float Derived ctor
>   ```
>
>   使用 using 子句从基类继承构造函数有一些限制。
>
>   当从基类继承构造函数时，会继承除默认构造函数外的其他全部构造函数，不能只是继承基类构造函数的一个子集。
>
>   第二个限制与多重继承有关，如果一个基类的某个构造函数与另一个基类的构造函数具有相同的参数列表，就不可能从基类继承构造函数，因为那样会导致歧义，下面用例子说明：
>
>   ```c++
>   class Base1
>   {
>    public:
>    	virtual ~Base1() = default;
>    	Base1() = default;
>    	Base1(float f);
>   };
>   
>   class Base2
>   {
>    public:
>    	virtual ~Base2() = default;
>    	Base2() = default;
>    	Base2(std::string_view str);
>    	Base2(float f);
>   };
>   
>   class Derived : public Base1, public Base2
>   {
>    public:
>    	// 希望从两个基类中继承除默认构造函数外的所有构造函数
>    	using Base1::Base1;
>    	using Base2::Base2;
>    	Derived(char c);
>   };
>   ```
>
>   然而上面的代码存在歧义：
>
>   -   Derived 类定义的第一条 using 语句继承了 Base1 类的构造函数。这意味着 Derived 类具有如下构造函数：
>
>       ```c++
>       Derived(float f);	// Inherited from Base1
>       ```
>
>   -   Derived 类定义的第二条 using 语句试图继承 Base2 类的构造函数。这意味着如果它将试图继承如下构造函数：
>
>       ```c++
>       Derived(std::string_view str);
>       Derived(float f);
>       ```
>
>       显然，这将造成 Derived 类拥有第二个 Derived(float f) 构造函数，造成定义歧义。
>
>   **现在，可通过在 Derived 类中显式声明冲突的构造函数，来解决这种歧义。**如下所示：
>
>   ```c++
>   class Derived : public Base1, public Base2
>   {
>   public:
>   	using Base1::Base1;
>   	using Base2::Base2;
>   	Derived(float f);
>   	Derived(char c);
>   }
>   ```
>
>   **歧义消失原因：**
>
>   -   **当 `Derived` 接受一个 `float` 类型参数时，它会优先使用你显式定义的 `Derived(float f)` 构造函数，而不会再尝试使用基类的 `float` 构造函数。**
>   -   **因为 `Derived(float f)` 是一个自定义的构造函数，编译器知道该调用它，因此歧义被消除了。**
>
>   如果愿意，在 Derived 类中显式声明的使用浮点数作为参数的构造函数仍然可以在 ctor-initializer 中调用 Base1 和 Base2 构造函数，如下所示：
>
>   ```c++
>   Derived::Derived(float f) : Base1(f), Base2(f) {}
>   ```
>
>   当使用继承的构造函数时，要确保所有成员变量都正确地初始化。例如，考虑下面 Base 和 Derived 类的新定义。
>
>   ```c++
>   class Base
>   {
>   public:
>   	virtual ~Base() = default;
>   	Base(std::string_view str) : mStr(str) {}
>       
>   private:
>   	std::string mStr;
>   };
>   
>   class Derived : public Base
>   {
>   public:
>   	using Base::Base;
>   	Derived(int i) : Base(""), mInt(i) {}
>       
>   private:
>   	int mInt;
>   };
>   ```
>
>   可采用如下方法创建一个 Derived 对象：
>
>   ```c++
>   Derived s1(2);
>   ```
>
>   这条语句将调用 Derived(int i) 构造初始函数，这个构造函数将初始化 Derived 类的 mInt 数据成员，并调用 Base 构造函数，用空字符串初始化 mStr 数据成员。
>
>   由于 Derived 类继承了 Base 构造函数，还可以按下面的方式创建一个 Derived 对象：
>
>   ```c++
>   Derived s2("Hello World");
>   ```
>
>   这个示例没有正确地初始化 mInt 数据成员，在任何情况下这都是一个严重错误。这条语句调用从 Base 类继承的构造函数。然而，从 Base 类继承的构造函数只初始化了 Base 类的 mStr 成员变量，而没有初始化 Derived 类的 mInt 成员变量，它处于未初始化状态，这很危险，通常不建议这样做。
>
>   **解决方法：**
>
>   **使用类内成员初始化器来解决继承基类后派生类的成岩变量未初始化问题。**在第 8 章已经讨论过这个特性了。以下代码使用类内成员初始化器将 mInt 初始化为 0。Derived(int i) 构造函数仍可修改这一初始化行为，将 mInt 初始化为参数 i 的值：
>
>   ```c++
>   class Derived : public Base
>   {
>   public:
>   	using Base::Base;
>   	Derived(int i) : Base(""), mInt(i) {}
>       	
>   private:
>   	int mInt = 0;
>   };
>   ```

****

#### 6.3重写方法时的特征情况

>   当重写方法时，需要注意几种特殊情况，本节将列出可能遇到的一切情况。

##### 1.静态基类方法

>   **在 C++ 中，不能重写静态方法。**
>
>   **为什么静态方法要设计为不能够被重写？**
>
>   -   **与类关联，不与对象关联**：静态方法是与类相关联的，而不是与类的某个具体对象相关联。换句话说，静态方法是属于类本身的，而不是某个特定的实例。因此，静态方法在调用时是通过类名直接调用的，而不是通过对象来调用的；而类普通方法，则是在描述特定对象的特性：
>
>       ```C++
>       cppCopy codeclass Base
>       {
>       	public:
>       		static void staticMethod() { /*...*/ }
>       };
>       
>       // 调用方式
>       Base::staticMethod();  // 使用类名调用
>       ```
>
>       静态方法不依赖类的实例（对象），所以它不能访问非静态成员变量或调用非静态成员函数。
>
>   -   **没有多态性，没有虚函数表支持**：静态方法与多态性无关。C++中的多态性（polymorphism）是通过**虚函数表（vtable）**和对象的类型来实现的，而静态方法既不依赖对象，也不会在虚函数表中注册，因此没有虚拟函数的动态调度机制。
>
>   -   **非动态绑定，与类绑定，而非对象实例**：重写（override）发生在类的派生（继承）中，是一个子类**替换**父类的虚函数实现的过程。重写的关键是**动态绑定**，也就是在运行时根据对象的实际类型决定调用哪个类的函数。但静态方法由于不依赖对象，而是与类关联，因此不涉及动态绑定，所有的静态方法调用都是**编译时决定的**（静态绑定），它们在编译时已经确定从哪个类中调用哪个静态方法。

##### 动态绑定与静态绑定：

>   | **特性**     | **静态绑定（Static Binding）**                             | **动态绑定（Dynamic Binding）**  |
>   | ------------ | ---------------------------------------------------------- | -------------------------------- |
>   | **绑定时机** | 编译时                                                     | 运行时                           |
>   | **作用对象** | 非虚函数、静态方法、私有方法(无法被派生类重写)、全局函数等 | 虚函数                           |
>   | **效率**     | 高效，不需要运行时开销                                     | 需要虚函数表，性能略低           |
>   | **多态支持** | 不支持                                                     | 支持                             |
>   | **调用依据** | 静态类型（编译时的类型）                                   | 动态类型（运行时的实际对象类型） |
>
>   动态绑定是实现**运行时多态**的关键，它使得程序可以在运行时灵活地选择具体调用哪个派生类的方法。静态绑定则提高了性能，但无法实现多态。

##### 虚表

>   虚表（**vtable**）是用来实现**动态绑定**和**运行时多态**的关键机制。它允许程序在运行时通过基类指针或引用调用派生类的函数。了解虚表的工作原理可以帮助我们理解C++中的虚函数是如何被实现的。
>
>   虚表（vtable）通过在对象中存储一个虚表指针（vptr）来实现**动态绑定**和**多态**。
>
>   在编译时，编译器为每个包含虚函数的类生成虚表，并在运行时通过 `vptr` 查找和调用虚函数。虚表机制的引入使得 C++ 支持了多态性，同时通过虚函数表实现了高效的运行时方法解析。

###### 虚表（vtable）是什么

>   虚表（vtable，**virtual table**）是一个表（数组），存储着类的**虚函数指针**。每个包含虚函数的类都有自己的虚表，每个对象通过一个指针（通常称为**虚表指针**或 **vptr**）指向这个虚表。
>
>   **虚表**是一个类级别的机制，包含该类所有虚函数的指针。每个定义了虚函数的类都会有一张虚表。
>
>   虚表的每个条目指向对应虚函数的地址，派生类的虚表可以覆盖基类的虚函数条目，指向重载后的实现。

###### 虚表结构的基本要点：

>   1.  **vtable** 是一个指针数组，每个元素都是一个虚函数的地址。
>   2.  **vptr** 是存储在对象中的一个隐藏指针，指向这个对象所属类的 vtable。
>   3.  每个类有一个唯一的虚表，派生类的虚表会覆盖基类虚表中的虚函数地址。

###### 虚表的作用：

>   -   **动态绑定**：在运行时，通过 `vptr` 确定对象的实际类型，并通过虚表调用对应的虚函数。

###### 虚表的构建与工作流程

>   当我们在 C++ 类中使用虚函数时，编译器自动为类生成虚表，并在对象实例化时设置虚表指针。虚表的创建和初始化在编译期发生，而虚函数的调用则在运行时通过虚表完成。
>
>   1. **编译期工作**
>
>   在编译过程中，编译器会为每个包含虚函数的类生成一张虚表。这张虚表包含该类所有虚函数的地址。虚表的构建依赖于类的继承结构：
>
>   -   **基类**：对于一个包含虚函数的基类，编译器会为其生成一个虚表，虚表中存储着基类的虚函数地址。
>   -   **派生类**：如果派生类重写了基类的虚函数，编译器会为派生类生成一个新的虚表，其中重写的函数将替代基类虚表中的相应函数地址。
>
>   当编译器遇到虚函数时，它不会直接将调用的目标函数硬编码，而是通过对象的 `vptr` 查找对应的函数地址。每个包含虚函数的类在编译过程中都有以下步骤：
>
>   -   生成虚表，记录所有虚函数的地址。
>   -   为每个类的对象生成 `vptr`，并在构造函数中设置 `vptr` 指向该对象所属类的虚表。
>
>   2. **运行期工作**
>
>   在运行时，当你调用一个虚函数时，实际发生的过程如下：
>
>   1.  对象的 `vptr` 指向它所属类的虚表。
>   2.  调用虚函数时，程序首先通过 `vptr` 查找虚表，然后根据虚表中的函数指针调用实际的函数。
>   3.  如果是通过基类指针调用虚函数，程序会通过指针的 `vptr` 查找到派生类的虚表，并调用派生类重写的虚函数。
>
>   **代码示例：**
>
>   ```c++
>   #include <iostream>
>   using namespace std;
>   
>   class Base
>   {
>   public:
>   	virtual void show()
>   	{
>   		cout << "Base show()" << endl;
>   	}
>   };
>   
>   class Derived : public Base
>   {
>   public:
>   	void show() override
>   	{
>   		cout << "Derived show()" << endl;
>   	}
>   };
>   
>   int main()
>   {
>   	Base* bptr;
>   	Derived d;
>   	bptr = &d;
>   	bptr->show();  // 动态绑定，调用 Derived::show()
>   	return 0;
>   }
>   ```
>
>   在上面的代码中，`bptr` 是 `Base*` 类型的指针，但它指向一个 `Derived` 类型的对象。调用 `bptr->show()` 时，会通过 `vptr` 指向 `Derived` 类的虚表，并调用 `Derived` 类的 `show()` 方法。这就是虚表在实现动态绑定中的作用。

###### 虚表的内部结构和实现细节

>   **虚表指针（vptr）**：每个包含虚函数的类的对象都有一个隐藏的成员变量 `vptr`，指向该对象所属类的虚表。`vptr` 的初始化发生在类的构造函数中，通常在对象构造时，编译器会将 `vptr` 设置为指向该对象所属类的虚表。每个对象只有一个 `vptr`，即使该类有多个虚函数。
>
>   **虚表的内容**：虚表通常是一个包含函数指针的数组。每个虚函数都会有一个相应的入口，在运行时通过 `vptr` 来进行查找和调用。例如，如果派生类重写了基类的虚函数，派生类的虚表中的对应位置会包含派生类的函数地址，而基类的虚表仍然包含基类函数的地址。
>
>   **虚表示意图**：
>
>   ```
>   sqlCopy codeBase vtable:          Derived vtable:
>   +-----------------+   +--------------------+
>   | &Base::show     |   | &Derived::show     | <- Derived 类重写了 Base::show
>   +-----------------+   +--------------------+
>   ```
>
>   **继承和虚表**：派生类会继承基类的虚表结构，但当派生类重写基类的虚函数时，派生类的虚表中相应的虚函数指针会指向派生类的重写方法。这意味着，当通过基类指针或引用调用虚函数时，如果对象实际是派生类的实例，调用的会是派生类的实现。

###### 编译器如何处理虚表

>   **虚表的生成**：在编译期，编译器为每个包含虚函数的类创建一个虚表，记录类的所有虚函数的地址。这个过程是编译器的工作，程序员不需要显式编写任何代码。
>
>   **对象的构造和 `vptr` 初始化**：在类的构造函数中，编译器会插入代码来初始化 `vptr`。每次创建对象时，`vptr` 被初始化为指向对象所属类的虚表。
>
>   **虚函数调用**：在编译时，虚函数的调用被编译器生成一系列间接调用的代码。虚函数的调用不再是直接的函数调用，而是先通过 `vptr` 查找虚表中的相应虚函数指针，再调用指针指向的函数。

###### 运行时如何通过虚表调用虚函数

>   **对象包含 `vptr`**：每个对象在内存中包含一个 `vptr`，它指向对象所属类的虚表。派生类对象的 `vptr` 指向派生类的虚表，而基类对象的 `vptr` 指向基类的虚表。
>
>   **调用过程**：
>
>   1.  当一个虚函数被调用时，程序通过对象的 `vptr` 找到虚表。
>   2.  然后根据函数的位置（通常是通过函数在类中的声明顺序）从虚表中取出函数指针。
>   3.  最终，程序调用这个函数指针指向的函数。

>   对于多数情况，只需要知道这些就足够了。

>   **然而，在此我们需要了解一些推论：**
>
>   **方法不可能既是静态的，又是虚的。**
>
>   处于这个原因，试图重写一个静态方法并不能得到预期的结果；如果派生类中存在的静态方法与基类中的静态方法同名，这是实际上是两个独立的方法。
>
>   下面的代码显示了两个类，这两个类都有一个名为 beStatic() 的静态方法。这两个方法毫无关系(它们各自建立的是各自类的与类相关的行为，而不是与某个特定对象相关的行为)：
>
>   ```c++
>   class BaseStatic
>   {
>    public:
>    	static void beStatic()
>    	{
>    		cout << "BaseStatic being static." << endl;
>    	}
>   };
>   
>   class Derived : public BaseStatic
>   {
>    public:
>    	static void beStatic()
>    	{
>    		cout << "DerivedStatic keepin' it static." << endl;
>    		// keepin' 是 keeping 的缩写
>    	}
>   };
>   ```
>
>   由于静态方法属于类，调用两个类的同名方法时，将调用各自的方法：
>
>   ```c++
>   BaseStatic::beStatic();
>   DerivedStatic::beStatic();
>   ```
>
>   输出为：
>
>   ```c++
>   BaseStatic being static.
>   DerivedStatic keepin' it static.
>   ```
>
>   用类名访问这些方法时一切都很正常，当涉及对象时，这一行为就不是那么明显。
>
>   在 C++ 中，可使用对象调用静态方法，但由于方法此时是静态的，因此没有 this 指针，也无法访问对象本身，使用对象调用静态方法，等价于使用 classname::method() 调用静态方法。
>
>   回到前面的示例，可以编写如下代码，但结果很令人震惊：
>
>   ```c++
>   DervedStatic myDerivedStatic;
>   BaseStatic& ref = myDerivedStatic;
>   myDerivedStatic.beStatic();
>   ref.beStatic();
>   ```
>
>   返回结果为：
>
>   ```c++
>   DerivedStatic keepin' it static.
>   BaseStatic being static.
>   ```
>
>   首先，很明显 beStatic() 的第一次调用是调用了 DerivedStaric 版本，因为调用它的对象被显式地声明为 DerivedStatic 对象；其次，第二次调用的运行方式，可能会并非原本预期的样子 —— 这个对象是一个 BaseStatic 引用，但指向的是一个 DerivedStatic 对象，在此情况下，会调用 BaseStatic 版本的 beStatic()。原因是当调用这个静态方法时，是以 BaseStatic 的引用作为开始的，也就是说，BaseStatic 类是它的 **“初始类型”**，然后如果是普通的对象方法，可以通过 **动态绑定** 进行 **“多态的实现”**，然而，这里是静态方法，它是和 BaseStatic 类 **静态绑定** 的，因此仍然会返回的是调用 BaseStatic 版本的 beStatic()。
>
>   **注意：**
>
>   静态方法属于定义它的类，而不属于特定的对象。当类中的方法调用静态方法时，所调用的版本时通过正常的名称解析来决定的。当你使用一个**对象**去调用**静态方法**时，虽然语法上看起来像是通过对象在调用该方法，但实际上对象并**不真正参与**到这个调用过程中。静态方法属于类本身，而不是某个具体的对象。因此，编译器并不会根据对象的类型来动态决定调用哪个类的静态方法，而是基于编译时的静态类型决定调用哪个类的静态方法。

##### 重载基类方法

>   当指定名称和一组参数以重写某个方法时，编译器隐式地隐藏基类中同名方法中的所有其他实例。
>
>   这样设计 C++ 的逻辑在于：如果重写了给定名称的某个方法，可能是想重写所有的同名方法，但是可能会忘记把所有的同名方法都重写，为了防止部分重写，部分没有重写的问题，处于防御性编程，应当将这种情况作为错误处理。所以，直接将基类中同名方法隐式地隐藏了，这样做的最根本的目的在于消除歧义。
>
>   **函数重载**、**函数重写**和**名称隐藏**的机制是基于**函数名称**而不是参数签名(参数列表和返回值)、访问说明符的。
>
>   考虑这个问题：为什么要修改方法的某些版本而不修改其他版本呢？下面的例子中，Derived 类重写了一个方法，而没有重写相关的 **同级重载方法**：
>
>   ```c++
>   class Base
>   {
>    public:
>    	virtual ~Base() = default;
>    	virtual void overload()
>    	{
>    		cout << "Base's overload()" << endl;
>    	}
>    	virtual void overload(int i)
>    	{
>    		cout << "Base's overload(int i)" << endl;
>    	}
>   };
>   
>   class Derived : public Base
>   {
>    public:
>    	// 只重写 overlaod()，这时，编译器将自动隐式地隐藏基类中的 其余版本的 同名函数。
>    	virtual void overload() override
>    	{
>    		cout << "Derived's overload()" << endl;
>    	}
>   };
>   ```
>
>   如果试图用 Derived 对象调用以 int 值作为参数的 overload()，代码将无法编译，因为没有显式地重写这个方法。
>
>   ```c++
>   Derived myDerived;
>   myDerived.overload(2);	// Error! No matching method for overload(int).
>   ```
>
>   然而，使用 Derived 对象访问该版本的方法是可行的。只需要使用指向 Base 对象的指针或引用：
>
>   ```c++
>   Derived myDerived;
>   Base& ref = myDerived;
>   ref.overload(7);
>   ```
>
>   在 C++ 中，隐藏未实现的重载方法只是表象。显式声明为子类型实例的对象无法使用这些方法，但可将其转换为基类类型，以使用这些方法。
>
>   如果只想改变一个方法，可以使用 using 关键词避免重载该方法的所有版本(这点在上面的构造函数中有所体现)。在下面的代码中，Derived 类定义中使用了从 Base 类继承一个 overload() 版本，并显式地重写了另一个版本：
>
>   ```c++
>   class Base
>   {
>    public:
>    	virtual ~Base() = default;
>    	virtual void overload()
>    	{
>    		cout << "Base's overload()" << endl;
>    	}
>    	virtual void overload(int i)
>    	{
>    		cout << "Base's overload(int i)" << endl;
>    	}
>   };
>   
>   class Derived : public Base
>   {
>    public:
>    	using Base::overload;
>    	virtual void overload() override
>    	{
>    		cout << "Derived's overload()" << endl;
>    	}
>   };
>   ```
>
>   **但是，using 子句存在一定风险。**假定在 Base 类中添加了第三个 overload() 方法，本来应该在 Derived 类中重写这个方法。但是由于使用了 using 子句，在派生类中没有重写这个方法不会被当作错误，因为 Derived 类已经显式地说明 **“我将接受父类其他所有的重载方法。”**
>
>   就是说，我在基类里加了这个在派生类中使用了 using 子句的一个新的重载方法，本来应该在派生类中也进行重写这个重载方法，但是容易被遗忘这个重载方法的重写，会产生不符合预期的行为，存在潜在的维护风险。

##### 3.private 或 protected 基类方法

>   重写 private 或 protected 方法当然没有问题。
>
>   但要记住，方法的访问说明符会判断谁可以调用这些方法。
>
>   派生类无法调用父类的 private 方法，并不意味着无法重写这个方法。实际上，在 C++ 中，重写 private 或 protected 方法是一种常见模式。这种模式允许派生类定义自己的 **“独特性”**，在基类中会引用这种独特性。注意， Java 和 C# 仅允许重写 public 和 protected 方法，不能重写 private 方法。
>
>   例如，下面的类是汽车模拟程序的一部分，根据汽油消耗量和剩余燃料计算汽车可行使的里程：
>
>   ```c++
>   class MilesEstimator
>   {
>    public:
>    	virtual ~MilesEstimator() = default;
>       
>    	virtual int getMilesLeft() const;
>       
>    	virtual void setGallonsLeft(int gallons);
>    	virtual int getGallonsLeft() const;
>       
>    private:
>    	int mGallonsLeft;
>    	virtual int getMilesPerGallon() const;
>   };
>   ```
>
>   这些方法的实现如下所示：
>
>   ```c++
>   int MilesEstimator::getMilesLeft() const
>   {
>    	return getMilesPerGallon() * getGallonsLeft();
>   }
>   
>   void MilesEstimator::setGallonsLest(int gallons)
>   {
>    	mGallonsLeft = gallons;
>   }
>   
>   int MilesEstimator::getGallonsLeft() const
>   {
>    	return mGallonsLeft;
>   }
>   
>   int MilesEstimator::getMilesPerGallon() const
>   {
>    	return 20;
>   }
>   ```
>
>   getMilesLeft() 方法根据两个方法的返回结果执行计算。下面的代码使用 MilesEstimator 计算两加仑汽油可以行使的里程：
>
>   ```c++
>   MilesEstimator myMilesEstimator;
>   myMilesEstimator.setGallonsLeft(2);
>   cout << "Normal estimator can go " << myMilesEstimator.getMileLeft() << " more miles." << endl;
>   ```
>
>   代码的输出如下：
>
>   ```c++
>   Normal estimator can go 40 more miles.
>   ```
>
>   为让这个模型程序更有趣，可以引入不同类型的车辆，或许是效率更高的汽车。现有的 MilesEstimator 假定所有的汽车燃烧一加仑的汽油可以跑 20 公里，这个值是从一个单独的方法返回的，因此派生类可以重写这个方法。下面就是这样一个派生类：
>
>   ```c++
>   class EfficientCarMilesEstimator : public MilesEstimator
>   {
>    private:
>    	// const 和 override 在 C++ 中可以互换位置，编译器会正确解析这两个关键字的含义。
>    	virtual int getMilesPerGallon() const override;
>   }
>   ```
>
>   实现代码如下：
>
>   ```c++
>   int EfficientCarMilesEstimator::getMilesPerGallon() const
>   {
>    	return 35;
>   }
>   ```
>
>   通过重写这个 private 方法，新类完全修改了没有更改的现有 public 方法的行为。基类中的 getMilesLeft() 方法将自动调用 private getMilesPerGallon() 方法的重写版本。下面是一个使用新类的实例：
>
>   ```c++
>   EfficientCarMilesEstimator myEstimator;
>   myEstimator.setGallonsLeft(2);
>   cout << "Efficient estimator can go " << myEstimator.getMilesLeft() << " more miles." << endl;
>   ```
>
>   此时的输出表明了重写的功能：
>
>   ```c++
>   Efficient estimator can go 70 more miles.
>   ```
>
>   **注意：**
>
>   **重写 private 或 protected 方法可以在不用重大改动的情况下改变类的某些特性。**

##### 4.基类方法具有默认参数

>   **派生类与基类可具有不同的默认参数，但使用的参数取决于声明的变量类型，而不是底层对象。**下面一个简单的派生类示例，派生类在重写的方法中提供了不同的默认参数：
>
>   ```c++
>   class Base
>   {
>    public:
>    	virtual ~Base() = default;
>    	virtual void go(int i = 2)
>    	{
>    		cout << "Base's go with i = " << i << endl;
>    	}
>   };
>   
>   class Derived : public Base
>   {
>    public:
>    	virtual void go(int i = 7) override
>    	{
>    		cout << "Derived's go with i = " << i << endl;
>    	}
>   };
>   ```
>
>   如果调用 Derived 对象的 go()，将执行 Derived 版本的 go()，默认参数为 7。如果调用 Base 对象的 go()，将执行 Base 版本的 go()，默认参数为 2.然而(虽然这样有些怪异)，但是如果实际执行 Derived 对象的 Base 指针或引用 调用 go() 方法，则将调用 Derived 版本的 go()，但是使用 Base 版本的默认参数 2，下面的例子显示这种行为：
>
>   ```c++
>   Base myBase;
>   Derived myDerived;
>   Base& myBaseReferenceToDerived = myDerived;
>   
>   myBase.go();
>   myDerived.go();
>   myBaseReferenceToDerived.go();
>   ```
>
>   代码的输出如下所示：
>
>   ```c++
>   Base's go with i = 2
>   Derived's go with i = 7
>   Derived's go wiht i = 2
>   ```
>
>   **产生这种行为的原因是 C++ 根据表达式的编译时类型(而非运行时类型)绑定默认参数。这一点有点像静态函数一样，是在编译时确定，而非运行时确定。**

##### 编译时确定与运行时确定

>   由于这里的相关概念太多，我这里总结如下：
>
>   | **概念**                      | **编译时确定**                                               | **运行时确定**                                               |
>   | ----------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
>   | **静态函数**                  | 静态函数与类绑定，而不与对象绑定，调用时不需要对象实例，编译时确定调用哪个函数。 | 无运行时动态行为，静态函数与对象无关。                       |
>   | **非虚函数**                  | 非虚函数根据表达式的**编译时类型**确定调用的函数，编译器直接选择静态类型的方法。 | 与运行时类型无关，编译时绑定，非虚函数不支持多态。           |
>   | **虚函数**                    | 编译时仅确定调用的是虚函数，但不确定具体版本。编译时通过虚函数表的指针进行初始化。 | 在运行时通过对象的**运行时类型**来确定具体调用的虚函数版本，多态性通过虚表实现。 |
>   | **默认参数**                  | 默认参数在编译时根据函数的**编译时类型**确定，即使调用虚函数，默认参数的值也是在编译时决定的。 | 与运行时类型无关，虚函数调用也不会改变默认参数的值。         |
>   | **模板实例化**                | 模板根据传入的模板参数，在编译时实例化为具体的类或函数。     | 模板实例化完全在编译时发生，运行时不涉及任何模板行为。       |
>   | **函数重载**                  | 函数重载解析在**编译时**根据参数的静态类型进行确定。         | 与运行时类型无关，函数重载不支持运行时的动态解析。           |
>   | **内联函数**                  | 内联函数的展开发生在编译时，编译器决定是否将函数展开为内联代码。 | 无运行时动态行为，内联决定仅在编译时进行。                   |
>   | **类型推导 (auto)**           | `auto` 关键字在编译时确定变量的具体类型，编译器会推导出该类型。 | 类型推导在编译时完成，运行时不再变化。                       |
>   | **类型转换**                  | 显式类型转换（如 `static_cast`）在编译时解析。               | 动态类型转换（如 `dynamic_cast`）在运行时解析，通过运行时类型判断转换是否合法。 |
>   | **类型信息 (typeid 和 RTTI)** | 编译时可以使用 `typeid` 提取静态类型信息，尤其在没有虚函数的情况下。 | `typeid` 和 RTTI（运行时类型识别）在运行时提供对象的实际类型信息，通常与虚函数一起工作。 |
>
>   ---
>

###### 详细说明

>   1. **静态函数**：
>
>      - **编译时确定**：静态函数属于类，不属于任何特定对象。在编译时，编译器根据类名解析函数调用，确定静态函数的绑定。
>
>      - **运行时确定**：静态函数与运行时的对象无关，因此不会依赖运行时类型。它们不参与多态。
>
>      - **示例说明**：
>
>          ```c++
>          #include <iostream>
>          using namespace std;
>                                   
>          class Base
>          {
>          public:
>          	static void staticFunction()
>          	{
>          		cout << "Base::staticFunction called" << endl;
>          	}
>          };
>                                   
>          class Derived : public Base
>          {
>          public:
>          	static void staticFunction()
>          	{
>          		cout << "Derived::staticFunction called" << endl;
>          	}
>          };
>                                   
>          int main()
>          {
>          	Derived::staticFunction();  // 编译时确定，调用 Derived 的静态函数
>          	Base::staticFunction();     // 编译时确定，调用 Base 的静态函数
>          	return 0;
>          }
>          ```
>
>   2. **非虚函数**：
>      - **编译时确定**：非虚函数根据对象的编译时类型确定，不管对象的运行时类型是什么，编译器在编译时就已经确定了要调用哪个函数。
>
>      - **运行时确定**：非虚函数不支持多态行为，因此运行时不会影响它们的解析。
>
>      - **示例说明**：
>
>          ```c++
>          #include <iostream>
>          using namespace std;
>                                                           
>          class Base
>          {
>          public:
>          	void nonVirtualFunction()
>          	{
>          		cout << "Base::nonVirtualFunction called" << endl;
>          	}
>          };
>                                                           
>          class Derived : public Base
>          {
>          public:
>          	void nonVirtualFunction()
>          	{
>          		cout << "Derived::nonVirtualFunction called" << endl;
>          	}
>          };
>                                                           
>          int main()
>          {
>          	Base* ptr = new Derived();
>          	ptr->nonVirtualFunction();  // 调用 Base 的非虚函数，编译时确定
>          	delete ptr;
>          	return 0;
>          }
>          ```
>
>   3. **虚函数**：
>      - **编译时确定**：编译器在编译时知道表达式是虚函数，但不会确定调用的是哪一个版本的实现。只会生成虚表指针访问的代码。
>
>      - **运行时确定**：通过虚表（vtable）和虚表指针（vptr），虚函数在运行时根据对象的实际类型动态解析，支持多态行为。
>
>      - **示例说明**：
>
>          ```c++
>          #include <iostream>
>          using namespace std;
>                                                           
>          class Base
>          {
>          public:
>          	virtual void virtualFunction()
>          	{
>          		cout << "Base::virtualFunction called" << endl;
>          	}
>          };
>                                                           
>          class Derived : public Base
>          {
>          public:
>          	void virtualFunction() override
>          	{
>          		cout << "Derived::virtualFunction called" << endl;
>          	}
>          };
>                                                           
>          int main()
>          {
>          	Base* ptr = new Derived();
>          	ptr->virtualFunction();  // 运行时确定，调用 Derived 的虚函数
>          	delete ptr;
>          	return 0;
>          }
>          ```
>
>   4. **默认参数**：
>      - **编译时确定**：默认参数是基于函数的编译时类型绑定的。如果你调用一个带有默认参数的函数，编译器在编译时就已经决定了使用的默认参数值。
>
>      - **运行时确定**：运行时不会改变默认参数的绑定，甚至在虚函数调用时，默认参数的值仍是基于编译时类型。
>
>      - **示例说明**：
>
>          ```c++
>          #include <iostream>
>          using namespace std;
>                                                           
>          class Base
>          {
>          public:
>          	virtual void print(int x = 10)
>          	{
>          		cout << "Base: " << x << endl;
>          	}
>          };
>                                                           
>          class Derived : public Base
>          {
>          public:
>          	void print(int x = 20) override
>          	{
>          		cout << "Derived: " << x << endl;
>          	}
>          };
>                                                           
>          int main()
>          {
>          	Base* ptr = new Derived();
>          	ptr->print();  // 调用 Derived 的虚函数，但默认参数取 Base 的值（10）
>          	delete ptr;
>          	return 0;
>          }
>          ```
>
>   5. **模板实例化**：
>      - **编译时确定**：模板在编译时根据传入的类型实例化，编译器生成特定的模板函数或类。模板的实例化完全是在编译时完成的。
>
>      - **运行时确定**：模板实例化后生成的代码在运行时是确定的，因此模板不具备运行时动态行为。
>
>      - **示例说明**：
>
>          ```c++
>          #include <iostream>
>          using namespace std;
>                                                           
>          template <typename T>
>          T add(T a, T b)
>          {
>          	return a + b;
>          }
>                                                           
>          int main()
>          {
>          	cout << add(5, 3) << endl;  // 编译时确定，生成 int add(int, int)
>          	cout << add(2.5, 3.1) << endl;  // 编译时确定，生成 double add(double, double)
>          	return 0;
>          }
>          ```
>
>   6. **函数重载**：
>      - **编译时确定**：编译器在编译时根据参数的编译时类型选择合适的重载函数，因此函数重载解析是编译时确定的。
>      - **运行时确定**：函数重载在运行时不会再发生变化，它是静态绑定的，不支持运行时的动态解析。
>      - 示例如下：
>
>      ```c++
>      #include <iostream>
>      using namespace std;
>                           
>      void print(int i) 
>      {
>      	cout << "Integer: " << i << endl;
>      }
>                           
>      void print(double d)
>      {
>      	cout << "Double: " << d << endl;
>      }
>                           
>      int main()
>      {
>      	print(5);      // 编译时确定调用 int 版本
>      	print(3.14);   // 编译时确定调用 double 版本
>      	return 0;
>      }
>      ```
>      
>   7. **内联函数**：
>
>      - **编译时确定**：内联函数的展开发生在编译时，编译器决定是否将函数体直接展开到调用处。内联性取决于编译器的决定，而非运行时的行为。
>
>      - **运行时确定**：内联函数在运行时没有任何动态行为，一旦编译器决定是否内联展开，就不会在运行时再发生变化。
>
>      - **示例说明**：
>
>          ```c++
>          #include <iostream>
>          using namespace std;
>                                   
>          inline void printInline()
>          {
>          	cout << "Inline function called" << endl;
>          }
>                                   
>          int main()
>          {
>          	printInline();  // 编译时决定是否展开为内联代码
>          	return 0;
>          }
>          ```
>
>   8. **类型推导 (auto)**：
>      - **编译时确定**：`auto` 是在编译时确定变量的类型，编译器推导出该类型并进行编译。推导完成后，类型信息在编译时就确定下来了。
>
>      - **运行时确定**：运行时不会对类型推导进行任何调整，`auto` 的类型一旦在编译时推导完成，运行时就不会发生变化。
>
>      - **示例说明**：
>
>          ```c++
>          #include <iostream>
>          using namespace std;
>                                                           
>          int main()
>          {
>          	auto x = 5;  // 编译时确定类型为 int
>          	auto y = 3.14;  // 编译时确定类型为 double
>                                                           
>          	cout << x << " " << y << endl;
>          	return 0;
>          }
>          ```
>
>   9. **类型转换**：
>      - **编译时确定**：`static_cast` 等显式类型转换在编译时进行类型检查和转换。编译器根据类型信息进行转换，不涉及运行时判断。
>
>      - **运行时确定**：`dynamic_cast` 用于运行时类型检查，特别是在多态体系中，编译时不确定转换是否合法，需要在运行时判断。如果转换失败，`dynamic_cast` 会返回 `nullptr`（指针）或抛出异常（引用）。
>
>      - **示例说明**：
>
>          ```c++
>          #include <iostream>
>          using namespace std;
>                                                           
>          class Base
>          {
>          	virtual void dummy() {}  // 必须有虚函数才能使用 dynamic_cast
>          };
>                                                           
>          class Derived : public Base {};
>                                                           
>          int main()
>          {
>          	Base* basePtr = new Derived();
>          	Derived* derivedPtr = dynamic_cast<Derived*>(basePtr);  // 运行时确定
>                                                           
>          	if (derivedPtr)
>          	{
>          		cout << "Successful cast" << endl;
>          	}
>          	else
>          	{
>          		cout << "Failed cast" << endl;
>          	}
>                                                           
>          	delete basePtr;
>          	return 0;
>          }
>          ```
>
>   10. **类型信息 (typeid 和 RTTI)**：
>       - **编译时确定**：在不涉及虚函数的情况下，`typeid` 可以提取对象的静态类型信息，编译时即能确定类型。
>
>       - **运行时确定**：在使用虚函数和多态时，`typeid` 会在运行时获取对象的实际类型，RTTI（运行时类型识别）是用于获取运行时的类型信息。
>
>       - **实例说明**：
>
>           ```c++
>           #include <iostream>
>           #include <typeinfo>
>           using namespace std;
>                                                                   
>           class Base
>           {
>           public:
>           	virtual ~Base() = default;
>           };
>                                                                   
>           class Derived : public Base {};
>                                                                   
>           int main()
>           {
>           	Base* basePtr = new Derived();
>                                                                   
>           	cout << "Type of basePtr: " << typeid(*basePtr).name() << endl;  // 运行时确定类型
>           	delete basePtr;
>           	return 0;
>           }
>           ```
>
>   ---
>

###### 实践中常见场景的应用

>   - **虚函数和默认参数**：在使用虚函数时，函数的具体实现取决于对象的运行时类型，而默认参数则总是基于编译时类型。
>     
>   - **模板与函数重载**：模板的实例化和函数重载的解析都是编译时确定的，因此编译器会在编译时生成代码并选择合适的函数调用版本。
>
>   - **类型推导 (auto)**：`auto` 在编译时推导出类型，因此开发者不需要明确指定类型，但其行为是编译时确定的，推导的类型一旦确定，在运行时不会再变化。
>
>   - **类型转换和 RTTI**：使用 `dynamic_cast` 时，只有在运行时才会进行类型检查，因此在多态环境中，转换操作可能在运行时失败。而 `static_cast` 则是编译时确定的，不会检查运行时的实际类型。
>
>   ---
>

###### 总结

>   在 C++ 中，理解**编译时确定**和**运行时确定**的逻辑对于掌握语言的核心特性至关重要。编译时的确定性依赖于类型系统、模板机制、函数重载等，而运行时的确定性则与多态性、虚函数以及运行时类型信息有关。在实践中，合理运用这些特性可以避免不必要的性能开销，并帮助设计出更加健壮的代码。

>   在 C++ 中，默认参数不会被 **“继承”**。如果上面的 Derived 类没有像父类那样提供父类那样提供默认参数，就用新的非 0 参数版本 go() 方法。
>
>   **注意：**
>
>   当重写具有默认参数的方法时，也应该提供默认参数，这个参数的值应该与基类模板相同。建议使用符号常量作为默认值，这样可在派生类中使用同一个符号常量。

##### 5.派生类方法具有不同的访问级别

>   可以采用两种方法来修改方法的访问级别 —— 可以加强限制，也可以放宽限制。在 C++ 中这两种方法的意义都不大，但是这么做还是有一定合理原因的。
>
>   温故一下，public、protected、private 三个访问修饰符：
>
>   -   **`public` 成员在任何地方都可以访问这些成员，包括类外部的代码。**基类的 `public` 成员在派生类中依然是 `public`，`protected` 成员在派生类中依然是 `protected`，而 `private` 成员依然不可访问。
>   -   **`protected` 成员只能在类的内部和派生类中访问。外部代码不能访问这些成员。**基类的 `public` 和 `protected` 成员在派生类中都变成了 `protected`，`private` 成员仍然不可访问。
>   -   **`private` 成员只能在类的内部访问，派生类和类外部都无法访问这些成员。**基类的 `public` 和 `protected` 成员在派生类中都变成了 `private`，`private` 成员依然不可访问。
>   -   **父类不能访问子类的 `protected` 或 `private` 成员。访问控制是单向的。**

###### 加强方法的访问限制

>   为了加强某个方法(或数据成员)的限制，有两个方法：
>
>   一种方法是修改整个基类的访问说明符，本章后面讲讲述这种方法。
>
>   另一种方法是在派生类中重新定义访问限制，下面的 Sky 类演示了这种方法：
>
>   ```c++
>   class Gregarious
>   {
>    public:
>    	virtual void talk()
>    	{
>    		cout << "Gregarious says hi!" << endl;
>    	}
>   };
>   
>   class Shy : public gregarious
>   {
>    protected:
>    	virtual void talk() override
>    	{
>    		cout << "Shy reluctantly says hello." << endl;
>    	}
>   };
>   ```
>
>   Shy 类中 protected 版本的 talk() 方法适当地重写 Gregarious::talk() 方法。任何客户代码试图使用 Shy 对象调用 talk() 都会导致编译错误。
>
>   ```c++
>   Shy myShy;
>   myShy.talk();	// Error! Attempt to access protected method.
>   ```
>
>   然而，这个方法并不是完全受保护的。可使用 Gregarious 引用或指针访问 protected 方法。
>
>   ```c++
>   Shy myShy;
>   Gregarious& ref = myShy;
>   ref.talk();
>   ```
>
>   上述代码的输出如下：
>
>   ```c++
>   Shy reluctantly says hello.
>   ```
>
>   这说明载派生类中将方法设为 protected 实际上是重写了这个方法(因为可以正确地调用)，此外还证明如果基类将方法设置为 public，就无法完整地强制访问 protected 方法(无法通过类本身直接访问，而非指针或引用的间接访问)。
>
>   **注意：**
>
>   **无法(也没有很好的理由)限制访问基类的 public 方法。**
>
>   **注意：**
>
>   **上例重新定义了派生类中的方法，因为它希望显示另一条消息。如果不希望修改实现，只想改变方法的访问级别，首选方法是在具有所需访问级别的派生类定义中添加 using 语句：**
>
>   ```c++
>   class Gregarious
>   {
>   public:
>    	virtual void talk()
>    	{
>    		cout << "Gregarious says hi!" << endl;
>    	}
>   };
>   
>   class Shy : public Gregarious
>   {
>   protected:
>    	using Gregarious::talk;  // 将基类中的 public 方法 talk 改为 protected
>   };
>   ```
>
>   **注意：**
>
>   **此外，在这里好像发现一个问题，这里好像破坏了我们上面的规定，即，父类不够访问子类的 `protected` 或 `private` 成员，其实不是这样的，产生这种理解错误的原因在于**：
>
>   -   **基类的引用类型**：在这段代码中，`Gregarious& ref = myShy;` 表示通过基类 `Gregarious` 的引用来引用一个 `Shy` 对象。尽管 `Shy::talk()` 是 `protected`，但 `Gregarious::talk()` 是 `public` 且是虚函数。
>   -   **虚函数的多态性**：当通过基类引用或指针调用 `talk()` 函数时，**编译器根据运行时的对象类型来决定实际调用哪个版本的函数**。在这种情况下，虽然 `Shy::talk()` 是 `protected` 的，但 `Gregarious::talk()` 是 `public` 的虚函数。在编译时，编译器根据引用类型（即 `Gregarious&`）允许调用 `talk()`。在运行时，通过多态性机制，调用的是派生类 `Shy` 的版本。
>   -   **访问控制规则**：C++ 的访问控制是基于**编译时类型**的，而不是**运行时类型**的。在编译时，`ref` 被视为 `Gregarious&`，所以可以合法调用 `Gregarious` 的 `public` 成员函数 `talk()`。尽管在 `Shy` 类中 `talk()` 是 `protected` 的，编译器允许通过基类的 `public` 接口来访问这个虚函数。
>   -   **根本原因在于：C++ 的访问控制是静态的，这意味着在编译时确定。编译器在检查访问权限时，基于引用或指针的类型（编译时类型），而不是运行时实际指向的对象类型。在编译时，`ref` 被视为一个 `Gregarious` 类型的引用，而在 `Gregarious` 中，`talk()` 是 `public` 的，所以可以合法调用它。**

###### 放宽访问限制

>   最简单的方法是提供一个 public 方法来调用基类的 protected 方法，如下所示：
>
>   ```c++
>   class Serect
>   {
>    protected:
>    	virtual void dontTell()
>    	{
>    		cout << "I'll never tell." << endl;
>    	}
>   };
>   
>   // Blabber，多嘴者、泄密者、胡说八道者
>   class Blabber : public Secrect
>   {
>    public:
>    	virtual void tell()
>    	{
>    		dontTell();
>    	}
>   };
>   ```
>
>   调用 Blabber 对象的 public 方法 tell() 的客户代码可有效地访问 Secret 类的 protected 方法。当然，这并未真正改变 dontTell 的访问级别，只是提供了这个方法的公共方式。
>
>   也可在 Blabber 派生类中显式地重写 dontTell()，并将这个方法设置为 public。这样做比拓宽访问级别更有意义，因为这样会：
>
>   -   **更加清晰明确**：它清楚地表明了派生类在访问权限上的改变。即使使用基类的指针或引用调用 `dontTell()` 方法时，行为也是一致的，且符合设计意图。
>   -   **保持多态性**：通过重写基类的虚函数并修改其访问级别，调用该方法时能够保留运行时多态的特性。
>
>   如下，假定 Blabber 类实际上将 dontTell() 方法设置为 public:
>
>   ```c++
>   class Blabber : public Secret
>   {
>   public:
>   	virtual void dontTell() override
>   	{
>   		cout << "I'll tell all!" << endl;
>   	}
>   };
>   ```
>
>   调用 Blabber 对象的 dontTell() 方法：
>
>   ```c++
>   myBlabber.dontTell();	// Outputs "I'll tell all!"
>   ```
>
>   如果不想更改重写方法的实现，只想更改访问级别，可使用 using 子句，例如：
>
>   ```c++
>   class Blabber : public Secret
>   {
>   public:
>   	using Secret::dontTell;
>   };
>   ```
>
>   这也允许调用 Blabber 对象的 dontTell() 方法，但这一次，输出将会是：
>
>   ```c++
>   myBlabber.dontTell();	// Outputs "I'll never tell."
>   ```
>
>   然而，在上述情况下，基类中的 protected 方法仍然是受保护的，因为使用 Secret 指针或引用调用 Secret 类的 dontTell() 方法将无法编译。
>
>   ```c++
>   Blabber myBlabber;
>   Secret& ref = myBlabber;
>   Secret* ptr = &myBlabber;
>   ref.dontTell();		// Error! Attempt to access protected method.
>   ptr->dontTell();	// Error! Attempt to access protected method.
>   ```
>
>   **注意：**
>
>   **修改方法访问级别的唯一真正有用的方法是对 protected 方法提供较宽松的访问限制。**

###### 总结提供宽松访问权限的方法：

>   -   **提供间接调用的 `public` 方法**（如 `tell()`）虽然能让外部代码访问 `protected` 方法，但并不清晰地表明该方法的访问级别已经被提升。
>   -   **显式重写并设置为 `public`** 更加清晰地展示了派生类对基类行为的改变，尤其在多态场景下（如通过基类指针或引用调用时）会更加直观。
>   -   **`using` 语句**是最简洁的方式，且不改变方法实现，仅改变访问权限。

****

#### 6.4派生类中的复制构造函数和赋值运算符

>   第 9 章讲过，在类中使用动态内存分配时，提供固执构造函数和赋值运算符是良好的编程习惯。当定义派生类时，必须注意复制构造函数和 operator=。
>
>   如果派生类没有任何需要使用的非默认复制构造函数或 operator= 的特殊数据(通常是指针)，无论基类是否具有这类数据，都不需要需要显式定义复制构造函数或 赋值运算符 (`operator=`)。派生类中的默认复制构造函数或 `operator=` 会自动调用基类的对应函数。基类负责管理它自己的成员，派生类无需显式处理基类的复制或赋值。派生类的数据成员由编译器生成的默认复制构造函数和 `operator=` 自动处理。
>
>   如果派生类省略了复制构造函数或 operator=，派生类中指定的数据成员就使用默认的复制构造函数或 operator=，基类中的数据成员使用基类的复制构造函数或 operator=。

>   下面分情况进行讨论：

##### 1.派生类没有特殊数据，基类也没有特殊数据

>   - **情况**：派生类 `Derived` 继承自基类 `Base`，两者都没有需要特殊管理的数据。
>   - **行为**：编译器自动生成的默认复制构造函数和赋值运算符适用于 `Derived` 和 `Base`。你不需要显式定义这些函数。
>
>   ```cpp
>   class Base
>   {
>   public:
>   	int data;
>   };
>   
>   class Derived : public Base
>   {
>   public:
>   	int moreData;
>   };
>   
>   Derived d1;
>   d1.data = 1;
>   d1.moreData = 2;
>   
>   Derived d2 = d1;    // 使用默认复制构造函数
>   d2 = d1;            // 使用默认赋值运算符
>   ```
>

##### 2. **派生类没有特殊数据，基类有需要特殊管理的数据（如指针）**

>   - **情况**：派生类 `Derived` 继承自基类 `Base`，基类有指针数据需要深拷贝。
>   - **行为**：基类定义了复制构造函数和赋值运算符来处理指针。派生类不需要自定义这些函数。
>
>   ```cpp
>   class Base
>   {
>   public:
>   	int* data;
>   
>   	Base() : data(new int(0)) {}
>   	Base(const Base& other) : data(new int(*other.data)) {}
>   	Base& operator=(const Base& other)
>   	{
>   		if (this != &other)
>   		{
>   			delete data;
>   			data = new int(*other.data);
>   		}
>   		return *this;
>   	}
>       
>   	~Base()
>   	{
>   		delete data;
>   	}
>   };
>   
>   class Derived : public Base
>   {
>   public:
>   	int moreData;
>   };
>   
>   Derived d1;
>   d1.data[0] = 10;
>   d1.moreData = 20;
>   
>   Derived d2 = d1;    // 使用基类的复制构造函数
>   d2 = d1;            // 使用基类的赋值运算符
>   ```
>

##### 3. **派生类有特殊数据，基类也有特殊数据**

>   - **情况**：派生类 `Derived` 继承自基类 `Base`，两者都有需要特殊管理的数据。
>   - **行为**：基类和派生类都需要定义自定义的复制构造函数和赋值运算符。
>
>   ```cpp
>   class Base
>   {
>   public:
>   	int* data;
>   
>   	Base() : data(new int(0)) {}
>   	Base(const Base& other) : data(new int(*other.data)) {}
>   	Base& operator=(const Base& other)
>   	{
>   		if (this != &other)
>   		{
>   			delete data;
>   			data = new int(*other.data);
>   		}
>   		return *this;
>   	}
>   	~Base() { delete data; }
>   };
>   
>   class Derived : public Base
>   {
>   public:
>   	int* moreData;
>   
>   	Derived() : moreData(new int(0)) {}
>   	Derived(const Derived& other) : Base(other), moreData(new int(*other.moreData)) {}
>   	Derived& operator=(const Derived& other)
>   	{
>   		if (this != &other)
>   		{
>   			Base::operator=(other);
>   			delete moreData;
>   			moreData = new int(*other.moreData);
>   		}
>   		return *this;
>   	}
>       
>   	~Derived()
>   	{
>   		delete moreData;
>   	}
>   };
>   
>   Derived d1;
>   *d1.data = 10;
>   *d1.moreData = 20;
>   
>   Derived d2 = d1;    // 使用自定义复制构造函数
>   d2 = d1;            // 使用自定义赋值运算符
>   ```
>

##### 4. **派生类有特殊数据，基类没有特殊数据**

>   - **情况**：派生类 `Derived` 有特殊数据（如指针），但基类 `Base` 只有简单的数据。
>   - **行为**：你需要在派生类中定义自定义的复制构造函数和赋值运算符来处理派生类的数据。基类的复制构造函数和赋值运算符由编译器生成。
>
>   ```cpp
>   class Base
>   {
>   public:
>   	int data;
>   };
>   
>   class Derived : public Base
>   {
>   public:
>   	int* moreData;
>   
>   	Derived() : moreData(new int(0)) {}
>   	Derived(const Derived& other) : Base(other), moreData(new int(*other.moreData)) {}
>   	Derived& operator=(const Derived& other)
>   	{
>   		if (this != &other)
>   		{
>   			Base::operator=(other);
>   			delete moreData;
>   			moreData = new int(*other.moreData);
>   		}
>   		return *this;
>   	}
>       
>   	~Derived()
>   	{
>   		delete moreData;
>   	}
>   };
>   
>   Derived d1;
>   *d1.moreData = 20;
>   
>   Derived d2 = d1;    // 使用自定义复制构造函数
>   d2 = d1;            // 使用自定义赋值运算符
>   ```
>

##### 总结：

>   | **情况**                                 | **基类的自定义复制构造函数和赋值运算符** | **派生类的自定义复制构造函数和赋值运算符** | **默认行为**                                           |
>   | ---------------------------------------- | ---------------------------------------- | ------------------------------------------ | ------------------------------------------------------ |
>   | **基类和派生类都没有特殊数据**           | 不需要                                   | 不需要                                     | 编译器生成的默认函数适用                               |
>   | **基类有特殊数据（如指针），派生类没有** | 需要                                     | 不需要                                     | 基类的自定义函数处理基类部分，派生类使用默认函数       |
>   | **基类和派生类都有特殊数据**             | 需要                                     | 需要                                       | 基类和派生类都需要自定义函数来处理各自的数据           |
>   | **基类没有特殊数据，派生类有**           | 不需要                                   | 需要                                       | 基类使用默认函数，派生类需要自定义函数处理派生类的数据 |
>
>   - **派生类没有特殊数据**：派生类可以依赖基类的复制构造函数和赋值运算符，即使基类有复杂的数据。
>   - **派生类有特殊数据**：派生类必须自定义复制构造函数和赋值运算符来处理这些特殊数据，而基类的部分由基类的函数处理。

##### 显式调用基类的复制构造函数

>   显式调用基类的复制构造函数的方法：
>
>   ```c++
>   class Base
>   {
>    public:
>    	virtual ~Base() = default;
>    	Base() = default;
>    	Base()(const Base& src);
>   };
>   
>   Base::Base(const Base& src)
>   {
>    	// 基类的复制构造函数，用于复制基类对象的成员
>   }
>   
>   class Derived : public Base
>   {
>    public:
>    	Derived() = default;
>    	Derived(const Derived& src);
>   };
>   
>   Derived::Derived(const Derived& src) : Base(src)
>   {
>    	// 复制构造函数中显式调用基类的复制构造函数
>   }
>   ```
>
>   如果你在派生类中编写了自己的**复制构造函数**，你必须**显式地调用基类的复制构造函数**，否则编译器会自动使用基类的**默认构造函数**，而不是基类的**复制构造函数**。这可能会导致基类部分没有被正确复制：
>
>   -   **不显式调用**基类的复制构造函数时，基类部分会使用**默认构造函数**，导致基类的成员没有被复制。
>   -   **显式调用**基类的复制构造函数时，基类的成员会被**正确复制**。

###### 1.**未**显式调用基类的复制构造函数：

>   ```c++
>   #include <iostream>
>   using namespace std;
>   
>   class Base
>   {
>    public:
>    	int data;
>    	Base() : data(0) {}  // 默认构造函数
>    	Base(const Base& src) : data(src.data) {}  // 复制构造函数
>   };
>   
>   class Derived : public Base
>   {
>    public:
>    	int moreData;
>    	Derived() : moreData(0) {}  // 默认构造函数
>    	Derived(const Derived& src) : moreData(src.moreData)  // 不显式调用 Base 的复制构造函数
>    	{
>    		// 基类的部分（data）会使用 Base 的默认构造函数
>    	}
>   };
>   
>   int main()
>   {
>    	Derived d1;
>    	d1.moreData = 100;
>    	d1.data = 50;
>   
>    	Derived d2 = d1;  // 复制 d1 到 d2
>   
>    	cout << "d2.moreData = " << d2.moreData << endl;  // 输出 100
>    	cout << "d2.data = " << d2.data << endl;          // 输出 0，因为调用了 Base 的默认构造函数
>    	return 0;
>   }
>   ```
>
>   **结果**：
>
>   ```c++
>   d2.moreData = 100
>   d2.data = 0
>   ```
>
>   **解释**：
>
>   由于 `Derived` 类没有显式调用基类 `Base` 的复制构造函数，`d2` 的 `data` 成员被重新初始化为 `0`（因为调用了 `Base` 的默认构造函数），而不是复制自 `d1`。

###### 2.显式调用基类的复制构造函数：

>   ```c++
>   #include <iostream>
>   using namespace std;
>   
>   class Base
>   {
>    public:
>    	int data;
>    	Base() : data(0) {}  // 默认构造函数
>    	Base(const Base& src) : data(src.data) {}  // 复制构造函数
>   };
>   
>   class Derived : public Base
>   {
>    public:
>    	int moreData;
>    	Derived() : moreData(0) {}  // 默认构造函数
>    	Derived(const Derived& src) : Base(src), moreData(src.moreData)  // 显式调用 Base 的复制构造函数
>    	{
>    		// 现在基类的部分（data）会被正确复制
>    	}
>   };
>   
>   int main()
>   {
>    	Derived d1;
>    	d1.moreData = 100;
>    	d1.data = 50;
>   
>    	Derived d2 = d1;  // 复制 d1 到 d2
>   
>    	cout << "d2.moreData = " << d2.moreData << endl;  // 输出 100
>    	cout << "d2.data = " << d2.data << endl;          // 输出 50，正确复制了 d1 的 data 成员
>    	return 0;
>   }
>   ```
>
>   **结果**：
>
>   ```c++
>   d2.moreData = 100
>   d2.data = 50
>   ```
>
>   **解释**：
>
>   这里 `Derived` 类的复制构造函数显式调用了 `Base` 的复制构造函数 (`Base(src)`)，所以 `d2` 的 `data` 成员被正确复制为 `50`，与 `d1` 相同。

##### 显式调用基类的 operator=

>   与此类似，如果派生类重写了operator=, 则几乎总是需要调用父类版本的operator=。唯一的例外是因为某些奇怪的原因，在赋值时只想给对象的一部分赋值。下面的代码显示了如何在派生类中调用父类的赋值运算符。 
>
>   ```c++
>   Derived& Derived::operator=(const Derived& rhs)
>   {
>   	if (&rhs == this)
>   	{
>   		return *this;
>   	}
>   
>   	Base::operator=(rhs);	// Calls parent's operator.
>   	// Do necessary assignments for derived class.
>   	return *this;
>   }
>   ```
>
>   **警告：**
>
>   **如果派生类不指定自己的复制构造函数或 operator=，基类的功能将继续运行。否则，将需要显式引用基类版本。**
>
>   **注意：**
>
>   **如果在继承层次结构中需要复制功能，专业 C++ 开发人员管用的做法是实现多态 clone() 方法，因为不能完全依靠标准复制构造函数和复制赋值运算符来满足需求，原因在于：**
>
>   **在 C++ 中，当你使用复制构造函数或复制赋值运算符来复制对象时，通常这些函数是在编译时决定的（静态绑定）。这意味着，如果你有一个基类指针指向一个派生类对象，调用基类的复制构造函数或复制赋值运算符时，编译器只会调用基类的版本，无法正确处理派生类的成员。这就会导致 "对象切片"（object slicing） 问题，也就是派生类的特有部分被切掉了，只剩下基类的部分。**
>
>   **为了避免这种问题，尤其是在涉及继承和多态（即在运行时根据对象的实际类型进行操作）时，专业的 C++ 开发人员通常会在基类中定义一个虚函数 `clone()`，并在派生类中进行重写。这个 `clone()` 方法允许基类指针或引用在运行时正确地复制对象，返回派生类对象的一个完整副本。**
>
>   **示例如下：**
>
>   假设有一个动物类 Animal 和它的派生类 Dog 和 Cat：
>
>   ```c++
>   class Animal
>   {
>   public:
>   	virtual ~Animal() {}
>   
>   	// 多态 clone 方法
>   	virtual Animal* clone() const = 0;
>   };
>   
>   class Dog : public Animal
>   {
>   public:
>   	Dog* clone() const override
>   	{
>   		return new Dog(*this);  // 返回当前 Dog 对象的复制品
>   	}
>   };
>   
>   class Cat : public Animal
>   {
>   public:
>   	Cat* clone() const override
>   	{
>   		return new Cat(*this);  // 返回当前 Cat 对象的复制品
>   	}
>   };
>   ```
>
>   在这个例子中，基类 `Animal` 中定义了一个纯虚函数 `clone()`，它要求所有派生类实现自己的 `clone()` 方法。在每个派生类中，`clone()` 方法返回一个派生类对象的**动态副本**。
>
>   ```c++
>   Animal* a1 = new Dog();
>   Animal* a2 = a1->clone();  // a2 是 Dog 对象的复制品
>   ```
>
>   在上面的代码中，尽管 `a1` 是一个 `Animal*`，它指向了一个 `Dog` 对象。当你调用 `clone()` 时，实际上返回的是 `Dog` 对象的复制品，而不是 `Animal` 对象。这是通过多态机制实现的。
>
>   **第 12 章将讨论多态 clone() 方法。**

****

#### 6.5运行时类型工具

>   相对于其他面向对象语言，C++ 以编译时为主。如前所述，重写方法是可行的，这是由于方法和实现之间的间隔，而不是由于对象又关于自身所属类的内建信息。
>
>   然而，在 C++ 中，有些特性提供了对象那个的运行时视角。这些特性通常归属于一个名为 **运行时类型信息(Run Time Type Information，RTTI)** 的特性集。RTTI 提供了许多有用的特性，用于判断对象所属的类。

##### RTTI 与 虚方法

>   RTTI（运行时类型信息）依赖于虚函数的存在，这是因为虚函数表（vtable）是 RTTI 功能的基础。要理解为什么 RTTI 需要虚函数，必须了解 C++ 对象模型中的虚函数表（vtable）和类型识别的底层机制。

###### 1. **虚函数表（vtable）和虚函数指针（vptr）**

>   当类中包含虚函数时，编译器会为该类生成一个**虚函数表（vtable）**。虚函数表是一个指向虚函数的指针数组，每个包含虚函数的类都拥有一个对应的 vtable，且每个对象都有一个隐藏的指针（称为 `vptr`，虚函数指针）指向这个虚函数表。
>
>   - **vtable（虚函数表）**：类的虚函数表中包含了所有虚函数的地址，用来实现动态绑定。当对象调用虚函数时，程序根据对象的 vtable 查找并调用实际的函数。
>     
>   - **vptr（虚函数指针）**：每个对象都有一个 vptr，指向它所属类的虚函数表。在对象构造时，编译器会将 vptr 初始化为指向正确的 vtable。
>
>   由于派生类可能会重写基类中的虚函数，每个派生类的虚函数表会有所不同。因此，通过 vptr，可以在运行时根据对象的实际类型找到对应的虚函数表，从而实现多态。
>

###### 2. **RTTI 是如何依赖虚函数表工作的？**

>   RTTI 的关键是动态类型识别，而动态类型识别必须基于对象的实际类型，而不仅仅是编译时的类型。C++ 的 RTTI 机制利用 vtable 来实现这一点。
>
>   - 当类包含虚函数时，编译器会在虚函数表的额外区域中存储类的类型信息（如类的 `type_info` 对象）。`typeid` 和 `dynamic_cast` 操作符都依赖于此信息。
>   - `dynamic_cast` 和 `typeid` 操作符在运行时使用对象的 vptr，查找到虚函数表，从中读取类型信息，从而确定对象的真实类型。
>
>   具体来说，C++ 标准中规定，当类包含虚函数时，编译器必须为每个类生成一个 `std::type_info` 对象（包含类的名称等信息），并将其与虚函数表关联。`typeid` 和 `dynamic_cast` 操作会通过对象的 vptr 定位到虚函数表，并从表中提取该 `std::type_info` 对象。
>

###### 3. **为什么没有虚函数就无法生成 RTTI？**

>   当类没有虚函数时，编译器不会为该类生成虚函数表和 vptr，因为不需要多态性（即动态绑定）。由于没有 vptr，编译器也不会为类生成运行时类型信息（RTTI）。这意味着在运行时无法通过指针或引用确定对象的真实类型。
>
>   - **没有虚函数时，编译器只知道静态类型**（编译时类型），无法通过运行时的机制来识别对象的实际类型。因此，`dynamic_cast` 和 `typeid` 在这种情况下无法工作，因为它们依赖于 vptr 和 vtable 中的类型信息。
>

###### 4. **底层实现的示例**

>   可以通过以下简化示例来看 RTTI 与虚函数的关系：
>
>   ```cpp
>   #include <iostream>
>   #include <typeinfo>
>   
>   class A
>   {
>   public:
>   	virtual void func() {}  // 虚函数，类 A 有虚函数表和类型信息
>   };
>   
>   class B : public A {};
>   
>   int main()
>   {
>   	A* a = new B();
>   	std::cout << typeid(*a).name() << std::endl;  // 输出 B，因为存在 RTTI
>   	return 0;
>   }
>   ```
>
>   在这个例子中：
>   - 当执行 `typeid(*a)` 时，程序会通过 `a` 的 vptr 指向虚函数表，从虚函数表中找到与 B 类对应的 `type_info` 对象，因此正确返回 `B` 类型。
>
>   如果去掉 `A` 中的虚函数，编译器将不会为 `A` 和 `B` 生成 vtable 和 vptr，也不会生成 RTTI 信息，因此 `typeid(*a)` 将只能返回编译时已知的 `A` 类型。

###### 5. **没有虚函数时的结果**

>   ```cpp
>   class A {};  // 没有虚函数，类 A 不会有 vtable
>   class B : public A {};
>   
>   int main()
>   {
>   	A* a = new B();
>   	std::cout << typeid(*a).name() << std::endl;  // 输出 A，因为没有 RTTI
>   	return 0;
>   }
>   ```
>
>   此时，`typeid(*a)` 只能输出 `A`，因为没有 vtable 和 RTTI 信息，程序无法在运行时判断 `a` 指向的是 `B` 类的对象。
>

###### 总结

>   - **虚函数表（vtable）和虚函数指针（vptr）** 是 RTTI 的基础。通过虚函数表，程序可以在运行时动态识别对象的真实类型。
>   - 当类有虚函数时，编译器会生成虚函数表，并在其中附加 RTTI 信息（如类的 `type_info`）。
>   - 没有虚函数的类没有 vtable，也没有 RTTI，因此无法通过 `dynamic_cast` 或 `typeid` 在运行时确定其实际类型。
>
>   RTTI 之所以依赖虚函数，是因为虚函数表提供了一个机制，使得在运行时可以通过 vptr 查找并获得对象的类型信息。而没有虚函数的类则没有这种动态查找的机制。
>
>   **注意：**
>
>   -   **小心过度使用虚函数**：虚函数非常有用，但要权衡性能开销。特别是在实时系统、嵌入式系统或性能关键的场合下，尽量减少不必要的虚函数调用。
>   -   **合理设计继承结构**：避免深层次的继承层次结构，尽量使用组合而不是继承，避免复杂的虚函数体系。
>   -   **使用 final 关键字优化**：C++11 引入了 `final` 关键字，告诉编译器类或虚函数不能被进一步派生或重载，允许编译器进行更多优化。

##### dynamic_cast()

>   其中一特性是本章前面说过的 dynamic_cast()，可在 OO(面向对象) 层面结构中进行安全的类型转换。本章前面讨论过这一点。如果使用类上的 gynamic_cast()，但没有虚表，即没有虚方法，将导致编译错误。

###### 面向对象层面的安全类型转换

>   在 C++ 中，当涉及到继承和多态时，**安全的类型转换** 至关重要。为了理解这一点，我们需要先了解一下概念：
>
>   -   **静态类型**：在编译时已经确定的类型。例如：
>
>       ```c++
>       Base* b = new Derived();
>       ```
>
>       这里的 b 的静态类型时 Base*，因为它是基类指针。
>
>   -   **动态类型**：在运行时对象的实际类型。例如，b 指向的是 Derived 类型的对象，所以 b 的动态类型是 Derived*。
>
>   在继承体系中，使用基类指针或引用可以指向派生类对象。这是多态的基础，但也带来了一些问题：**如何在运行时确定指针或引用指向的实际类型？**
>
>   现假设存在如下类结构：
>
>   ```c++
>   class Animal
>   {
>   public:
>   	virtual ~Animal() {}  // 使 Animal 成为多态类型
>   };
>   
>   class Dog : public Animal
>   {
>   public:
>   	void bark() {}
>   };
>   
>   class Cat : public Animal
>   {
>   public:
>   	void meow() {}
>   };
>   ```
>
>   如果我们拥有一个 Animal*，但是不知道它指向的是 Dog 还是 Cat，这时我们就需要一种安全的方法来确定它的动态类型，以便于调用派生类特有的成员函数，使用 dynamic_cast() 方法可以在运行时执行这种安全的类型转换。
>
>   ```c++
>   Animal* a = new Dog();
>   Dog* d = dynamic_cast<Dog*>(a);
>   if (d)
>   {
>   	d->bark();  // 安全地调用 Dog 类的函数
>   }
>   else
>   {
>   	// a 不是指向 Dog 的对象，转换失败
>   }
>   ```
>
>   在这个例子中，`dynamic_cast` 保证了类型转换的安全性，只有当 `a` 实际上是 `Dog` 类型时，转换才会成功。这避免了不安全的类型转换所带来的风险。
>
>   **那么为什么一定需要安全的类型转换？**
>
>   因为：C++ 中的强制类型转换（例如 `reinterpret_cast` 和 `static_cast`）在某些情况下是不安全的，因为它们不检查转换的合法性。如果类型不匹配，可能会导致未定义行为。`dynamic_cast` 通过在运行时检查类型信息，确保转换是合法的，并在失败时提供安全的处理方式（返回 `nullptr` 或抛出异常）。这对程序的健壮性和可靠性至关重要，尤其是在复杂的继承层次结构中。

##### typeid()

>   RTTI 的第二个特性是 typeid 运算符，这个运算符可在运行时查询对象，从而判别对象的类型。
>
>   大多数情况下，不应该使用 typeid，因为最好用虚方法处理基于对象类型运行的代码。
>
>   下面的代码使用了 typeid，根据对象的类型输出消息：
>
>   ```c++
>   #include <typeinfo>
>   
>   class Animal
>   {
>    public:
>    	virtual ~Ainmal() = default;
>   };
>   
>   class Dog : public Animal
>   {
>       
>   };
>   
>   class Bird : public Ainmal
>   {
>       
>   };
>   
>   void speak(const Animal& animal)
>   {
>    	if (typeid(animal) == typeid(Dog))
>    	{
>    		cout << "Woof!" << endl;
>    	}
>    	else if (typeid(animal) == typeid(Bird))
>    	{
>    		cout << "Chirp!" << endl;
>    	}
>   }
>   ```
>
>   一旦看到这样的代码，就应该立即考虑从虚方法的角度实现该功能。在此情况下，更好的实现是在 Animal 类中声明一个 speak() 虚方法。Dog 类和 Bird 类会分别重写输出："Woof!" 和 "Chirp!"。这种方式更适合面向对象程序，会将与对象有关的功能基于这些对象。
>
>   **警告：**
>
>   **类至少有一个虚方法，typeid 运算符才能正常运行。如果在没有虚方法的类上使用 dynamic_case()，会导致编译错误。typeid 运算符也会从实参中去除引用和 const 限定符。**
>
>   typeid 运算符的主要价值之一在于日志记录和调试。下面的代码将 typeid 用于日志记录。logObject() 函数将 “可记录” 对象作为参数。设计是这样的：任何可记录的对象都从 Loggable 类中继承，都支持 getLogMessage() 方法：
>
>   ```c++
>   class Loggage
>   {
>    public:
>    	virtual ~Loggable() = default;
>    	virtual std::string getLogMessage() const = 0;
>   };
>   
>   class Foo : public Loggable
>   {
>    public:
>    	std::string getLogMessage() const override;
>   };
>   
>   std::string Foo::getLogMessage() const
>   {
>    	return "Hello logger.";
>   }
>   
>   void logObject(const Loggable& loggableObject)
>   {
>    	cout << typeid(loggableObject).name() << ":";
>    	cout << loggableObject.getLogMessage() << endl;
>   }
>   ```
>
>   logObject() 函数首先将对象所属类的名称写道输出流，随后是日志信息。这样之后阅读日志时，就可以看出文件每一行涉及的对象。用 Foo 示例调用 logObject() 函数时，Mirosoft Visual C++ 2017 生成的输出如下所示：
>
>   ```c++
>   class Foo : Hello logger.
>   ```
>
>   可以看出，typeid 运算符返回的名称是 class Foo。但这个名称因编译器而异。例如，若用 GCC 编译相同的代码，输出将如下所示：
>
>   ```c++
>   3Foo : Hello logger.
>   ```
>
>   **注意：**
>
>   如果不是为了日志记录或调试而使用 typeid，应该考虑用虚方法替代 typeid。

****

#### 6.6非 public 继承

>   在前面的所有示例中，总是用 public 关键字列出父类。父类是否可以是 private 或 protected？实际上可以这样做，尽管两者并不像 public 那样普遍，但是如果没有为父类指定任何访问说明符，就会默认是类的 private 继承；结构体的 public 继承，详细说明如下：
>
>   -   **类（class）**：默认是 `private` 继承，如果没有显式指定 `public`、`protected` 或 `private`，则继承方式为 `private`。
>
>       ```c++
>       class Base
>       {
>       public:
>       	int pub;
>       };
>       
>       class Derived : Base
>       {  // 默认 private 继承
>       public:
>       	void func()
>       	{
>       		// pub = 10;  // 错误，pub 成为了 private
>       	}
>       };
>       ```
>
>   -   **结构体（struct）**：默认是 `public` 继承，如果没有显式指定 `public`、`protected` 或 `private`，则继承方式为 `public`。
>
>       ```c++
>       struct Base
>       {
>       	int pub;
>       };
>                                           
>       struct Derived : Base
>       {  // 默认 public 继承
>       	void func()
>       	{
>       		pub = 10;  // OK，仍然是 public
>       	}
>       };
>       ```

##### 滥用继承机制

>   将父类的关系声明为 protected, 意味着在派生类中，基类所有的 public 方法和数据成员都成为受保护的。与此类似，指定 private 继承意味着基类所有的 public、protected 方法和数据成员在派生类中都成为私有的。
>
>   一些程序员可能会过度使用这种方式，将类的内部结构与继承层次复杂化，以解决设计中的问题。然而，这样的做法往往是一种**设计缺陷**，这可能导致类层次结构变得复杂，并且会让类之间的关系难以理解和维护，并没有充分利用继承和组合的优势。
>
>   假设我们要设计一个 `Airplane`（飞机）类。飞机有两个重要组成部分：**引擎（Engine）和 机身（Fuselage）**。

###### **合理的设计：**

>   `Airplane` 类应该**包含**引擎和机身的数据成员，也就是说，飞机类应该通过**组合**的方式拥有这些部件，而不是继承它们。
>
>   组合表示 `Airplane` 对象有一个或多个 `Engine` 和 `Fuselage` 成员，但它并不是这些东西本身，它只是**拥有**这些东西。
>
>   ```c++
>   class Engine
>   {
>   public:
>    	void start()
>    	{
>    		/* 启动引擎的代码 */
>    	}
>   };
>   
>   class Fuselage
>   {
>   public:
>    	void repair()
>    	{
>    		/* 修理机身的代码 */
>    	}
>   };
>   
>   class Airplane
>   {
>   private:
>    	Engine engine;
>    	Fuselage fuselage;
>   public:
>    	void fly()
>    	{
>    		engine.start();
>    		// 飞行的代码，可能还要使用 fuselage 的功能
>    	}
>   };
>   ```
>
>   在这个设计中，`Airplane` 类通过 **组合** 的方式使用 `Engine` 和 `Fuselage`，它拥有一个引擎和一个机身。客户代码不需要知道飞机的引擎和机身是如何工作的，只需要通过 `Airplane` 类的接口来控制飞机的行为。

###### **错误的设计（滥用继承）：**

>   -   `Airplane` 类可以内部使用 `Engine` 和 `Fuselage` 的功能（如 `start()` 和 `repair()`），但这些功能对外部代码不可见，因为它们被 `protected` 隐藏起来。
>
>   -   对外部代码来说，`Airplane` 对象看起来**不像是**一个 `Engine` 或 `Fuselage`，因为它并不暴露这些类的接口。
>
>       ```c++
>       class Engine
>       {
>       public:
>       	void start()
>       	{
>       		/* 启动引擎的代码 */
>       	}
>       };
>                                               
>       class Fuselage
>       {
>       public:
>       	void repair()
>       	{
>       		/* 修理机身的代码 */
>       	}
>       };
>                                               
>       class Airplane : protected Engine, protected Fuselage
>       {
>       public:
>       	void fly()
>       	{
>       		start();  // 调用 Engine 的方法
>       		// 使用 Fuselage 的功能
>       	}
>       };
>       ```
>
>       在这个设计中，`Airplane` 类 **继承** 了 `Engine` 和 `Fuselage`，并使用 `protected` 继承。它滥用了继承的概念。飞机并不是引擎，也不是机身，飞机只 **拥有** 这些部件。使用继承来实现这种“拥有”关系是一种设计上的误用。这样，对于客户代码来说，Airplane 对象看上去并不像引擎或机身(因为一切都是受保护的)，但在内部可以使用引擎和机身的功能。

###### **为什么会产生滥用？**

>   -   **继承**：用于表示一种**“is-a”**（是一个）关系，例如：`Dog` 是一个 `Animal`，`Car` 是一种 `Vehicle`。
>
>       **组合**：用于表示一种**“has-a”**（有一个）关系，例如：`Car` 有一个 `Engine`，`House` 有一个 `Door`。
>
>   然而，在这个飞机的例子中，`Airplane` 并不是 `Engine` 或 `Fuselage`，而是**包含**这些部件。因此，继承并不是正确的设计方式。正确的方式是**组合**，即 `Airplane` 包含 `Engine` 和 `Fuselage` 作为成员变量。
>
>   滥用继承的坏处包括：
>
>   -   代码设计混乱：类之间的关系不明确，代码难以理解和维护。
>   -   代码复用困难：因为 `protected` 继承会导致派生类的内部功能对外不可见，导致功能的封装和复用受到限制。
>   -   灵活性下降：如果将来想要更改 `Engine` 或 `Fuselage` 的实现，可能会因为继承层次复杂化而难以修改。
>
>   虽然，多重继承本身是 C++ 支持的一种特性，但在很多情况下，它会导致复杂性，尤其是当涉及到**菱形继承**（diamond inheritance）时，容易引发问题，如虚拟继承等。
>
>   在大多数情况下，组合比多重继承更易于理解、维护和扩展。因此，在设计中尽量避免多重继承，除非确有其必要。
>
>   **注意：**
>
>   非 public 继承很少见，建议慎用这一特性，因为多数程序员并不熟悉它。

****

#### 6.7虚基类

>   本章前面学习了歧义父类，当多个基类拥有共同父类时，就会发生这种情况，如下图所示：
>
>   ![image-20240920184354150](https://s2.loli.net/2024/09/20/SzkhyMfmr8nTsDG.png)
>
>   我们建议的解决方案是让共享的父类本身没有任何自有功能(完全的纯虚方法)，这样就永远无法实例化这个抽象类(因为内部含有纯虚方法)，也就永远无法调用这个类的方法，因此也就不存在歧义。

##### 抽象基类与虚基类

>   抽象基类与虚基类，解决不同问题，下面进行讨论：
>
>   | **特性**             | **抽象类**                             | **虚基类**                                 |
>   | -------------------- | -------------------------------------- | ------------------------------------------ |
>   | **定义**             | 含有纯虚函数的类，定义接口，不可实例化 | 在多重继承中共享的基类，防止基类重复实例化 |
>   | **目的是解决的问题** | 定义接口规范，强制派生类实现某些功能   | 解决菱形继承问题，避免多次实例化基类       |
>   | **语法**             | 至少包含一个纯虚函数（`= 0`）          | 使用 `virtual` 关键字继承基类              |
>   | **实例化**           | 不能实例化，必须派生实现后才能实例化   | 可以实例化，控制基类实例的唯一性           |
>   | **应用场景**         | 强制实现接口，抽象行为                 | 多重继承，避免菱形继承中的基类重复实例化   |
>   | **典型用法**         | 抽象的基类接口，派生类必须实现纯虚函数 | 复杂的继承结构中，确保基类只出现一次       |

###### 抽象类

>   抽象类是通过至少一个**纯虚函数**（`virtual function() = 0;`）定义的类，它用于定义接口，不能直接实例化。派生类必须实现抽象类中的纯虚函数，才能实例化。
>
>   **抽象类的特点：**
>
>   -   **含有纯虚函数**：一个类至少包含一个纯虚函数即被认为是抽象类。
>   -   **不能实例化**：抽象类不能创建对象实例。
>   -   **接口设计**：抽象类通常用于定义派生类必须实现的接口。
>   -   **派生类必须实现纯虚函数**：如果派生类不实现所有纯虚函数，它自己也会成为抽象类，无法实例化。
>
>   **示例：**
>
>   ```c++
>   class Animal
>   {
>   public:
>   	virtual void eat() = 0;  // 纯虚函数
>   	virtual void sleep()
>   	{   // 虚函数，可以有默认实现
>   		cout << "Animal sleeps." << endl;
>   	}
>   };
>   
>   class Dog : public Animal
>   {
>   public:
>   	void eat() override
>   	{    // 派生类必须实现纯虚函数
>   		cout << "Dog eats." << endl;
>   	}
>   };
>   ```

###### 虚基类

>   **虚基类**主要用于解决**多重继承中的“菱形继承问题”**（也称为钻石问题）。在多重继承的情况下，虚基类确保从多个派生类继承的共享基类只存在一份实例，避免多次继承同一个基类时的冲突和冗余。
>
>   **菱形继承问题：**
>
>   当一个基类被多个派生类继承，而这些派生类又被另一个类继承时，可能会导致基类被重复继承，导致冗余的副本。虚继承通过确保只创建一个基类实例来避免这个问题。
>
>   **虚基类的特点：**
>
>   -   **用于多重继承**：虚基类主要在多重继承时使用，以避免基类的重复实例化。
>   -   **只存在一份基类实例**：无论基类被间接继承多少次，通过虚继承，派生类中只会有一份基类实例。
>   -   **解决菱形继承问题**：虚继承在复杂的继承结构中确保不重复继承基类。
>
>   **示例：**
>
>   ```c++
>   class Animal
>   {
>   public:
>   	virtual void eat()
>   	{
>   		cout << "Animal eats." << endl;
>   	}
>   };
>   
>   class Mammal : public virtual Animal {};   // 虚基类继承
>   class Bird : public virtual Animal {};     // 虚基类继承
>   
>   class Bat : public Mammal, public Bird
>   {
>   	// Bat 类从 Mammal 和 Bird 继承
>   	// Animal 的成员只会有一份，不会重复
>   };
>   ```
>
>   在上面的例子中，`Mammal` 和 `Bird` 都继承了 `Animal`，而 `Bat` 又继承了 `Mammal` 和 `Bird`。通过使用虚基类，`Animal` 的实例只会在 `Bat` 中存在一份。如果没有虚继承，`Animal` 的成员在 `Bat` 中会有两个副本，从而导致歧义和资源浪费。

>   如果希望被共享的父类拥有自己的功能，C++ 提供了另一种机制来解决这个问题。如果被共享的基类是一个虚基类(virtual base class)，就不存在歧义。以下代码在 Animal 基类中添加了 sleep() 方法，并修改了 Dog 和 Bird 类，从而将 Animal 作为虚基类继承。如果不使用 virtual 关键字，用 DogBird 对象调用 sleep() 会产生歧义，从而导致编译错误。因为 DogBird 对象有两个子对象，一个来自于 Dog 类，另一个来自于 Bird。然而如果 Animal 被作为虚基类，DogBird 对象只有 Animal 类的一个子对象，因此调用 sleep() 也就不存在歧义。
>
>   ```c++
>   class Animal
>   {
>    public:
>    	virtual void eat() = 0;
>    	virtual void sleep()
>    	{
>    		cout << "zzzzz...." << endl;
>    	}
>   };
>   
>   class Dog : public virtual Animal
>   {
>    public:
>    	virtual void bark()
>    	{
>    		cout << "Woof!" << endl;
>    	}
>       
>    	virtual void eat() overrride
>    	{
>    		cout << "The dog ate." << endl;
>    	}
>   };
>   
>   class Bird : public virtual Animal
>   {
>    public:
>    	virtual void chirp()
>    	{
>    		cout << "Chirp!" << endl;
>    	}
>       	
>    	virtual void eat() override
>    	{
>    		cout << "The bird ate." << endl;
>    	}
>   };
>   
>   class DogBird : public Dog, public Bird
>   {
>    public:
>    	virtual void eat() override
>    	{
>    		Dog::eat()
>    	}
>   };
>   
>   int main()
>   {
>    	DogBird myConfusedAnimal;
>    	myConfusedAnimal.sleep();	// Not ambiguous because of virtual class
>    	return 0;
>   }
>   ```
>
>   **注意：**
>
>   **虚基类是在类层次结构中避免歧义的好办法，唯一的缺点是：许多 C++ 程序员不熟悉这个概念。**

****

### 10.7本章小结

>   继承是一种功能强大的语言特性，需要花费许多时间去熟悉， 希望在面向对象设计中，继承会成为你可供选择的工具。  

****

## 第11章 —— 理解灵活而奇特的 C++

>   本章将清晰说明 C++ 中最灵活、最奇怪的内容，来弥补书本上没有将透彻或容易被程序员遗忘的用方法和特性。

****

### 11.1引用

>   从开始学习 C++ 我们就知道专业的 C++ 代码中会大量使用引用。现在就有必要回过头来考虑一下究竟什么是引用，引用的机制是什么？
>
>   在 C++ 中，引用是另一个变量的别名。对引用的所有修改都会改变被引用的变量的值。可将引用当作隐式指针，这个指针没有取变量地址和解引用的麻烦。也可将引用当作原始变量的另一个名称。可创建单独的引用变量，在类中使用引用数据成员，将引用作为函数和方法的参数，也可让函数或方法返回引用。

****

#### 1.1引用变量

>   引用变量在创建时必须初始化，如下所示：
>
>   ```c++
>   int x = 3;
>   int& xRef = x;
>   ```
>
>   在赋值后，xRef 就是 x 的别名(alias)。使用 xRef 就是使用 x 的当前值。对 xRef 赋值会改变 x 的值。例如,下面的代码通过 xRef 将 x 的值设置为 10：  
>
>   ```c++
>   xRef = 10;
>   ```
>
>   不能在类的外部声明一个引用而不初始化它：
>
>   ```c++
>   int& emptyRef;	// DOES NOT COMPILE!
>   ```
>
>   **警告：**
>
>   创建引用时必须总是初始化它。通常会在声明引用时对其进行初始化，但是对于包含类而言，需要在构造函数初始化器中初始化引用数据变量。

##### 未命名值不可引用

###### 字面量不可引用

>   **不能创建对未命名值(例如一个整数字面量)的引用，除非这个引用是一个 const 值。在下例中，unnamedRef1 将无法编译，因为这是一个针对常量的非 const 引用。**
>
>   ```c++
>   int& unnamedRef1 = 5;	// DOES NOT COMPILE
>   const int& unnamedRef = 5;	// Works as expected
>   ```
>
>   这条语句意味着可改变常量 5 的值，而这样做没有意义。由于 unnamedRef2 是一个 const 引用，因此可以运行，不能编写 "unnamedRef2 = 7"。
>
>   为什么上面的不行，下面的代码却可以？原因如下：
>
>   在C++中，**字面值**（例如 `5`）属于**右值**，即临时对象。这些对象的生命周期非常短暂，通常只存在于表达式的计算过程中，之后就会被销毁。临时对象的特性是：不能通过普通的左值引用直接绑定，因为左值引用要求引用的对象有一个明确的、持久的内存地址。
>
>   -   **左值引用（`int&`）**：只能绑定到左值，即有持久地址的对象。临时对象不符合这一要求，因为它们在表达式计算完成后就会被销毁。
>   -   **`const` 引用（`const int&`）**：C++标准允许`const`引用绑定到临时对象，且延长临时对象的生命周期，直到引用本身的生命周期结束。这是`const`引用的一个重要特性。

###### 临时对象不可引用

>   临时对象同样如此，不能具有临时对象的非 const 引用，但可具有 const 引用。例如，假设以下函数返回一个 std::string 对象：
>
>   ```c++
>   std::string getString()
>   {
>   	return "Hello world!";
>   }
>   ```
>
>   对于调用 getString() 的结果，可以由一个 const 引用；在该 const 引用超出作用域之前，将使 std::string 对象一直处于活动状态：
>
>   ```c++
>   std::string& string1 = getString();	// DOES NOT COMPILE
>   const std::string& string2 = getString();	// Works as expected
>   ```

##### 1.修改引用

>   **引用总是引用初始化的那个变量：引用一旦创建，就无法修改。**
>
>   这一规则导致许多让人迷惑的语法。如果在声明引用时用一个变量 **“赋值”**，那么这个引用就指向这个变量。然而，如果在此后使用变量对引用赋值，被引用变量的值就变为被赋值变量的值，引用不会更新为指向这个新变量。
>
>   ```c++
>   int x = 3, y = 4;
>   int& xRef = x;
>   xRef = y;	
>   // Change value of x to 4. Does not make xRef refer to y.
>   ```
>
>   你可能试图在赋值时取 y 的地址，以绕过这一限制：
>
>   ```c++
>   xRef = &y;	// DOES NOT COMPOLE!
>   ```
>
>   上面代码无法完成编译：y 的地址是一个指针，但 xRef 被声明为一个指向 int 值的引用，而不是指向指针的引用。
>
>   一些程序员甚至更进一步，尝试回避引用的语义 —— 如果将一个引用赋值给另一个引用，会发生什么？这样做会使得第一个引用指向第二个引用吗？编写下方代码发现：
>
>   ```c++
>   int x = 3, y = 5;
>   int& xRef = x;
>   int& yRef = y;
>   yRef = xRef;	// Assigns value, not references
>   ```
>
>   最后一行代码没有改变 yRef 的引用对象，只是将 y 的值设置为了 3，因为 xRef 指向 x，x 的值为 3。
>
>   **警告：**
>
>   **在初始化引用之后，无法改变引用所指(别名)的变量，只能改变该变量的值。**

##### 2.指向指针的引用和指向引用的指针

>   可创建任何类型的引用，包括指针类型，下面列举一个指向 int 值的指针的引用；
>
>   ```c++
>   int* intP;
>   (int*)&ptrRef = intP;
>   ptrRef = new int;
>   *ptrRef = 5;
>   ```
>
>   对于初学者上面的很难理解，不过对于我来说，已经是熟米饭了。
>
>   **指针的引用很少见，但是在某些特殊场合下却十分有用，本章的 1.3 节将会讨论这一内容。**
>
>   **注意：**
>
>   对引用取地址的结果与被引用变量取地址的结果相同。例如：
>
>   ```c++
>   int x = 3;
>   int& xRef = x;
>   int* xPtr = &xRef;	// Address of a reference is pointer to value
>   *xPtr = 100;
>   ```
>
>   上述代码通过取 x 应用的地址，使 xPtr 指向 x。将 *xPtr 赋值为 100，x 的值也变成了 100。比较表达式 "xPtr == xRef" 将无法编译，因为类型不匹配；xPtr 是一个指向 int 值的指针，而 xRef 是一个指向 int 值的引用。比较表达式 "xPtr == &xRef" 和 "xPtr == &x" 都可以正确编译，结果都是 true。
>
>   **注意：**
>
>   **无法声明引用的引用或者指向引用的指针：例如，不允许使用 (int&)& 或 (int&) ***，原因如下：
>
>   在C++的底层，**引用**的实现本质上是通过**指针**来完成的。虽然在语言的语义层面，引用是一种比指针更直接、更简化的抽象，但在实际的底层实现中，编译器通常会将引用优化为指针。
>
>   在编译器生成的机器代码中，**引用通常会被转换为指向原对象的指针**。这意味着，尽管你在源代码中使用的是引用，但在实际的执行过程中，它的行为就像是一个指针。
>
>   尽管在底层引用可以被当作指针来实现，但与指针相比，引用有一些重要的限制和区别，这些差异也会反映在底层：
>
>   -   **引用不能重新绑定**：在C++中，引用一旦绑定到一个对象，它就不能重新指向其他对象。这意味着编译器不会生成类似于重新赋值指针的代码，而是确保引用始终绑定到初始对象。
>
>       对于指针来说，类似的操作是允许的，但引用在编译时会强制保证其绑定的不可变性。
>
>   -   **引用的地址不可访问**：引用本质上是对象的别名，而不是一个实际的对象，所以不能获取引用本身的地址。尽管底层引用通常实现为指针，用户代码中却无法访问这个指针。这意味着你不能对引用执行类似于 `&ref` 这样的操作来得到一个“指向引用的指针”。 

****

#### 1.2引用数据成员

>   第 9 章讲过，类的数据成员可以是引用。如果不指向其他变量，引用就无法存在。因次，必须在构造函数初始化器(constructor initializer)中初始化引用数据成员，而不是在构造函数体中。下面列举一个简单示例：
>
>   ```c++
>   class MyClass
>   {
>   public:
>   	MyClass(int& ref) : mRef(ref) {}
>   
>   private:
>   	int& mRef;
>   };
>   ```
>
>   详细参考第 9 章内容。

****

#### 1.3引用参数

>   C++ 程序员通常不会单独使用引用变量或引用数据成员。
>
>   引用经常作为函数或方法的参数。
>
>   默认的参数传递机制是按值传递：函数接收参数的副本，修改这些副本时，原始的参数保持不变。
>
>   引用允许指定另一种向函数传递参数的语义：按引用传递，当使用引用参数时，函数将引用作为参数，如果引用被修改，最初的参数变量也会被修改。假如，下面给出了一个简单的交换函数，交换两个 int 变量的值：
>
>   ```c++
>   void swap(int& first, int& second)
>   {
>   	int temp = first;
>   	first = second;
>   	second = temp;
>   }
>   ```
>
>   可采用下面的方式调用这个函数：
>
>   ```c++
>   int x = 5, y = 6;
>   swap(x, y);
>   ```
>
>   当使用 x 和 y 作为参数调用 swap() 时，将会交换引用的值。
>
>   就像无法用常量初始化普通引用变量一样，不能将常量作为参数传递给 “按非 const 引用传递” 的函数：
>
>   ```c++
>   swap(3, 4);		// DOES NOT COMPILE
>   ```
>
>   **注意：**
>
>   **使用 “按 const 引用传递”(将在本章后面讨论) 或 “按右值引用传递”(见第 9 章的讨论)，可将常量作为参数传递给函数。**

##### 1.使用指针转换为引用

>某个函数或方法需要一个引用作为参数，而你拥有一个指向被传递值的指针，这是一种十分常见的困境。在此情况下，可对指针解除引用(dereferencing)，将指针 **“转换”** 为引用。这一行为会给出指针所指的值，随后编译器用这个值初始化引用参数。例如，可以这样调用 swap()：
>
>```c++
>int x = 5, y = 6;
>int* xp = &x;
>int* yp = &y;
>swap(*xp, *yp);
>```

##### 2.按引用传递与按值传递

>如果要修改参数，并修改参数传递给函数或方法的变量，就需要使用按引用给传递。然而，按引用传递的用途，并不具局限于此。按引用传递不需要将参数的副本复制到函数，在有些情况下这会带来以下两方面好处：
>
>1.   **效率：**复制较大的对象或结构需要较长时间，按值传递只是把指向对象或结构的指针传递给函数。
>2.   **正确性：**并非所有对象都允许按值传递，即使允许按值传递的对象，也可能不支持正确地深度拷贝(deep copying)，第 9 章提到为支持深度复制，动态分配的对象必须提供自定义复制构造函数或复制赋值运算符。
>
>如果要利用这些好处，但不想修改原始对象，可将参数标记为 const，从而实现按常量引用传递参数。本章后面将会详细讨论这一主题。
>
>按引用传递的这些优点意味着，只有在参数是简单的内建类型(例如：int 或 double)，且不需要修改参数的情况下，才应该使用按值传递。在其他所有情况都应该使用按值传递。

****

#### 1.4将引用作为返回值

>   还可以让函数或方法返回一个引用。这样做主要是为了提高效率，返回对象的引用而不是整个对象可以避免不必要的复制。当然，只有涉及的对象在函数终止之后仍然存在的情况下才能使用这一技巧。
>
>   **警告：**
>
>   **如果变量的作用域局限于函数或方法(例如：堆栈中自动分配的变量，在函数结束时会被销毁)，绝不能返回这个变量的引用。这时极其危险的行为。**
>
>   如果从函数返回的类型支持移动语义(见第 9 章)，按值返回就几乎和返回引用一样高效。
>
>   返回引用的另一个原因是希望将返回值直接赋为左值(lvalue)(赋值语句的左边)。一些重载的运算符通常会返回引用，第 9 章列举了一些示例，在第 15 章可以看到这一技术的更过应用。

****

#### 1.5右值引用

>   右值(rvalue)就是非左值(lvalue)，例如常量值、临时对象或值。通常而言，右值位于赋值运算符的右侧。第 9 章讨论了右值引用，这里做一下简单回顾：
>
>   ```c++
>   // lvalue reference parameter
>   void handleMessage(std::string& message)
>   {
>       cout << "handleMessage with lvalue reference: " << message << endl;
>   }
>   ```
>
>   对于这个 handleMessage() 版本，不能采用如下方法调用它：
>
>   `````c++
>   handleMessage("Hello World");	// A literal is not an lvalue.
>   
>   std::string a = "Hello ";
>   std::string b = "World";
>   handleMessage(a + b);	// A temperary is not an lvalue.
>   `````
>
>   需要支持此类调用，需要一个接收右值引用的版本：
>
>   ```c++
>   // rvale reference parameter
>   void handleMessage(std::string&& message)
>   {
>       cout << "handleMessage with rvale reference: " << message << endl;
>   }
>   ```
>
>   可参阅第 9 章以复习相关知识。

****

#### 1.6使用引用还是指针

>   在 C++ 中，可认为引用是多余的：几乎所有使用引用可以完成的任务都可以用指针来完成。(因为引用在之后编译中确实是转化为了指针)例如，可这样编写前面的 swap() 函数：
>
>   ```c++
>   void swap(int* first, int* second)
>   {
>      int temp = *first;
>      *first = *second;
>      *second = temp;
>   }
>   ```
>
>   然而，这些代码不如使用引用的版本那么清晰：**引用可使程序整洁并易于理解。**
>
>   此外，引用比指针更安全：**不可能存在无效引用，也不需要显式地解除引用，因此不会遇到像指针那样的接触引用的问题。**
>
>   有人说引用更安全，但这个论点只有在不涉及指针的情况下才成立。例如，下面的函数将会指向 int 值的引用作为参数：
>
>   ```c++
>   void refcall(int& t)
>   {
>      ++t;
>   }
>   ```
>
>   可声明一个指针并将其初始化为指向内存某一个随机位置。然后可对这个指针接触引用，并将其作为引用参数传递给 refcall()，下面的代码可以编译，但是试图执行时会崩溃：
>
>   ```c++
>   int* ptr = (int*)8;
>   recall(*ptr);
>   ```
>
>   大多数情况下，应该使用引用而不是指针。对象的引用甚至可以向指向对象的指针那样支持多样性。但也有一些情况要求使用指针：
>
>   -   一个例子是更改指向的位置，因为无法改变引用所指的变量。例如，动态分配内存时，应该将结果存储在指针而不是引用中。
>   -   需要使用指针的另一个情况时可选参数，即指针参数可以定义为带默认 mullptr 的可选参数，而引用参数不能这样定义。
>   -   还有一种情况是要在容器中存储多态类型。
>
>   有一种方法可以判断使用指针还是引用作为参数和返回类型：考虑谁拥有内存。如果接收变量的代码负责释放相关的内存，那么必须使用指向对象的指针，最好是智能指针，这时传递拥有权的推荐方式。如果接收变量的代码不需要释放内存，那么就应该使用引用。
>
>   **注意：**
>
>   **要优先使用引用，也就是说，只有在无法使用引用的情况下，才使用指针。**
>
>   首先，我先补充一部分 C/C++ 语言知识，关于指针和地址的问题：
>
>   在 C++ 中，指针和引用的行为取决于传递的数据类型和作用范围。让我们从基本概念入手，解释为什么 `int*` 只能修改指针指向的值，但不能修改指针本身，而 `int**` 可以修改指针本身。
>
>   1.   **`int*` (单指针)传递**
>
>   当你传递 `int*`（单指针）作为函数参数时，**传递的是指针的副本**，这个指针副本指向某个数据，但它本身也是一个变量。在函数内部，你可以通过这个指针修改它所指向的内存中的值，但是不能改变这个指针本身的地址，因为你操作的只是副本，**对副本的修改不会影响原始指针**。
>
>   ```cpp
>   void modifyPointer(int* p) {
>       *p = 20;  // 修改指针指向的值
>       p = nullptr;  // 尝试修改指针本身（无效，因为 p 是一个局部副本）
>   }
>   
>   int main() {
>       int x = 10;
>       int* ptr = &x;
>   
>       modifyPointer(ptr);
>   
>       std::cout << x << std::endl;  // 输出 20，指针指向的值已被修改
>       std::cout << ptr << std::endl;  // 输出原来的地址，指针本身未被修改
>   }
>   ```
>
>   - `*p = 20;`：这里修改了 `p` 指向的值，因此 `x` 的值从 10 变成了 20。
>   - `p = nullptr;`：这里尝试修改指针 `p` 本身，但这只会修改 `p` 的**局部副本**，不会改变 `main` 函数中的 `ptr`。因此，`ptr` 的值不会变为 `nullptr`。
>
>   **结论**：当传递 `int*` 时，你可以修改指针指向的值（即 `*p`），但不能修改指针本身的值（即 `p`），因为 `p` 是指针的局部副本。
>
>   2.   **`int**` (双重指针)传递**
>
>   当你传递 `int**`（双重指针）时，**实际上传递的是指向指针的指针**。换句话说，`int**` 让你在函数内部拥有对指针本身的控制权。因此，你可以通过双重指针修改指针的值，改变它所指向的地址。
>
>   #### 示例：
>
>   ```cpp
>   void modifyPointer(int** p) {
>       **p = 20;  // 修改指针指向的值
>       *p = nullptr;  // 修改指针本身
>   }
>   
>   int main() {
>       int x = 10;
>       int* ptr = &x;
>   
>       modifyPointer(&ptr);  // 传递指针的地址
>   
>       std::cout << x << std::endl;  // 输出 20，指针指向的值已被修改
>       std::cout << ptr << std::endl;  // 输出 nullptr，指针本身也被修改
>   }
>   ```
>
>   - `**p = 20;`：这里通过双重指针修改了 `p` 所指向的指针所指向的值，即修改了 `ptr` 所指向的值，因此 `x` 的值被修改为 20。
>   - `*p = nullptr;`：这里通过双重指针修改了 `p` 所指向的指针（即 `ptr` 本身），因此 `ptr` 被改为 `nullptr`。
>
>   **结论**：当传递 `int**` 时，你可以通过双重指针修改原始指针的指向（即 `ptr`），因此可以改变原始指针本身。
>
>   3.   **`int*&` 传递时的行为**
>
>   在 C++ 中，`int*&` 是指向指针的引用，它可以让你通过引用修改指针的值，而无需使用双重指针。`int*&` 是引用语法的简洁版本，但它的作用和 `int**` 类似，因为你仍然可以通过引用修改原始指针。
>
>   ```cpp
>   void modifyPointer(int*& p) {
>       p = nullptr;  // 修改指针本身
>   }
>   
>   int main() {
>       int x = 10;
>       int* ptr = &x;
>   
>       modifyPointer(ptr);  // 传递指针的引用
>   
>       std::cout << ptr << std::endl;  // 输出 nullptr，指针本身已被修改
>   }
>   ```
>
>   - `p = nullptr;`：这里通过引用修改了指针 `p`，因此原始指针 `ptr` 被修改为 `nullptr`。
>
>   **结论**：使用 `int*&`（引用指针）可以实现类似 `int**` 的效果，即可以修改原始指针的值。
>
>   4.   **总结：**
>
>   - **`int*`**：当你传递 `int*` 时，传递的是指针的副本。你可以修改指针指向的值，但不能修改指针本身，因为你操作的是副本。
>   - **`int**`**：当你传递 `int**` 时，传递的是指向指针的指针。你可以通过双重指针修改原始指针的指向，因此可以修改指针本身及其指向的值。
>   - **`int*&`**：是 C++ 中的一种引用语法，它提供了与 `int**` 类似的功能，可以修改原始指针的值。
>
>   因此，**`int*` 不能修改指针本身**，而 `int**` 和 `int*&` 可以，因为它们提供了对指针本身的访问。
>
>   ****
>
>   接下来，考虑将一个 int 数组分割为两个数组的函数：一个是偶数数组，另一个是奇数数组。这个函数并不知道源数组中有多少个奇数和偶数，因此只有在测试完源数组后，才能为目标数组动态分配内存，此外还需要返回这两个新数组的大小。因此总共需要返回 4 项 —— 两个新数组的指针和两个新数组的大小。显然必须使用按引用传递，用规范的 C 语言方式编写的这个函数如下所示：
>
>   ```c++
>   void separateOddaAndEvens(const int arr[], 
>                             size_t size, 
>                             int** odds,
>                             size_t* numOdds, 
>                             int** evens, 
>                             size_t* numEvens)
>   {
>       // Count the number of oods and evens
>       *numOdds = *numEvens = 0;
>       for (size_t i = 0; i < size; ++i)
>       {
>           if (arr[i] % 2 == 1)
>           {
>               ++(*numOdds);
>           }
>           else
>           {
>               ++(*numEven);
>           }
>       }
>   
>       // Allocate two new arrays of the appropriate size.
>       *oods = new int(*numOdds);
>       *evens = new int(*numEvens);
>   
>       // Copy the odds and evens to the new array
>       size_t oddsPos = 0;
>       size_t evensPos = 0;
>       for (size_t i = 0; i < size; ++i)
>       {
>           if (arr[i] % 2 == 1)
>           {
>               (*oods)[oddsPos++] = arr[i];
>           }
>           else
>           {
>               (*even)[evensPos++] = arr[i];
>           }
>       }
>   }
>   ```
>
>   函数的后 4 个参数是 **“引用”** 参数。为修饰它们指向的值，separateOddsAndEvens() 必须解除引用，这使得函数体内部的语法看起来很丑陋，确实如此。此外，如果要调用 separateOddsAndEvens()，就必须传递两个指针的地址，这样函数才能修改实际的指针，还必须传递两个 int 值的地址，这样函数才能修改实际的 int 值。另外注意，主调方负责删除由 separateOddsAndEvens() 还必须创建两个数组！
>
>   ```c++
>   int upSplit[] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
>   int* oddNums = nullptr;
>   int* evenNums = nullptr;
>   size_t numOdds = 0;
>   size_t numEvens = 0;
>   
>   separateOddsAndEvens(unSplit, std::size(unSplit), &oddNums, &numOdds, &evenNums, &numEvens);
>   
>   // Use the arrays...
>   
>   delete[] oddNums;
>   oddNums = nullptr;
>   delete[] evenNums;
>   evenNums = nullptr;
>   ```
>
>   正常人都会觉得上面的代码很难理解，而我们事实上在 C++ 中使用 引用 便可以很轻松地实现这一点：
>
>   ```c++
>   void separateOddsAndEvens(const int arr[],
>                             size_t size, 
>                             (int*)& odds, 
>                             size_t& numOdds, 
>                             (int*)& evens, 
>                             size_t& numEvens)
>   {
>       numOdds = numEvens = 0;
>       for (size_t i = 0; i < size; ++i)
>       {
>           if (arr[i] % 2 == 1)
>           {
>               ++numOdds;
>           }
>           else
>           {
>               ++numEvens;
>           }
>       }
>   
>       odds = new int[numOdds];
>       evens = new int[numEvens];
>   
>       size_t oddsPos = 0;
>       size_t evensPos = 0;
>       for (size_t i = 0; i < size; ++i)
>       {
>           if(arr[i] % 2 == 1)
>           {
>               odds[oddsPos++] = arr[i];
>           }
>           else
>           {
>               evens[evensPos++] = arr[i];
>           }
>       }
>   }
>   ```
>
>   在此情况下，adds 和 evens 参数是指向 int* 的引用。separateOddsAndEvnes() 可以修改用作函数参数的 int*(通过引用)，而不需要显式地解除引用。这一逻辑同样适用于 numOdds 和 numEvens，这两个参数是指向 int 值的引用。使用这个版本的函数时，不需要再使用传递指针或 int 值的地址，引用参数会自动进行处理：
>
>   ```c++
>   separateOddsAndEvens(unSplit, std::size(unSplit), oddNums, numOdds, evenNums, numEvens);
>   ```
>
>   虽然与使用指针相比，使用引用参数总是更加整洁，但建议尽可能避免动态分配数组。例如，使用标准库的 vector 容器重写前面的 separateOddsAndEvens() 函数，可以使用更安全、更紧凑、更易读，因为所有的内存分配和释放内存都是自动完成的。
>
>   ```c++
>   void separateOddsAndEvens(const vector<int>& arr, vector<int>& odds, vector<int>& evens)
>   {
>       for (int i : arr)
>       {
>           if (i % 2 == 1)
>           {
>               odds.push_bash(i);
>           }
>           else
>           {
>               evens.push_back(i);
>           }
>       }
>   }
>   ```
>
>   可这样使用这个版本的函数：
>
>   ```c++
>   vector<int> vecUnSplit = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
>   vector<int> odds;
>   vector<int> evens;
>   separateOddsAndEvens(vecUnSplit, odds, evens);
>   ```
>
>   注意，不需要释放 odds 和 evens 容器：该任务由 vector 类负责完成。与使用指针或引用版本相比，这个版本更容易使用。第 17 章将详细讨论标准库的 vector 容器。
>
>   **虽然使用 vector 容器的版本比使用指针或引用的版本要的多，但通常要避免使用输出参数。如果函数需要返回一些内容，则直接返回，而不要使用输出参数。**
>
>   **自从 C++11 引入移动语义以来，从函数返回值变得十分高效；**
>
>   **而 C++17 引入了结构化绑定(见第 1 章)，从函数返回多个值是十分简便的。**
>
>   因此，对于 separateOddsAndEvens() 函数而言，不是接收两个输出矢量(vector)，而是返回矢量 pair。<utility> 中定义的 std::pair 实用工具类将在第 17 章中讨论，其方法相当简单。基本上，矢量 pair 可存储两个相同类型的值，也可以存储两个不同类型的值。它是一个模板类，需要使用放在尖括号之间的类型来指定值的类型。可使用 std::make_pair() 来创建矢量 pair。下面的 spearateOddsAndEvens() 函数返回矢量 pair：
>
>   ```c++
>   pair<vector<int>, vector<int>> sepearateOddsAndEvens(const vector<int>& arr)
>   {
>       vector<int> odds;
>       vector<int> evens;
>   
>       for (int i : arr)
>       {
>           if (i % 2 == 1)
>           {
>               odds.push_back(i);
>           }
>           else
>           {
>               evens.push_back(i);
>           }
>       }
>   
>       return make_pair(odds, evens);
>   }
>   ```
>
>   通过使用结构话绑定，调用 separateOddsAndEvens() 代码变得更加紧凑，更容易读取和理解：
>
>   ```c++
>   vector<int> vecUnSplit = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
>   auto{odds, evens} = separateOddsAndEvens(vectorUnSplit);
>   ```

****

### 11.2关键字的疑问

>   C++ 中的两个关键字 const 和 static 非常让人困惑。这两个关键字有多个不同的涵义，每个用法都很微妙，很容易理解出现偏差。

****

#### 2.1const 关键字

>   **const 是 constant 的缩写，指保持不变的量。**
>
>   **编译器会执行这一要求，任何尝试改变常量的行为都会被当作错误处理。**
>
>   **此外，当启用优化时，编译可利用此信息生成更好的代码。关键字 const 有两种相关的用法。可以用这个关键字标记比爱能量或参数，也可以用其标记方法。**本章将详细讨论这两种含义：

##### 1.cosnt 变量和参数

>   可使用 const 来 **“保护”** 变量不被修改。
>
>   这个关键字的一个重要用法就是替换 #define 宏 来定义常量，这时 const 最直接的用法。
>
>   例如，可以这样声明常量 PI：
>
>   ```c++
>   const double PI = 3.141592653589793238462;
>   ```
>
>   可将任何变量标记为 const，包括全局变量和类数据成员。
>
>   还可使用 const 指定函数或方法的此参数保持不变。例如，下面的函数将接收一个 const 参数。在函数体内部，不允许修改整数 param，如果试图修改这个变量，编译器将会生成错误：
>
>   ```c++
>   void func(const int param)
>   {
>       // Not allowed to change param...
>   }
>   ```
>
>   下面详细讨论两种特殊的 const 变量或参数：const 指针 和 const 引用：

###### const 指针

>   当变量通过指针包含一层或多层间接取值时，const 的应用将会变得十分微妙。考虑下面的代码行：
>
>   ```c++
>   int* ip;
>   ip = new int[10];
>   ip[4] = 5;
>   ```
>
>   假定要将 const 应用到 ip 上。暂时不考虑这么做有没有作用，只考虑这样做意味着什么？是想阻止修改 ip 变量本身，还是阻止修改 ip 所指的指？也就是说，是组织上例的第 2 行还是第 3 行？
>
>   为了阻止修改所指的值(第 3 行)，可在 ip 的声明中这样添加关键字 const：
>
>   ```c++
>   const int* = ip;
>   ip = new int[10];
>   ip[4] = 5;	// DOES NOT COMPILE！
>   ```
>
>   现在无法修改 ip 所指的值。
>
>   下面是在语义上等价的另一种方法：
>
>   ```c++
>   int const* ip;
>   ip = new int[10];
>   ip[4] = 5;	// DOES NOT COMPILE!
>   ```
>
>   将 const 放到 int 前面还是后面并不影响其功能。
>
>   如果要将 ip 本身标记为 const(而不是 ip 所指的值)，可以这样做：
>
>   ```c++
>   int* const ip = nullptr;
>   ip = new int[10];	// DOES NOT COMPILE!
>   ip[4] = 5;			// Error: dereferencing a null pointer
>   ```
>
>   现在 ip 本身无法修改，编译器要求在声明 ip 时就执行初始化，可使用前面代码中的nullptr，也可以使用新分配的内存，如下所示：
>
>   ```c++
>   int* const ip = new int[10];
>   ip[4] = 5;
>   ```
>
>   还可以将指针和所指的值全部标记为 const，如下所示：
>
>   ```c++
>   const int* const ip = nullptr;
>   ```
>
>   下面是另一种等价的语法：
>
>   ```c++
>   int const* const ip = nullptr;
>   ```
>
>   尽管这些语法看起来十分凌乱，但规则实际上非常简单：将 cosnt 关键字应用到直接位于它左边的任何内容。再次考虑从这一行：
>
>   ```c++
>   int const* const ip = nullptr;
>   ```
>
>   从左到右，第一个 const 直接位于 int 的右边，因此将 const 应用到 ip 所指的 int，从而指定无法修改的 ip 所指的值。第二个 const 直接位于 * 的右边，因此将 const 应用于指向 int 变量的指针，也就是 ip 的变量。因此，无法修改 ip(指针)本身。
>
>   这一规则由于一个例外而变得令人费解：第一个 const 可出现在变量的前面，如下所示。
>
>   ```c++
>   const int* const ip = nullptr;
>   ```
>
>   这种 **“异常的”** 语法相比其他语法更常见。
>
>   可将这个规则应用到任意层次的间接取值，例如：
>
>   ```c++
>   const int * const * const * const ip = nullptr;
>   ```
>
>   **注意：**
>
>   还有一种易于记忆的、用于指出复杂变量声明的规则：从右往左读，考虑示例 "int* const ip"，从右向左读这条语句，就可以知道 “ip 是一个指向 int 值的 const 指针”。另外，"int const* ip" 读作 “ip 是一个指向 const int 的指针”。

###### const 引用

>   将 const 应用于引用通常比引用于指针更简单，原因有两个。首先，引用默认为 const,无法改变引用所指的对象。因此，不必显式地将引用标记为 const。其次，无法创建指向引用的指针，所以引用通常只有一层间接取值。获取多层间接取值的唯一方法就是创建指向指针的引用。
>
>   因此，C++ 提到 “const 引用” 时，含义如下所示：
>
>   ```c++
>   int z;
>   const int& zRef = z;
>   zRef = 4;	// DOES NOT COMPILE!
>   ```
>
>   由于将 const 引用到 int，因此无法对 zRef 赋值，如前所示。
>
>   **与指针类似，const int& zRef 等价于 int const& zRef。**
>
>   **然而，要注意，将 zRef 标记为 const 对 z 没有影响。仍然可以通过 z 对值进行修改，具体就是：直接改变 z 值，而非通过间接引用的方式。**
>
>   const 引用经常作为阐述，这非常有用。如果为了提高效率，想按引用传递某个值，但不想修改这个值，可将其标记为 const 引用。例如：
>
>   ```c++
>   void deSomething(const BigClass& arg)
>   {
>      // Implementation here
>   }
>   ```
>
>   **警告：**
>
>   **将对象作为参数传递时，默认选择是 const 引用。只有在明确需要修改对象时，才能忽略 const。**

##### 2.const 方法

>   第 9 章讲过，可将类方法标记为 const，以禁止方法修改类的任何非可变(non-mutable)数据成员，示例请参阅第 9 章。

##### 3.constexpr 关键字

>   C++ 中一直存在常量表达式的概念，在某些情况下需要常量表达式。例如当定义数组时，数组的大小就必须是一个常量表达式。由于这一限制，下面代码在 C++ 中是无效的：
>
>   ```c++
>   const int getArraySize()
>   {
>       return 32;
>   }
>   
>   int main()
>   {
>       int myArray[getArraySize()];	// Invalid in C++
>       return 0;
>   }
>   ```
>
>   可使用 constexpr 关键字重新定义 getArraySize() 函数，把它变成常量表达式。常量表达式在编译时计算。
>
>   `````C++
>   constexpr int getArraySize() 
>   {
>       return 32;
>   }
>   
>   int main()
>   {
>       int myArray[getArraySize()];	// OK
>       return 0;
>   }
>   `````
>
>   甚至可以这样做：
>
>   ```c++
>   int myArray[getArraySize() + 1];	// OK
>   ```
>
>   将函数声明为 constexpr 会对函数行为施加一些限制，因为编译器必须是在编译期间对 constexpr 函数求值，函数也不允许由任何副作用。下面是几个限制：
>
>   -   函数体不包含 goto 语句、try chatch 块、未初始化的变量、非字面量类型的变量定义，也不抛出异常，但可调用其他的 constexpr 函数。**“字面量类型”(literal type)** 是 constexpr 变量的类型，可从 constexpr 函数返回。字面量类型可以是 void(可能有 const/volatile 限定符)、标量类型(整型和浮点类型、枚举类型、指针类型、成员指针类型，这些类型由 const/volatile 限定符)、引用类型、字面量数组类型或类类型。类类型可能也有 const/volatile 限定符，具有普通的(即非用户提供的)析构函数，至少有一个 constexpr 构造函数，所有非静态数据成员和基类都是字面量类型。
>   -   函数的返回类型应该是字面量类型。
>   -   如果 constexpr 函数是类的一个成员，那么这个函数不能是虚函数。
>   -   函数所有的参数都应该是字面量类型。
>   -   在编译单元(translation unit)中定义了 constexpr 函数后，才能调用这个函数，因为编译器需要知道完整的定义。
>   -   不允许使用 dynamic_cast() 和 reinterpret_cast()。
>   -   不允许使用 new 和 delete 表达式。
>
>   通过定义 constexpr 构造函数，可创建用户自定义类型的常量表达式变量。constexpr 构造函数具有很多限制，其中的一些限制如下所示：
>
>   -   类不能具有任何虚基类。
>   -   构造函数中的所有参数都应该是字面量类型。
>   -   构造函数体不应该是 function-try-block(见第 14 章)。
>   -   构造函数体应该满足与 constexpr 函数体相同的要求，并显式设置为默认(= default)。
>   -   所有数据成员都应该用常量表达式初始化。
>
>   例如，下面的 Rect 类定义了一个满足上述要求的 constexpr 构造函数，此外还定义了一个 constexpr getArea() 方法，执行一些计算：
>
>   ```c++
>   class Rect 
>   {
>   public:
>       constexpr Rect(size_t width, size_t height) : meWidth(width), mHeight(height) {}
>       constexpr size_t getArea() const 
>       {
>           return mWidth * mHeight;
>       }
>       
>   private：
>       size_t mWidth;
>       size_t mHeight;
>   };
>   ```
>
>   使用这个类声明 constexpr 对象相当直接：
>
>   ```c++
>   constexpr Rect r(8, 2);
>   int myArray[r.getArea()];	// OK
>   ```

****

#### 2.2static 关键字

>   在 C++ 中，static 关键字有多种用法，这些用法好像并没有关系。**“重载”** 这个关键字的部分原因是为了避免在语言中引入新的关键字。

##### 1.静态数据成员和方法

>   **可声明类的静态数据成员和方法。静态数据成员与非静态数据成员不同，它们不是对象的一部分。相反，这个数据成员只有一个副本，这个副本存在于类的任何对象之外。**
>
>   **静态方法与此类似，位于类层次(而不是对象层次)。静态方法不会在某个特定对象环境中执行。**
>
>   第 9 章提供了静态数据成员和静态方法的示例。

##### 2.静态链接(static linkage)

>   在解释用于链接的 static 关键字之前，首先要理解 C++ 中链接的概念：
>
>   **在 C++ 中，每个源文件（`.cpp` 文件）通常都会被**单独编译**，生成相应的目标文件（`.o` 或 `.obj` 文件）。编译完成后，所有目标文件会通过**链接器**进行链接，组合成一个可执行文件。**
>
>   **C++ 源文件中的每个名称，包括函数和全局变量，都有一个内部或外部的链接。**
>
>   **外部链接意味着这个名称在其他源文件中也有效，内部链接(也称静态链接)意味着在其他源文件中无效。**
>
>   **在这个过程中，符号的链接性决定了某个符号（变量或函数）的作用范围是仅限于当前源文件（即内部链接），还是可以在多个源文件中共享（即外部链接）。因此，链接性控制了符号是否可以在不同的文件之间互相引用和使用。**
>
>   **默认情况下，函数和全局变量都拥有外部链接。然而，可在声明的前面使用关键字 static 指定内部(或静态)链接。**
>
>   例如，假定有两个源文件 FirstFile.cpp 和 AnotherFile.cpp，下面是 FirstFlie.cpp：
>
>   ```c++
>   void f();
>   
>   int main()
>   {
>      f();
>      return 0;
>   }
>   ```
>
>   注意这个文件中提供了 f() 函数的原型，但没有给出具体定义。下面是 AnotherFile.cpp：
>
>   ```c++
>   #include <iostream>
>   
>   void f();
>   
>   void f()
>   {
>      std::cout << "f\n";
>   }
>   ```
>
>   这个文件同时提供了 f() 函数的原型和定义。注意在这两个不同文件中编写相同函数的原型是合法的。如果将原型放在头文件中，并在每个源文件中都用 #include 包含这个头文件，预处理器就会自动在每个源文件中给出函数原型。之所以使用头文件，是因为它便于维护(并保持同步)原型的副本。然而，这个示例没有使用头文件。
>
>   这两个源文件都可成功编译，程序链接也没有问题：因为 f() 具有外部链接，main() 函数可从另一个文件调用这个函数。
>
>   现在假定在 AnotherFile.cpp 中将 static 应用到 f() 函数原型。注意不需要在 f() 函数的定义前面重复使用 static 关键字。只需要在函数名称的第一个示例前使用这个关键字，不需要重复它：
>
>   ```c++
>   #include <iostream>
>   
>   static void f();
>   
>   void f()
>   {
>       std::cout << "f\n";
>   }
>   ```
>
>   现在每个源文件都可成功编译，但链接时将失效，因为 f() 函数具有内部(静态)链接，FirstFile.cpp 无法使用这个函数。如果在源文件中定义了静态方法但是没有使用它，有些编译器会给出警告(指出这些方法不应该是静态的，因为其他文件可能会使用到它们)。
>
>   将 static 用于内部链接的另一个方式是使用匿名名称空间(anonymous namespaces)。可将变量或函数封装到一个没有名字的名称空间，而不是使用 static，如下所示：
>
>   ```c++
>   #include <iostream>
>   
>   namespace
>   {
>       void f();
>       
>       void f()
>       {
>           std::cout << "f\n";
>       }
>   }
>   ```
>
>   在同一源文件中，可在声明匿名名称空间之后的任何位置访问名称空间中的项，但不能在其他源文件中访问。这一语义与 static 关键字相同。
>
>   **警告：**
>
>   **要获取内部链接，建议使用匿名名称空间，而不要使用 static 关键字。**它适用于更复杂的场景，如包含多个函数和变量的命名空间封装。而且在现代 C++ 编程中，匿名命名空间被认为是更优雅和安全的方式，因为：
>
>   -   **可读性**：匿名命名空间清楚地表达了其意图：封装当前文件的符号，使其在其他文件中不可见。相比之下，`static` 关键字的含义更加多样（还可以用于静态局部变量、静态类成员等），可能会增加代码的复杂性。
>   -   **命名空间功能**：匿名命名空间还可以封装多个函数和变量，提供更强的组织和管理功能，而 `static` 只能作用于单个符号。

###### extern 关键字

>   **extern 关键字好像是 static 的反义词，将它后面的名称指定为外部链接。**
>
>   某些情况下可使用这种方法。例如，const 和 typedef 在默认情况下都是内部链接，可使用 extern 使其变为外部链接。
>
>   然而，extern 有一些复杂 —— 当指定某个名称为 extern 时，编译器将这条语句当作声明而不是定义。**声明**告诉编译器某个符号（变量或函数）的存在，而**定义**是实际分配内存或实现该符号的地方。
>
>   对于变量而言，这意味着编译器不会为这个变量分配空间。必须为这个变量提供单独的、不使用 extern 关键字的定义行。**这意味着该变量或函数是在其他源文件中定义的，编译器需要在链接阶段找到该符号的定义。**例如，下面是 AnotherFile.cpp 的内容：
>
>   ```c++
>   extern int x;  // 只是声明，不分配空间
>   
>   int x = 3;     // 这是定义，x 实际上在这里分配了内存
>   ```
>
>   也可在 extern 行初始化 x，这一行既是声明又是定义：
>
>   ```c++
>   extern int x = 3;
>   ```
>
>   这种情形下的 extern 并不是非常有用，因为 x 默认具有外部链接。当另一个源文件 FirstFile.cpp 使用 x 时，才会真正用到 extern：
>
>   ```c++
>   #include <iostream>
>   
>   extern int x;  // 声明 x，告诉编译器它在其他文件中定义
>   
>   int main()
>   {
>      std::cout << x << std::endl;  // 使用 x
>      return 0;
>   }
>   ```
>
>   FirstFile.cpp 使用了 extern 声明，因此可以使用 x。编译器需要知道 x 的声明，才能在 main() 函数中使用这个变量。然而，如果声明 x 时未使用 extern 关键字，编译器会认为这是定义，因而会为 x 分配空间，导致连接步骤失败(因为有两个全局作用域的 x 变量)。使用 extern，就可在多个源文件中全局访问这个变量。
>
>   **警告：**
>
>   **然而，建议不要使用全局变量。全局变量会让人迷惑，并且很容易出错，尤其是在大型项目中。**

##### 3.函数中的静态变量

>   **C++ 中 static 关键字的最终目的是创建离开和进入作用域时都可以保留值的局部变量。**
>
>   函数中的静态变量就像只能在函数内部访问的全局变量。静态变量最常见的用法就是 “记住” 某个函数是否执行了特定的初始化操作 —— 这意味着当函数多次调用时，静态变量不会重新初始化，它会“记住”上一次的值。
>
>   例如，下面的代码就使用了这一技术：
>
>   ```c++
>   void performTask()
>   {
>      static bool initialized = false;
>      if (!initialized)
>      {
>          cout << "initializing" << endl;
>          // Perform initializing.
>          initializied = true;
>      }
>      // Perform the desired task.
>   }
>   ```
>
>   然而，静态变量容易使人感到迷惑：
>
>   -   **可维护性差**：随着代码变复杂，使用静态变量会让函数的行为更加难以预期，尤其是当其他开发人员或将来自己阅读代码时，很难立即理解静态变量的状态是如何变化的。
>   -   **难以扩展**：一旦对某些局部静态变量的行为有了依赖，重构代码时可能会变得更加复杂。静态变量会在多个函数调用之间共享状态，这种隐式的状态共享不容易跟踪。
>
>   在构建代码时，通常有更好的方法，以避免使用静态变量。在此情况下，可编写一个类，用构造函数执行所需的初始化操作：
>
>   ```c++
>   class TaskPerformer
>   {
>   public:
>       TaskPerformer() : initialized(false)
>       {
>           // 构造函数中执行初始化操作
>           cout << "initializing" << endl;
>           // Perform initializing.
>           initialized = true;
>       }
>   
>       void performTask()
>       {
>           // Perform the desired task.
>           cout << "Task is being performed." << endl;
>       }
>   
>   private:
>       // 作为类内 private 对象进行状态维持
>       bool initialized;
>   };
>   ```
>
>   **注意：**
>
>   **避免使用单独的静态变量，为了维护状态可以改用对象。**
>
>   但有时，它们十分有用，一个例子是实现 Meyer 的 singleton(单例) 设计模式，详见第 29 章。
>
>   **注意：**
>
>   **performTask() 的实现不是线程安全的，它包含了一个竞态条件。在多线程环境中，需要使用原子或其他机制来同步多个线程，多线程详见第 23 章。**

****

#### 2.3非局部变量的初始化顺序

>   在结束讨论静态数据成员和全局变量的主题前，考虑这些变量的初始化顺序。程序中所有的全局变量和类的静态数据成员都会在 main() 函数开始之前初始化。**给定源文件中的变量以在源文件中出现的顺序初始化。**例如，在下面的文件中，Demo::x 一定会在 y 之前初始化：
>
>   ```c++
>   class Demo
>   {
>       public:
>       	static int x;
>   };
>   
>   int Demo::x = 3;
>   int y = 4;
>   ```
>
>   然而，C++ 没有提供规范，用以说明在不同源文件中初始化非局部变量的顺序。如果在某个源文件中有一个全局变量 x，在另一个源文件中有一个全局变量 y，就 **无法知道** 哪个变量先初始化。
>
>   通常，不需要关注这一规范的缺失，但如果某个全局变量或静态变量依赖于另一个变量，就可能引发问题。对象的初始化意味着调用构造函数，全局对象的构造函数可能会访问另一个全局对象，并假定另一个全局对象已经构建。如果这两个全局对象在不同的源文件中声明，就不能指望一个全局对象在另一个全局对象之前构建，也无法控制它们的初始化顺序。不同编译器可能有不同的初始化顺序，即使同一编译器的不同版本也可能如此，甚至在项目中添加另一个源文件也可能影响初始化顺序。
>
>   **警告：**
>
>   **不同源文件中，非局部变量的初始化顺序是不确定的。**

****

#### 2.4非局部变量的销毁顺序

>   **非局部变量按初始化的逆顺序进行销毁。**
>
>   **不同源文件中的非局部变量的初始化顺序是不确定的，所以销毁顺序也是不确定的。**

****

### 11.3类型和类型转换

>   第 1 章回顾了 C++的基本类型，第 8 章讲述了如何利用类编写自己的类型。
>
>   本节讲述类型的一些微妙特征：类型别名、函数指针的类型别名、方法和数据成员的指针的类型别名、typedef 以及类型转换。

****

#### 3.1类型别名

>   类型别名为现有的类型声明提供了新名称。可将类型别名视作为现有类型声明引入同义词的语法(不创建新类型)。下面为 int* 类型声明指定新名称 IntPtr：
>
>   ```c++
>   using IntPtr = int*;
>   ```
>
>   可以互相使用新的类型名和别名定义。例如，以下两行是有效的：
>
>   ```c++
>   int* p1;
>   IntPtr p2;
>   ```
>
>   使用新类型名称创建的变量与使用原始类型声明创建的变量完全兼容。给定上面的定义后，编写下面的代码时完全合法的，因为它们不仅时“兼容的”类型，而且它们本就是同一类型：
>
>   ```c++
>   p1 = p2;
>   p2 = p1;
>   ```
>
>   类型别名最常见的用法时当实际类型的声明过于笨拙时，提供易于管理的名称，这一情形通常出现在模板中。例如，第 1 章介绍了标准库的 std::vector。为声明一个 string 矢量，需要将其声明为 std::vector< std::string >。这是一个模板类，因此想要使用 vector 类型，就要指定模板参数，模板将在 第 12 章详细讨论。在声明变量、指定函数参数等操作中，必须编写 std::vector< std::string >：
>
>   ```c++
>   void processVector(const std::vector<std::string>& vec)
>   {
>       /* omitted*/
>   }
>   
>   int main()
>   {
>       std::vector<std::string> myVector;
>       processVector(myVector);
>       
>       return 0;
>   }
>   ```
>
>   使用类型别名，可创建更简短、有意义的名称：
>
>   ```c++
>   using StringVector = std::vector<std::string>;
>   
>   void processVector(const StringVector& vec)
>   {
>       /* omitted */
>   }
>   
>   int main()
>   {
>       StringVector myVector;
>       processVector(myVector);
>       
>       return 0;
>   }
>   ```
>
>   类型别名可包括作用域限定符。上例显示了这一点，这其中包括 StringVector 的作用域 std。
>
>   标准库广泛使用类型别名来提供类型的简短名称。
>
>   例如，std::string 实际上就是这样的一个类型别名：
>
>   ```c++
>   using string = basic_string<char>;
>   ```

****

#### 3.2函数指针的类型别名

>   我们通常不考虑函数在内存中的位置，但每个函数实际上都位于某个特定地址。
>
>   **在 C++中，可像使用数据那样使用函数。换言之，可使用函数的地址，就像使用变量那样。**
>
>   函数指针的类型取决于兼容函数的参数类型的返回类型。处理函数指针的一种方式是使用类型别名。类型别名允许将一个类型名指定给具有指定特征的一系列函数。例如，下面的代码行定义了 MatchFunction 类型，该类型表示一个指针，这个指针指向具有两个 int 参数并返回布尔值的任何函数：
>
>   ```c++
>   using MatchFunction = bool(*)(int, int);
>   ```
>
>   有了这个新类型，可编写将 MatchFunction 作为参数的函数。例如，以下函数接收两个 int 数组以及其大小，还接收 MatchFunction。它并行迭代数组，并在两个数组的相应元素上调用 MatchFunction。如果调用返回 true，就打印消息。注意，即使将 MatchFunction 作为变量传入，也仍可像普通函数那样调用它：
>
>   ```c++
>   void findMatches(int values1[], int values2[], size_t numValues, MatchFunction matcher)
>   {
>       for (size_t i = 0; i < numValues; i++)
>       {
>           if (matcher(values1[i], values2[i]))
>           {
>               cout << "Match found at position " << i << " (" << values1[i] << ", " << values2[i] << ")" << endl;
>           }
>       }
>   }
>   ```
>
>   注意，该实现要求两个数组至少有 numValues 个元素。要调用 findMatches() 函数，所需要的就是符合所给定的 MatchFunction 类型的任何函数，即接收两个 int 参数并返回布尔值的函数。例如，考虑以下函数，如果两个参数相等，就返回 ture：
>
>   ```c++
>   bool intEqual(int item1, int item2)
>   {
>       return item1 == item2;
>   }
>   ```
>
>   由于 intEqual() 函数与 MatchFunction 类型匹配，可将其作为 findMatches() 的最后一个参数进行传递，如下所示：
>
>   ```c++
>   int arr1[] = {2, 5, 6, 9, 10, 1, 1};
>   int arr2[] = {4, 4, 2, 9, 0, 3, 4};
>   size_t arrSize = std::size(arr1);	// Pre-C++17: sizeof(arr1)/sizeof(arr1[0]);
>   cout << "Calling findMatches() using intEqual():" << endl;
>   findMatches(arr1, arr2, arrSize, &intEqual);
>   ```
>
>   通过地址方式将 intEqual() 函数传入 findMatches() 函数。在技术上，& 字符时可选的，可以只用一个函数名，编译器知道它代表函数的地址。输出如下所示：
>
>   ```c++
>   Calling findMatches() using intEqual():
>   Match found at position 3 (9, 9)
>   ```
>
>   函数指针的好处在于 findMatches() 是比较两个数组中对应值的通用函数。参考上例中的用法，这个函数根据相等性比较两个数组。然而，因为它接收了一个函数指针，所以可根据其他标准进行比较。假如，下面的函数也遵循 MatchFunction 的定义：
>
>   ```c++
>   bool bothOdd(int item1, int item2)
>   {
>       return (item1 % 2 == 1) && (item2 % 2 == 1);
>   }
>   ```
>
>   下面的代码在调用 findMatches() 是使用了 bothOdd：
>
>   ```c++
>   cout << "Calling findMatches() using bothOdd():" << endl;
>   findMatches(arr1, arr2, arrSize, &bothOdd);
>   ```
>
>   输出结果为：
>
>   ```c++
>   Calling findMatches() using bothOdd():
>   Match found at position 3 (9, 9)
>   Match found at position 5 (1, 3)
>   ```
>
>   使用函数指针，可根据 matcher 参数自定义单个 findMatches() 函数的功能。  
>
>   **注意：**
>
>   如果不适用这些旧式的函数指针，还可以使用 std::function，详情参阅第 18 章。
>
>   尽管在 C++中函数指针并不常见(被 virtual 关键字替代)，但在某些情况下还是需要获取函数指针。或许在动态链接库中获取函数指针是最常见的示例。下例获取 Windows DLL 中的一个函数指针。本书讲述与平台无关的 C++, 因此有关 Windows DLL 的细节超出了本书的讨论范围，然而，Windows DLL 对于 Windows 程序员非常重要，因此这个主题值得讨论，通常这也是一个阐述函数指针细节的良好示例。
>
>   考虑一个 DLL(动态链接库)，这个 DLL 有一个名为 Connect() 的函数。只有需要调用 Connect() 时，才会加载这个 DLL。这个在运行时加载的 DLL 由 Windows 的 LoadLibrary() 核心调用完成：
>
>   ```c++
>   HMODULE lib = ::LoadLibrary("hardware.dll");
>   ```
>
>   这个调用的结果就是所谓的“库句柄”，如果发生错误，结果就是 NULL。从库加载函数前，需要知道这个函数的原型。假定下面就是 Connect() 函数的原型，这个函数返回一个整数，接收 3 个参数：一个布尔值、一个整数和一个 C 风格的字符串。
>
>   ```c++
>   int __stdcall Connect(bool b, int n, const char* p);
>   ```
>
>   __stdcall 是 Microsoft 特有的指令，指示如何将参数传递到函数以及如何执行清理。现在可使用类型别名为执行函数的指针定义一个缩写名称(ConnectFunction)，该函数具有前面所示的原型：
>
>   ```c++
>   using Connection = int(__stdcall*)(bool, int, const char*);
>   ```
>
>   在成功加载库并定义函数指针的简短名称后，可获取指向库函数的指针，如下所示：
>
>   ```c++
>   ConnectFunction connect = (ConnectFunction)::GetProAddress(lib, "Connect");
>   ```
>
>   如果这个过程失败，connect 将是 nullptr。如果成功，就可采用以下方式调用被加载的函数：
>
>   ```c++
>   connect(true, 3, "Hello world");
>   ```
>
>   C 程序员可能认为在调用函数前，需要对函数指针进行解引用，如下所示：
>
>   ```c++
>   (*connect)(true, 3, "Hello world");
>   ```
>
>   十几年前确实是这样的，但是现在，所有的 C 和 C++ 编译器都很智能，它们知道如何在调用函数之前对函数指针进行解引用。也就是说，**函数指针会自动解引用，我们可以像使用函数本身那样用它的指针对参数直接处理。**

****

#### 3.3方法和数据成员的指针的类型别名

>   前面讨论了变量及函数的指针，下面考虑类数据成员和方法的指针。
>
>   **在 C++ 中，取得类成员和方法的地址，获得指向它们的指针是完全合法的。**
>
>   **但不能访问非静态成员，也不能在没有对象的情况下调用非静态方法。**
>
>   **类数据成员和方法完全依赖于对象的存在。**
>
>   **因此，通过指针调用方法或访问数据成员时，一定要在对象的上下文中解除对指针的引用。**
>
>   下面举一个例子，使用第 1 章介绍的 Employee 类：
>
>   ```c++
>   Employee employee;
>   int (Employee::*methodPtr) () const = &Employee::getSalary;
>   cout << (employee.*methodPtr)() << endl;
>   ```
>
>   不必担心上述语法。第二行声明了一个指针类型的变量 methodPtr,，该指针指向 Employee 类的一个非静态const 方法，这个方法不接收参数并返回一个 int 值。同时，这行代码将这个变量初始化为指向 Employee 类的 getSalary() 方法。这种语法和声明简单函数指针的语法非常类似，只不过在 *methodPtr 的前面添加了 Employee:: 。**还要注意，在这种情况下需要使用 &。**
>
>   第 3 行代码调用 myCell 对象的 getSalary() 方法(通过 methodPtr 指针)。注意在 employlee.*methodPtr 的周围使用了括号。这些括号是必要的，因为 () 的优先级比 * 高，否则，否则编译器会将 methodPtr 和 () 结合在一起：会试图首先解析 methodPtr()，把它看作是一个函数调用，但 methodPtr() 是一个指向成员函数的指针，而不是一个可直接调用的函数。
>
>   可通过类型别名简化第二行代码：
>
>   ```c++
>   Employee employee;
>   using PtrToGet = int (Employee::*) () const;
>   PtrToGet methodPtr = &Employee::getSalary;
>   cout << (employee.*methodPtr)() << endl;
>   ```
>
>   使用 auto 可进一步简化：
>
>   ```c++
>   Employee employee;
>   auto methodPtr = &Employee::getSalary;
>   cout << (employee.*methodPtr)() << endl;
>   ```
>
>   **注意：**
>
>   **可通过使用 std::mem_fn() 来丢弃 (.*) 语法。第 18 章的函数对象上下文将对此进行解释。**
>
>   方法和数据成员的指针通常不会出现在程序中。然而，要记住，不能再没有的对象的情况下解除对非静态方法或数据成员的指针的引用。有时试图将指向非静态方法的指针传入像 qsort() 这样需要函数指针的函数，但这样是 **不可行** 的。
>
>   **注意：**
>
>   **C++ 允许在没有对象的情况下解除对静态方法或将静态数据成员的指针的引用。**

****

#### 3.4typedef

>   C++11 中介绍了类型别名。在 C++11 之前，可使用 typedef 完成一些类似的工作，但较为复杂。
>
>   与类型别名一样，typedef 为已有的类型声明提供新名称。例如，使用以下类型别名：
>
>   ```c++
>   using IntPtr = int*;
>   ```
>
>   如果不使用类型别名，就必须使用如下 typedef：
>
>   ```c++
>   typedef int* IntPtr;
>   ```
>
>   可以看到，可读性很差！顺序几乎是颠倒的，不过还好吧，但是，由于 typedef 十分复杂，即使专业的 C++ 开发人员有时也会感到困惑，不过，它的行为与类型别名几乎一样。例如，可按如下方式使用 typedef：
>
>   ```c++
>   IntPtr p;
>   ```
>
>   在引入类型别名之前，必须为函数指针使用 typedef，这更复杂了。例如，对以下类型别名：
>
>   ```c++
>   using FunctionType = int(*)(char, double);
>   ```
>
>   如果用 typedef 定义相同的 FunctionType，形式将如下：
>
>   ```c++
>   typedef int (*FunctionType)(char, double);
>   ```
>
>   这非常复杂，因为这玩意 FunctionType 作为声明出来的类型名，竟然位于声明语句中间，这是可读性很差的。
>
>   类型别名和 typedef 并非完全等效。与 typedef 相比，类型别名与模板一起使用时功能更强大；由于涉及有模板的更多细节，这部分将放到第 12 章进行介绍。
>
>   **警告：**
>
>   **始终优先使用类型别名，而非 typedef。**

****

#### 3.5类型转换

>   这一章节内容，曾经多少都有所涉及，但未详述其机理，这一节将详细讲述。
>
>   **C++ 还提供了 4 种类型转换：const_cast()、static_cast()、reinterpret_cast()、dynamic_cast()。**
>
>   使用 () 的 C 风格类型转换在 C++ 种仍然有效，并且在已有的代码种使用广泛。C++ 风格的类型转换包含这 4 种 C++ 类型转换，但较容易出错，因为得到的结果并不注释很明显，也可能得到意想不到的结果。**强烈建议在新代码中仅使用 C++ 风格的类型转换，因为它们更安全，在语法上更优秀。**
>
>   本节讲述这些 C++ 类型转换的目的，并指出使用它们的时机。

##### 1. const_cast()

>   **const_cast() 最直接，可用于给变量添加常量特性，或去掉变量的常量特性。**
>
>   这是上述 4 中类型转换中唯一可舍弃常量特性的类型转换。
>
>   **当然，从理论上讲，并不需要 const 类型转换。如果某个变量是 const，那么应该一直是 const。**
>
>   然而实际中，有时某个函数需要采用 const 变量，但必须将这个变量传递给非 const 变量作为参数的函数。“正确的”解决方案是在程序中保持 const 的一致性，但这并非唯一选择，特别是在使用第三方库时。因此，有时，需要舍弃变量的常量特性，但只有在确保调用的函数不修改对象的情况下才能这么做，否则就只能重新构建程序。下面是一个示例：
>
>   ```c++
>   entern void ThirdPartLibraryMethod(char* str);
>   
>   void f(const char* str)
>   {
>       ThirdPartLibraryMethod(const_cast<char*>(str));
>   }
>   ```
>
>   从 C++17 开始，<utility> 中定义了一个辅助方法 std::as_const()，该方法返回引用参数的 const 引用版本。as_const(obj) 基本等同于 const_cast<const T&>(obj)，其中，T 的类型为 obj。可以看到，与使用 const_cast() 相比，使用 as_const() 更简短。示例如下：
>
>   ```c++
>   std::string str = "C++";
>   const std::string& constStr = std::as_const(str);
>   ```
>
>   **将 as_const() 与 auto 一起使用时要保持警惕。回顾第 1 章可知，auto 将去除引用和 const 限定符！**因此，下面的 result 变量具有类型 std::string 而非 const std::string&：
>
>   ```c++
>   auto result = std::as_const(str);
>   ```
>
>   这里还有就是好像 std::as_const(str) 实现了类似于 std::string_view 的功能，但是，本质上是不同的 —— std::as_const(str) 得到的是常量引用；而 std::string_view 是非拥有引用，这是最本质的区别。

##### 2.static_cast()

>   **可使用 static_cast 显式地执行 C++ 语言直接支持的转换。**
>
>   例如，如果编写了一个算数表达式，其中需要将 int 转换为 double 以避免整除，可以使用 static_cast()，这个示例中，使用了带着参数 i 的 static_cast() 就足够了，因为只要把两个操作数之一设置为 double，就可以确保 C++ 执行浮点数出发：
>
>   ```c++
>   int i = 3;
>   int j = 4;
>   double result = static_cast<double>(i) / j;
>   ```
>
>   如果用户定义了相关的构造函数或转换例程，也可以使用 static_cast() 执行显式转换。例如，如果类 A 的构造函数将类 B 的对象作为参数，就可以使用 static_cast() 将 B 对象转换为 A 对象。许多情况下都需要这一行为，然而编译器会自动执行这一转换，这意味着：
>
>   ```c++
>   class B {};
>   class A {
>   public:
>      A(const B& b) {
>          // 使用 B 的对象构造 A 的对象
>      }
>   };
>   
>   B b;
>   A a = b;  // 这种情况下编译器会隐式调用 A(const B&) 的构造函数
>   
>   
>   B b;
>   A a = static_cast<A>(b);  // 也可以使用 B 的对象显式地构造 A 的对象
>   ```
>
>   static_cast() 的另一种用法是在继承层次中执行向下转换。例如：
>
>   ```c++
>   calss Base
>   {
>      public:
>      	virtual ~Base() = default;
>   };
>   
>   class Derived : public Base
>   {
>      public:
>      	virtual ~Derived() = default;
>   };
>   
>   int main()
>   {
>      Base* b;
>      Derived* d = new Derived();
>      b = d;	// Don't need a cast to go up the inheritance hierarchy
>      d = static_cast<Derived*>(b);	// Need a cast to go down the hierarchy
>   
>      Base base;
>      Derived derived;
>      Base& br = derived;
>      Derived& dr = static_cast<Derived>(br);
>   
>      return 0;
>   }
>   ```
>
>   这种类型转换可以很好地适用于指针和引用(因为不需要真地去分配内存，因此不会出现截断或无法完成初始化的情况)，而不适用于对象本身(需要分配内存，因此可能会截断或无法完成初始化)。
>
>   **注意 static_cast() 类型转换不执行运行间的类型检测。**
>
>   **它允许将任何 Base 指针转换为 Derived 指针，或将 Base 引用转换为 Derived 引用，哪怕在运行时 Base 对象实际上并不是 Derived 对象，也是如此。**
>
>   例如，下面的代码可以编译并执行，但使用指针 d 可能导致灾难性结果，包括内存重写超出对象边界。
>
>   ```c++
>   Base* b = new Base();
>   Derived* d = static_cast<Derived*>(b);
>   ```
>
>   **为执行具有运行时检测功能的更安全的类型转换，可以使用稍后介绍的 dynamic_cast()。**
>
>   static_cast() 并不是全能的。使用 static_cast() 无法将某种类型的指针转换为不相关的其他类型的指针。
>
>   如果没有可用的转换构造函数，static_cast() 无法将某种类型的对象直接转换为另一种类型的对象。
>
>   static_cast() 无法将 const 类型转换为非 const 类型，无法将指针转换为 int。
>
>   **基本上，无法完成 C++ 类型规则认为没意义的转换。**

##### 3.reinterpret_cast()

>   **reinterpret_cast() 的功能比 static_cast() 更强大，同时安全性更差。**
>
>   可以使用它执行一些在技术上不被 C++ 规则允许，但是在某些情况下程序员又需要的类型转换。例如，可将某种引用类型转换为其他引用类型，即使这两个引用并不相关，同样地，可将某种指针类型转换为其他指针类型，即使这两个指针并不存在继承层次上的关系。这种用法经常用于将指针转换为 void* ；这可隐式完成，不需要进行显式转换。但将  void* 指针没有的

****

### 11.4作用域解析

****

### 11.5特征

****

#### 5.1[[noreturn]] 特征

****

#### 5.2[[deprecated]] 特征

****

#### 5.3[[fallthrough]] 特征

****

#### 5.4[[nodiscard]] 特征

****

#### 5.5[[maybe_unused]] 特征

****

#### 5.6供应商专用特性

****

### 11.6用户定义的字面量

****

### 11.7头文件

****

### 11.8 C 的实用工具

****

#### 8.1变长参数列表

****

#### 8.2预处理器宏

****

### 11.9本章小结

****

## 第12章 —— 利用模板编写泛型代码

****

### 12.1模板概述

****

### 12.2类模板

****

#### 2.1编写类模板

****

#### 2.2尖括号

****

#### 2.3编译器处理模板的原理

****

#### 2.4将模板代码分布在多个文件中

****

#### 2.5模板参数

****

#### 2.6方法模板

****

#### 2.7类模板的特例化

****

#### 2.8从类模板派生

****

#### 2.9继承还是特例化

****

#### 2.10模板别名

****

### 12.3函数模板

****

#### 3.1函数模板的特例化

****

#### 3.2函数模板的重载

****

#### 3.3类模板的友元函数模板

****

#### 3.4对模板参数推导的更多介绍

****

#### 3.5模板函数的返回类型

****

### 12.4可变模板

****

### 12.5本章小结

****

## 第13章 —— C++ I/O 揭秘

****

### 13.1使用流

****

#### 1.1流的含义

****

#### 1.2流的来源和目的地

****

#### 1.3流式输出

****

#### 1.4流式输入

****

#### 1.5对象的输入输出

****

### 13.2字符串流

****

### 13.3文件流

****

#### 3.1文本模式和二进制模式

****

#### 3.2通过 seek() 和 tell() 在文件中转移

****

#### 3.3将流链接在一起

****

### 13.4双向 I/O

****

### 13.5本章小结

****

## 第14章 —— 错误处理

****

### 14.1错误与异常

****

#### 1.1异常的含义

****

#### 1.2C++ 中异常的优点

****

#### 1.3我们的建议

****

### 14.2异常机制

****

#### 2.1抛出和捕获异常

****

#### 2.2异常类型

****

#### 2.3按 const 和引用捕获异常对象

****

#### 2.4抛出并捕获多个异常对象

****

#### 2.5未捕获的异常

****

#### 2.6noexcept

****

#### 2.7抛出列表(已赞成使用/已删除)

****

### 14.3异常和多态性

****

#### 3.1标准异常体系

****

#### 3.2在类层次结构中捕获异常

****

#### 3.3编写自己的异常类

****

#### 3.4嵌套异常

****

### 14.4重新抛出异常

****

### 14.5堆栈的释放与清理

****

#### 5.1使用智能指针

****

#### 5.2捕获、清理并重新抛出

****

### 14.6常见的错误处理问题

****

#### 6.1内存分配错误

****

#### 6.2构造函数中的错误

****

#### 6.3构造函数的 function-try-blocks

****

#### 6.4析构函数中的错误

****

### 14.7综合应用

****

### 14.8本章小结

****

## 第15章 —— C++ 运算符重载

****

### 15.1运算符重载概述

****

#### 1.1重载运算符的原因

****

#### 1.2运算符重载的限制

****

#### 1.3运算符重载的选择

****

#### 1.4不应重载的运算符

****

#### 1.5可重载运算符小结

****

#### 1.6右值引用

****

#### 1.7关系运算符

****

### 15.2重载算术运算符

****

#### 2.1重载一元负号和一元正号运算符

****

#### 2.2重载递增和递减运算符

****

### 15.3重载按位运算符和二元逻辑运算符

****

### 15.4重载插入运算符和提取运算符

****

### 15.5重载下标运算符

****

#### 5.1通过 operator[] 提供只读访问

****

#### 5.2非整数数组索引

****

### 15.6重载函数调用运算符

****

### 15.7重载解除引用运算符

****

#### 7.1实现 operator*

****

#### 7.2实现 operator->

****

#### 7.3operator.* 和 operator->* 的含义

****

### 15.8编写转换运算符

****

#### 8.1使用显式转化运算符解决多义性问题

****

#### 8.2用于布尔表达式的转换

****

### 15.9重载内存分配和内存释放运算符

****

#### 9.1new 和 delete 的工作原理

****

#### 9.2重载 operator new 和 operator delete

****

#### 9.3显式地删除/默认化 operator new 和 operator delete

****

#### 9.4重载带有内存大小参数的 operator delete

****

### 15.10本章小结

****

## 第16章 —— C++ 标准库概述

****

### 16.1编码原则

****

#### 1.1使用模板

****

#### 1.2使用运算符重载

****

### 16.2C++ 标准概述

****

#### 2.1字符串

****

#### 2.2正则表达式

****

#### 2.3I/O流

****

#### 2.4智能指针

****

#### 2.5异常

****

#### 2.6数学工具

****

#### 2.7时间工具

****

#### 2.8随机数

****

#### 2.9初始化列表

****

#### 2.10pair 和 tuple

****

#### 2.11optional、variant 和 any

****

#### 2.12函数对象

****

#### 2.13文件系统

****

#### 2.14多线程

****

#### 2.15类型特质

****

#### 2.16标准整数类型

****

#### 2.17容器

****

#### 2.18算法

****

#### 2.19标准库中还缺少什么？

****

### 16.3本章小结

****

## 第17章 —— 理解容器与迭代器

****

### 17.1容器概述

****

#### 1.1对元素的要求

****

#### 1.2异常和错误检查

****

#### 1.3迭代器

****

### 17.2顺序容器

****

#### 2.1vector

****

#### 2.2vector<bool>特化

****

#### 2.3deque

****

#### 2.4list

****

#### 2.5forword_list

****

#### 2.6array

****

### 17.3容器适配器

****

#### 3.1queue

****

#### 3.2priority_queue

****

#### 3.3stack

****

### 17.4有序关联容器

****

#### 4.1pair 工具类

****

#### 4.2map

****

#### 4.3multimap

****

#### 4.4set

****

#### 4.5multiset

****

### 17.5无序关联容器/哈希表

****

#### 5.1哈希函数

****

#### 5.2unordered_map

****

#### 5.3unordered_multimap

****

#### 5.4unordered_set/unordered_multiset

****

### 17.6其他容器

****

#### 6.1标准 C 风格数组

****

#### 6.2string

****

#### 6.3流

****

#### 6.4bitset

****

### 17.7本章小结

****

## 第18章 —— 掌握标准库算法

****

### 18.1算法概述

****

#### 1.1find() 和 find_if() 算法

****

#### 1.2accumulate() 算法

****

#### 1.3在算法中使用移动语义

****

### 18.2std::function

****

### 18.3lambda 表达式

****

#### 3.1语法

****

#### 3.2泛型 lambda 表达式

****

#### 3.3lambda 捕捉表达式

****

#### 3.4将 lambda 表达式作为返回类型

****

#### 3.5将 lambda 表达式用作参数

****

#### 3.6标准库算法示例

****

### 18.4函数对象

****

#### 4.1算术函数对象

****

#### 4.2比较函数对象

****

#### 4.3逻辑函数对象

****

#### 4.4按位函数对象

****

#### 4.5函数对象适配器

****

#### 4.6std::invoke()

****

#### 4.7编写自己的函数对象

****

### 18.5算法详解

****

#### 5.1迭代器

****

#### 5.2非修改序列算法

****

#### 5.3修改序列算法

****

#### 5.4操作算法

****

#### 5.5交换算法

****

#### 5.6分区算法

****

#### 5.7排序算法

****

#### 5.8二叉树搜素算法

****

#### 5.9集合算法

****

#### 5.10最大/最小算法

****

#### 5.11并行算法

****

#### 5.12数值处理算法

****

### 18.6算法示例：审核选民登记

****

#### 6.1选民登记审核问题描述

****

#### 6.2auditVoterRolls() 函数

****

#### 6.3getDuplicates() 函数

****

#### 6.4测试 auditVoterRolls() 函数

****

### 18.7本章小结

****

## 第19章 —— 字符串的本地化与正则表达式 

****

### 19.1本地化

****

#### 1.1本地化字符串字面量

****

#### 1.2宽字符

****

#### 1.3反西方字符集

****

#### 1.4转换

****

#### 1.5locale 和 facet

****

### 19.2正则表达式

****

#### 2.1ECMAScript 语法

****

#### 2.2regex 库

****

#### 2.3regex_match() 方法

****

#### 2.4regex_search() 方法

****

#### 2.5regex_iterator

****

#### 2.6regex_token_iterator

****

#### 2.7regex_replace()

****

### 19.3本章小结

****

## 第20章 —— 其他库工具

****

### 20.1ratio 库

****

### 20.2chrono 库

****

#### 2.1持续时间

****

#### 2.2时钟

****

#### 2.3时点

****

### 20.3生成随机数

****

#### 3.1随机数引擎

****

#### 3.2随机数引擎适配器

****

#### 3.3预定义的随机数引擎和引擎适配器

****

#### 3.4生成随机数

****

#### 3.5随机数分布

****

### 20.4optional

****

### 20.5variant

****

### 20.6any

****

### 20.7元组

****

#### 7.1分解元组

****

#### 7.2串联

****

#### 7.3比较

****

#### 7.4make_from_tuple()

****

#### 7.5apply()

****

### 20.8文件系统支持库

****

#### 8.1path

****

#### 8.2directory_entry

****

#### 8.3辅助函数

****

#### 8.4目录迭代

****

### 20.9本章小结

****