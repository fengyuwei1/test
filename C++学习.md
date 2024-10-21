# 1.C++学习

## 1.变量

作用：给一段指定的内存空间起名，方便这段内存的使用

语法：数据类型  变量名  =  初始值;

示例：

![image-20240509211450787](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509211450787.png)

### 1.1变量存在的意义

方便我们管理内存空间

## 2.常量

作用：用于记录程序中不可更改的数据

C++定义常量的两种方式：

1.#define 宏常量：`#define 常量名 常量值`

通常在文件上方定义，表示一个常量

2.const修饰的变量：`const 数据类型 常量名 = 常量值`

通常定义在变量定义前加关键字const，修饰该变量为常量，不可修改

示例：

```c++
#define day 7
#include<iostream>
using namespace std;
int main()
{  
	const int a = 1;
	cout << a << endl;
	cout << day << endl;
	system("pause");
	return 0;
}
```

## 3.关键字

作用：关键字是C++中预先保留的单词(标识符)

在定义变量或者常量时候，不要用关键字

C++关键字如下：

![image-20240510002505860](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510002505860.png)

注：不要用关键字给变量或者常量起名称

## 4.标识符命名规则

作用：C++规定给标识符(变量，常量)命名时，有一套自己的规则

**1.标识符不能是关键字**

**2.标识符只能由字母，数字，下划线组成**

**3.第一个字符必须为字母或下划线**

**4.标识符中字母区分大小写**

## 5.数据类型

C++规定在创建一个变量或者常量时，必须要指定出相应的数据类型，否则无法给变量分配内存

存在意义：给变量分配合适的内存空间

### 2.1整型

作用：整形变量表示的是整数类型的数据

C++中能够表示整型的类型有以下几种方式，区别在于所占内存空间不同

![image-20240510005459438](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510005459438.png)

### 2.2sizeof关键字

作用：利用sizeof关键字可以统计数据类型所占内存的大小

语法：sizeof(数据类型 / 变量)

示例：

![image-20240510192644557](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510192644557.png)

整型结论：short < int <= long <= long long

### 2.3实型(浮点型)

作用：用于表示小数

浮点型变量分为两种：

1.单精度float

2.双精度double

两者的区别在于表示的有效数子范围不同

![image-20240510192942602](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510192942602.png)

默认情况下，输出一个小数，会显示出6位有效数字

示例：

![image-20240510194041253](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510194041253.png)

### 2.4字符型

作用：字符型变量用于显示单个字符

语法：char ch = 'a';

![image-20240510194202567](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510194202567.png)

C和C++中字符型变量只占用1个字节

字符型变量并不是把字符本身放到内存中储存，而是将对应的ASCII编码放入到1储存单元

示例：

![image-20240510195826187](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510195826187.png)

### 2.5转义字符

作用：用于表示一些不能显示出来的ASCII字符

![image-20240510200718018](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510200718018.png)

![image-20240510201321905](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510201321905.png)

示例：

![image-20240510201350959](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510201350959.png)

### 2.6字符串型

作用：用于表示一串字符

两种风格：

1.C语言风格

![image-20240510201522171](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510201522171.png)

2.C++风格

![image-20240510202127329](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510202127329.png)

### 2.7布尔类型 bool

作用：布尔数据类型代表真或假的值

bool类型只有两个值：

true --- 真(本质是1)

false --- 假(本质是0)

bool类型占1个字节大小

示例：

![image-20240511154934850](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240511154934850.png)

### 2.8数据的输入

作用：用于从键盘获取数据

关键字：cin

语法:cin >> 变量

## 6.运算符

作用：用于执行代码的运算

![image-20240511160025209](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240511160025209.png)

### 6.1算术运算符

作用：用于处理四则运算

![image-20240515193843045](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240515193843045.png)

### 6.2赋值运算符

作用：用于将表达式的值赋给变量

![image-20240515200824905](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240515200824905.png)

### 6.3比较运算符

作用：用于表达式的比较，并返回一个真值或假值

![image-20240515201454362](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240515201454362.png)

### 6.4逻辑运算符

作用：用于根据表达式的值返回真值或假值

![image-20240515201706195](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240515201706195.png)

## 7.程序流程结构

![image-20240516104905299](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240516104905299.png)

### 7.1选择结构

#### 7.1.1if语句

作用：执行满足条件的语句

if语句的三种形式

![image-20240516105033622](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240516105033622.png)

##### 1.单行格式if语句：```if(条件){条件满足执行的语句}```

![image-20240516105156001](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240516105156001.png)

示例：

![image-20240516105704467](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240516105704467.png)

##### 2.多行格式if语句```if(条件){条件满足执行的语句}else{条件不满足执行的语句}```

![image-20240516110143457](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240516110143457.png)

##### 3.多条件的if语句if(条件1){条件1满足执行的语句}else if(条件2){条件2满足执行的语句}...else{都不满足执行的语句}

![image-20240516110533116](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240516110533116.png)

##### 4.嵌套if语句

#### 7.1.2三目运算符

作用：通过三目运算符实现简单的判断

语法：表达式1？表达式2：表达式3

![image-20240516192009528](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240516192009528.png)

在C++中三目运算符返回的是变量，可以继续赋值

示例：

![image-20240516192835176](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240516192835176.png)

#### 7.1.3switch语句

作用：执行多条件分支语句

语法：

![image-20240516193113034](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240516193113034.png)

![image-20240516193539480](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240516193539480.png)

### 7.2循环结构

#### 7.2.1 while循环结构

作用：满足循环条件，执行循环语句

语法：while(循环条件){循环语句}

解释：只要循环条件的结果为真，就执行循环语句

![image-20240517211419924](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240517211419924.png)

示例：

![image-20240517211530766](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240517211530766.png)

案例：

```c++
int main()
{
	srand((unsigned int)time(NULL));
	int score = rand() % 100+1;
	int a = 0;
	while (a != score)
	{
		cin >> a;
		if (a > score)
		{
			cout << "猜大了" << endl;
		}
		else if (a < score)
		{
			cout << "猜小了" << endl;
		}
		else
		{
			cout << "猜对了" << endl;
		}
	}
	return 0;
}
```

#### 7.2.2do···while循环语句

作用：满足循环条件，执行循环语句

语法：do{循环语句}while{循环条件}

注意：与while的区别是do···while会先执行一次循环语句，再判断循环条件

![image-20240519200111456](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240519200111456.png)

#### 7.2.3for循环语句

作用：满足循环条件，执行循环语句

语法：for(起始表达式;条件表达式;末尾表达式){循环语句}；

示例：

![image-20240519202306031](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240519202306031.png)

#### 7.2.4嵌套循环

作用：在循环体中再嵌套一层循环，解决一些实际问题

### 7.3跳转语句

#### 7.3.1break语句

作用：用于选择跳出结构或者循环结构

break使用的时机:

![image-20240519204859012](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240519204859012.png)

#### 7.3.2continue语句

作用：在循环语句中，跳过本次循环中余下尚未执行的语句，继续执行下一次循环

示例：

![image-20240519205424191](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240519205424191.png)

#### 7.3.3goto语句

作用：可以无条件跳转语句

语法：goto 标记;

解释：如果标记的名称存在，执行到goto语句时，会跳转到标记的位置

注意：在程序中不建议使用goto语句，以免造成程序的混乱

## 8.数组

### 8.1概述

所谓数组，就是一个集合，里面存放了相同类型的数据元素

特点1：数组中的每个元素都是相同的数据类型

特点2：数组是由连续的内存位置组成的

### 8.2一维数组

#### 8.2.1一维数组定义方式

![image-20240520192713133](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240520192713133.png)

数组的特点

放在一块连续的内存空间中

数组中每个元素都是相同类型的

#### 8.2.2一维数组数组名

一维数组名称的用途：

1.可以统计整个数组在内存中的长度

2.可以获取数组在内存中的首地址

#### 8.2.3冒泡排序

作用：最常用的排序算法，对数组内元素进行排序

![image-20240521154153288](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240521154153288.png)

```c++
int main()
{
	int i = 0;
	int j = 0;
	int arr[9] = { 4,2,8,0,5,7,1,3,9 };
	for (i = 0; i < 9-1; i++)
	{
		for (j = 0; j < 8-i; j++)
		{
			if (arr[j] > arr[j+1])
			{
				int temp = arr[j];
				arr[j] = arr[j + 1];
				arr[j + 1] = temp;
			}
		}
	}
	for (int k = 0; k < 9; k++)
	{
		cout << arr[k] << endl;
	}
	system("pause");
	return 0;
}
```

### 8.3二维数组

二维数组就是在一维数组上，多加一个数组

#### 8.3.1二维数组定义方式

二维数组定义的四种方式:

1.`数据类型 数组名 [行数][列数];`

2.`数据类型 数组名 [行数][列数]={{数据1，数据2},{数据3，数据4}}`

3.`数据类型 数组名 [行数][列数]={数据1,数据2,数据3,数据4}`

4.`数据类型 数组名 [][列数]={数据1，数据2，数据3，数据4}`

建议用第二种

打印二维数组：外层循环打印行数，内层循环打印列数

#### 8.3.2二维数组数组名

查看二维数组所占内存空间

获取二维数组首地址

示例：

![image-20240521175734853](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240521175734853.png)

## 9.函数

### 9.1概述

作用：将一段经常使用的代码封装起来，减少重复代码

一个较大的程序，一般分为若干个程序块，每个模块实现特定的功能

### 9.2函数的定义

函数的定义一般主要有5个步骤：
1.返回值类型

2.函数名

3.参数表列

4.函数体语句

5.return 表达式

语法：

 ![image-20240522153841746](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240522153841746.png)

 ![image-20240522154812621](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240522154812621.png)

### 9.3函数的调用

功能：使用定义好的函数

语法：```函数名 (参数)```

总结：函数定义里小括号内称为形参，函数调用时传入的参数称为实参

### 9.4值传递

所谓值传递，就是函数调用时实参将数值传入给形参

值传递时，如果形参发生变化，并不会影响实参

总结：值传递时，形参是修饰不了实参的

### 9.5函数的常见样式

常见的函数样式有4种

1.无参无返

2.有参无返

3.无参有返

4.有参有返

### 9.6函数的声明

作用：告诉编译器函数名称及如何调用函数，函数的实际主体可以单独定义

函数的声明可以多次，但是函数的定义只能有一次

示例：

![image-20240522171341739](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240522171341739.png)

### 9.7函数的分文件编写

作用：让代码结构更加清晰

![image-20240522171631514](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240522171631514.png)

## 10.指针

### 10.1指针的基本概念

指针的作用：可以通过指针间接访问内存

内存编号是从0开始记录的，一般用十六进制数字表示

可以利用指针变量保存地址

### 10.2指针变量的定义和使用

指针变量定义语法： `数据类型 * 变量名`

示例：

![image-20240523153157442](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240523153157442.png)

### 10.3指针所占内存空间

指针的数据类型占多少字节，指针就占多少字节

![image-20240523153807938](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240523153807938.png)

示例：

![image-20240523153836807](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240523153836807.png)

### 10.4空指针和野指针

空指针：指针变量指向内存中编号为0的空间

用法：初始化指针变量

注意：空指针指向的内存是不可以访问的

0-255之间的内存编号是系统占用的，因此不可以访问

示例：

![image-20240523154455217](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240523154455217.png)

野指针：指针变量指向非法的内存空间

示例：

![image-20240523154605599](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240523154605599.png)

总结：空指针和野指针都不是我们申请的空间，因此不要访问

### 10.5const修饰指针

const修饰指针有三种情况：

1.const修饰指针 -- 常量指针

2.const修饰常量 -- 指针常量

3.const即修饰指针，又修饰常量

4.`const int *p = &c;`//常量指针

特点：指针的指向可以修改，但是指针指向的值不可以修改

5.`int * const p = &a;`//指针常量

特点：指针的指向不可以改，但指针的值可以改

6.`const int * const p = &a;`

特点：指针的指向和指针指向的值都不可以改

技巧：看const右侧紧跟着的是指针还是常量，是指针就是常量指针，是常量就是指针常量

### 10.6指针和数组

作用：利用指针访问数组中元素

示例：

![image-20240523192602350](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240523192602350.png)

### 10.7指针和函数

作用：利用指针作函数参数，可以修改实参的值

示例：

```c++
void swap(int *a,int *b)
{
	int temp = *a;
	*a = *b;
	*b = temp;
}
int main()
{
	int a = 10;
	int b = 20;
	swap(&a, &b);
	cout << a << b << endl;
	system("pause");
	return 0;
}
```

### 10.8指针，函数，数组

封装一个函数，利用冒泡排序，实现对整型数组的升序排序

示例：

```c++
void bubblesort(int* arr, int len)
{
	for (int i = 0; i < len; i++)
	{
		for (int j = 0; j < len - 1 - i; j++)
		{
			if (arr[j] > arr[j + 1])
			{
				int temp = arr[j];
				arr[j] = arr[j+1];
				arr[j+1] = temp;
			}
		}
	}
}
int main()
{
	int arr[10] = { 4,3,6,9,1,2,10,8,7,5 };
	bubblesort(arr, 10);
	for (int k = 0; k < 10; k++)
	{
		cout << arr[k] << endl;
	}
	system("pause");
	return 0;
}
```

## 11.结构体

### 11.1结构体基本概念

结构体属于用户自定义的数据类型，允许用户储存不同的数据类型

### 11.2结构体定义和使用

语法：```struct 结构体名 {结构体成员列表}；```

![image-20240525170922175](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240525170922175.png)

示例：

![image-20240525171013376](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240525171013376.png)

![image-20240525171055298](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240525171055298.png)

### 11.3结构体数组

作用：将自定义的结构体放入到数组中方便维护

语法：```struct 结构名 数组名[元素个数] = {{}，{}，... {}}```

示例：

```c++
struct student
{
	string name;
	int age;
	int score;
};
int main()
{
	struct student arr[3] =
	{
		{"张三",18,80},
		{"李四",19,60},
		{"王五",20,100}
	};
	for (int i = 0; i < 3; i++)
	{
		cout << arr[i].name << " ";
		cout << arr[i].age << " ";
		cout << arr[i].score << " ";
		cout << endl;
	}
	system("pause");
	return 0;
}
```

### 11.4结构体指针

作用：通过指针访问结构体中的成员

利用操作符`->`可以通过结构体指针访问结构体属性

示例：

```c++
struct student
{
	string name;
	int age;
	int score;
};
int main()
{
	struct student s = { "张三",18,100 };
	struct student* p = &s;
	cout << p->name << p->age << p->score;
	system("pause");
	return 0;
}
```

### 11.5结构体嵌套结构体

作用：结构体中的成员可以是另一个结构体

例如：每个老师辅导一个学员，一个老师的结构体中，记录一个学生的结构体

示例：

```c++
struct student
{
	string name;
	int age;
	int score;
};
struct teacher
{
	int id;
	string name;
	int age;
	struct student stu;
};
int main()
{
	teacher t;
	t.id = 10000;
	t.name = "老王";
	t.age = 50;
	t.stu.name = "小王";
	t.stu.age = 20;
	t.stu.score = 60;

 	system("pause");
	return 0;
}
```

### 11.6结构体做函数参数

作用：将结构体作为参数向函数中传递

传递方式有两种：

1.值传递

2.地址传递

示例：

```c++
struct student
{
	string name;
	int age;
	int score;
};
//值传递
void printStudent1(student stu)
{
	stu.age = 28;
	cout << stu.name << stu.age << stu.score << endl;
}
//地址传递
void printStudent2(struct student* p)
{
	cout << p->name << p->age << p->score << endl;
}

int main()
{
	struct student s;
	s.name = "张三";
	s.age = 20;
	s.score = 85;
	printStudent1(s);
	printStudent2(&s);
	system("pause");
	return 0;
}
```

### 11.7结构体中const使用场景

作用：用const来防止误操作

示例：

```c++
struct student
{
	string name;
	int age;
	int score;
};
void printStudent(const student *s)
{
	//s->age = 100;
	cout << s->name << s->age << s->score << endl;
}
int main()
{
	struct student s = { "张三",15,70 };

	printStudent(&s);
	system("pause");
	return 0;
}
```

# 2.C++核心编程

本阶段主要针对C++面向对象编程技术做详细讲解，探讨C++的核心和精髓

## 1.内存分区模型

![image-20240603193643309](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240603193643309.png)

***内存四区的意义：***

不同区域存放的数据，赋予不同的生命周期，给我们更大的灵活编程

### 1.1程序运行前

![image-20240603194055745](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240603194055745.png)

```c++
#include <iostream>
using namespace std;
//全局变量
int g_a = 10;
int g_b = 10;
const int g_c = 10;
int main()
{
	//全局区
	//全局变量，静态变量，常量
	//创建一个普通的局部变量
	int a = 10;
	int b = 10;
	cout << "地址:" << (int) & a << endl;
	cout << "全局变量：" << (int) & g_a << endl;
	//静态变量,在普通变量前面加static，属于静态变量
	static int s_a = 10;
	static int s_b = 10;
	cout << "静态变量s_a的地址为：" << (int)&s_a << endl;
	cout << "静态变量s_b的地址为：" << (int)&s_b << endl;
	//常量
	//字符串常量
	cout << "字符串常量的地址为：" << (int)&"hello world" << endl;
	//const修饰的变量
	//const修饰的全局变量，const修饰的局部变量
	cout << "全局常量g_c的地址为：" << (int)&g_c << endl;
	const int c_l_a = 10;
	cout << "局部常量c_l_a的地址为：" << (int)&c_l_a << endl;
	system("pause");
	return 0;
}
```

总结：

1.C++中在程序运行前分为全局区和代码区

2.代码区特点是共享和只读

3.全局区中存放全局变量，静态变量，常量

4.常量区中存放const修饰的全局常量和字符串常量

### 1.2程序运行后

**栈区**：

由编译器自动分配释放，存放函数的参数值，局部变量等

注意事项：不要返回局部变量的地址，栈区开辟的数据由编译器自动释放

示例：

```c++
//栈区数据的注意事项
int* func()
{
	int a = 10;
	return &a;
}
int main()
{
	int* p = func();
	cout << *p << endl;//第一次打印正确的数字，是因为编译器做了保留
	cout << *p << endl;//第二次这个数据不再保留
	system("pause");
	return 0;
}
```

**堆区**：

由程序员分配释放，若程序员不释放，程序结束时由操作系统回收

在C++主要利用new在堆区开辟内存

示例:

```c++
//在堆区开辟数据
int* func()
{
	//利用new关键字 可以将数据开辟到堆区
	int* p = new int(10);

	return p;
}
int main()
{
	int* p = func();
	cout << *p << endl;
	system("pause");
	return 0;
}
```

### 1.3new操作符

C++中利用new操作符在堆区开辟数据

地区开辟的数据，由程序员手动开辟，释放利用操作符delete

语法：`new 数据类型`

利用new创建的数据，会返回该数据对应的类型的指针

**new( )** 分配这种类型的一个大小的内存空间,并以括号中的值来初始化这个变量

**new[ ]** 分配这种类型的n个大小的内存空间,并用默认构造函数来初始化这些变量

例：

```c++
void func()
{
	int *p = new int[10];
	for (int i = 0; i != 10; ++i)
	{
		*p = i;
		cout << *p << endl;
	}
}
int main()
{
	func();
}
```



注意：

![image-20240603204501544](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240603204501544.png)

```c++
//new的基本语法
int* func()
{
	//在堆区创建整数数据
	//new返回是 该数据类型的指针
	int *p  = new int(10);
	return p;
}
void test01()
{
	int* p = func();
	cout << *p << endl;
}
int main()
{
	int* p = func();
	cout << *p << endl;
	cout << *p << endl;
	cout << *p << endl;
	//如果想释放堆区的数据，利用关键字delete
	delete p;
	cout << *p << endl;
}
```

## 2.引用

### 2.1引用的基本使用

作用：给变量起别名

语法：`数据类型 &别名 = 原名`

```c++
int main()
{
	int a = 10;
	int& b = a;
	cout << b << endl;//输出也是10
    b = 100;
	cout << a << endl;//输出100
	cout << b << endl;//输出也是100
	system("pause");
	return 0;
}
```

### 2.2引用的注意事项

1.引用必须初始化

2.引用在初始化后，不可以改变

示例：

```c++
int main()
{
	int a = 10;
	//1.引用必须初始化
	//int& b;//错误
	//2.引用在初始化后，不可以改变
	int& b = a;
	int c = 20;
	b = c;//赋值操作，而不是更改引用
	system("pause");
	return 0;
}
```

### 2.3引用做函数参数

作用：函数传参时，可以利用引用的技术让形参修饰实参

优点：可以简化指针修改实参

```c++
//1.值传递
void myswap01(int a, int b)
{
	int temp = a;
	a = b;
	b = temp;
}
//2.地址传递
void myswap02(int* a, int* b)
{
	int temp = *a;
	*a = *b;
	*b = temp;
}
//3.引用传递
void myswap03(int& a, int& b)
{
	int temp = a;
	a = b;
	b = temp;
}
int main()
{
	int a = 10;
	int b = 20;
	myswap01(a, b);//值传递
	cout << "a= " << a << endl;
	cout << "b= " << b << endl;
	myswap02(&a, &b);//地址传递
	cout << "a= " << a << endl;
	cout << "b= " << b << endl;
	myswap03(a, b);//引用传递
	cout << "a= " << a << endl;
	cout << "b= " << b << endl;
	system("pause");
	return 0;
}
```

总结：通过引用参数产生的效果同按地址传递是一样的。引用的语法更清楚简单

### 2.4引用做函数返回值

作用：引用是可以作为函数的返回值存在的

注意：不要返回局部变量引用

用法：函数调用作为左值

```c++
//引用做函数的返回值
//1.不要返回局部变量的引用
int& test01()
{
	int a = 10;
	return a;
}
//2.函数的调用可以作为左值
int& test02()
{
	static int a = 10;//静态变量，存放在全局区
	return a;
}
int main()
{
	int &ref = test01();
	cout << "ref= " << ref << endl;
	int& ref2 = test02();
	cout << "ref2= " << ref2 << endl;
	test02() = 1000;//如果函数的返回值是引用，这个函数调用可以作为左值
	cout << "ref2= " << ref2 << endl;
	system("pause");
	return 0;
}
```

### 2.5引用的本质

本质：引用的本质在C++内部实现是一个指针常量

引用初始化后就不能发生改变

示例：

![image-20240604164827400](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240604164827400.png)

结论：C++推荐用引用技术，因为语法方便，引用的本质是指针常量，但是所有的指针操作编译器都帮我们做了

### 2.6常量引用

作用：常量引用主要来修饰形参，防止误操作

在函数形参列表中，可以加const修饰形参，防止形参改变实参

![image-20240604175252104](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240604175252104.png)

示例2：

```c++
//常量引用
//使用场景：用来修饰形参，防止误操作
int main()
{
	int a = 10;
	int& ref = a;//引用必须引用一块合法的内存空间
	//加上const后，编译器将代码修改，int temp = 10; const int &ref = temp;
	const int& ref = 10;
	system("pause");
	return 0;
}
```

## 3.函数的提高

### 3.1函数默认值

在C++中，函数的形参列表中的形参是可以有默认值的。

语法：`返回值类型 函数名 （参数 = 默认值）{}`

示例：

```c++
//函数默认参数
//如果我们自己传入数据，就用自己的数据，如果没有，那么就用默认值
int func(int a,int b = 20,int c=30)
{
	return a + b + c;
}
//注意事项
//1.如果某个位置已经有了默认参数，那么从这个位置往后，从左到右都必须有默认值
//int func2(int a = 10, int b, int c)
//{
//	return a + b + c;
//}
//2.如果函数声明有默认参数，函数的实现就不能有默认参数
//声明和实现只能有一个默认参数
int func2(int a = 10, int b = 10);
int func2(int a , int b )
{
	return a + b ;
}

int main()
{
	int c = func(10,30);
	cout << c << endl;
	cout << func2() << endl;
	system("pause");
	return 0;
}
```

### 3.2函数的占位参数

C++中函数的形参列表里可以有占位参数，用来做占位，调用函数时必须填补该位置

语法：`返回值类型 函数名 (数据类型) {}`

```c++
//函数的占位参数
//目前阶段的占位参数，我们还用不到
//占位参数还可以有默认参数
void func(int a, int = 10)
{
	cout << "this is func" << endl;
}
int main()
{
	func(10,10);
	system("pause");
	return 0;
}
```

### 3.3函数重载

#### 3.3.1函数重载概述

作用：函数名可以相同，提高复用性

函数重载满足条件：

1.同一个作用域

2.函数名称相同

3.函数参数类型不同 或者 个数不同 或者 顺序不同

注意：函数的返回值不可以作为函数重载的条件

示例：

```c++
//函数重载
//可以让函数名相同，提高复用性
//函数重载的满足条件
//1.同一个作用域下
//2.函数名相同
//3.函数参数类型不同，个数不同，顺序不同
void func()
{
	cout << "func的调用" << endl;
}
void func(int a)
{
	cout << "func的调用!" << endl;
}
void func(double a)
{
	cout << "func的调用!?" << endl;
}
void func(int a,int b)
{
	cout << "func的调用2" << endl;
}
//注意事项
//函数的返回值不可以作为函数重载的条件
int func(int a, int b)
{
	cout << "func的调用2" << endl;
}
int main()
{
	func(10.0);
	system("pause");
	return 0;
}
```

#### 3.3.2函数重载的注意事项

引用作为重载条件

函数重载碰到函数默认参数

**避免使用默认参数进行重载**:

- 当两个重载函数之间的唯一区别是默认参数时，编译器会产生歧义。

示例：

```c++
//函数重载的注意事项
//1.引用作为重载的条件
void fun(int& a)//int &a = 10;不合法
{
	cout << "func(int& a)调用" << endl;
}
void fun(const int& a)//const int &a = 10;合法
{
	cout << "func(const int& a)调用" << endl;
}
//2.函数重载碰到默认参数
void fun2(int a)
{
	cout << "fun2(int a)的调用" << endl;
}
void fun2(int a,int b = 10)
{
	cout << "fun2(int a,int b)的调用" << endl;
}
int main()
{
	/*int a = 10;
	fun(a);*/
	//fun(10);
	//fun2(10);
	fun2(10);//当函数重载碰到默认参数，出现二义性
	system("pause");
	return 0;
}
```

## 4.类和对象

C++面向对象的三大特性为：封装，继承，多态

C++认为万事万物都皆为对象，对象上有其属性和行为

例如：

![image-20240606165717504](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240606165717504.png)

### 4.1封装

#### 4.1.1封装的意义

封装是C++面向对象的三大特性之一

封装的意义：

1.将属性和行为作为一个整体，表现生活中的事物

2.将属性和行为加以权限控制

封装意义一：

在设计类的时候，属性与行为写在一起，表现事物

语法：`class 类名{ 访问权限：属性 / 行为};`

示例1：设计一个圆类，求圆的周长

```c++
//1.圆类
const double PI = 3.14;
class circle 
{
	//访问权限
public:
	//属性
	int m_r;//半径
	//行为
	double calculateZC()
	{
		return 2 * PI * m_r;
	}
};
int main()
{
	//通过圆类创建具体的圆(对象)
	circle c1;
	c1.m_r = 10;
	cout << c1.calculateZC() << endl;
	system("pause");
	return 0;
}
```

示例2：学生类

```c++
class student
{
public:
	string m_name;
	int M_ID;
	void showstudent()
	{
		cout << m_name << " " << M_ID << endl;
	}
	//给姓名赋值
	void setname(string name)
	{
		m_name = name;
	}
	void setid(int ID)
	{
		M_ID = ID;
	}
};
int main()
{
	student s1;
	/*s1.name = "张三";
	s1.ID = 1;
	s1.showstudent();*/
	s1.setname("张三");
	s1.setid(1);
	s1.showstudent();
	system("pause");
	return 0;
}
```

封装的意义二:

类在设计时，可以把属性和行为放在不同的权限下，加以控制

权限访问有三种：

1.public  公共权限  成员类内可以访问  类外可以访问

2.protected  保护权限  成员类内可以访问  类外不可以访问  儿子也可以访问父亲中的保护内容

3.private  私有权限  成员类内可以访问  类外不可以访问  儿子不可以访问父亲的私有内容

```c++
//访问权限
//三种
//公共权限  public      成员类内可以访问  类外可以访问
//保护权限  protected   成员类内可以访问  类外不可以访问  儿子也可以访问父亲中的保护内容
//私有权限  private     成员类内可以访问  类外不可以访问  儿子不可以访问父亲的私有内容

class Person
{
public:
	//公共权限
	string m_name;
protected:
	//保护权限
	string m_car;
private:
	//私有权限
	int m_Password;
public:
	void func()
	{
		m_name = "张三";
		m_car = "拖拉机";
		m_Password = 123456;
	}
};
int main()
{
	Person s1;
	s1.m_name = "李四";

	system("pause");
	return 0;
}
```

#### 4.1.2struct和class的区别

在C++中struct和class唯一的区别就在于默认的访问权限不同

区别：

struct默认权限为公共

class默认权限为私有

```c++
//struct 和 class区别
class c1
{
	//private
	int m_a;
};
struct c2
{
	//public
	int m_a;
};
int main()
{
	c1 c1;
	//c1.m_a = 100;
	c2 c2;
	c2.m_a = 20;
	cout << c2.m_a << endl;
	system("pause");
	return 0;
}
```

#### 4.1.3成员属性设置为私有

优点1：将所有成员属性设置为私有，可以自己控制读写权限

优点2：对于写权限，我们可以检测数据的有效性

示例：

```c++
//成员属性设置为私有
class Person
{
public:
	//设置姓名
	void setname(string name)
	{
		m_name = name;
	}
	//获取姓名
	string getname()
	{
		return m_name;
	}
	int getage()
	{
		return m_age;
	}
	//设置偶像
	void setTdol(string Idol)
	{
		m_Tdol = Idol;
	}
	//设置年龄（0-150）
	void setage(int age)
	{
		if (age < 0 || age>150)
		{
			cout << "错误" << endl;
			return;
		}
		m_age = age;
	}
private:
	string m_name;//姓名 可读可写
	int m_age=18;//年龄 只读 //可读可写(年龄在0-150之间)
	string m_Tdol;//偶像 只写
};

int main()
{
	Person p;
	p.setname("张三");
	cout << p.getname() << endl;
	cout << p.getage() << endl;
	system("pause");
	return 0;
}
```

#### 4.1.4案例一：设计立方体类

```c++
//案例：设计立方体类
class cube
{
public:
	//设置长
	void setl(int l)
	{
		m_l = l;
	}
	//获取长
	int getl()
	{
		return m_l;
	}
	//设置宽
	void setw(int w)
	{
		m_w = w;
	}
	//获取宽
	int getw()
	{
		return m_w;
	}
	//设置高
	void seth(int h)
	{
		m_h = h;
	}
	//获取高
	int geth()
	{
		return m_h;
	}
	//获取立方体面积
	int calculates()
	{
		return 2 * m_l * m_w + 2 * m_w * m_h + 2 * m_l * m_h;
	}
	//获取立方体体积
	int calculatev()
	{
		return m_l * m_w * m_h;
	}
private:
	int m_l;//长
	int m_w;//宽
	int m_h;//高
};
int main()
{
	cube c1;
	c1.setl(10);
	c1.seth(10);
	c1.setw(10);
	c1.calculates();
	c1.calculatev();
	cout << c1.calculates() << endl;
	cout << c1.calculatev() << endl;
	system("pause");
	return 0;
}
```

### 4.2对象的初始化和清理

C++中的面向对象来源于生活，每个对象也都会有初始设置以及对象销毁前的清理数据的设置

#### 4.2.1构造函数和祈构函数

![image-20240607215234596](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240607215234596.png)

##### 构造函数：`类名(){}`

1.构造函数，没有返回值也不写void

2.函数名称与类名相同

3.构造函数可以有参数，因此可以发生重载

4.程序在调用对象时候会自动调用构造，无须手动调用，而且只会调用一次

##### 祈构函数：`~类名(){}`

1.祈构函数，没有返回值也不写void

2.函数名称与类名相同，在名称前加上符号~

3.祈构函数不可以有参数，因此不可以发生重载

4.程序在对象销毁前会自动调用构造，无须手动调用，而且只会调用一次

```c++
class Person
{
public:
	//构造函数
	Person()
	{
		cout << "Person构造函数的调用" << endl;
	}
	//祈构函数 进行清理操作
	~Person()
	{
		cout << "Person的祈构函数调用" << endl;
	}
};

void test01()
{
	Person p;//在栈上的数据，test01执行完毕后，释放这个对象
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 4.2.2构造函数的分类和调用

两种分类方式：

​			按参数分为：有参构造和无参构造

​			按类型分为：普通构造和拷贝构造

三种调用方式：

​		括号法

​		显示法

​		隐式转换法

示例：

```c++
//分类
class Person
{
public:
	//构造函数
	Person()
	{
		cout << "Person的无参构造函数调用" << endl;
	}
	Person(int a)
	{
		age = a;
		cout << "Person的有参构造函数调用" << endl;
	}
	//拷贝构造函数
	Person(const Person& p)
	{
		cout << "Person的拷贝构造函数调用" << endl;
		//将传入的人身上的所有属性，拷贝到我身上
		age = p.age;
	}
	//祈构函数
	~Person()
	{
		cout << "Person的祈构函数调用" << endl;
	}
	int age;
};
//调用
void test01()
{
	//1.括号法
	//Person p1;//默认构造函数调用
	//Person p2(10);//有参构造函数
	//Person p3(p2);//拷贝构造函数
	//注意事项
	//调用默认构造函数时，不要加（）
	//因为下面这行代码，编译器认为是一个函数的声明，不会认为在创建对象
	//Person p1();
	//cout << "p2的年龄为：" << p2.age << endl;
	//cout << "p3的年龄为：" << p3.age << endl;
	//2. 显示法
	//Person p1;
	//Person p2 = Person(10);//有参构造
	//Person p3 = Person(p2);//拷贝构造
	//Person(10);//匿名对象  特点：当前行执行结束后，系统会立即回收掉匿名对象
	//cout << "aaaaa" << endl;
	//注意：不要利用拷贝构造函数初始化匿名对象
	// 编译器会认为Person(p3) == Person p3;对象声明
	// Person(p3);
	//3.隐式转换法
	Person p4 = 10;//相当于 写了 Person p4 = Person(10);
	Person p5 = p4;//拷贝构造
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 4.2.3拷贝构造函数调用时机

C++中拷贝构造函数调用时机通常有三种情况

1.使用一个已经创建完毕的对象来初始化对象

2.值传递的方式给函数参数传参

3.以值方式返回局部对象

示例：

```c++
//拷贝构造函数调用时机

class Person
{
public:
	Person()
	{
		cout << "Person构造函数调用" << endl;
	}
	Person(int age)
	{
		m_age = age;
	}
	Person(const Person& p)
	{
		cout << "Person拷贝构造函数调用" << endl;
		m_age = p.m_age;
	}
	~Person()
	{
		cout << "Person祈构函数调用" << endl;
	}
	int m_age;
};

//1.使用一个已经创建完毕的对象来初始化对象
void test01()
{
	Person p1(20);
	Person p2(p1);
}
//2.值传递的方式给函数参数传参
void dowork(Person p)
{

}
void test02()
{
	Person p;
	dowork(p);
}
//3.以值方式返回局部对象
Person dowork02()
{
	Person p1;
	cout << (int*)&p1 << endl;
	return p1;

}
void test03()
{
	Person p = dowork02();
	cout << (int*)&p << endl;
}
int main()
{
	//test01();
	//test02();
	test03();
	system("pause");
	return 0;
}
```

#### 4.2.4构造函数调用规则

默认情况下，C++编译器至少给一个类添加三个函数

1.默认构造函数(无参，函数体为空)

2.默认祈构函数(无参，函数体为空)

3.默认拷贝构造函数，对属性进行值拷贝

构造函数调用规则如下：

1.如果用户定义有参构造函数，C++不在提供默认无参构造，但是会提供默认拷贝构造

2.如果用户定义拷贝构造函数，C++不会再提供其他构造函数

示例：

```c++
//构造函数的调用规则
class Person
{
public:
	/*Person()
	{
		cout << "Person的默认构造函数调用" << endl;
	}*/
	Person(int age)
	{
		cout << "Person的有参构造函数调用" << endl;
		m_age = age;
	}
	/*Person(const Person& p)
	{
		cout << "Person的拷贝构造函数调用" << endl;
		m_age = p.m_age;
	}*/
	~Person()
	{
		cout << "Person的祈构函数调用" << endl;
	}
	int m_age;
};
//void test01()
//{
//	Person p;
//	p.m_age = 18;
//	Person p2(p);
//	cout << p2.m_age << endl;
//}
void test02()
{
	Person p(28);
	Person p2(p);
}
int main()
{
	//test01();
	test02();
	system("pause");
	return 0;
}
```

#### 4.2.5深拷贝与浅拷贝

深浅拷贝是面试经典问题，也是常见的一个坑

浅拷贝：简单的赋值拷贝操作，浅拷贝创建一个新对象，但不复制对象中的引用或指针指向的实际数据。相反，它复制对象中的指针或引用，因此新旧对象共享同一块内存。这意味着对一个对象中共享数据的修改会影响另一个对象。

eg：`m_age = p.m_age;  // 浅拷贝：只复制指针，两个对象共享同一内存`

深拷贝：在堆区重新申请空间，进行拷贝操作，深拷贝不仅创建一个新对象，还复制对象中指针或引用指向的实际数据。这样，新对象和原对象互不影响，对一个对象的修改不会影响另一个对象。

eg：`m_age = new int(*p.m_age);  // 深拷贝：复制指针指向的数据`

类有先进后出的特性

浅拷贝带来的问题是：堆区的内存重复释放(浅拷贝的问题要利用深拷贝进行解决)

示例：

```c++
//深拷贝与浅拷贝

class Person
{
public:
	Person()
	{
		cout << "Person的默认构造函数调用" << endl;
	}
	//浅拷贝
	Person(int age,int height)
	{
		cout << "Person的有参构造函数调用" << endl;
		m_age = age;
		m_height =new int(height);
	}
	//深拷贝
	Person(const Person& p)
	{
		cout << "Person的拷贝构造函数调用" << endl;
		m_age = p.m_age;
		//m_height = p.m_height;编译器默认实现就是这行代码
		//深拷贝操作
		m_height = new int(*p.m_height);
	}
	~Person()
	{
		if (m_height != NULL)
		{
			delete m_height;
			m_height = NULL;
		}
		cout << "Person的祈构函数调用" << endl;
	}
	
	int m_age; //年龄
	int* m_height; //身高
};
void test01()
{
	Person p1(18,170);
	Person p2(p1);
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

总结：如果属性有在堆区开辟的，一定要自己提供拷贝构造函数，防止浅拷贝带来的问题

#### 4.2.6初始化列表

作用：

C++提供了初始化列表语法，用来初始化属性

语法：`构造函数()：属性1(值1)，属性2(值2) ... {}`

示例：

```c++
//初始化列表

class Person
{
public:
	
	//传统初始化操作
	/*Person(int a, int b, int c)
	{
		m_a = a;
		m_b = b;
		m_c = c;
	}*/
	//初始化列表
	Person(int a,int b,int c) :m_a(a), m_b(b), m_c(c)
	{

	}
	int m_a;
	int m_b;
	int m_c;
};
void test01()
{
	//Person p(10, 20, 30);
	Person p(30,20,10);
	cout << "m_a = " << p.m_a << endl;
	cout << "m_b = " << p.m_b << endl;
	cout << "m_c = " << p.m_c << endl;
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 4.2.7类对象作为类成员

C++类中的成员可以是另一个类的对象，我们称该成员为对象成员

例如：

```c++
class A {}
class b
{
    A a;
}
```

B类中有对象A作为成员，A为对象成员

示例：

```c++
#include <iostream>
#include <string>
using namespace std;

class Phone {
public:
	Phone(string name) {
		m_pname = name;
	}
	~Phone() {
		cout << "Phone的析构函数调用" << endl;
	}
	string m_pname;
};

class Person {
public:
	Person(string m_name, string pname) :m_name(m_name), m_phone(pname) {}

	~Person() {
		cout << "Person的析构函数调用" << endl;
	}

	string m_name;
	Phone m_phone;
};

void test01()
{
	 Person p("张三", "abab"); // 将 Phone 对象传递给 Person 的构造函数

	cout << p.m_name << " " << p.m_phone.m_pname << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 4.2.8静态对象

静态对象就是在成员变量和成员函数前加上关键字static，称为静态成员

静态成员分为：

静态成员变量：

​		所有对象共享同一份数据

​		在编译阶段分配内存

​		类内声明，类外初始化

静态成员函数：

​		所有对象共享同一个函数

​		静态成员函数只能访问静态成员变量

示例1：静态成员变量

```c++
//静态成员变量
class Person
{
public:
	//所有对象共享同一份数据
	//编译阶段就分配内存
	//类内声明，类外初始化操作
	static int m_a;
	//静态成员变量也是有访问权限的
private:
	static int m_b;
};
int Person::m_a = 100;
int Person::m_b = 200;
void test01()
{
	Person p;
	cout << p.m_a << endl;
	Person p2;
	p2.m_a = 200;
	cout << p.m_a << endl;
}
void test02()
{
	//静态成员变量 不属于某个对象上，所有对象都共享同一份数据
	//因此静态成员变量有两种访问方式
	//1.通过对象进行访问
	Person p;
	cout << p.m_a << endl;
	//2.通过类名进行访问
	cout << Person::m_a << endl;
	//cout << Person::m_b << endl;
}
int main()
{
	//test01();
	test02();
	system("pause");
	return 0;
}
```

示例2：静态成员函数

```c++
//静态成员函数
class Person
{
public:
	static void func()
	{
		m_a = 100;
		//m_b = 200;//静态成员函数不可以访问非静态成员变量，无法区分到底是哪个对象的m_b
		cout << "static void func调用" << endl;
	}
	//静态访问函数也是有权限的
private:
	static void func2()
	{
		cout << "static void func调用" << endl;
	}
	static int m_a;
	int m_b;
};
int Person::m_a = 0;
void test01()
{
	//1.通过对象访问
	Person p;
	p.func();
	//2.通过类名访问
	Person::func;
	//Person::func2();
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

### 4.3C++对象模型和this指针

#### 4.3.1成员变量和成员函数分开储存

在C++中，类内的成员变量和成员函数分开储存

只有非静态成员变量才属于类的对象上

```c++
//成员变量和成员函数分开储存
class Person
{
	int m_a;//非静态成员变量,属于类的对象上
	static int m_b;//静态成员变量，不属于类的对象上
	void func(){}//非静态成员函数，不属于类的对象上
	static void func2() {}//静态成员函数
};
void test01()
{
	Person p;
	//空对象占用内存空间为：1
	//C++编译器会给每个空对象也分配一个字节空间，是为了区分空对象占内存的位置
	//每个空对象也应该有一个独一无二的内存地址
	cout << "sizeof p = " << sizeof(p) << endl;
}
void test02()
{
	Person p;
	cout << "sizeof p = " << sizeof(p) << endl;
}
int main()
{
	//test01();
	test02();
	system("pause");
	return 0;
}
```

#### 4.3.2this指针概念

![image-20240610181558432](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240610181558432.png)

this指针的用途：

1.当形参和成员变量同名时，可用this指针来区分

2.在类的非静态成员函数中返回对象本身，可用return *this

```c++
class Person
{
public:
	Person(int age)
	{
		//this指针指向被调用的对象函数所属的对象
		this->age = age;
	}

	Person& PersonAddAge(Person &p)
	{
		this->age += p.age;
		//this指向p2的指针，而*this指向的就是p2这个对象本体
		return *this;
	}

	int age;
};
//1.解决名称冲突
void test01()
{
	Person p1(18);
	cout << "p1的年龄为：" << p1.age << endl;
}
//2.返回对象本身用*this
void test02()
{
	Person p1(10);

	Person p2(10);
	//链式编程思想
	p2.PersonAddAge(p1).PersonAddAge(p1).PersonAddAge(p1);
	cout << "p2的年龄为：" << p2.age << endl;
}
int main()
{
	//test01();
	test02();
	system("pause");
	return 0;
}
```

#### 4.3.3空指针访问成员函数

C++中空指针也是可以调用成员函数的，但是也要注意有没有用到this指针

如果用到this指针，需要加以判断保证代码的健壮性

示例：

```c++
//空指针调用成员函数

class Person
{
public:
	void showclassname()
	{
		cout << "this is Person class" << endl;
	}

	void showpersonage()
	{
		//报错的原因是因为传入的指针是为NULL
		if (this == NULL)
		{
			return;
		}
		cout << "age = " << this->m_age << endl;
	}

	int m_age;
};
void test01()
{
	Person* p = NULL;

	//p->showclassname();

	p->showpersonage();

}

int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 4.3.4const修饰成员函数

常函数：

1.成员函数后加const后我们称这个函数为常函数

2.常函数内不可以修改成员属性

3.成员属性声明时加关键字mutable后，在常函数中依然可以修改

常对象：

1.声明对象前加const称该对象为常对象

2.常对象只能调用常函数

```c++
//常函数
class Person
{
public:
	//this指针的本质 是指针常量 指针的指向是不可以修改的
	//const Person * const this
	//在成员函数后面加const，修饰的是this指针，让指针指向的值也不可以修改
	void showperson()const
	{
		this->m_b = 100;
		//this->m_a = 100;
		//this = NULL;//this指针不可以修改指针的指向
	}
	void func()
	{
		m_a = 100;
	}
	int m_a;
	mutable int m_b;//特殊变量，即使在常函数中，也可以修改这个值
};
void test01()
{
	Person p;
	p.showperson();
	p.func();
}
//常对象

void test02()
{
	const Person p;//在对象前加const，变为常对象
	//p.m_a = 100;
	p.m_b = 100;//m_b是特殊值，在常对象下也可以修改
	//常对象只能调用常函数
	p.showperson();
	//p.func();//常对象不可以调用普通成员函数，因为普通成员函数可以修改属性
}
int main()
{
	test01();
	test02();
	system("pause");
	return 0;
}
```

### 4.4友元

在 C++ 中，**友元（friend）** 关键字允许一个类或函数访问另一个类的私有（private）和保护（protected）成员。通常，类的私有和保护成员只能被该类的成员函数或友元函数访问。友元机制允许你为特定的类或函数提供这种访问权限，而无需使用公共接口。

![image-20240611163518150](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240611163518150.png)

友元的三种实现

1.全局函数做友元

2.类做友元

3.成员函数做友元

#### 4.4.1全局函数做友元

```c++
//全局函数做友元
class Building
{
	//goodgay全局函数是buliding的好朋友，可以访问buliding中私有成员
	friend void goodgay(Building& buliding);
public:
	Building()
	{
		m_sittingroom = "客厅";
		m_bedroom = "卧室";
	}
public:
	string m_sittingroom;//客厅
private:
	string m_bedroom;//卧室
};
//全局函数
void goodgay(Building &buliding)
{
	cout << buliding.m_sittingroom << endl;
	cout << buliding.m_bedroom << endl;
}
void test01()
{
	Building buliding;
	goodgay(buliding);
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 4.4.2类做友元

```c++
//类做友元
class Building;
class goodgay
{
public:
	goodgay();
	void visit();//参观函数，访问Building中的属性
	Building* building;
};
class Building
{
	friend class goodgay;
public:
	Building();
public:
	string m_sittingroom;//客厅
private:
	string m_bedroom;//卧室
};
//类外写成员函数
Building::Building()
{
	m_sittingroom = "客厅";
	m_bedroom = "卧室";
}
goodgay::goodgay()
{
	building = new Building;
}
void goodgay::visit()
{
	cout << building->m_sittingroom << endl;
	cout << building->m_bedroom << endl;
}
void test01()
{
	goodgay gg;
	gg.visit();
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 4.4.3成员函数做友元

```c++
//成员函数做友元
class Building;
class goodgay
{
public:
	goodgay();
	void visit();//让visit函数可以访问Building中私有成员
	void visit2();//让visit2函数不可以访问Building中私有成员
	Building* building;
};
class Building
{
	friend void goodgay::visit();
public:
	Building();
public:
	string m_sittingroom;
private:
	string m_bedroom;
};
//类外实现成员函数
Building::Building()
{
	m_sittingroom = "客厅";
	m_bedroom = "卧室";
}
goodgay::goodgay()
{
	building = new Building;
}
void goodgay::visit()
{
	cout << building->m_sittingroom << endl;

	cout << building->m_bedroom<< endl;
}
void goodgay::visit2()
{
	cout << building->m_sittingroom << endl;

	//cout << building->m_bedroom << endl;
}
void test01()
{
	goodgay gg;
	gg.visit();
	gg.visit2();
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

### 4.5运算符重载

运算符重载的概念：对已有的运算符重新进行定义，赋予其另一种功能，以适应不同的数据类型

#### 4.5.1加号运算符重载

作用：实现两个自定义数据类型相加的运算

```c++
//加号运算符重载
class Person
{
public:
	//1.成员函数重载+号
	/*Person operator+(Person& p)
	{
		Person temp;
		temp.m_a = this->m_a + p.m_a;
		temp.m_b = this->m_b + p.m_b;
		return temp;
	}*/
	int m_a;
	int m_b;
};
//2.全局函数重载+号
Person operator+(Person& p1, Person& p2)
{
	Person temp;
	temp.m_a = p1.m_a + p2.m_a;
	temp.m_b = p1.m_b + p2.m_b;
	return temp;
}
void test01()
{
	Person p1;
	p1.m_a = 10;
	p1.m_b = 10;
	Person p2;
	p2.m_a = 10;
	p2.m_b = 10;
	Person p3 = p1 + p2; 
	cout << p3.m_a << endl;
	cout << p3.m_b << endl;
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

总结1：对于内置的数据类型的表达式的运算符是不可能改变的

总结2：不要滥用运算符重载

#### 4.5.2左移运算符重载

作用：可以输出自定义数据类型

```c++
//左移运算符
class Person
{
	friend ostream& operator<<(ostream& cout, Person& p);
	//friend void test01();
public:
	Person(int a, int b)
	{
		m_a = a;
		m_b = b;
	}
	//利用成员函数重载左移运算符 p.operator<<(cout) 简化版本 p<<cout
	//不会利用成员函数重载<<运算符，因为无法实现cout在左侧
	/*void operator<<(Person& p)
	{

	}*/
private:
	int m_a;
	int m_b;
};
//只能利用全局函数重载左移运算符
ostream & operator<<(ostream &cout,Person &p)  //本质 operator<<(cout,p) 简化 cout << p
{
	cout << p.m_a << " " << p.m_b << endl;
	return cout;
}
void test01()
{
	Person p(10,10);
	cout << p << endl;
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

总结：重载左移运算符配合友元可以实现输出自定义的类型

#### 4.5.3递增运算符重载

作用：通过重载递增运算符，实现自己的整型数据

```c++
//递增运算符重载
//自定义整型
class MyIntager
{
	friend ostream& operator<<(ostream& cout, MyIntager myint);
public:
	MyIntager()
	{
		m_num = 0;
	}
	//重载前置++运算符 返回引用是为了对一个数据进行递增
	MyIntager &operator++()
	{
		m_num++;
		return* this;
	}
	//重载后置++运算符
	//int代表的是一个占位参数，可以用于区分前置和后置递增
	MyIntager operator++(int)
	{
		//先
		MyIntager temp = *this;
		//后
		m_num++;
		return temp;
	}
private:
	int m_num;
};
//重载左移运算符
ostream& operator<<(ostream& cout, MyIntager myint)
{
	cout << myint.m_num;
	return cout;
}
void test01()
{
	MyIntager myint;
	cout << ++(++myint) << endl;
}
void test02()
{
	MyIntager myint;
	cout << myint++ << endl;
	cout << myint << endl;
}
int main()
{
	//test01();
	test02();
	system("pause");
	return 0;
}
```

总结：前置递增返回引用，后置递增返回值

#### 4.5.4赋值运算符重载

C++编译器至少给一个类添加四个函数

1.默认构造函数(无参，函数体为空)

2.默认祈构函数(无参，函数体为空)

3.默认拷贝构造函数，对属性进行值拷贝

4.赋值运算符operator=，对属性进行值拷贝

如果类中有属性指向堆区，做赋值操作时也会出现深浅拷贝的问题

```c++
//赋值运算符重载

class Person
{
public:
	Person(int age)
	{
		m_age = new int(age);
	}
	~Person()
	{
		if (m_age != NULL)
		{
			delete m_age;
			m_age = NULL;
		}
	}
	//重载赋值运算符
	Person &operator=(Person &p)
	{
		//先判断是否有属性在堆区，如果有先释放干净，然后再深拷贝
		if (m_age != NULL)
		{
			delete m_age;
			m_age = NULL;
		}
		m_age = new int(*p.m_age);
		return *this;
	}
	int* m_age;
};

void test01()
{
	Person p1(18);
	Person p2(20);
	Person p3(30);
	p3 = p2 = p1;
	cout << *p1.m_age << endl;
	cout << *p2.m_age << endl;
	cout << *p3.m_age << endl;
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 4.5.5关系运算符重载

作用：重载关系运算符，可以让两个自定义类型对象进行对比操作

示例：

```c++
//关系运算符重载
class Person
{
public:
	Person(string name,int age)
	{
		m_name = name;
		m_age = age;
	}
	//重载 == 号
	bool operator==(Person& p)
	{
		if (this->m_name == p.m_name && this->m_age == p.m_age)
		{
			return true;
		}
		return false;
	}
	string m_name;
	int m_age;
};
void test01()
{
	Person p1("Tom",18);
	Person p2("Jerry", 18);
	if (p1 == p2)
	{
		cout << "p1和p2是相等的" << endl;
	}
	else
	{
		cout << "p1和p2是不相等的" << endl;
	}
	
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 4.5.6函数调用运算符重载

1.函数调用运算符()也可以重载

2.由于重载后使用的方式非常像函数的调用，因此称为仿函数

3.仿函数没有固定写法，非常灵活

示例：

```c++
//函数调用重载
//打印输出类
class Myprint
{
public:
	//重载函数调用运算符
	void operator()(string test)
	{
		cout << test << endl;
	}

};
void test01()
{
	Myprint myprint;
	myprint("hello world");//由于使用起来非常类似于函数调用，因此称为仿函数
}
//仿函数非常灵活，没有固定的写法
//加法类

class MyAdd
{
public:
	int operator()(int num1, int num2)
	{
		return num1 + num2;
	}
};
void test02()
{
	MyAdd myadd;
	int result = myadd(100, 100);
	cout << "result = " << result << endl;
	//匿名函数对象
	cout << MyAdd()(100, 100) << endl;
}
int main()
{
	//test01();
	test02();
	system("pause");
	return 0;
}
```

### 4.6继承

继承是面向对象三大特性之一

![image-20240614151457689](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240614151457689.png)

#### 4.6.1继承的基本语法

继承的好处：减少重复代码

语法：`class 子类 : 继承方式 父类`

子类也被称为派生类

父类也被称为基类

派生类中的成员，包含两大部分：

一类是从基类继承过来的，一类是自己增加的成员。

从基类继承过来的表现其共性，而新增的成员体现了其个性

#### 4.6.2继承方式

继承的语法：`class 子类 : 继承方式 父类`

继承方式一共有三种：

1.公共继承

2.保护继承

3.私有继承

![image-20240614152904094](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240614152904094.png)

```c++
//继承方式
//公共继承
class Base1
{
public:
	int m_a;
protected:
	int m_b;
private:
	int m_c;
};
class Son1 :public Base1
{
public:
	void func()
	{
		m_a = 10;//父类中的公共权限成员，到子类中依然是公共权限
		m_b = 10;//父类中的保护权限成员，到子类中依然是保护权限
		//m_c = 10;//父类中的私有权限成员，子类访问不到
	}
};

void test01()
{
	Son1 s1;
	s1.m_a = 100;
	//s1.m_b = 100;//到Son1中m_b是保护权限，类外访问不到
}
//保护继承
class Base2
{
public:
	int m_a;
protected:
	int m_b;
private:
	int m_c;
};
class Son2 :protected Base2
{
public:
	void func()
	{
		m_a = 100;//父类中公共成员，到子类中变为保护权限
		m_b = 100;//父类中保护成员，到子类中变为保护权限
		//m_c = 100;//父类子类访问不到，子类访问不到
	}
};
void test02()
{
	Son2 s1;
	//s1.m_a = 1000;//在Son2中m_a变为保护权限，因此类外访问不到
	//s1.m_b = 1000;//在Son2中m_b保护权限，不可以访问
}
//私有继承
class Base3
{
public:
	int m_a;
protected:
	int m_b;
private:
	int m_c;
};
class Son3 :private Base3
{
public:
	void func()
	{
		m_a = 100;//父类中公共成员，到子类中变为私有成员
		m_b = 100;//父类中保护成员，到子类中变为私有成员
		//m_c=100;//父类中私有成员，子类访问不到
	}
};
class GrandSon3 :public Son3
{
public:
	void func()
	{
		//私有成员
		//m_a = 1000;
		//m_b = 1000;
	}
};
int main()
{
	system("pause");
	return 0;
}
```

#### 4.6.3继承中的对象模型

父类中所有非静态成员属性都会被子类继承下去

父类中私有成员属性是被编译器给隐藏了，因此是访问不到，但的确被继承下去了

```c++
//继承中的对象模型
class Base
{
public:
	int m_a;
protected:
	int m_b;
private:
	int m_c;
};
class Son :public Base
{
public:
	int m_d;
};
void test01()
{
	cout << "size of Son = " << sizeof(Son) << endl;
}
int main()
{
	test01();//16
	system("pause");
	return 0;
}
```

结论：父类中私有成员也是被子类继承下去了，只是由编译器给隐藏后访问不到

#### 4.6.4继承中构造和祈构顺序

子类继承父类后，当创建子类对象，也会调用父类的构造函数

继承中的构造和祈构顺序如下：

先构造父类，再构造子类，祈构的顺序与构造的顺序相反

示例：

```c++
//继承中构造和祈构顺序
class Base
{
public:
	Base()
	{
		cout << "Base构造函数!" << endl;
	}
	~Base()
	{
		cout << "Base祈构函数!" << endl;
	}
};
class Son:public Base
{
public:
	Son()
	{
		cout << "Son构造函数!" << endl;
	}
	~Son()
	{
		cout << "Son祈构函数!" << endl;
	}
};
void test01()
{
	//Base b;
	Son b;
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

总结：继承中先调用父类构造函数，再调用子类构造函数，祈构函数与构造相反

#### 4.6.5继承同名成员处理方式

1.访问子类同名成员，直接访问即可

2.访问父类同名成员，需要加作用域

```c++
//继承同名成员处理方式
class Base
{
public:
	Base()
	{
		m_a = 100;
	}
	void func()
	{
		cout << "Base - func()调用" << endl;
	}
	void func(int a)
	{
		cout << "Base - func(int a)调用" << endl;
	}
	int m_a;
};
class Son :public Base
{
public:
	Son()
	{
		m_a = 200;
	}
	void func()
	{
		cout << "Son - func()调用" << endl;
	}
	int m_a;
};
//同名的属性的处理方式
void test01()
{
	Son s;
	cout << s.m_a << endl;
	cout << s.Base::m_a << endl;
}
//同名的函数的处理方式
void test02()
{
	Son s;
	s.func();//直接调用，调用的是子类中的同名成员
	s.Base::func();//调用父类中的函数
	//如果子类中出现和父类同名的成员函数，子类的同名成员会隐藏掉父类中所有同名成员函数
	//如果想访问到父类中被隐藏的同名成员函数，需要加作用域
	s.Base::func(10);
}
int main()
{
	//test01();
	test02();
	system("pause");
	return 0;
}
```

总结：

1.子类对象可以直接访问到子类中同名成员

2.子类对象加作用域可以访问到父类同名成员

3.当子类与父类拥有同名的成员函数，子类会隐藏父类中同名成员函数，加作用域可以访问到父类中同名函数

#### 4.6.6继承中同名静态成员处理方式

静态成员和非静态成员出现同名，处理方式一致

1.访问子类同名成员，直接访问即可

2.访问父类同名成员，需要加作用域

```c++
//继承同名静态成员处理方式
class Base
{
public:
	static int m_a;

	static void func()
	{
		cout << "Base - static void func()" << endl;
	}

	static void func(int a)
	{
		cout << "Base - static void func(int a)" << endl;
	}
};
int Base::m_a = 100;
class Son:public Base
{
public:
	static int m_a;

	static void func()
	{
		cout << "Son - static void func()" << endl;
	}

	
};
int Son::m_a = 200;
//同名的静态成员属性
void test01()
{
	//1.通过对象访问数据
	Son s;
	cout << s.m_a << endl;
	cout << s.Base::m_a << endl;
	//2.通过类名访问
	cout << Son::m_a << endl;
	//第一个::代表通过类名方式访问，第二个::代表访问父类作用域下
	cout << Son::Base::m_a << endl;
}
//同名的静态成员函数
void test02()
{
	//1.通过对象的方式来访问
	Son s;
	s.func();
	s.Base::func();
	//2.通过类名的方式来访问
	Son::func();
	Son::Base::func();
	//子类出现和父类同名静态成员函数，也会隐藏父类中所有同名成员函数
	//如果想访问到父类中被隐藏的同名成员函数，需要加作用域
	Son::Base::func(100);
}
int main()
{
	//test01();
	test02();
	system("pause");
	return 0;
}
```

总结：同名静态成员处理方式和非静态处理方式一样，只不过有两种访问方式(通过对象和通过类名)

#### 4.6.7多继承语法

C++允许一个类继承多个类

语法：`class 子类 ：继承方式 父类1，继承方式  父类2...`

多继承可能会引发父类中有同名成员出现，需要加作用域区分

C++实际开发中不建议用多继承

```c++
//多继承语法
class Base1
{
public:
	Base1()
	{
		m_a = 100;
	}
	int m_a;
};
class Base2
{
public:
	Base2()
	{
		m_b = 200;
	}
	int m_b;
};
//子类需要继承Base1和Base2
class Son :public Base1, public Base2
{
public:
	Son()
	{
		m_c = 300;
		m_d = 400;
	}
	int m_c;
	int m_d;
};
void test01()
{
	Son s;
	cout << sizeof(s) << endl;
	s.Base1::m_a;
	s.Base2::m_b;
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

总结：多继承中如果父类中出现了同名情况，子类使用时要加作用域

#### 4.6.8菱形继承

菱形继承概念：

两个派生类继承同一个基类

又有某个类同时继承两个派生类

这种继承被称为菱形继承，或者钻石继承

典型的菱形继承案例：

![image-20240615191155245](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240615191155245.png)

菱形继承问题：

![image-20240615191352180](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240615191352180.png)

示例：

```c++
//菱形继承
//动物类
class Animal
{
public:
	int m_age;
};

//利用虚继承，解决菱形继承的问题
//继承之前，加上关键字virtual变为虚继承
//Animal类称为 虚基类
//羊类
class Sheep:virtual public Animal{};

//驼类
class Tuo:virtual public Animal{};

//羊驼类
class SheepTuo :public Sheep, public Tuo
{

};

void test01()
{
	SheepTuo st;
	st.Sheep::m_age = 18;
	st.Tuo::m_age = 28;
	//当菱形继承，两个父类拥有相同的数据，需要加以作用域区分
	cout << st.Sheep::m_age << endl;
	cout << st.Tuo::m_age << endl;
	//这份资源我们知道，只要有一份就可以，菱形继承导致数据有两份，资源浪费
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

在虚继承情况下，派生类中只有一个基类的实例。因此，不管通过哪个派生类来访问基类的成员变量，都是访问同一个实例。所以设置`st.Tuo::m_age`为28后，`st.Sheep::m_age`也会是28，因为它们指向的是同一个`Animal`实例。

总结：

1.菱形继承带来的主要问题是子类继承两份相同的数据，导致资源浪费以及毫无意义

2.利用虚继承可以解决菱形继承问题

注：虚继承（Virtual Inheritance）是C++中的一个特性，用于解决多重继承（Multiple Inheritance）中的“菱形继承”（Diamond Inheritance）问题。菱形继承问题会导致基类的多个副本在派生类中存在，从而引发数据冗余和歧义。虚继承通过确保基类在派生类中只有一个共享副本来解决这个问题。

虚继承通过确保只有一个基类副本来解决这个问题。在派生类继承基类时使用 `virtual` 关键字即可实现虚继承：

```c++
class A {
public:
    int value;
};

class B : public virtual A {};

class C : public virtual A {};

class D : public B, public C {};

```

通过这种方式，类 `D` 中的 `A` 类只有一个共享副本。

```c++
D d;
d.value = 10; // 直接访问唯一的 A 的 value

std::cout << d.value << std::endl; // 输出 10
```

### 4.7多态

#### 4.7.1多态的基本概念

多态是C++面向对象三大特性之一

多态分为两类

1.静态多态：函数重载和运算符重载属于静态多态，复用函数名

2.动态多态：派生类和虚函数实现运行时多态

静态多态和动态多态区别：

1.静态多态的函数地址早绑定 - 编译阶段确定函数地址

2.动态多态的函数地址晚绑定 - 运行阶段确定函数地址

动态多态的满足条件：

1.要有继承关系

2.子类要重写父类的虚函数

动态多态的使用

父类的指针或者引用执行子类对象

示例：

```c++
void Dospeak(Animal& animal)//Animal &animal = cat;
{
	animal.speak();
}
```

总示例：

```c++
//多态
class Animal
{
public:
	//虚函数
	virtual void speak()
	{
		cout << "动物在说话" << endl;
	}
};
//猫类
class cat :public Animal
{
public:
	//重写 函数返回值类型 函数名 参数列表 完全相同
	void speak()
	{
		cout << "小猫在说话" << endl;
	}
};
class dog :public Animal
{
public:
	void speak()
	{
		cout << "小狗在说话" << endl;
	}
};
//地址早绑定，在编译阶段确定函数地址
//如果想执行让猫说话，那么这个函数地址就不能提前绑定，需要在运行阶段进行绑定，地址晚绑定
void Dospeak(Animal& animal)//Animal &animal = cat;
{
	animal.speak();
}
void test01()
{
	cat cat;
	Dospeak(cat);
	dog dog;
	Dospeak(dog);
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

重写：函数返回值类型 函数名 参数列表 完全相同称为重写

虚函数的定义：

![image-20240616132731510](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240616132731510.png)

#### 4.7.2多态案例---计算器类

案例描述：

分别用普通写法和多态技术，设计实现两个操作数进行运算的计算器类

多态的优点：

1.代码组织结构清晰

2.可读性强

3.利于前期和后期的扩展以及维护

在真实开发中，提倡开闭原则

开闭原则：对扩展进行开发，对修改进行关闭

普通写法：

```c++
class Calculator
{
public:
	int getreslt(string oper)
	{
		if (oper == "+")
		{
			return m_num1 + m_num2;
		}
		else if (oper == "-")
		{
			return m_num1 - m_num2;
		}
		else if (oper == "*")
		{
			return m_num1 * m_num2;
		}
		//想要扩展新功能，需要修改源码
		//在真实开发中，提倡开闭原则
		//开闭原则：对扩展进行开发，对修改进行关闭
		else if (oper == "/")
		{
			return m_num1 / m_num2;
		}
	}
	int m_num1;//操作数1
	int m_num2;//操作数2
};
void test01()
{
	//创建计算器对象
	Calculator c;
	c.m_num1 = 10;
	c.m_num2 = 20;
	cout << c.getreslt("+") << endl;
	cout << c.getreslt("-") << endl;
	cout << c.getreslt("*") << endl;
}
```

多态写法：

```c++
//实现一个计算器的抽象类
class AbstractCalculator
{
public:
	virtual int getresult()
	{
		return 0;
	}
	int m_num1;
	int m_num2;
};
//加法计算器类
class AddCalculator :public AbstractCalculator
{
public:
	int getresult()
	{
		return m_num1+m_num2;
	}
};
//减法计算器类
class SubCalculator :public AbstractCalculator
{
public:
	int getresult()
	{
		return m_num1 - m_num2;
	}
};
//乘法计算器类
class MulCalculator :public AbstractCalculator
{
public:
	int getresult()
	{
		return m_num1 * m_num2;
	}
};
void test02()
{
	//多态使用条件
	//父类指针或者引用指向子类对象
	AbstractCalculator* abc = new AddCalculator;
	abc->m_num1 = 10;
	abc->m_num2 = 20;
	cout << abc->getresult() << endl;
	delete abc;
	//减法
	abc = new SubCalculator;
	abc->m_num1 = 10;
	abc->m_num2 = 20;
	cout << abc->getresult() << endl;
	delete abc;
	//乘法
	abc = new MulCalculator;
	abc->m_num1 = 10;
	abc->m_num2 = 20;
	cout << abc->getresult() << endl;
	delete abc;
}
int main()
{
	//test01();
	test02();
	system("pause");
	return 0;
}
```

总结：C++开发提倡利用多态设计程序架构，因为多态优点很多

#### 4.7.3纯虚函数和抽象类

在多态中，通常父类中虚函数的实现时毫无意义的，主要都是调用子类重写的内容

因此可以将虚函数写成纯虚函数

纯虚函数的语法：`virtual 返回值类型 函数名 (参数列表) = 0；`

当类中有了纯虚函数，这个类也称为抽象类

抽象类的特点：

1.无法实例化对象

2.子类必须重写抽象类中的纯虚函数，否则也属于抽象类

```c++
//纯虚函数和抽象类
class Base
{
public:
	virtual void func() = 0; 
};
class Son :public Base
{
public:
	virtual void func()
	{
		cout << "func函数调用" << endl;
	}
};
void test01()
{
	//Base b;//抽象类是无法实例化对象
	//new Base;//抽象类是无法实例化对象
	//Son s;//子类必须重写父类中的纯虚函数，否则无法实例化对象
	Base* base = new Son;
	base->func();

}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 4.7.4多态案例二-制作饮品

案例描述：

制作饮品的大致流程为：煮水 - 冲泡 - 倒入杯中 - 加入辅料

利用多态技术实现本案例，提供抽象制作饮品基类，提供子类制作咖啡和茶叶

```c++
//案例二
class AbstractDrinking
{
public:
	//煮水
	virtual void Boil() = 0;
	//冲泡
	virtual void Brew() = 0;
	//倒入杯中
	virtual void PourIncup() = 0;
	//加入辅料
	virtual void PutSomething() = 0;
	//制作饮品
	void makeDrink()
	{
		Boil();
		Brew();
		PourIncup();
		PutSomething();
	}
};
//制作咖啡
class Coffee :public AbstractDrinking
{
public:
	//煮水
	virtual void Boil()
	{
		cout << "煮农夫山泉" << endl;
	}
	//冲泡
	virtual void Brew()
	{
		cout << "冲泡咖啡" << endl;
	}
	//倒入杯中
	virtual void PourIncup()
	{
		cout << "倒入杯中" << endl;
	}
	//加入辅料
	virtual void PutSomething()
	{
		cout << "加入牛奶和糖" << endl;
	}
};
//制作茶叶
class Tea :public AbstractDrinking
{
public:
	//煮水
	virtual void Boil()
	{
		cout << "煮农夫山泉" << endl;
	}
	//冲泡
	virtual void Brew()
	{
		cout << "冲泡茶叶" << endl;
	}
	//倒入杯中
	virtual void PourIncup()
	{
		cout << "倒入杯中" << endl;
	}
	//加入辅料
	virtual void PutSomething()
	{
		cout << "加入枸杞" << endl;
	}
};
void dowork(AbstractDrinking * abs)
{
	abs->makeDrink();
	delete abs;//释放
}
void test01()
{
	//制作咖啡
	dowork(new Coffee);
	cout << "--------------------" << endl;
	//制作茶叶
	dowork(new Tea);
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 4.7.5虚祈构和纯虚祈构

多态使用时，如果子类中有属性开辟到堆区，那么父类指针在释放时无法调用到子类的祈构代码

解决方案：将父类中的祈构函数改为虚构祈或者纯虚构祈

![image-20240617193053701](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240617193053701.png)

虚祈构语法：

`virtual ~类名(){}`

纯虚构祈语法：

`virtual ~类名() = 0;`

`类名::~类名(){}`

示例：

```c++
//虚祈构和纯虚祈构
class Animal
{
public:
	Animal()
	{
		cout << "Animal构造函数调用" << endl;
	}
	//利用虚祈构可以解决父类指针释放子类对象时不干净的问题
	/*virtual ~Animal()
	{
		cout << "Animal祈构函数调用" << endl;
	}*/
	//纯虚祈构 需要声明也需要实现
	virtual ~Animal() = 0;
	//纯虚函数
	virtual void speak() = 0;
};
Animal:: ~Animal()
{
	cout << "Animal纯虚祈构函数调用" << endl;
}
class Cat :public Animal
{
public:
	Cat(string name)
	{
		m_name = new string(name);
	}
	~Cat()
	{
		if (m_name != NULL)
		{
			delete m_name;
			m_name = NULL;
		}
	}
	virtual void speak()
	{
		cout << *m_name << "小猫在说话" << endl;
	}
	string* m_name;
};
void test01()
{
	Animal* animal = new Cat("Tom");
	animal->speak();
	delete animal;
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

总结：

1.虚析构或纯虚祈构就是用来解决通过父类指针释放子类对象

2.如果子类中没有堆区数据，可以不写为虚祈构或纯虚祈构

3.拥有纯虚祈构函数的类也属于抽象类

## 5.文件操作

程序运行时产生的数据都属于临时数据，程序一旦运行结束都会被释放

通过文件可以将数据持久化

C++中对文件操作需要包含头文件`<fstream>`

文件类型分为两种：

1.***文本文件***  -  文件以文本的ASCII码形式存储在计算机中

2.***二进制文件***  -  文件以文本的二进制形式存储在计算机中，用户一般不能直接读懂它们

操作文件的三大类：

1.ofstream:写操作

2.ifstream:读操作

3.fstream:读写操作

**文件操作的步骤**

1. **引入头文件：**
   文件操作需要包含 `<fstream>` 头文件。
2. **打开文件：**
   文件需要被打开才能进行读写操作。可以使用 `.open()` 方法或通过构造函数直接指定文件名。
3. **操作文件：**
   可以使用流插入运算符 (`<<`) 向文件写入数据，或者使用流提取运算符 (`>>`) 从文件读取数据。
4. **关闭文件：**
   完成文件操作后，需要调用 `.close()` 方法来关闭文件。

### 5.1文本文件

#### 5.1.1写文件

写文件步骤如下：

1.包含头文件

`#include <fstream>`

2.创建流对象

`ofstream ofs;`

3.打开文件

`ofs.open("文件路径",打开方式);`

4.写数据

`ofs << "写入的数据";`

5.关闭文件

`ofs.close();`

文件打开方式：

![image-20240618144535917](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240618144535917.png)

注意：文件打开方式可以配合使用，利用|操作符

例如：用二进制方式写文件`ios::binary | ios::out`

```c++
//文件操作
#include <fstream>
void test01()
{
	//1.包含头文件

	//2.创建流对象
	ofstream ofs;
	//3.指定打开方式
	ofs.open("test.txt", ios::out);
	//4.写内容
	ofs << "ababa" << endl;
	//关闭文件
	ofs.close();
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```

总结：

1.文件操作必须包含头文件fstream

2.读文件可以利用ofstream，或者fstream类

3.打开文件时需要指定操作文件的路径，以及打开方式

4.利用<<可以向文件中写数据

5.操作完毕，要关闭文件

#### 5.1.2读文件

读文件与写文件步骤类似，但是读取方式相对于比较多

读文件的步骤如下：

1.包含头文件

`#include <fstream>`

2.创建流对象

`ifstream ifs`

3.打开文件并判断文件是否打开成功

`ifs.open("文件路径",打开方式);`

4.读数据

四种方式读取

5.关闭文件

`ifs.close();`

```c++
//读文件
#include <fstream>
void test01()
{
	//1.包含头文件

	//2.创建流对象
	ifstream ifs;
	//3.打开文件 并且判断是否打开成功
	ifs.open("test.txt", ios::in);
	if (!ifs.is_open())
	{
		cout << "文件打开失败" << endl;
		return;
	}
	//4.读数据
	//第一种
	/*char buf[1024] = { 0 };
	while (ifs >> buf)
	{
		cout << buf << endl;
	}*/
	//第二种
	/*char bf[1024] = { 0 };
	while (ifs.getline(buf,sizeof(buf)))
	{
		cout << buf << endl;
	}*/
	//第三种
	string buf;
	while (getline(ifs, buf))
	{
		cout << buf << endl;
	}
	//第四种
	char c;
	while ((c = ifs.get()) != EOF)//EOF end of file
	{
		cout << c;
	}
	//5.关闭文件
	ifs.close();
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

总结：

1.读文件可以利用ifstream，或者fstream类

2.利用is_open()函数可以判断文件是否打开成功

3.close关闭文件

### 5.2二进制文件

以二进制的方式对文件进行读写操作

打开方式要指定为ios::binary

#### 5.2.1写文件

二进制方式写文件主要利用流对象调用成员函数write

函数原型：`ostream& write(const char * buffer,int len);`

参数解释：字符指针buffer指向内存中一段存储空间，len是读写的字节数

示例：

```c++
//二进制文件 写文件
#include <fstream>
class Person
{
public:
	char m_name[64];//姓名
	int m_age;//年龄
};
void test01()
{
	//包含头文件
	//创建流对象
	ofstream ofs;
	//打开文件
	ofs.open("person.txt", ios::out|ios::binary);
	//写文件
	Person p = { "张三",18 };
	ofs.write((const char*)&p, sizeof(Person));
	//关闭文件
	ofs.close();
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

总结：

文件输出流对象，可以通过write函数，以二进制方式写数据

#### 5.2.2读文件

二进制方式读文件主要利用流对象调用成员函数read

函数原型：`istream& read(char *buffer,int len);`

参数解释：字符指针buffer指向内存中一段存储空间。len是读写的字节数

示例：

```c++
//二进制文件 读文件
#include <fstream>
class Person
{
public:
	char m_name[64];
	int m_age;
};
void test01()
{
	//1.包含头文件

	//2.创建流对象
	ifstream ifs;
	//3.打开文件 判断文件是否打开成功
	ifs.open("Person.txt", ios::in| ios::binary);
	if (!ifs.is_open())
	{
		cout << "文件打开失败" << endl;
	}
	//4.读文件
	Person p;
	ifs.read((char*)&p, sizeof(Person));
	cout << p.m_name << p.m_age << endl;
	//5，关闭文件
	ifs.close();
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

文件输入流对象，可以通过read函数，以二进制方式读数据

# 3.C++提高编程

## 1.模板

### 1.1模板的概念

模板就是建立通用的模具，大大提高复用性

例如：生活中的模板

像照片的背景，PPT模板

总结：

1.模板不可以直接使用，他只是一个框架

2.模板的通用并不是万能的

### 1.2函数模板

1.C++另一种编程思想称为泛型编程，主要利用的技术就是模板

2.C++提供两种模板机制：函数模板和类模板

#### 1.2.1函数模板语法

函数模板作用：

建立一个通用函数，其函数返回值类型和形参类型可以不具体制定，用一个虚拟的类型来代表

语法：

```c++
template<typename T>
函数声明或定义
```

解释：

template --- 声明创建模板

typename --- 表面其后面的符号是一种数据类型，可以用class代替

T --- 通用的数据类型，名称可以替代，通常为大写字母

```c++
//函数模板

//实现两个整形交换的函数
void swapint(int& a, int& b)
{
	int temp = a;
	a = b;
	b = temp;
}
//交换两个浮点型的函数
void swapdouble(double& a, double& b)
{
	double temp = a;
	a = b;
	b = temp;
}
//函数模板
template<typename T>//声明一个模板，告诉编译器后面的代码中紧跟着的T不要报错，T是一个通用数据类型
void myswap(T& a, T& b)
{
	T temp = a;
	a = b;
	b = temp;
}

void test01()
{
	int a = 10;
	int b = 20;
	//swapint(a, b);
    //利用函数模板交换
	//两种方式使用函数
    //1.自动类型推导
	//2.显示指定类型
	myswap(a, b);
    myswap<int>(a, b);
	cout << a << b << endl;
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

总结：

1.函数模板利用关键字template

2.使用函数模板有两种方式：

​	1.自动类型推导
​	2.显示指定类型

3.模板的目的是为了提高复用性，将类型参数化

#### 1.2.2函数模板注意事项

注意事项：

1.自动类型推导：必须推导出一致的数据类型T，才可以使用

2.模板必须要确定出T的数据类型，才可以使用

示例：

```c++
//函数模板注意事项
template<typename T>
void myswwap(T& a, T& b)
{
	T temp = a;
	a = b;
	b = temp;
}
//1.自动类型推导，必须推导出一致的数据类型T，才可以使用
void test01()
{
	int a = 10;
	int b = 20;
	char c = 'c';
	myswwap(a, b); //正确
	//myswwap(a, c);//错误推导不出一致符号
	cout << a << endl;
	cout << b << endl;
}
//2.模板必须要确定出T的数据类型，才可以使用
template<class T>
void func()
{
	cout << "func 调用" << endl;
}
void test02()
{
	func<int>();
}

int main()
{
	//test01();
	test02();
	system("pause");
	return 0;
}
```

#### 1.2.3函数模板案例

```c++
//实现一个通用的 对数组进行快速排序的函数
// 交换函数模板
template<typename T>
void myswap(T& a, T& b)
{
	T temp = a;
	a = b;
	b = temp;
}
//排序算法
template<typename T>
void mysort(T arr[],int len)
{
	for (int i = 0; i < len; i++)
	{
		int max = i;
		for (int j = i + 1; j < len; j++)
		{
			if (arr[max] < arr[j])
			{
				max = j;
			}
		}
		if (max != i)
		{
			myswap(arr[max], arr[i]);
		}
	}
}
//打印数组模板
template<class T>
void printarr(T arr[],int len)
{
	for (int i = 0; i < len; i++)
	{
		cout << arr[i] << " ";
	}
	cout << endl;
}
void test01()
{
	char arr[] = "badcfs";
	int num = sizeof(arr);
	mysort(arr, num);
	printarr(arr, num);
}
void test02()
{
	int arr[] = { 1,3,2,4,7,6,5 };
	int num = sizeof(arr)/sizeof(int);
	mysort(arr, num);
	printarr(arr, num);
}
int main()
{
	//test01();
	test02();
	system("pause");
	return 0;
}
```

#### 1.2.4普通函数与函数模板的区别

普通函数与函数模板区别

1.普通函数调用时可以发生自动类型转换(隐式类型转换)

2.函数模板调用时，如果利用自动类型推导，不会发生隐式类型转换

3.如果利用显示指定类型的方式，可以发生隐式类型转换

示例：

```c++
//普通函数
int myadd01(int a,int b)
{
	return a + b;
}
//函数模板
template<typename T>
T myadd02(T a, T b)
{
	return a + b;
}

void test01()
{
	int a = 10;
	int b = 20;
	char c = 'c';
	cout << myadd01(a, c) << endl;

	//cout << myadd02(a, c) << endl;//错误
	cout << myadd02<int>(a, c) << endl;//正确
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```

总结：建议使用显示指定类型的方法，调用函数模板，因为可以自己确定通用类型T

#### 1.2.5普通函数与函数模板的调用规则

调用规则如下：

1.如果函数模板和普通函数都可以实现，优先调用普通函数

2.可以通过空模板参数列表来强制调用函数模板

3.函数模板也可以发生重载

4.如果函数模板可以发生更好的匹配，优先调用函数模板

示例：

```c++
//1.如果函数模板和普通函数都可以实现，优先调用普通函数
//2.可以通过空模板参数列表来强制调用函数模板
//3.函数模板也可以发生重载
//4.如果函数模板可以发生更好的匹配，优先调用函数模板
void myprint(int a, int b)
{
	cout << "调用的普通函数" << endl;
}
template<class T>
void myprint(T a, T b)
{
	cout << "调用的函数模板" << endl;
}
template<class T>
void myprint(T a, T b,T c)
{
	cout << "调用函数的重载模板" << endl;
}
void test01()
{
	int a = 10;
	int b = 20;
	//myprint(a, b);
	//通过空模板参数列表来强制调用函数模板
	//myprint<>(a,b);
	myprint(a, b, 100);
	//4.如果函数模板可以发生更好的匹配，优先调用函数模板
	char c1 = 'a';
	char c2 = 'b';
	myprint(c1, c2);
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

总结：既然提供了函数模板，最好就不要提供普通函数，否则容易出现二义性

#### 1.2.6模板的局限性

局限性：

模板的通用性并不是万能的

例如：

```c++
template<class T>
void f(T a,T b)
{
    a = b;
}
```

在上述代码中提供的赋值操作，如果传入的a和b是一个数组，就无法实现了

再例如：

```c++
template<class T>
void f(T a,T b)
{
    if(a > b){...}
}
```

在上述代码中，如果T的数据类型传入的是像Person这样的自定义数据类型，也无法正常运行

因此C++为了解决这种问题，提供模板的重载，可以为这些特点的类型提供具体化的模板

`template<>` 表示这是一个模板的具体化版本，`bool mycompare(Person& a, Person& b)` 指定了具体的类型为 `Person`。

示例:

```c++
//模板局限性
//模板并不是万能的，有些特定数据类型，需要用具体化
//对比两个数据是否相等函数
class Person
{
public:
	Person(string name, int age)
	{
		this->name = name;
		this->age = age;
	}
	string name;
	int age;
};
template<class T>
bool mycompare(T& a, T& b)
{
	if (a == b)
	{
		return true;
	}
	else
	{
		return false;
	}
}

//利用具体化Person版本实现代码，具体1优化调用
template<> bool mycompare(Person& a, Person& b)
{
	if (a.name == b.name && a.age == b.age)
	{
		return true;
	}
	else
	{
		return false;
	}
}
void test01()
{
	int a = 10;
	int b = 20;
	bool ret = mycompare(a, b);
	if (ret)
	{
		cout << "a == b" << endl;
	}
	else
	{
		cout << "a != b" << endl;
	}
}
void test02()
{
	Person p1("Tom", 10);
	Person p2("Tom", 10);
	bool ret = mycompare(p1, p2);
	if (ret)
	{
		cout << "p1 == p2" << endl;
	}
	else
	{
		cout << "p1 != p2" << endl;
	}
}
int main()
{
	//test01();
	test02();
	system("pause");
	return 0;
}
```

总结：

1.利用具体化的模板，可以解决自定义类型的通用化

2.学习模板并不是为了写模板，而是在STL能够运营系统提供的模板

### 1.3类模板

#### 1.3.1类模板语法

类模板作用：

建立一个通用类，类中的成员 数据类型可以不具体制定，用一个虚拟的类型来代表

语法：

```c++
template<typename T>
类
```

解释：

template --- 声明创建模板

typename --- 表明其后面的符号是一种数据类型，可以用class代替

T --- 通用的数据类型，名称可以替换，通常为大写字母

```c++
//类模板
template<class nameType,class ageType>
class Person
{
public:
	Person(nameType name, ageType age)
	{
		this->m_name = name;
		this->m_age = age;
	}
	void showPerson()
	{
		cout << this->m_name << endl;
		cout << this->m_age << endl;
	}
	nameType m_name;
	ageType m_age;
};
void test01()
{
	Person<string, int>p1("嘻嘻", 99);
	p1.showPerson();
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

总结：类模板和函数模板语法相似，在声明模板template后面加类，此类称为类模板

#### 1.3.2类模板与函数模板区别

类模板与函数模板区别主要有两点：

1.类模板没有自动类型推导的使用方式

2.类模板在模板参数列表中可以有默认参数

```c++
//类模板与函数模板区别
template<class nametype,class agetype = int>
class Person
{
public:
	Person(nametype name, agetype age)
	{
		this->m_name = name;
		this->m_age = age;
	}
	void showPerson()
	{
		cout << this->m_name << endl;
		cout << this->m_age << endl;
	}
	nametype m_name;
	agetype m_age;
};
//1.类模板没有自动类型推导的使用方式
void test01()
{
	//Person p("孙悟空", 1000); 错误
	Person<string, int>p("孙悟空", 1000);
	p.showPerson();
}
//2.类模板在模板参数列表中可以有默认参数
void test02()
{
	Person<string>p("123", 123);
	p.showPerson();
}
int main()
{
	//test01();
	test02();
	system("pause");
	return 0;
}
```

总结：

1.类模板使用只能用显示指定类型方式

2.类模板中的模板参数列表可以有默认参数

#### 1.3.3类模板中成员函数创建时机

类模板中成员函数和普通类中成员函数创建时机是有区别的：

1.普通类中的成员函数一开始就开始创建

2.类模板中的成员函数在调用时才创建

示例：

```c++
//类模板中成员函数的创建时机
class Person1
{
public:
	void showPerson1()
	{
		cout << "Person1 show" << endl;
	}
	void showPerson2()
	{
		cout << "Person2 show" << endl;
	}
};


template<class T>
class myclass
{
public:
	T obj;
	//类模板的成员函数
	void func1()
	{
		obj.showPerson1();
	}
	void func2()
	{
		obj.showPerson2();
	}
};
void test01()
{
	myclass<Person1>m;
	m.func1();
	//m.func2();
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

总结：类模板中的成员函数并不是一开始就创建的，在调用时才去创建的

#### 1.3.4类模板对象做函数参数

一共

有三种传入方式：

1.指定传入的类型 --- 直接显示对象的数据类型

2.参数模板化 --- 将对象中的参数变为模板进行传递

3.整个模板化 --- 将这个对象类型 模板化进行传递

示例：

```c++
//类模板对象做函数参数
template<class T1,class T2>
class Person
{
public:
	Person(T1 name, T2 age)
	{
		this->m_name = name;
		this->m_age = age;
	}
	void showPerson()
	{
		cout << this->m_name << endl;
		cout << this->m_age << endl;
	}
	T1 m_name;
	T2 m_age;
};
//1.指定传入类型
void printPerson(Person<string, int>&p)
{
	p.showPerson();
}
void test01()
{
	Person<string, int>p("孙悟空", 100);
	printPerson(p);
}
//2.模板参数化
template<class T1,class T2>
void printPerson2(Person<T1, T2>&p)
{
	p.showPerson();
	cout << typeid(T1).name() << endl;
	cout << typeid(T2).name() << endl;
}
void test02()
{
	Person<string, int>p("猪八戒", 90);
	printPerson2(p);
}
//3.整个类模板化
template<class T>
void printPerson3(T &p)
{
	p.showPerson();
	cout << typeid(T).name() << endl;
}
void test03()
{
	Person<string, int>p("唐僧", 30);
	printPerson3(p);
}
int main()
{
	//test01();
	//test02();
	test03();
	system("pause");
	return 0;
}
```

总结：

1.通过类模板创建的对象，可以有三种方式向函数中进行传参

2.使用比较广泛是第一种：指定传入的类型

#### 1.3.5类模板与继承

当模板遇到继承时，需要注意一下几点：

1.当子类继承的父类是一个类模板时，子类在声明的时候，要指定出父类中T的类型

2.如果不指定，编译器无法给子类分配内存

3.如果想灵活指定出父类中T的类型，子类也需要变为类模板

示例：

```c++
//类模板与继承
template<class T>
class Base
{

	T m;
};
//class Son :public Base//错误，必须要指定父类的T类型，才能继承子类
class Son:public Base<int>
{

};
void test01()
{
	Son s1;
}
//如果想灵活指定父类中T类型，子类也需要变类模板
template<class T1,class T2>
class Son2 :public Base<T2>
{
public:
	Son2()
	{
		cout << typeid(T1).name << endl;
		cout << typeid(T2).name << endl;
	}
	T1 obj;

};
void test02()
{
	Son2<int, char>s2;
}
int main()
{
	test01();
	test02();
	system("pause");
	return 0;
}
```

总结：如果父类是类模板，子类需要指定父类中T的数据类型

#### 1.3.6类模板成员函数类外实现

```c++
//类模板成员函数类外实现
template<class T1,class T2>
class Person
{
public:
	Person(T1 name, T2 age);
	void showPerson();
	T1 m_name;
	T2 m_age;
};
//构造函数类外实现
template<class T1, class T2>
Person<T1,T2>::Person(T1 name, T2 age)
{
	this->m_name = name;
	this->m_age = age;
}
//成员函数类外实现
template<class T1, class T2>
void Person<T1,T2>::showPerson()
{
	cout << this->m_name << endl;
	cout << this->m_age << endl;
}
void test01()
{
	Person<string, int>p("Tom", 20);
	p.showPerson();
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

总结：类模板中的成员函数类外实现时，需要加上模板参数列表

#### 1.3.7类模板分文件编写

学习目标：

掌握类模板成员函数分文件编写产生的问题以及解决方式

问题:

类模板中成员函数创建时机是在调用阶段，导致文件编写时链接不到

解决：

1.解决方式1：直接包含.cpp源文件

2.解决方式2：将声明和实现写到同一个文件中，并更改后缀名为.hpp，hpp是约定的名称，并不是强制

示例：

1.Person.h文件

```c++
#pragma once
#include <iostream>
using namespace std;
template<class T1, class T2>
class Person
{
public:
	Person(T1 name, T2 age);
	void showPerson();
	T1 m_name;
	T2 m_age;
};
```

2.Person.cpp文件

```c++
#include "Person.h"
template<class T1, class T2>
Person<T1, T2>::Person(T1 name, T2 age)
{
	this->m_name = name;
	this->m_age = age;
}
template<class T1, class T2>
void Person<T1, T2>::showPerson()
{
	cout << this->m_name << endl;
	cout << this->m_age << endl;
}
```

3.Person.hpp文件

```c++
#pragma once
#include <iostream>
using namespace std;
template<class T1, class T2>
class Person
{
public:
	Person(T1 name, T2 age);
	void showPerson();
	T1 m_name;
	T2 m_age;
};
template<class T1, class T2>
Person<T1, T2>::Person(T1 name, T2 age)
{
	this->m_name = name;
	this->m_age = age;
}
template<class T1, class T2>
void Person<T1, T2>::showPerson()
{
	cout << this->m_name << endl;
	cout << this->m_age << endl;
}
```

4.主元素

```c++
//第一种解决方式，直接包含源文件
//#include "Person.cpp"
//第二中解决方式，将.h和.cpp中的内容写到一起，将后缀名改为.hpp
#include "Person.hpp"
void test01()
{
	Person<string, int>p("jerry", 10);
	p.showPerson();
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

总结：主流的解决方法是第二种，将类模板成员函数写到一起，并将后缀名改为.hpp

#### 1.3.8类模板与友元

学习目标：

掌握类模板配合友元函数的类内和类外实现

全局函数类内实现 - 直接在类内声明友元即可

全局函数类外实现 - 需要提前让编译器知道全局函数的存在

示例：

```c++
//类模板与友元
//通过全局函数打印Person信息
//提前让编译器知道Person类存在
template<class T1, class T2>
class Person;
//类外实现
template<class T1, class T2>
void printPerson2(Person<T1, T2> p)
{
	cout << p.m_name << endl;
	cout << p.m_age << endl;
}
template<class T1,class T2>
class Person
{
	//全局函数类内实现
	friend void printPerson(Person<T1,T2> p)
	{
		cout << p.m_name << p.m_age << endl;
	}
	//全局函数类外实现
	//加一个空模板的参数列表
	//如果全局函数是类外实现，需要让编译器提前知道这个函数的存在
	friend void printPerson2<>(Person<T1, T2> p);
public:
	Person(T1 name, T2 age)
	{
		this->m_name = name;
		this->m_age = age;
	}
private:
	T1 m_name;
	T2 m_age;
};
//1.全局函数在类内实现
void test01()
{
	Person<string, int>p("Tom", 20);
	printPerson(p);
}
void test02()
{
	Person<string, int>p("jerry", 10);
	printPerson2(p);
}
int main()
{
	//test01();
	test02();
	system("pause");
	return 0;
}
```

总结：建议全局函数做类内实现，用法简单，而且编译器可以直接识别

## 2.STL初识

### 2.1STL的诞生

![image-20240624170846651](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240624170846651.png)

### 2.2STL基本概念

![image-20240624171110243](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240624171110243.png)

### 2.3STL六大组件

STL大体分为六大组件，分别是：容器，算法，迭代器，仿函数，适配器(配接器)，空间配置器

![image-20240624171850891](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240624171850891.png)

### 2.4STL中容器，算法，迭代器

![image-20240624172106814](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240624172106814.png)

![image-20240624172235796](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240624172235796.png)

![image-20240624172306930](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240624172306930.png)

### 2.5容器算法迭代器初识

#### 2.5.1STLvector存放内置数据类型

容器：`vector`

算法：`for_each`

迭代器：`vector<int>::iterator`

示例：

```c++
//vector容器存放内置数据类型
#include <vector>
#include <algorithm> //算法的头文件

//vector容器存放内置数据类型
void myprint(int val)
{
	cout << val << endl;
}
void test01()
{
	//创建了一个vector容器，数组
	vector<int>v;
	//向容器中插入数据
	v.push_back(10);
	v.push_back(20);
	v.push_back(30);
	v.push_back(40);
	//通过迭代器访问容器中的数据
	vector<int>::iterator itBegin = v.begin();//起始迭代器 指向容器中的第一个元素
	vector<int>::iterator itEnd = v.end();//结束迭代器 指向容器中最后一个元素的下一个位置
	//第一种遍历方式
	/*while (itBegin != itEnd)
	{
		cout << *itBegin << endl;
		itBegin++;
	}*/
	//第二种遍历方式
	/*for (vector<int>::iterator it = v.begin(); it != v.end(); it++)
	{
		cout << *it << endl;
	}*/
	//第三种遍历方式
	for_each(v.begin(), v.end(), myprint);
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 2.5.2vector存放自定义数据类型

```c++
//vector容器中存放自定义数据类型
#include <vector>
class Person
{
public:
	Person(string name, int age)
	{
		this->m_name = name;
		this->age = age;
	}
	string m_name;
	int age;
};
void test01()
{
	vector<Person>v;
	Person p1("aaa",10);
	Person p2("bbb", 20);
	Person p3("ccc", 30);
	Person p4("ddd", 40);
	Person p5("eee", 50);
	//向容器中添加数据
	v.push_back(p1);
	v.push_back(p2);
	v.push_back(p3);
	v.push_back(p4);
	v.push_back(p5);
	//遍历容器中的数据
	for (vector<Person>::iterator it = v.begin(); it != v.end(); it++)
	{
		//cout << (*it).m_name << endl;
		//cout << (*it).age << endl;
		cout << it->m_name << endl;
		cout << it->age << endl;
	}
}
//存放自定义数据类型 指针
void test02()
{
	vector<Person*>v;
	Person p1("aaa", 10);
	Person p2("bbb", 20);
	Person p3("ccc", 30);
	Person p4("ddd", 40);
	Person p5("eee", 50);
	//向容器中添加数据
	v.push_back(&p1);
	v.push_back(&p2);
	v.push_back(&p3);
	v.push_back(&p4);
	v.push_back(&p5);
	//遍历容器
	for (vector<Person*>::iterator it = v.begin(); it != v.end(); it++)
	{
		cout << (*it)->m_name << endl;
		cout << (*it)->age << endl;
	}
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 2.5.3vector容器嵌套容器

```c++
//vector容器嵌套容器
#include <vector>
void test01()
{
	vector<vector <int>>v;
	//创建小容器
	vector<int>v1;
	vector<int>v2;
	vector<int>v3;
	vector<int>v4;
	//向小容器添加数据
	for (int i = 0; i < 4; i++)
	{
		v1.push_back(i + 1);
		v2.push_back(i + 2);
		v3.push_back(i + 3);
		v4.push_back(i + 4);
	}
	//将小容器插入到大容器中
	v.push_back(v1);
	v.push_back(v2);
	v.push_back(v3);
	v.push_back(v4);
	//通过大容器，把所有数据遍历一遍
	for (vector<vector<int>>::iterator it = v.begin(); it != v.end();it++)
	{
		//(*it) --- vector<int>
		for (vector<int>::iterator vit = (*it).begin(); vit != (*it).end(); vit++)
		{
			cout << *vit << " ";
		}
		cout << endl;
	}
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```

## 3.STL常用容器

### 3.1string容器

#### 3.1.1string基本概念

本质：

string是C++风格的字符串，而string本质上是一个类

string和char*区别：

char*是一个指针

string是一个类，类内封装了`char*`，管理这个字符串，是一个`char*`型的容器

特点：

string类内封装了很多成员方法

例如：查找find，拷贝copy，删除delete，替换replace，插入insert

string管理char*所分配的内存，不用担心赋值越界和取值越界等，由类内部进行负责

#### 3.1.2string构造函数

构造函数原型：

1.string();     //创建一个空的字符串，例如string str;

2.string(const char* s);   //使用字符串s初始化

3.string(const string& str);   //使用一个string对象初始化另一个string对象

4.string(int n,char c);   //使用n个字符c初始化

示例：

```c++
//string的构造函数
void test01()
{
	string s1;//默认构造
	const char* str = "hello world";
	string s2(str);
	cout << s2 << endl;
	string s3(s2);
	cout << s3 << endl;
	string s4(10, 'a');
	cout << s4 << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```

总结：string的多种构造方式没有可比性，灵活使用即可

#### 3.1.3string赋值操作

功能描述：

给string字符串进行赋值

赋值的函数原型：

1.`string& operator=(const char* s);`  //char*类型字符串 赋值给当前的字符串

2.`string& operator=(const string &s);`  //把字符串s赋给当前的字符串

3.`string& operator=(char c);`  //字符赋值给当前的字符串

4.`string& assign(const char*s);`  //把字符串s赋给当前字符串

5.`string& assign(const char*s,int n);`  //把字符串s的前几个字符赋给当前的字符串

6.`string& assign(const string &s);`  //把字符串s赋给当前字符串

7.`string& assign(int n,char c);`  //用n个字符c赋给当前字符串

示例：

```c++
//string赋值操作
void test01()
{
	string str1;
	str1 = "hello world";
	cout << str1 << endl;
	string str2;
	str2 = str1;
	cout << str2 << endl;
	string str3;
	str3 = 'a';
	cout << str3 << endl;
	string str4;
	str4.assign("hello C++");
	cout << str4 << endl;
	string str5;
	str5.assign("hello C++",5);
	cout << str5 << endl;
	string str6;
	str6.assign(str5);
	cout << str6 << endl;
	string str7;
	str7.assign(10,'w');
	cout << str7 << endl;
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 3.1.4string字符串拼接

功能描述：

实现在字符串末尾拼接字符串

函数原型：

1.string& operator+=(const char* str);  //重载+=操作符

2.string& operator+=(const char c);  //重载+=操作符

3.string& operator+=(const string& str);  //重载+=操作符

4.string& append(const char* s);  //把字符串s连接到当前字符串结尾

5.string& append(const char* s,int n);  //把字符串s的前n个字符连接到当前字符串结尾

6.string& append(const string &s);  //同operator+=(const string& str)

7.string& append(const string &s,int pos,int n);  //字符串s中从pos开始的n个字符连接到字符串结尾

示例：

```c++
//string字符串拼接
void test01()
{
	string str1 = "我";
	str1 += "爱玩游戏";
	str1 += ".";
	cout << str1 << endl;
	string str2 = "LOL DNF";
	str1 += str2;
	cout << str1 << endl;
	string str3 = "I";
	str3.append("love ");
	cout << str3 << endl;
	str3.append("game abcde", 4);
	cout << str3 << endl;
	str3.append(str2);
	cout << str3 << endl;
	str3.append(str2, 0, 3);
	cout << str3 << endl;
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 3.1.5string查找和替换

功能描述：

查找：查找指定字符串是否存在

替换：在指定的位置替换字符串

函数原型：

![image-20240626154347225](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240626154347225.png)

```c++
//字符串查找和替换
//1.查找
void test01()
{
	string str1 = "abcdefgde";
	//find
	int pos = str1.find("de");
	if (pos == -1)
	{
		cout << "未找到字符串" << endl;
	}
	else
	{
		cout << pos << endl;
	}
	//rfind 和 find区别
	//rfind从右往左查找 find从左往右查找
	pos = str1.rfind("de");
	cout << pos << endl;
}
//2.替换
void test02()
{
	string str1 = "abcdefg";
	//从一号位置起 三个字符 替换为"1111"
	str1.replace(1, 3, "1111");
	cout << str1 << endl;
}
int main()
{
	//test01();
	test02();
	system("pause");
	return 0;
}
```

总结：
1.find查找是从左往右，rfind从右往左

2.find找到字符串后返回查找的第一个字符位置，找不到返回-1

3.replace在替换时，要指定从哪个位置起，多少个字符，替换成什么样的字符串

#### 3.1.6string字符串比较

功能描述：

字符串之间的比较

比较方式：

字符串比较是按字符的ASCII码进行对比

`=` 返回 0

`> ` 返回 1

`<` 返回 -1

函数原型：

1.int compare(const string &s)const;  //与字符串s比较

2.int compare(const char* s)const; //与字符串s比较

示例：

```c++
//字符串比较
void test01()
{
	string str1 = "hello";
	string str2 = "xello";
	if (str1.compare(str2) == 0)
	{
		cout << "str1 == str2" << endl;
	}
	else if (str1.compare(str2) > 0)
	{
		cout << "str1 > str2" << endl;
	}
	else
	{
		cout << "str1 < str2" << endl;
	}
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

总结：字符串对比主要是用于比较两个字符串是否相等，判断谁大谁小的意义并不是很大

#### 3.1.7string字符存取

string中单个字符存取方式有两种

1.`char& operator[](int n);`  //通过[]方式取字符

2.`char& at(int n)`  //通过at方式获取字符

示例:

```c++
//string 字符存取
void test01()
{
	string str = "hello";
	cout << str << endl;
	//1.通过[]访问单个字符
	for (int i = 0; i < str.size(); i++)
	{
		cout << str[i] << endl;
	}
	cout << endl;
	//2.通过at方式访问单个字符
	for (int i = 0; i < str.size(); i++)
	{
		cout << str.at(i) << endl;
	}
	//修改单个字符
	str[0] = 'x';
	cout << str << endl;
	str.at(1) = 'x';
	cout << str << endl;
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

总结：string字符串中单个字符存取有两种方式，利用[]或at

#### 3.1.8string插入和删除

功能描述：

对string字符串进行插入和删除字符操作

函数原型：

1.string& insert(int pos,const char* s);  //插入字符串

2.string& insert(int pos,const string& str);  //插入字符串

3.string& insert(int pos,int n,char c);  //在指定位置插入n个字符c

4.string& erase(int pos,int n = npos);  //删除从pos开始的n个字符

示例：

```c++
//字符串 插入和删除
void test01()
{
	string str = "hello";
	//插入
	str.insert(1, "111");
	cout << str << endl;
	//删除
	str.erase(1, 3);
	cout << str << endl;
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

总结：插入和删除的起始下标都是从0开始

#### 3.1.9string子串

功能描述：

从字符串中获取想要的子串

函数原型：

string substr(int pos = 0,int n = npos)const;  //返回由pos开始的n个字符组成的字符串

示例：

```c++
//string求子串
void test01()
{
	string str = "abcdef";
	string substr = str.substr(1, 3);
	cout << substr << endl;
}
//实用操作
void test02()
{
	string email = "hello@sina.com";
	//从邮件地址中获取用户名信息
	int pos = email.find("@");
	string username = email.substr(0, pos);
	cout << username << endl;
}
int main()
{
	//test01();
	test02();
	system("pause");
	return 0;
}
```

总结：灵活的运用求子串的功能，可以在实际开发中获取有效信息

### 3.2vector容器

#### 3.2.1vector基本概念

功能：vector数据结构和数组非常相似，也被称为单端数组

***vector与普通数组的区别：***

不同在于数组是静态空间，而vector可以动态扩展

***动态扩展：***

并不是在原有的空间之后续接新空间，而是找更大的内存空间，然后将原有数据拷贝到新空间，释放原空间

![image-20240706221854117](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240706221854117.png)

1.vector容器的迭代器是支持随机访问的迭代器

#### 3.2.2vector构造函数

功能描述：

创建vector容器

函数原型：

1.`vector<T> v;`    //采用模板实现类实现，默认构造函数

2.`vector(v.begin(),v.end());`    //将v.begin(),end()区间中的元素拷贝给本身

3.`vector(n,elem);`    //构造函数将n个elem拷贝给本身

4.`vector(const vector &vec);`    //拷贝构造函数

示例：

```c++
//vector容器构造
#include <vector>
void printvector(vector<int>&v)
{
	for (vector<int>::iterator it = v.begin(); it != v.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}
void test01()
{
	vector<int>v1;
	for (int i = 0; i < 10; i++)
	{
		v1.push_back(i);
	}
	printvector(v1);
	//
	vector<int>v2(v1.begin(), v1.end());
	printvector(v2);
	//
	vector<int>v3(10, 100);
	printvector(v3);
	//
	vector<int>v4(v3);
	printvector(v4);
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 3.2.3vector赋值操作

功能描述：

给vector容器进行赋值

函数原型：

1.`vector& operator=(const vector &vec);`   //重载等号操作符

2.`assign(begin,end);`   //将(begin,end)区间中的数据拷贝赋值给本身

3.`assign(n,elem);`   //将n个elem拷贝赋值给本身

示例：

```c++
//vector的赋值
#include <vector>
void printVector(vector<int>&v)
{
	for (vector<int>::iterator it = v.begin(); it != v.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}
//vector赋值
void test01()
{
	vector<int>v1;
	for (int i = 0; i < 10; i++)
	{
		v1.push_back(i);
	}
	printVector(v1);
	//赋值 operator=
	vector<int>v2;
	v2 = v1;
	printVector(v2);
	//assgin
	vector<int>v3;
	v3.assign(v1.begin(), v1.end());
	printVector(v3);
	//n个elem方式赋值
	vector<int>v4;
	v4.assign(10, 100);
	printVector(v4);
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 3.2.4vector容量和大小

功能描述：

对vector容器的容量和大小操作

函数原型：

1.`empty();`   //判断容器是否为空

2.`capacity()；`    //容器的容量

3.`size();`    //返回容器中元素的个数

4.`resize(int num);`   //重新指定容器的长度为num，若容器变长，则以默认值填充新位置

//如果容器变短，则末尾超出容器长度的元素被删除

5.`resize(int num,elem);`   //重新指定容器的长度为num，若容器变长，则以elem填充新位置

//如果容器变短，则末尾超出容器长度的元素被删除

示例：

```c++
//vector容器的容量和大小操作
#include <vector>
void printVector(vector<int>& v)
{
	for (vector<int>::iterator it = v.begin(); it != v.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}
void test01()
{
	vector<int>v1;
	for (int i = 0; i < 10; i++)
	{
			v1.push_back(i);
	}
	printVector(v1);
	if (v1.empty())//为真 代表容器为空
	{
		cout << "v1为空" << endl;
	}
	else
	{
		cout << "v1的容量为：" << v1.capacity() << endl;
		cout << "v1的大小为：" << v1.size() << endl;
	}
	//重新定义指定大小
	v1.resize(15,100);//利用重载版本，可以指定默认填充值
	printVector(v1);//如果重新指定的比原来长了，默认用0填充
	v1.resize(5);
	printVector(v1);
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 3.2.5vector插入和删除

功能描述：

对vector容器进行插入，删除操作

函数原型：

1.`push_back(ele);`   //尾部插入元素

2.`pop_back();`   //删除最后一个元素

3.`insert(const_iterator pos,ele);`   //迭代器指向位置pos插入元素ele

4.`insert(const_iterator pos,int count,ele);`   //迭代器指向位置pos插入count个元素ele

5.`erase(const_iterator pos);`   //删除迭代器指向的元素

6.`erase(const_iterator start,const_iterator end);`     //删除迭代器从start到end之间的元素

7.`clear();`   //删除容器中所有元素

示例：

```c++
//插入和删除
#include <vector>
void printVector(vector<int>& v)
{
	for (vector<int>::iterator it = v.begin(); it != v.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}
void test01()
{
	vector<int>v1;
	//尾插
	v1.push_back(10);
	v1.push_back(20);
	v1.push_back(30);
	v1.push_back(40);
	v1.push_back(50);
	printVector(v1);
	//尾删
	v1.pop_back();
	printVector(v1);
	//插入
	v1.insert(v1.begin(), 100);
	printVector(v1);
	v1.insert(v1.begin(), 2, 1000);
	printVector(v1);
	//删除
	v1.erase(v1.begin());
	printVector(v1);
	v1.erase(v1.begin(), v1.end());
	printVector(v1);
	//清空
	v1.clear();
	printVector(v1);
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 3.2.6vector数据存取

功能描述：

对vector中的数据的存取操作

函数原型：

1.`at(int idx);`    //返回索引idx所指的数据

2.`operator[];`    //返回索引idx所指的数据

3.`front();`   //返回容器中第一个数据元素

4.`back();`    //返回容器中最后一个数据元素

示例：

```c++
//vector的数据存储
#include <vector>
void printVector(vector<int>& v)
{
	for (vector<int>::iterator it = v.begin(); it != v.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}
void test01()
{
	vector<int>v1;
	for (int i = 0; i < 10; i++)
	{
		v1.push_back(i);
	}
	//利用[]访问数组中的元素
	for (int i = 0; i < v1.size(); i++)
	{
		cout << v1[i] << " ";
	}
	cout << endl;
	//利用at访问元素
	for (int i = 0; i < v1.size(); i++)
	{
		cout << v1.at(i) << " ";
	}
	cout << endl;
	//获取第一个元素
	cout << v1.front() << endl;
	//获取最后一个元素
	cout << v1.back() << endl;
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 3.2.7vector互换容器

功能描述：

实现两个容器内元素进行互换

函数原型：

1.`swap(vec);`   //将vec与本身的元素互换

示例：

```c++
//vector容器的互换
#include <vector>
void printVector(vector<int>& v)
{
	for (vector<int>::iterator it = v.begin(); it != v.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}
//1.基本使用
void test01()
{
	vector<int>v1;
	for (int i = 0; i < 10; i++)
	{
		v1.push_back(i);
	}
	printVector(v1);
	vector<int>v2;
	for (int i = 10; i > 0; i--)
	{
		v2.push_back(i);
	}
	printVector(v2);
	v1.swap(v2);
	printVector(v1);
	printVector(v2);
}
//2.实际用途
//巧用swap可以收缩空间
void test02()
{
	vector<int>v;
	for (int i = 0; i < 100000; i++)
	{
		v.push_back(i);
	}
	cout << v.capacity() << endl;
	cout << v.size() << endl;
	v.resize(3);
	cout << v.capacity() << endl;
	cout << v.size() << endl;
	//巧用swap收缩内存
	vector<int>(v).swap(v);//匿名对象
	cout << v.capacity() << endl;
	cout << v.size() << endl;
}
int main()
{
	//test01();
	test02();
	system("pause");
	return 0;
}
```

#### 3.2.8vector预留空间

功能描述：
减少vector在动态扩展容量时的扩展次数

函数原型：

1.`reserve(int len);`  //容器预留len个元素长度，预留位置不初始化，元素不可访问

示例：

```c++
//vector容器 预留空间
#include <vector>
void test01()
{
	vector<int>v;

	//利用reserve预留空间
	v.reserve(100000);
	int num = 0;//统计开辟次数
	int* p = NULL;
	for (int i = 0; i < 100000; i++)
	{
		v.push_back(i);
		if (p != &v[0])
		{
			p = &v[0];
			num++;
		}
	}
	cout << num << endl;
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

### 3.3deque容器

#### 3.3.1deque容器基本概念

功能：

双端数组，可以对头端进行插入删除操作

deque和vector区别：

1.vector对于头部的插入删除效率低，数据量越大，效率越低

2.deque相对而言，对头部的插入删除速度会比vector快

3.vector访问元素时的速度会比deque快，这和两者内部实现有关

deque内部工作原理：

![image-20240713220824619](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240713220824619.png)

deque容器的迭代器也是支持随机访问的

#### 3.3.2deque构造函数

功能描述：

deque容器构造

函数原型：

1.`deque<T>deqT;`   //默认构造形式

2.`deque(begin,end);`  //构造函数将[begin,end)区间中的元素拷贝给本身

3.`deque(n,elem);`    //构造函数将n个elem拷贝给本身

4.`deque(const deque &deq);`   //拷贝构造函数

示例：

```c++
//deque 构造函数
#include <deque>
void printdeque(deque<int>& d)
{
	for (deque<int>::iterator it = d.begin(); it != d.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}
void test01()
{
	deque<int>d1;
	for (int i = 0; i < 10; i++)
	{
		d1.push_back(i);
	}
	printdeque(d1);
	deque<int>d2(d1.begin(), d1.end());
	printdeque(d2);
	deque<int>d3(10, 100);
	printdeque(d3);
	deque<int>d4(d3);
	printdeque(d4);
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 3.3.3deque赋值操作

功能描述：

给deque容器进行赋值

函数原型：

1.`deque& operator=(const deque &deq);`   //重载等号操作符

2.`assign(begin,end);`   //将[begin，end)区间中的数据拷贝赋值给本身

3.`assign(n,elem);`  //将n个elem拷贝赋值给本身

示例：

```c++
//deque容器赋值操作
#include <deque>
void printdeque(const deque<int>& d)
{
	for (deque<int>::const_iterator it = d.begin(); it != d.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}
void test01()
{
	deque<int>d1;
	for (int i = 0; i < 10; i++)
	{
		d1.push_back(i);
	}
	printdeque(d1);
	deque<int>d2;
	d2 = d1;
	printdeque(d2);
	deque<int>d3;
	d3.assign(d1.begin(), d1.end());
	printdeque(d3);
	deque<int>d4;
	d4.assign(10, 100);
	printdeque(d4);
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 3.3.4deque大小操作

功能描述：

对deque容器的大小进行操作

函数原型：

1.`deque.empty();`   //判断容器是否为空

2.`deque.size();`   //返回容器中元素的个数

3.`deque.resize(num);`   //重新指定容器的长度为num，若容器变长，则以默认值填充新位置。

//如果容器变短，则末尾超出容器长度的元素被删除

4.`deque.resize(num,elem);`    //重新指定容器的长度为num，若容器变长，则以elem填充新位置。

//如果容器变短，则末尾超出容器长度的元素被删除

示例：

```c++
//deque容器大小操作
#include <deque>
void printdeque(const deque<int>& d)
{
	for (deque<int>::const_iterator it = d.begin(); it != d.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}
void test01()
{
	deque<int>d1;
	for (int i = 0; i < 10; i++)
	{
		d1.push_back(i);
	}
	printdeque(d1);
	if (d1.empty())
	{
		cout << "为空" << endl;
	}
	else
	{
		cout << d1.size() << endl;

	}
	d1.resize(15, 1);
	printdeque(d1);
	d1.resize(5);
	printdeque(d1);
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 3.3.5deque插入与删除

功能描述：

向deque容器中插入和删除数据

函数原型：

两端插入操作：

1.`push_back(elem);`   //在容器尾部添加一个数据

2.`push_front(elem);`   //在容器的头部插入一个数据

3.`pop_back();`   //删除容器最后一个数据

4.`pop_front();`   //删除容器第一个数据

指定位置操作：
1.`insert(pos,elem);`    //在pos位置插入一个elem元素的拷贝，返回新数据的位置

2.`insert(pos,n,elem);`   //在pos位置插入n个elem数据，无返回值

3.`insert(pos,begin,end);`   //在pos位置插入[begin,end)区间的数据，无返回值

4.`clear();`    //清空容器的所有数据

5.`erase(begin,end);`   //删除[begin，end)区间的数据，返回下一个数据的位置

6.`erase(pos);`   //删除pos位置的数据，返回下一个数据的位置

示例：

```c++
//deque容器插入和删除
#include <deque>
void printdeque(const deque<int>& d)
{
	for (deque<int>::const_iterator it = d.begin(); it != d.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}
//两端操作
void test01()
{
	deque<int>d1;
	//尾插
	d1.push_back(10);
	d1.push_back(20);
	//头插
	d1.push_front(100);
	d1.push_front(200);
	printdeque(d1);
	//尾删
	d1.pop_back();
	printdeque(d1);
	
}
void test02()
{
	deque<int>d1;
	d1.push_back(10);
	d1.push_back(20);
	d1.push_front(100);
	d1.push_front(200);
	printdeque(d1);
	//insert插入
	d1.insert(d1.begin(), 1000);
	printdeque(d1);
	d1.insert(d1.begin(), 2, 10000);
	printdeque(d1);
	//按照区间进行插入
	deque<int>d2;
	d2.push_back(1);
	d2.push_back(2);
	d2.push_back(3);
	d1.insert(d1.begin(), d2.begin(), d2.end());
}
void test03()
{
	deque<int>d1;
	d1.push_back(10);
	d1.push_back(20);
	d1.push_front(100);
	d1.push_front(200);
	//删除
	deque<int>::iterator it = d1.begin();
	it++;
	d1.erase(it);
	printdeque(d1);
	//按区间方式删除
	d1.erase(d1.begin(), d1.end());
	//清空
	d1.clear();
	printdeque(d1);
}
int main()
{
	//test01();
	test02();
	system("pause");
	return 0;
}
```

#### 3.3.6deque数据存取

功能描述：

对deque中的数据的存取操作

函数原型：

1.`at(int idx);`   //返回索引idx所指的数据

2.`operator[];`    //返回索引idx所指的数据

3.`front();`    //返回容器中第一个数据元素

4.`back();`    //返回容器中最后一个数据元素

示例：

```c++
//deque容器数据存取
#include <deque>
void test01()
{
	deque<int>d;
	d.push_back(10);
	d.push_back(20);
	d.push_back(30);
	d.push_front(100);
	d.push_front(200);
	d.push_front(300);
	//通过[]方式访问元素
	for (int i = 0; i < d.size(); i++)
	{
		cout << d[i] << " ";
	}
	cout << endl;
	//利用at方式访问元素
	for (int i = 0; i < d.size(); i++)
	{
		cout << d.at(i) << " ";
	}
	cout << endl;
	cout << d.front() << endl;
	cout << d.back() << endl;
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 3.3.7deque排序

功能描述：

利用算法实现对deque容器进行排序

算法：

1.`sort(iterator begin,iterator end);`   //对begin和end区间内元素进行排序

示例：

```c++
//deque容器排序
#include <deque>
#include <algorithm>
void printdeque(const deque<int>& d)
{
	for (deque<int>::const_iterator it = d.begin(); it != d.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}
void test01()
{
	deque<int>d;
	d.push_back(10);
	d.push_back(20);
	d.push_back(30);
	d.push_front(100);
	d.push_front(200);
	d.push_front(300);
	//排序 默认排序规则：从小到大，升序
	sort(d.begin(), d.end());
	printdeque(d);
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```

注：对于支持随机访问的迭代器的容器，都可以利用sort算法直接对其排序

### 3.4stack容器

#### 3.4.1stack基本概念

概念：stack是一种先进后出的数据结构，他只有一个出口

![image-20240716225453902](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240716225453902.png)

注意：

1.栈可以判断容器是否为空

2.栈可以返回元素的个数

#### 3.4.2stack常用接口

功能描述：栈容器常用的对外接口

![image-20240716230123396](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240716230123396.png)

示例：

```c++
//栈stack容器
#include <stack>
void test01()
{
	stack<int>s;
	//入栈
	s.push(10);
	s.push(20);
	s.push(30);
	s.push(40);
	//只要栈不为空，查看栈顶，并且执行出栈操作
	while (!s.empty())
	{
		cout << s.top() << endl;
		s.pop();
	}
	cout << s.size() << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```

### 3.5queue容器

#### 3.5.1queue基本概念

概念：Queue是一种先进先出的数据结构，它有两个出口

![image-20240716231219673](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240716231219673.png)

![image-20240716231936945](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240716231936945.png)

#### 3.5.2queue常用接口

功能描述：栈容器常用的对外接口

![image-20240716232035120](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240716232035120.png)

示例：

```c++
//队列 Queue
#include <queue>
class Person
{
public:
	Person(string name, int age)
	{
		this->m_name = name;
		this->m_age = age;
	}
	string m_name;
	int m_age;
};
void test01()
{
	queue<Person>q;
	//准备数据
	Person p1("唐僧", 30);
	Person p2("孙悟空", 1000);
	Person p3("猪八戒", 900);
	Person p4("沙僧", 800);
	//入队
	q.push(p1);
	q.push(p2);
	q.push(p3);
	q.push(p4);
	cout << q.size() << endl;
	while (!q.empty())
	{
		//队首
		cout << q.front().m_name << q.front().m_age << endl;
		//队尾
		cout << q.back().m_name << q.back().m_age << endl;
		//出队
		q.pop();
	}
	cout << q.size() << endl;
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

### 3.6list容器

#### 3.6.1list基本概念

功能：将数据进行链式存储

![image-20240717224951462](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240717224951462.png)

![image-20240717225705120](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240717225705120.png)

![image-20240717225907485](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240717225907485.png)

总结：STL中list和vector是两个最常被使用的容器，各有优缺点

#### 3.6.2list构造函数

功能描述:
创建list容器

函数原型：

1.`list<T> lst;`   //list采用模板类实现，对象的默认构造形式

2.`list(begin,end);`   //构造函数将[begin,end)区间中的元素拷贝给本身

3.`list(n,elem);`   //构造函数将n个elem拷贝给本身

4.`list(const list &lst);`   //拷贝构造函数

示例：

```c++
//list容器的构造函数
#include <list>
void printlist(const list<int>& L)
{
	for (list<int>::const_iterator it = L.begin(); it != L.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}
void test01()
{
	list<int>L1;
	//添加数据
	L1.push_back(10);
	L1.push_back(20);
	L1.push_back(30);
	L1.push_back(40);
	//遍历容器
	printlist(L1);
	//区间方法
	list<int>L2(L1.begin(), L1.end());
	printlist(L2);
	//拷贝构造
	list<int>L3(L2);
	printlist(L3);
	//n个elem
	list<int>L4(10, 1000);
	printlist(L4);
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 3.6.3list赋值与交换

功能描述：

给list容器进行赋值，以及交换list容器

函数原型：

1.`assign(begin,end);`  //将[begin,end)区间中的数据赋值给本身

2.`assign(n,elem);`   //将n个elem拷贝赋值给本身

3.`list& operator=(const list &lst);`   //重载等号操作符

4.`swap(lst);`  //将lst与本身元素互换

示例：

```c++
//list容器赋值和交换
#include <list>
void printlist(const list<int>& L)
{
	for (list<int>::const_iterator it = L.begin(); it != L.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}
//赋值
void test01()
{
	list<int>L1;
	//添加数据
	L1.push_back(10);
	L1.push_back(20);
	L1.push_back(30);
	L1.push_back(40);
	//遍历容器
	printlist(L1);
	list<int>L2;
	L2 = L1;
	printlist(L2);
	list<int>L3;
	L3.assign(L2.begin(), L2.end());
	printlist(L3);
	list<int>L4;
	L4.assign(10, 100);
	printlist(L4);
}
//交换
void test02()
{
	list<int>L1;
	//添加数据
	L1.push_back(10);
	L1.push_back(20);
	L1.push_back(30);
	L1.push_back(40);
	list<int>L2;
	L2.assign(10, 100);
	printlist(L1);
	printlist(L2);
	L1.swap(L2);
	printlist(L1);
	printlist(L2);
}
int main()
{
	test01();
	test02();
	system("pause");
	return 0;
}
```

#### 3.6.4list大小操作

功能描述：

对list容器的大小进行操作

函数原型：

1.`size();`   //返回容器中元素的个数

2.`empty();`   //判断容器是否为空

3.`resize(num);`  //重新指定容器的长度为num，若容器变长，则以默认值填充新位置。

//如果容器变短，则末尾超出容器长度的元素被删除

4.`resize(num,elem);`  //重新指定容器的长度为num，若容器变长，则以elem填充新位置。

//如果容器变短，则末尾超出容器长度的元素被删除

示例：

```c++
//list容器大小操作
#include <list>
void printlist(const list<int>& L)
{
	for (list<int>::const_iterator it = L.begin(); it != L.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}
void test01()
{
	list<int>L1;
	//添加数据
	L1.push_back(10);
	L1.push_back(20);
	L1.push_back(30);
	L1.push_back(40);
	printlist(L1);
	if (L1.empty())
	{
		cout << "L1为空" << endl;
	}
	else
	{
		cout << L1.size() << endl;
	}
	L1.resize(10);
	printlist(L1);
	L1.resize(2);
	printlist(L1);
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 3.6.5list插入和删除

功能描述：

对list容器进行数据的插入和删除

函数原型：

![image-20240718205859035](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240718205859035.png)

示例：

```c++
//list容器插入和删除
#include <list>
void printlist(const list<int>& L)
{
	for (list<int>::const_iterator it = L.begin(); it != L.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}
void test01()
{
	list<int>L;
	//尾插
	L.push_back(10);
	L.push_back(20);
	L.push_back(30);
	//头插
	L.push_front(100);
	L.push_front(200);
	L.push_front(300);
	printlist(L);
	//尾删
	L.pop_back();
	printlist(L);
	//头删
	L.pop_front();
	printlist(L);
	//insert插入
	list<int>::iterator it = L.begin();
	L.insert(++it, 1000);
	printlist(L);
	//删除
	it = L.begin();
	L.erase(it);
	printlist(L);
	//移除
	L.push_back(10000);
	L.push_back(10000);
	L.push_back(10000);
	L.push_back(10000);
	printlist(L);
	L.remove(10000);
	printlist(L);
	//清空
	L.clear();
	printlist(L);
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 3.6.6list数据存取

功能描述：

对list容器中数据进行存取

函数原型：

1.`front();`   //返回第一个元素

2.`back();`   //返回最后一个元素

示例：

```c++
//list容器数据存取
#include <list>
void printlist(const list<int>& L)
{
	for (list<int>::const_iterator it = L.begin(); it != L.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}
void test01()
{
	list<int>L;
	//尾插
	L.push_back(10);
	L.push_back(20);
	L.push_back(30);
	L.push_back(40);
	//不可以用[]或at方式访问list容器元素
	cout << "第一个元素为：" << L.front() << endl;
	cout << "最后一个元素为：" << L.back() << endl;
	list<int>::iterator it = L.begin();
	it++;//支持访问
	it--;//支持访问
	//it = it + 1;//不支持随机访问
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 3.6.7list反转和排序

功能描述：

将容器中的元素反转，以及将容器中的数据进行排序

函数原型：

1.`reverse();`   //反转链表

2.`sort();`   //链表排序

示例：

```c++
//list容器反转和排序
#include <list>
#include <algorithm>
void printlist(const list<int>& L)
{
	for (list<int>::const_iterator it = L.begin(); it != L.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}
void test01()
{
	list<int>L;
	//尾插
	L.push_back(20);
	L.push_back(10);
	L.push_back(50);
	L.push_back(40);
	L.push_back(30);
	printlist(L);
	//反转
	L.reverse();
	printlist(L);
}
bool myCompare(int v1,int v2)
{
	//降序
	return v1 > v2;
}
//排序
void test02()
{
	list<int>L;
	//尾插
	L.push_back(20);
	L.push_back(10);
	L.push_back(50);
	L.push_back(40);
	L.push_back(30);
	printlist(L);
	//排序
	//sort(L.begin(), L.end());//不行
	L.sort();//默认排序规则 从小到大 升序
	printlist(L);
	L.sort(myCompare);
	printlist(L);
}
int main()
{
	//test01();
	test02();
	system("pause");
	return 0;
}
```

### 3.7set/multiset容器

#### 3.7.1set基本概念

简介：

所有元素都会在插入时自动排序

本质：

set/multiset属于关联式容器，底层结构是用二叉树实现的

set和multiset区别：

1.set不允许容器中有重复元素

2.multiset允许容器中有重复的元素

#### 3.7.2set构造和赋值

功能描述：创建set容器以及赋值

构造：

1.`set<T> st;`    //默认构造函数

2.`set(const set &st);`   //拷贝构造函数

赋值：

1.`set& operator=(const set &st);`    //重载等号操作符

示例：

```c++
//set容器的构造和赋值
#include <set>
void printset(set<int>& s)
{
	for(set<int>::iterator it = s.begin(); it != s.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}
void test01()
{
	set<int>s1;
	//插入数据只有insert
	s1.insert(10);
	s1.insert(30);
	s1.insert(40);
	s1.insert(20);
	//set不允许插入重复值
	printset(s1);
	//拷贝构造
	set<int>s2(s1);
	printset(s2);
	//赋值
	set<int>s3;
	s3 = s2;
	printset(s3);
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 3.7.3set大小和交换

功能描述：

统计set容器大小以及交换set容器

函数原型：

1.`size();`   //返回容器中元素的数目

2.`empty();`   //判断容器是否为空

3.`swap(st);`   //交换两个集合容器

示例：

```c++
//set容器大小和交换
// #include <set>
void printset(set<int>& s)
{
	for (set<int>::iterator it = s.begin(); it != s.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}
//大小
void test01()
{
	set<int>s1;
	s1.insert(10);
	s1.insert(30);
	s1.insert(40);
	s1.insert(20);
	printset(s1);
	if (s1.empty())
	{
		cout << "s1为空" << endl;
	}
	else
	{
		cout << s1.size() << endl;
	}
}
//交换
void test02()
{
	set<int>s1;
	s1.insert(10);
	s1.insert(30);
	s1.insert(40);
	s1.insert(20);
	set<int>s2;
	s1.insert(100);
	s1.insert(200);
	s1.insert(300);
	s1.insert(400);
	printset(s1);
	printset(s2);
	s1.swap(s2);
	printset(s1);
	printset(s2);
}

int main()
{
	//test01();
    test02();
	system("pause");
	return 0;
}
```

#### 3.7.4set插入和删除

功能描述：

set容器进行插入数据和删除数据

函数原型：

![image-20240719223429653](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240719223429653.png)

示例：

```c++
//set容器 插入和删除
#include <set>
void printset(set<int>& s)
{
	for (set<int>::iterator it = s.begin(); it != s.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}
void test01()
{
	set<int>s1;
	s1.insert(10);
	s1.insert(30);
	s1.insert(40);
	s1.insert(20);
	printset(s1);
	//删除
	s1.erase(s1.begin());
	printset(s1);
	//删除重载
	s1.erase(30);
	printset(s1);
	//清空
	s1.erase(s1.begin(), s1.end());
	s1.clear();
	printset(s1);
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 3.7.5set查找和统计

功能描述：

对set容器进行查找数据以及统计数据

函数原型：

1.`find(Key);`  //查找Key是否存在，若存在，返回改键的元素的迭代器，若不存在，返回set.end();

2.`count(Key);`   //统计Key的元素个数

示例：

```c++
//set容器 查找和统计
#include <set>
//查找
void test01()
{
	set<int>s1;
	s1.insert(10);
	s1.insert(30);
	s1.insert(40);
	s1.insert(20);
	set<int>::iterator pos = s1.find(30);
	if (pos != s1.end())
	{
		cout << "找到元素" << endl;
	}
	else
	{
		cout << "未找到元素" << endl;
	}
}
//统计
void test02()
{
	set<int>s1;
	s1.insert(10);
	s1.insert(30);
	s1.insert(40);
	s1.insert(20);
	int num = s1.count(30);
	cout << num << endl;
}
int main()
{
	//test01();
	test02();
	system("pause");
	return 0;
}
```

#### 3.7.6set和multiset区别

区别：

![image-20240720220752902](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240720220752902.png)

示例：

```c++
//set和multiset的区别
#include <set>
void printset(multiset<int>& s)
{
	for (multiset<int>::iterator it = s.begin(); it != s.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}
void test01()
{
	set<int>s;
	pair<set<int>::iterator,bool>ret = s.insert(10);
	if (ret.second)
	{
		cout << "第一次插入成功" << endl;
	}
	else
	{
		cout << "第一次插入失败" << endl;
	}
	ret = s.insert(10);
	if (ret.second)
	{
		cout << "第二次插入成功" << endl;
	}
	else
	{
		cout << "第二次插入失败" << endl;
	}
	multiset<int>ms;
	//允许插入重复值
	ms.insert(10);
	ms.insert(10);
	printset(ms);
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 3.7.7pair对组创建

功能描述：

成对出现的数据，利用对组可以返回两个数据

两种创建方式：

1.`pair<type,type> p (values1,values2);`  

2.`pair<type,type> p = make_pair(values1,values2);` 

示例：

```c++
//pair对组的创建
void test01()
{
	pair<string, int>p("Tom", 20);
	cout << p.first << endl;
	cout << p.second << endl;
	pair<string, int>p2 = make_pair("Jerry", 30);
	cout << p2.first << endl;
	cout << p2.second << endl;
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 3.7.8set容器排序

主要技术点：

利用仿函数，可以改变排序规则

示例1  set存放内置数据类型：

```c++
//set容器排序
#include <set>
class MaCompare
{
public:
	bool operator()(int v1,int v2)const
	{
		return v1 > v2;
	}
};
void printset(set<int>& s)
{
	for (set<int>::iterator it = s.begin(); it != s.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}
void test01()
{
	set<int>s1;
	s1.insert(10);
	s1.insert(40);
	s1.insert(20);
	s1.insert(50);
	s1.insert(30);
	printset(s1);
	set<int,MaCompare>s2;
	s2.insert(10);
	s2.insert(40);
	s2.insert(20);
	s2.insert(50);
	s2.insert(30);
	for (set<int,MaCompare>::iterator it = s2.begin(); it != s2.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;

}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

示例二

```c++
//set容器的排序，存放自定义数据类型
#include <set>
#include <string>
class Person
{
public:
	Person(string name, int age)
	{
		this->m_name = name;
		this->m_age = age;
	}
	string m_name;
	int m_age;
};
class comparePerson
{
public:
	bool operator()(const Person& p1, const Person& p2)const
	{
		return p1.m_age > p2.m_age;
	}
};
void test01()
{
	set<Person,comparePerson>s;
	Person p1("刘备", 24);
	Person p2("关羽", 25);
	Person p3("张飞", 27);
	Person p4("赵云", 28);
	s.insert(p1);
	s.insert(p2);
	s.insert(p3);
	s.insert(p4);
	for (set<Person,comparePerson>::iterator it = s.begin(); it != s.end(); it++)
	{
		cout << it->m_name << " ";
		cout << it->m_age << " ";
	}
	cout << endl;
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

### 3.8map/multimap容器

#### 3.8.1map基本概念

![image-20240721221925894](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240721221925894.png)

#### 3.8.2map构造和赋值

功能描述：

对map容器进行构造和赋值操作

函数原型：

1.`map<T1,T2>map;`   //map默认构造函数

2.`map(const map &mp);`   //拷贝构造函数

赋值：

1.`map& operator=(const map &mp);`   //重载等号操作符

示例：

```c++
//map容器 构造和赋值
#include <map>
void printmap(map<int,int>&m)
{
	for (map<int, int>::iterator it = m.begin(); it != m.end(); it++)
	{
		cout << (*it).first << it->second << endl;
	}
	cout << endl;
}
void test01()
{
	map<int, int>m;
	m.insert(pair<int, int>(1, 10));
	m.insert(pair<int, int>(2, 20));
	m.insert(pair<int, int>(3, 30));
	m.insert(pair<int, int>(4, 40));
	printmap(m);
	//拷贝构造
	map<int, int>m2(m);
	printmap(m);
	//赋值
	map<int, int>m3;
	m3 = m2;
	printmap(m3);
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 3.8.3map大小和交换

功能描述：

统计map容器大小以及交换map容器

函数原型：

1.`size();`  //返回容器中元素的数目

2.`empty();`   //判断容器是否为空

3.`swap(st);`   //交换两个集合容器

示例：

```c++
//map容器的大小和交换
#include <map>
void printmap(map<int, int>& m)
{
	for (map<int, int>::iterator it = m.begin(); it != m.end(); it++)
	{
		cout << (*it).first << it->second << endl;
	}
	cout << endl;
}
//大小
void test01()
{
	map<int, int>m;
	m.insert(pair<int, int>(1, 10));
	m.insert(pair<int, int>(2, 20));
	m.insert(pair<int, int>(3, 30));
	m.insert(pair<int, int>(4, 40));
	printmap(m);
	if (!m.empty())
	{
		cout << m.size() << endl;
	}
	else
	{
		cout << "为空" << endl;
	}
}
//交换
void test02()
{
	map<int, int>m1;
	m1.insert(pair<int, int>(1, 10));
	m1.insert(pair<int, int>(2, 20));
	m1.insert(pair<int, int>(3, 30));
	map<int, int>m2;
	m2.insert(pair<int, int>(4, 40));
	m2.insert(pair<int, int>(5, 50));
	m2.insert(pair<int, int>(6, 60));
	m1.swap(m2);
	printmap(m1);
	printmap(m2);
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 3.8.4map插入和删除

功能描述：

map容器进行插入数据和删除数据

函数原型：

![image-20240721224239598](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240721224239598.png)

示例：

```c++
//map容器插入和删除
#include <map>
void printmap(map<int, int>& m)
{
	for (map<int, int>::iterator it = m.begin(); it != m.end(); it++)
	{
		cout << (*it).first << it->second << endl;
	}
	cout << endl;
}
//大小
void test01()
{
	map<int, int>m;
	m.insert(pair<int, int>(1, 10));
	m.insert(make_pair(2, 20));
	m.insert(map<int, int>::value_type(3, 30));
	m[4] = 40;
	printmap(m);
	//删除
	m.erase(m.begin());
	printmap(m);
	m.erase(3);
	printmap(m);
	//清空
	m.erase(m.begin(), m.end());
	printmap(m);
	m.clear();
	printmap(m);

}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 3.8.5map查找和统计

功能描述：

对map容器进行查找数据以及统计数据

函数原型：

1.`find(key);`  //查找key是否存在，若存在，返回改键的元素的迭代器；若不存在，返回set.end();

2.`count(key);`   //统计key的元素个数

示例：

```c++
//map查找和统计
#include <map>
void printmap(map<int, int>& m)
{
	for (map<int, int>::iterator it = m.begin(); it != m.end(); it++)
	{
		cout << (*it).first << it->second << endl;
	}
	cout << endl;
}
void test01()
{
	//查找
	map<int, int>m;
	m.insert(pair<int, int>(1, 10));
	m.insert(pair<int, int>(2, 20));
	m.insert(pair<int, int>(3, 30));
	map<int, int>::iterator pos = m.find(3);
	if (pos != m.end())
	{
		cout << (*pos).first << pos->second << endl;
	}
	else
	{
		cout << "未找到元素" << endl;
	}

	//统计
	int num = m.count(3);
	cout << num << endl;
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 3.8.6map容器排序

功能描述：

map容器默认排序规则为 按照key值进行 从小到大排序，掌握如何改变排序规则

主要技术点：

利用仿函数，可以改变排序规则

示例：

```c++
//map容器排序
#include <map>
class mycompare
{
public:
	bool operator()(int v1, int v2)const
	{
		return v1 > v2;
	}
};
void test01()
{
	map<int, int,mycompare>m;
	m.insert(make_pair(1, 10));
	m.insert(make_pair(2, 20));
	m.insert(make_pair(3, 30));
	m.insert(make_pair(4, 40));
	m.insert(make_pair(5, 50));

	for (map<int, int, mycompare>::iterator it = m.begin(); it != m.end(); it++)
	{
		cout << (*it).first << it->second << endl;
	}
	cout << endl;
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

## 4.STL-函数对象

### 4.1函数对象

#### 4.1.1函数对象概念

概念：

1.重载函数调用操作符的类，其对象常称为函数对象

2.函数对象使用重载的()时，行为类似函数调用，也叫仿函数

本质：

函数对象是一个类，不是一个函数

#### 4.1.2函数对象使用

特点：

![image-20240723215944517](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240723215944517.png)

示例：

```c++
//函数对象
class MyAdd
{
public:
	int operator()(int v1, int v2)
	{
		return v1 + v2;
	}
};
void test01()
{
	MyAdd myadd;
	cout << myadd(10, 10) << endl;
}
class MyPrint
{
public:
	MyPrint()
	{
		this->count = 0;
	}
	void operator()(string test)
	{
		cout << test << endl;
		this->count++;
	}
	int count;//内部自己的状态

};
void test02()
{
	MyPrint myprint;
	myprint("hello world");
	myprint("hello world");
	myprint("hello world");
	myprint("hello world");
	cout << myprint.count << endl;
}
void doPrint(MyPrint& mp, string test)
{
	mp(test);
}
void test03()
{
	MyPrint myprint;
	doPrint(myprint, "hello C++");
}
int main()
{
	//test01();
	//test02();
	test03();
	system("pause");
	return 0;
}
```

### 4.2谓词

#### 4.2.1谓词概念

概念：

![image-20240723221713805](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240723221713805.png)

#### 4.2.2一元谓词

示例：

```c++
//一元谓词
#include <vector>
#include <algorithm>
class GreaterFive
{
public:
	bool operator()(int val)
	{
		return val > 5;
	}
};
void test01()
{
	vector<int>v;
	for (int i = 0; i < 10; i++)
	{
		v.push_back(i);
	}
	//查找容器中有没有大于5的数字
	vector<int>::iterator it = find_if(v.begin(), v.end(), GreaterFive());
	if (it == v.end())
	{
		cout << "未找到" << endl;
	}
	else
	{
		cout << *it << endl;
	}
}
int main()
{

	system("pause");
	return 0;
}
```

#### 4.2.3二元谓词

示例：

```c++
//二元谓词
#include <vector>
#include <algorithm>
class GreaterFive
{
public:
	bool operator()(int v1,int v2)
	{
		return v1 > v2;
	}
};
void test01()
{
	vector<int>v;
	v.push_back(10);
	v.push_back(40);
	v.push_back(20);
	v.push_back(30);
	v.push_back(50);
	sort(v.begin(), v.end());
	for (vector<int>::iterator it = v.begin(); it != v.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
	//使用函数对象
	sort(v.begin(),v.end(), GreaterFive());
	for (vector<int>::iterator it = v.begin(); it != v.end(); it++)
	{
		cout << *it << " ";
	}
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

### 4.3内建函数对象

#### 4.3.1内建函数对象意义

概念：

1.STL内建了一些函数对象

分类：

1.算术仿函数

2.关系仿函数

3.逻辑仿函数

用法：

这些仿函数所产生的对象，用法和一般函数完全相同

使用内建函数对象，需要引入头文件`#include <functional>`

#### 4.3.2算术仿函数

功能描述：

实现四则运算

其中negate是一元运算，其他都是二元运算

仿函数原型：

![image-20240723225253020](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240723225253020.png)

示例：

```c++
//内建函数对象 算术仿函数
#include <functional>
void test01()
{
	negate<int>n;
	cout << n(50) << endl;
}
void test02()
{
	plus<int>p;
	cout << p(10, 20) << endl;
}
int main()
{
	//test01();
	test02();
	system("pause");
	return 0;
}
```

#### 4.3.3关系仿函数

功能描述：

实现关系对比

仿函数原型：

![image-20240724222958758](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240724222958758.png)

示例：

```c++
//内建函数对象 关系仿函数
#include <functional>
#include <algorithm>
#include <vector>
//大于 greater
class MyCompare
{
public:
	bool operator()(int v1, int v2)
	{
		return v1 > v2;
	}
};
void test01()
{
	vector<int>v;
	v.push_back(10);
	v.push_back(30);
	v.push_back(40);
	v.push_back(20);
	v.push_back(50);

	for (vector<int>::iterator it = v.begin(); it != v.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
	//降序
	//sort(v.begin(), v.end(), MyCompare());
	sort(v.begin(), v.end(), greater<int>());
	for (vector<int>::iterator it = v.begin(); it != v.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 4.3.4逻辑仿函数

功能描述：

实现逻辑运算

函数原型：

![image-20240724223913103](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240724223913103.png)

示例：

```c++
//逻辑仿函数
//逻辑非 logical_not
#include <functional>
#include <algorithm>
#include <vector>
void test01()
{
	vector<bool>v;
	v.push_back(true);
	v.push_back(false);
	v.push_back(true);
	v.push_back(false);
	for (vector<bool>::iterator it = v.begin(); it != v.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
	vector<bool>v2;
	v2.resize(v.size());
	transform(v.begin(), v.end(), v2.begin(), logical_not<bool>());
	for (vector<bool>::iterator it = v2.begin(); it != v2.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

## 5.STL - 常用算法

概述：

![image-20240725230741650](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240725230741650.png)

### 5.1常用遍历算法

学习目标：

掌握常用的遍历算法

算法简介：

1.`for_each`  //遍历容器

2.`transform`  //搬运容器到另一个容器中

#### 5.1.1 for_each

功能描述：

实现遍历容器

函数原型：

![image-20240725231033878](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240725231033878.png)

示例：

```c++
#include <iostream>
using namespace std;
#include <vector>
#include <algorithm>
//常用遍历算法
//普通函数
void print(int val)
{
	cout << val << " ";
}
//仿函数
class print01
{
public:
	void operator()(int val)
	{
		cout << val << " ";
	}
};
void test01()
{
	vector<int>v;
	for (int i = 0; i < 10; i++)
	{
		v.push_back(i);
	}

	for_each(v.begin(), v.end(), print);
	for_each(v.begin(), v.end(), print01());

}

int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 5.1.2 transform

功能描述：

搬运容器到另一个容器中

函数原型：

![image-20240726231729154](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240726231729154.png)

示例：

```c++
//transform
class Transform
{
public:
	int operator()(int v)
	{
		return v;
	}
};
class Myprint
{
public:
	void operator()(int val)
	{
		cout << val << " ";
	}
};
void test01()
{
	vector<int>v;
	for (int i = 0; i < 10; i++)
	{
		v.push_back(i);
	}

	vector<int>vTarget;//目标容器
	vTarget.resize(v.size());//目标空间需要提前开辟空间
	transform(v.begin(),v.end(),vTarget.begin(), Transform());
	for_each(vTarget.begin(), vTarget.end(), Myprint());
	cout << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```

### 5.2常用查找算法

学习目标：

掌握常用的查找算法

算法简介：

![image-20240727173015379](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240727173015379.png)

#### 5.2.1 find

功能描述：

查找指定元素，找到返回指定元素的迭代器，找不到返回结束迭代器end()

函数原型：

![image-20240727173503888](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240727173503888.png)

示例：

```c++
//查找算法
//find
//查找内置数据类型
void test01()
{
	vector<int>v;
	for (int i = 0; i < 10; i++)
	{
		v.push_back(i);
	}
	vector<int>::iterator it = find(v.begin(), v.end(), 5);
	if (it == v.end())
	{
		cout << "没有找到" << endl;
	}
	else
	{
		cout << "找到 " << *it << endl;
	}
}

class Person
{
public:
	Person(string name, int age)
	{
		this->m_name = name;
		this->m_age = age;
	}
	//重载 == 
	bool operator==(const Person& p)
	{
		if (this->m_name == p.m_name && this->m_age == m_age)
		{
			return true;
		}
		else
		{
			return false;
		}
	}
	string m_name;
	int m_age;
};
//查找 自定义数据类型
void test02()
{
	vector<Person>v;
	Person p1("aaa", 10);
	Person p2("bbb", 20);
	Person p3("ccc", 30);
	Person p4("ddd", 40);
	v.push_back(p1);
	v.push_back(p2);
	v.push_back(p3);
	v.push_back(p4);
	vector<Person>::iterator it = find(v.begin(), v.end(), p2);
	if (it == v.end())
	{
		cout << "没有找到" << endl;
	}
	else
	{
		cout << "找到 " << it->m_name << it->m_age << endl;
	}
}
int main()
{
	//test01();
	test02();
	system("pause");
	return 0;
}
```

#### 5.2.2 find_if

功能描述：

按条件查找元素

函数原型：

![image-20240728201055998](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240728201055998.png)

示例：

```c++
//find_if
//1.查找内置数据类型
class GreaterFive
{
public:
	bool operator()(int val)
	{
		return val > 5;
	}
};
void test01()
{
	vector<int>v;
	for (int i = 0; i < 10; i++)
	{
		v.push_back(i);
	}
	vector<int>::iterator it = find_if(v.begin(), v.end(), GreaterFive());
	if (it == v.end())
	{
		cout << "没有找到" << endl;
	}
	else
	{
		cout << "找到 " << *it << endl;
	}
}
//2.查找自定义的数据类型
class Person
{
public:
	Person(string name, int age)
	{
		this->m_name = name;
		this->m_age = age;
	}
	//重载 == 
	bool operator==(const Person& p)
	{
		if (this->m_name == p.m_name && this->m_age == m_age)
		{
			return true;
		}
		else
		{
			return false;
		}
	}
public:
	string m_name;
	int m_age;
};
class Greater20
{
public:
	bool operator()(Person& p)
	{
		return p.m_age > 20;
	}
};
void test02()
{
	vector<Person>v;
	Person p1("aaa", 10);
	Person p2("bbb", 20);
	Person p3("ccc", 30);
	Person p4("ddd", 40);
	v.push_back(p1);
	v.push_back(p2);
	v.push_back(p3);
	v.push_back(p4);
	vector<Person>::iterator it = find_if(v.begin(), v.end(), Greater20());
	if (it == v.end())
	{
		cout << "没有找到" << endl;
	}
	else
	{
		cout << "找到 " << it->m_name << it->m_age << endl;
	}
}
int main()
{
	//test01();
	test02();
	system("pause");
	return 0;
}
```

#### 5.2.3 adjacent_find

功能描述：

查找相邻重复元素

函数原型：

![image-20240730230831889](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240730230831889.png)

示例：

```c++
//adjacent_find
void test01()
{
	vector<int>v;
	v.push_back(0);
	v.push_back(2);
	v.push_back(0);
	v.push_back(3);
	v.push_back(1);
	v.push_back(4);
	v.push_back(3);
	v.push_back(3);
	vector<int>::iterator pos = adjacent_find(v.begin(), v.end());
	if (pos == v.end())
	{
		cout << "未找到相邻重复元素" << endl;
	}
	else
	{
		cout << *pos << endl;
	}
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 5.2.4 binary_search

功能描述：

查找指定元素是否存在

函数原型：

![image-20240730231523376](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240730231523376.png)

示例:

```c++
//binary_search
void test01()
{
	vector<int>v;
	for (int i = 0; i < 10; i++)
	{
		v.push_back(i);
	}
	bool ret = binary_search(v.begin(), v.end(),9);
	if (ret)
	{
		cout << "找到了元素" << endl;
	}
	else
	{
		cout << "未找到元素" << endl;
	}
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 5.2.5 count

功能描述：

统计元素个数

函数原型：

![image-20240731224052225](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240731224052225.png)

示例：

```c++
//count
//1.统计内置是数据类型
void test01()
{
	vector<int>v;
	v.push_back(10);
	v.push_back(40);
	v.push_back(30);
	v.push_back(40);
	v.push_back(20);
	v.push_back(40);
	int num = count(v.begin(), v.end(), 40);
	cout << num << endl;
}
//2.统计自定义数据类型
class Person
{
public:
	Person(string name,int age)
	{
		this->m_name = name;
		this->m_age = age;
	}
	bool operator==(const Person& p)
	{
		if (this->m_age == p.m_age)
		{
			return true;
		}
		else
		{
			return false;
		}
	}
	string m_name;
	int m_age;
};
void test02()
{
	vector<Person>v;
	Person p1("刘备", 35);
	Person p2("关羽", 35);
	Person p3("张飞", 35);
	Person p4("赵云", 30);
	Person p5("曹操", 40);
	Person p("诸葛亮", 35);
	v.push_back(p1);
	v.push_back(p2);
	v.push_back(p3);
	v.push_back(p4);
	v.push_back(p5);
	int num = count(v.begin(), v.end(), p);
	cout << num << endl;
}
int main()
{
	//test01();
	test02();
	system("pause");
	return 0;
}
```

#### 5.2.6 count_if

功能描述：

按条件统计元素个数

函数原型：

![image-20240801215827241](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240801215827241.png)

示例：

```c++
//count_if
//1.统计内置的数据类型
class Greater20
{
public:
	bool operator()(int val)
	{
		return val > 20;
	}
};
void test01()
{
	vector<int>v;
	v.push_back(10);
	v.push_back(40);
	v.push_back(30);
	v.push_back(20);
	v.push_back(40);
	v.push_back(20);

	int num = count_if(v.begin(), v.end(), Greater20());
	cout << num << endl;
}
class Person
{
public:
	Person(string name, int age)
	{
		this->m_name = name;
		this->m_age = age;
	}
	string m_name;
	int m_age;
};
class AgeGreater20
{
public:
	bool operator()(const Person& p)
	{
		return p.m_age > 20;
	}
};
//统计自定义数据类型
void test02()
{
	vector<Person>v;
	Person p1("刘备", 35);
	Person p2("关羽", 35);
	Person p3("张飞", 35);
	Person p4("赵云", 20);
	Person p5("曹操", 40);
	v.push_back(p1);
	v.push_back(p2);
	v.push_back(p3);
	v.push_back(p4);
	v.push_back(p5);
	int num = count_if(v.begin(), v.end(), AgeGreater20());
	cout << num << endl;
}
int main()
{
	//test01();
	test02();
	system("Pause");
	return 0;
}
```

### 5.3常用排序算法

学习目标：

掌握常用的排序算法

算法简介：

![image-20240801221414536](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240801221414536.png)

#### 5.3.1 sort

功能描述：

对容器内元素进行排序

函数原型：

![image-20240801221609080](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240801221609080.png)

示例：

```c++
//常用的排序算法 sort
void Myprint(int val)
{
	cout << val << endl;
}
void test01()
{
	vector<int>v;
	v.push_back(10);
	v.push_back(30);
	v.push_back(50);
	v.push_back(20);
	v.push_back(40);
	sort(v.begin(), v.end());
	for_each(v.begin(), v.end(), Myprint);
	cout << endl;
	//改变为降序
	sort(v.begin(), v.end(), greater<int>());
	for_each(v.begin(), v.end(), Myprint);
	cout << endl;
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 5.3.2 random_shffle

功能描述：

洗牌 指定范围内的元素随机调整次序

函数原型：

![image-20240802220426151](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240802220426151.png)

示例：

```c++
//random_shffle
void MyPint(int val)
{
	cout << val << " "; 
}
void test01()
{
	srand((unsigned int)time(NULL));
	vector<int>v;
	for (int i = 0; i < 10; i++)
	{
		v.push_back(i);
	}
	random_shuffle(v.begin(), v.end());
	for_each(v.begin(), v.end(), MyPint);
	cout << endl;
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 5.3.3 merge

功能描述：

两个容器元素合并，并存储到另一个容器中

函数原型：

![image-20240802222306098](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240802222306098.png)

示例：

```c++
//merge
void MyPrint(int val)
{
	cout << val << " ";
}
void test01()
{
	vector<int>v1;
	vector<int>v2;
	for (int i = 0; i < 10; i++)
	{
		v1.push_back(i);
		v2.push_back(i + 1);
	}
	vector<int>vTarget;
	merge(v1.begin(), v1.end(), v2.begin(), v2.end(), vTarget.begin());
	for_each(vTarget.begin(), vTarget.end(), MyPrint);
	cout << endl;
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

merge合并的必须是两个有序数列

#### 5.3.4 reverse

功能描述：

给容器内元素进行反转

函数原型：

![image-20240803224953259](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240803224953259.png)

示例：

```c++
//reverse
void MtPrint(int val)
{
	cout << val << " ";
}
void test01()
{
	vector<int>v;
	v.push_back(10);
	v.push_back(30);
	v.push_back(50);
	v.push_back(20);
	v.push_back(40);
	for_each(v.begin(), v.end(), MtPrint);
	cout << endl;
	//反转
	reverse(v.begin(), v.end());
	for_each(v.begin(), v.end(), MtPrint);
	cout << endl;
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

### 5.4 常用的拷贝和替换算法

学习目标：

掌握常用的拷贝和替换算法

算法简介：

![image-20240803225702157](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240803225702157.png)

#### 5.4.1 copy

功能描述：

容器内指定范围内的元素拷贝到另一容器中

函数原型：

![image-20240803225827595](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240803225827595.png)

示例：

```c++
//常用的拷贝和替换算法
//copy
void Myprint(int val)
{
	cout << val << " ";
}
void test01()
{
	vector<int>v1;
	for (int i = 0; i < 10; i++)
	{
		v1.push_back(i);
	}
	vector<int>v2;
	v2.resize(v1.size());
	copy(v1.begin(), v1.end(), v2.begin());
	for_each(v2.begin(), v2.end(), Myprint);
	cout << endl;
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 5.4.2 replace

功能描述：

将容器内指定范围的旧元素修改为新元素

函数原型：

![image-20240804220401197](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240804220401197.png)

示例：

```c++
//replace
class MyPrint
{
public:
	void operator()(int val)
	{
		cout << val << " ";
	}
};
void test01()
{
	vector<int>v;
	v.push_back(10);
	v.push_back(20);
	v.push_back(40);
	v.push_back(50);
	v.push_back(60);
	v.push_back(30);
	replace(v.begin(), v.end(), 20, 2000);
	for_each(v.begin(), v.end(), MyPrint());
	cout << endl;
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 5.4.3 replace_if

功能描述：

将区间满足条件的元素，替换成指定元素

函数原型：

![image-20240804221036465](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240804221036465.png)

示例：

```c++
//replace_if
class MyPrint
{
public:
	void operator()(int val)
	{
		cout << val << " ";
	}
};
class Greater30
{
public:
	bool operator()(int val)
	{
		return val >= 30;
	}
};
void test01()
{
	vector<int>v;
	v.push_back(10);
	v.push_back(20);
	v.push_back(40);
	v.push_back(50);
	v.push_back(60);
	v.push_back(30);
	//将大于等于30的替换成3000
	replace_if(v.begin(), v.end(), Greater30(), 3000);
	for_each(v.begin(), v.end(), MyPrint());
	cout << endl;
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 5.4.4 swap

功能描述：

互换两个容器的元素

函数原型：

![image-20240805224038973](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240805224038973.png)

示例：

```c++
//swap
void Myprint(int val)
{
	cout << val << " ";
}
void test01()
{
	vector<int>v1;
	vector<int>v2;
	for (int i = 0; i < 10; i++)
	{
		v1.push_back(i);
		v2.push_back(i * 100);
	}
	for_each(v1.begin(), v1.end(), Myprint);
	cout << endl;
	for_each(v2.begin(), v2.end(), Myprint);
	cout << endl;
	swap(v1, v2);
	for_each(v1.begin(), v1.end(), Myprint);
	cout << endl;
	for_each(v2.begin(), v2.end(), Myprint);
	cout << endl;
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

### 5.5 常用算术生成算法

学习目标：

掌握常用的算术生成算法

注意：
算术生成算法属于小型算法，使用时包含的头文件为`#include <numeric>`

算法简介：

![image-20240805224821807](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240805224821807.png)

#### 5.5.1 accumulate

功能描述：

计算区间内容器元素累计总和

函数原型：

![image-20240805224929340](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240805224929340.png)

示例：

```c++
//常用算术生成算法
//accumulate
#include <numeric>
void test01()
{
	vector<int>v;
	for (int i = 0; i <= 100; i++)
	{
		v.push_back(i);
	}
	int total = accumulate(v.begin(), v.end(),0);
	cout << total << endl;
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 5.5.2 fill

功能描述：

向容器中填充指定的元素

函数原型：
![image-20240806224057919](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240806224057919.png)

示例：

```c++
//fill
void myprint(int val)
{
	cout << val << " ";
}
void test01()
{
	vector<int>v;
	v.resize(10);
	fill(v.begin(), v.end(), 100);
	for_each(v.begin(), v.end(), myprint);
	cout << endl;
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

### 5.6 常用的集合算法

学习目标：

掌握常用的集合算法

算法简介：

![image-20240806224559521](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240806224559521.png)

#### 5.6.1 set_intersection

功能描述：

求两个容器的交集

函数原型：

![image-20240806224726275](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240806224726275.png)

示例：

```c++
//常用的集合算法
//set_intersection
void myprint(int val)
{
	cout << val << " ";
}
void test01()
{
	vector<int>v1;
	vector<int>v2;
	for (int i = 0; i < 10; i++)
	{
		v1.push_back(i);
		v2.push_back(i + 5);
	}
	vector<int>vTarget;
	vTarget.resize(min(v1.size(),v2.size()));
	vector<int>::iterator itend = set_intersection(v1.begin(), v1.end(), v2.begin(), v2.end(), vTarget.begin());
	for_each(vTarget.begin(), itend, myprint);
	cout << endl;
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

#### 5.6.2 set_union

功能描述：

求两个集合的并集

函数原型：

![image-20240807193420909](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240807193420909.png)

示例：

```c++
//set_uniom
void myprint(int val)
{
	cout << val << " ";
}
void test01()
{
	vector<int>v1;
	vector<int>v2;
	for (int i = 0; i < 10; i++)
	{
		v1.push_back(i);
		v2.push_back(i + 5);
	}
	vector<int>vTarget;
	vTarget.resize(v1.size()+v2.size());
	vector<int>::iterator itend = set_union(v1.begin(), v1.end(), v2.begin(), v2.end(), vTarget.begin());
	for_each(vTarget.begin(), vTarget.end(), myprint);
	cout << endl;
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

总结：

1.求并集的两个集合必须的有序序列

2.目标容器开辟的空间需要两个容器相加

3.set_union返回值既是并集中最后一个元素的位置

#### 5.6.3 set_difference

功能描述：

求两个集合的差集

函数原型：

![image-20240807195109033](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240807195109033.png)

示例：

```c++
//set_difference
void myprint(int val)
{
	cout << val << " ";
}
void test01()
{
	vector<int>v1;
	vector<int>v2;
	for (int i = 0; i < 10; i++)
	{
		v1.push_back(i);
		v2.push_back(i + 5);
	}
	vector<int>vTarget;
	vTarget.resize(max(v1.size(), v2.size()));
	vector<int>::iterator itend = set_difference(v1.begin(), v1.end(), v2.begin(), v2.end(), vTarget.begin());
	for_each(vTarget.begin(), vTarget.end(),myprint);
	cout << endl;
}
int main()
{
	test01();
	system("pause");
	return 0;
}
```

总结：

1.求差集的两个集合必须为有序序列

2.目标容器开辟空间需要从两个容器取较大值

3.返回值为差集中最后一个元素的位置
