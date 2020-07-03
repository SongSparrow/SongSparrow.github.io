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

<hr>

## 1. Qt的准备

- 下载地址：[Qt清华大学下载镜像](https://mirrors.tuna.tsinghua.edu.cn/qt/official_releases/qt/) 

- 安装过程： 随便一搜就有很多写得很好的博客，这里不赘述了

## 2. CMake的准备

- 下载地址；[官方下载地址](https://cmake.org/download/)

- 安装过程：

  1. 选择第二个，为所有用户**添加环境变量**
  
  2. 选择安装路径

## 3. VS Code的准备

- 下载地址：[官方下载地址](https://code.visualstudio.com/Download)

- 安装过程：不赘述

- 个性化设计：不是本文要讨论的内容



# 二、VS Code中的设置

<hr>

## 1. 推荐插件
1. CMake (author：twxs)

2. CMake Tools (author：Microsoft)

3. C++ (author：Microsoft)



## 2. 配置.vscode文件夹

打开一个空文件夹作为项目路径，之后

1. 创建`.vscode`文件夹

2. 在.vscode中创建`c_cpp_properties.json`，并填入以下内容

   1. 所有的`~/Qt5.13.0/5.13.0/mingw73_64/include`要替换成自己的实际安装路径
   
   2. `"compilerPath": "~\\bin\\g++.exe"`中也要替换成自己的实际编译器路径
   
   c_cpp_properties.json
   
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
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/Qt3DCore",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/Qt3DExtras",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/Qt3DInput",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/Qt3DLogic",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/Qt3DQuick",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/Qt3DQuickAnimation",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/Qt3DQuickExtras",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/Qt3DQuickInput",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/Qt3DQuickRender",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/Qt3DQuickScene2D",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/Qt3DRender",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtAccessibilitySupport",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtANGLE",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtBluetooth",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtBodymovin",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtCharts",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtConcurrent",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtCore",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtDataVisualization",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtDBus",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtDesigner",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtDesignerComponents",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtDeviceDiscoverySupport",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtEdidSupport",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtEglSupport",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtEventDispatcherSupport",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtFbSupport",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtFontDatabaseSupport",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtGui",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtHelp",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtLocation",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtMultimedia",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtMultimediaQuick",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtMultimediaWidgets",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtNetwork",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtNetworkAuth",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtNfc",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtOpenGL",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtOpenGLExtensions",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtPacketProtocol",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtPlatformCompositorSupport",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtPlatformHeaders",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtPositioning",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtPositioningQuick",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtPrintSupport",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtPurchasing",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtQml",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtQmlDebug",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtQuick",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtQuickControls2",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtQuickParticles",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtQuickShapes",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtQuickTemplates2",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtQuickTest",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtQuickWidgets",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtRemoteObjects",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtRepParser",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtScxml",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtScript",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtScriptTools",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtSensors",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtSerialBus",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtSerialPort",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtSql",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtSvg",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtTest",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtTextToSpeech",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtThemeSupport",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtUiPlugin",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtUiTools",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtVirtualKeyboard",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtVulkanSupport",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtWebChannel",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtWebSockets",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtWidgets",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtWindowsUIAutomationSupport",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtWinExtras",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtXml",
                   "~/Qt5.13.0/5.13.0/mingw73_64/include/QtXmlPatterns",
                   "${workspaceRoot}"
               ],
               "browse": {
                   "path": [
                       "~/Qt5.13.0/5.13.0/mingw73_64/include",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/Qt3DAnimation",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/Qt3DCore",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/Qt3DExtras",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/Qt3DInput",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/Qt3DLogic",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/Qt3DQuick",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/Qt3DQuickAnimation",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/Qt3DQuickExtras",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/Qt3DQuickInput",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/Qt3DQuickRender",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/Qt3DQuickScene2D",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/Qt3DRender",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtAccessibilitySupport",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtANGLE",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtBluetooth",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtBodymovin",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtCharts",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtConcurrent",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtCore",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtDataVisualization",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtDBus",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtDesigner",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtDesignerComponents",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtDeviceDiscoverySupport",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtEdidSupport",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtEglSupport",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtEventDispatcherSupport",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtFbSupport",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtFontDatabaseSupport",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtGui",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtHelp",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtLocation",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtMultimedia",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtMultimediaQuick",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtMultimediaWidgets",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtNetwork",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtNetworkAuth",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtNfc",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtOpenGL",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtOpenGLExtensions",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtPacketProtocol",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtPlatformCompositorSupport",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtPlatformHeaders",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtPositioning",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtPositioningQuick",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtPrintSupport",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtPurchasing",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtQml",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtQmlDebug",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtQuick",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtQuickControls2",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtQuickParticles",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtQuickShapes",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtQuickTemplates2",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtQuickTest",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtQuickWidgets",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtRemoteObjects",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtRepParser",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtScxml",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtScript",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtScriptTools",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtSensors",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtSerialBus",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtSerialPort",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtSql",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtSvg",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtTest",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtTextToSpeech",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtThemeSupport",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtUiPlugin",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtUiTools",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtVirtualKeyboard",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtVulkanSupport",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtWebChannel",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtWebSockets",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtWidgets",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtWindowsUIAutomationSupport",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtWinExtras",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtXml",
                       "~/Qt5.13.0/5.13.0/mingw73_64/include/QtXmlPatterns",
                       "${workspaceRoot}"
                   ]
               },
               "compilerPath": "~\\bin\\g++.exe",
               "cStandard": "c11",
               "cppStandard": "c++17",
               "configurationProvider": "vector-of-bool.cmake-tools",
            "compileCommands": "${workspaceFolder}/build/compile_commands.json"
           }
       ]
   }
   ```
   



## 3. 配置CMakeLists.txt文件

1. 在根目录下创建CMakeLists.txt，并填入以下内容

   ```cmake
   # 设置cmake版本
   cmake_minimum_required(VERSION 3.0)
   # 设置项目名称
   project(Animation)
   # 添加项目路径
   add_subdirectory(src)
   ```

2. 

3. 

