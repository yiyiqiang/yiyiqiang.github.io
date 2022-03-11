# 1. 【常见头文件】

## 1.1. 【stdio.h】

1. **变量**
    - `size_t`  无符号整数类型，是 sizeof 关键字的结果
    - `FILE`  文件流信息的对象类型
2. **宏**
    - `NULL`  空指针常量
    - `EOF`  表示一个到达文件结束的负整数
    - `stderr`、`stdin` 、`stdout`  FILE 类型的指针，分别对应于标准错误、标准输入和标准输出流
    - `SEEK_CUR`、`SEEK_END` 、`SEEK_SET`  fseek 函数中使用，用于在一个文件中定位不同的位置
3. 函数
    - `int fclose(FILE *stream)`  关闭流 stream。刷新所有的缓冲区


## 1.2. 【system函数】


1. **【格式】** `int system(const char *command)`
    - 【所属头文件】 `#include <stdlib.h>`
    - 【功能】在已经运行的程序中执行另外一个外部程序
    - 【参数】外部可执行程序名字
    - 【返回值】成功时不同系统返回值不一样，失败时通常是 -1
2. **【POSIX】**
    - C语言所有的库函数调用，只能保证语法一致，不能保证执行结果是否一致
    - 同样的库函数在不同的操作系统下其执行结果可能一样，也可能不一样
    - POSIX是一个标准，只要符合这个标准的函数，在不同的系统下执行的结果就可以一致
    - Unix和linux很多库函数都是支持POSIX的，但windows支持的比较差
3. **【Qt图形界面调用system】**
    - step1. New Project  >>  Application  >>  Qt Widgets Application
    - step2. 编辑选项卡中，双击 Forms >> mainwindow.ui
    - step3. 设计选项卡中，拖到按钮控件到设计区，双击按钮修改文字，右击选择 转到槽...
        - 使用 `system("calc");` 会出现cmd黑窗口
        - 导入系统库 `windows.h` 输入 `WinExec("calc",SW_HIDE);` 系统调用时默认隐藏黑窗口



math.h
double sqrt(double x) 计算x的平方根
double pow(double x, double y) 计算x的y次幂
double ceil(double x) 求不小于x的最小整数，并以double形式显示
double floor(double x) 求不大于x的最大整数，并以double形式显示

ctype.h
int toupper(int x) 如果x为小写字母，则返回对应的大写字母
int tolower(int x) 如果x为大写字母，则返回对应的小写字母

stdlib.h
int rand(void)  产生一个随机数
void exit(int retval) 终止程序
