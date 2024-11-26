# C++面向对象高级编程

## 1.头文件与类的声明

C语言中用函数来处理数据。

C++中把数据和处理这些数据的函数包括在一起，也叫做class

object based：面对的是单一class的设计

object oriented：面对的是多重classes的设计，classes和classes之间的关系。

### 1.C++代码基本形式

.h为头文件

.cpp为主文件

.h也可能为标准库

头文件应该写成防卫式声明

例：

```c++
#ifndef __COMPLEX__
#define __COMPLEX__
...
#endif
```

class template(模板)简介

```c++
template<typename T>
class complex
{
public:
    complex(T r = 0,T i = 0):re(r),im(i){}
}
complex<double> c1(2.5,1.5);
```

## 2.构造函数

### 1.内联(inline)函数

函数若在class Body内定义完成，便自动定义为inline函数

例如：

```c++
inline double imag(const complex& x)
{
    return x.imag();
}
```

注意：若函数太复杂，就不能写成内联函数。

### 2.访问级别

private:一般用来封装数据，只能在内部使用，不能在类外使用。

public:一般用来给函数方法用

protected:保护权限，最高级别权限

### 3.构造函数

构造函数结构：

```c++
类名(){}
```

只有构造函数才有的操作：初值列(初始列)

```c++
complex(double r = 0,double i = 0):re(r),im(i)
```

构造函数可以有很多个 - overloading(重载)

把构造函数放在private区：

设计模式(Singleton):这个类只能在外界被一个变量用

```c++
class A
{
public:
    static A& getInstance();
    setup(){...}
private:
    A();
    A(const A& rhs);
    ...
};
A& A::getInstance()
{
    static A a;
    return a;
}
A::getInstance().setup();
```

### 4.常量成员函数

结构：

```c++
函数类型 函数()const{}
```

**常量成员函数的作用**：保证这个函数**不会修改类的成员变量**。这意味着该函数只能被用于那些**不修改对象状态**的操作，比如获取数据的操作。

### 5.参数与返回值

参数与返回值都尽量用引用。

### 6.友元

在 C++ 中，**友元（friend）** 是一种机制，它允许一个类向特定的函数或类提供访问其私有成员和保护成员的权限。这种机制可以用于增强类之间的协作，但需要谨慎使用，以避免破坏封装性。

------

**友元的类型**

C++ 中的友元主要有以下几种类型：

1. **友元函数（Friend Function）**
   - 一个非成员函数，可以访问类的私有成员和保护成员。
2. **友元类（Friend Class）**
   - 一个类声明为另一个类的友元，该类中的所有成员函数都可以访问友元类的私有和保护成员。
3. **友元成员函数**
   - 一个类的某个成员函数可以是另一个类的友元。

------

**友元的声明**

1. **友元函数的声明**

   - 使用 `friend` 关键字在类内声明友元函数。
   - 友元函数可以是普通函数，也可以是类的成员函数。

   **语法：**

   ```cpp
   class 类名 {
       friend 返回类型 函数名(参数表);
   };
   ```

   **示例：**

   ```cpp
   class MyClass {
   private:
       int value;
   
   public:
       MyClass(int v) : value(v) {}
   
       // 声明友元函数
       friend void display(const MyClass& obj);
   };
   
   // 定义友元函数
   void display(const MyClass& obj) {
       std::cout << "Value: " << obj.value << std::endl;
   }
   ```

2. **友元类的声明**

   - 使用 `friend class` 声明一个类为另一个类的友元。
   - 友元类中的所有成员函数都可以访问被声明类的私有和保护成员。

   **语法：**

   ```cpp
   class 类名 {
       friend class 友元类名;
   };
   ```

   **示例：**

   ```cpp
   class MyClass {
   private:
       int value;
   
   public:
       MyClass(int v) : value(v) {}
   
       friend class FriendClass;  // 声明 FriendClass 为友元类
   };
   
   class FriendClass {
   public:
       void showValue(const MyClass& obj) {
           std::cout << "Value: " << obj.value << std::endl;
       }
   };
   ```

3. **友元成员函数的声明**

   - 一个类的某个成员函数可以被声明为另一个类的友元函数。

   **示例：**

   ```cpp
   class MyClass;
   
   class AnotherClass {
   public:
       void show(const MyClass& obj);
   };
   
   class MyClass {
   private:
       int value;
   
   public:
       MyClass(int v) : value(v) {}
   
       friend void AnotherClass::show(const MyClass& obj);  // 声明友元成员函数
   };
   
   void AnotherClass::show(const MyClass& obj) {
       std::cout << "Value: " << obj.value << std::endl;
   }
   ```

------

### **友元的特点**

1. **访问权限：**
   - 友元可以访问类的所有成员（包括私有和保护成员）。
2. **单向关系：**
   - 友元关系是单向的，声明某函数为友元，并不会使该类成为该函数的友元。
3. **不传递：**
   - 友元关系不能传递。例如，`A` 是 `B` 的友元，`B` 是 `C` 的友元，但 `A` 并不是 `C` 的友元。
4. **破坏封装性：**
   - 友元机制允许外部函数访问私有成员，这在某种程度上破坏了封装性，因此需要慎用。

相同class的各个object互为友元

## 3.操作符重载与临时对象

### 1.成员函数

```c++
#include <iostream>
using namespace std;

// 定义 Complex 类
class complex {
public:
    double re, im; // 实部和虚部

    // 构造函数
    complex(double real = 0, double imag = 0) : re(real), im(imag) {}

    // 重载 operator+= 运算符
    inline complex& operator+=(const complex& r) {
        return __doapl(this, r);
    }

private:
    // 辅助函数，用于执行加法逻辑
    inline static complex& __doapl(complex* ths, const complex& r) {
        ths->re += r.re; // 实部相加
        ths->im += r.im; // 虚部相加
        return *ths;     // 返回更新后的对象
        //operator+= 被调用时，this 指针指向 c2，而 c1 被作为第二个参数 (const complex& r) 传入
    }
};

// 测试代码
int main() {
    complex c1(2, 1); // 定义 c1，实部为 2，虚部为 1
    complex c2(5, 3); // 定义 c2，实部为 5，虚部为 3

    c2 += c1; // 执行 c2 = c2 + c1
    cout << "c2 = (" << c2.re << ", " << c2.im << ")" << endl;

    return 0;
}
```

**解释**

1. **构造函数**：
   - `complex(double real = 0, double imag = 0)` 用于初始化实部和虚部，提供默认值 0。
2. **`operator+=`**：
   - 重载 `+=` 运算符，调用 `__doapl` 辅助函数。
   - 返回值为当前对象的引用，支持链式操作。
3. **`__doapl`**：
   - 执行实部和虚部的加法操作，将结果更新到当前对象中。
   - 通过返回 `*ths`，将更新后的对象引用返回。
4. **测试部分**：
   - 创建了两个 `complex` 对象 `c1` 和 `c2`。
   - 使用 `c2 += c1;` 将 `c1` 加到 `c2` 上。
   - 打印结果验证 `c2` 的值更新为 `(7, 4)`，即实部 `2+5=7`，虚部 `1+3=4`。

**关键点**

- **链式操作支持**： `operator+=` 返回 `*this`，使得类似 `c2 += c1 += c3;` 的操作成为可能。
- **逻辑分离**： `__doapl` 封装了加法逻辑，简化了 `operator+=` 的实现。这样，如果以后需要修改加法逻辑，只需调整 `__doapl`，而无需改变 `operator+=` 的定义。
- **内联函数**： 使用 `inline` 提高了性能，减少了函数调用的开销。

在 C++ 类中，`this` 是一个隐式指针，指向调用成员函数的当前对象。以下是关于 `this` 指针的详细解释：

------

### **2. `this` 的定义与作用**

- **指向当前对象：**
  `this` 是类的每个成员函数（包括构造函数和析构函数）自动包含的一个指针，指向调用该函数的对象。
- **作用域：**
  只能在非静态成员函数中使用。静态成员函数没有 `this` 指针，因为它们与具体对象无关。

### 3.引用

传递者无需知道接收者是以引用形式接收的

### 4.非成员函数(无this)

**非成员函数的特点**

1. **没有 `this` 指针**：
   - 非成员函数不能直接访问类的私有成员变量。
   - 需要通过类的公共接口（如 getter 函数）访问数据。
2. **必须声明为友元函数（`friend`）**：
   - 如果非成员函数需要访问类的私有或保护成员，必须在类中声明为友元。
3. **灵活性**：
   - 非成员函数可以支持对左操作数为非类对象（如 `double + complex`）的运算符重载。
   - 更加通用，不局限于特定对象。

重载加号运算符 (`operator+`) 的三种不同实现，分别支持以下操作：

1. 复数 + 复数
2. 复数 + 实数
3. 实数 + 复数

```c++
#include <iostream>
using namespace std;

class complex {
private:
    double re, im; // 实部和虚部

public:
    // 构造函数
    complex(double real = 0, double imag = 0) : re(real), im(imag) {}

    // 获取实部和虚部
    double real() const { return re; }
    double imag() const { return im; }

    // 输出复数
    void print() const {
        cout << "(" << re << ", " << im << ")" << endl;
    }

    // 重载运算符+
    // 1. 复数 + 复数
    friend inline complex operator+(const complex& x, const complex& y) {
        return complex(x.real() + y.real(), x.imag() + y.imag());
    }

    // 2. 复数 + 实数
    friend inline complex operator+(const complex& x, double y) {
        return complex(x.real() + y, x.imag());
    }

    // 3. 实数 + 复数
    friend inline complex operator+(double x, const complex& y) {
        return complex(x + y.real(), y.imag());
    }
};

// 测试代码
int main() {
    complex c1(2, 1); // c1 的实部为 2，虚部为 1
    complex c2(5, 3); // c2 的实部为 5，虚部为 3
    complex c3;

    // 测试复数 + 复数
    c3 = c1 + c2;
    cout << "c1 + c2 = ";
    c3.print(); // 输出 (7, 4)

    // 测试复数 + 实数
    c3 = c1 + 5;
    cout << "c1 + 5 = ";
    c3.print(); // 输出 (7, 1)

    // 测试实数 + 复数
    c3 = 7 + c1;
    cout << "7 + c1 = ";
    c3.print(); // 输出 (9, 1)

    return 0;
}
```

**总结**

1. **复数加法（`complex + complex`）：**
   - 使用两个复数的实部和虚部分别相加，返回一个新的复数。
2. **复数与实数相加（`complex + double`）：**
   - 将实数加到复数的实部，虚部保持不变。
3. **实数与复数相加（`double + complex`）：**
   - 将实数加到复数的实部，虚部保持不变。
4. **灵活性：**
   - 运算符重载支持不同类型间的加法操作（如复数与实数）。
   - 使用 `friend` 让全局函数访问类的私有成员，提高效率。
5. **使用友元函数：**
   - 友元函数使得 `operator+` 能访问 `complex` 类的私有成员（`re` 和 `im`），实现代码的封装与简化。
6. **链式操作支持：**
   - 通过返回新的 `complex` 对象，支持链式操作（如 `(c1 + c2) + c3`）。

### 5.临时对象

**总结**

1. **临时对象**：
   - 每次调用 `operator+` 运算符函数时，都会创建一个新的临时对象作为返回值。
   - 临时对象在当前表达式结束时会被销毁。
2. **不能返回引用**：
   - 函数返回值是局部对象时，不能返回其引用，因为局部对象在函数结束时会被销毁，导致悬垂引用（dangling reference）。
   - 返回局部对象的值（即返回拷贝）是正确的做法。
3. **构造对象用法**：
   - 示例中展示了复数的不同构造方式，如默认构造函数、带参数的构造函数，以及通过直接传递值创建临时对象。
4. **运算符重载的三种形式**：
   - **复数 + 复数**：两个复数的对应实部和虚部相加。
   - **复数 + 实数**：将实数加到复数的实部，虚部保持不变。
   - **实数 + 复数**：将实数加到复数的实部，虚部保持不变。

```c++
#include <iostream>
using namespace std;

class complex {
private:
    double re, im; // 实部和虚部

public:
    // 构造函数
    complex(double real = 0, double imag = 0) : re(real), im(imag) {}

    // 获取实部和虚部
    double real() const { return re; }
    double imag() const { return im; }

    // 输出复数
    void print() const {
        cout << "(" << re << ", " << im << ")" << endl;
    }

    // 重载运算符+
    // 1. 复数 + 复数
    friend inline complex operator+(const complex& x, const complex& y) {
        return complex(x.real() + y.real(), x.imag() + y.imag());
    }

    // 2. 复数 + 实数
    friend inline complex operator+(const complex& x, double y) {
        return complex(x.real() + y, x.imag());
    }

    // 3. 实数 + 复数
    friend inline complex operator+(double x, const complex& y) {
        return complex(x + y.real(), y.imag());
    }

    // 输出重载（便于打印）
    friend ostream& operator<<(ostream& os, const complex& c) {
        os << "(" << c.re << ", " << c.im << ")";
        return os;
    }
};

// 测试代码
int main() {
    complex c1(2, 1);       // 定义复数 c1，实部为 2，虚部为 1
    complex c2;             // 默认构造函数
    complex c3 = c1 + c2;   // 复数 + 复数
    cout << "c1 + c2 = " << c3 << endl;

    c3 = c1 + 5;            // 复数 + 实数
    cout << "c1 + 5 = " << c3 << endl;

    c3 = 7 + c1;            // 实数 + 复数
    cout << "7 + c1 = " << c3 << endl;

    complex c4(4, 5);       // 定义复数 c4，实部为 4，虚部为 5
    cout << "c4 = " << c4 << endl;

    cout << complex(2) << endl; // 创建临时复数对象并打印
    return 0;
}
```

**重点解释**

1. **临时对象创建**：
   - `complex(2)` 创建了一个临时复数对象，实部为 `2`，虚部默认初始化为 `0`。
2. **返回值设计**：
   - `operator+` 返回一个临时对象而不是引用，确保在表达式结束后，临时对象自动销毁，避免内存问题。
3. **灵活性**：
   - 重载了不同版本的 `operator+`，支持复数与实数之间的混合运算。
4. **代码可扩展性**：
   - 重载了 `operator<<`，简化了复数的打印操作，增强代码的友好性。

### 6.操作符重载

```c++
#include <iostream>
using namespace std;

// 定义 complex 类
class complex {
private:
    double re, im; // 实部和虚部

public:
    // 构造函数
    complex(double real = 0, double imag = 0) : re(real), im(imag) {}

    // 获取实部和虚部
    double real() const { return re; }
    double imag() const { return im; }

    // 共轭复数函数
    friend inline complex conj(const complex& x) {
        return complex(x.real(), -x.imag()); // 实部不变，虚部取反
    }

    // 重载输出运算符
    friend ostream& operator<<(ostream& os, const complex& x) {
        return os << '(' << x.real() << ',' << x.imag() << ')';
    }
};

// 测试代码
int main() {
    complex c1(2, 1);       // 定义复数 c1，实部为 2，虚部为 1

    // 输出共轭复数
    cout << conj(c1) << endl;         // 输出 (2,-1)

    // 输出原始复数和其共轭复数
    cout << c1 << conj(c1) << endl;   // 输出 (2,1)(2,-1)

    return 0;
}
```

**目的**

重载 `operator<<` 的目的是让自定义的类支持直接使用 `cout` 等输出流来打印对象的信息。对于复数类，通过重载 `operator<<`，可以以格式化的形式输出复数的实部和虚部，比如 `(real, imag)`。

------

**实现方式**

**1. 函数签名**

```c++
ostream& operator<<(ostream& os, const complex& x);
```

- 返回类型：

  ostream&

  - 返回输出流对象的引用，保证可以进行链式操作（如 `cout << obj1 << obj2;`）。

- 参数：

  - `ostream& os`：标准输出流对象（如 `cout`）。
  - `const complex& x`：要输出的复数对象，使用 `const` 避免修改。

**2. 使用 `friend` 声明**

`operator<<` 是一个非成员函数，因此无法直接访问类的私有或保护成员变量（如 `re` 和 `im`）。为了解决这一问题，需要将其声明为类的友元函数。

在类中添加：

```c++
friend ostream& operator<<(ostream& os, const complex& x);
```

**3. 格式化输出**

在实现中，使用 `ostream` 的重载运算符 `<<` 格式化输出复数对象的实部和虚部，具体格式为 `(real, imag)`。

## 4.复数类的设计思路

```c++
#include <iostream>
using namespace std;
#ifndef __COMPLEX__
#define __COMPLEX__
class complex
{
private:
	double re, im;
	friend complex& __doapl(complex*, const complex&);
public:
	complex(double r = 0, double i = 0) :re(r), im(i) {}
	complex& operator += (const complex&);
	double real()const { return re; }
	double imag()const { return im; }
};
inline complex& __doapl(complex* ths, const complex& r)
{
	ths->re += r.re;
	ths->im += r.im;
	return *ths;
}
inline complex& complex::operator += (const complex& r)
{
	return __doapl(this, r);
}
inline complex operator+(const complex & x, const complex & y)
{
	return complex(x.real() + y.real(), x.imag() + y.imag());
}
inline complex operator+(const complex& x, double y)
{
	return complex(x.real() + y, x.imag());
}
inline complex operator+(double x, const complex& y)
{
	return complex(x + y.real(),y.imag());
}
inline ostream& operator << (ostream& os, const complex& x)
{
	return os << x.real() << x.imag();
}
#endif // !__COMPLEX__
```

## 5.String类

```c++
#include <iostream>
#include <cstring>
using namespace std;
#ifndef __STRING__
#define __STRING__
class String
{
public:
	String(const char* str = 0);//构造函数
	String(const String& str);//拷贝构造
	String& operator=(const String& str);//拷贝赋值
	~String();
	char* get_c_str()const { return m_data; }
private:
	char* m_data;
};
inline String::String(const char* str)
{
	if (str)
	{
		m_data = new char[strlen(str) + 1];
		strcpy(m_data, str);
	}
	else
	{
		m_data = new char[1];
		*m_data = '\0';
	}
}
inline String::~String()
{
	delete[] m_data;
}
inline String::String(const String& str)
{
	m_data = new char[strlen(str.m_data) + 1];
	strcpy(m_data, str.m_data);
}
inline String& String::operator=(const String& str)
{
	if (this == &str)
	{
		return *this;
	}//检测是否为自我赋值
	delete[] m_data;
	m_data = new char[strlen(str.m_data)];
	strcpy(m_data, str.m_data);
	return *this;
}
#endif // !__STRING__
int main()
{
	//String s1();
	String s2("hello");
	String s1(s2);
	s2 = s1;
	//String* p = new String("hello");
	//delete p;
}
```

注意：在拷贝赋值中，我们要进行自我检测

**问题描述：拷贝赋值操作中的自赋值问题**

1. **自赋值情况**：
   - 当对象`a`执行`a = a`时，`this`和`rhs`（右值对象）指向同一个内存块。
   - 此时，`operator=` 的实现若不处理自赋值的特殊情况，会导致未定义行为。
2. **常见实现中的问题**：
   - 在`operator=` 函数中，通常会先执行`delete`释放当前对象的内存。
   - 如果`this`和`rhs`指向同一个内存块，则释放内存后，`rhs`的数据也被释放了。
   - 接下来尝试从`rhs`读取数据时，会导致未定义行为（Undefined Behavior）。

所以必须进行自我检测

## 6.堆，栈和内存管理

### 1.output函数

```C++
ostream& operator<<(ostream& os, const String& str)
{
	os << str.get_c_str();
	return os;
}
```

### 2.栈和堆

**栈 (Stack)** 是存在于某作用域 (scope) 的一块内存空间 (memory space)。例如，当你调用函数，函数本身会形成一个栈，用来存放它接收的参数以及返回地址。

在函数体 (function body) 内声明的任何变量，其所使用的内存块都来自上述的栈。

**堆 (Heap)**，也称为系统堆 (system heap)，是指由操作系统提供的一块全局内存空间 (global memory space)，程序可以动态分配 (dynamically allocated) 从中获取若干块 (blocks)。

### 3.栈对象的生命期

eg:

```c++
class Complex{...};
...
{
    Complex c1(1,2);
}
```

c1便是所谓的栈对象，其生命周期在作用域 (scope) 结束时终结。这种作用域内的对象，又称为自动对象 (auto object)，因为它会被“自动”清理。

### 4.静态对象的生命期

eg:

```c++
class Complex{...};
...
{
    static Complex c2(1,2);
}
```

c2便是所谓的静态对象，其生命在作用域结束之后仍然存在，直到程序结束

### 5.全局对象的生命期

eg:

```c++
class Complex{...};
...
Complex c3(1,2);
int main
{
    ...
}
```

c3便是所谓的全局变量，其生命期在程序结束之后才结束。

### 6.堆对象的生命期

eg1:

```c++
class Complex { ... };
...

{
    Complex* p = new Complex;
    ...
    delete p;
}
```

**p** 所指的便是堆对象 (heap object)，其生命周期在它被 `delete` 之后结束。

eg2:

```c++
class Complex { ... };
...

{
    Complex* p = new Complex;
}
```

以上出现内存泄漏 (memory leak)，因为当作用域结束时，**p** 所指的堆对象 (heap object) 仍然存在，但指针 **p** 的生命周期结束了，作用域之外再也看不到 **p**（也就没有机会调用 `delete p`）.

### 7.new

new:先分配memory，在再调用构造函数

eg:

```c++
Complex* pc = new Complex(1,2);
```

`new` 运算符的底层工作可以分为三个步骤：

1. **调用 `operator new` 分配内存**：

   ```c++
   void* mem = operator new(sizeof(Complex));
   ```

   - `operator new` 是一个内置函数，用于动态分配指定大小的内存（与 `malloc` 类似）。
   - `sizeof(Complex)` 表示为类 `Complex` 分配足够大小的内存。

2. **类型转换，将分配的内存转换为对象指针**：

   ```c++
   pc = static_cast<Complex*>(mem);
   ```

   - 使用 `static_cast` 将 `void*` 指针转换为 `Complex*`，从而为接下来的操作提供正确的类型。

3. **调用构造函数初始化对象**：

   ```c++
   pc->Complex::Complex(1, 2);
   ```

   - 在分配的内存上显式调用类的构造函数，完成对象的初始化。
   - 也就是`Complex::Complex(pc,1,2);`

### 8.delete

delete:先调用dtor，再释放memory

eg:

```c++
Complex* pc = new Complex(1,2);
...
delete pc;
```

编译器转化为：

```c++
Complex::~Complex(pc);
operator delete(pc);//其内部调用free(ps)
```

### 9.动态分配所得的内存块

**Complex Object**

| 字段           | 值                 | 描述                         |
| -------------- | ------------------ | ---------------------------- |
| Header         | `00000011`         | 内存块的头部                 |
| Complex Object | `8h`               | 对象占用的实际大小           |
| Padding (0xfd) | 4 bytes            | 填充字节                     |
| Padding (pad)  | 4 bytes            | 填充字节                     |
| **总计**       | `8 + (4 * 2) = 16` | 计算出的对齐后的总内存块大小 |

------

**String Object**

| 字段          | 值                 | 描述                         |
| ------------- | ------------------ | ---------------------------- |
| Header        | `00000011`         | 内存块的头部                 |
| String Object | `4h`               | 对象占用的实际大小           |
| Padding (pad) | 4 bytes            | 填充字节                     |
| **总计**      | `4 + (4 * 2) = 16` | 计算出的对齐后的总内存块大小 |

------

**复杂内存块**

| 字段           | 值                                    | 描述                   |
| -------------- | ------------------------------------- | ---------------------- |
| Complex Object | `8h`                                  | Complex 对象占用的大小 |
| Padding (0xfd) | 32 bytes                              | 填充字节               |
| Padding (pad)  | 4 bytes                               | 填充字节               |
| String Object  | `4h`                                  | String 对象占用的大小  |
| **总计**       | `8 + (32 + 4) + (4 * 2) = 52` -> `64` | 对齐后的总内存块大小   |

### 10.动态分配所得的数组 (Array)

**Complex 数组 `Complex* p = new Complex[3];`**

| 字段                  | 值                                            | 描述                                   |
| --------------------- | --------------------------------------------- | -------------------------------------- |
| Header                | `51h`                                         | 调试器头部 (Debugger Header, 32 bytes) |
| 数组长度 (Array Size) | 3                                             | 表示分配的数组长度                     |
| 数据部分 (Data)       | 每个 Complex 占用 `8 bytes`，共 `3` 个        |                                        |
| Padding               | `4 * 2 bytes`                                 | 对齐填充                               |
| **总计**              | `(8 * 3) + (4 * 2) + 4 = 36 -> 向上对齐为 48` |                                        |
| **最终总计**          | `8 * 3 + 32 + 4 + (4 * 2) = 80`               |                                        |

------

**String 数组 `String* p = new String[3];`**

| 字段                  | 值                                            | 描述                                   |
| --------------------- | --------------------------------------------- | -------------------------------------- |
| Header                | `41h`                                         | 调试器头部 (Debugger Header, 32 bytes) |
| 数组长度 (Array Size) | 3                                             | 表示分配的数组长度                     |
| 数据部分 (Data)       | 每个 String 占用 `4 bytes`，共 `3` 个         |                                        |
| Padding               | `4 * 2 bytes`                                 | 对齐填充                               |
| **总计**              | `(4 * 3) + (4 * 2) + 4 = 24 -> 向上对齐为 32` |                                        |
| **最终总计**          | `4 * 3 + 32 + 4 + (4 * 2) = 64`               |                                        |

## 7.扩充内容

### 1.static

在数据和函数前面加上static后，就变成了静态。

**1. C++中的成员类型**

**静态数据成员**

- 在所有类对象之间共享。
- 存储在类级别（不属于具体的对象）。
- 可以通过 `ClassName::staticMemberName` 或 `objectName.staticMemberName` 访问。

**非静态数据成员**

- 每个对象都有独立的副本。
- 存储在对象的内存空间中。

**静态成员函数**

- 不直接操作类的实例对象（没有 `this` 指针）。
- 只能访问静态数据成员或其他静态成员函数。
- 使用 `ClassName::functionName` 调用。

**非静态成员函数**

- 操作特定的类实例（通过 `this` 指针）。
- 可以访问静态和非静态成员。

------

**2. 对象行为**

- 对象（如 `c1`、`c2`、`c3`）各自拥有独立的**非静态数据成员**，它们存储在不同的内存空间。
- 静态数据成员是共享的，仅存储在一个固定的内存位置。

------

**3. 成员访问方式**

**非静态成员函数**

- 隐式使用 this指针访问非静态成员。
  - 例如：`return this->re;` 访问当前对象的 `re` 成员。

**静态成员函数**

- 使用 ClassName::functionName调用。
  - 例如：`complex::real(&c1);`。

**4.关于 `this` 指针的关键点**

- 只有在**非静态成员函数**中才可用。
- 指向调用该函数的对象，便于访问其非静态成员。

 **使用static函数的方式有：**

1.通过对象调用：a.set_rate(7.0)

2.通过加上类名的函数调用:Acount::set_rate(5.0)

### 2.把构造函数放在private区内

```c++
class A {
public:
    static A& getInstance();
    void setup() { ... }
private:
    A();
    A(const A& rhs);
    ...
};

A& A::getInstance() {
    static A a;
    return a;
}

// 使用方式
A::getInstance().setup();
```

这段代码实现了 **Meyers Singleton** 模式，这是 C++ 中一种优雅的单例模式实现。

1. **单例模式简介**

单例模式是一种设计模式，其目标是保证某个类在整个程序运行过程中只有一个实例存在，同时提供一个全局访问点来访问这个实例。

------

2. **代码解读**

- **`static A& getInstance()`**
  - 这是一个静态成员函数，返回类 `A` 的唯一实例的引用。
  - 它的作用是确保只有一个实例被创建，同时提供对该实例的访问。
- **`static A a;`**
  - 在 `getInstance()` 函数中，使用了静态局部变量 `a`。C++ 标准规定，静态局部变量只会在程序运行期间初始化一次，这保证了 `a` 是全局唯一的。
  - 静态局部变量的生命周期从程序开始到结束，因此可以确保 `a` 始终有效。
- **`A::getInstance().setup();`**
  - 调用方式，通过单例对象调用其方法（`setup()`）。
  - 不需要直接创建对象，而是通过 `getInstance()` 获取全局唯一实例。

------

3. **优点**

- 线程安全性
  - 从 C++11 开始，静态局部变量的初始化是线程安全的，这避免了传统单例实现中的锁机制。
- 延迟初始化
  - 实例仅在第一次调用 `getInstance()` 时创建，节约资源。

------

4. **限制**

- 构造函数和拷贝构造函数私有化
  - 构造函数 `A()` 和拷贝构造函数 `A(const A& rhs)` 被设为 `private`，以防止外部直接创建或拷贝 `A` 的实例。

------

5. **适用场景**

Meyers Singleton 模式适用于需要全局唯一对象且延迟初始化的场景，例如：

- 配置管理器
- 日志管理器
- 数据库连接池

### 3.cout

```c++
class ostream : virtual public ios
{
public:
    ostream& operator<<(char c);
    ostream& operator<<(unsigned char c) { return (*this) << (char)c; }
    ostream& operator<<(signed char c) { return (*this) << (char)c; }
    ostream& operator<<(const char *s);
    ostream& operator<<(const unsigned char *s) 
    { 
        return (*this) << (const char*)s; 
    }
    ostream& operator<<(const signed char *s) 
    { 
        return (*this) << (const char*)s; 
    }
    ostream& operator<<(const void *p);
    ostream& operator<<(int n);
    ostream& operator<<(unsigned int n);
    ostream& operator<<(long n);
    ostream& operator<<(unsigned long n);
    ...
};

class _IO_ostream_withassign : public ostream 
{
    ...
};

extern _IO_ostream_withassign cout;
```

这段代码展示了 C++ 标准库中 `ostream` 类的部分实现细节，以及 `<<` 运算符的重载。它主要用于输出流操作，例如通过 `std::cout` 打印各种类型的数据。

------

1. **`ostream` 类**

`ostream` 是 C++ 标准库中的一个输出流类，用于格式化输出。它继承自 `ios`（输入输出流的基类），是标准输出流的核心部分。

------

2. **运算符重载 `operator<<`**

`ostream` 类通过重载 `<<` 运算符支持输出各种数据类型。

- **`ostream& operator<<(char c);`**
  - 用于输出单个字符。
- **`ostream& operator<<(unsigned char c)` 和 `ostream& operator<<(signed char c)`**
  - 用于输出无符号和有符号字符。
  - 它们通过强制类型转换为 `char`，然后调用 `ostream& operator<<(char c)` 方法完成输出。
- **`ostream& operator<<(const char \*s);`**
  - 用于输出 C 风格的字符串（以 `'\0'` 结尾的字符数组）。
- **`ostream& operator<<(const unsigned char \*s)` 和 `ostream& operator<<(const signed char \*s)`**
  - 用于输出指向无符号或有符号字符的字符串指针。
  - 它们将字符串指针转换为 `const char*`，然后调用 `ostream& operator<<(const char *s)`。
- **`ostream& operator<<(const void \*p);`**
  - 用于输出指针类型。通常将指针的值打印为地址（十六进制格式）。
- **`ostream& operator<<(int n);`、`ostream& operator<<(unsigned int n);`**
  - 用于输出整型数据。
  - 类似的，还有对 `long` 和 `unsigned long` 类型的支持。

------

3. **`_IO_ostream_withassign` 类**

- `_IO_ostream_withassign` 是 `ostream` 的派生类，可能在内部用于管理与 `ostream` 相关的特定实现。

------

4. **`cout`**

- `cout` 是一个全局对象，通常用于标准输出流。
- 通过 `extern _IO_ostream_withassign cout;` 声明，可以直接使用 `std::cout` 对象。

### 4.class template 类模板

```c++
template<typename T>
class complex
{
public:
    complex(T r = 0, T i = 0)
        : re(r), im(i)
    { }

    complex& operator += (const complex&);
    
    T real() const { return re; }
    T imag() const { return im; }

private:
    T re, im;

    friend complex& __doapl (complex*, const complex&);
};

// 使用示例
complex<double> c1(2.5, 1.5);
complex<int> c2(2, 6);
```

这段代码展示了一个模板类 `complex` 的实现，它可以表示并操作任意类型的复数（如 `int`、`float`、`double`）。

------

1. **模板类概念**

模板类允许开发者定义一个通用的类，而无需为每种数据类型（如 `int` 或 `double`）重复编写代码。

```cpp
template<typename T>
```

- `T` 是模板参数，在实例化类时用具体的类型替换（例如 `int`、`double`）。
- 该模板类 `complex` 的所有成员函数和数据成员都基于模板参数类型 `T`。

------

2. **构造函数**

```cpp
complex(T r = 0, T i = 0)
    : re(r), im(i)
{ }
```

- 这是一个默认构造函数，使用成员初始化列表初始化复数的实部 `re` 和虚部 `im`。
- 默认参数 `T r = 0` 和 `T i = 0` 表示如果用户没有提供值，实部和虚部默认为 `0`。

------

3. **成员函数**

- **`real()` 和 `imag()`**

  ```cpp
  T real() const { return re; }
  T imag() const { return im; }
  ```

  - `real()` 返回复数的实部，`imag()` 返回虚部。
  - 它们被声明为 `const`，表示不会修改类的数据成员。

- **`operator +=`**

  ```cpp
  complex& operator += (const complex&);
  ```

  - 这是 `+=` 运算符的重载，允许对复数进行加法操作。

  - 例如：

    ```cpp
    complex<double> a(1.0, 2.0), b(0.5, 0.5);
    a += b; // 实部和虚部分别相加
    ```

------

4. **私有数据成员**

```cpp
T re, im;
```

- `re` 和 `im` 分别存储复数的实部和虚部。
- 类型 `T` 由模板参数决定。

------

5. **友元函数**

```cpp
friend complex& __doapl(complex*, const complex&);
```

- 友元函数 `__doapl` 声明为 `complex` 的友元，允许它直接访问 `complex` 的私有成员。
- 该函数的具体实现未展示，但它通常用于实现与 `+=` 运算符相关的逻辑。

------

6. **使用示例**

```cpp
complex<double> c1(2.5, 1.5);
complex<int> c2(2, 6);
```

- `complex<double>`：实例化一个以 double为类型参数的复数类。
  - 实部为 `2.5`，虚部为 `1.5`。
- `complex<int>`：实例化一个以 int为类型参数的复数类。
  - 实部为 `2`，虚部为 `6`。

### 5.函数模板

**模板函数**

```cpp
template <class T>
inline
const T& min(const T& a, const T& b)
{
    return b < a ? b : a;
}
```

**类 `stone`**

```cpp
class stone
{
public:
    stone(int w, int h, int we)
        : _w(w), _h(h), _weight(we)
    {
    }

    bool operator<(const stone& rhs) const
    {
        return _weight < rhs._weight;
    }

private:
    int _w, _h, _weight;
};
```

**使用代码**

```cpp
stone r1(2, 3, 10), r2(3, 3, 8), r3;
r3 = min(r1, r2);
```

1. **模板函数 `min`**

```cpp
template <class T>
inline
const T& min(const T& a, const T& b)
{
    return b < a ? b : a;
}
```

- 这是一个模板函数，支持比较任意类型 `T` 的两个对象 `a` 和 `b`，返回较小的一个。
- 模板参数：
  - `T` 是模板参数，它的具体类型会在调用时由编译器通过 **类型推导 (argument deduction)** 决定。
- 函数逻辑：
  - 使用 `b < a` 进行比较，若 `b` 小于 `a`，则返回 `b`；否则返回 `a`。
  - 返回的是对象的引用，以避免拷贝对象，提高效率。

------

2. **类 `stone`**

- `stone` 类表示一个石头对象，具有宽度、高度和重量三个属性。

**构造函数**

```cpp
stone(int w, int h, int we)
    : _w(w), _h(h), _weight(we)
{
}
```

- 构造函数初始化了石头的宽度 `_w`、高度 `_h` 和重量 `_weight`。
- 使用 **初始化列表** 提高性能。

**运算符 `<` 的重载**

```cpp
bool operator<(const stone& rhs) const
{
    return _weight < rhs._weight;
}
```

- 重载了小于运算符 `<`，用于比较两个 `stone` 对象。
- 比较的依据是重量 `_weight`。
- `const` 修饰符表示该函数不会修改类的成员变量。

------

3. **使用 `min` 函数**

```cpp
stone r1(2, 3, 10), r2(3, 3, 8), r3;
r3 = min(r1, r2);
```

- **对象初始化**
  - `r1` 的宽度、高度和重量分别是 `(2, 3, 10)`。
  - `r2` 的宽度、高度和重量分别是 `(3, 3, 8)`。
- **调用模板函数 `min`**
  - 函数 `min` 的模板参数 `T` 由编译器自动推导为 `stone` 类型。
  - 比较 r1和 r2的逻辑：
    - `r2._weight` = 8，`r1._weight` = 10。
    - 调用 `stone::operator<`，发现 `r2` 小于 `r1`。
  - 返回较小的对象 `r2`。
  - `r3` 被赋值为 `r2`。

### 6.namespace

```c++
namespace std
{
    ...
}
```

1. **命名空间简介**

C++ 的标准库中大多数功能（如 `cin`、`cout` 等）都位于命名空间 `std` 中。为了避免名字冲突，C++ 使用命名空间来组织代码。

常见的命名空间使用方式包括：

1. `using namespace` 指令（`using directive`）。
2. `using` 声明（`using declaration`）。
3. 完全限定名（直接使用 `std::` 前缀）。

------

2. **方式一：Using Directive（使用指令）**

```cpp
#include <iostream>
using namespace std;

int main()
{
    cin >> ...;
    cout << ...;
    return 0;
}
```

特点：

1. `using namespace std;` 使得命名空间 `std` 中的所有标识符（如 `cin`、`cout` 等）在当前作用域可直接使用，无需加 `std::` 前缀。
2. 优点：
   - 简洁，适合小型程序或快速实现代码。
3. 缺点：
   - **潜在风险**：如果多个命名空间中有同名的标识符（如 `std::count` 和另一个库中的 `count`），可能导致名称冲突。
   - 在大型工程中，`using namespace std;` 可能引入不必要的标识符，增加命名冲突的风险。

建议：

不推荐在大型项目或头文件中使用 `using namespace std;`，以免引发命名冲突。

------

3. **方式二：Using Declaration（使用声明）**

```cpp
#include <iostream>
using std::cout;

int main()
{
    std::cin >> ...;
    cout << ...;
    return 0;
}
```

特点：

1. 只将命名空间 `std` 中的某个标识符（如 `cout`）引入当前作用域，而不是整个命名空间。
2. 优点：
   - 只引入需要的标识符，避免了命名冲突的风险。
   - 在较复杂的代码中，可以清楚地看到哪些标识符来自 `std`。
3. 缺点：
   - 对于需要频繁使用的标识符（如 `cin`、`cout` 等），可能稍显繁琐。

建议：

这种方式适合中大型项目中，明确只需要使用某些特定标识符时。

------

4. **方式三：完全限定名**

```cpp
#include <iostream>

int main()
{
    std::cin >> ...;
    std::cout << ...;
    return 0;
}
```

特点：

1. 每次使用标识符时都要加上 `std::` 前缀。
2. 优点：
   - 完全避免了命名冲突。
   - 更具可读性，明确标识符的来源。
3. 缺点：
   - 如果标识符使用频繁，代码会变得冗长。

建议：

适合大型项目和团队开发时，明确标识符来源是 `std`，提高代码的可维护性和可读性。

------

**总结：选择合适的方式**

| 方式                  | 使用场景                           | 优点                       | 缺点                               |
| --------------------- | ---------------------------------- | -------------------------- | ---------------------------------- |
| **Using Directive**   | 小型项目、快速测试代码             | 简洁方便，减少代码输入     | 易引发命名冲突，不适合复杂项目     |
| **Using Declaration** | 中型项目，使用部分 `std` 标识符    | 避免命名冲突，代码更安全   | 对于多个标识符需多次声明，稍显繁琐 |
| **完全限定名**        | 大型项目、团队开发，明确标识符来源 | 完全避免命名冲突，可读性高 | 使用频繁时代码较冗长               |
