# typedef



要想理解typedef，最好先了解一下函数指针

### C/C++的关键字typedef

```
// 创建名为uint和uchar的别名
typedef unsigned int uint;
typedef unsigned char uchar;

uint a; // 等同于unsigned int a;
uchar b;
```

### 函数指针

原名叫`function pointer`

```cpp
// 声明一个void类型的函数，没有参数
void func();

// 声明一个void类型的函数指针，没有参数
void (*fun_ptr)():	//仅仅是前面加个*而已

// 定义该函数
void func(){
 cout << 1 << endl;
}

// 定义该函数指针
func_ptr = &func;
```

### typedef用于泛型指针

```cpp
void* (*AllocMem)(size_t size); // 声明一个指针函数，其返回类型是一个无类型指针，输入参数为size_t
```

正常如果使用这个函数指针，大概是这么用：

```cpp
  // 声明函数指针
	void* (*func_ptr)(size_t t);
	
	// 声明函数
	void* func(size_t t) 
	{
		return nullptr;
	}

	int printHello()
	{
		// 对该函数指针进行赋值
		func_ptr = &func;
		// 调用函数
		auto a = func_ptr(3);
		...
	}
```

多个函数指针

```cpp
  // 声明四个指针函数，类型完全相同
	void* (*func_ptr1)(size_t t);
	void* (*func_ptr2)(size_t t);
	void* (*func_ptr3)(size_t t);
	void* (*func_ptr4)(size_t t);

	void* func(size_t t) 
	{
		return nullptr;
	}

	int printHello()
	{
		func_ptr1 = &func;
		func_ptr2 = &func;
		func_ptr3 = &func;
		func_ptr4 = &func;
	} 
```

加上`typedef`后

```cpp
typedef void* (*func_ptr)(size_t t);
	
	void* func(size_t t) 
	{
		return nullptr;
	}

	int printHello()
	{
		// 通过定义func_ptr这个别名，来简化生成函数指针的操作
		func_ptr func_ptr1 = &func;
		func_ptr func_ptr2 = &func;
		func_ptr func_ptr3 = &func;
		func_ptr func_ptr4 = &func;
	}
```
