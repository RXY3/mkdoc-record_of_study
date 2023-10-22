# MARKDOWN
[TOC]
## INTRO
*本markdown文档用于记录笔者学习和使用markdown语言时遇到的问题以及解决方式，同时不定期对于某些特定格式或是较为好用的语法进行总结*
## 简单语法
### 标题(Heading)
* 一级标题：# 一级标题
* 二级标题：## 二级标题
* 三级标题：### 三级标题
* 四级标题：#### 四级标题
* ......
### 列表(List)
* 无序列表：* 无序列表
* 有序列表：
  1. 有序列表示例  
  2. 2
  3. 3
  4. 4
  5. 5
### 字体
```markdown
**加粗**
*斜体*
***加粗且斜体***
~~划掉~~
==高亮==
__666__
```
**加粗**
*斜体*
***加粗且斜体***
~~划掉~~
==高亮==
__666__
### 引用
> this is a quote
> > this is a 嵌套引用（笔者英语水平堪忧）

### 代码语法
```py
print("helloworld")
```
通过标注不同的语言，可以实现不同的高亮以及标注
### 目录
在对应位置使用[toc]即可实现

### 字体与颜色

<div>
<font color=red size=3 face="Times New Roman">
this is red color  


```md
<font color=red size=3 face="Times New Roman">
```
通过如上格式的输入，可以使得下方的字体改变颜色，大小以及字体
</div>
<font color=black size=3 face="Times New Roman">

### 表格
| 1    | 2    | 3    |
| ---- | ---- | ---- |
| 4    | 5    | 6    |
| 7    | 8    | 9    |

```md
| 1    | 2    | 3    |
| ---- | ---- | ---- |
| 4    | 5    | 6    |
| 7    | 8    | 9    |
```
### 图片
![图片](https://img-blog.csdnimg.cn/20210412161059990.png)

```md
![图片](https://img-blog.csdnimg.cn/20210412161059990.png)
```
### 超链接
[百度](https://www.baidu.com)

```md
[百度](https://www.baidu.com)
```
### 分割线
---
```md
---
```
### 脚注
这是一个脚注[^1]

```md
这是一个脚注[^1]
[^1]:这是一个脚注
```
### 网页
<https://www.baidu.com>

```md
<https://www.baidu.com>
```
### 转义
\# 1

```md
\# 1
```



