# using



### 指定别名

```cpp
//给类型指定别名
using value_type = _Ty

//给模板指定别名
template <typename T>
using Vec = MyVector<T, MyAlloc<T>>;
 
// usage
Vec<int> vec;
```

####

### 简化了从命名空间的成员访问

```cpp
namespace veryLongName {
    int a=100;
    void func(){cout<<"hello namespace"<<endl;}
}

void test07()
{

    //使用veryLongName命名空间
    using namespace veryLongName;

    //出现的变量 从veryLongName命名空间中找 找不到 从其他地方中
    cout<<"a = "<<a<<endl;
    func();
}
```

### using命名空间是,变量名相同,先访问局部变量

```cpp
namespace veryLongName {
    int a=100;
    void func(){cout<<"hello namespace"<<endl;}
}

void test07()
{
    int a=200;
    //使用veryLongName命名空间
    using namespace veryLongName;

    //出现的变量 从veryLongName命名空间中找 找不到 从其他地方中
    cout<<"a = "<<a<<endl;//访问的是局部变量中的a
    cout<<"a = "<<veryLongName::a<<endl;//访问的是veryLongName的a
    func();
}
```

### using 命名空间的成员变量,会很本地同名变量冲突,但不会和全局变量冲突

```cpp
namespace veryLongName {
	int a = 100;
	void func(){cout << "hello namespace" << endl;}
}
void test01()
{
	//using直接使用 命名空间的成员会和局部变量冲突
	int a = 200;
	//指明 使用命名空间中的具体成员 容易和其他变量冲突
	using veryLongName::a; //error
	
	cout << "a = " << a << endl;
	//但是func使用的时候 必须加作用域
	veryLongName::func();
}
```
