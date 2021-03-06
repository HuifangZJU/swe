# 匿名Namespace

名字空间(namespace)，是C++提供的一个解决符合名字冲突的特性。标准规定，在不同名字空间中命名相同的符号，代表不同的实体。通常，利用定义名字空间的办法，可以使模块划分更加方便，减少模块间的相互影响。

通常定义一个名为MyNameSpace的名字空间，其形式为：
```cpp
namespace MyNameSpace
{
}
```

static修饰，在处理函数和变量（包括常量）的时候已经工作得很好了。但是static的缺陷是不能修饰class和struct这样的结构定义。因此，当出现这种情况： 在某个cpp实现里需要辅助的几个结构a,b,c来帮助实现，但是又不希望这些结构污染整个名字空间。

这时，如果使用匿名名字空间，就可以比较完美解决问题了。

匿名的namespace,即

```cpp
namespace {
/* code */
}
```

### 总结　

1. 匿名名字空间提供了类似在全局函数前加 static 修饰带来的限制作用域的功能。它的这种特性可以被用在struct和class上， 而普通的static却不能。

2. 未命名的名字空间中定义的名字只在包含该名字空间的文件中可见，但其中的变量的生存期却从程序开始到程序结束。如果有多个文件包含未命名的名字空间，这些名字空间是不相关的，即使这些名字空间中定义了相同的名字，这些名字也代表不同的对象。
