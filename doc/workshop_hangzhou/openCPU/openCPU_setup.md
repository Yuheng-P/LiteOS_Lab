# openCPU开发环境安装指导

本文档旨在帮助开发者配置openCPU开发环境。文档中涉及的安装包都在开发环境工具包中给出。安装时请尽量安装到默认路径，否则可能需要开发者手动添加环境变量。
## 1.安装GCC Compiler
GCC Compiler安装包为gcc-arm-none-eabi-4_9-2015q2-20150609-win32.exe。打开安装程序，按照默认安装即可。

![1](assets/1.PNG)

![2](assets/2.PNG)

![3](assets/3.PNG)

![4](assets/4.PNG)

注意，在最后一步中，需要勾选add path to environment variable。否则需要手动将GCC Compiler安装路径添加到系统环境变量，如下图所示。

![5](assets/5.PNG)

## 2.安装自动化构建工具Scons
Scons构建工具通过Python2.7编写，其它Python版本可能不兼容。因此需要先安装Python2.7。开发者可以通过开发环境工具包中的python-2.7.10.msi来安装。

![6](assets/6.PNG)

![7](assets/7.PNG)

![8](assets/8.PNG)

注意上图，这里需要勾选添加路径。

![9](assets/9.PNG)

![10](assets/10.PNG)

至此完成了Python2.7的安装。但是，默认情况下Python脚本无法访问Windows系统API库，因此需要安装pywin32库。开发者可以通过开发环境工具包中的pywin32-220.win32-py2.7.exe来安装。

![11](assets/11.PNG)

![12](assets/12.PNG)

![13](assets/13.PNG)

![14](assets/14.PNG)

现在，开发者可以通过开发环境工具包中的scons-2.4.0-setup.exe来安装Scons，安装过程与pywin32类似。

![15](assets/15.PNG)

![16](assets/16.PNG)

![17](assets/17.PNG)

![18](assets/18.PNG)

## 3.安装Microsoft .NET Framework

开发者可通过开发环境工具包中NDP452-KB2901907-x86-x64-AllOS-ENU.exe安装。按照默认安装即可。

![19](assets/19.PNG)

![20](assets/20.PNG)

![21](assets/21.PNG)

## 4.安装UEMonitor-3.22.0.14
通过开发环境工具包中提供的UEMonitor-3.22.0.14.msi进行安装。类似于串口调试工具，开发者可以通过该软件观察串口日志。

![22](assets/22.PNG)

![23](assets/23.PNG)

![24](assets/24.PNG)

## 5.安装UEUpdaterUI-3.22.0.14

开发者可以通过该软件，从openCPU模组的主串口进行固件升级。安装包为UEUpdaterUI-3.22.0.14.msi。

![25](assets/25.PNG)

![26](assets/26.PNG)

## 6.安装UpdatePackage-3.22.0.14

通过UpdatePackage-3.22.0.14.msi进行安装。

![27](assets/27.PNG)

![28](assets/28.PNG)

## 7.验证开发环境

完成上述环境搭建步骤后，开发者可以通过开发环境工具包中的样例工程来验证开发环境是否搭建成功。比如，打开example目录下的OLED文件夹，打开其中的“命令提示符”，并输入命令```scons_new.bat```：

![33](assets/33.PNG)

![30](assets/30.PNG)

若环境搭建成功，则会输出：

![31](assets/31.PNG)

并且在工程目录下，会生成new.fwpkg文件。该文件就是openCPU方案需要烧录到模组中的firmware package。

![32](assets/32.PNG)

若得到了上面的结果，则说明环境搭建成功。

## 8.常见问题及解决方法

### 8.1报 arm-none-eabi-gcc 错误

打开“命令提示符”，并输入命令```scons_new.bat```，出现```No such file or directory```的错误：

![34](assets/34.PNG)

解决方案：
1. 查看系统环境变量是否正确配置。

2. 查找电脑中是否有文件与Compiler-GCC(GNU Tools ARM Embedded)重名。若有请将其删除。

### 8.2路径有误
若开发者在安装过程中修改了默认的安装路径，需要在scons_new.bat中的路径做相应的修改。

![35](assets/35.PNG)

### 8.3路径中包含中文
若工程目录中含有中文，则编译过程中会出现下面的错误：

![36](assets/36.PNG)

解决方案：

* 使用全英文路径。