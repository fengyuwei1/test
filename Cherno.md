# Cherno C++

## 1.C++是如何工作的

c++是一种高级语言，我们写的c++代码并不能直接让计算机的cpu明白我们要干什么，必须通过编译器和链接器进行编译和链接后才能得到可以运行的二进制文件。

（1）编译 ：把文本形式的源代码翻译成机器语言，并形成目标文件。
（2）连接 ：把目标文件 操作系统的启动代码和库文件组织起来形成可执行程序。

值得注意的是c++并不关心文件，所有的文件如（.cpp .h）仅仅只是为了给c++提供源码，如果是.cpp那么就按照普通的c++文件进行编译，如果是.h就按照头文件的方式进行编译，如果你喜欢你可以自己造一个.zhangsan文件，只要你告诉编译器像处理.cpp一样处理.zhangsan就好了。

每一个.cpp都会在编译阶段被编译成独立的.obj文件，但.h并不会被编译成.obj，因为.h会在预处理的时候过“#include”命令包含进.cpp中。当每一个.cpp都被编译成独立的.obj时，链接器就会开始将这些.obj链接起来，组合成一个可运行的.exe。

### 1. 预处理

编译大概可以分为两个阶段，第一个阶段是预处理阶段，这个阶段会进行一些文本替换，会生成不含#指令的.i文件，预处理命令以#开头。该阶段会拷贝#include里的内容到cpp中，进行宏定义#define的替换，和条件编译指令如#if，#ifdef，#endif等。

#### 1.1 #include的替换

上面有提到“.h并不会被编译成.obj，因为.h会在预处理的时候通过“#include”命令包含进.cpp中”，当编译器注意到#include时，它会进入xxxx.h，阅读其中的代码并将其全部拷贝到.cpp文件中。
\#include的实质就是将它所包含的头文件里的所有的代码全部复制到.cpp文件中。

#### 1.2 宏定义#define的替换

#### 1.3 条件编译指令

### 2.编译

当预处理结束后编译器就会创建一个抽象语法树，并通过这个抽象语法树开始实际生成可被cpu执行的机器代码。

### 3.main函数

- main函数被称作程序的**入口点**（entry point），因为**程序是从main函数处开始执行的**

### 4.链接

每一个源文件（就是.c文件，上图中的程序1）都有对应的零碎文件（就是.h文件），通过预编译（通过#include实现）把.c和.h文件整合成一个组合C文件，这个组合C文件的扩展名为.i。把组合C文件编译成汇编文件.s，目标文件为机器指令（放在一个.o文件当中），单个目标文件是不能工作的，因为各个目标文件是相互支撑工作的。

把各个目标文件整合的过程就叫链接过程。整合后的文件就叫可执行程序，windows后缀为.exe，Linux后缀为.out

## 2.编译器是如何工作的

C++编译器唯一要做的是把文本变为中继格式---obj

编译器产出obj时会做许多事：

1.预处理代码(#include,#define,#if,#pragma)

2.标记解释和解析

3.编译器就会创建一个抽象语法树，并通过这个抽象语法树开始实际生成可被cpu执行的机器代码

C++根本不在乎文件，文件这种东西在C++里不存在

文件只是用来给编译器提供源码的某种方法

## 3.链接器是如何工作的

链接是一个过程，主要的焦点是找到每个符号和函数在哪里，并把它们连接起来

.exe文件有一个入口点，入口点正确才能链接，入口点不一定是main()函数，只要有一个入口点就行了

 从源C++文件到实际的可执行的二进制文件，有两个阶段过程：
  • 第一阶段是编译源文件
  • 第二阶段就是链接，链接的主要作用是找到每个符号和函数在哪里，并把他们链接起来
• 每个cpp文件，都会编译生成单独的目标文件，有单独的编译单元，链接器的作用就是将多个目标文件链接起来，生成最终的可执行文件
• include预处理语句，会将包含的头文件内容拷贝到目标文件中进行编译，需要注意函数重复定义

## 4.C++变量

不同变量类型之间的唯一区别：在C++中是大小(这个变量会占用多少内存)

变量的大小实际上取决于编译器的不同

int数据类型的意思在一定范围内存储整数(int--4字节)

unsigned表示无符号类型

char -- 1字节

short -- 2字节

long -- 4字节

long long -- 8字节

float -- 4字节

double -- 8字节

float与double的区别在于变量后面是否加上f，如:

```c
float a = 5.5f;
double b = 5.2;
```

bool一般返回1(0代表false，除0之外的任何数字，都是true)

bool需要一个比特，但是分配的任然是一个字节

sizeof操作符 -- 查看数据类型的大小

## 5.C++函数

使用函数避免代码重复

在一个运行的程序中，为了调用一个函数，会创建一个堆栈结构

主函数可以没有返回值，它会自动返回一个0(return 0)

函数示例：

```c++
int Multiply(int a, int b)
{
	return a * b;
}
int main()
{
	int result = Multiply(3, 2);
	std::cout << result << std::endl;
	std::cin.get();
}
```

## 6.C++头文件

头文件通常用于声明某些类型的函数，以便它们能够被使用在程序中

定义函数只能定义一次

因为头文件通过#include来实现，所以#include具有复制和粘贴的能力

任何以#开头的东西被称为预处理器命令或预处理器指令

#pragma once本质上是一个被发送到编译器或预处理器的预处理指令，作用是只包括这个文件一次，监督这个文件，阻止我们单个头文件多次被包含，并转换为单个翻译单元

## 7.在visual studio中调试代码

重要的两点：

断点和读取内存

断点是程序中调试器将中断的点(Fn+F9)

### 更改执行流

当调试执行到 21 行时，想要回到前面的行，只需要抓住黄色箭头拖动其回到前面的行（如 18 行）即可从那里开始执行
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/1f15c38a8360fcaa4677c886d0363837.png)

### 断点

当我们需要在代码执行的过程中，从某条语句开始，停下来一步一步，一条一条地过每一条代码的时候，这是我们就需要用到断点。

### 基本的断点操作

1.设置基本断点
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/e8675dab5ac5546f100e76ebfba54a4f.png)

如上图，在你需要停下来的语句中，在其左侧的那条竖栏处左击，就会出现一个红色圆点，这表示当你运行代码的时候（不是运行 .exe 程序）会在这里停下来。

【注】程序只会从断点开始的地方停下来，而之前的语句将会快速执行过去

2.进入调试
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/074f307fab0e9e74166a5ba22ebd91a6.png)

按上图红框所示，进入调试状态。

3.调试界面简述

![img](https://i-blog.csdnimg.cn/blog_migrate/0b3d7a9ee5d5757583558bb9e8e3844f.png)

在调试程序启动后，程序快速运行至 ① 处停下等候你的下一步操作，可以看见，红色的 ① 上面多了一个黄色的向右箭头，这表示当前程序运行到了这条语句。

② 处有三个操作符：
向下的箭头表示，进入更深层次的代码中。比如，当黄色箭头运行到一个调用的函数时，我想进入看看这个函数内部究竟是怎么运行的，就可以用这个箭头。

弯曲向下的箭头表示在当前程序中一条一条执行。那上一个箭头中的例子举例，我并不想进入这个调用的函数，仅仅想在当前页面执行函数，就用这个箭头。

向上的箭头，表示跳出更深层次的代码。还是那最开始的例子举例，如果你进入了更深层次的函数中，但这个函数太冗长了，你想跳出来，回到本来执行的页面，就应该用这个箭头。

③ 处有一个红色的方框，这表示停止调试，退出调试。

④ 处，可以看到下面有两个输出数据的框。如果你仔细观察，这些框的底部还有一排隐藏的框，比如 Autos 的右边还有 Locals，Watch1 这些隐藏起来的框。这些输出框可以帮助你进行调试。
Fn+Fn11断点移动

## 8.C++条件与分支

当我们运行我们写的if语句时，先是对实际condition(条件语句)的评估，然后是基于这个条件语句评估后的分支语句

0是false，其他数为true

if会占用内存和cpu，尽量少用

else if是一种巧妙的隐藏语法，实际上是两个分开的语句，它不是关键字

示例：

```c++
int main()
{
	int a = 8;
	/*if (a == 8)
	{
		std::cout << a << std::endl;
		Log("hello world");
		std::cout << "hello world" << std::endl;
	}*/
	bool comparisonReasult = a == 8;
	if (comparisonReasult)
	{
		std::cout << "hello world" << std::endl;
	}
	std::cin.get();
}
```



## 9.C++循环(for,while)

for(变量的声明;一个条件(只要条件的结果为真，就将执行for循环内部的代码);最后这部分会在for循环的下一次迭代之前被调用)

注：这样也行

```c
int main()
{
	int i = 0;
	for (; i < 5;)
	{
		i++;
		std::cout << "hello world" << std::endl;
	}
}
```

while(条件(只要为真就一直循环))

```c
int main()
{
	int i = 0;
	while (i < 5)
	{
		std::cout << "hello world" << std::endl;
		i++;
	}
}
```

do-while(不管如何，循环体必须先执行一次)

```c
int main()
{
	int i = 6;
	do {
		std::cout << "hello world" << std::endl;
	} while (i < 5);
}
```

## 10.C++循环流语句(continue,break,return)

continue只能在循环中使用，表示进入这个循环的下一个迭代

break主要运用于循环中，意思是跳出循环，也就是终止循环

return可用方面很多，可用作函数返回值等

## 11.C++指针(原始指针)

指针是一个内存地址，是一个保存内存地址的整数
内存地址0不是有效的内存地址，不能从内存地址0中读取或者写入。指针被赋予0，意味着这个指针是无效的

指针本身也是变量

示例：

```c
int main()
{
	int var = 8;
	void* ptr = &var;
	//double* ptr2 = (double*)&var;
	*(int*)ptr = 10;
	std::cout << *(int*)ptr << std::endl;
	char* buffer = new char[8];
	memset(buffer, 0, 8);
	delete[] buffer;
}
```

memset()函数介绍

```c
void *memset(void *str, int c, size_t n)
```

- 解释：复制字符 c（一个无符号字符）到参数 str 所指向的字符串的前 n 个字符。
- 作用：是在一段内存块中填充某个给定的值，它是对较大的结构体或数组进行清零操作的一种最快方法
- 头文件：C中`#include<string.h>`，C++中`#include<cstring>`

看着介绍其实函数作用非常简单，就是用于初始化，但是需要注意的是memset赋值的时候是按字节赋值，是将参数化成二进制之后填入一个字节。就比如前面的例子中，想要通过memset(a,100,sizeof a)给int类型的数组赋值，你给第一个字节的是一百，转成二进制就是0110 0100，而int有四个字节，也就是说，一个int被赋值为
0110 0100,0110 0100,0110 0100,0110 0100，对应的十进制是1684300900，根本不是你想要赋的值100，这也就解释了为什么数组中的元素的值都为1684300900。

## 12.C++引用

引用通常只是指针的伪装

这是一种我们引用现有变量的方式

引用必须是已经存在的变量，引用本身并不是新的变量

引用不占用内存，也没有真正的存储空间

在 C++ 中，**引用** 提供了对已存在变量的别名或另一种名称。与指针不同，指针存储变量的地址，而引用直接指向另一个变量。一旦引用被初始化，它就不能再被更改为指向其他变量。

引用使用 `&` 符号来声明。其语法如下：

```c++
类型 &引用名 = 变量名;
```

**类型**：要引用的变量的数据类型。

**引用名**：引用的名称。

**变量名**：引用所指向的变量。

示例：

```c++
void Increment(int& value)
{
	value++;
}
int main()
{
	int a = 5;
	int* b = &a;
	Increment(a);
	int& ref = a;
	std::cout << a << std::endl;
}
```

## 13.C++类

类只是对数据和功能组合一起的一种方法

由类类型构成的变量称为对象，新的对象变量称为实例

类内的函数被称为方法

## 14.类与结构体的对比

基本上没有什么区别，默认情况下，类是私有的，而结构体是公开的

```c++
struct ve2
{
	int x, y;
};
void print(struct ve2& vec)
{
	vec.x = 1;
	vec.y = 2;
	std::cout << vec.x << " " << vec.y << std::endl;
}
int main()
{
	struct ve2 vec;
	vec.x = 1;
	vec.y = 2;
	print(vec);
	std::cin.get();
}
```

## 15.如何写一个C++类

实例：

```c++
class LOG
{
public:
	const int LogLevelError = 0;
	const int LogLevelWarning = 1;
	const int LogLevelInfo = 2;
private:
	int m_LogLevel = LogLevelInfo;
public:
	void SetLevel(int level)
	{
		m_LogLevel = level;
	}
	void error(const char* message)
	{
		if(m_LogLevel >= LogLevelError)
		std::cout << "[error]:" << message << std::endl;
	}
	void warning(const char* message)
	{
		if(m_LogLevel >= LogLevelWarning)
		std::cout << "[warning]:" << message << std::endl;
	}
	void info(const char* message)
	{
		if(m_LogLevel >= LogLevelInfo)
		std::cout << "[info]:" << message << std::endl;
	}
};
int main()
{
	LOG log;
	log.SetLevel(1);
	log.warning("hello");
	std::cin.get();
}
```

## 16.C++中的静态(static)

static在C++中有两个意思，其中之一是在类或结构体外部使用static关键字，另一种是在类或结构体内部使用static

类外面的static，意味着你声明为static的符号，链接将只是在内部，你只能对定义它的翻译单元可见

而类或结构体内部的static意味着该变量实际上将与类的所有实例共享内存，静态变量在你在类中创建的所有实例中

静态变量只有一个实例

在类或结构体外的static,会使静态变量被限制在所在的文件中

## 17.C++类和结构体中的静态(static)

实例：

```c++
struct Entity
{
	static int x, y;
	static void print()
	{
		std::cout << x << ',' << y << std::endl;
	}
};
int Entity::x;
int Entity::y;
int main()
{
	Entity e;
	Entity::x = 2;
	Entity::y = 3;
	Entity e1;
	Entity::x = 5;
	Entity::y = 8;
	Entity::print();
	Entity::print();
	std::cin.get();
}
```

`static int x, y;`：`x` 和 `y` 是静态成员变量，这意味着它们是 `Entity` 类所有实例共享的。也就是说，无论你创建多少个 `Entity` 对象，所有对象共享同一个 `x` 和 `y` 变量。

`static void print()`：这是一个静态成员函数。静态函数可以直接访问静态成员变量（如 `x` 和 `y`），并且可以在没有实例的情况下被调用（例如通过 `Entity::print()` 方式调用）

```c++
int Entity::x;
int Entity::y;
```

这里定义了 `x` 和 `y` 的实际存储空间。因为静态成员变量在类外部定义，所以需要在类定义外部为它们分配内存空间，并初始化它们。此时，`x` 和 `y` 的初始值是未定义的，可能是任何值。

`Entity e;` 和 `Entity e1;`：创建了两个 `Entity` 的实例 `e` 和 `e1`。由于 `x` 和 `y` 是静态变量，所以无论创建多少个 `Entity` 对象，`x` 和 `y` 都是全局共享的变量，所有实例共享同一个 `x` 和 `y`。

`Entity::x = 2;` 和 `Entity::y = 3;`：通过类名直接访问并修改静态变量 `x` 和 `y` 的值。此时，`x = 2`，`y = 3`。

`Entity::x = 5;` 和 `Entity::y = 8;`：再一次通过类名直接访问并修改静态变量 `x` 和 `y`。此时，`x` 被修改为 `5`，`y` 被修改为 `8`。因为 `x` 和 `y` 是静态的，所有 `Entity` 实例都看到这些更改。

`Entity::print();`：调用 `print` 函数，输出当前 `x` 和 `y` 的值。因为上一步将 `x` 和 `y` 分别设置为 `5` 和 `8`，所以这将输出 `5,8`。

`Entity::print();`：再次调用 `print` 函数，结果依然是 `5,8`。

## 18.C++中的局部静态(Local Static)

生存期指的是变量实际存在的时间

变量的作用域是指我们可以访问变量的范围

静态局部变量允许我们声明一个变量，他的生存期基本上相当于整个函数，它的作用范围被限制在这个函数内

实例：

```c++
void Function()
{
	int i = 0;
	i++;
	std::cout << i << std::endl;
}
int main()
{
	Function();
	int i = 10;
	Function();
}
```

## 19.C++枚举

枚举实际上就是一个数值集合

枚举默认从0开始递增

实例：

```c++
enum  Example : unsigned char
{
	a, b, c, d, e, f
};
int main()
{
	Example value = b;
	if (value == 1)
	{
		std::cout << "yes" << std::endl;
	}
}
```

## 20.C++构造函数

构造函数是一种特殊类型的方法，这是一种每次你构造一个对象时都会调用的方法

实例：

```c++
class Entity
{
public:
	float x, y;
	Entity()
	{
		x = 0.0f;
		y = 0.0f;
	}//构造函数
	Entity(float x,float y)
	{
		y = y;
		x = x;
	}//构造函数
	/*void init()
	{
		x = 0.0f;
		y = 0.0f;
	}*/
	void Print()
	{
		std::cout << x << " " << y << std::endl;
	}
};
int main()
{
	Entity e(1.0,10.1);
	e.Print();
	std::cin.get();
}
```

## 21.C++祈构函数

祈构函数是在销毁对象时运行的

祈构函数是你卸载变量等东西，并清理你使用过的内存

祈构函数同时适用于栈和堆分配的对象

调用祈构函数并不会销毁对象

实例：

```c++
class Entity
{
public:
	float x, y;
	Entity()
	{
		x = 0.0f;
		y = 0.0f;
		std::cout << "created Entity!" << std::endl;
	}//构造函数
	//Entity(float x,float y)
	//{
	//	y = y;
	//	x = x;
	//}//构造函数
	/*void init()
	{
		x = 0.0f;
		y = 0.0f;
	}*/
	~Entity()
	{
		std::cout << "Destroyed Entity!" << std::endl;
	}//祈构函数
	void Print()
	{
		std::cout << x << " " << y << std::endl;
	}
};
void function()
{
	Entity e;
	e.Print();
	e.~Entity();
}
int main()
{
	function();
	std::cin.get();
}
```

## 22.C++继承

继承允许我们有一个相互关联的类的层次结构

它允许我们有一个包含公共功能的基类，然后从基类分离出来，从最初的父类中创建子类

实例：

```c++
class Entity
{
public:
	float x, y;
	void Move(float xa, float ya)
	{
		x += xa;
		y += ya;
	}
};
class Player:public Entity
{
public:
	void print()
	{
		std::cout << x << " " << y << std::endl;
	}
};
int main()
{
	class Player p;
	p.x = 1.1f;
	class Entity a;
	a.x = 1.1f;
	a.y = 2.1f;
	std::cout << a.x << " " << a.y << std::endl;
 	p.print();
	std::cin.get();
}
```

## 23.C++虚函数

虚函数允许我们在子类中重写方法。

虚函数引入了一种叫做动态联编的东西，通过v表进行编译，可以通过映射找到相应的虚函数

override可以用来检验虚函数的错误

```c++
class Entity
{
public:
	virtual std::string Getname() { return "Entity"; }
};
class Player :public Entity
{
private:
	std::string name;
public:
	Player(const std::string& m_name) :name(m_name){}
		std::string Getname()override
		{
			return name; 
		}
};
int main()
{
	Entity* e = new Entity();
	std::cout << e->Getname() << std::endl;
	Player* p = new Player("cherno");
	std::cout << p->Getname() << std::endl;
	Entity* a = p;
	std::cout << a->Getname() << std::endl;
	std::cin.get();
}
```

## 24.C++接口(纯虚函数)

纯虚函数允许我们在基类中定义一个没有实现的函数，然后强制子类去实现该函数。

类中的接口只包含未实现的方法作为模板。

实例：

```c++
class Entity
{
public:
	virtual std::string Getname() = 0;
};
class Player :public Entity
{
private:
	std::string m_name;
public:
	Player(const std::string& name):m_name(name){}
	std::string Getname()override { return m_name; }
	
};
void Printname(Entity* entity)
{
	std::cout << entity->Getname() << std::endl;
}
int main()
{
	Entity* e = new Player("hello");
	Printname(e);
	Player* p = new Player("cherno");
	Printname(p);
	std::cin.get();
}
```

## 25.C++可见性

可见性是一个属于面向对象编程的概念，他指的是类的某些成员或方法实际上有多可见。

C++有三个基础的可见符：

1.public(不论怎么样都可以使用)

2.private(只要出了所在的类外就是不可见的)

3.protected(在所在的类和继承的类中都可以使用)

实例：

```c++
class Entity
{
private:
	int x, y;
	void print(){}
protected:
	int a, b;
public:
	Entity()
	{
		x = 0;
		print();
	}
};
class Player :public Entity
{
public:
	Player()
	{
		a = 1;//可以实现
		//x = 0;
		//print();
	}
};
int main()
{
	Entity e;
	//e.x = 2;//private的值在类外不可访问
	std::cin.get();
}
```

## 26.C++数组

数组是元素的集合，按照一定的顺序排列在一起。

它们连续存储数据。

```c++
int main()
{
	int example[5];
	example[0] = 2;
	example[4] = 4;
	std::cout << example[0] << std::endl;
	std::cout << example << std::endl;
	for (int i = 0; i < 5; i++)
	{
		std::cout << example[i] << std::endl;
	}
	int* ptr = example;
	example[2] = 5;
	*(example + 2) = 6;
	int* another = new int[5];
	delete[] another;
	std::cin.get();
}
```

## 27.C++字符串

字符串：一个接一个字符的一组字符。

字符串能够表示和处理文本的方法

```C++
int main()
{
	//const char* name = "cherno";
	//std::cout << sizeof(name) << std::endl;
	//std::string name = "hello";
	std::string name = std::string("cherno") + "hello!";
	std::cout << name.size() << std::endl;
	std::cout << sizeof(name) << std::endl;
	std::cin.get();
}
```

## 28.C++字符串字面量

字符串字面量：在双引号之间的一串字符。

字符串字面量是存储在内存的只读部分。

字符串字面量永远保存在内存的只读区域内。

实例：

```c++
int main()
{
	using namespace std::string_literals;
	std::string name0 = std::string("cherno") + "hello";
	std::string name1 = "cherno"s + "hello";
	const char* name = "cherno";
	//name[2] = 'a';不能进行修改
	const wchar_t* name2 = L"cherno";//宽字符
	const char* example = R"(Line1 line2 line3 \t)";//忽视转义字符
	std::cout << strlen(name) << std::endl;
	std::cin.get();
}
```

## 29.C++中的CONST

const只是声明变量的一个方式，他告诉变量值不可被修改

实例：

```c++
class Entity
{
private:
	int m_x, m_y;
public:
	int Getx()const
	{
		return m_x;
	}
	void setx(int x)
	{
		m_x = x;
	}
};
int main()
{
	//const int a = 5;
	//a = 2;不能进行改变
	const int MAX_AGE = 90;
	//const int* a = new int;//不能改变指针指向的内容
	//int* const a = new int;//不能改变指针指向内容的值
	//*a = 2;
	//a = (int*)&MAX_AGE;

	std::cin.get();
}
```

## 30.C++的mutable关键字

mutable的两种用途：1.与const结合使用，2.在lambda表达式中使用

mutable的意思是可改变的，可以把const转换为变量。

实例：

```c++
class Entity
{
private:
	std::string m_name;
	mutable int m_Debugcount = 0;
public:
	const std::string& Getname()const
	{
		m_Debugcount++;
		return m_name;
	}
	void print()
	{
		std::cout << m_Debugcount << std::endl;
	}
};
int main()
{
	const Entity e;
	e.Getname();
	int x = 8;
	auto f = []()
		{
			std::cout << "hello" << std::endl;
		};//lambda表达式

	std::cin.get();
}
```

## 31.C++的成员初始化列表

在构造函数中初始化一个类成员有两种方法。

第一种方法：

```c++
class Entity
{
private:
	std::string m_name;
public:
	Entity()
	{
		m_name = "Unknown";
	}
	Entity(const std::string& name)
	{

	}
	const std::string& Getname()const { return m_name; }
};
int main()
{
	Entity e0;
	std::cout << e0.Getname() << std::endl;
	Entity e1("cherno");
	std::cout << e1.Getname() << std::endl;
	std::cin.get();
}
```

第二种方法：

```c++
class Entity
{
private:
	std::string m_name;
	int m_score;
public:
	Entity():m_name("Unkown"),m_score(0)
	{
		
	}
	Entity(const std::string& name):m_name(name)
	{

	}
	const std::string& Getname()const { return m_name;   }
};
```

注意：在做成员初始化列表时，要与成员变量声明时的顺序一致。

## 32.C++中的三元操作符

(关系表达式) ? 表达式1 : 表达式2;
int x = 10;
int y = 5;
int z;
如果x大于y 则是true，将x赋值给z；
如果x不大于y 则是false，将y赋值给z；
z = (x > y) ? x : y;
System.out.println("x = " + x);

实例：

```c++
static int s_Level = 1;
static int s_Speed = 2;
int main()
{
	s_Speed = (s_Level > 5) ? 10 : 5;
	std::cin.get();
}
```

## 33.创建并初始化C++对象

### 33.1 在栈上

当在栈上创建对象时，对象的生命周期由其作用域决定。对象在其所在的代码块（通常是函数或控制结构）中创建，当代码块执行结束时，对象会自动销毁。这意味着栈上创建的对象的生命周期是自动管理的，您不需要手动释放内存。

### 33.2 在堆上

当在堆上创建对象时，对象的生命周期不受其作用域的限制。使用`new`关键字在堆上创建对象时，对象会一直存在，直到您使用`delete`关键字手动释放内存。这意味着您需要自己管理堆上创建的对象的生命周期。

```c++
class Entity
{
private:
	std::string m_name;
public:
	Entity():m_name("Unknown"){}
	Entity(const std::string& name):m_name(name){}
	const std::string& Getname()const { return m_name; }
};
void Function()
{
	int a = 2;
	Entity entity = Entity("Cherno");
}
int main()
{
	Function();
	//Entity entity;//在栈上创建
	Entity* entity = new Entity("cherno");//在堆上创建
	std::cout << entity->Getname() << std::endl;
	delete entity;
	std::cin.get();
}
```

## 34.C++ new关键字

它会在一行内存中找到4个字节的地址空间，并返回一个指向这个内存的指针。

它是在堆上创建的,实际上就相当于malloc的用法。

实例：

```c++
int main()
{
	Function();
	//Entity entity;//在栈上创建
	Entity* entity = new Entity("cherno");//在堆上创建
	std::cout << entity->Getname() << std::endl;
	delete entity;
	int a = 2;
	int* b = new int;
	*b = 2;
	delete b;
	std::cin.get();
}
```

## 35.C++隐式转换与explicit关键字

C++运行隐式进行转换，而不需要用cast做强制转换。

C++只能做一次隐式转换。

explicit用来禁用隐式转换，如果有这个关键字，就没有隐式转换。

实例：

```c++
class Entity
{
private:
	std::string m_name;
	int m_age;
public:
	explicit Entity(const std::string& name):m_name(name)//禁用隐式转换
	{

	}
	Entity(int age) :m_name("nkown"), m_age(age)
	{

	}
};
int main()
{
	Entity a("cherno");//隐式转换
	//Entity a = "cherno";
	Entity b = Entity(22);//隐式转换
	std:: cin.get();
}
```

## 36.C++运算符及其重载

运算符是我们使用的一种符号。

运算符重载用的非常少，应该在完全有意义的情况下使用。

运算符重载实际上就是一个函数。

运算符重构：

```c++
struct vector2
{
	float x, y;
	vector2(float x, float y):x(x),y(y){}
	vector2 Add(const vector2& other)const
	{
		return vector2(x + other.x, y + other.y);
	}
	//运算符重构
	vector2 operator+(const vector2& other)const
	{
		return Add(other);
	}
};
int main()
{
	vector2 position(4.0f, 4.0f);
	vector2 speed(0.5f, 1.5f);
	vector2 result = position+speed;
	std::cout << result.x << " " << result.y << std::endl;
}
```

## 37.C++中的this关键字

通过this，可以访问成员函数。

this是一个指向当前对象实例的指针。

实例：

```c++
class Entity
{
public:
	int x, y;
	Entity(int x, int y):x(x),y(y)
	{
		Entity* const& e = this;
	}
	int Get()const
	{
		return this->x;
	}
};
int main()
{
	Entity e(1,2);
	e.Get();
}
```

## 38.C++的对象生存期(栈作用域生存期)

栈可以被认为是一种数据结构。

基于栈的变量，在我们一出作用域就被释放了。

实例：

```c++
class Entity
{
public:
	Entity()
	{
		std::cout << "created Entity!" << std::endl;
	}
	~Entity()
	{
		std::cout << "finished Entity!" << std::endl;
	}
};
//int* CreateArray()
//{
//	int array[50];
//	return array;
//}这个是错误的，因为是在栈上创建的，所以会被销毁
int* CreateArray()
{
	int* array = new int[50];
	return array;
}
int main()
{
	int* a = CreateArray();
	{
		Entity* e = new Entity();
	}
	std::cin.get();
}
```

## 39.C++的智能指针

智能指针是实现这一过程(new和delete)自动化的一种方式。

智能指针本质上是一个原始指针的包装。

智能指针 --- unique_ptr,他是作用域指针，是超出作用域时，他会自动销毁。它不能复制。

实例：

```c++
#include <memory>
class Entity
{
public:
	Entity()
	{
		std::cout << "Created Entity" << std::endl;
	}
	~Entity()
	{
		std::cout << "Destroyed Entity" << std::endl;
	}
	void Print(){}
};
int main()
{
	{
		//std::unique_ptr<Entity> entity(new Entity());
		std::unique_ptr<Entity> entity = std::make_unique<Entity>();
		std::shared_ptr<Entity>sharedEntity = std::make_shared<Entity>();//共享指针，可以被多个指针指向。
		entity->Print();
	}
	std::cin.get();
}
```

## 40.C++中的复制和拷贝构造函数

拷贝指的是要求复制数据，复制内存

实例1：

```c++
struct vector2
{
	float x, y;
};
int main()
{
	vector2* a = new vector2();
	vector2* b = a;//copy 内存指向的是同一个地方

	std::cin.get();
}
```

实例2(用类来实现复制):

```c++
class String
{
private:
	char* m_buffer;
	unsigned int m_size;
public:
	String(const char* string)
	{
		m_size = strlen(string);
		m_buffer = new char[m_size+1];
		memcpy(m_buffer, string, m_size+1);
		m_buffer[m_size] = 0;
	}
	~String()
	{
		delete[] m_buffer;
	}
	friend std::ostream& operator<<(std::ostream& stream, const String& string);
};
std::ostream& operator<<(std::ostream& stream, const String& string)
{
	stream << string.m_buffer;
	return stream;
}
int main()
{
	String string = "cherno";
	String second = string;
	std::cin.get();
}
```

深拷贝：复制一个内存块，但希望第二个字符串有自己的指针，以拥有自己唯一的内存块，当修改这个指针时，之前被复制的指针不会发生变化。

实例3(深拷贝)：

```c++
class String
{
private:
	char* m_buffer;
	unsigned int m_size;
public:
	String(const char* string)
	{
		m_size = strlen(string);
		m_buffer = new char[m_size+1];
		memcpy(m_buffer, string, m_size+1);
		m_buffer[m_size] = 0;
	}
	//String(const String& other) = delete;
	String(const String& other)
	{
		m_size = other.m_size;
		m_buffer = new char[m_size + 1];
		memcpy(m_buffer, other.m_buffer, m_size + 1);
	}//深拷贝
	~String()
	{
		delete[] m_buffer;
	}
	friend std::ostream& operator<<(std::ostream& stream, const String& string);
};
std::ostream& operator<<(std::ostream& stream, const String& string)
{
	stream << string.m_buffer;
	return stream;
}
int main()
{
	String string = "cherno";
	String second = string;
	std::cin.get();
}
```

## 41.C++的箭头操作符

实例：

```c++
class Entity
{
public:
	int x;
public:
	void Print()const
	{
		std::cout << "hello!" << std::endl;
	}
};
class ScopedPtr
{
private:
	Entity* m_obj;
public:
	ScopedPtr(Entity* entity):m_obj(entity)
	{

	}
	~ScopedPtr()
	{
		delete m_obj;
	}
	/*Entity* GetObject()
	{
		return m_obj;
	}*/
	Entity* operator->()
	{
		return m_obj;
	}
};
int main()
{
	/*Entity e;
	e.Print();
	Entity* ptr = &e;
	Entity& entity = *ptr;
	ptr->Print();*///(*ptr).Print();
	/*ptr->x = 2;*/
	ScopedPtr entity = new Entity();
	//entity.GetObject()->Print();
	entity->Print();
	std::cin.get();
}
```

## 42.C++的动态数组(std::vector)

vector与数组的不同是：它可以调整数组大小。

它初始时没有固定的大小。

实例：

```c++
#include <vector>
struct Vertex
{
	float x, y, z;
};
std::ostream& operator<<(std::ostream& stream, const Vertex& vertex)
{
	stream << vertex.x << "," << vertex.y << "," << vertex.z;
	return stream;
}
int main()
{
	//Vertex* vertices = new Vertex[5];
	std::vector<Vertex>vertices;
	vertices.push_back({ 1,2,3 });
	vertices.push_back({ 4,5,6 });
	for (int i = 0; i < vertices.size(); i++)
	{
		std::cout << vertices[i] << std::endl;
	}
	vertices.clear();
	std::cin.get();
}
```

## 43.C++的std::vector使用优化

优化：

```c++
#include <vector>
struct Vertex
{
	float x, y, z;
	Vertex(float x, float y, float z) :x(x), y(y), z(z)
	{

	}
	Vertex(const Vertex& vertex):x(vertex.x),y(vertex.y),z(vertex.z)
	{
		std::cout << "Copied!" << std::endl;
	}
};

int main()
{
	//Vertex* vertices = new Vertex[5];
	std::vector<Vertex>vertices;
	vertices.reserve(3);
	vertices.emplace_back(Vertex(1,2,3));
	vertices.emplace_back(Vertex(4,5,6));
	vertices.emplace_back(Vertex(7, 8, 9));
	std::cin.get();
}
```

## 44.C++中使用库(静态链接)

在实际解决方案中的实际项目文件夹中，保留使用的库的版本。

以二进制文件的形式进行链接，而不是获取实际依赖库的源代码并自己编译。

动态链接与静态链接的区别：

1.静态链接意味着这个库会被放到你的可执行文件中，他在你的exe文件中。

2.动态链接库是在运行时被链接的，你可以选择在程序运行时，装载动态链接库。

3.主要区别是：库文件是否被编译到exe文件中或链接到exe文件中，还是只是一个单独的文件中。

右键点击解决方案，打开属性，在C/C++中改变常规的文件指向，在编译器中也要改变指向。

实例：

```c++
#include "GLFW/glfw3.h"
int main()
{
	int a = glfwInit();
	std::cout << a << std::endl;
	std::cin.get();
}
```

## 45.C++中使用动态库

静态链接可以允许更多的优化。

把glfw3.lib换为glfw3dll.lib。

把glfw3.dll放到debug里面。

## 46.C++中创建与使用库

建立两个在同一根目录下的项目，一个项目为.exe可执行文件，一个项目为.lib文件。.exe文件为主体，.lib文件是创建库所用的项目。

注意：要链接完成还需要在引用里的另一个项目配置好。

具体看：VS中看cherno创建与使用库这个解决方案。

## 47.C++中如何处理多返回值

### 1. 使用 `std::tuple`

C++11 引入了 `std::tuple`，它允许你将多个返回值打包在一起。

实例：

```c++
#include <iostream>
#include <tuple>

std::tuple<int, double, std::string> getValues() {
    return std::make_tuple(42, 3.14, "Hello");
}

int main() {
    auto [i, d, s] = getValues(); // C++17 解构绑定
    std::cout << "int: " << i << ", double: " << d << ", string: " << s << std::endl;
    return 0;
}
```

### 2.使用 `std::pair`

如果只需要返回两个值，可以使用 `std::pair`。

实例：

```c++
#include <iostream>
#include <utility>  // for std::pair

std::pair<int, double> getPair() {
    return {42, 3.14};
}

int main() {
    auto [i, d] = getPair(); // C++17 解构绑定
    std::cout << "int: " << i << ", double: " << d << std::endl;
    return 0;
}
```

### 3.通过指针或引用参数

你可以通过函数参数返回多个值，使用指针或引用来修改传入的参数。

实例：

```c++
#include <iostream>

void getValues(int& i, double& d) {
    i = 42;
    d = 3.14;
}

int main() {
    int i;
    double d;
    getValues(i, d);
    std::cout << "int: " << i << ", double: " << d << std::endl;
    return 0;
}
```

### 4.使用自定义结构体或类

如果返回值有逻辑上的关联，可以创建一个结构体或类来封装这些返回值。

实例：

```c++
#include <iostream>

struct Values {
    int i;
    double d;
    std::string s;
};

Values getValues() {
    return {42, 3.14, "Hello"};
}

int main() {
    Values vals = getValues();
    std::cout << "int: " << vals.i << ", double: " << vals.d << ", string: " << vals.s << std::endl;
    return 0;
}
```

### 5.使用 `std::vector` 或其他容器

当返回的多个值是同一种类型时，可以使用 `std::vector`、`std::array` 等标准容器。

实例：

```c++
#include <iostream>
#include <vector>

std::vector<int> getValues() {
    return {1, 2, 3, 4, 5};
}

int main() {
    std::vector<int> values = getValues();
    for (int value : values) {
        std::cout << value << " ";
    }
    std::cout << std::endl;
    return 0;
}
```

### 注意：

#### 1.std::pair

`std::pair` 是一个用于存储两个值的模板类，这两个值可以是不同类型的。可以使用 `std::make_pair` 或直接用构造函数初始化它。

实例：

```c++
#include <iostream>
#include <utility>  // std::pair

std::pair<int, double> getPair() {
    return std::make_pair(42, 3.14);  // 通过 std::make_pair 创建
}

int main() {
    std::pair<int, double> p = getPair();  // 返回 std::pair
    std::cout << "First: " << p.first << ", Second: " << p.second << std::endl;
    return 0;
}
```

**说明：**

- **`std::pair<T1, T2>`**：表示一个包含两个值的模板类，`T1` 和 `T2` 分别是两个值的类型。
- **`p.first` 和 `p.second`**：分别访问 `pair` 中的第一个和第二个元素。
- **`std::make_pair`**：用来简化 `std::pair` 的创建，也可以直接使用构造函数。

#### 2.std::tuple

`std::tuple` 是一个可以存储多个不同类型元素的模板类，适合需要返回多个值的情况。`std::tuple` 支持任意多个元素.

实例：

```c++
#include <iostream>
#include <tuple>
#include <string>

std::tuple<int, double, std::string> getTuple() {
    return std::make_tuple(42, 3.14, "Hello");
}

int main() {
    std::tuple<int, double, std::string> t = getTuple();  // 返回 std::tuple
    std::cout << "First: " << std::get<0>(t) << ", Second: " << std::get<1>(t)
              << ", Third: " << std::get<2>(t) << std::endl;
    return 0;
}
```

**说明：**

- **`std::tuple<T1, T2, T3, ...>`**：表示一个可以包含多个不同类型元素的模板类，`T1`, `T2`, `T3` 是元素的类型。
- **`std::get<N>(tuple)`**：通过索引 `N` 获取 `tuple` 中的第 `N` 个元素（注意：索引是从 0 开始的）。
- **`std::make_tuple`**：用来创建 `std::tuple`，类似于 `std::make_pair`

## 48.C++的模板

模板有点像宏。

模板允许你定义一个可以根据你的用途进行编译的模板。

只有当它基于模板的使用情况，发送到编译器，进行编译后，才会具体化为真正的代码。

实例1：

```c++
template<typename T>
void Print(T value)
{
	std::cout << value << std::endl;
}
int main()
{
	Print(5);
	Print("hello");
	//Print<int>(5);
	std::cin.get();
}
```

实例2：

```c++
template<typename T,int N>
class Array
{
private:
	int m_Array[N];
public:
	int Getsize()const { return N; }
};
int main()
{
	Array<int,5> array;
	std::cout << array.Getsize() << std::endl;
	std::cin.get();
}
```

## 49.C++的堆与栈内存的比较

栈通常是一个预定义大小的内存区域，通常约为2兆字节左右。

堆也是一个预定义了默认值的区域，但是它可以增长。

这两个的储存位置是一样的，都在我们的内存中。

## 50.C++的宏

在C++中使用预处理器来宏化某些操作。

预处理阶段基本上是一个文本编辑阶段。

写一些宏，将代码中的文本替换为其他东西。

Debug:不会优化代码

Relese:会优化代码

实例：

```c++
#define WAIT std::cin.get()
int main()
{
	WAIT;
}
```

实例：

```c++
#define MAIN int main()\
{\
	std::cin.get();\
}

MAIN;
```

## 51.C++的auto关键字

auto可以自动匹配变量的数据类型。

弱化了数据类型。

它没有改变api，会导致有时使用函数时出现问题。

实例1：

```c++
int main()
{
	auto a = 5L;
	auto b = a;
	std::cout << b << std::endl;
	std::cin.get();
}
```

实例2：

```c++
std::string Getname()
{
	return "cherno";
}
int main()
{
	auto name = Getname();
	int a = name.size();
	std::cout << a << std::endl;
	std::cin.get();
}
```

## 52.C++的静态数组(std::array)

这个库用来处理静态数组。

静态数组指的是不增长的数组。

```c++
#include <array>
void PrintArray(std::array<int,5>& data)
{
	for (int i = 0; i < data.size();)
	{

	}
}
int main()
{
	std::array<int,5> data;
	data.size();
	data[0] = 2;
	data[4] = 1;
	/*int dataOld[5];
	dataOld[0];*/
	std::cin.get();
}
```

## 53.C++的函数指针

```c++
void HelloWorld()
{
	std::cout << "Hello World!" << std::endl;
}
int main()
{
	//void(*function)();//这个就是auto的类型
	auto function = &HelloWorld;//这是在取得函数指针
	function();
	function();
	std::cin.get();
}
```

## 54.C++的lambda

lambda的本质是我们定义的一种叫做匿名函数的方式。

只要你有一个函数指针，你都可以使用匿名函数。

lambda是我们不需要通过函数定义，就可以定义一个函数的方法。

```c++
#include <vector>
#include <algorithm>
void forEach(const std::vector<int>& values, void(*func)(int))
{
	for (int value : values)
	{
		func(value);
	}
}
int main()
{
	std::vector<int> values = { 1,2,3,4,5 };
	auto lambda = [](int value) {std::cout << "value: " << value << std::endl; };
	forEach(values,lambda);
	std::cin.get();
}
```

注：使用原始函数指针时，不能进行值传递或引用传递。

**lambda的用法：**

```c++
[capture](parameters) -> return_type {
    // function body
}
```

**组件说明**

1. **捕获列表 (`capture`)**：

   - 这部分定义了如何访问外部变量。你可以使用 

     ```
     &
     ```

      引用捕获，或者使用 

     ```
     =
     ```

      值捕获。例如：

     - `[]`：不捕获任何变量。
     - `[x]`：按值捕获变量 `x`。
     - `[&x]`：按引用捕获变量 `x`。
     - `[=]`：按值捕获所有外部变量。
     - `[&]`：按引用捕获所有外部变量。

2. **参数列表 (`parameters`)**：

   - 和普通函数一样，可以定义输入参数。可以省略，如果不需要参数。

3. **返回类型 (`return_type`)**：

   - 可以指定返回类型，通常可以省略，编译器会自动推断。

4. **函数体**：

   - Lambda 函数的实际代码块。

可以使用 `std::function` 将 Lambda 赋值给函数指针或存储在其他容器中。

## 55.C++的using namespace std

为什么不用using namespace std？

区别标准库和其他库的区别。

在不同的命名空间下写代码时可以识别出来。

在不同环境下写的代码可能与理想的状态不同。

## 56.C++的名称空间

在同一空间下，我们不能有两个相同的符号。

名称空间的主要目的是避免命名冲突。

要用到某个名称空间时，你只需要写上::,然后就进入到这个名称空间。

```c++
#include <string>
#include <algorithm>
namespace apple {
	void print(const char* text)
	{
		std::cout << text << std::endl;
	}
}
namespace orange
{
	void print(const char* text)
	{
		std::string temp = text;
		std::reverse(temp.begin(), temp.end());
		std::cout << temp << std::endl;
	}
}
int main()
{
	apple::print("hello");
	orange::print("hello");
	std::cin.get();
}
```

## 57.C++的线程

C++ 的线程是由标准库 `<thread>` 提供的，通过多线程的方式可以让程序并行执行多个任务，从而提高效率，特别是在处理 I/O 密集型或 CPU 密集型任务时。线程可以被用来执行独立的任务，并且每个线程都有自己的执行路径，但它们共享同一个进程的内存空间。

**基本概念**

- **线程（Thread）** 是进程中的一个执行单元，线程共享进程的内存空间和资源。
- **多线程编程** 是指在一个程序中创建多个线程，使它们可以并行执行不同的任务。
- **主线程（Main thread）** 是程序一开始运行时默认的线程，通常在主线程中创建其他子线程。

**创建线程**

在 C++11 标准中，引入了 `std::thread` 来处理多线程，使用非常方便。创建一个线程非常简单，可以通过将一个函数传递给 `std::thread` 来启动新的线程。

**重要成员函数**

- **`join()`**：主线程等待子线程完成，只有子线程结束后主线程才能继续执行。如果不调用 `join()` 或 `detach()` 会导致程序崩溃。
- **`detach()`**：将线程与主线程分离，线程将在后台独立运行，主线程无需等待它结束。

实例：

```c++
#include <thread>
static bool s_Finished = false;
void Dowork()
{
	using namespace std::literals::chrono_literals;
	while (!s_Finished)
	{
		std::cout << "working..\n";
		std::this_thread::sleep_for(1s);
	}
}
int main()
{
	std::thread worker(Dowork);
	std::cin.get();
	s_Finished = true;
	worker.join();
	std::cin.get();
}
```

## 58.C++的计时

想要知道计算机程序运行的具体时间---C++标准库

实例：

```c++
#include <chrono>
#include <thread>
int main()
{
	using namespace std::literals::chrono_literals;
	auto start = std::chrono::high_resolution_clock::now();
	std::this_thread::sleep_for(1s);
	auto end = std::chrono::high_resolution_clock::now();
	std::chrono::duration<float> duration = end - start;
	std::cout << duration.count() << std::endl;
	std::cin.get();
}
```

## 59.C++的多维数组

二维数组是数组的集合。

```c++
int main()
{
	int* array = new int[50];
	int** a2d = new int*[50];
	a2d[0] = nullptr;
	for (int i = 9; i < 50; i++)
	{
		a2d[i] = new int[50];
	}
	a2d[0][0] = 0;
	for (int i = 0; i < 50; i++)
	{
		delete[] a2d[i];
	}
	delete[] a2d;
	std::cin.get();
}
```

## 60.C++的排序

实例：

```c++
#include <vector>
#include <algorithm>
int main()
{
	std::vector<int> values = { 3,4,1,2,5 };
	std::sort(values.begin(), values.end(),std::greater<int>());
	for (int value : values)
	{
		std::cout << value << std::endl;
	}
}
```

## 61.C++的类型双关

在 C++ 中，**类型双关**（Type Punning）是指通过一种类型的变量访问另一种类型的内存数据。类型双关通常涉及使用指针或联合体，来绕过 C++ 中的类型系统，直接访问内存中的字节。这种操作有时用于优化或低层次编程，但可能引发未定义行为，尤其是在涉及不同的数据类型时。

### 常见的类型双关手法

#### 1. 使用联合体（`union`）

联合体是 C++ 中的一个工具，允许在同一内存地址上存储不同的数据类型。通过联合体，可以通过访问其中一个成员的数据，来解释为另一种类型的数据。

```c++
#include <iostream>

union TypePunning {
    int i;
    float f;
};

int main() {
    TypePunning pun;
    pun.i = 0x40490FDB;  // 这是浮点数 π 的位模式
    std::cout << pun.f << std::endl;  // 输出的是 float 类型的值：π (~3.14159)
    return 0;
}
```

#### 解释：

- 这里通过将整数赋值给 `pun.i`，然后读取联合体中的 `pun.f`，实现了通过整数值访问浮点数表示的类型双关。

#### 2. 使用指针强制转换

C++ 中可以通过强制转换指针的类型来实现类型双关。

```c++
#include <iostream>

int main() {
    int x = 65;
    char* p = reinterpret_cast<char*>(&x);
    std::cout << *p << std::endl;  // 输出：A （65 对应的 ASCII 字符）
    return 0;
}
```

#### 解释：

- 这里将 `int` 类型的变量 `x` 的地址强制转换为 `char*`，然后通过 `p` 读取 `x` 的第一个字节。这种方式可以用来直接访问不同数据类型的内存表示。

### 类型双关的风险

虽然类型双关在某些场合（如低级编程或硬件访问）很有用，但它通常会带来未定义行为。特别是在 C++ 中，以下情况可能会导致问题：

- **平台差异**：不同数据类型的内存布局和对齐要求可能因平台而异。
- **类型别名规则（Strict Aliasing Rule）**：C++ 中有严格的别名规则，规定不同类型的指针不能指向同一块内存，否则会导致编译器优化失效，从而产生未定义行为。

### 安全替代方案

为了避免类型双关引发的未定义行为，可以使用 `std::memcpy` 来实现不同类型间的内存拷贝：

```c++
#include <iostream>
#include <cstring>

int main() {
    float f = 3.14159;
    int i;
    std::memcpy(&i, &f, sizeof(f));  // 安全地将 float 转换为 int
    std::cout << std::hex << i << std::endl;  // 输出 16 进制表示
    return 0;
}
```

#### 解释：

- 使用 `std::memcpy` 可以安全地将一种类型的二进制表示复制到另一种类型的内存区域，从而实现类型双关的效果，而不违反 C++ 的类型系统规则。

### 总结

类型双关是一种通过直接访问内存的低级技术，可以用于特定的优化或硬件编程场景。常见的手段包括联合体和指针强制转换，但应谨慎使用，避免违反 C++ 的类型别名规则，导致未定义行为。安全的替代方案是使用 `std::memcpy`。

实例1：

```c++
struct Entity
{
	int x, y;
};
//int main()
//{
//	int a = 50;
//	double& value = *(double*)&a;
//	value = 0.0;
//	std::cout << value << std::endl;
//	std::cin.get();
//}
int main()
{
	Entity e = { 5,8 };
	int* position = (int*)&e;
	std::cout << position[0] << position[1] << std::endl;
	std::cin.get();
}
```

## 62.C++的联合体

联合体有点像结构体类型，但是它一次只能占用一个成员的内存。

联合体不能使用虚方法。

通常union是匿名使用的，但是匿名union不能含有成员函数。

实例：

```c++
#include <iostream>

union TypePunning {
    int i;
    float f;
};

int main() {
    TypePunning pun;
    pun.i = 0x40490FDB;  // 这是浮点数 π 的位模式
    std::cout << pun.f << std::endl;  // 输出的是 float 类型的值：π (~3.14159)
    return 0;
}
```

## 63.C++的虚祈构函数

C++中的**虚析构函数**（Virtual Destructor）是与继承和多态密切相关的一个概念，用于确保在通过基类指针或引用删除派生类对象时，正确调用派生类的析构函数，从而避免资源泄露或未释放动态内存。

例如：

```c++
#include <iostream>

class Base {
public:
    Base() {
        std::cout << "Base Constructor\n";
    }
    ~Base() {
        std::cout << "Base Destructor\n";
    }
};

class Derived : public Base {
public:
    Derived() {
        m_array = new int[5];
        std::cout << "Derived Constructor\n";
    }
    ~Derived() {
        delete[] m_array;
        std::cout << "Derived Destructor\n";
    }
private:
    int* m_array;
};

int main() {
    Base* poly = new Derived();
    delete poly;  // 问题出现在这里
    return 0;
}
```

`Derived`类的析构函数**没有被调用**，导致`Derived`类中的动态内存没有被释放。这是因为`Base`类的析构函数**不是虚函数**，编译器只会调用`Base`类的析构函数，而不会管`Derived`类的析构函数。

为了避免这种情况，应该将基类的析构函数声明为**虚函数**，这样在使用基类指针删除派生类对象时，会先调用派生类的析构函数，再调用基类的析构函数。

例如：

```c++
#include <iostream>

class Base {
public:
    Base() {
        std::cout << "Base Constructor\n";
    }
    virtual ~Base() {  // 虚析构函数
        std::cout << "Base Destructor\n";
    }
};

class Derived : public Base {
public:
    Derived() {
        m_array = new int[5];
        std::cout << "Derived Constructor\n";
    }
    ~Derived() {
        delete[] m_array;
        std::cout << "Derived Destructor\n";
    }
private:
    int* m_array;
};

int main() {
    Base* poly = new Derived();
    delete poly;  // 现在会正确调用Derived的析构函数
    return 0;
}
```

现在，程序会首先调用`Derived`类的析构函数，然后调用`Base`类的析构函数，正确地释放了`Derived`类的资源。

## 64.C++的类型转换

C++是强类型语言，意味着存在一个类型系统，并且类型是强制的。

在C++中，类型转换有四种专门的风格，用于取代传统的C风格的类型转换。它们分别是：

1. `static_cast`
2. `dynamic_cast`
3. `const_cast`
4. `reinterpret_cast`

### 1. `static_cast`

`static_cast`用于在相关类型之间进行显式类型转换，比如在基本数据类型之间转换、父类与子类之间的转换等。它是最常用的类型转换。

#### 用途：

- 基本类型之间的转换（如`int`到`float`）。
- 指针类型之间的转换（在类的继承体系中，将基类指针转换为派生类指针，反之亦然）。
- 去除类型上的`const`限定符时（若不想使用`const_cast`）

实例：

```c++
int main() {
    int a = 10;
    double b = static_cast<double>(a); // 将int转换为double
    std::cout << b << std::endl;

    Base* base = new Derived(); // 基类指针指向派生类
    Derived* derived = static_cast<Derived*>(base); // 安全的向下转换
    return 0;
}
```

### 2. `dynamic_cast`

`dynamic_cast`用于在类的继承体系中，进行安全的类型转换，主要用于向下转型（从基类指针或引用转换为派生类指针或引用）。它使用**运行时类型识别**（RTTI）来确保转换的安全性。

#### 用途：

- 在类层次结构中，将基类指针或引用转换为派生类指针或引用。
- 只有当基类有至少一个**虚函数**时，才能使用`dynamic_cast`。

实例:

```c++
class Base {
public:
    virtual ~Base() {} // 必须有虚函数
};

class Derived : public Base {
public:
    void show() {
        std::cout << "Derived class\n";
    }
};

int main() {
    Base* base = new Derived();
    Derived* derived = dynamic_cast<Derived*>(base); // 向下转换
    if (derived) {
        derived->show();
    } else {
        std::cout << "Conversion failed\n";
    }
    return 0;
}
```

### 3. `const_cast`

`const_cast`用于添加或移除对象的`const`属性。它是唯一能够操作`const`属性的类型转换。

#### 用途：

- 将`const`对象转换为非`const`，以便对其进行修改（尽量避免这种情况，可能导致未定义行为）。
- 将非`const`对象转换为`const`，以确保不对其进行修改。

实例：

```c++
void print(const int* p) {
    // 这里的p是const指针，不能修改*p
}

int main() {
    const int a = 10;
    int* b = const_cast<int*>(&a); // 移除const属性
    *b = 20; // 可能导致未定义行为，因为a本来是const
    return 0;
}
```

### 4. `reinterpret_cast`

`reinterpret_cast`用于重新解释对象的位模式，可以进行几乎任意类型的转换，但通常用于**指针**之间的转换。它的主要作用是告诉编译器将一种类型的位模式解释为另一种类型。

#### 用途：

- 将指针转换为其他不相关类型的指针（如`int*`到`char*`）。
- 将指针转换为整数类型，反之亦然（不常用，且可能与不同系统的字长有关）。

实例：

```c++
int main() {
    int a = 65;
    char* p = reinterpret_cast<char*>(&a); // 将int*转换为char*
    std::cout << *p << std::endl; // 输出 'A'，因为65的ASCII码是'A'

    long addr = reinterpret_cast<long>(&a); // 将指针转换为整数
    std::cout << "Address: " << addr << std::endl;
    return 0;
}
```

案例实例：

```c++
int main()
{
	/*int a = 5;
	double value = a;*/
	/*double value = 5.25;
	int a = (int)value;*/
	double value = 5.25;
	double a = (int)(value + 5.3);
	double s = static_cast<int>(value) + 5.3;
	std::cout << a << std::endl;
	std::cin.get();
}
```

## 65.条件与操作断点

条件断点：内存中的某些东西满足了我的条件，那就触发这个断点。

操作断点：允许我们采取某种动作，一般是在碰到断点时打印一些东西到控制台。

两种类型的断点：

让你在打印你想要的东西时继续执行或者打印一些东西到控制台，但仍然中断程序，暂停程序的执行。

具体使用可以百度。

## 66.现代C++的安全以及如何教授

安全编程：我们希望降低崩溃，内存泄漏，非法访问等问题。

智能指针和自动内存管理系统的存在使程序员的生活更容易。

## 67.C++的预编译头文件

预编译的头文件：实际上是让你抓取一堆头文件，并将它们转换成编译器可以使用的格式，而不必一遍又一遍地读取这些头文件。

预编译头文件以二进制格式存取，这对编译器来说比单纯的文本处理要快得多。

注意：不要将频繁更改的文件放入预编译头文件中。

预编译头文件真正有用的是外部依赖。

具体使用时再去搜索。

## 68.C++的基准测试

在 C++ 中进行基准测试，可以使用标准库中的 `chrono` 库，它提供了用于高精度计时的工具，能够测量代码执行的时间。我们可以通过 `chrono` 记录代码块的起始时间和结束时间，然后计算它们之间的差值。以下是更详细的步骤与示例。

### 1. `chrono` 库概述

`chrono` 库是 C++11 引入的时间处理库，包含了高精度的计时工具。它有三个主要的时钟类型：

- **`system_clock`**：表示系统时钟，通常用于获取当前的系统时间。
- **`steady_clock`**：表示单调时钟，时间流逝不会被调整（例如系统时间更改），适合做基准测试。
- **`high_resolution_clock`**：高分辨率时钟，精度最高，但通常是 `steady_clock` 或 `system_clock` 的别名。

### 2.基准测试的步骤

1. **记录起始时间**：在代码块开始时记录起始时间。
2. **执行代码**：运行你想要测量的代码。
3. **记录结束时间**：在代码块结束时记录结束时间。
4. **计算时间差**：用结束时间减去起始时间，计算执行时间。

**实例：**

```c++
#include <memory>
#include <chrono>
class Timer
{
public:
	Timer()
	{
		std::chrono::high_resolution_clock::now();
	}
	~Timer()
	{
		stop();
	}
	void stop()
	{
		auto endTimepoint = std::chrono::high_resolution_clock::now();
		auto start = std::chrono::time_point_cast <std::chrono::microseconds>(m_StartTimepoint).time_since_epoch().count();
		auto end = std::chrono::time_point_cast <std::chrono::microseconds>(endTimepoint).time_since_epoch().count();
		auto duration = end - start;
		double ms = duration * 0.001;
		std::cout << duration << "us (" << ms << "ms)\n";

	}
private:
	std::chrono::time_point < std::chrono::high_resolution_clock > m_StartTimepoint;
};
int main()
{
	int value = 0;
	{
		Timer timer;
		for (int i = 0; i < 100000; i++)
		{
			value += 2;
		}
	}
	std::cout << value << std::endl;
	__debugbreak();//在这里中断编译
}
```

###  3.详细解释

- **`high_resolution_clock::now()`**：这是 `chrono` 中提供的获取当前时间的函数，精度取决于系统，可以使用 `high_resolution_clock` 或 `steady_clock`。
- **`duration_cast<milliseconds>`**：用于将计时的结果转换为毫秒（或其他单位，如秒、微秒等）。`milliseconds` 是一种单位类型。
- **`duration.count()`**：这是获取时间差的实际数值。

## 69.C++的结构化绑定

C++ 的 **结构化绑定（Structured Bindings）** 是 C++17 引入的一种语言特性，旨在简化从复杂类型中解构出多个值的过程，类似于其他编程语言中的解构赋值。这一特性使得可以轻松地将元组、对、数组等类型中的元素分解为单独的变量，从而提高代码的可读性和简洁性。

### 1. 结构化绑定的基本语法

结构化绑定的语法非常直观，通过 `auto` 关键字和花括号 `{}`，将右值解构到多个局部变量中：

```c++
auto [a, b] = some_pair;  // 解构 some_pair 到 a 和 b
```

其中，`some_pair` 可以是支持结构化绑定的任何类型，如元组、对、数组或自定义类。

### 2. 适用于哪些类型

结构化绑定主要适用于以下几类类型：

- **`std::tuple` 和 `std::pair`**：标准库中的元组和对。
- **数组**：定长数组或 C 风格数组。
- **类或结构体**：如果类支持解构。
- **返回多个值的函数**：通过返回元组或对的函数。

### 3. 使用 `std::pair` 进行结构化绑定

`std::pair` 是 C++ 标准库中的二元组，结构化绑定可以很方便地将 `std::pair` 的两个元素解构为两个独立的变量。

```c++
#include <iostream>
#include <utility>  // for std::pair

int main() {
    std::pair<int, std::string> my_pair = {1, "Hello"};

    // 结构化绑定
    auto [id, message] = my_pair;

    std::cout << "ID: " << id << ", Message: " << message << std::endl;

    return 0;
}
```

在这个例子中，`my_pair` 包含一个整数和一个字符串，通过结构化绑定，将其解构为 `id` 和 `message` 两个局部变量。

### 4. 使用 `std::tuple` 进行结构化绑定

`std::tuple` 是标准库提供的多元组，结构化绑定也同样适用于元组。

```c++
#include <iostream>
#include <tuple>  // for std::tuple

int main() {
    std::tuple<int, double, std::string> my_tuple = {1, 2.5, "Hello"};

    // 结构化绑定
    auto [id, value, message] = my_tuple;

    std::cout << "ID: " << id << ", Value: " << value << ", Message: " << message << std::endl;

    return 0;
}
```

在这里，`my_tuple` 包含三个元素，通过结构化绑定，可以将其分解为三个独立的局部变量 `id`、`value` 和 `message`。

### 5. 数组的结构化绑定

结构化绑定同样适用于定长数组或 C 风格数组。

```c++
#include <iostream>

int main() {
    int my_array[3] = {1, 2, 3};

    // 结构化绑定
    auto [x, y, z] = my_array;

    std::cout << "x: " << x << ", y: " << y << ", z: " << z << std::endl;

    return 0;
}
```

数组的结构化绑定要求数组的大小是已知的，绑定时必须提供足够的变量来匹配数组中的每个元素。

### 6. 自定义类型的结构化绑定

C++17 允许你为自定义类和结构体启用结构化绑定，只要它们符合某些要求即可。具体来说，结构体中的成员必须是 `public` 且类型支持访问，或者通过特殊函数提供解构功能.

```c++
#include <iostream>

struct Point {
    int x;
    int y;
};

int main() {
    Point p = {10, 20};

    // 结构化绑定
    auto [x, y] = p;

    std::cout << "x: " << x << ", y: " << y << std::endl;

    return 0;
}
```

在这个例子中，`Point` 是一个简单的结构体，包含两个 `public` 成员变量 `x` 和 `y`，通过结构化绑定可以直接将这两个成员解构出来。

### 7. 结构化绑定与 `const` 以及引用

结构化绑定支持 `const` 和引用绑定，如果希望绑定后的变量保持常量或引用特性，可以使用 `const` 或 `&`。

```c++
#include <iostream>
#include <tuple>

int main() {
    std::tuple<int, std::string> my_tuple = {1, "Hello"};

    // 结构化绑定为常量
    const auto [id, message] = my_tuple;

    // id 和 message 是 const 类型，无法修改
    // id = 2;  // 错误

    std::cout << "ID: " << id << ", Message: " << message << std::endl;

    return 0;
}
```

示例（常量绑定）：

```c++
#include <iostream>
#include <tuple>

int main() {
    std::tuple<int, std::string> my_tuple = {1, "Hello"};

    // 结构化绑定为常量
    const auto [id, message] = my_tuple;

    // id 和 message 是 const 类型，无法修改
    // id = 2;  // 错误

    std::cout << "ID: " << id << ", Message: " << message << std::endl;

    return 0;
}
```

示例（引用绑定）：

```c++
#include <iostream>
#include <tuple>

int main() {
    std::tuple<int, std::string> my_tuple = {1, "Hello"};

    // 结构化绑定为引用
    auto& [id, message] = my_tuple;

    // 修改引用
    id = 2;
    message = "World";

    std::cout << "ID: " << id << ", Message: " << message << std::endl;

    return 0;
}
```

在引用绑定中，修改绑定后的变量会直接影响原始对象。

### 8. 注意事项

- 结构化绑定只能用于 C++17 及其后续版本。如果你使用的编译器不支持 C++17，结构化绑定将无法工作。
- 结构化绑定要求绑定的变量数必须与解构对象的元素数一致。否则会出现编译错误。

### 9. 实际应用场景

结构化绑定可以应用在多种场景中，尤其是在 STL 中的迭代器、返回多个值的函数或与其他标准库类型交互时，例如：

#### 应用在 `std::map` 的遍历中：

```c++
#include <iostream>
#include <map>

int main() {
    std::map<int, std::string> my_map = {{1, "One"}, {2, "Two"}, {3, "Three"}};

    // 使用结构化绑定遍历 std::map
    for (const auto& [key, value] : my_map) {
        std::cout << "Key: " << key << ", Value: " << value << std::endl;
    }

    return 0;
}
```

在这种场景中，结构化绑定大大简化了代码的可读性，不需要显式地访问 `std::pair` 的 `first` 和 `second` 成员。

## 70.如何处理OPTIONAL数据

在C++中处理 `optional` 数据可以通过使用 C++17 引入的 `std::optional` 类型，这是标准库中的一种类型，用于表示一个变量可能包含值，也可能不包含值。它非常适合用来表示可能为空或未定义的数据，避免使用传统的指针来表示缺失的值。

### 基本用法

```c++
#include <iostream>
#include <optional>

int main() {
    // 创建一个 optional 变量
    std::optional<int> opt;

    // 1. 检查是否有值
    if (!opt.has_value()) {
        std::cout << "opt 不包含值" << std::endl;
    }

    // 2. 给 opt 赋值
    opt = 42;

    // 3. 再次检查并访问值
    if (opt.has_value()) {
        std::cout << "opt 包含值：" << opt.value() << std::endl;
    }

    // 4. 使用 'value_or' 方法给默认值
    std::cout << "opt 或默认值：" << opt.value_or(0) << std::endl;

    return 0;
}
```

### 主要功能

1.**初始化**：`std::optional<T>` 可以在初始化时为空，也可以直接赋一个值。

```c++
std::optional<int> opt; // 默认不包含值
std::optional<int> opt_with_value = 10; // 包含值10
```

2.**检查值**：通过 `has_value()` 或 `operator bool()` 来检查 `optional` 是否包含值。

```c++
if (opt.has_value()) {
    // opt contains a value
}
```

3.**获取值**：通过 `value()` 来获取值，但如果 `optional` 没有值会抛出异常。可以使用 `value_or()` 方法返回一个默认值。

```c++
int val = opt.value(); // 如果 opt 没有值，抛出异常
int val_or_default = opt.value_or(0); // 如果 opt 没有值，返回0
```

4.**重置值**：可以通过 `reset()` 方法清除 `optional` 中的值。

```c++
opt.reset(); // 清除 opt 的值
```

实例(检测文件是否有数据存在)：

```c++
#include <fstream>
#include <optional>
std::optional<std::string> ReadFileString(const std::string& filepath)
{
	std::ifstream stream(filepath);
	if (stream)
	{
		std::string result;
		stream.close();
		return result;
	}
	return std::string();
}
int main()
{
	auto data = ReadFileString("data.txt");
	if (data.has_value())
	{
		std::cout << "File read successfully!\n";
	}
	else
	{
		data.value();
		std::cout << "File could not be opened\n";
	}
}
```

## 71.单一变量存放多种类型的数据

### 使用 `std::variant` (C++17)

`std::variant` 是 C++17 中引入的一个类模板，它允许一个变量存储多个可能的类型（但同时只能存储其中一种类型）。这是一个类型安全的解决方案。

实例:

```c++
#include <iostream>
#include <variant>

int main() {
    // 创建一个 std::variant 可以存储 int, float 或 std::string
    std::variant<int, float, std::string> data;

    // 存放 int
    data = 42;
    std::cout << "当前存储的 int 值: " << std::get<int>(data) << std::endl;

    // 存放 float
    data = 3.14f;
    std::cout << "当前存储的 float 值: " << std::get<float>(data) << std::endl;

    // 存放 std::string
    data = std::string("Hello, World!");
    std::cout << "当前存储的 string 值: " << std::get<std::string>(data) << std::endl;

    // 使用 std::holds_alternative 检查类型
    if (std::holds_alternative<int>(data)) {
        std::cout << "当前存储的是 int" << std::endl;
    } else if (std::holds_alternative<float>(data)) {
        std::cout << "当前存储的是 float" << std::endl;
    } else if (std::holds_alternative<std::string>(data)) {
        std::cout << "当前存储的是 string" << std::endl;
    }

    return 0;
}
```

#### 主要功能：

1. **`std::get<T>`**：用于从 `std::variant` 中获取值，必须确保当前存储的值是该类型。
2. **`std::holds_alternative<T>`**：用于检查 `std::variant` 当前是否存储某种类型的值。
3. **`std::visit`**：可以使用访问器函数对象来处理 `variant` 内部的值。

实例：

```c++
#include <variant>
int main()
{
	std::variant<std::string, int>data;
	data = "chreno";
	std::cout << std::get<std::string>(data) << std::endl;
	if (auto value = std::get_if<std::string>(&data))
	{
		std::string& v = *value;
	}
	data = 2;
}
```

## 72.如何存储任意类型的数据

`std::any` 是 C++17 引入的标准库类型，它允许存储任何类型的值，并且可以在运行时通过 `std::any_cast` 将其取出。它是一个类型安全的、灵活的方案。

```c++
#include <iostream>
#include <any>
#include <string>

int main() {
    std::any data;  // 可以存储任意类型的数据

    // 存放 int
    data = 42;
    std::cout << "当前存储的 int 值: " << std::any_cast<int>(data) << std::endl;

    // 存放 std::string
    data = std::string("Hello, World!");
    std::cout << "当前存储的 string 值: " << std::any_cast<std::string>(data) << std::endl;

    // 尝试错误的类型转换将抛出异常
    try {
        std::cout << std::any_cast<int>(data) << std::endl;  // 这将抛出异常
    } catch (const std::bad_any_cast& e) {
        std::cout << "类型转换错误: " << e.what() << std::endl;
    }

    return 0;
}
```

**主要功能**：

- **存储任意类型**：`std::any` 可以存储任何类型的对象，包括基本类型和自定义类型。
- **类型安全的提取**：使用 `std::any_cast` 来提取存储的值，类型必须匹配，否则会抛出 `std::bad_any_cast` 异常。
- **灵活性高**：非常适合需要存储和传递不同类型的数据的场景。

## 73.如何让C++运行的更快

通过多线程来提高性能。

在一个程序中，有一些东西能够被放到一个不同的线程中，这叫做工作线程。它可以独立地完成，他什么时候开始，什么时候结束并不重要。

在 C++ 中，`std::async` 和 `std::future` 是标准库提供的工具，用于异步任务管理和并发编程。`std::async` 用于启动一个异步任务，`std::future` 用于存储和获取异步操作的结果。这种方式允许你在不同线程中执行任务，而不需要显式管理线程。

### `std::async`

`std::async` 是 C++11 引入的一个函数，用于启动一个异步任务。该函数将一个可调用对象（例如函数、lambda 表达式、仿函数等）作为参数，并在后台线程中执行该任务。

用法：

```c++
#include <iostream>
#include <future>
#include <thread>

// 简单函数，用于演示
int computeSum(int a, int b) {
    return a + b;
}

int main() {
    // 使用 std::async 启动异步任务
    std::future<int> result = std::async(std::launch::async, computeSum, 5, 10);

    // 等待并获取结果
    int sum = result.get();  // 这里阻塞，直到任务完成
    std::cout << "Sum: " << sum << std::endl;  // 输出 15

    return 0;
}
```

**关键点：**

- ```
  std::async
  ```

  ：启动一个异步任务。

  - 第一个参数是启动策略（`std::launch::async` 或 `std::launch::deferred`）。
  - 第二个参数是你希望异步执行的函数，接下来的参数是传递给该函数的参数。

- ```
  std::future
  ```

  ：用于存储异步任务的结果，类似于一个占位符。你可以通过调用 

  ```
  get()
  ```

   来获取任务的结果。

  - `get()`：如果任务尚未完成，会阻塞当前线程，直到结果可用。

**启动策略**

`std::async` 可以接受两种启动策略，它们控制任务的执行方式：

1. **`std::launch::async`**：任务将在新线程中异步运行。
2. **`std::launch::deferred`**：任务不会立即执行，只有在调用 `get()` 或 `wait()` 时才会运行。这实际上是惰性计算，类似于延迟求值。

实例：

```c++
#include <iostream>
#include <future>
#include <chrono>
#include <thread>

void slowFunction() {
    std::this_thread::sleep_for(std::chrono::seconds(2));
    std::cout << "Function completed" << std::endl;
}

int main() {
    // std::launch::async：任务立即在新线程中执行
    std::future<void> asyncTask = std::async(std::launch::async, slowFunction);

    // std::launch::deferred：任务延迟执行，只有调用 get 时才会运行
    std::future<void> deferredTask = std::async(std::launch::deferred, slowFunction);

    std::cout << "Async task is running in background..." << std::endl;

    // 获取结果，阻塞直到异步任务完成
    asyncTask.get();  // 任务已在新线程运行
    std::cout << "Async task completed" << std::endl;

    std::cout << "Deferred task starts now..." << std::endl;
    deferredTask.get();  // 此时才开始执行任务
    std::cout << "Deferred task completed" << std::endl;

    return 0;
}
```

在上面的例子中，`std::launch::async` 会立即启动任务，而 `std::launch::deferred` 直到 `get()` 被调用时才会执行任务。

### `std::future`

`std::future` 是 C++ 标准库提供的一种工具，用于异步操作的结果管理。它是一个占位符，表示未来某个时间点可能会产生的值。可以通过调用 `get()` 来获取结果，`get()` 会阻塞当前线程，直到异步任务完成。

**主要方法：**

- **`get()`**：用于获取异步任务的返回值。如果任务未完成，它会阻塞当前线程，直到任务完成。
- **`wait()`**：等待任务完成，但不获取结果。
- **`wait_for()`** 和 **`wait_until()`**：允许你等待指定时间或直到某个时间点。

**示例：`wait_for()` 和 `wait_until()`**

```c++
#include <iostream>
#include <future>
#include <thread>
#include <chrono>

int slowSum(int a, int b) {
    std::this_thread::sleep_for(std::chrono::seconds(3));
    return a + b;
}

int main() {
    std::future<int> result = std::async(std::launch::async, slowSum, 5, 10);

    // 等待至多 2 秒
    if (result.wait_for(std::chrono::seconds(2)) == std::future_status::timeout) {
        std::cout << "Task is taking too long, wait more..." << std::endl;
    }

    // 再次等待直到任务完成
    result.wait();
    std::cout << "Task completed, result: " << result.get() << std::endl;

    return 0;
}
```

### `std::promise` 和 `std::future`

除了使用 `std::async` 启动任务外，`std::future` 也可以与 `std::promise` 搭配使用。在这种方式下，你可以手动设置异步任务的返回值。

**示例：`std::promise` 和 `std::future`**

```c++
#include <iostream>
#include <thread>
#include <future>

// 异步任务，将计算结果设置到 promise 中
void computeSum(std::promise<int>& prom, int a, int b) {
    int result = a + b;
    prom.set_value(result);  // 设置计算结果
}

int main() {
    // 创建 promise 和 future
    std::promise<int> prom;
    std::future<int> result = prom.get_future();

    // 在新线程中运行任务
    std::thread t(computeSum, std::ref(prom), 5, 10);

    // 等待并获取结果
    std::cout << "Result: " << result.get() << std::endl;

    t.join();  // 等待线程完成
    return 0;
}
```

**关键点：**

- **`std::promise`**：用于手动设置异步任务的结果。
- **`get_future()`**：获取与 `promise` 关联的 `future`，用于获取异步结果。

**总结**

- **`std::async`** 是启动异步任务的简单方式，不需要显式管理线程。它返回一个 `std::future` 对象，允许你异步地获取结果。
- **`std::future`** 是异步操作的占位符，你可以通过 `get()` 来获取任务的返回值。`wait_for()` 和 `wait_until()` 提供了额外的时间控制功能。
- **`std::promise`** 是一种更灵活的方式，可以手动设置异步任务的结果，并与 `std::future` 结合使用。

## 74.如何让C++字符串更快

std::string的主要问题之一，可能就是字符串格式化以及字符串操作。因为它们要分配内存。

### 使用 `std::string_view` (C++17)

`std::string_view` 是 C++17 引入的轻量级字符串类，它可以视为对现有字符串的只读引用，而不需要进行拷贝。这特别适用于只读字符串操作，避免了频繁的内存分配和拷贝。

实例：

```c++
#include <iostream>
#include <string_view>

void printString(std::string_view strView) {
    std::cout << strView << std::endl;  // 不拷贝字符串，直接读取视图
}

int main() {
    std::string myStr = "Hello, World!";
    printString(myStr);  // 使用 string_view 传递，不拷贝

    return 0;
}
```

**优势：**

- `std::string_view` 是只读的，并且避免了拷贝开销，适合需要频繁读取和传递字符串的场景。

**常用方法**

`std::string_view` 提供了一些常用的方法，与 `std::string` 类似：

- **`length()`**：返回字符串的长度。
- **`substr()`**：返回该字符串视图的子串。
- **`remove_prefix()` 和 `remove_suffix()`**：移除前缀或后缀，缩小视图的范围。
- **`data()`**：返回指向字符串数据的指针。
- **`empty()`**：检查字符串是否为空。

## 75.C++的可视化基准测试

C++ 的可视化基准测试是一种强大的工具，能帮助你优化代码性能。通过使用 Google Benchmark、数据导出和可视化工具，你可以轻松评估和比较不同算法和实现的性能。确保关注环境一致性和多次运行，以获得可靠的基准测试结果。

具体使用需要自己去尝试

## 76.C++的单例模式

单例是一个类的单一实例。

当我们想要拥有应用于某种全局数据集的功能，且我们只是想要重复使用时，单例是非常有用的。

单例模式是一种设计模式，确保一个类只有一个实例，并提供一个全局访问点。

### 1. 懒汉式单例

懒汉式单例在首次使用时创建实例，适合需要延迟加载的情况。

```c++
#include <iostream>
#include <mutex>

class Singleton {
public:
    // 获取实例的方法
    static Singleton& getInstance() {
        static Singleton instance; // C++11 及以上保证线程安全
        return instance;
    }

    // 示例方法
    void someFunction() {
        std::cout << "Function called!" << std::endl;
    }

private:
    Singleton() {} // 构造函数私有化
    ~Singleton() {} // 析构函数私有化

    // 禁止拷贝构造和赋值
    Singleton(const Singleton&) = delete;
    Singleton& operator=(const Singleton&) = delete;
};

int main() {
    Singleton::getInstance().someFunction();
    return 0;
}
```

### 2. 饿汉式单例

饿汉式单例在程序启动时创建实例，适合在应用启动时就需要使用的情况。

```c++
#include <iostream>

class Singleton {
public:
    // 获取实例的方法
    static Singleton& getInstance() {
        return instance; // 直接返回静态实例
    }

    void someFunction() {
        std::cout << "Function called!" << std::endl;
    }

private:
    Singleton() {} // 构造函数私有化
    ~Singleton() {} // 析构函数私有化

    // 静态实例
    static Singleton instance;

    // 禁止拷贝构造和赋值
    Singleton(const Singleton&) = delete;
    Singleton& operator=(const Singleton&) = delete;
};

// 静态实例初始化
Singleton Singleton::instance;

int main() {
    Singleton::getInstance().someFunction();
    return 0;
}
```

### 3. 线程安全的懒汉式单例

使用 `std::call_once` 和 `std::once_flag` 可以确保线程安全地创建单例。

```c++
#include <iostream>
#include <mutex>

class Singleton {
public:
    static Singleton& getInstance() {
        std::call_once(initFlag, []() {
            instance.reset(new Singleton());
        });
        return *instance;
    }

    void someFunction() {
        std::cout << "Function called!" << std::endl;
    }

private:
    Singleton() {} // 构造函数私有化
    ~Singleton() {} // 析构函数私有化

    static std::unique_ptr<Singleton> instance;
    static std::once_flag initFlag;

    // 禁止拷贝构造和赋值
    Singleton(const Singleton&) = delete;
    Singleton& operator=(const Singleton&) = delete;
};

// 静态成员初始化
std::unique_ptr<Singleton> Singleton::instance;
std::once_flag Singleton::initFlag;

int main() {
    Singleton::getInstance().someFunction();
    return 0;
}
```

## 77.C++的小字符串优化

减少字符串在代码中的使用可以显著提高速度。

可以让小字符串(也就是不是很长的字符串)，它们不需要堆分配。它们用栈分配。

小字符串优化（SSO，Short String Optimization）是一种 C++ 标准库实现的技术，它针对小字符串进行了性能优化，目的是避免频繁的动态内存分配，从而提升字符串处理的效率。

### 1. 什么是 SSO？

C++ 中的 `std::string` 通常是动态分配内存来存储字符串数据的。当字符串较短时，频繁的动态分配和释放内存会带来性能损耗。为了解决这个问题，大多数 C++ 标准库实现了 **小字符串优化**，即：当字符串长度足够短时，不会进行动态内存分配，而是将字符串的数据存储在 `std::string` 对象内部的一个固定大小的缓冲区中。

### 2. SSO 的工作原理

通常情况下，`std::string` 对象包含如下信息：

- 指向堆上分配的字符数组的指针。
- 当前字符串的长度。
- 已分配的内存容量。

而在启用 SSO 时，当字符串的长度小于某个预定义的阈值（通常为 15 个字节左右，具体取决于实现），`std::string` 会使用一个**内嵌的缓冲区**来存储小字符串，而不是在堆上动态分配内存。这样就避免了内存分配带来的开销。

```c++
#include <iostream>
#include <string>

int main() {
    std::string shortStr = "abc";  // 短字符串，可能会使用 SSO
    std::string longStr = "This is a very long string that will likely exceed the SSO limit.";

    std::cout << "Short string: " << shortStr << std::endl;
    std::cout << "Long string: " << longStr << std::endl;

    return 0;
}
```

在这个例子中，`shortStr` 可能会启用 SSO，因为它的长度较短，而 `longStr` 会在堆上分配内存，因为它的长度超出了 SSO 的阈值。

### 3. 优点

1. **减少内存分配**：通过在 `std::string` 对象本身存储小字符串，避免了动态内存分配，这使得小字符串的创建、复制、移动和销毁操作更加高效。
2. **提高性能**：SSO 减少了因动态内存分配带来的性能开销，尤其是在短字符串的场景下，这显著提升了性能。
3. **减少缓存失效**：由于小字符串存储在栈上（`std::string` 对象内部），它们通常在 CPU 缓存中，因此访问这些字符串的速度更快。

### 4. SSO 的实现

SSO 的具体实现细节取决于 C++ 标准库的实现，但通常会有如下特点：

- `std::string` 对象中包含一个用于存储小字符串的固定大小缓冲区（通常是 15 或 23 个字符）。
- 当字符串长度小于缓冲区大小时，字符串数据存储在这个缓冲区中。
- 当字符串长度超过缓冲区大小时，才会在堆上分配内存。

**注意**：SSO 并不是 C++ 标准的一部分，而是标准库实现中的优化。不同编译器和标准库实现对 SSO 的支持可能有所不同，但大多数现代 C++ 标准库（如 GNU libstdc++、LLVM libc++ 等）都支持 SSO。

### 5. SSO 的限制

- **字符串长度限制**：SSO 只适用于短字符串，超过 SSO 阈值的字符串仍然需要在堆上分配内存。阈值大小取决于标准库的具体实现，通常是 15 或 23 字符。
- **非强制性**：SSO 是一种优化技术，但不是标准的一部分，因此你不能依赖它的存在，特别是跨平台或不同标准库的实现。

### 6. 如何检查 SSO 是否生效

由于 SSO 是标准库实现的内部优化，C++ 标准并没有规定它的行为。不过，你可以通过一些实验性的代码来观察 SSO 的行为，比如检查内存分配次数。

```c++
#include <iostream>
#include <string>

int main() {
    std::string shortStr = "short";
    std::string longStr = "this is a very long string";

    std::cout << "Size of short string: " << shortStr.size() << std::endl;
    std::cout << "Capacity of short string: " << shortStr.capacity() << std::endl;

    std::cout << "Size of long string: " << longStr.size() << std::endl;
    std::cout << "Capacity of long string: " << longStr.capacity() << std::endl;

    // 比较地址以判断是否在栈上存储 (不完全可靠，但可以尝试)
    std::cout << "Address of short string data: " << static_cast<const void*>(shortStr.data()) << std::endl;
    std::cout << "Address of long string data: " << static_cast<const void*>(longStr.data()) << std::endl;

    return 0;
}
```

### 7. 性能影响

SSO 对性能的提升在于减少小字符串的内存分配和释放操作，减少不必要的内存拷贝。对于频繁创建短字符串的场景，如字符串拼接、文本处理、日志系统等，SSO 能够显著提升性能。

性能对比示例：

```c++
#include <iostream>
#include <string>
#include <chrono>

void benchmark() {
    const int N = 1000000;
    auto start = std::chrono::high_resolution_clock::now();

    for (int i = 0; i < N; ++i) {
        std::string s = "short";  // 可能会使用 SSO
    }

    auto end = std::chrono::high_resolution_clock::now();
    std::chrono::duration<double> duration = end - start;
    std::cout << "SSO benchmark duration: " << duration.count() << " seconds\n";
}

int main() {
    benchmark();
    return 0;
}
```

## 78.跟踪内存分配的简单方法

在 C++ 中，跟踪内存分配是性能优化和调试内存泄漏的重要步骤。你可以通过一些简单的方法跟踪内存分配，帮助检测不必要的分配、过多的内存使用或内存泄漏。以下是几种常见的内存分配跟踪方法，从简单的自定义 `new/delete` 操作符到更高级的工具和库。

### 1. 自定义 `new` 和 `delete` 操作符

通过重载全局的 `new` 和 `delete` 操作符，可以轻松记录每次内存分配和释放的操作。这种方法非常直观，适合小型项目中进行快速跟踪。

#### 示例：自定义 `new` 和 `delete`

```C++
#include <iostream>
#include <cstdlib>  // For malloc and free

static size_t totalAllocated = 0;  // 记录总分配内存的大小

// 重载全局 new 操作符
void* operator new(size_t size) {
    totalAllocated += size;
    std::cout << "Allocating " << size << " bytes, Total allocated: " << totalAllocated << " bytes\n";
    return malloc(size);  // 使用 malloc 进行内存分配
}

// 重载全局 delete 操作符
void operator delete(void* ptr, size_t size) noexcept {
    totalAllocated -= size;
    std::cout << "Freeing " << size << " bytes, Total allocated: " << totalAllocated << " bytes\n";
    free(ptr);  // 使用 free 释放内存
}

int main() {
    int* arr = new int[10];  // 触发自定义 new 操作
    delete[] arr;  // 触发自定义 delete 操作

    std::string* str = new std::string("Hello, World!");  // 触发自定义 new 操作
    delete str;  // 触发自定义 delete 操作

    return 0;
}
```

输出：

```bash
Allocating 40 bytes, Total allocated: 40 bytes
Freeing 40 bytes, Total allocated: 0 bytes
Allocating 32 bytes, Total allocated: 32 bytes
Freeing 32 bytes, Total allocated: 0 bytes
```

#### 说明：

- 通过重载 `new` 和 `delete`，可以记录每次分配的大小、释放的大小以及当前已分配的总内存。
- `new` 操作符调用 `malloc` 来分配内存，而 `delete` 调用 `free` 来释放内存。

## 79.C++的左值和右值

左值被认为是有地址的值

**左值（Lvalue）**

- **左值**是指程序中可以**取地址**的对象或变量，它们具有持久的存储位置。简单来说，左值就是可以放在赋值操作符 (`=`) 左边的值。
- 左值可以是变量、数组元素、对象的成员等，通常表示**具名对象**。

**右值（Rvalue）**

- **右值**是那些**不能取地址**的值，通常是临时对象或常量，通常表示**匿名的值**。
- 右值通常位于赋值操作符的右边，它们的生命周期通常非常短暂，通常是表达式的结果或字面值。

**左值引用和右值引用**

**左值引用（Lvalue Reference）**

- 左值引用是 C++ 中最常见的引用类型，它可以绑定到左值，也就是持久存储的对象。
- 左值引用通常用于函数参数传递，避免不必要的复制。

```c++
int a = 5;
int& refA = a;  // refA 是 a 的左值引用

void modify(int& x) {
    x = 10;  // 修改的是传入的左值
}

modify(a);  // 传入左值 a
```

**右值引用（Rvalue Reference）**

- 右值引用是 C++11 引入的新特性，专门用于绑定右值。右值引用通过 `&&` 来声明。
- 右值引用的引入是为了支持**移动语义**，从而减少不必要的拷贝，提升程序的性能。

```c++
int&& rref = 5;  // rref 是 5 的右值引用

void printRvalue(int&& x) {
    std::cout << x << std::endl;
}

printRvalue(10);  // 传递右值 10
```

## 80.C++持续集成

持续集成指的是在开发期间持续集成代码的过程

它的本质是构建自动化和测试

在 C++ 项目中实现**持续集成（Continuous Integration, CI）**，可以确保代码库的质量和稳定性，尤其是当团队协作、多人开发时。持续集成的核心思想是：在每次代码提交或合并时，自动构建、测试并反馈结果，确保代码始终处于可构建和稳定的状态。

**持续集成的核心流程**

1. **代码提交**：开发者将代码提交到版本控制系统（如 Git）。
2. **触发构建**：CI 系统检测到新的提交，自动拉取代码并开始构建。
3. **自动化测试**：CI 系统运行测试代码，确保新提交的代码不破坏现有功能。
4. **结果反馈**：CI 系统反馈测试结果，成功或失败。
5. **合并和部署**：如果一切正常，代码可以合并到主分支，并部署到生产环境（这是持续部署的部分）。

## 81.C++静态分析

**C++ 静态分析** 是在编译代码之前，使用工具或技术对代码进行分析，以检测潜在的错误、性能问题、编码风格不一致、未初始化的变量、内存泄漏、安全漏洞等问题。静态分析不需要运行程序，因此可以在开发早期发现问题。

**静态分析的作用**

静态分析工具可以帮助开发者在代码编译或执行前识别各种问题。它们的主要作用包括：

- **发现潜在的错误**：例如未初始化的变量、可能导致崩溃的非法内存访问等。
- **代码优化建议**：通过分析代码，提出优化建议以提高程序性能。
- **提高代码质量**：识别不符合编码标准的地方，并给出改进建议。
- **安全漏洞检测**：一些工具可以检测出潜在的安全漏洞，如缓冲区溢出或 SQL 注入等。
- **增强可维护性**：帮助开发者识别复杂的代码结构或潜在的技术债务，改进代码的可维护性。

## 82.C++的参数计算顺序

在 C++ 中，**函数参数的计算顺序** 是一个常见的讨论话题，因为它可能影响程序的行为，尤其是在涉及副作用时（如修改变量或使用指针）。C++ 标准对参数的计算顺序没有明确规定，这意味着不同的编译器或编译器设置可能会导致不同的行为。因此，开发者需要小心处理可能引发问题的代码。

### 1. 参数计算顺序的定义

**参数计算顺序**是指在调用函数时，函数的实参在被传递给形参之前按什么顺序进行求值。C++ 标准对**函数参数的求值顺序没有强制性的要求**，也就是说，编译器可以以任何顺序计算函数的实参值。

举个例子：

```c++
int f1() {
    std::cout << "f1" << std::endl;
    return 1;
}

int f2() {
    std::cout << "f2" << std::endl;
    return 2;
}

int main() {
    int result = std::max(f1(), f2());  // 参数 f1() 和 f2() 的计算顺序未定义
    std::cout << "Result: " << result << std::endl;
}
```

在这个例子中，编译器可能先调用 `f1()`，也可能先调用 `f2()`，这取决于编译器的实现，C++ 标准对此没有强制规定。

### 2. C++ 标准中关于计算顺序的规定

在 C++ 标准中，虽然没有规定函数参数的计算顺序，但有一些相关的规则：

- **参数的求值顺序是未定义的**：函数参数的计算顺序是未定义的，这意味着编译器可以选择从左到右或从右到左计算，或者以其他方式计算。开发者不能依赖某种顺序，因为这可能会导致非确定性的行为，特别是在涉及副作用时。
- **参数求值的独立性**：虽然求值顺序未定义，但 C++ 标准规定不同参数的计算之间不能相互依赖。也就是说，编译器必须确保每个参数独立求值，不能因为计算一个参数而影响另一个参数的结果。

### 3. 副作用与未定义行为

当函数参数之间存在副作用时，未定义的计算顺序可能导致意外行为。

**副作用的例子：**

```c++
int x = 0;

int incrementX() {
    return ++x;  // 增加 x 的值
}

int useX() {
    return x;
}

int main() {
    int result = incrementX() + useX();  // 参数的计算顺序未定义
    std::cout << result << std::endl;
}
```

在这个例子中，`incrementX()` 会修改 `x` 的值，而 `useX()` 使用 `x` 的值。因为参数的计算顺序未定义，`incrementX()` 和 `useX()` 的计算顺序也未定义，可能导致两种不同的结果：

1. 如果 `incrementX()` 先执行，则 `useX()` 将使用 `x == 1` 的值，结果是 `1 + 1 == 2`。
2. 如果 `useX()` 先执行，则 `useX()` 使用 `x == 0` 的值，结果是 `1 + 0 == 1`。

这个例子展示了副作用和未定义参数计算顺序可能引发的不确定行为。因此，在有副作用的代码中，应该避免依赖参数的计算顺序。

### 4. 特定场景下的计算顺序

虽然函数参数的计算顺序未定义，但在一些特定场景下，C++ 标准确实有规定计算顺序的地方：

#### 1. **逗号运算符**

在逗号运算符（`,`）中，表达式从左到右进行计算。例如：

```c++
int x = (f1(), f2());  // 先计算 f1()，再计算 f2()
```

#### 2. **逻辑与运算符 `&&` 和逻辑或运算符 `||`**

逻辑与运算符 `&&` 和逻辑或运算符 `||` 是短路运算符，它们的左操作数先进行求值，只有在需要时才会求值右操作数。

```c++
bool result = f1() && f2();  // 如果 f1() 为 false，则不会执行 f2()
```

#### 3. **条件运算符 `?:`**

条件运算符的条件部分首先求值，之后根据条件的结果求值第二个或第三个操作数。

```c++
int x = (f1() > 0) ? f2() : f3();  // 先计算 f1()，根据结果决定 f2() 或 f3() 的执行
```

#### 4. **函数调用中的实际计算顺序**

尽管 C++ 标准并没有规定参数计算的顺序，但一些编译器有它们的默认行为。例如，GCC 和 Clang 通常会从右到左求值参数，而 MSVC 则可能采用从左到右的顺序。但这是编译器的行为，并且在不同的版本或优化设置下可能会发生变化。

## 83.C++移动语义

**移动语义** 是 C++11 引入的一项重要特性，旨在提升对象的复制效率，尤其是在处理大对象时。移动语义通过**右值引用**（`&&`）和 **move 构造函数** 及 **move 赋值运算符** 实现，能够避免不必要的深拷贝操作，提升程序性能。通过移动语义，资源（如内存、文件句柄等）可以从一个对象“移动”到另一个对象，而不是简单地复制，这样可以减少资源的重复分配和释放。

### 1. C++ 中的值类型

在理解移动语义之前，我们首先需要理解 C++ 中的两种值类型：

- **左值（Lvalue）**：具名对象，拥有持久的存储空间。左值是可以取地址的，可以放在赋值操作的左边。
- **右值（Rvalue）**：临时对象或字面值，不具名，通常是短暂存在的。右值通常是表达式的结果，生命周期较短，不能取地址。

### 2. 问题背景：复制的性能问题

在传统的 C++ 中，复制对象时会进行**深拷贝**，即复制对象的所有数据。对于小对象，这通常没什么问题，但对于**大对象**（如容器类 `std::vector`、`std::string`），深拷贝可能会导致严重的性能问题，因为需要分配新的内存并复制数据。

#### 复制问题的示例：

```c++
#include <iostream>
#include <vector>

std::vector<int> createLargeVector() {
    std::vector<int> vec(1000000, 1);  // 创建一个包含100万元素的向量
    return vec;  // 返回该向量
}

int main() {
    std::vector<int> vec = createLargeVector();  // 这里会进行深拷贝
    std::cout << "Vector size: " << vec.size() << std::endl;
}
```

在这个示例中，`createLargeVector` 返回一个大型的向量，当将其赋给 `vec` 时，传统的 C++ 会进行深拷贝，导致性能开销。为了解决这种性能问题，C++11 引入了 **移动语义**。

### 3. 移动语义的概念

**移动语义** 的核心是通过右值引用（`&&`）来接收和转移右值对象的资源。移动语义允许通过“窃取”资源的方式来避免不必要的深拷贝操作。在这种情况下，资源的所有权从一个对象移动到另一个对象，而不是复制资源。

#### 右值引用的引入

C++11 引入了 **右值引用**（`T&&`），它允许开发者区分**左值**和**右值**，并对右值对象进行优化。

- **左值引用（`T&`）**：只能绑定到左值，即具名的、持久的对象。
- **右值引用（`T&&`）**：只能绑定到右值，即临时对象或字面值，生命周期较短。

### 4. 移动构造函数和移动赋值运算符

为了实现移动语义，C++11 允许开发者为类定义 **移动构造函数** 和 **移动赋值运算符**，它们分别处理对象的初始化和赋值时的资源转移。

#### 1. 移动构造函数

移动构造函数的作用是接收一个右值引用参数，并将该对象的资源“移动”到新对象中，而不是进行深拷贝。

```c++
#include <iostream>
#include <vector>

class MyClass {
public:
    std::vector<int> data;

    // 默认构造函数
    MyClass() {}

    // 移动构造函数
    MyClass(MyClass&& other) noexcept {
        std::cout << "Move constructor called!" << std::endl;
        data = std::move(other.data);  // 转移资源
    }
};

int main() {
    MyClass obj1;
    obj1.data = std::vector<int>(1000, 1);  // 初始化 obj1

    MyClass obj2 = std::move(obj1);  // 触发移动构造函数
    std::cout << "obj1 size: " << obj1.data.size() << std::endl;
    std::cout << "obj2 size: " << obj2.data.size() << std::endl;
}
```

输出：

```bash
Move constructor called!
obj1 size: 0
obj2 size: 1000
```

在这个示例中，`obj2` 从 `obj1` 移动了数据资源，而不是深拷贝。`std::move()` 用于将 `obj1` 转换为右值引用，告知编译器可以“移动”资源。

#### 2. 移动赋值运算符

**移动赋值操作符** 是一种特殊的赋值操作符，旨在实现对象之间的资源转移。与传统的拷贝赋值不同，移动赋值操作符能够“窃取”源对象的资源，而不是复制资源。

移动赋值操作符通常用于当一个现有对象被重新赋值为一个右值时。移动赋值操作符的参数类型是**右值引用**，即 `T&&`。

**移动赋值操作符的格式：**

```c++
T& operator=(T&& other) noexcept;
```

**`T&&`** 表示右值引用，意味着它只能接收临时对象或通过 `std::move` 转换的左值。

**`noexcept`** 通常用于移动语义的函数中，以确保在异常情况下不会抛出异常。

**定义移动赋值操作符：**

移动赋值运算符的作用与移动构造函数类似，允许对象在赋值时转移资源，而不是进行深拷贝。

```c++
class MyClass {
public:
    std::vector<int> data;

    // 默认构造函数
    MyClass() {}

    // 移动赋值运算符
    MyClass& operator=(MyClass&& other) noexcept {
        std::cout << "Move assignment operator called!" << std::endl;
        if (this != &other) {
            data = std::move(other.data);  // 转移资源
        }
        return *this;
    }
};

int main() {
    MyClass obj1;
    obj1.data = std::vector<int>(1000, 1);

    MyClass obj2;
    obj2 = std::move(obj1);  // 触发移动赋值运算符
}
```

在移动赋值运算符中，我们首先检查自赋值（`this != &other`），避免自我赋值带来的错误。然后，通过 `std::move` 将 `other` 对象的资源转移到当前对象中。

### 5. `std::move` 和 `std::forward`

- **`std::move`** 是一个标准库函数，用于将对象显式地转换为右值引用。它并不会真正“移动”对象，而是告诉编译器该对象可以“被移动”，从而启用移动语义。

**`std::move`** 是一个用于**将对象转换为右值引用**的工具函数。它的作用是将一个左值显式地转换为右值引用（`T&&`），从而告知编译器该对象的资源可以安全地“移动”。

**`std::move` 的主要特点：**

- **转换左值为右值引用**：`std::move` 仅仅是一个类型转换工具，它不会真的移动对象，只是将对象的类型从左值转换为右值引用。
- **启用移动语义**：当对象被转换为右值引用后，它将触发该对象的 **移动构造函数** 或 **移动赋值操作符**，以实现资源的转移。

**std::move的实现：**

```c++
template<typename T>
typename std::remove_reference<T>::type&& move(T&& arg) noexcept {
    return static_cast<typename std::remove_reference<T>::type&&>(arg);
}
```

示例：

```c++
#include <iostream>
#include <string>

int main() {
    std::string str1 = "Hello, World!";
    std::string str2 = std::move(str1);  // 将 str1 移动到 str2

    std::cout << "str1: " << str1 << std::endl;  // str1 变为空（未指定状态）
    std::cout << "str2: " << str2 << std::endl;  // str2 得到了 str1 的资源

    return 0;
}
```

- **`std::forward`** 用于完美转发（perfect forwarding），特别是在模板函数中。它可以根据参数的类型决定传递左值还是右值。

**`std::forward`** 是一种用于 **完美转发（Perfect Forwarding）** 的工具函数，它通常在**模板函数**中使用。`std::forward` 的作用是**保持参数的值类别（左值或右值）**，确保在传递参数时不会改变它的左值或右值属性。

#### `std::forward` 的主要特点：

- **保持参数的值类别**：`std::forward` 会根据传递的参数是左值还是右值，转发相应的左值或右值引用，从而实现“完美转发”。
- **模板参数推导**：`std::forward` 通常与模板函数结合使用，以确保传递的参数能够保持其原始的值类别。

**`std::forward` 的实现：**

```c++
template <typename T>
void forwardTest(T&& arg) {
    foo(std::forward<T>(arg));  // 根据 arg 是左值还是右值选择不同的传递方式
}
```

**示例：**

```c++
#include <iostream>
#include <utility>  // for std::move, std::forward

void process(int& x) {
    std::cout << "Lvalue reference: " << x << std::endl;
}

void process(int&& x) {
    std::cout << "Rvalue reference: " << x << std::endl;
}

template <typename T>
void forwardTest(T&& arg) {
    process(std::forward<T>(arg));  // 使用 std::forward 转发参数
}

int main() {
    int a = 10;
    forwardTest(a);  // 传递左值，匹配到 lvalue reference 版本
    forwardTest(20);  // 传递右值，匹配到 rvalue reference 版本

    return 0;
}
```



### 6. 移动语义的好处

- **性能提升**：移动语义避免了大对象的深拷贝，减少了内存分配和复制操作。对于使用大量资源的对象（如 `std::vector`、`std::string` 等容器类），移动语义可以显著提升程序的性能。
- **资源转移**：通过移动语义，资源（如内存、文件句柄等）可以从一个对象“转移”到另一个对象，而不是被复制。这种转移是轻量级的，避免了重复分配和释放资源的开销。

### 7. 使用移动语义的场景

- **返回局部对象**：当从函数返回局部对象时，可以通过移动构造函数避免拷贝。

```c++
std::vector<int> createVector() {
    std::vector<int> vec(1000, 1);
    return vec;  // 使用移动语义
}
```

- **容器类的元素转移**：`std::vector` 等容器类可以使用移动语义将元素从一个容器转移到另一个容器，而不是逐个元素进行深拷贝。

```c++
std::vector<std::string> v1;
std::vector<std::string> v2 = std::move(v1);  // v2 从 v1 移动资源
```

### 8. 移动语义和拷贝语义的共存

在实际开发中，一个类可能同时需要支持**移动语义**和**拷贝语义**。C++11 提供了规则来管理这种共存关系：

- **如果定义了移动构造函数或移动赋值运算符**，编译器将不再自动生成拷贝构造函数和拷贝赋值运算符。因此，如果你需要同时支持拷贝和移动语义，必须手动定义这些函数。
