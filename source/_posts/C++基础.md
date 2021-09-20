---
title: C++基础知识总结
date: 2020-11-09
updated: 2021-05-01
tags: [C/C++]
group: todo
categories: 编程与开发
references:
  - title: C语言中文网
    url: http://c.biancheng.net/cplus/
---

> Object Oriented Programming，面向对象的编程的思想是一种对现实世界理解和抽象的方法，其有的封装、继承、多态性的特性，可以设计出低耦合的系统，使系统更灵活和易于维护，对软件开发相当重要。C++是一门面向对象的编程语言，本文包含对于C++语言中类、对象、运算符重载、继承、多态等面向对象的程序设计方法，以及模板、标准模板库STL等泛型程序设计的机制的描述，希望帮助读者能够更好的体会和领悟面向对象程序设计方法和泛型程序设计方法的优势。由于之前已经有了C语言的基础，所以我选择的C++语言程序设计课程是农大的国家精品课：[从C到C++](https://www.icourse163.org/course/CAU-432001)，附上我学慕课和阅读文档时的[练习代码](https://github.com/Bezhuang/LearnCS/tree/main/%E4%BB%8EC%E5%88%B0C%2B%2B)

<!--more-->

### 从C到C++

#### C++程序

- GCC 是所有编译器的总称，在C语言中使用`gcc`命令编译和链接C程序。`g++`命令用来编译 C++，`gcj`命令用来编译 Java，`gccgo`命令用来编译Go语言

- C++ 引入了命名空间（Namespace）的概念来解决合作开发时的命名冲突问题

  ```c++
  namespace name{
      //variables, functions, classes
  }
  ```

- `name`是命名空间的名字，它里面可以包含变量、函数、类、typedef、#define 等

- 使用变量、函数时要指明它们所在的命名空间，`::`是域解析操作符，用来指明要使用的命名空间

- 可以采用`using`关键字声明变量或整个命名空间，`using Li::fp;`，`using namespace Li;`

- C++头文件和`std`标准命名空间

  ```c++
  #include <iostream>
      /*
      如果希望在所有函数中都使用命名空间 std，可以将它声明在全局范围中
      using namespace std;
      */
  void func(){
      using namespace std;  //必须重新声明
      cout<<"Bezhuang"<<endl;
  }
  
  int main(){
      using namespace std; //声明命名空间std
      cout<<"C++学习者："<<endl;
      func();
      return 0;
  }
  ```

- 使用输入输出时需要包含头文件`iostream`，`cin>>`标准输入、`cout<<`标准输出、`cerr`标准错误，`endl`结束此行

- `new` 动态分配内存（对应`malloc()`），`delete` 释放内存（对应`free()`）

  ```c++
  int *p = new int[10];  //分配10个int型的内存空间
  delete[] p;
  ```

#### 内联函数

- 在函数调用处直接嵌入函数体的函数称为内联函数（Inline Function），类似于C语言中的宏展开，注意要在函数定义处添加 inline 关键字而不是在声明处（编译器会忽略）

  ```c++
  #include <iostream>
  using namespace std;
  
  inline void swap(int *a, int *b){    //内联函数，交换两个数的值
      int temp;
      temp = *a;
      *a = *b;
      *b = temp;
  }
  int main(){
      int m, n;
      cin>>m>>n;
      cout<<m<<", "<<n<<endl;
      swap(&m, &n);
      cout<<m<<", "<<n<<endl;
      return 0;
  ```

#### 重载和引用

- 通过使用默认参数，可以减少要定义的析构函数、方法以及方法重载的数量

- 实参和形参的传值是从左到右依次匹配的，默认参数只能放在形参列表的最后，一旦为某个形参指定了默认值，那么它后面的所有形参都必须有默认值

  ```C++
  void func(int a, float b=d+2.9, char c='@', int e){ }
  ```

- 函数的重载（Function Overloading）允许多个函数拥有相同的名字，只要它们的参数列表（参数的类型、参数的个数和参数的顺序）不同就可以，但仅返回类型不同不能作为重载的依据

- 同指针一样，引用能够减少数据的拷贝，提高数据的传递效率

- 引用可以看做是数据的一个别名，通过这个别名和原来的名字都能够找到这份数据
  ```C++
  type &name = data;    //类型名 &引用变量名 = 被引用变量名;
  ```

- 引用在定义时需要添加`&`，在使用时不能添加`&`，使用时添加`&`表示取地址

- 如果不希望通过引用来修改原始的数据，那么可以在定义时添加 `const` 限制

  ```C++
  const type &name = value;  //常引用
  ```

- C++引用可以作为函数参数也可以作为函数返回值

  ```c++
  #include <iostream>
  using namespace std;
  int &plus10(int &r) {
      r += 10;
      return r;
  }
  int main() {
      int num1 = 10;
      int num2 = plus10(num1);
      cout << num1 << " " << num2 << endl;
      return 0;
  }  //运行结果20 20
  ```

#### C++字符串

- `string` 是 C++ 中常用的一个类，使用 string 类需要包含头文件  `#include <string>`


- `string s1;`   `string s2 = "c plus plus";`   `string s3 = s2;`   `string s4 (5, 's');`

- `length()` 函数求长度，`c_str()` 函数转为C风格字符串

- `string` 类可以使用`+`或`+=`运算符来直接拼接字符串

- `insert()` 函数可以在 `string` 字符串中指定的位置插入另一个字符串
  
  ```c++
  string& insert (size_t pos, const string& str);
  //pos 表示要插入的位置，也就是下标；str 表示要插入的字符串
  s1.insert(pos, str);
  ```

- `erase(pos, len)` 函数可以删除 `string` 中的一个子字符串
- `substr(pos, len)` 函数用于从 `string` 字符串中提取子字符串
- `find(str, pos)` 函数用于在 `string` 字符串中查找子字符串出现的位置
- `rfind()` 和 `find()` 很类似，同样是在字符串中查找子字符串，不同的是 `find()` 函数从 `pos` 参数开始往后查找，而 `rfind()` 函数则最多查找到 `pos` 处
- `find_first_of(str)` 函数用于查找子字符串和字符串共同具有的字符在字符串中首次出现的位置

### 类与对象编程

#### 类的定义

- 类是创建对象的模板，通过类名创建对象的过程叫做类的实例化，对象是类的一个实例（Instance）

- 类的成员变量称为类的属性（Property），类的成员函数称为类的方法（Method）

- 类是一个通用的概念，C++、Java、C#、PHP 等很多编程语言都可以通过类创建对象

  ```c++
  class Student{    //类通常定义在函数外面
  public:
      //成员变量
      char *name;
      int age;
      float score;
      //成员函数
      void say(){cout<<name<<"年龄是"<<age<<"，成绩是"<<score<<endl;}
  };
  ```

- 类只是一个模板（Template），编译后不占用内存空间，所以在定义类时不能对成员变量进行初始化，只有在创建对象以后才会给成员变量分配内存，才可以赋值

  ```c++
  int main(){
      Student stu;  //创建对象
      stu.name = "小明"; stu.age = 15; stu.score = 92.5f;
      stu.say();
      return 0;
  }
  ```

- 使用 `class` 时，类中的成员默认都是 `private` 属性的，而使用 `struct` 时，结构体中的成员默认都是 `public` 属性的
- 使用 `class` 来定义类，使用 `struct` 来定义结构体，这样做语义更加明确

#### 成员变量和成员函数

- 类的成员有成员变量和成员函数两种，成员函数之间可以互相调用，成员函数内部可以访问成员变量

- 在栈上创建对象指针，形式和定义普通变量类似，不能使用 delete 删除在栈上创建的对象

  ```c++
  Student stu;  //对象stu 在栈上分配内存，需要使用&获取它的地址
  Student *pStu = &stu;  //pStu 是一个指针，它指向 Student 类型的数据
  ```

- 使用 new 在堆上创建出来的对象必须要用一个指针指向它来访问它的成员变量或成员函数

  ```c++
  Student *pStu = new Student;
  pStu -> name = "小明" ;pStu -> age = 15; pStu -> score = 92.5f;
  pStu -> say();
  delete pStu;  //删除对象
  return 0;
  ```

- 可以用 `对象名.成员名`、`引用名.成员名`、`对象指针->成员名` 的方法访问对象的成员变量或调用成员函数

- 每个对象所占用的内存空间都等于类中全部数据成员所需内存空间总和

- 当成员函数定义在类外时必须在函数名前面加上类名予以限定，域解析符（也称作用域运算符或作用域限定符）`::` 用来连接类名和函数名，指明当前函数属于哪个类

  ```c++
  class Student{
  public:
      //成员函数
      void say();  //成员函数必须先在类体中作原型声明，然后在类外定义
  };
  void Student::say(){
      cout<<name<<"的年龄是"<<age<<"，成绩是"<<score<<endl;
  ```

- 在类体外定义 inline 函数的方式，必须将类的定义和成员函数的定义都放在同一个头文件中（或者同一个源文件中），否则编译时无法进行嵌入，因此强烈建议将内联函数定义在类的内部

#### 类的封装

- 成员访问限定符`public`、`protected`、`private` 控制成员变量和成员函数的访问权限
- C++中的类没有共有私有之分，public、private、protected 只能修饰类的成员，不能修饰类
- 封装，是指尽量隐藏类的内部实现，只向用户提供有用的成员函数

  - 实际项目开发中的成员变量以及只在类内部使用的成员函数（只被成员函数调用的成员函数）都应声明为 private，只将允许通过对象调用的成员函数声明为 public
  - 给成员变量赋值的函数通常称为 set 函数，以`set`开头后跟成员变量名，读取成员变量的值的函数通常称为 get 函数，以`get`开头后跟成员变量名
- 包含成员对象的类叫封闭类。任何能够生成封闭类对象的语句，都要说明对象中包含的成员对象是如何初始化的，如果不说明则编译器认为成员对象是用默认构造函数或参数全部可以省略的构造函数初始化
- 在封闭类的构造函数的初始化列表中可以说明成员对象如何初始化。封闭类对象生成时，先执行成员对象的构造函数，再执行自身的构造函数；封闭类对象消亡时，先执行自身的析构函数，再执行成员对象的析构函数。

#### 构造函数和析构函数

- 构造函数（Constructor）名字和类名相同，没有返回值，不需要用户显式调用（用户也不能调用），而是在创建对象时自动执行  `类名(){}`

  ```c++
  //声明构造函数（Student类中）
  Student(char *name, int age, float score);
  //定义构造函数
  Student::Student(char *name, int age, float score){
      m_name = name; m_age = age; m_score = score;}
  //创建对象时向构造函数传参（主函数中）
  Student *pstu = new Student("李华", 16, 96);
  pstu -> show();
  ```

- 构造函数必须是 public 属性的，否则创建对象时无法调用

- 构造函数没有返回值因此不管是声明还是定义，函数名前面都不能出现返回值类型，函数体中不能有 return 语句

- 构造函数的调用是强制性的，一旦在类中定义了构造函数，那么创建对象时就一定要调用

- 创建对象时只有一个构造函数会被调用，如果有多个重载的构造函数，那么创建对象时提供的实参必须和其中的一个构造函数匹配

- 一个类必须有构造函数，要么用户自己定义，要么编译器自动生成默认构造函数 `类名(){}`

- 构造函数的初始化列表

  ```c++
  Student::Student(char *name, int age, float score): m_name(name){
      m_age = age;
      m_score = score;
  }  //只对 m_name 使用初始化列表，其他成员变量还是一一赋值
  ```

- 成员变量的初始化顺序与初始化列表中列出的变量的顺序无关，只与成员变量在类中声明的顺序有关

- 初始化 `const` 成员变量的唯一方法就是使用初始化列表

  ```c++
  class VLA{
  private:
      const int m_len;
      int *m_arr;
  public:
      VLA(int len);
  };
  //必须使用初始化列表来初始化 m_len
  VLA::VLA(int len): m_len(len){
      m_arr = new int[len];
  }
  ```

- 析构函数（Destructor）也是一种特殊的成员函数，没有返回值，不需要程序员显式调用，在销毁对象时自动执行  `~类名(){}`

- 构造函数和析构函数对于类来说是不可或缺的，`new` 分配内存时会调用构造函数，用 `delete` 释放内存时会调用析构函数

#### 静态成员和常成员

- `this` 指针也是一个 `const` 指针，它指向当前对象，用`->`来访问当前对象的所有成员变量或成员函数，它的值是不能被修改的

- `this` 只能用在类的内部，通过 this 可以访问类的所有成员，包括 `private`、`protected`、`public` 属性的

- `this` 只能在成员函数内部使用，只有当对象被创建后 `this` 才有意义，因此也不能在 `static` 成员函数中使用

- `this` 实际上是成员函数的一个形参，在调用成员函数时将对象的地址作为实参传递给 `this`

- 静态成员变量是一种特殊的成员变量，它被关键字`static`修饰

  ```c++
  static int m_total;  //静态成员变量
  ```

- `static` 成员变量不占用对象的内存，而是在所有对象之外开辟内存，即使不创建对象也可以访问

- 一个类中可以有一个或多个静态成员变量，所有的对象都共享这些静态成员变量，都可以引用它

- 每个对象有各自的一份普通成员变量，但是静态成员变量只有一份，被所有对象所共享。

- 静态成员变量必须初始化，而且只能在类体外进行：`int Student::m_total = 10;`

- `static` 静态成员函数不具体作用于某个对象。即便对象不存在，也可以访问类的静态成员。

- 静态成员函数内部不能访问非静态成员变量，也不能调用非静态成员函数。

- 和静态成员变量类似，静态成员函数在声明时要加 `static`，在定义时不能加 `static`。静态成员函数可以通过类来调用（一般都是这样做），也可以通过对象来调用

- 如果你不希望某些数据被修改，可以使用`const`关键字加以限定。`const` 可以用来修饰成员变量和常成员函数

- `const` 成员和引用成员必须在构造函数的初始化列表中初始化，此后值不可修改。

- 常成员函数需要在声明和定义的时候在函数头部的结尾加上 `const` 关键字

  ```c++
  //声明常成员函数
  char *getname() const;
  //定义常成员函数
  char * Student::getname() const{
      return m_name;
  ```

- 函数开头加 `const` 用来修饰函数的返回值，表示返回值是 `const` 类型，也就是不能被修改，例如`const char * getname()`

- 函数头部的结尾加上 `const` 表示常成员函数，这种函数只能读取成员变量的值，而不能修改成员变量的值，例如`char * getname() const`

- `const` 也可以用来修饰对象，称为常对象。一旦将对象定义为常对象之后，就只能调用类的 `const` 成员了

  ```c++
  //定义常对象的语法和定义常量的语法类似
  const class object(params); 
  class const object(params);
  //当然你也可以定义 const 指针
  const class *p = new class(params);  
  class const *p = new class(params);
  //class为类名，object为对象名，params为实参列表，p为指针名
  ```

#### 友元函数和友元类

- 借助友元（friend）可以使得其他类中的成员函数以及全局范围内的函数访问当前类的 `private` 成员
  ```c++
  friend void show(Student *pstu);  //将show()声明为友元函数
  ```
  
- 友元函数不同于类的成员函数，在友元函数中不能直接访问类的成员，必须要借助对象。

  ```c++
  void show(Student *pstu){cout<<pstu->m_name<<"的年龄是 "<<pstu->m_age<<endl;}
  ```
  
- 可以将非成员函数声明为友元函数，也可以将其他类的成员函数声明为友元函数

- 一个函数可以被多个类声明为友元函数，这样就可以访问多个类中的 private 成员

- 友元类中的所有成员函数都是另外一个类的友元函数  `friend class Student;`

- 友元的关系是单向的而不是双向的。如果声明了类 B 是类 A 的友元类，不等于类 A 是类 B 的友元类

- 友元的关系不能传递。如果类 B 是类 A 的友元类，类 C 是类 B 的友元类，不等于类 C 是类 A 的友元类

### 继承与派生

#### 三种继承方式

- 继承（Inheritance）/ 派生（Derive）是一个类从另一个类获取成员变量和成员函数的过程

- 被继承的类称为父类或基类，继承的类称为子类或派生类

  ```c++
  class 派生类名:［继承方式］ 基类名{
      派生类新增加的成员
  };
  ```

- 继承方式包括 `public`、`private`和 `protected`，此项是可选的，如果不写，那么默认为 `private`
- 类成员的访问权限由高到低依次为 `public` --> `protected` --> `private`





















### 重用类代码
- 用类定义对象
- 通过组合定义新的类（组合类）
- 多级访问
- 类的聚合（指针形式传递）
- 通过继承定义新的类（继承类）
- 基类，派生类（基类成员与新增成员）
- 同名覆盖
- 派生类对基类成员的二次封装
- `obj.Circle::input()`
- 保护权限与保护继承
- 继承与派生主要用于重用类代码和凝练类代码
- 多态性：相同程序元素不同的语法解释
- 运算符的多态与重载
- 对象的替换和多态
- Liskov 替换准则：将派生类对象当做基类对象使用
- 类族：基类和派生类
- 对象的多态性
- 虚函数（virtual关键字）
- 抽象类
- 多继承（从多个类中继承，JAVA和C#中没有）

### 流类库和文件读写
- 输入/输出流
- 流类库：以ios为基类的类族
- 数据缓冲区和流缓冲区
- 标准I/O（`<iostream>`，`cin`/`cout`）
- 文件I/O（`<fstream>`，`fin`/`fout`）
- string类和字符串I/O（`<string>`，`<sstream>`，`str`）
- 基于Unicode编码的流类库（以wios为基类）

### C++标准库
- 系统函数和系统类库
- 模板技术：函数模板和类模板
- 使用typedef类型定义显示地实例化类模板
- 标准模板库STL（Standard Template Library）
- 异常处理机制：throw语句 / try-catch机制 / `<exception>`
- 数据集合及处理算法（CRUD）
- 链表
- 迭代器（Iterator）
- 查找算法、增删改算法和排序相关算法
- 容器类：`<vector>`、`<list>`、`<set>`、`<map>`

### 第三方开发的函数/类库
- 微软基础类库 Microsoft Foundation Classes（MFC）