# C language daily study
## The usage of .h (self writing)
### 什么是.h文件
.h文件是头文件，是一种包含函数声明和宏定义的文件，用于在多个源文件之间共享信息。
### .h文件的作用
.h文件的作用是将函数的声明和定义分离，将函数的声明放在.h文件中，将函数的定义放在.c文件中，这样可以使得程序的结构更加清晰，便于维护。
适合与多c文件的程序，便于变量的声明以及函数的调用。
### .h文件的使用
.h文件的使用分为两种情况：
#### 1.在同一个文件夹下
在同一个文件夹下，只需要在需要调用的文件中使用#include "filename.h"即可。
#### 2.在不同文件夹下
在不同文件夹下，需要在需要调用的文件中使用#include "../filename.h"即可。
### .h文件的编写
.h文件的编写分为两种情况：
#### 1.只有函数的声明
```cpp
#ifndef _TEST_H_
#define _TEST_H_
int add(int a,int b);
#endif
```
#### 2.函数的声明和定义
```cpp
#ifndef _TEST_H_
#define _TEST_H_
int add(int a,int b)
{
    return a+b;
}
#endif
```
### .h文件的注意事项
#### 1.头文件的名字
头文件的名字应该与.c文件的名字相同，例如test.c的头文件应该命名为test.h。（不是必须）
#### 2.头文件的保护
头文件的保护是为了防止头文件被重复包含，防止重复定义，防止重复声明。
#### 3.头文件的包含
头文件的包含应该放在所有的头文件的最前面，包含的顺序应该是从小到大，例如：
```cpp
#include <stdio.h>
#include "test.h"
```
这是因为有些头文件中包含了其他的头文件，如果先包含了大的头文件，那么就会出现重复包含的情况。
#### 4.头文件的编译
头文件不需要单独编译，只需要在需要调用的文件中使用#include "filename.h"即可。
#### 5.头文件的注释
头文件的注释应该包含头文件的作用，头文件的作者，头文件的版本，头文件的修改记录等。
### 头文件的使用原理（c语言编译原理
#### 1.预处理
预处理是在编译之前进行的，预处理的主要工作是将#include包含的文件插入到程序中，将#define定义的宏进行替换，将#if进行判断，将#ifdef进行判断，将#ifndef进行判断，将#endif进行判断，将#elif进行判断，将#undef取消宏定义，将#line进行行号指定，将#error进行错误提示，将#warning进行警告提示，将#pragma进行编译器指令等。
#### 2.编译
编译是将预处理后的文件进行编译，编译的主要工作是将c语言翻译成汇编语言。
#### 3.汇编
汇编是将编译后的文件进行汇编，汇编的主要工作是将汇编语言翻译成机器语言。
#### 4.链接
链接是将汇编后的文件进行链接，链接的主要工作是将多个文件链接成一个可执行文件。
#### 5.执行
执行是将链接后的文件进行执行，执行的主要工作是将可执行文件加载到内存中，然后执行。








# 洛谷学习

## 二分查找  

### 二分查找的基本思想
二分查找是一种在有序数组中查找某一特定元素的搜索算法。  

查找过程从数组的中间元素开始，如果中间元素正好是要查找的元素，则搜索过程结束；  

如果某一特定元素大于或者小于中间元素，则在数组大于或小于中间元素的那一半中查找，  

而且跟开始一样从中间元素开始比较。如果在某一步骤数组为空，则代表找不到。
这种搜索算法每一次比较都使搜索范围缩小一半。
### 二分查找的实现
#### 二分查找的递归实现
```cpp
int binary_search(int a[],int left,int right,int x)
{
    if(left>right)return -1;
    int mid=(left+right)/2;
    if(a[mid]==x)return mid;
    else if(a[mid]>x)return binary_search(a,left,mid-1,x);
    else return binary_search(a,mid+1,right,x);
}
```
#### 二分查找的非递归实现
```cpp
int binary_search(int a[],int left,int right,int x)
{
    while(left<=right)
    {
        int mid=(left+right)/2;
        if(a[mid]==x)return mid;
        else if(a[mid]>x)right=mid-1;
        else left=mid+1;
    }
    return -1;
}
```
### 二分查找的变形
#### 查找第一个等于给定值的元素
```cpp
int binary_search(int a[],int left,int right,int x)
{
    while(left<=right)
    {
        int mid=(left+right)/2;
        if(a[mid]<x)left=mid+1;
        else if(a[mid]>x)right=mid-1;
        else
        {
            if(mid==0||a[mid-1]!=x)return mid;
            else right=mid-1;
        }
    }
    return -1;
}
```
#### 查找最后一个等于给定值的元素
```cpp
int binary_search(int a[],int left,int right,int x)
{
    while(left<=right)
    {
        int mid=(left+right)/2;
        if(a[mid]<x)left=mid+1;
        else if(a[mid]>x)right=mid-1;
        else
        {
            if(mid==right||a[mid+1]!=x)return mid;
            else left=mid+1;
        }
    }
    return -1;
}
```
#### 查找第一个大于等于给定值的元素
```cpp
int binary_search(int a[],int left,int right,int x)
{
    while(left<=right)
    {
        int mid=(left+right)/2;
        if(a[mid]<x)left=mid+1;
        else
        {
            if(mid==0||a[mid-1]<x)return mid;
            else right=mid-1;
        }
    }
    return -1;
}
```
### 查找最后一个小于等于给定值的元素
```cpp
int binary_search(int a[],int left,int right,int x)
{
    while(left<=right)
    {
        int mid=(left+right)/2;
        if(a[mid]>x)right=mid-1;
        else
        {
            if(mid==right||a[mid+1]>x)return mid;
            else left=mid+1;
        }
    }
    return -1;
}
```
------------------
### [P1102 A-B 数对](https://www.luogu.com.cn/problem/P1102)
#### 题目描述
> 给出一串正整数数列以及一个正整数 
C，要求计算出所有满足  A−B=C的数对的个数（不同位置的数字一样的数对算不同的数对）
#### 输入格式
> 第一行包含两个整数 N,C，分别表示数列中数字的个数以及题目中的 C。
> 第二行包含 N 个整数，表示数列中的 N 个数字。  
> > 数据范围
> $1 ≤ N ≤ 200000$
> $1 ≤ C,a ≤ 2^{30}$
#### 代码实现思路
> 1. 读入数据
> 2. 使用sort函数直接排序
> 3. 使用二分查找，找到一个等于a[i]+c的数的位置，记为r
> 4. 向后遍历，直到找到一个不等于a[i]+c的数的位置，记为l
> 5. 答案加上r-l
> 6. 重复2-5
> 7. 输出答案
#### 代码实现
```cpp
#include <bits/stdc++.h>
using namespace std;

long long a[1000001]={0};
long long sum=0;
void find(int x,int n,int i)
{   
    int left = i,right = n;
    while(left<=right){
        int mid = (left+right)/2;
        if(x > a[mid])left = mid+1;
        else if(x < a[mid])right = mid-1;
        else {
            int tmmp=mid;
            while(a[mid-1]==a[mid]&&mid>=2)
            {mid--;sum++;}
            while(a[tmmp+1]==a[tmmp]&&tmmp<n)
            {tmmp++;sum++;}
            sum++;
            return;}
    }
    return;
}
int main()
{
    int N;
    long long C;
    cin >> N >> C;
    for (int i = 1; i <= N; i++)
    {
        cin >> a[i];
    }
    sort(a+1,a+N+1);
    int i=1;
    long long sum1;
    while(a[i]+C<=a[N])
    {
        if(a[i]==a[i-1]){sum+=sum1;i++;continue;}
        long long tmp=sum;
        find(a[i]+C,N,i);
        sum1 = sum-tmp;
        i++;
    }
    cout << sum;
    system("pause");
    return 0;

}
```
------------------

#### 总结以及反思
> 1. 二分查找的时候，要注意边界条件，以及循环条件
> 2. 二分查找的时候，要注意找到的是第一个等于x的数，还是最后一个等于x的数
> 3. 注意数据范围，以及数据类型，防止溢出（本题需注意某些变量使用longlong类型）


