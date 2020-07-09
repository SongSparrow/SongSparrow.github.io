---
layout: post
title: 在VS Code中编写Qt项目
description: 将Qt的开发环境使用CMake迁移到VS Code
date: 2020-07-02 13:11:00 +0800
share: true
tags:
- qt
- cmake
---

# 一、开发环境的准备


## 1. Qt的准备

- 下载地址：[Qt清华大学下载镜像](https://mirrors.tuna.tsinghua.edu.cn/qt/official_releases/qt/) 
- 安装的时候,如果还没有安装C++的编译器,就把直接使用qt自带的编译器即可
- 环境变量


## 2. CMake的准备

- 下载地址；[官方下载地址](https://cmake.org/download/)
- 按着的时候记得加上环境变量


## 3. VS Code的准备

- 下载地址：[官方下载地址](https://code.visualstudio.com/Download)
- 可以适当地个性化一下,有一个好的环境,效率也会大大提高




# 二、VS Code中的设置

<hr>

## 1. 推荐插件
1. CMake (author：twxs)

2. CMake Tools (author：Microsoft)

3. C++ (author：Microsoft)



## 2. 配置.vscode文件夹

### 为什么要配置.vscode文件夹？

这是为可以让C++可以找到qt的源文件，从而实现自动补全功能；如果不配置c_cpp_properties.json，C++就找不到qt项目中所使用的头文件，也无法使用自动补全功能，还会在引用的头文件下画出红色波浪线，非常影响体验。

### 如何操作？

打开一个空文件夹作为项目路径，之后

1. 创建`.vscode`文件夹

2. 在.vscode中创建`c_cpp_properties.json`，并填入以下内容

   1. 所有的`~/Qt5.13.0/5.13.0/mingw73_64/include`要替换成自己的实际安装路径
   
   2. `"compilerPath": "~\\bin\\g++.exe"`中也要替换成自己的实际编译器路径
   
   c_cpp_properties.json样例，完整版在[这里](https://github.com/SongSparrow/CMakeQtVSCodeConfig/blob/master/vscode/c_cpp_properties.json)
   
   ```json
   {
       "version": 4,
       "configurations": [
           {
               "name": "mingw73_64",
               "intelliSenseMode": "gcc-x64",
               "includePath": [
                   "~/Qt5.13.0/5.13.0/mingw73_64/include",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/Qt3DAnimation",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtXmlPatterns",
                   "${workspaceRoot}"
               ],
               "browse": {
                   "path": [
                       "~/Qt5.13.0/5.13.0/mingw73_64/include",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/Qt3DAnimation",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtXmlPatterns",
                       "${workspaceRoot}"
                   ]
               },
               "compilerPath": "~~~\\bin\\g++.exe",
               "cStandard": "c11",
               "cppStandard": "c++17",
               "configurationProvider": "vector-of-bool.cmake-tools",
            "compileCommands": "${workspaceFolder}/build/compile_commands.json"
           }
       ]
   }
   ```
   
3. 根据自己的需求在适当地添加其它配置文件

## 3. 编写CMakeLists.txt文件

### 1. 官方文档

[CMake官方文档](https://cmake.org/documentation/)

1. 选择自己安装的对应的CMake版本的文档，进行阅读。

2. 如果点击了`QtHelp`则会下载一个qch格式的文件，它是qt的帮助文档的格式，其中的内容和对应的网页文档完全一致。

3. 如果上网不方便，可以将qch文件导入QtCreator中进行阅读，也可以选择将之打印为PDF。

### 2. 找到介绍CMake命令的部分

此时正在使用的CMake版本是3.16，那么自然选择进入3.16版本的文档，然后就是找到文档中关于对CMakeLists语法的介绍和与qt的相关内容。

如果找不到相关内容，如下即是可供参考的链接：

1. [CMakeLists语法](https://cmake.org/cmake/help/v3.16/manual/cmake-commands.7.html)

2. [CMake Qt 用法](https://cmake.org/cmake/help/v3.16/manual/cmake-qt.7.html)

3. [Qt官方CMake文档](https://doc.qt.io/qt-5/cmake-manual.html)

如果不懂英文，这几篇博客可供参考： 

1. [知乎CMake 和 QMake](https://zhuanlan.zhihu.com/p/156231762)

2. [CSDN使用CMake构建Qt5工程](https://blog.csdn.net/wingover/article/details/82728230)

3. [博客园CMake中添加Qt模块的合理方法](https://www.cnblogs.com/whwywzhj/p/10721673.html)

4. [博客园CMakeLists.txt常用命令](https://www.cnblogs.com/xl2432/p/11225276.html)

如果还是看不懂，也不用担心，只需要下载已经写好的CMakeLists.txt即可：

[我要下载CMakeLists.txt](https://github.com/SongSparrow/CMakeQtVSCodeConfig)



**CMakeLists.txt例子**

```txt
# https://cmake.org/documentation/
cmake_minimum_required(VERSION 3.16) # 用来指定最低的cmake版本

project(YiYan) # 设置项目的名称，设置PROJECT_NAME的值

set(CMAKE_CXX_STANDARD 17) # 设置C++标准
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Qt必备，若要深入了解则查阅qt和cmake的官方文档
set(CMAKE_AUTOMOC ON) 
set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTORCC ON)

set(CMAKE_INCLUDE_CURRENT_DIR ON)

set(CMAKE_PREFIX_PATH "~~/Qt5.13.0") # 设置qt的安装路径

find_package(Qt5 COMPONENTS Widgets Core Gui REQUIRED) # 引入Qt库

# 将项目文件添加到工程中去
set(SOURCE_FILES mainwindow.cpp main.cpp) # 当前目录下的所有源文件
set(HEADER_FILES mainwindow.h) # 当前目录下的所有所有头文件
set(UI_FILES mainWindow.ui) # 当前目录下的所有ui文件
# set(RESOURCE_FILES resource.qrc) #当前目录下的所有资源文件
# set(EXTRA_RESOURCES app.rc) # 额外的资源文件
add_executable(${PROJECT_NAME}
    ${SOURCE_FILES}
    ${HEADER_FILES}
    ${UI_FILES}
    # ${RESOURCE_FILES}
    # ${EXTRA_RESOURCES}
)

target_link_libraries(${PROJECT_NAME} Qt5::Widgets Qt5::Core Qt5::Gui) # 添加Qt库
```



# 三、项目操作

### 1. 对于初学者

可以使用QtCreator创建项目，之后将qmake的文件删除，并使用VSCode打开项目文件路径

### 2. 对于熟练者

如果已经清楚地了解Qt项目的文件夹及其文件、文件内容，动手创建文件即可

### 3. 选择开发包

CMake会自动探测已有的编译器,只需要选择想要使用地编译器即可

### 3. build and run and debug

创建launch.json, 根据提示填写相应内容即可

### 6. 自动化

1. Windows

   使用bat

   ```txt
   
   ```

   







