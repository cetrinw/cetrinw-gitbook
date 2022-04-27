# PROJECT

可以用来指定工程的名字和支持的语言，默认支持所有语言

PROJECT (HELLO) 指定了工程的名字，并且支持所有语言—建议

PROJECT (HELLO CXX) 指定了工程的名字，并且支持语言是C++

PROJECT (HELLO C CXX) 指定了工程的名字，并且支持语言是C和C++

该指定隐式定义了两个CMAKE的变量

\_BINARY\_DIR，本例中是 HELLO\_BINARY\_DIR

\_SOURCE\_DIR，本例中是 HELLO\_SOURCE\_DIR

MESSAGE关键字就可以直接使用者两个变量，当前都指向当前的工作目录，后面会讲外部编译

问题：如果改了工程名，这两个变量名也会改变

解决：又定义两个预定义变量：PROJECT\_BINARY\_DIR和PROJECT\_SOURCE\_DIR，这两个变量和HELLO\_BINARY\_DIR，HELLO\_SOURCE\_DIR是一致的。所以改了工程名也没有关系
