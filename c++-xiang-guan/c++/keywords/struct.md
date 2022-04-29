# struct

## 1. 结构体(struct) <a href="#1-jie-gou-ti-struct" id="1-jie-gou-ti-struct"></a>

#### 1.1 结构体的概念 <a href="#t1" id="t1"></a>

* **结构体(struct)：**是由一系列具有相同类型或不同类型的数据构成的数据集合，叫做结构。
* **结构体(struct)：**是一种复合数据类型，结构类型。
* **注：“结构”是一种构造类型，它是由若干“成员”组成的。 每一个成员可以是一个基本数据类型或者又是一个构造类型。 结构即是一种“构造”而成的数据类型， 那么在说明和使用之前必须先定义它，也就是构造它。如同在说明和调用函数之前要先定义一样。**

#### 1.2 C语言中的结构体 <a href="#t2" id="t2"></a>

* **说明：**在C语言中，结构体(struct)是复合数据类型的一种。同时也是一些元素的集合，这些元素称为结构体的成员，且这些成员可以为不同的类型，成员一般用名字访问。结构体可以被声明为变量、指针或数组等，用以实现较复杂的数据结构。
* **注：在C语言中，结构体不能包含函数。**
* **定义与声明：**
  *   &#x20;(1)示例代码一

      ```
      1 struct tag 
      2 {
      3     member-list
      4 } variable-list;
      5 注：struct为结构体关键字；
      6    tag为结构体的标志；
      7    member-list为结构体成员变量列表，其必须列出其所有成员；
      8    variable-list为此结构体声明的变量
      ```


  *   (2)示例代码二

      ```
       1 //此声明声明了拥有3个成员的结构体，分别为整型的a，字符型的b和双精度的c，但没有标明其标签，声明了结构体变量s1
       2 struct 
       3 {
       4     int a;
       5     char b;
       6     double c;
       7 } s1;
       8 
       9 //此声明声明了拥有3个成员的结构体，分别为整型的a，字符型的b和双精度的c，结构体的标签被命名为SIMPLE，用SIMPLE标签的结构体，另外声明了变量t1, t2[20], *t3
      10 struct SIMPLE
      11 {
      12     int a;
      13     char b;
      14     double c;
      15 };
      16 SIMPLE t1, t2[20], *t3; 
      17 
      18 //可以用typedef创建新类型，此声明声明了拥有3个成员的结构体，分别为整型的a，字符型的b和双精度的c，结构体的标签被命名为Simple2，用Simple2作为类型声明新的结构体变量u1, u2[20], *u3
      19 typedef struct
      20 {
      21     int a;
      22     char b;
      23     double c; 
      24 } Simple2;
      25 Simple2 u1, u2[20], *u3;//若去掉typedef则编译报错，error C2371: “Simple2”: 重定义；不同的基类型
      26 
      27 注：在上面的声明中，第一个和第二声明被编译器当作两个完全不同的类型，即使他们的成员列表是一样的，如果令t3=&s1，则是非法的。
      ```

      [![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void\(0\);)

      **注：在一般情况下，tag、member-list、variable-list这3部分至少要出现2个。**

#### 1.3 C++中的结构体 <a href="#t3" id="t3"></a>

* **说明：**在C语言中，结构体不能包含函数。在面向对象的程序设计中，对象具有状态（属性）和行为，状态保存在成员变量中，行为通过成员方法（函数）来实现。C语言中的结构体只能描述一个对象的状态，不能描述一个对象的行为。在C++中，考虑到C语言到C++语言过渡的连续性，对结构体进行了扩展，C++的结构体可以包含函数，这样，C++的结构体也具有类的功能，与class不同的是，结构体包含的函数默认为public，而不是private。
* **注：在C++中，结构体可以包含函数。**
* **定义与声明：**
*   (1)示例代码一

    ```
    1 struct tag 
    2 {
    3     member-list
    4 }variable-list;
    5 注：struct为结构体关键字；
    6    tag为结构体的标志；
    7    member-list为结构体成员变量及成员函数列表，其必须列出其所有成员；
    8    variable-list为此结构体声明的变量
    ```

    (2)示例代码二

    ```
     1 #include <iostream> 
     2 
     3 using namespace std;
     4 
     5 struct SAMPLE
     6 {
     7     int x;
     8     int y;
     9     int add() {return x+y;}
    10 }s1;
    11 
    12 int main()
    13 {
    14     cout<<"没初始化成员变量的情况下："<<s1.add()<<endl;
    15     s1.x = 3;
    16     s1.y = 4;
    17     cout<<"初始化成员变量的情况下："<<s1.add()<<endl;
    18     system("pause");
    19     return 0;
    20 }
    21 =>没初始化成员变量的情况下：0
    22   初始化成员变量的情况下：
    ```

    **C++中的结构体与类的区别：** **(1)class中默认的成员访问权限是private的，而struct中则是public的。** **(2)class继承默认是private继承，而从struct继承默认是public继承。**

#### 1.4 结构体的作用 <a href="#t4" id="t4"></a>

* 在实际项目中，结构体是大量存在的。研发人员常使用结构体来封装一些属性来组成新的类型。由于C语言内部程序比较简单，研发人员通常使用结构体创造新的“属性”，其目的是简化运算。
* 结构体在函数中的作用不是简便，**最主要的作用就是封装。**封装的好处就是可以再次利用。让使用者不必关心这个是什么，只要根据定义使用就可以了。

#### 1.5 结构体的大小与内存对齐 <a href="#t5" id="t5"></a>

* **默认的对齐方式：**各成员变量在存放的时候根据在结构中出现的顺序依次申请空间，同时按照上面的对齐方式调整位置，空缺的字节VC会自动填充。同时VC为了确保结构的大小为结构的字节边界数（即该结构中占用最大空间的类型所占用的字节数）的倍数，所以在为最后一个成员变量申请空间后，还会根据需要自动填充空缺的字节。
* **注：VC对变量存储的一个特殊处理。为了提高CPU的存储速度，VC对一些变量的起始地址做了“对齐”处理。在默认情况下，VC规定各成员变量存放的起始地址相对于结构的起始地址的偏移量必须为该变量的类型所占用的字节数的倍数。**
*   (1)示例代码一

    ```
    1 struct MyStruct
    2 {
    3     double dda1;
    4     char dda;
    5     int type;
    6 };
    7 //错：sizeof(MyStruct)=sizeof(double)+sizeof(char)+sizeof(int)=13。
    8 //对：当在VC中测试上面结构的大小时，你会发现sizeof(MyStruct)为16
    ```

    **注：为上面的结构分配空间的时候，VC根据成员变量出现的顺序和对齐方式。**
* **(1)先为第一个成员dda1分配空间，其起始地址跟结构的起始地址相同（刚好偏移量0刚好为sizeof(double)的倍数），该成员变量占用sizeof(double)=8个字节；**
* **(2)接下来为第二个成员dda分配空间，这时下一个可以分配的地址对于结构的起始地址的偏移量为8，是sizeof(char)的倍数，所以把dda存放在偏移量为8的地方满足对齐方式，该成员变量占用sizeof(char)=1个字节；**
* **(3)接下来为第三个成员type分配空间，这时下一个可以分配的地址对于结构的起始地址的偏移量为9，不是sizeof(int)=4的倍数，为了满足对齐方式对偏移量的约束问题，VC自动填充3个字节（这三个字节没有放什么东西），这时下一个可以分配的地址对于结构的起始地址的偏移量为12，刚好是sizeof(int)=4的倍数，所以把type存放在偏移量为12的地方，该成员变量占用sizeof(int)=4个字节；**
* **这时整个结构的成员变量已经都分配了空间，总的占用的空间大小为：8+1+3+4=16，刚好为结构的字节边界数（即结构中占用最大空间的类型所占用的字节数sizeof(double)=8）的倍数，所以没有空缺的字节需要填充。所以整个结构的大小为：sizeof(MyStruct)=8+1+3+4=16，其中有3个字节是VC自动填充的，没有放任何有意义的东西。**
  * (2)示例代码二：交换一下上述例子中MyStruct的成员变量的位
*   ```
    1 struct MyStruct
    2 {
    3     char dda;
    4     double dda1;
    5     int type;
    6 };
    7 //错：sizeof(MyStruct)=sizeof(double)+sizeof(char)+sizeof(int)=13。
    8 //对：当在VC中测试上面结构的大小时，你会发现sizeof(MyStruct)为24。
    ```



    &#x20;
* **注：为上面的结构分配空间的时候，VC根据成员变量出现的顺序和对齐方式。**
* **(1)先为第一个成员dda分配空间，其起始地址跟结构的起始地址相同（刚好偏移量0刚好为sizeof(char)的倍数），该成员变量占用sizeof(char)=1个字节；**
* **(2)接下来为第二个成员dda1分配空间，这时下一个可以分配的地址对于结构的起始地址的偏移量为1，不是sizeof(double)=8的倍数，需要补足7个字节才能使偏移量变为8（满足对齐方式），因此VC自动填充7个字节，dda1存放在偏移量为8的地址上，它占用8个字节；**
* **(3)接下来为第三个成员type分配空间，这时下一个可以分配的地址对于结构的起始地址的偏移量为16，是sizeof(int)=4的倍数，满足int的对齐方式，所以不需要VC自动填充，type存放在偏移量为16的地址上，该成员变量占用sizeof(int)=4个字节；** **这时整个结构的成员变量已经都分配了空间，总的占用的空间大小为：1+7+8+4=20，不是结构的节边界数（即结构中占用最大空间的类型所占用的字节数sizeof(double)=8）的倍数，所以需要填充4个字节，以满足结构的大小为sizeof(double)=8的倍数。所以该结构总的大小为：sizeof(MyStruct)为1+7+8+4+4=24。其中总的有7+4=11个字节是VC自动填充的，没有放任何有意义的东西。**
* **字节的对齐方式：**
* 在VC中提供了#pragmapack(n)来设定变量以n字节对齐方式。n字节对齐就是说变量存放的起始地址的偏移量有两种情况：第一，如果n大于等于该变量所占用的字节数，那么偏移量必须满足默认的对齐方式；第二，如果n小于该变量的类型所占用的字节数，那么偏移量为n的倍数，不用满足默认的对齐方式。结构的总大小也有个约束条件，分下面两种情况：如果n大于所有成员变量类型所占用的字节数，那么结构的总大小必须为占用空间最大的变量占用的空间数的倍数；否则必须为n的倍数。
* **注：VC对结构的存储的特殊处理确实提高了CPU存储变量的速度，但有时也会带来一些麻烦，我们也可以屏蔽掉变量默认的对齐方式，自己来设定变量的对齐方式。**
*   (1)示例代码

    ```
     1 #pragmapack(push)//保存对齐状态
     2 
     3 
     4 #pragmapack(4)//设定为4字节对齐
     5 
     6 struct test
     7 {
     8     char m1;
     9     double m4;
    10     int m3;
    11 };
    12 
    13 #pragmapack(pop)//恢复对齐状
    ```

    &#x20;

    **注：以上结构的大小为16，下面分析其存储情况。**
* **(1)首先为m1分配空间，其偏移量为0，满足我们自己设定的对齐方式（4字节对齐），m1占用1个字节；**
* **(2)接着开始为m4分配空间，这时其偏移量为1，需要补足3个字节，这样使偏移量满足为n=4的倍数（因为sizeof(double)大于n）,m4占用8个字节；**
* **(3)接着为m3分配空间，这时其偏移量为12，满足为4的倍数，m3占用4个字节； 这时已经为所有成员变量分配了空间，共分配了16个字节，满足为n的倍数。如果把上面的#pragmapack(4)改为#pragma pack(8)，那么我们可以得到结构的大小为24。**