---
layout: post
title: javah的使用方式
categories:
- Programming
tags:
- android ndk javah
---

 
## javah的使用方式


1. javah在JDK/bin路径下，与java同路径；

2. 执行javah时需要在目标类的class的顶层包所在的目录（比如`bin/classes/com/example/hellojni/HelloJni.class`，就需要在classes目录）下执行，或者用参数`-classpath`指定到该目录，否则会报`错误: 找不到 'com.example.hellojni.HelloJni' 的类文件`。

3. javah不一定要用`.class`文件，也可以使用java源文件。

4. 对应Android代码，需要用`-bootclasspath`指定android.jar路径，例如：`-bootclasspath %ANDROID_SDK_HOME%\platforms\android-20\android.jar`，否则会报`错误: 无法访问android.app.Activity  找不到android.app.Activity的类文件`。

5. 默认生成的.h文件的位置是执行javah命令的目录，也可以用-d命令指定到其他目录位置。

6. 在Eclipse中配置外部工具时，Working Directory应该指定为期望生成.h文件的位置，Arguments应该填入：`-bootclasspath "${android_sdk_home}/platforms/android-20/android.jar" -classpath "${project_classpath}" ${java_type_name}`。





----
