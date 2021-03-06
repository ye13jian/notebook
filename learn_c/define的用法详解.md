---
title: 宏define的用法
categories: C语言
tags: [C语言]
---
# 宏define的用法

define的介绍信息、总结信息

## 无参数宏定义
#define 标识符 字符串  
“标识符”为所定义的宏名。“字符串”可以是常数、表达式、格式串等。

它的作用是指定标识符PI来代替常数3.14。在编写源程序时，所有用到3.14的地方都可用PI代替，而对源程序作编译时，将先由预处理程序进行宏代换，即用3.14去置换所有的宏名PI，然后再进行编译。

宏定义是用宏名来表示一个字符串，在宏展开时又以该字符串取代宏名，这只是一种简单的代换，字符串可以是常数，也可以是表达式，预处理程序对它不作任何检查。如有错误，只能在编译已被宏展开后的源程序时发现。

宏定义不是说明或语句(它是预处理指令)，在行末不必加分号，如加上分号则连分号也一起置换。

下面举一个无参数宏替代常数的例子：
```c
#define PI 3.14
#include <stdio.h>

int main()
{
float r = 1.0;
float area = PI*r*r;
printf("The area of the circle is %f",area);
return 0;
}
```
## 带参数宏定义

C语言允许宏带有参数。在宏定义中的参数称为形式参数，在宏调用中的参数称为实际参数。对带参数的宏，在调用中，不仅要宏展开，而且要用实参去代换形参。

带参数宏定义的一般形式为：#define 宏名(形参表) 字符串。在字符串中含有各个形参。带参数宏调用的一般形式为：宏名(实参表)。例如：

```
#define M(y) y*y+3*y
....
k=M(5);
....
```
在宏调用时，用实参5去代替形参y，经预处理宏展开后的语句为:`k=5*5+3*5`。举一个具体例子：
```c
#define MAX(a,b) (a>b)?a:b
#include <stdio.h>

int main(){
    int x,y,max;
    printf("input two numbers: ");
    scanf("%d%d",&x,&y);
    max = MAX(x,y);
    printf("max=%d\n",max);
    return 0;
}
```