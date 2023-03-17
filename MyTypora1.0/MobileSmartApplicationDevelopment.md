# Learning Materials

1. Android Developer Website

	https://developer.android.google.cn/

2. Kotlin Website

	https://kotlinlang.org/

3. Google website: Kotlin learning resources

	https://developer.android.google.cn/kotlin

# Get Started!

- 创建新的project建议放在D盘
- 选择5.0（兼容大部分用户）

创建虚拟机和实体机：

1. 点击右上角的Device Manager

![微信图片_20230302102637](C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230302102637.png)

2. 上部可以选择虚拟机和实体机（Virtual and Physical）

	<img src="C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230302103512.png" alt="微信图片_20230302103512" style="zoom:33%;" />

3. 需要创建点击Create device即可

## Basic Element Introduction

### MainActivity.kt

```
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
    }
}
```

在MainActivity.kt中：

语句

```
setContentView(R.layout.activity_main)
```

用于连接Kotlin和布局文件

Kotlin用来写逻辑，页面的布局由布局文件负责

### Gradle

Gradle和Gradle的Android插件提供了一种灵活的方式来编译、构建和打包你的Android应用程序或库。

<img src="C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230309102110.png" alt="微信图片_20230309102110" style="zoom:50%;" />

（重要配置文件）



# Kotlin

Kotlin可以在java虚拟机（JVM）使用（两种语言兼容）

Java和Kotlin：

<img src="C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230309090705.png" alt="微信图片_20230309090705" style="zoom: 50%;" />

## Kotlin Basis

### 不可更改/可更改变量

<img src="C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230309092004.png" alt="微信图片_20230309092004" style="zoom: 50%;" />

（val：不可改，只读的变量。**必须设置初值**。如果更改将会出现编译错误）

<img src="C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230309092905.png" alt="微信图片_20230309092905" style="zoom: 33%;" />

（var：可更改的变量。建议使用val，必要时才使用var）

### 空指针的安全错误

Kotlin不允许将变量设置为空（编译错误）

<img src="C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230309093057.png" alt="微信图片_20230309093057" style="zoom:50%;" />

### Kotlin中?的使用

例

<img src="C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230309093901.png" alt="微信图片_20230309093901" style="zoom: 50%;" />

其中String后的问号：函数输入值可以为空

Int后的问号：函数输出值可以为空

与上代码等同效果的代码：

<img src="C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230309093905.png" alt="微信图片_20230309093905" style="zoom:50%;" />

其中

```kotlin
...
	return str?.length
```

如果输出值是空值，则不执行str.length

与上代码等同效果的代码：

<img src="C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230309093908.png" alt="微信图片_20230309093908" style="zoom:50%;" />

如果输出值不为空，则执行str.length；如果输出值为空，则输出0。

### 占位符实现字符串拼接

占位符$

<img src="C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230309095913.png" alt="微信图片_20230309095913" style="zoom:50%;" />

与上代码等同效果的代码：

![微信图片_20230309095916](C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230309095916.png)

### Kotlin中的类

#### 数据类

#### 类的性质

get和set方法

### 扩展

扩展什么？扩展系统已经实现的类

链式调用：string.func1.func2. ... .funcN

### lambda表达式

```
({it -> it > 2})
```

提取大于二的值







# Tasks in class

2023.2.23 Homework

1. 安装Android Studio
2. 回答砺儒云平台的问题
3. The tasks of the first phase

2023.3.2Homework

1. 安装Android Studio
2. 做练习1.03（看ppt）



