# ADD\_SUBDIRECTORY



```cpp
ADD_EXECUTABLE(hello main.cpp)
```

ADD\_SUBDIRECTORY(source\_dir \[binary\_dir] \[EXCLUDE\_FROM\_ALL])

* 这个指令用于向当前工程添加存放源文件的子目录，并可以指定中间二进制和目标二进制存放的位置
* EXCLUDE\_FROM\_ALL函数是将写的目录从编译中排除，如程序中的example
*   ADD\_SUBDIRECTORY(src bin)

    将 src 子目录加入工程并指定编译输出(包含编译中间结果)路径为bin 目录

    如果不进行 bin 目录的指定，那么编译结果(包括中间结果)都将存放在build/src 目录
