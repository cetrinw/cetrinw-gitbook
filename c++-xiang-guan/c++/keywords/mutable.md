# mutable



mutalbe的中文意思是“可变的，易变的”，跟constant（既C++中的const）是反义词。 在C++中，mutable也是为了突破const的限制而设置的。被`mutable`修饰的变量，将永远处于可变的状态，即使在一个const函数中。 我们知道，如果类的成员函数不会改变对象的状态，那么这个成员函数一般会声明成const的。但是，有些时候，我们需要在const的函数里面修改一些跟类状态无关的数据成员，那么这个数据成员就应该被`mutalbe`来修饰。

```cpp
#include <iostream>

using namespace std;

class A
{
public:
	A(int a):m_a(a){}
	void matest()const;
	void macout()const
	{
		cout << m_a << endl;
	}
private:
	int m_a;
};

void A::matest() const
{
	//m_a = 10;//被const修饰的函数不允许修好任何类状态值(类里面的数据)
	cout << m_a << endl;
}

int main()
{
	const A a(1);
	a.macout();//用const修饰的一个类使用一个const修饰的方法
	return 0;
}
```

使用`mutalbe`

```cpp
#include <iostream>

using namespace std;

class A
{
public:
	A(int a):m_a(a){}
	void matest()const;
	void macout()const
	{
		cout << m_a << endl;
	}
private:
	mutable int m_a;
};

void A::matest() const
{
	m_a = 10;//在定义时用mutable来突破这层限制
	cout << m_a << endl;
}

int main()
{
	const A a(1);
	a.macout();
	return 0;
}
```
