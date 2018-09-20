# Miracl-Library-
摸索了两天终于配置好了

MIRACL Lib 配置指南！20180920耗时两天终于琢磨通了，Visual Studio， Windows 环境
1. 首先github上获取miracl的source code
2. IDE 环境 Visual Studio
1. 首先github上获取miracl的source code
https://github.com/miracl/MIRACL
上不去请用梯子

2. IDE 环境 Visual Studio
（1） 让我们打开miracl code里面vc2005.txt，
Name: miracl
Location: d:\myprojects (for example)
Solution name: miracl

Click OK

Click Application settings
Click on Static library.
Disable precompiled headers
Click on Finish

Click on Header Files in the left hand pane
Click on Project, and Add Existing Item
Add miracl.h and mirdef.h from wherever you have unzipped the miracl
distribution

Click on Source Files in the left hand pane
Click on Project, and Add Existing Item
Add the following MIRACL source files from the miracl distribution
to the project
（2）此处需要注意，在添加source file的时候请参照ms32doit.bat 里面的C 文件列表

此处需要注意： 1. 如果提示precompiled headers 的错，请在properties->C/C+±>Precompiled Headers选择not using！

Then Click on Build miracl. The library is created in directory
d:\myprojects\miracl\debug\miracl.lib

Close this project

(3) 此时我们就做好了一个miracl.lib，然后请找到这个lib，连同miracl.h和mirdef.h一起放到同一个文件下。

(4)然后我们用brent.c举个例子

Click on Header Files in the left hand pane
Click on Project, and Add Existing Item
Add miracl.h and mirdef.h from wherever you have unzipped the miracl
distribution
Click on Source Files in the left hand pane
Right click on the automatically generated file brent.cpp, and exclude it
from the project.
Click on Project, and Add Existing Item
Add the file brent.c 此处注意使用brent.c并不是txt里所说的cpp from the miracl distribution

Click on Project, and Add Existing Item. Navigate to where-ever the miracl
library has been created (d:\myprojects\miracl\debug) and add miracl.lib
to the project.

Click on Build brent

此处需要注意在build 过程中 会有这么几种error：

如果遇到precompiled headers 的错，在properties->Configuration Properties->C/C+±>Precompiled Headers选择not using！
libc.lib相关的错 请加入 #pragma comment (linker,"/NODEFAULTLIB:libc.lib")
记住使用MFC static library，在properties->->Configuration Properties->General->Use of MFC -> Use MFC in a static library
external symbol __imp__fputc 的错，properties->Configuration Properties->C/C+±>Code Generation->Runtime Library -> Multi-threaded Debug DLL （这一步卡了好久，最后一google就查到了！！智商捉急）
快乐的使用吧！！！！！
The source files are compiled and linked to the miracl library. To run the
program Click on Debug, and then on Start without Debugging.

如果还有什么别的问题，可以邮箱leapoo@126.com联系我。
