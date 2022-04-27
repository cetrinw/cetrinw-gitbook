# const\_cast

### 一.函数描述：

```cpp
const_cast < type-id > ( expression )
```

主要是用来去掉const属性，当然也可以加上const属性。主要是用前者，后者很少用。

#### 1.去掉const属性：

```cpp
const_case<int*> (&num)
```

常用，因为不能把一个const变量直接赋给一个非const变量，必须要转换。

#### 2.加上const属性：

```cpp
const int* k = const_case<const int*>(j)
```

一般很少用，因为可以把一个`非const`变量直接赋给一个const变量，比如：

```cpp
const int* k = j;
```

### 二. 使用范围：

#### 1. 常量指针被转化成非常量指针，转换后指针指向原来的变量(即转换后的指针地址不变)。

```cpp
class A  
{  
public:  
     A()  
     {  
      m_iNum = 0;  
     }  
      
public:  
     int m_iNum;  
};  
      
void foo()  
{  
    //1. 指针指向类  
    const A *pca1 = new A;  
    A *pa2 = const_cast<A*>(pca1);  //常量对象转换为非常量对象  
    pa2->m_iNum = 200;    //fine  
     
    //转换后指针指向原来的对象  
    cout<< pca1->m_iNum <<pa2->m_iNum<<endl; //200 200  
      
    //2. 指针指向基本类型  
    const int ica = 100;  
    int * ia = const_cast<int *>(&ica);  
    *ia = 200;  
    cout<< *ia <<ica<<endl;   //200 100  
```

#### 2. 常量引用转为非常量引用。

```cpp
class A
{
public:
　　A()
　　{
	m_iNum = 1;
　　}
 
public:
　　int m_iNum;
};
 
void foo()  
{  
 
　　A a0;
　　const A &a1 = a0;
　　A a2 = const_cast<A&>(a1);　//常量引用转为非常量引用
	
　　a2.m_iNum = 200;    //fine  
 
　　cout<< a0.m_iNum << a1.m_iNum << a2.m_iNum << endl; //１　1 200  
}
```

常量对象(或基本类型)不可以被转换成非常量对象(或基本类型)。
