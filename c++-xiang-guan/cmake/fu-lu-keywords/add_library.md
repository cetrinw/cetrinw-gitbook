# ADD\_LIBRARY

ADD\_LIBRARY(hello SHARED ${LIBHELLO\_SRC})

* hello：就是正常的库名，生成的名字前面会加上lib，最终产生的文件是libhello.so
* SHARED，动态库 STATIC，静态库
* ${LIBHELLO\_SRC} ：源文件
