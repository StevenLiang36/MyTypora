# Introduction

## What is Django？

Django是一个开放源代码的Web应用框架，由Python写成。

采用了MTV的框架模式，即模型M，视图V和模版T：

![微信图片_20230225164248](C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230225164248.png)

Django概念图：

<img src="C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230225165645.png" alt="微信图片_20230225165645" style="zoom:50%;" />

- Django用于前端的开发。



## 默认项目（目录）介绍

1.  manage.py

	<img src="C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230225162527.png" alt="微信图片_20230225162527" style="zoom: 50%;" />

	项目管理、启用项目、创建app、数据管理。

2. asgi.py与wsgi.py

	<img src="C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230225162841.png" alt="微信图片_20230225162841" style="zoom:50%;" />
	
	接收网络请求

3. urls.py

	<img src="C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230225163355.png" alt="微信图片_20230225163355" style="zoom:50%;" />
	
	记录路径URL与python函数的对应关系
	
	### 什么是url？
	
	在WWW上，每一信息资源都有统一的且在网上的地址，该地址就叫URL（Uniform Resource Locator, 统一资源定位器），它是WWW的统一资源定位标志，就是指网络地址。

4. settings.py

	<img src="C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230225163618.png" alt="微信图片_20230225163618" style="zoom:50%;" />
	
	项目的配置文件

# Apps

## 什么是App？

我的理解是：App相当于是**功能模块**。

它可以用来实现不同的功能（例如用户管理、订单管理、后台管理、网站、API等等），且相互独立（可以有独立的表结构、函数、HTML模板等等）

## 如何创建App？

```Terminal
python manage.py startapp app名字
```

例：

```Terminal
python manage.py startapp app01
```

回车后会在与djangoProject文件夹同级的地方创建一个叫app01的文件夹

## App组件说明

1. **models.py**

	【重要】对数据库进行操作

2. **views.py**

	【重要】执行URL所要调用的函数需要写在这

3. tests.py

	单元测试

4. admin.py

	django默认提供了admin后台管理的功能

5. apps.py

	app启动类

6. migrations

	数据库的字段变更

## App注册

创建App后还需要对其进行注册

注册位置位于settings.py中的INSTALLED_APPS：

<img src="C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230225211252.png" alt="微信图片_20230225211252" style="zoom:50%;" />

如何注册？

1. 打开对应App中的app.py，里面有一个类，复制其类名

2. 回到上图注册位置，在最后加入以下代码：

	```
	'App名.apps.类名'
	```
	
	例：
	
	```
	'app01.apps.App01Config'
	```
	
	<img src="C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230225211939.png" alt="微信图片_20230225211939" style="zoom:50%;" />

# 上手django项目

如何启动一个django项目？

步骤如下：

1. 确保App已经注册（注册教程在上）

2. 在**urls.py**编写URL和视图函数的对应关系

	找到urls.py中的urlpatterns，在里面编写对应关系
	
	```
	path('url',函数),
	```
	
	例：
	
	```
	path('index/',views.func),
	```
	
	（index为url名称，func为函数名称。皆任取。）
	
	<img src="C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230225214500.png" alt="微信图片_20230225214500" style="zoom:50%;" />
	
	**注意要从相应App中引入views**！！！

3. 在**views.py**中编写视图函数

  打开views.py，在里面编写函数

  例：

  ```python
  from django.shoutcuts import render, HttpResponse
  
  def func(request):
  	return HttpResponse("欢迎使用")
  ```

  （request为函数的默认参数。import的HttpResponse为页面回应）

  

  **当用户访问www.xxx.com/index/时，将会自动调用func函数。在此例中，将会弹出写有“欢迎使用”的页面。**

  （用户访问网址，便可看到结果）

  

4. 启动django项目

	两种方式启动django项目：
	
	1. pycharm启动按键
	
	2. 命令行启动
	
	```Terminal
	python manage.py runserver
	```


总结：

写一个页面的基本步骤：

1. 在urls.py中编写url与函数的对应关系

	```python
	urlpatterns = [
	    path(...)
	    path(...)
	    .
	    .
	    path(...)
	]
	```

2. 在views.py中编写函数

	```python
	def func1(request):
		...
	def func2(request):
		...
	.
	.
	def funcN(request):
		...
	```

后续再写页面，开发本质上最常见的操作步骤就是上面两步：url编写对应关系+views编写函数（二者一一对应）。

## templates模板

当你想让用户打开网址时看见的是一个HTML页面，而不是普通的文本，那么要进行如下操作：

views.py中所编写的函数则需要：

```
return render(request,'XXX.html')
```

例：

返回用户列表的HTML

```python
def user_list(request):
    return render(request,'user_list.html')
```

自此在render的内部会帮助你寻找user_list.html文件，并将文件内容读取到内存，然后反馈给用户。

**那么，django会在哪里找这个user_list.html文件呢？**

**默认会在App的目录下的templates的目录下寻找这个HTML文件**

**（其实是根据App的注册顺序，逐一去它们的templates文件夹中寻找）**

在App目录下创建一个templates文件夹，在文件夹中放置所要使用的HTML文件

![Snipaste_2023-02-26_11-02-57](C:/Users/StevenLiang/Pictures/Camera Roll/Snipaste_2023-02-26_11-02-57.png)

### 特殊情况

有不少开发者会在settings.py中的TEMPLATES中：

```python
'BACKEND': ...
'DIRS':[os.path.join(BASE_DIR,'templates')],
'APP_DIRS': ...
...
```

那么render寻找HTML文件的步骤会有变化：

它会先在根目录的templates的文件夹中寻找文件：

1. 根目录的templates的文件夹
2. （如果根目录templates的文件夹没有对应HTML文件）按照注册顺序的App中的templates的文件夹中寻找

如果没有编写以上代码，则会先在App中的templates的文件夹中寻找，即没有第一步，直接执行第二步。

## 静态文件

在开发过程中：

- CSS
- js
- 图片

一般都会当作静态文件处理

同样在django框架中，HTML中所涉及用到的CSS、js等静态文件都不能乱放。

那么静态文件需要放在哪里呢？

静态文件需要放在App目录下的static文件夹中。一般来说static文件夹可以再细分为图片、CSS、js等文件夹。

<img src="C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230226122847.png" alt="微信图片_20230226122847" style="zoom:80%;" />

# Django模板语法

在本质上是在HTML中写一些占位符，由数据对这些占位符进行替换和处理

## HTML使用外部数据

这里的外部数据可以是数据库的数据，也可以是其他要在HTML之外获取的数据（这些数据可以是不断变化的，并未像HTML中标题一样完全定死，可以理解为HTML中的**变量**，只不过这些变量是从外部获取的）

下面详细说明：

首先将HTML页面创建好（设置对应关系，编写函数）

函数基本格式：

```python
def func(request):
    item1 = 字符串
    item2 = 列表
    .
    .
    itemN = 字典
    return render(request,'xxx.html',                                       {"n1":item1,"n2":item2,...,"nN":itemN})
   
```

### 照搬数据

例1：

定义函数：

```python
def squad(request):
    name = "狗官"
    return render(request,'squad.html',{"n1:name"})
```

此处设置为n1对应name，而name就是狗官

对应HTML中：

```html
...
<body>
    <h1>战术小队里的兵种</h1>
    <div>{{n1}}</div>
</body>
...
```

页面效果：

```
战术小队里的兵种
狗官
```

当想用模板显示一个单独的值的时候，使用**两个花括号** {{}}

例2：

```python
def squad(request):
    medic = ["医疗1","医疗2"]
    return render(request,'squad.html',{"n1:medic"})
```

对应HTML中：

```html
...
<body>
    <h1>战术小队里的兵种</h1>
    <div>{{n1}}</div>
</body>
...
```

页面效果：

```
战术小队里的兵种
["医疗1","医疗2"]
```

当是如例子中的列表时，双花括号依然**原封不动**将列表打印

那么如何遍历列表中的数据，让其一个一个打印出来呢？

### 遍历列表数据

上面例2的函数不动，修改HTML

1. 索引

	```html
	<body>
	    <h1>战术小队里的兵种</h1>
	    <div>{{n1.0}}</div>
	    <div>{{n1.1}}</div>
	</body>
	```
	
	页面效果：
	
	```
	战术小队里面的兵种
	医疗1
	医疗2
	```
	
	注意：此处并没有像python那样用[ ]来索引列表中的数据而是用.
	
	（非n1[0]而是n1.0）

2. 循环

	```html
	<body>
	    <h1>战术小队里的兵种</h1>
	    <div>
	        {% for item in n1 %}
	        	<span>{{ item }}</span>
	        {% endfor %}
	    </div>
	</body>
	```
	
	其中注意for循环的格式 {%   %}
	
	endfor表示for循环的结束
	
	页面效果：
	
	```
	战术小队里面的兵种
	医疗1 医疗2
	```

### 处理字典数据

函数：

```python
def squad(request):
    captain = {"name":"Steven","age":"20"}
    return render(request,'squad.html'，                                     {"n1:captain"})
```

1. 索引

	HTML:
	
	```html
	<body>
	    <h1>战术小队的队长</h1>
	    <div>{{n1.name}}</div>
	    <div>{{n1.age}}</div>
	</body>
	```
	
	页面效果：
	
	```
	战术小队的队长
	Steven
	20
	```

2. 循环

	HTML:
	
	循环所有的key：
	
	```html
	<body>
	    <h1>战术小队的队长</h1>
	    <div>
	        {% for item in n1.key %}
	        	<span>{{ item }}</span>
	        {% endfor %}
	    </div>
	</body>
	```
	
	循环所有的value：
	
	```html
	<body>
	    <h1>战术小队的队长</h1>
	    <div>
	        {% for item in n1.value %}
	        	<span>{{ item }}</span>
	        {% endfor %}
	    </div>
	</body>
	```
	
	循环key+value：
	
	```html
	<body>
	    <h1>战术小队的队长</h1>
	    <div>
	        {% for k,v in n1.items %}
	        	<span>{{ k }} = {{ v }}</span>
	        {% endfor %}
	    </div>
	</body>
	```
	
	页面效果：
	
	```
	战术小队的队长
	name = Steven
	age = 20
	```


**注意：其中列表和字典都可以嵌套，与python中嵌套的索引机制差不多。**

## if...else（elif）

例：

函数：

```python
def person(request):
    name = Steven
    return render(request,'person.html'，                                     {"n1:name"})
```

HTML：

```html
...
<body>
    {% if n1 == "Steven" %}
        <h1>哈哈哈哈哈</h1>
    {% elif n1 == "John" %}
        <h1>嘟嘟嘟嘟嘟</h1>
    {% else %}
        <h1>顶顶顶顶顶</h1>
    {% endif %}
</body>
...
```

页面效果：

```
哈哈哈哈哈
```

## 视图函数的render内部

![微信图片_20230226210948](C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230226210948.png)

1. 读取含有模板语法的HTML文件
2. 内部进行渲染（执行模板语法并替换数据），得到只有HTML标签的字符串
3. 将渲染（替换）完成的字符串返还给用户浏览器

# 请求和响应

**什么是GET和POST请求？？？？**

**用户是在浏览器发送请求的**

浏览器向网站可以发送两种请求：GET和POST

```python
import ... HttpResponse,redirect

def func(request):
#request是一个对象，封装了用户发送过来的所有请求相关的数据
	print(request.method) #获取请求方式（用户提交数据的方式）
                          #得到GET或POST
    print(request.GET) #在URL上传递值
    print(request.POST) #通过请求体中提交数据
    
    return HttpResponse("返回内容") #【响应】将字符串内容返回给                                      请求者
	return render(...) #【响应】亦可以返回HTML内容给请求者
    return redirect("url") #【响应】让浏览器重定向到其他页面
```

详解一下：

1. request.GET

	```python
	def func(request):
	    print(request.GET)
	```
	
	在url输入数据，通过request.GET命令可以在pycharm得到
	
	例在url：
	
	```
	...你的网站地址.../func/?n1=123&n2=456
	```
	
	回车后可以在pycharm接收到数据（获取在url接收到的数据）：
	
	```
	<QueryDict:{'n1':['123'],'n2':['456']}>
	```

2. redirect("url")

	浏览器向django发送请求，django告诉浏览器去哪里找，浏览器自己再去给相应网址发送请求，网址回应。
	
	**重定向**：
	
	类似于“我没有，你去别的地儿吧”
	
	<img src="C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230228210925.png" alt="微信图片_20230228210925" style="zoom: 50%;" />

## 帮助理解GET和POST请求

- GET最常用于向服务器查询信息；POST通常用于向服务器发送应该被保存的数据。
- 浏览器和服务器的交互是通过 HTTP 协议执行的，而 get 请求和 post 请求也是 HTTP 协议中的两种方法。
- GET请求一般去获取数据（亦可提交），POST请求一般去提交数据。
- GET请求是不安全的，因为在传输过程中，**数据被放在请求的 url 中**（如详解中的例子。数据放在了url的末端）；POST请求的所有操作对用户来说一般都是不可见的，其通过request body传递参数。
- GET请求在URL中传送的参数是有长度限制的，而POST没有。

# 数据库操作

Django开发操作数据库更简单，内部提供了ORM框架

可以理解为ORM帮助我们**翻译**（翻译为SQL语句以帮助操作数据库）

![微信图片_20230307210809](C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230307210809.png)

## ORM

它可以做什么？

- 创建、修改、删除数据库中的表。（无法创建数据库）
- 操作表中的数据

以上两件事都不需要你写SQL语句

## 创建数据库

两种方式：

- 终端

	```
	create database 数据库名 DEFAULT CHARSET utf8 COLLATE utf8_general_ci;
	```

- XAMPP

	创建方式可见DatabaseSystem中的笔记

	可先创建一个空的数据库，里面的表可以通过django添加

## Django连接数据库

在settings.py文件中进行配置和修改：

![微信图片_20230308215854](C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230308215854.png)

原本在settings.py的DATABASES是如注释部分所示（sqlite3是另外一种数据库形式）。

因为我们需要使用mysql，所以需要如图修改（未注释部分）

## ORM类创建表

（利用django内部功能在新的数据库创建表）

打开app中的model.py，在里面进行创建：

<img src="C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230308220333.png" alt="微信图片_20230308220333" style="zoom:50%;" />

如图

![微信图片_20230308220438](C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230308220438.png)

定义了一个类，类名叫Users（这其实就是所要创建的表的名字）

这个表包含什么元素？name和passward。它们的最大长度分别设置为32和64

操作完这步后，需要执行两项命令，打开终端：

```
python manage.py makemigrations
```

```
python manage.py migrate
```

两项命令执行后，原本空的数据库将添加了新表：

<img src="C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230308220906.png" alt="微信图片_20230308220906" style="zoom:50%;" />

按道理来说不是只创建了app01_users这一个表吗？为什么多创建了这么多其他表？

原因是django中默认注册了很多其他的app：

<img src="C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230308221216.png" alt="微信图片_20230308221216" style="zoom:50%;" />

## Django操作表

- 创建表

	在app的model.py中添加类便可，添加完成后再输入上面的两行命令

- 删除表

	同样道理，只需要在app的model.py中将相应的类注释掉（删去）即可，再输入上面的两行命令 

- 修改表

	在app的model.py对应位置更改表的内容即可，修改后输入上面的两行命令

	当在原有表（表中已有数据）中新增列时（新增一个表头，元素），django会给你两种选项：

	1. 手动添加默认值（你新建的那一列的默认值）

	2. 退出后在model.py中添加默认值，例

		```
		age = models.IntegerField(default=20)
		data = models.IntegerField(null=True,blank=True)
		```
		
		（添加age的一列并且默认值设置为20; data可以为空）


## Django操作表中数据

- 新建数据

	上述在model.py中的操作只是将数据库中的表建了出来，但里面仍然没有数据

	那么如何添加数据呢？

	例：

	在djangoProject的urls.py中添加条路径：

	<img src="C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230309202145.png" alt="微信图片_20230309202145" style="zoom:50%;" />

	 views.py中添加函数：

	![微信图片_20230309202323](C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230309202323.png)

	其中，添加数据的语句是（重要）：

	```
	Users.objects.create(name="Steven",passward="123456")
	```

	(语义是在Users的表中添加name=Steven和passward=123456的数据。HttpResponse只是验证确认命令是否执行)

	

	运行django项目：

	![微信图片_20230309202705](C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230309202705.png)

	打开网页：

	![微信图片_20230309202931](C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230309202931.png)

	（语句成功运行）

	再打开数据库检查是否有新数据加入：

	<img src="C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230309203032.png" alt="微信图片_20230309203032" style="zoom: 67%;" />

	成功！

- 删除数据

	大部分步骤相同，只需要在写函数时，写上以下语句：

	```
	Users.object.filter(id=1).delete()
	```

	filter为选择器，选择id为1的数据并进行删除

	```
	Users.objects.all().delete()
	```

	将表中的所有数据删除

- 获取数据

	获取表中所有数据：

	```python
	data_list = Users.objects.all()
	for obj in data_list:
	    print(obj.id, obj.name, obj.passward)
	```

	获取行数据：

	```python
	row_obj=Users.objects.filter(id=1).first()
	print(row_obj.id,row_obj.name,row_obj.passward)
	```

- 更新数据

	更新表中所有数据：

	```
	Users.objects.all().update(passward=123)
	```

	（表所有的passward数据更新为123）

	更新所选择的数据：

	```
	Users.objects.filter(id=1).update(passward=123)
	
	Users.objects.filter(name="Steven").update(passward=123)
	```

	

# 案例：用户管理

## 在HTML中查看数据库数据

1. 于url.py添加路径

	<img src="C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230311215631.png" alt="微信图片_20230311215631" style="zoom: 50%;" />

2. 于views.py添加函数

	![微信图片_20230311215540](C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230311215540.png)
	
	data_list用于获取数据库所有数据

3. 编写展示数据的HTML页面

	![微信图片_20230311215929](C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230311215929.png)
	
	注意上面所学的django HTML语法，将数据库中的数据通过HTML动态呈现

4. 运行django查看展示页面

	![微信图片_20230311214908](C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230311214908.png)
	
	查看数据库，数据相同！
	
	![微信图片_20230311215142](C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230311215142.png)

## 在HTML添加数据进入数据库

我打算直接贴近大创项目进行案例实践

使用已经写好了的系统html：homePage.html进行尝试。虽然说只写了个登入界面，按照道理是用来验证数据库信息（看看数据库里有没有这个用户），而不是添加用户（添加用户应该在注册页面）。但为了方便，直接用登入界面尝试实现在HTML添加用户

示范步骤如下：

1. 于url.py添加路径

	![微信图片_20230311212650](C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230311212650.png)
	
	（homePage即为我要打开的HTML的名字。userAdd即为我在views.py里需要写的函数）

2. 于views.py添加函数

	![微信图片_20230311213657](C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230311213657.png)
	
	import的redirect用于跳转页面

3. HTML页面和css文件

	![微信图片_20230311214116](C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230311214116.png)
	
	注意圈出来的地方（表单怎么写？有哪些东西需要添加？），还需要关注HTML文件和CSS文件的相对位置

4. 运行并添加用户数据

	<img src="C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230311214533.png" alt="微信图片_20230311214533" style="zoom: 33%;" />
	
	（这里不知道为什么CSS不管用）

5. 查看结果

	跳转成功！
	
	![微信图片_20230311214908](C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230311214908.png)
	
	（这是我根据视频P18前半部分写好的展示数据库数据页面）
	
	此处序号问题忽略！
	
	再看看数据库：
	
	![微信图片_20230311215142](C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230311215142.png)
	
	也没问题！

## 删除数据库中的数据

1. 于url.py添加路径

	![微信图片_20230313152220](C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230313152220.png)

2. 于views.py添加函数

	![微信图片_20230313152437](C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230313152437.png)

3. 运行django后编辑网址以删除用户

	原数据库：
	
	![微信图片_20230313152624](C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230313152624.png)
	
	此时选择删除id为5的用户数据：
	
	![微信图片_20230313152739](C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230313152739.png)
	
	注意网址后部圈起来的地方，此处是设置删除id为多少的数据
	
	如果要删除id为1的数据，则在等号后写数字1
	
	再看数据库：
	
	![微信图片_20230313153026](C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230313153026.png)
	
	删除成功！

那么问题就来了，如果每次删除数据都要在网址上写，那岂不是非常麻烦？

于是想到在**HTML网页上直接操作**，步骤如下：

1. 编写拥有删除操作的HTML网页（此处直接在原有的数据库表上添加操作功能）

	![微信图片_20230313154045](C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230313154045.png)

2. 于HTML页面删除用户

	<img src="C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230313154153.png" alt="微信图片_20230313154153" style="zoom:50%;" />
	
	删除成功！
	
	![微信图片_20230313154227](C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230313154227.png)

如果想删除后直接看到用户列表删除后的状态，可以在views.py的函数做修改：

![微信图片_20230313154515](C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230313154515.png)

删除后可直接看到操作更改后的用户列表

## 表结构分析

### 表头注解

利用CharField中的verbose_name的属性

![微信图片_20230313215623](C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230313215623.png)

### 表表关联

很多情况下我们要创建很多的表，表与表之间如何关联呢？

举个例子：

现在有两张表，第一张表为部门表，第二张为员工表

<img src="C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230313215138.png" alt="微信图片_20230313215138" style="zoom: 67%;" />

<img src="C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230313215141.png" alt="微信图片_20230313215141" style="zoom: 67%;" />

此时员工表中部门可以只写部门表相应部门的id，这样做是为了节省空间

那么具体是什么部门如何得知？（光看员工表并不能知道员工属于什么部门，毕竟只能看到部门id，要想知道只能对照着部门表看）那么此时需要的就是将两张表关联

有约束关联：

何为有约束关联？就是员工表中的部门id必须是部门表中存在的（上例只有三个部门，员工表中的部门id不能是10000，只能是1、2、3中的一个）

```python
class Department(models.Model):
    ...
class UserInfo(models.Model):
    ...
    department = models.ForeignKey(to="Department",to_field='id')
```

那么如果部门表中有部门要解散，相应的员工表中的部门信息会如何变化？

- 级联删除

	```python
	department = models.ForeignKey(to="Department",to_field='id',on_delete=models.CASCADE)
	```

- 置空

	```python
	department = models.ForeignKey(to="Department",to_field='id',  null=True,blank=True,on_delete=models.SET_NULL)
	```


### Django的代码约束

就拿性别来说明：性别就两种，可直接用1和2分别表示男和女，如何实现？

```python
gender_choices=(
	(1,"男"),
	(2,"女")
)
gender=models.SamllIntegerField(choices=gender_choices)
```

## 登录

![微信图片_20230316093000](C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230316093000.png)
