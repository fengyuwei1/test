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
