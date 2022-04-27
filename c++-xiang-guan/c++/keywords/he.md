# & 和 \*



### 取地址运算符 &

`&`是一元运算符，返回操作数的内存地址。例如，如果 `var` 是一个整型变量，则 `&var` 是它的地址。该运算符与其他一元运算符具有相同的优先级，在运算时它是**从右向左**顺序进行的。

您可以把`&`运算符读作`取地址运算符`，这意味着，\&var 读作`var 的地址`。

### 间接寻址运算符 \*

第二个运算符是间接寻址运算符 `*`，它是 `&` 运算符的补充。`*` 是一元运算符，返回操作数所指定地址的变量的值。

请看下面的实例，理解这两种运算符的用法。

```cpp
#include <iostream>
 
using namespace std;
 
int main ()
{
   int  var;
   int  *ptr;
   int  val;

   var = 3000;

   // 获取 var 的地址
   ptr = &var;

   // 获取 ptr 的值
   val = *ptr;
   cout << "Value of var :" << var << endl;
   cout << "Value of ptr :" << ptr << endl;
   cout << "Value of val :" << val << endl;

   return 0;
}
```

当上面的代码被编译和执行时，它会产生下列结果：

```
Value of var :3000
Value of ptr :0xbff64494
Value of val :3000
```
