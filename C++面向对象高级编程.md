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
