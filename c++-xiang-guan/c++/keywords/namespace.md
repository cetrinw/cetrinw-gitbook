# namespace



作用域

### 作用域运算符 ::（表明 数据、方法 的归属性问题）

```cpp
using namespace std;

int a = 10;//全局变量

void test01()
{
    int a = 20;//局部变量
    cout<<"局部变量a = "<<a<<endl;//优先选择局部变量

    //::作用域运算符（c++独有）
    cout<<"全局变量a = "<<::a<<endl;//取全局变量

}
```

### namespace命名空间的定义

```cpp
//定义一个名字为A的命名空间（变量、函数）
namespace A {
    int a = 100;
}

namespace B {
    int a = 200;
}

void test02()
{
    //A::a  a是属于A中
    cout<<"A中a = "<<A::a<<endl;//100
    cout<<"B中a = "<<B::a<<endl;//200
}
```

### 命名空间可嵌套命名空间

```cpp
namespace A {

    int a = 1000;

    namespace B {
        int a = 2000;
    }
}

void test03()
{
    cout<<"A中的a = "<<A::a<<endl; //1000
    cout<<"B中的a = "<<A::B::a<<endl; //2000
}
```

### 命名空间是开放的，即可以随时把新的成员加入已有的命名空间中

```cpp
namespace A {
    int a = 100;
    int b = 200;
}

//将c添加到已有的命名空间A中
namespace A {
    int c = 300;
}

void test04()
{
    cout<<"A中a = "<<A::a<<endl;//100
    cout<<"A中c = "<<A::c<<endl;//200
}
```

### 命名空间可以存放`变量`和`函数`

```cpp
amespace A {
    int a=100;//变量

    void func()//函数
    {
        cout<<"func遍历a = "<<a<<endl;
    }
}

void test05()
{
    //变量的使用
    cout<<"A中的a = "<<A::a<<endl;

    //函数的使用
    A::func();
}
```

### 命名空间中的函数，可以在“命名空间”外 定义

```cpp
namespace A {
    int a=100;//变量

    void func();
}

void A::func()//成员函数 在外部定义的时候 记得加作用域
{
    //访问命名空间的数据不用加作用域
    cout<<"func遍历a = "<<a<<endl;
}

void funb()//普通函数
{
    cout<<"funb遍历a = "<<A::a<<endl;
}

void test06()
{
   A::func();//100
   funb();//100
}
```

### 无名命名空间，意味着命名空间中的标识符只能在本文件内访问，相当于给这个标识符加上了static，使得其可以作为内部连接

```cpp
namespace{

int a =10;

void func(){cout << "hello namespace "<< endl}
}

void test(){
	cout << "a:" << a << endl;
	func();
}
```

### 命名空间能取别名

```cpp
namespace veryLongName{

int a = 10;
void func(){ cout << "hello namespace" << endl; }
}

void test(){
    namespace shortName = veryLongName;
    cout << "veryLongName::a : " << shortName::a << endl;
    veryLongName::func();
    shortName::func();
}
```
