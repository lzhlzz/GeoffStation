layout: post
title: VS2010 控制台和窗口的转换
date: 2015/9/28 20:00:00
categories: 
- Visual Studio
tags: 
- vs2010
- console
- windows
---

# 1. 控制台和窗口是什么？

Visual Studio 是常用的开发工具，包括多种部件。其中，开发C/C++程序的称为 Visual C++。

新建项目的时候，一般选择“Win32控制台应用程序”或“Win32工程”，区别是：

* Win32控制台应用程序： 程序入口是main函数，运行程序会出现一个控制台（黑框），从控制台输入输出比较方便

* Win32工程： 程序入口是WinMain函数，运行程序没有控制台，如果要输出窗口需要开发者自己创建

在VS2010下，如下图：

![VS2010新建工程](/images/20150529/createproject.png)




# 2. 相互转换

建立工程后，如果需要在“控制台”和“窗口”程序之间相互转换，要设置两个地方。

## 2.1. 设置CPP文件

选择具有主函数（main或WinMain）的c或cpp文件，右键选择“属性”，找到下图所示部分，

![设置cpp文件](/images/20150529/cpp.png)

如果要更改为控制台程序，则参数为：

* Debug模式下是 **WIN32, _DEBUG, _CONSOLE**
* Release模式下是 **WIN32, _NDEBUG, _CONSOLE**

如果要更改为窗口程序，则参数为：

* Debug模式下是 **WIN32, _DEBUG, _WINDOWS**
* Release模式下是 **WIN32, _NDEBUG, _WINDOWS**

## 2.2. 设置连接器

选择工程，右键选择“属性”，找到链接器，如下图：

![设置连接器](/images/20150529/linker.png)

如果要更改为控制台程序，则参数为：

**/subsystem:console**

如果要更改为窗口程序，则参数为：

**/subsystem:windows**




# 3. 设定错误会出现什么提示？

如果设定错误，编译链接时可能会出现如下提示：

**LIBCD.lib(crt0.obj) : error LNK2001: unresolved external symbol _main**

# 参考资料

[1. PRB: Link Error LNK2001: Unresolved External Symbol _main](https://support.microsoft.com/en-us/kb/291952)
