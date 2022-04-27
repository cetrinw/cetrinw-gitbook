# size\_t

### 1. size\_t类型

`size_t` 类型定义在`cstddef`头文件中，该文件是C标准库的头文件`stddef.h`的C++版。它是一个与机器相关的unsigned类型，其大小足以保证存储内存中对象的大小。

### 2. size\_t由来

: 在C++中，设计 `size_t` 就是为了适应多个平台的 。`size_t`的引入增强了程序在不同平台上的可移植性，`size_t`是针对系统定制的一种数据类型，一般是整型

### 3. 实现方式

在C++中，设计`size_t`就是为了适应多个平台的。`size_t`的引入增强了程序在不同平台上的可移植性。`size_t`是针对系统定制的一种数据类型，一般是整型，因为C/C++标准只定义一最低的位数，而不是必需的固定位数。而且在内存里，对数的高位对齐存储还是低位对齐存储各系统都不一样。为了提高代码的可移植性，就有必要定义这样的数据类型。一般这种类型都会定义到它具体占几位内存等。当然，有些是编译器或系统已经给定义好的。经测试发现，在32位系统中size\_t是4字节的，而在64位系统中，size\_t是8字节的，这样利用该类型可以增强程序的可移植性。

`size_t`是标准C库中定义的，在64位系统中为`long long unsigned int`，非64位系统中为`long unsigned int`。

通常我们用`sizeof(XXX)`操作，这个操作所得到的结果就是`size_t`类型。

size\_t还经常出现在C++标准库中，此外，C++库中经常会使用一个相似的类型size\_type，用的可能比size\_t还要多。

`size_t`类型是一个类型定义，通常将一些无符号的整形定义为`size_t`，比如说`unsigned int`或者`unsigned long`，甚至`unsigned long long`。每一个标准C实现应该选择足够大的无符号整形来代表该平台上最大可能出现的对象大小。