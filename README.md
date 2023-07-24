# C-p54---1-
C语言学习笔记 p54 自定义数据类型-结构体(1)
//结构体，枚举，联合体都为自定义类型
#include<stdio.h>
//声明一个结构体类型
//声明一个学生类型是想通过学生类型来创建一个学生变量(对象)
//描述学生：属性-名字+电话+性别+年龄
struct Stu
{
    char name[20];//名字
    char tele[12];//电话
    char sex[10];//性别
    int age;
}s4,s5,s6;

struct Stu s3;//全局变量
int main()
{
    //创建的结构体变量
    struct Stu s1;
    struct stu s2;
    return 0;
}

//特殊声明
//匿名结构体类型
struct 
{
    int a;
    char b;
    float c;
}x;
//这里struct后面没有变量名，需要在后面赶紧补一个x。一般这种代码比较挫，不建议使用

struct
{
    int a;
    char c;
}sa;

struct
{
    int a;
    char c;
}* psa;
int main()
{
    psa=&sa;
    return 0;
}//这里代码编不过去，因为这里不是同一个类型的变量，一个是匿名结构体类型，一个是匿名结构体指针类型

struct Node
{
    int data;//4/8。存放数据的地方是数据域
    //struct Node n;这种写法是错误的
    struct Node* next;//4/8。存放指针的地方是指针域
};
int main()
{
    sizeof(struct Node);
    return 0;
}

typedef struct Node//即使重命名，这里的Node是不可以省略掉的
{
    int dataa;//4
    struct Node* next;//4/8
}Node;
int main()
{
    struct Node n1;
    Node n2;
    return 0;
}

struct T
{
    double weight;
    short age;
};
struct S
{
    char c;
    struct T st;//这里的意思是T类型的st
    int a;
    double d;
    char arr[20];
};
int main()
{
    struct S s={'c',100,3.14,"hello bit"};
    struct S s={'c',{55.6,30},100,3.14,"hello bit"};
    printf("%c %d %lf %s\n",s.c,s.a,s.d,s.arr);
    printf("lf\n",s.st.weight);
    return 0;
}


//结构体内存的对齐
struct S1
{
    char c1;
    int a;
    char c2;
};

struct S2
{
    char c1;
    char c2;
    int a;
    
};
int main()
{
    struct S1 s1={0};
    printf("%d\n",sizeof(s1));//
    struct S2 s2={0};
    printf("%d\n",sizeof(s2));//
    return 0;
}
