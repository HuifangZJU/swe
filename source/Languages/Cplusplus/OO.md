# 面向对象三大特征

## 封装

## 继承

## 多态
### 多态概念

多态性可以简单地概括为“一个接口，多种方法”，程序在运行时才决定调用的函数。

**封装**可以使得代码模块化，**继承**可以扩展已存在的代码，他们的目的都是为了代码重用。而**多态**的目的则是为了接口重用。

### C++多态如何实现
1. 编译时的多态

    通过函数重载和运算符重载实现的

2. 运行时的多态

    通过虚函数和继承实现的

### 虚函数/虚函数表

1. 该部分参考博客
    * [c++虚函数、多态性与虚表](http://my.oschina.net/hnuweiwei/blog/280894?fromerr=eHnrIYPr)
2. C++的虚函数怎么实现的

    * 虚函数
        * 虚函数可以在一个或多个派生类中被重新定义，因此，属于函数重载的情况（函数模型相同的特殊的函数重载override，这个到底是重载还是重写，其实是有争议的）
    * 纯虚函数
      `virtual int fun()=0;`
    * 虚函数表
        * ①每一个具有虚函数的**类**都有一个虚函数表VTABLE，里面按在类中声明的虚函数的顺序存放着虚函数的地址，这个虚函数表VTABLE是这个类的所有对象所共有的，也就是说无论用户声明了多少个类对象，但是这个VTABLE虚函数表只有一个；②在每个具有虚函数的类的**对象**里面都有一个VPTR虚函数指针，这个指针指向VTABLE的首地址，每个类的对象都有这么一种指针。
        * 虚函数的类对象的大小是数据成员的大小加上一个VPTR指针(void *)的大小；没有虚函数类对象的大小正好是数据成员的大小。
        * [陈皓的博客](http://coolshell.cn/articles/12165.html)
        * [这篇博客也谈到了虚继承](http://blog.csdn.net/hackbuteer1/article/details/7883531)

3. 在没有虚函数的类中虚函数表指针是否存在？
不存在

4.  虚函数缺点
    * 虚函数最主要的缺点是执行效率较低（看一看虚拟函数引发的多态性的实现过程，你就能体会到其中的原因）
    * 由于要携带额外的信息（VPTR），导致类多占的内存空间也会比较大，对象也是一样的。

4. 构造函数是否可以为虚？
    不可以，因为在构造函数执行之前，对象尚未初始化，也就没有虚函数指针，无法查找虚函数表。故构造函数不可能是虚函数。
