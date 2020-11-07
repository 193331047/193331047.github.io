

【裕语言】是一基于java的扩展性脚本语言，丰富的类库定置简单快速开发你的应用程序，让开发过程变得娱乐化大众化。《裕语言》是由游改乐计算编程工程师 黄裕先生、宇恒先生 定制以及实现成型代码功能，其代码简单方便的编写体验是一大亮点，目前还会有更多强大的功能完善中。iApp是基于裕语言平台上运行的应用程序，全面向公众开放开放平台，任何有兴趣的人都可以参与开放设计自己的程序。

【3.0 iyu升级简介】
1. uigo代码必须加文件后缀，如 uigo("a.iyu") 或 uigo("a.ilua")。 否则将会闪退等。
2. uls必须正确的 输入界面宽度，输入界面高度。 否则界面列表可能异常。
3. 代码中双引号需进行转义，如 fw("%a.txt", "ab"cd") 修改成 fw("%a.txt", "ab\"cd")


【s 变量】
用法：

//申明一个变量，如果不赋值，系统将默认赋值 null
s a

申明事件局部变量
//可以赋数值
s a = 123
tw(a)

s 我是变量 = 123
tw(我是变量)

申明界面变量
//可以赋字符串
ss a = "123"
tw(ss.a)

申明全局变量
//可以赋其他变量
sss b = a
tw(sss.b)

区域介绍：
局部变量：服务于一个事件，当用户与界面发生交互时，产生一个事件，仅供于该事件的变量产生以及操作。
界面变量：生产界面变量后，同一个界面中的所有事件，均可对其进行操作。
全局变量：生产全局变量后，同一个应用中的所有事件，均可对其进行操作。

说明：
变量类似一个箱子，你可以把数据储存在里面，等需要的时候就取出来使用，可以改变它装你想要装的数据。裕语言中的变量是可以根据赋值，而且自动转换的，所以无需申明数据类型。

提示：
变量的定义规范， 以 “s、ss、sss”开头。 然后加上自己自定义的变量名，比如“abc、 nihao、sfw123、www_zzw”变量不允许全部为数字，不允许掺杂符号，请不要使用太长的变量名，不推荐使用中文作为变量名。

空值：
如果访问一个没有声明的变量，将返回“null”空值类型，这个不对等于字符的 'null'。
判断是否空值的例子:(这里我们不知道变量“abc”是否空值)
f(abc == null)
{
	syso("是null")
}

【// 或 /. ./ 注释语句】
用法
//这个是变量“a”它的值等于“1”
s a = 1
//这个是变量“b”它的值等于“2”
s b = 2

/.
大量代码注释方法
s c = 3
s d = 4

./


说明：
注释语句符号可以用“//”，以注释符号开头的正行，将会被代码执行器无视。通常用于给自己标示代码的含义

提示：
此注释语句可用于属性。

提示：
不支持代码尾部使用注释语句，注释行必须开头为注释符，举错误的例：

s a = 1 //这个是变量“a”它的值等于“1”
//这个是变量“b”它的值等于“2” s b = 2

【syso 打印】
用法：
syso("1314")
可以打印出数据，代码同等于 System.out.println("1314")，可以在测试时，选择 调试日志查看打印数据。

说明：
打包后，安装运行可以通过 Log Tag：iapp 进行监听数据。

【f 判断语句】
用法：
s a = 2
f(a == 1)
{
	syso("等于1")
}
else f(a == 2)
{
	syso("等于2")
}
else
{
	syso("等于其他")
}

s a = 1
s b = 1
f(a == b)
{
	syso("等于")
}
else
{
	syso("不等于")
}

s a = "nimei"
s b = "nimei"
f(a == b)
{
	syso("等于")
}
else
{
	syso("不等于")
}

s a = 1
s b = 2
f(!a == b)
{
	syso("等于")
}
else
{
	syso("不等于")
}

s a = 1
s b = 2
s c = 3
f(a < b && b < c)
{
	syso("等于")
}
else
{
	syso("不等于")
}

s a = 1
s b = 2
s c = 2
f(a == b || b == c)
{
	syso("等于")
}
else
{
	syso("不等于")
}

说明：
条件判断语句，用于两个值的比较，常用于判断值是否对等与数值的大小，判断数据需要同类型数据对比。表达式返回的“是”，那么将执行 { 代码 } 里面的代码。“否”将执行else后面的代码（不支持运算表达式，例：a+b=2）

支持运算符（返回 是 与 否）：
== 是否对等
!= 是否不等于
>= 是否大于或等于
<= 是否小于或等于
> 是否大于
< 是否小于
?* 字符串开通是否相同
*? 字符串结尾是否相同
? 字符串是否被包含
上面三个举例：
s a = "abcdef"
f(a ?* "abc") 返回“是”
f(a *? "def") 返回“是”
f(a ? "cde") 返回“是”

支持逻辑运算符：
|| 或者
&& 并且
! 反意

【w 循环】
用法：
//这将循环99次
s a = 99
w(a > 0)
{
syso(a)
s(a - 1, a)
}

说明：
条件循环语句，比较值的变化，然后进行循环执行 { 代码 } 里面的代码。当条件为“否”的时候会停止循环，条件“是”的话，将一直循环执行。
支持运算符（返回 是 与 否）：（跟 f 语句 一样，请参考）

【for 循环】
用法：
for(1; 20)
{
	syso("循环20次")
}

s a = 1
s b = 10
for(a; b)
{
	syso("循环10次")
}

说明：
参数可以给予另个参数，一个为初始循环的值，一个是最大循环值。


【t 新线程】
用法：
t()
{
	syso("新线程里执行代码")
}

说明：
启用新线程，去执行一些需要执行很久的代码。比如把下载文件，获取网页源码，大量的文件操作，可以放入新线里执行。这里线程的概念，启用新的线程帮你处理代码，这样不会影响到主线程。

【ssj 设置或修改控件事件代码】
用法：
s id = 3
ssj(id, "clicki")
{
tw("ok")
}

说明：
输入控件Id，输入事件类型，并将事件代码填写在 { 中 }，动态控件将触发该事件代码。

事件类型：
clicki=单击事件
touchmonitor=触屏监听事件
press=触屏长按事件
keyboard=键盘触发事件
pressmenu=触屏长按菜单事件
editormonitor=框编辑监听事件
ontextchanged=文本内容已改变
beforetextchanged=文本内容改变之前
aftertextchanged=文本内容改变之后
focuschange=获得焦点事件
onscrollstatechanged=滚动状态已改变
onscroll=滚动
clickitem=单击项目事件
onprogresschanged=加载过程进度改变
shouldoverrideurlloading=加载网址之前
ondownloadstart=文件下载事件
onpageselected=滑动切换界面事件
onpagescrolled=滑动切换界面过程
onpagescrollstatechanged=滑动操作过程
ondrawerclosed=侧滑关闭事件
ondraweropened=侧滑展示事件
onoptionsitemselected=项目选择
onitemselected=选择项目事件


【tw 提示】
用法：
tw("你好")

//设置参数1：显示的时间长久；0：显示的时间短暂；\n为换行的意思，其他地方通用
tw("你好\n吗？", 1)

说明：
用于提醒用户，界面显示时长大约为 2秒钟。弹出代码中的文字，来提醒用户。

【fd 删除文件】
用法：(将删除SD卡根目录的abc.zip文件)
s a = "%abc.zip"
fd(a, b)
tw(b)

说明：
用于删除指定的文件，是否成功返回数据：true或 false

提示：同时将创建变量“b”，作为记录返回的值。（通用于下咧）

【fe 文件是否存在】
用法：(将判断SD卡根目录的abc.zip文件是否存在)
s a = "%abc.zip"
fe(a, b)
tw(b)

说明：
用于判断指定的文件存在，是否存在返回数据：true或 false

【fs 文件大小】
用法：(将获取SD卡根目录的abc.zip文件占用的大小)
s a = "%abc.zip"
fs(a, b)
tw(b)

说明：
用于判断指定的文件存在，是否存在返回数值单位(字节)，若获取失败将返回 “-1”。
转换为KB：
s a = "%abc.zip"
fs(a, b)
s(b/1024, b)
tw(b)

转换为MB：
s2(b/1024/1024, b)
//保留所有小数
sn(b/1024/1024, b2)

【fr 读取文本】
用法：(将读取SD卡根目录的abc.txt文件里面的内容)
s a = "%abc.txt"
fr(a, b)
tw(b)

s a = "%abc.txt"
s b = "utf-8"
fr(a, b, c)
tw(c)

说明：
用于读取文本文件的数据内容。

【fc 复制文件】
用法：（在SD卡根目录abc.txt文件拷贝一个新的副本至abc2.txt）
s a = "%abc.txt"
s b = "%abc2.txt"
fc(a, b, c)

//设置重复不覆盖
s c = false
fc(a, b, c, d)

说明：
用于复制文件，创建一个新的副本文件。是否成功返回数据：true或 false


【fw 写入文本】
用法：(将文本数据写入至SD卡根目录的abc.txt文件里面)
s a = "%abc.txt"
s b = "我是一个txt文件的内容"
fw(a, b)

s a = "%abc.txt"
s b = "我是一个txt文件的内容"
s c = "utf-8"
fw(a, b, c)

说明：
用于写入文件。

【fl 文件列表】
用法：（获取一个目录的文件列表）
s a = "%dir"
fl(a, b)
for(c; b)
{
	syso(c)
}

//仅获取文件夹
s a = "%dir"
fl(a, true, b)
for(c; b)
{
	syso(c)
}

//仅获取文件
s a = "%dir"
fl(a, false, b)
for(c; b)
{
	syso(c)
}

说明：上面例子是获取sd卡根目录文件夹“dir”里面的所有子目录以及文件，并获取结果传入变量“b”，并用for循环，来读取变量“b”里面的列表数据，并把列表数据复制给变量“c”，其中代码会自动创建并赋值好变量：b、c

提示：
看似有些复杂，理解了就简单了， 这里的变量“b”类型是一个数组，里面包含了一个数据列表。通过for循环可以顺序读取这个列表。并每次循环把每列的数据赋值给变量“c”

【ft 转移文件】
用法：（将SD卡根目录的abc.txt转移至abc3.txt）
s a = "%abc.txt"
s b = "%abc3.txt"
ft(a, b, c)
tw(c)

说明：
用于转移文件。是否成功返回数据：true或 false

【fdir 获取SD卡根目录路径】
用法：（获取根目录路径并赋值至变量“a”）
//获取根目录
fdir(a)
tw(a)

//获取目录的绝对路径
s a = "%dir"
fdir(a, b)
tw(b)

说明：
通过获取根目录路径，就可以计算文件的绝对路径。

【fuz 解压zip部分文件】
用法：（将根目录文件abc.apk压缩包里的AndroidManifest.xml文件，解压到根目录AndroidManifest2.xml）
s a = "%abc.apk"
s b = "AndroidManifest.xml"
s c = "%AndroidManifest2.xml"
fuz(a, b, c, d)
tw(d)

//解压文件遇到重复不覆盖
s a = "%abc.apk"
s b = "AndroidManifest.xml"
s c = "%AndroidManifest2.xml"
s d = false
fuz(a, b, c, d, e)
tw(e)

说明：
通过上面代码可以实现压缩包解压部分的文件，并返回赋值至变量“d”解压文件的数量。

【fuzs 解压整个zip】
用法：(将根目录文件abc.apk压缩包解压至根目录文件夹abcdir，会自动创建)
s a = "%abc.apk"
s b = "%abcdir"
fuzs(a, b, c)
tw(c)

//解压文件遇到重复不覆盖
s a = "%abc.apk"
s b = "%abcdir"
s c = false
fuzs(a, b, c, d)
tw(d)

说明：
通过上面代码将解压整个压缩包至指定文件，并赋值至变量“c”，是否成功返回数据：true或 false

【fj 压缩文件或文件夹至zip】
用法：
s a = "%adc.txt"
s b = "%abc.zip"
fj(a, b, c)
tw(c)

//不去除根目录
s a = "%adc.txt"
s b = "%abc.zip"
s c = false
fj(a, b, c, d)
tw(d)

说明：
压缩文件。返回赋值数据：true 或 false

【fo 打开文件】
用法：（将根目录打开安装abc.apk文件）
s a = "%abc.apk"
fo(a)

说明：
可以调用系统工具打开不同的文件。

【s+-*/% 运算方式】
用法：
s a = 2

//加法例子赋值a=4
s+(2, a)
//减法例子赋值a=3
s-(5, a)
//乘法例子赋值a=6
s*(3, a)
//除法例子赋值a=4
s/(8, a)
//求余例子赋值a=2
s%(5, a)

//其他用法

//加法例子赋值a=7
s+(2, 5, a)

//乘法例子赋值b=8，保留小数
s*(4, a, true, b)


说明：
此方法的效率高于 s计算表达式、sb计算表达式。 在循环数据运行时，是受到推荐的用法。

【s 计算表达式】
用法：（用于计算表达式）
s a = 12
s b = 13
s(a + b, c)
//将提示：25
tw(c)

s a = 60
s b = 14
s(a / (b + 12), c)
//将提示：2 （自动去除了小数）
tw(c)

说明：
用于计算数据表达式，不支持逻辑表达式计算。

【s2 计算表达式】
说明：
功能跟上面的一样，但这个会保留2位小数。

【sn 计算表达式】
说明：
功能跟上面的一样，但保留所有小数。

【ss 变量相加】
用法：
s a = "123"
s b = "789"
ss(a + "456" + b, c)
//将提示：123456789
tw(c)

说明：
将字符串数据相连，并赋值至变量“c”。

【sr 替换字符】
用法：
s a = "123456789"
s b = "456"
s c = "."
sr(a, b, c, d)

//将提示：123.789
tw(d)

//支持正则表达式
//sr(a, b, c, true, d)

说明：
用于替换字符

【sj 截取字符】
用法：
s a = "123456789"
s b = "34"
s c = "8"
sj(a, b, c, d)
//将提示：567
tw(d)

//从头部开始截取
sj(a, null, c, d)
tw(d)

//截取到尾部
sj(a, b, null, d)
tw(d)


说明：
用于截取数据部分字符

【sl 数据数组】
用法：
s a = "12;12;12;12;12"
s b = ";"
sl(a, b, c)

//可以支持正则表达式；例子看（注意说明）
//sl(a, b, true, c)

for(d; c)
{
//将打印5次：12
	syso(d)
}

说明：
将把变量“a”的字符串，切割成一个数组，以字符“.”为分割字符。并用循环顺序打印出数据。

注意：
如果支持正则表达式数据数组，上例子的 s b = ";" 其内的值。需要转义的特殊字符 “$()*+.[]?\^{},|”

支持正则的特殊字符转义方法：
如：
s a = "12|a$12|a$12|a$12|a$12"

//关键分割字符串如果包含特殊字符，需要在每个特殊字符前面增加“\”
s b = "\\|a\\$"
sl(a, b, true, c)

for(d; c)
{
//将打印5次：12
	syso(d)
}

【siof 获取字符位置】
用法：
s a = "123456789"
s b = "3"
s c = 0
siof(a, b, c, d)
//将提示：2
tw(d)

s a = "123456789"
s b = "3"
siof(a, b, c)
//将提示：2
tw(c)
说明：
从前面向后面进行匹配。字符位置以0计算，若无数据找到将返回 -1

【slof 获取字符位置】
用法：
s a = "123456789"
s b = "4"
s c = 8
slof(a, b, c, d)
//将提示：3
tw(d)

s a = "123456789"
s b = "4"
slof(a, b, c)
//将提示：3
tw(c)

说明：
从后面向前面进行匹配。字符位置以0计算，若无数据找到将返回 -1


【ssg 截取字符】
用法：
s a = "abcdefghijk"
ssg(a, 2, 6, b)
//将提示：cdef
tw(b)

s a = "abcdefghijk"
ssg(a, 6, b)
//将提示：ghijk
tw(b)

说明：
根据字符的位置进行截取字符，若失败将变量“b”赋值 null


【slg 获取字符长度】
用法：
s a = "123456789"
slg(a, b)
//将提示：9
tw(b)

说明：
顾名思义。

【strim 去除头尾空格】
用法：
s a = "   123456789 "
strim(a, b)
//将提示:123456789
tw(b)

说明：
常用于去除后进行判断头尾字符。

【slower 转换为小写】
用法：
s a = "AiufSUscN"
slower(a, b)
//将提示:aiufsuscn
tw(b)

说明：
常用于转换为小写后进行判断。

【supper 转换为大写】
用法：
s a = "AiufSUscN"
supper(a, b)
//将提示:AIUFSUSCN
tw(b)

说明：
常用于转换为大写后进行判断。

【stop 暂停代码】
用法：
t()
{
syso("1")

stop(1000)
syso("2")

stop(1000)
syso("3")

stop(1000)
syso("4")
}

说明：
每次执行 stop(1000) 将暂停1秒后，再执行下面代码。单位为毫秒：1000毫秒 = 1秒

【sran 生产范围随机数】
用法：（生产一个 100 至 1000的随机数）
sran(100, 1000, a)
tw(a)

说明：
有时候需要利用到随机机制，可以利用这个来开发！

【nsz 创建数组】
用法：
s a = 6
nsz(a, b)

或

//指定数组数据类型
s a = 6
nsz(a, "String", b)

说明：
申明一个数组。并且舍子数组总行数为6

【sgsz 指定访问数组维数】
用法：（根据序号访问数组）
s a = "12;34;56;78;90"
s b = ";"
sl(a, b, c)
sgsz(c, 2, d)
tw(d)

说明：
数组可以进行列表形式存储数据，常用于数据列表。注意的是序号是从0开始的。数组总行数如果是5，那序号最大为4

【sssz 设置数组数据】
用法：
s a = 6
nsz(a, b)
s c = 1
s d = "数据"
sssz(b, c, d)

说明：
指定数组序号设置数组的数据。


【sgszl 访问数组总行数】
用法：
s a = "12;34;56;78;90"
s b = ";"
sl(a, b, c)
sgszl(c, d)
tw(d)

说明：
可以获取到长度，更准确的访问数组

【hs 获取网页源码】
用法：
t()
{
s a = "https://m.baidu.com/"
hs(a, b)
syso(b)
}

2，提交post数据:
如果参数包含 & 为普通字符，可以进行转义 \& 如提交数据:&text=abc\&def
输入说明：地址，post数据提交，目标网页编码，赋值变量
t()
{
s a = "https://m.baidu.com/"
hs(a, "title=你好&text=你好吗？", "utf-8", b)
syso(b)
}

3，带自定义cookie方式获取网页:
//传递cookie项值，格式为nama=value 下例： uid=112;name=nihao;sb=123456789;

t()
{
s a = "https://m.baidu.com/"
hs(a, "title=你好&text=你好吗？", "utf-8", "uid=112;name=nihao;sb=123456789;", b)
syso(b)
}

4，带自动设置cookie方式获取网页，并记录当前网页的Cookie:
//传递cookie项值，当自定义为null 系统将自动设置已记录的cookie
t()
{
s a = "https://m.baidu.com/"
hs(a, "title=你好&text=你好吗？", "utf-8", null, true, b)
syso(b)
}

5，带自动设置cookie方式获取网页，并记录当前网页的Cookie，并设置Header头:（可设置多条，以“||”隔开）文件头包括了Cookie，User-Agent设备型号。
//传递cookie项值，当自定义为null 系统将自动设置已记录的cookie
t()
{
s a = "https://m.baidu.com/"
hs(a, "title=你好&text=你好吗？", "utf-8", null, true, "User-Agent=Mozilla/5.0 (iPad; U; CPU OS 6_0 like Mac OS X; zh-CN; iPad2)||accept=*/*||accept-language=zh-CN", b)
syso(b)
}

6，带自动设置cookie方式获取网页，并记录当前网页的Cookie，并设置Header头:（可设置多条，以“||”隔开）文件头包括了Cookie，User-Agent设备型号，设置连接超时，设置接收超时，设置代理IP。
//传递cookie项值，当自定义为null 系统将自动设置已记录的cookie
t()
{
s a = "https://m.baidu.com/"
hs(a, "title=你好&text=你好吗？", "utf-8", null, true, "User-Agent=Mozilla/5.0 (iPad; U; CPU OS 6_0 like Mac OS X; zh-CN; iPad2)||accept=*/*||accept-language=zh-CN", 20000, 20000, "10.0.0.172:80", b)
syso(b)
}

7，应用系统存储Cookie的浏览查看，返回赋值变量为字符串
hs("cookie", b)

8，应用系统存储Cookie的清空，无赋值变量
hs("del cookie")

9，应用系统存储Cookie的浏览查看指定网址，返回赋值变量为字符串
hs("cookie:https://m.baidu.com", b)

说明：
这里先开了一个线程，然后在线程里执行获取网页源码的工作，开线程是担心有些主线程界面。大部分网页都需要使用cookie登陆，可使用工具查询所需cookie然后进行操作。
设置cookie有说明作用？
1.登陆用户名
2.获取验证码图片并发送验证码
....

【hd 下载文件】
用法：（下载文件至SD卡根目录 abc.apk）

1，下载文件，默认不覆盖重复
t()
{
s a = "http://abc.com/abc.apk"
s b = "abc.apk"
hd(a, b, c)
syso(c)
}

2，设置重复是否覆盖
t()
{
s a = "http://abc.com/abc.apk"
s b = "abc.apk"
hd(a, b, true, c)
syso(c)
}


3，带自动设置cookie方式下载网页形式文件（如图片形式验证码，论坛的附件等），支持post数据，自定义Cookie或系统设置Cookie，并记录当前网页的Cookie，并设置重复是否覆盖。可参考hs获取网页，并设置Header头:（可设置多条，以“||”隔开，也可留空为null）
输入说明：下载地址，保存文件位置，是否重复覆盖，post数据提交，目标网页编码，自定义Cookie，是否系统自动设置Cookie，设置Header头，赋值变量
t()
{
s a = "http://abc.com/abc.apk"
s b = "abc.apk"
hd(a, b, true, "title=你好&text=你好吗？", "utf-8", null, true, null, b)
syso(b)
}

说明：
开个线程，然后在里面下载一个文件。并存到SD卡。下载结果将赋值到变量“c”
返回的赋值：
1 文件已经存在
0 下载成功
-1 下载失败

【hw 访问网页】
用法：
s a = "https://m.baidu.com/"
hw(a)

说明：
使用内置浏览器访问网页。
可用于下载文件：
s a = "http://abc.com/abc.apk"
hw(a)


//跳转访问网页，并且自定义标题栏颜色
//主体颜色
s b = "#387bd6"
//底部横杠颜色
s c = "#255eab"
hw("https://m.baidu.com/", b, c)

【hws 系统浏览器访问网页】
用法：
s a = "https://m.baidu.com/"
hws(a)

说明：
使用内置浏览器访问网页。
可用于下载文件：
s a = "http://abc.com/abc.apk"
hws(a)

【ug 获取控件属性】
用法：(1为：控件ID，第二个参数为控件属性标识，然后赋值到变量)
//
ug(1, "text", c)

//获取侧滑控件 左边的侧滑是否展开状态
ug(1, "isdraweropen", "start", c)

说明：
输入属性标示来返回不同的控件数据。注意：有些控件没有指定属性，将返回null。下面有属性介绍，可参考。

可用属性标识：
text=内容、background=背景、width=宽度、height=高度、x=X轴、y=Y轴、paddingleft=左内边距、paddingtop=顶内边距、paddingright右内边距、paddingbottom=底内边距、layout_marginleft=左外边距、layout_margintop=顶外边距、layout_marginright=右外边距、layout_marginbottom=底外边距、
hint=提示字符、imeoptions=虚拟键盘按键状态、visibility=控件可视状态、checked=选项是否被选中、title=浏览器网页标题、url=浏览器网址、lastvisibleposition=列表滑动到项目位置的序号、count=列表项目总数、
selecteditem=获取下拉框选值、rating=评分当前数值、progress=控件当前进度数值、date=日期控件选值、time=时间控件选值、currentitem=获得滑动窗体界面序号、isdraweropen=侧滑是否界面展开状态、selectionstart=获取文本框光标开始位置、selectionend=获取文本框光标结束位置、
cangoback=是否存在可返回的网页、cangoforward=是否存在可前进的网页、collapsecolumns=表格布局获取指定列是否折叠、shrinkcolumns=表格布局获取指定的列是否可收缩、stretchcolumns=表格布局获取指定的列是否可拉伸、shrinkcolumnsall=表格布局获取指示是否所有的列都是可收缩的、
stretchcolumnsall=表格布局获取指示是否所有的列都是可拉伸的


【us 设置控件属性】
用法：(1为：控件ID，第二个参数为控件属性标识，第三个是需要设置的数据或变量)

//设置文本控件内容
s c = "文本内容"
us(1, "text", c)


//关闭下拉刷新加载图标
us(1, "refreshing", false)


//设置浏览器的连接url
s c = "https://m.baidu.com/"
us(2, "url", c)
//提示：如果浏览器正在播放视频或音乐，直接关闭浏览器可能还会有声音，建议关闭浏览器时先跳转成另一个网页。
//提示：如果需要加载本地的文件，可以 us(2, "url", "file:///android_asset/res/web.html") 加载安装包内assets/res/web.html文件


//设置浏览器显示的html文件或文本
s c = "<html><p>html内容</></html>"
s d = "utf-8"
s e = "text/html"
us(2, "url", c, d, e, f)
tw(f)


//设置控件阴影（部分控件有效果如文本、文本框、按钮）
s radius = 5
s dx = 0
s dy = 0
s color = "#000000"
us(2, "shadow", radius, dx, dy, color, f)
tw(f)


//带有赋值变量，变量d将返回数据是否设置成功 true 或 false
s c = "文本内容"
us(1, "text", c, d)

//设置文本框控件光标
us(1, "selection", 1, d)

//选中文本框部分内容
us(1, "selection", 1, 3, d)

//浏览器前进1个网页
us(1, "gobackorforward", 1)

//浏览器后退1个网页
us(1, "gobackorforward", -1)

//设置控件点击波纹效果颜色；需系统5.0以及以上才有效果；部分控件还需要设置 clickable=true 才有效果。
us(1, "backgroundripple", "#888888")

//设置编辑框光标颜色
us(1, "textcursordrawable", "#000000")

//自定义文本控件字体
us(1, "typeface", "@ttf.ttf")

说明：
输入控件标示设置控件数据。【可参照控件属性，所有属性标识通用】

更多属性标识：
currentitem=设置滑动窗体界面序号、closedrawer=关闭指定侧滑、opendrawer=展开指定侧滑、drawerlockmode=设置手势滑动、selection=设置文本框光标位置、gobackorforward=浏览器的前进或推后、backgroundripple=波纹效果、dh=执行动画（非队列动画）

【uigo 跳转界面】
用法：（输入界面文件名，跳转指定的界面）
uigo("abc.iyu")

//带参数的跳转
uigo("abc.iyu", 536870912)


说明：
可以界面之间的转换，扩展新的界面。

参数：
67108864：如果在内存中发现存在该界面，则清空这个界面之上的所有其他界面，使其处于栈顶。
268435456：系统会寻找或创建一个新的内存来放置该界面
1073741824：跳转到的界面，不排在内存中
536870912：当内存中存在该界面并且位手机的显示状态时，不再创建一个新的，直接利用这个界面。


【utw 弹出界面】
用法：（在原有的界面弹出界面）
s a = null
s b = "界面标题"
s c = "界面内容"
s d = "退出"
s e = "保存"
s f = "取消"

//三个按钮
//输入图标，输入标题，输入内容，输入按钮名称，输入按钮名称，输入按钮名称，输入是否点击弹窗以外界面是否关闭弹窗，输入赋值变量
utw(a, b, c, d, e, f, false, v)
{
syso("点击了确定")
}
else
{
syso("点击了保存")
}
else
{
syso("点击了取消")
}

//两个按钮
utw(a, b, c, d, e, false, v)
{
syso("点击了确定")
}
else
{
syso("点击了取消")
}

//一个按钮
utw(a, b, c, d, false, v)
{
syso("点击了确定")
}

//没有按钮
utw(a, b, c, false, v)


//将界面添加到弹窗界面上，直接将界面内容设为一个界面文件
s a = "界面标题"
s b = "a.iyu"
s c = "取消"
utw(null, a, b, c, false, v)
{
syso("点击了确定")
}

说明：
常用于询问用户当前的操作，弹窗展示内容。

赋值变量说明：
弹出界面需要设置一个赋值变量，用于自定义界面弹窗的操作。

【endutw 关闭弹出界面】
用法：
endutw()

说明：
用于关闭当前打开的弹窗界面

【end 结束界面】
用法：
end()

说明：
调用后，将结束当前的界面。 并返回原来的界面。如果原来没有界面，将退出应用。

【ends 显示桌面】
用法：
ends()

说明：
跳转到手机的桌面，程序将后台运行。

【bfm 播放音频】
用法：
s a = "%abc.mp3"
bfm(a)

s a = "http://www.abc.com/abc.mp3"
bfm(a)

s a = "%abc.mp3"
bfm(a, b)
//播放
//bfms(b, "st")
//暂停
//bfms(b, "pe")
//停止
//bfms(b, "sp")
//结束播放组件
//bfms(b, "re")
//是否在播放
//bfms(b, "ip", c)
//tw(c)

//获取音频时长（毫秒）
//bfms(b, "dn", c)
//tw(c)
//获取当前播放时长（毫秒）
//bfms(b, "cn", c)
//tw(c)

//指定播放的位置（毫秒）
//bfms(b, "seekto", 2000)

//设置音量（0-100）
//bfms(b, "volume", 100, 100)

//一直循环播放
//bfms(b, "sl", true)

说明：
可以直接访问安装包里面的音频文件，也可以访问sd卡上的。

【html标签支持】
用法：
s a = "(html)<a href="https://m.baidu.com">百度</a>"
us(1, "text", a)

说明：
text属性：设置支持html代码！

【ula 列表操作内容】
用法：
//输入数据列表对象，输入数据项...不限制数量。
ula(a, 1="abc", 2="bac", 3="bbc")

//刷新列表显示内容，常用增加数据后的刷新。
ula(a)

//清空列表对象
ula(a, null)
//ula(a, "clear")

//获得列表对象，赋值返回v变量为列表对象
ula(a, "list", v)

说明：
根据数据列表，进行增加数据。

提示：
1=abc，其中1为控件id，abc为设置控件值
其中所谓的控件，为a.iyu界面中的控件。
增加标识数据，不作为设置控件数据，可在标识处设负数。如下：
-1=abc

提示：
如果需要设置 单选控件、多选控件 的选择状态，可设值为 true 或 false

注意：
将要执行事件的控件，必须在此设置值。如你有一个按钮控件无需设置值，但需要使用事件，可设置 1=null
不设置值的控件，将无法获取列表内容数据。

【uls 列表显示内容】
用法：
ula(a, 1="abc", 2="bac", 3="bbc")
s c = "a.iyu"
s d = -1
s e = -2
//列表项目界面高度 建议输入 -2 ，如果高度输入 -1 v7列表单项会填充整个界面。项目界面的宽度建议输入 -1
//输入控件id或控件对象，输入数据列表，输入列表项界面文件名，输入项目界面宽度，输入项目界面高度
uls(1, a, c, d, e)

//设置下拉选择列表
s a = "a;b;c"
s b = ";"
sl(a, b, c)
//输入控件id或控件对象，输入数据列表或数组数据
uls(1, c)


//自定义标签布局 的子项
ula(a, 1="abc", 2="bac", 3="bbc")
//输入控件id或控件对象，输入数据列表，输入列表项界面文件名，输入界面宽度，输入界面高度
uls(1, a, "a.iyu", -2, -2)


说明：
设置列表控件、视图控件、下拉列表、标签布局 的数据。

注意：
列表控件、视图控件 设置的界面 a.iyu 其中的载入事件是允许被调用。
可以通过列表控件、视图控件 设置的界面 a.iyu 的载入事件，进行每项列表布局的个性化设计。
每当显示到每项列表内容就会调用一次此载入事件，并且将该项的布局控件赋值给 st_vW 变量对象，
然后可以通过 gvs(st_vW, a.2, b) 获取其中的子控件对象，然后进行操作子控件即可。
还可以通过 st_pN 获取当前的视图中的序号，方便判断目前操作的是那一个视图。


【ulag 获取列表内容数据】
用法：

//输入当前的控件对象，输入获取控件ID 1的数据参数，输入赋值变量
ulag(a, 1, b)

//输入当前的控件对象，输入获取标识为 -1的数据参数，输入赋值变量
ulag(a, -1, b)

//通过 数据列表对象 或 列表控件对象 获取数据
//输入数据列表对象 或 列表控件对象，输入视图中的位置序号，输入获取标识为 -1的数据参数，输入赋值变量
ulag(a, 1, -1, b)

//如v7列表、滑动窗体控制 的加载界面中的 载入事件里可使用此方法获取数据内容
ulag(st_vW, 1, b)


说明：
常用与在列表控件的事件中，获取参数数据与用户进行互动。获取失败将赋值变量为 null

注意：
使用此方法在uls中设置控件参数后，有设置参数的控件，在事件中可使用此方法。

【ulas 更新列表内容数据】
用法：

//输入当前的控件对象，输入获取控件ID 1的数据参数，输入新的数据
ulas(a, 1, b)

//输入当前的控件对象，输入获取标识为 -1的数据参数，输入新的数据
ulas(a, -1, b)

//通过 数据列表对象 或 列表控件对象 获取数据
//输入数据列表对象 或 列表控件对象，输入视图中的位置序号，输入获取标识为 -1的数据参数，输入新的数据
ulas(a, 1, -1, b)

//刷新列表显示内容，常用增加数据后的刷新。
ula(a)

//如v7列表、滑动窗体控制 的加载界面中的 载入事件里可使用此方法获取数据内容
ulas(st_vW, 1, b)


说明：
常用与更新修改列表内容数据。修改数据后，别忘记刷新列表。

【usms 发送短信】
用法：
s a = "10086"
s b = "0"
usms(a, b)

注意:测试时只显示syso日志，不直接 发送短信，打包即可。

【ucall 拨打电话】
用法：
s a = "10086"
ucall(a)

注意:测试时只显示syso日志，不直接 拨出号码，打包即可。

【time 当前时间】
用法：
s a = 0
time(a, b)
tw(b)

说明：
第一个参数为时间类型，第二个赋值变量

[数字类型]
0：2014-07-07 09:10:08
1：2014/07/07 09:10:08
2：2014-07-07
3：09:10:08
4：18144133553151
5：2014年07月07日 09:10:08
[字符类型，输入字符形式需引号概括]
Y 年
m 月
d 日
H 时
M 分
S 秒
a/A 星期几

【fi 判断路径是否文件夹】
用法：
s a = "abc"
fi(a, b)
tw(b)

说明：
指定路径，判断是否为目录文件夹，返回：true 或 false

【swh 获取屏幕分辨率】
用法：
s a = "w"
//获取屏幕宽度的dp
swh(a, w)
s a = "h"
//获取屏幕高度的dp
swh(a, h)
s a = "hh"
//获取屏幕真实高度的dp
swh(a, hh)

s a = "pxw"
//获取屏幕宽度的px像素
swh(a, w)
s a = "pxh"
//获取屏幕高度的px像素
swh(a, h)
s a = "pxhh"
//获取屏幕真实高度的px像素
swh(a, hh)

s a = "pxztl"
//获取屏幕状态栏高度的px像素
swh(a, h)

s a = "pxbvk"
//获取屏幕底部虚拟键盘的高度的px像素
swh(a, h)

说明：
常用于获取屏幕的大小。

真实高度：不去除其他系统界面所占用（如状态栏）


【stobm 汉子转换编码字符】
用法：（你 转换 %E4%BD%A0）
stobm("你", "utf-8", b)
tw(b)

//转换网址中的汉字
stobm("你", "utf-8", true, b)
tw(b)

说明：
有些时候网络操作的时候，网址需要带有字符参数，就可以把这个汉字转换下。

【sutf8to 将UTF-8编码字符转换中文】
sutf8to("%E4%BD%A0", b)
tw(b)

//网址中的汉字
sutf8to("%E4%BD%A0", "utf-8", true, b)
tw(b)

【uycl 隐藏状态栏】
用法：
//隐藏
uycl(true)
//不隐藏
uycl(false)

说明：
隐藏手机顶部的状态栏

【uycl 修改状态栏颜色】
用法：
//输入更变颜色，并且保留状态栏空间，并默认设置软键盘
uycl("#50c4e5", true)

//输入更变颜色，并且不保留状态栏空间，并默认设置软键盘
uycl("#50c4e5", false)


//输入更变颜色，并且保留状态栏空间，只设置状态栏，不设置软键盘
uycl("#50c4e5", true, 0)

//输入更变颜色，并且不保留状态栏空间，只设置软键盘，不设置状态栏
uycl("#50c4e5", false, 1)


说明：
常用与设置一体化颜色，以及更变不同的状态栏颜色。

ps:如果不保留状态栏空间的话，你的底部控件可能会与底部软键盘重叠，你可以使用 swh 获取底部虚拟键盘的高度，然后可以增加一个底部外边距。

注意：
仅系统android 4.4以及以上才有效果，系统android 5.0以及以上效果更佳！
android 4.4以下的系统，无效果！

【ushsp 设置横屏或竖屏】
用法：
//横屏
ushsp(true)
//竖屏
ushsp(false)

说明：
设置屏幕的显示方式，注意的是设置后载入事件将重新执行

【bfv 播放视频】
用法：(播放SD卡上的视频文件)
s a = "%abcd.mp4"
bfv(a)

//并且横屏
s a = "%abcd.mp4"
s b = true
bfv(a, b)


//并且横屏
s a = "http://m.baidu.com/abcd.mp4"
s b = true
bfv(a, b)
说明：
此方法将全屏播放SD卡上的视频文件。调用自带的播放器。

注意：
不支持加载assets文件。支持SD卡文件、应用私有文件、（http）远程网络文件！

支持格式：
3gp、MP4、avi

【endcode 结束执行】
用法：
s a = 1
s b = 1
f(a == b)
{
tw("会提示")
//结束执行代码
endcode
}
tw("不会提示")

说明：
可用于提前结束执行代码，也可以用于模块的函数结束。

【break 跳出循环以及代码块】
用法：
w(1 == 1)
{
syso("1")
break
syso("2")
}
f(1 == 1)
{
syso("1")
break
syso("2")
}

说明：
代码块当执行 break 语句后，将跳出。


【fn 模块与函数】
1.创建一个模块：
在程序文件列表，新建一个模块名“mokuai”

2.在模块mokuai.myu里定义各种函数：
fn hanshu(a, b)
ss(a + b, c)
tw(c)
end fn
fn hanshu(a)
tw(a)
end fn

3.在事件里根据模块对象来调用函数：
s a = "abc"
s b = "def"
fn mokuai.hanshu(a, b)
fn mokuai.hanshu(a)

说明：
常用与将重复性的代码，放入模块中执行。

注意：
模块的调用过程将不共享使用 调用事件的局部变量；

例：
//(m.myu模块代码)
fn abc()
s bb = "456"
sss cc = "789"
end fn

//（mian.iyu载入事件代码）
s bb = "123"
fn abc()

//将提示 123，因为模块代码与事件代码的局部变量是不共享的；
tw(bb)

//将提示 789，可以通过全局变量进行共享数据
tw(sss.cc)

【ftz 发送通知栏】
用法：

ftz("提醒标题", "标题", "内容", null)
{
tw("点击了")
}

//设置显示图标
ftz("提醒标题", "标题", "内容", "%abc.png")
{
tw("点击了")
}

说明：
可以用于通知用户。

【uapp 打开App应用或游戏】
用法：
uapp("com.iapp", c)

//或 带有指定类名的启动
uapp("com.iapp", "com.yougaile.MakeiApp.logoActivity", c)

说明：
输入应用包名，赋值变量； 赋值变量返回启动结果：true 或 false

【uapplist 获取App列表】
用法：
uapplist(true, b)
sgsz(b, 1, d)
tw(d)

说明：
输入 是否包括获取系统App，返回一个列表数组 至变量 “b”，每列数据将存储一个应用的信息，并且以 “\n”隔开。

其中列内容格式：
应用包名，启动类，应用标题，应用版本

【uapplistgo 获取正在运行的App列表】
用法：
uapplistgo(b)
sgsz(b, 1, d)
tw(d)

说明：
输入 返回一个列表数组 至变量 “b”，每列数据将存储一个应用的信息，并且以 “\n”隔开。

其中列内容格式：
应用包名，pid, uid

【uninapp 卸载应用】
用法：
uninapp("com.iapp")

说明：
输入应用包名

【huf 上传文件】
用法：
t()
{
s a = "http://abc.com/upfile.php"
s b = "filename=iApp我的应用.apk&test=一款非常好的应用哦"
s c = "%abc/iApp.apk"
// 支持多文件上传
//s c = "%abc/iApp.apk|%abc/iApp2.apk|%abc/iApp3.apk"
s d = "utf-8"
huf(a, b, c, d, e)
syso(e)
}

2.设置 header文件头，文件头包括了Cookie，User-Agent设备型号。。
t()
{
s a = "http://abc.com/upfile.php"
s b = "filename=iApp我的应用.apk&test=一款非常好的应用哦"
s c = "%abc/iApp.apk"
// 支持多文件上传
//s c = "%abc/iApp.apk|%abc/iApp2.apk|%abc/iApp3.apk"
s d = "utf-8"
s e = "User-Agent=Mozilla/5.0 (iPad; U; CPU OS 6_0 like Mac OS X; zh-CN; iPad2)||Cookie=aa:123;bb:456;||accept-language=zh-CN"
huf(a, b, c, d, e, e)
syso(e)
}

说明：
输入 http接口，表单内容，手机内存选择文件，接口的网页编码， 赋值变量。 返回网页内容将赋值给变量 “e”

【nvw 创建动态控件】
用法：
//将控件添加至指定的控件作为子控件
//输入要添加的控件ID或控件对象，输入添加至指定控件ID或控件对象
nvw(id, did)

//输入要添加的控件ID或控件对象，输入添加至指定控件ID或控件对象，输入插入指定序号
nvw(id, did, 0)

//创建文本控件
//输入控件ID，输入添加至指定控件ID或控件对象，输入控件类型，输入控件属性
s id = 123456
s did = 1
nvw(id, did, "文本", "width=-2\nheight=-2\ntext=内容")

//创建文本控件
//输入控件ID，输入添加至指定控件ID或控件对象（若不添加则输入null），输入控件类型，输入控件属性，赋值变量为创建控件的对象
s id = 123456
s did = 1
nvw(id, did, "文本", "width=-2\nheight=-2\ntext=内容", b)

说明：
输入创建的控件ID，输入将新控件添加至指定控件ID或控件对象，创建控件的类型，创建控件的属性，可带有赋值变量


【uall 获取子控件】
用法：
//输入控件ID或控件对象，输入false时将赋值子控件ID，输入赋值变量将返回一个数据列表
uall(1, false, a)

//输入控件ID或控件对象，输入true时将赋值子控件对象，输入赋值变量将返回一个数据列表
uall(1, true, a)

s b = 1
gslist(a, b，c)
tw(c)

说明：
获取一个包含子控件的，控件中所有的子控件。

【urvw 移除控件】
用法：
urvw(3)

说明：
输入需要移除的控件ID或控件对象


【sbp 图像分割】
用法：
//载入一个图像变量，并赋值到图像变量“b”
sbp("%1.png", b)

//载入一个用户图标，{裁剪图像区域（像素）：x坐标:80，y坐标:90，裁剪宽度:50，裁剪高度:60}
//并将裁剪好的赋值到图像变量“b”
sbp("%1.png", 80, 90, 50, 60, b)

//载入一个SD卡上的图标，{裁剪图像区域（像素）：x坐标:80，y坐标:90，裁剪宽度:50，裁剪高度:60}，图像旋转图像:180度
//并将裁剪好的赋值到图像变量“b”
sbp("%1.png", 80, 90, 50, 60, 180, b)

说明：
三种方式载入图像，从图像变量，从用户图标，从SD上图标；并可设置裁剪图片；可设置图像旋转； 并赋值到新的图像变量；

【bfs 保存图像】
用法：
bfs(b, "%1.jpg")

//或 压缩比例（1至100）
bfs(b, 70, "%1.jpg")

说明：
输入图像变量，输入压缩比例（1至100），输入保存图像的路径，图像将保存至该路径。

【sdeg 启动调试模式】
用法：
sdeg(0)
sdeg(1)
sdeg(2)

说明：
提示日志方式。0打包后没有任何提示，1打包后可任然打印错误，2打包后记录日志保存至文件 iApp/Log


【tot 获取控件图标】
用法：
s id = 4
tot(id, b)

说明：
输入控件ID或控件对象，返回将赋值“b”图像变量。注：此方法仅限于 图片控件，图标按钮控件。


【tzz 图像旋转】
用法：
sbp("%1.png", a)
s b = 90
tzz(a, b, c)

说明：
输入被旋转图像变量，输入旋转度数（逆向旋转数为负数），返回将赋值“c”图像变量。


【tsf 图像缩放】
用法：
sbp("%1.png", a)

//按照倍增缩放，值小于则为缩小，否则为放大
s b = 2
tsf(a, b, c)

//指定高度与宽度缩放
s w = 100
s h = 200
tsf(a, w, h, c)

说明：
输入被缩放图像变量，输入缩放倍数 或 指定图像高度与宽度缩放，返回将赋值“c”图像变量。


【tfz 图像反转】
用法：
sbp("%1.png", a)
//水平反转
s b = "x"
tfz(a, b, c)

//垂直反转
s b = "y"
tfz(a, b, c)

说明：
输入被反转图像变量，输入反转方式 x为水平 y为垂直，返回将赋值“c”图像变量。

【tcc 获取图像变量尺寸】
用法：
sbp("%1.png", a)
s b = "w"
tcc(a, b, c)
tw(c)

s b = "h"
tcc(a, b, c)
tw(c)

说明：
获取图像变量的 w宽度 和 h高度。

【sxb 写入剪切板】
用法：
s a = "nihao"
sxb(a)

说明：
可用于复制到剪切板，其他应用可获取到此数据。

【shb 获取剪切板】
用法：
shb(a)
tw(a)

说明：
可获取剪切板数据，得到其他地方写入的剪切板数据。

【usjxm 手机休眠】
用法：
usjxm(false)

说明：
设置后手机将不休眠，不锁屏。默认为 true 需要休眠。

【bfvs 播放视频】
用法：

//设置SD卡视频文件
bfvs(1, "%a.mp4")

//设置网络远程视频文件
bfvs(1, "http://abc.com/a.mp4")

//增加控制器，c为赋值变量
bfvss(1, "media", c)
//开始播放
bfvss(1, "st")

说明：
自定义视频播放控件进行播放视频。

注意：
不支持加载assets文件。支持SD卡文件、（http）远程网络文件！

支持格式：
3gp、MP4、avi

【bfvss 播放视频控制】
用法：
//开始播放
bfvss(1, "st")

//暂停播放
bfvss(1, "pe")

//停止播放
bfvss(1, "sp")

//定位到指定帧
bfvss(1, "seekto", 300)

//增加控制器，c为赋值变量
bfvss(1, "media", c)

//是否在播放
bfvss(1, "ip", c)
tw(c)

//获取视频时长（毫秒）
bfvss(1, "dn", c)
tw(c)

//获取当前播放时长（毫秒）
bfvss(1, "cn", c)
tw(c)

【addv 加载界面】
用法：
//界面中载入其他界面
s id = 1
addv(id, "a.iyu")
addv(id, "b.iyu")

//侧滑窗体
s id = 1
addv(id, "a.iyu|b.iyu")

//滑动窗体，将带有赋值变量。此处变量“b”赋值为根控件列表，先通过 gslist 访问指定序号的根控件。通过 gvs 指定的根控件访问指定ID的控件。
s id = 1
addv(id, "a.iyu|b.iyu", b)



说明：
输入控件ID，输入界面名，输入辅助参数。可用将一个界面的控件，载入到指定控件作为子控件。

如何设置或获取属性上例 a.iyu 中的控件呢？
通过文件名作为对象，进行访问，如：

//注意：此对象的使用方式。
ug(a.2, "text", b)
us(a.3, "text", "你好")

注意：
如果载入事件中使用 addv 滑动窗体进行绑定， 如果还需要给滑动窗体内的界面中的控件设置数据，需要将设置控件的代码写在 载入完毕事件 中。否将将可能设置数据失败。

注意：
若增加 侧滑窗体 与 滑动窗体 的子控件，需要在被载入的界面设计中，自设一个根目录，作为界面唯一根目录。

【gvs 获取控件对象】
用法：
//根据当前界面，来获取控件
//输入要获取的控件ID，输入赋值变量
gvs(1, c)

//根据控件对象，来获取内部的子控件
//输入控件ID或控件对象，输入要获取的控件ID，输入赋值变量
gvs(1, 2, c)

说明：
常用与于利用根控件获取内部的子控件 或 获取控件对象。获取失败将赋值返回 null

【aslist 添加数据列表】
用法：
s b = "你好"
aslist(a, b)
s c = "你好2"
aslist(a, c)

//可插入数据到指定序号
s c = "你好3"
s b = 1
aslist(a, c, b)

说明：
输入列表对象，输入要添加的数据，输入插入指定序号。

【sslist 数据列表设置数据】
用法：
s b = 1
s c = "数据"
sslist(a, b，c)


说明：
输入列表对象，输入指定数据序号，输入设置的数据

【gslist 数据列表访问数据】
用法：
s b = 1
gslist(a, b，c)
tw(c)

说明：
输入列表对象，输入指定数据序号，输入赋值变量

【gslistl 数据列表访问数据总数】
用法：
gslistl(a, b)
tw(b)

说明：
输入列表对象，输入赋值变量

【dslist 数据列表删除指定数据】
用法：
s b = 1
dslist(a, b)

//清空所有数据
s b = -1
dslist(a, b)

说明：
输入列表对象，输入指定数据序号

提示：
如果需要清空所有数据，[输入指定数据序号]可输入 -1 即会删除当前数据列表所有数据。

【gslistsz 列表数据转化为数组】
用法：
gslistsz(a, b)

说明：
输入列表对象，输入赋值变量

【gslistis 列表数据检查是否存在指定数据】
用法：
s b = "数据"
gslistis(a, b, c)

说明：
输入列表对象，被判断的数据，输入赋值变量。赋值数据：true 或 false

【gslistiof 列表数据从头开始检查是否包含该数据】
用法：
s b = "数据"
gslistiof(a, b, c)

说明：
输入列表对象，被判断的数据，输入赋值变量

【gslistlof 列表数据从尾开始检查是否包含该数据】
用法：
s b = "数据"
gslistlof(a, b, c)

说明：
输入列表对象，被判断的数据，输入赋值变量


【nuibs 背景选择器】
用法：
//使用颜色作为背景
s pressed = "#333333"
s selected = "#333333"
s normal = "#888888"
nuibs(pressed, selected, normal, b)


//使用图像作为背景
s pressed = "%a.png"
s selected = "%a.png"
s normal = "%b.png"
nuibs(pressed, selected, normal, b)


//使用渐变颜色作为背景
.配置选中状态背景
s a = 0
s b = 0
s c = "#255779|#3e7492|#a6c0cd"
s d = "0"
s e = "topbottom"
ngde(a, b, c, d, e, pressed)

.配置正常状态背景
s a = 0
s b = 0
s c = "#255779|#3e7492|#a6c0cd"
s d = "0"
s e = "rightleft"
ngde(a, b, c, d, e, normal)

s selected = pressed

nuibs(pressed, selected, normal, b)

说明：
输入按下背景，输入选中背景，正常状态背景，输入赋值变量。


【ngde 背景调控器】
用法：
//输入圆角半径，输入背景填充色，输入赋值变量
s a = 15
s b = "#888888"
ngde(a, b, c)

//输入边框宽度，输入背景填充色，输入边框颜色，输入赋值变量
s a = 5
s b = "#888888"
s c = "#333333"
ngde(a, b, c, d)

//输入边框宽度，输入圆角半径，输入背景填充色，输入边框颜色，输入赋值变量
s a = 5
s b = 15
s c = "#888888"
s d = "#333333"
ngde(a, b, c, d, e)

//颜色渐变。输入边框宽度，输入圆角半径，输入背景填充渐变色组，输入边框颜色，输入颜色渐变方向，输入赋值变量
s a = 5
s b = 15
s c = "#255779|#3e7492|#a6c0cd"
s d = "#333333"
s e = "topbottom"
ngde(a, b, c, d, e, f)

说明：
背景空调生成的赋值变量，可配合背景选择器进行应用。

注意：
ngde 代码将赋值返回一个背景对象，此背景对象如果被多个不同大小的控件引用为背景。因为控件的大小不同，会导致此背景对象大小被修改。从而影响其他引用者控件。

提示：
边框与圆角半径 若不想调整，可设值为0 。适用于颜色渐变，不需要调节圆角半径和边框。

颜色渐变方向说明：
	topbottom：绘制从顶部梯度至底部
	trbl：借鉴右上角渐变左下角
	rightleft：绘制从右侧的梯度向左
	brtl：借鉴右下角渐变左上角
	bottomtop：绘制从底部梯度顶端
	bltr：借鉴渐变左下角到右上角
	leftright：绘制从左侧的梯度向右
	TL_BR：从绘制渐变的左上角到右下角

【sit 目标的设置】
用法：
//如，分享软件
//输入对象，输入属性标识，输入属性值
sit(a, "action", "android.intent.action.SEND")
sit(a, "type", "text/plain")
sit(a, "extra", "android.intent.extra.SUBJECT", "共享软件")
sit(a, "extra", "android.intent.extra.TEXT", "共享内容文本")
sit(a, "flags", 268435456)
uit(a, "chooser", "标题")

说明：
常用于调用系统程序以及功能 或 第三方程序功能。

可属性标识：action、type、extra、flags、data、classname、component

【uit 目标的执行】
用法：
//输入目标对象，输入属性，输入属性值
uit(a, "chooser", "标题")

//输入目标对象，输入属性，输入请求数值
uit(a, "result", 1)

//输入目标对象
uit(a)

说明：
常用于调用系统程序以及功能 或 第三方程序功能。

属性支持：chooser、result

【git 目标获取参数】
用法：
//输入目标对象，输入属性标识，输入赋值变量
git(a, "action", c)
git(a, "type", c)
git(a, "extra", "title", c)
git(a, "flags", c)

说明：
获取目标的属性。

【uqr 二维码扫描】
用法：

//扫描二维码
uqr()

//扫描结果，需要在 回调结果事件 写代码
f(st_sC == 1102)
{
git(st_iT, "extra", "result", c)
tw(c)
}


//生成二维码图像
s a = "https://m.baidu.com"
//输入字符串数据，输入图像长宽像素，输入赋值变量；将返回一个图像变量
uqr(a, 400, c)


//识别二维码图像
//输入图像变量或图片路径，输入赋值变量；将返回一个字符串
uqr(a, c)

说明：
常用于网络通用二维码扫描。

【zdp  dip转换px】
用法：
s dp = 10
//输入dp数值，输入赋值变量
zdp(dp, c)

说明：
用于常用数据转换。

【zpd  px转换dip】
用法：
s px = 10
//输入px数值，输入赋值变量
zpd(px, c)

说明：
用于常用数据转换。

【zps  px转换sp】
用法：
s px = 10
//输入px数值，输入赋值变量
zps(px, c)

说明：
用于常用数据转换。

【zsp  sp转换px】
用法：
s sp = 10
//输入sp数值，输入赋值变量
zsp(sp, c)

说明：
用于常用数据转换。

【lan 跳转界面动画】
用法：
uigo("abc.iyu")
//输入跳转界面动画的序号；6 右往左推出效果
lan(6)

说明：
用于跳转界面时候进行的动画效果

提示：
0.淡入淡出效果 1.放大淡出效果 2.转动淡出效果1 3.转动淡出效果2 4.左上角展开淡出效果 5.压缩变小淡出效果 6.右往左推出效果 7.下往上推出效果 8.左右交错效果 9.放大淡出效果 10.缩小效果 11.上下交错效果

【sjxx 获取设备信息】
用法：
sjxx(a)
sgsz(a, 0, d)
tw(d)

说明：
获取手机基本信息，将返回一个数组到赋值变量“a”，数组格式如下：

数据格式：（真实数据 \n 旁边将不没有空格）

CPU型号 \n CPU频率
屏幕宽度 \n 屏幕高度 \n 分辨率宽度 \n 分辨率高度
手机型号 \n 手机品牌 \n 手机SDK

【simsi 获取设备imsi】
用法：
simsi(a)
tw(a)

说明：
常用于识别用户的手段。

【simei 获取设备imei】
用法：
simei(a)
tw(a)

说明：
常用于识别用户的手段。

【endkeyboard 强制隐藏虚拟键盘】
用法：
endkeyboard()

说明：
常用于需要隐藏安卓弹出的虚拟键盘。

【hdfl 文件下载器】
用法：
//两个参数的方法设置
s savedir = "%SaveDir"
//输入下载保存目录，输入赋值变量返回一个下载器对象
hdfl(savedir, a)
{
//每当下载完一个执行
//系统赋值 st_drD 文件下载项的序号
//系统赋值 st_drI 文件下载项的状态

//获取下载的URL
ulag(a, st_drD, "url", b1)
syso(b1)

//获取自定义整数标识
ulag(a, st_drD, "type", b2)
syso(b2)

//获取自定义参数任意数据
ulag(a, st_drD, "text", b3)
syso(b3)

//获取下载文件保存的路径
ulag(a, st_drD, "filename", b4)
syso(b4)

}
else
{
//当下载完目前所有执行
//系统赋值 st_drJ 本次文件下载完成总数
ufnsui()
{
tw(st_drJ)
}
}

//三个参数的方法设置
s tempdir = "%TempDir"
s savedir = "%SaveDir"
//输入下载临时文件保存目录，输入下载保存目录，输入赋值变量返回一个下载器对象
hdfl(tempdir, savedir, a)
{
ufnsui()
{
tw(st_drD)
}
}
else
{
ufnsui()
{
tw(st_drJ)
}
}

//六个参数的方法设置
s tempdir = "%TempDir"
s savedir = "%SaveDir"
//输入下载临时文件保存目录，输入下载保存目录, 下载线程数量，连接网络超时时间（25秒的意思），文件重复是否覆盖，输入赋值变量返回一个下载器对象
hdfl(tempdir, savedir, 3, 25000, true, a)
{
ufnsui()
{
tw(st_drD)
}
}
else
{
ufnsui()
{
tw(st_drJ)
}
}

说明：
常用与单个或多个的文件下载。推荐图片列表下载或小文件下载。

提示：
代码{ 区域中 }属于线程内执行。在其中更新界面控件属性需要使用ufnsui代码
上例子使用tw代码，并且用了ufnsui代码。

【hdfla 文件下载器 增加文件下载项】
用法：
//创建一个文件下载器
hdfl(tempdir, a)
{
ufnsui()
{
tw(st_drD)
}
}
else
{
ufnsui()
{
tw(st_drJ)
}
}

//增加下载项
//输入下载器对象，输入下载连接URL，输入自定义整数标识，输入自定义参数任意数据
hdfla(a, "http://abc.com/1.jpg", 1, "abcd123")


//增加下载项，并且自定义保存目录
//输入下载器对象，输入下载连接URL，输入自定义整数标识，输入自定义参数任意数据，输入自定义保存路径
hdfla(a, "http://abc.com/2.jpg", 1, "abcd123", "%abc.jpg")

说明：
调用下载器增加下载项，并且立刻进行下载。

【hdd 配置下载管理器】
用法：
//下载产生的临时文件目录
s a = "%tempdir"
//下载至保存的目录
s b = "%filedir"
//允许同时下载任务数量
s c = 3
//每个任务开启线程数量
s d = 3
//连接失败重试次数
s e = 2
//连接超时时间，25秒的意思
s f = 25000
//是否显示下载进度通知
s g = true
hdd(a, b, c, d, e, f, g)

说明：
如果不使用此代码进行配置，那么系统将使用默认配置。下载配置器可以很方便的制作下载文件，并且方便管理。

默认目录属性：
临时文件目录：iApp/DownloadFileDir/TempDefaultDownFile
保存文件目录：iApp/DownloadFileDir/DefaultDownFile

【hdda 下载管理器 增加文件下载项】
用法：

//===========方法一
//下载的链接
s url = "http://abc.com/abc.apk"

//保存的文件名（仅输入文件名,请勿不包含目录）
s name = "abc.apk"

//输入自定义参数任意数据
s data = "abcde123"

//变量v为赋值变量，为下载对象
hdda(url, name, data, v)

//===========方法二
//下载的链接
s url = "http://abc.com/abc.apk"

//保存的文件名（仅输入文件名,请勿不包含目录）
s name = "abc.apk"

//下载任务的标题
s title = "abc.apk最新版"

//输入自定义参数任意数据
s data = "abcde123"

//变量v为赋值变量，为下载对象
hdda(url, name, title, data, v)

//===========方法三
//下载的链接
s url = "http://abc.com/abc.apk"

//保存的文件名（仅输入文件名,请勿不包含目录）
s name = "abc.apk"

//下载任务的标题
s title = "abc.apk最新版"

//下载任务的图标
s icon = "@abc.png"

//输入自定义参数任意数据
s data = "abcde123"

//变量v为赋值变量，为下载对象
hdda(url, name, title, icon, data, v)

//===========方法四
//下载的链接
s url = "http://abc.com/abc.apk"

//保存至目录
s dir = "%filedir"

//保存的文件名（仅输入文件名,请勿不包含目录）
s name = "abc.apk"

//下载任务的标题
s title = "abc.apk最新版"

//下载任务的图标
s icon = "@abc.png"

//是否显示下载进度通知
s notsohw = true

//输入自定义参数任意数据
s data = "abcde123"

//变量v为赋值变量，为下载对象
hdda(url, dir, name, title, icon, notsohw, data, v)

说明：
增加常用的网络文件进行下载。

【hddgl 获取下载管理器下载列表】
用法：
//输入赋值变量返回下载列表
hddgl(list)

//使用for循环下载列表
for(b; list)
{
hddg(b, "url", c)
syso(c)
}

说明：
获取下载管理器所有的下载列表。

【hddg 获取下载管理器获取下载项属性】
用法：
//下载的链接
s url = "http://abc.com/abc.apk"
//保存的文件名（仅输入文件名,请勿不包含目录）
s name = "abc.apk"
//输入自定义参数任意数据
s data = "abcde123"
//变量v为赋值变量，为下载对象
hdda(url, name, data, v)

//===========获取下载项的属性
//获取下载项的 ID
hddg(v, "id", b)

//获取下载项的 下载链接
hddg(v, "url", b)

//获取下载项的 保存的绝对路径
hddg(v, "dirfilename", b)

//获取下载项的 下载链接的md5
hddg(v, "urlmd5", b)

//获取下载项的 保存的目录
hddg(v, "dir", b)

//获取下载项的 保存的文件名
hddg(v, "filename", b)

//获取下载项的 下载文件的大小（字节）
hddg(v, "contentlength", b)

//获取下载项的 已下载的数据（字节）
hddg(v, "equivalent", b)

//获取下载项的 当前下载速度（字节）
hddg(v, "downloadspeed", b)

//获取下载项的 当前下载进度百分比
hddg(v, "downloadpercentage", b)

//获取下载项的 下载状态；（0为等待下载；1为正在下载；2为下载完成；3下载已经暂停或停止；-1下载失败；-2已删除）
hddg(v, "status", b)

//获取下载项的 是否显示下载通知
hddg(v, "notificationshow", b)

//获取下载项的 自定义的数据
hddg(v, "text", b)

//获取下载项的 通知标题
hddg(v, "title", b)

//获取下载项的 通知图标
hddg(v, "icon", b)

说明：
可获取详细的下载项目状态属性。

【hdds 设置下载管理器下载项的属性】
用法：
//下载的链接
s url = "http://abc.com/abc.apk"
//保存的文件名（仅输入文件名,请勿不包含目录）
s name = "abc.apk"
//输入自定义参数任意数据
s data = "abcde123"
//变量v为赋值变量，为下载对象
hdda(url, name, data, v)

//===========可设置的下载项属性

//设置下载项的 下载状态；（0为等待下载；1为正在下载；2为下载完成；3下载已经暂停或停止；-1下载失败；-2已删除）
hdds(v, "status", 0)

//设置下载项的 是否显示下载通知
hdds(v, "notificationshow", true)

//设置下载项的 自定义的数据
hdds(v, "text", "abcd123")

//设置下载项的 通知标题
hdds(v, "title", "abc.apk最新版本")

//设置下载项的 通知图标
hdds(v, "icon", "@abc.png")

说明：
设置下载项目的属性。

【hdduigo 跳转至下载管理器】
用法：
//跳转至下载管理器
hdduigo()

//跳转至下载管理器，并且自定义标题栏颜色
//主体颜色
s a = "#387bd6"
//底部横杠颜色
s b = "#255eab"
hdduigo(a, b)

说明：
跳转至文件下载的管理器。

【ufnsui 线程更新界面】
用法：
ufnsui()
{
tw(a)
us(1, "text", "内容")
}

说明：
线程中直接修改界面或修改设置控件属性，出错。
需要使用ufnsui模块进行更新或设置控件属性。

提示：
线程中获取控件数据不会出错。

【se 正则表达式操作】
用法：
//===========例子1；所有属性展示
//字符串
s a = "qqqq123456eee"
//正则表达式
s b = "([a-z]+)(\d+)"
//更多参数
s c = 0
se(a, b, c, d)

//替换成，将替换全部
se(d, "sral", "1:$1, 2:$2", e)
syso(e)
//替换成，只替换第一个
se(d, "srft", "1:$1, 2:$2", e)
syso(e)

//返回是否匹配成功，需字符串被完全匹配，赋值返回true或 false
.se(d, "ms", e)

//开始匹配 或 匹配下一个，赋值返回true或 false
.se(d, "find", e)

//给定位置序号进行匹配，赋值返回true或 false
.se(d, "find", 1, e)

//获取匹配组的数量，当前为2组：([a-z]+)、(\d+)
.se(d, "gl", e)

//获取第1组匹配到的子字符串在字符串中的开头位置 
.se(d, "start", 1, e)

//获取第1组匹配到的子字符串在字符串中的结尾位置 
.se(d, "end", 1, e)

//获取第1组匹配到的子字符串
.se(d, "group", 1, e)
//获取第2组匹配到的子字符串
.se(d, "group", 2, e)


//===========例子2；获取所有手机号

//字符串
s a = "我的号码 13612345678 , 你的号码 13412345678"
//正则表达式
s b = "[1][3-8]\d{9}"
//更多参数
s c = 0
se(a, b, c, d)

//开始匹配 或 匹配下一个
se(d, "find", e)

//循环判断是否匹配成功
w(e == true)
{
//因为 [1][3-8]\d{9} 没有组，所以这里我们输入 0
se(d, "group", 0, e)

//打印出匹配到的子字符串
syso(e)

//开始匹配 或 匹配下一个
se(d, "find", e)
}

//===========例子3；判断是否为手机号

//字符串
s a = "13612345678"
//正则表达式
s b = "^[1][3-8]\d{9}$"
//更多参数
s c = 0
se(a, b, c, d)

se(d, "ms", e)
f(e == true)
{
syso("手机号格式正确")
}
else
{
syso("手机号格式错误")
}


说明：
常用与字符串处理，高效的处理字符串，以及检测字符串类型等。使用此方法，需要对正则表达式有部分知识。

【usg 闪光灯操作】
用法：
//开启闪光灯
//输入闪光灯变量对象，输入是否开启闪光灯
usg(sss.sgd, true)

//关闭闪光灯
//输入闪光灯变量对象，输入是否开启闪光灯
usg(sss.sgd, false)

说明：
开启或关闭 设备闪光灯！

说明：
常用照明。

注意：
此方法调用将无法与摄像头同时调用。如启动摄像头需要使用闪光灯，可在摄像头操作中开启闪光灯。

【uzd 震动器操作】
用法：
//震动1秒时长
//输入振动器变量对象，输入震动时长
uzd(sss.zdq, 1000)

//静止1秒，震动1秒，静止1秒，震动1秒，静止1秒，震动1秒，静止1秒，..， 并且不重复
//输入振动器变量对象，输入震动规则，输入是否重复循环执行
uzd(sss.zdq, "1000 1000 1000 1000 1000 1000 1000 1000", false)

//强制停止震动器
uzd(sss.zdq, "sp")

//检查硬件是否具有振动器
uzd(sss.zdq, "ip", b)
syso(b)

说明：
常用提示用户。

【usxq 开启前置摄像头】
用法：
//开启摄像头
//输入摄像头变量对象，输入面控件的对象或ID，摄像头旋转角度
usxq(sss.ps, 1, 90)

//输入摄像头变量对象，输入面控件的对象或ID，摄像头旋转角度，输入拍摄宽度像素，输入拍摄高度像素，输入图像品质1-100
usxq(sss.ps, 1, 90, 640, 480, 95)

//自动对焦拍摄
//输入摄像头变量对象，输入保存路径，输入图像旋转角度，输入拍摄是否停止预览
usx(sss.ps, "shot", "%abc.jpg", -90, false)

说明：
指定打开前置摄像头。

注意：
此功能需要与一个面控件进行绑定，你可以在面控件上面设置拍摄事件。

注意：
此代码仅限于载入事件调用。

【usxh 开启后置摄像头】
用法：
//开启摄像头
//输入摄像头变量对象，输入面控件的对象或ID，摄像头旋转角度
usxh(sss.ps, 1, 90)

//输入摄像头变量对象，输入面控件的对象或ID，摄像头旋转角度，输入拍摄宽度像素，输入拍摄高度像素，输入图像品质1-100
usxh(sss.ps, 1, 90, 1280, 960, 95)

//自动对焦拍摄
//输入摄像头变量对象，输入保存路径，输入图像旋转角度，输入拍摄是否停止预览
usx(sss.ps, "shot", "%abc.jpg", 90, false)

说明：
指定打开后置摄像头。

注意：
此功能需要与一个面控件进行绑定，你可以在面控件上面设置拍摄事件。

注意：
此代码仅限于载入事件调用。

【usx 摄像头操作】
用法：
//开启摄像头
usxh(sss.ps, 1, 90)

//自动对焦拍摄
//输入摄像头变量对象，输入保存路径，输入图像旋转角度，输入拍摄是否停止预览
usx(sss.ps, "shot", "%abc.jpg", 90, false)

//开始预览
usx(sss.ps, "st")

//停止预览
usx(sss.ps, "sp")

//旋转摄像头角度
usx(sss.ps, "rotaing", 180)
//获取旋转摄像头角度
usx(sss.ps, "getrotaing", b)
syso(b)

//启动摄像头闪光灯
usx(sss.ps, "usg", true)

//结束摄像头组件变量对象
usx(sss.ps, "re")

说明：
摄像头的控制。

【bly 录制音频】
用法：
//开始录制
//输入录音变量对象，输入保存文件路径
bly(sss.ly, "%abcd.amr")

//停止录音
bly(sss.ly, "sp")

说明：
常用于录制音频。

说明：
可使用 bfm 代码来播放录制好的音频。

【ujp 截取屏幕】
用法：
//输入保存路径，输入图像品质（1-100）
ujp("%123.jpg", 70)

说明：
常用于截取当前界面。

【sqlite 数据库操作】
用法：
//连接一个私有数据库，如果不存在将自动新建
//输入数据库对象变量，输入数据库文件名
sqlite(sss.data, "iapp.db")

//连接一个公共数据库，如果不存在将自动新建
//输入数据库对象变量，输入数据库文件名
sqlite(sss.data, "%iapp.db")

//判断数据库是否存在
sqlite("iapp.db", "ip", b)
syso(b)

//删除数据库
sqlite("iapp.db", "del", b)
syso(b)

//释放数据库
sqlite(sss.data, "re")

说明：
进行数据库的操作。

【sql 数据表操作】
用法：

//创建数据表
s table = "_id integer primary key,url text, filename text,status interger,createTime datetime"
sql(sss.data, "info", "add", table, b)

//判断数据表是否存在
sql(sss.data, "info", "ip", b)
syso(b)

//删除数据表
sql(sss.data, "info", "del", b)
syso(b)

//添加数据表一条数据
s table = "url,filename,status,createTime"
time(0, sj)
ss("'http://abc.com/abc.apk', 'abc.apk', 1, '" + sj + "'", data)
sql(sss.data, "info", "add", table, data, b)
syso(b)

//修改数据表的数据，若不需要设置条件(_id=1)可设为 null 视为适用于执行所以数据
sql(sss.data, "info", "up", "status=2", "_id=1", b)
syso(b)

//删除数据表的数据，若不需要设置条件(_id=1)可设为 null 视为适用于执行所以数据
sql(sss.data, "info", "del", "_id=1", b)
syso(b)


//查询，若不需要设置条件(status=1 order by _id desc LIMIT 0,1)可设为 null 视为适用于执行所以数据

// LIMIT <跳过的数据数目>, <取数据数目>
s table = "_id,url,filename,status,createTime"
s sqlx = "status=1 order by _id desc LIMIT 0,1"
sql(sss.data, "info", "sele", table, sqlx, data)

//自定义sql查询
//s sqlx = "select _id,url,filename,status,createTime from info where status=1 order by _id desc LIMIT 0,1"
//sql(sss.data, sqlx, data)

//光标对象移到下一条数据
sqlsele(data, "next", e)
w(e == true)
{
//获取光标对象的第一列数据
sqlsele(data, 0, e)
syso(e)

//获取光标对象的第二列数据
sqlsele(data, 1, e)
syso(e)

//光标对象移到下一条数据
sqlsele(data, "next", e)
}


//自定义的sql执行，需要对sql语法了解才能灵活运用
s sqlx = "insert into info (url,filename,status,createTime) values ('http://abc.com/abc.apk', 'abc.apk', 1, '2016-7-31 10:31:21')"
sql(sss.data, sqlx)

说明：
数据表的操作。

注意：
在执行sql语句的时候，需要注意你的字符串的特殊字符的转义。
     /   ->    //
     '   ->    ''
     [   ->    /[
     ]   ->    /]
     %   ->    /%
     &   ->    /&
     _   ->    /_
     (   ->    /(
     )   ->    /)

【sqlsele 查询数据操作】
用法：

//获取光标对象的第一列数据
sqlsele(data, 0, e)

//获取光标对象有多少列
sqlsele(data, "columncount", e)
syso(e)

//获取总共查询到多少条数据
sqlsele(data, "count", e)
syso(e)

//光标对象移到下一条数据
sqlsele(data, "next", e)

//光标对象移到上一条数据
sqlsele(data, "previous", e)

//光标对象移到第一条数据
sqlsele(data, "first", e)

//光标对象移到最后第一条数据
sqlsele(data, "last", e)

//光标对象移到指定第2条数据
sqlsele(data, "position", 2)

//获取光标对象当前位置
sqlsele(data, "getposition", e)
syso(e)

//释放数据查询
sqlite(data, "re")

说明：
数据查询的操作。

【dha 渐变透明度动画】
用法：
//创建一个渐变透明度动画，开始显示，然后渐变消失
//输入动画开始是否透明，输入动画结束是否透明
dha(dh, true, false)
dh(dh, "duration", 2000)
us(2, "dh", dh)

说明：
常用于控件透明度动画。

【dhs 渐变尺寸伸缩动画】
用法：
//创建一个渐变尺寸伸缩动画
//0为没有，2.5为原始2.5倍

//输入X开始尺寸比例，输入X结束尺寸比例，输入Y开始尺寸比例，输入Y结束尺寸比例
dhs(dh, 0.5, 2.5, 0.5, 2.5)
dh(dh, "duration", 2000)
us(2, "dh", dh)

//输入X开始尺寸比例，输入X结束尺寸比例，输入Y开始尺寸比例，输入Y结束尺寸比例，输入X位置类型，输入X坐标的开始位置，输入Y位置类型，输入Y坐标的开始位置
dhs(dh, 0.5, 2.5, 0.5, 2.5, 1, 0.5, 1, 0.5)
dh(dh, "duration", 2000)
us(2, "dh", dh)

说明：
常用于控件伸缩动画。

位置类型：
0 默认
1 以对象本身为基准位置类型
2 以父控件为基准位置类型

【dht 画面位置移动动画】
用法：
//创建一个画面位置移动动画
//输入开始X坐标上的移动位置，结束X坐标上的移动位置，开始Y坐标上的移动位置，结束Y坐标上的移动位置
dht(dh, 30, 80, 30, 80)
dh(dh, "duration", 2000)
us(2, "dh", dh)

说明：
常用于控件移动动画。

【dhr 画面旋转动画】
用法：
//创建一个画面旋转动画
//输入动画开始的旋转角度，输入动画旋转到的角度
dhr(dh, 0, 180)
dh(dh, "duration", 2000)
us(2, "dh", dh)

//输入动画开始的旋转角度，输入动画旋转到的角度，输入X位置类型，输入X坐标的开始位置，输入Y位置类型，输入Y坐标的开始位置
dhr(dh, 0, 180, 1, 0.5, 1, 0.5)
dh(dh, "duration", 2000)
us(2, "dh", dh)

说明：
常用于控件旋转动画。

位置类型：
0 默认
1 以对象本身为基准位置类型
2 以父控件为基准位置类型

【dhset 动画集合】
用法：

//渐变尺寸伸缩动画
dhs(dh1, 0.5, 2.5, 0.5, 2.5)
dh(dh1, "duration", 2000)

//画面位置移动动画
dht(dh2, 30, 80, 30, 80)
dh(dh2, "duration", 2000)

//画面旋转动画
dhr(dh3, 0, 180)
dh(dh3, "duration", 2000)

//创建一个动画集合
//输入动画集合变量对象，输入是否使用动画集合的interpolator，输入动画...（可输入N个参数）
dhset(dhlist, false, dh1, dh2, dh3, dh4)
us(2, "dh", dhlist)
	
说明：
常用于动画集合执行。

提示：
动画集合允许被其他动画集合添加成为子动画。

提示：
动画集合如果设置了动画控制属性，同时也会重置所有子控件的属性。

【dhas 队列动画执行】
用法：
//旋转动画
//输入动画变量对象，输入控件ID或控件对象，输入动画类型，输入旋转角度...（可输入N个参数）
dhas(dh, 2, "rotation", 60, 180)
//dhas(dh, 2, "rotationX", 30, 80, 60, 20, 60)
//dhas(dh, 2, "rotationY", 30, 80)
dh(dh, "duration", 2000)
dh(dh, "start")

//伸缩动画
//输入动画变量对象，输入控件ID或控件对象，输入动画类型，输入伸缩尺寸比例...（可输入N个参数）
dhas(dh, 2, "scaleX", 1.5, 2.5)
//dhas(dh, 2, "scaleY", 1.5, 2.5, 1.2, 2.6, 1.3)
dh(dh, "duration", 2000)
dh(dh, "start")

//移动动画
//输入动画变量对象，输入控件ID或控件对象，输入动画类型，输入移动到位置...（可输入N个参数）
dhas(dh, 2, "translationX", 0, 60)
//dhas(dh, 2, "translationY", 0, 60, 30, 10, 60)
dh(dh, "duration", 2000)
dh(dh, "start")

//透明度
//输入动画变量对象，输入控件ID或控件对象，输入动画类型，可见度比例(0.0至1.0)...（可输入N个参数）
dhas(dh, 2, "alpha", 1, 0.3, 1, 0.2, 1)
dh(dh, "duration", 2000)
dh(dh, "start")

说明：
自定义队列动画执行。


【dhast 队列动画集合】
用法：

//旋转动画
dhas(dh1, 2, "rotation", 60, 180)
dh(dh1, "duration", 2000)

//伸缩动画
dhas(dh2, 2, "scaleX", 1.5, 2.5)
dh(dh2, "duration", 2000)

//移动动画
dhas(dh3, 2, "translationX", 0, 60)
dh(dh3, "duration", 2000)

//透明度
dhas(dh4, 2, "alpha", 1, 0.3, 1, 0.2, 1)
dh(dh4, "duration", 2000)

//顺序执行
dhast(dhlist, "sequen", dh1, dh2, dh3, dh4)

//同时执行
//dhast(dhlist, "together", dh1, dh2, dh3, dh4)
dh(dhlist, "start")

说明：
常用于动画集合执行。

提示：
队列动画集合允许被其他队列动画集合添加成为子动画。

提示：
动画集合如果设置了动画控制属性，同时也会重置所有子控件的属性。


【dh 动画控制】
用法：

//========动画的属性（非队列动画）设置========================

//取消动画，取消后若需要重新播放，需要先执行 reset 然后再执行 start 进行播放
dh(dh, "cancel")

//重置动画属性
dh(dh, "reset")

//启动动画
dh(dh, "start")

//动画持续时长
dh(dh, "duration", 2000)

//延迟执行，延迟指定时长后才执行动画
dh(dh, "delay", 2000)

//启动动画结束填充效果（如果设false 那么 after 与 before将无效）
dh(dh, "enabled", true)

//动画执行后，控件停留执行结束状态
dh(dh, "after", true)

//动画执行后，控件停留执行开始状态
dh(dh, "before", true)

//动画重复执行的次数
dh(dh, "repeat", 20)

dhas(dh2, 2, "rotation", 60, 180)
//动画集合添加动画，仅用于 dhset 动画集合追加更多的动画
dh(dh, "add", dh2)

//========队列动画的属性设置========================

//取消动画
dh(dh, "cancel")

//播放动画
dh(dh, "start")

//动画持续时长
dh(dh, "duration", 2000)

//延迟执行，延迟指定时长后才执行动画
dh(dh, "delay", 2000)

//动画是否正在运行
dh(dh, "running", b)
syso(b)

//设置动画执行的控件ID或控件对象
dh(dh, "target", 2)

//克隆动画
dh(dh, "clone", dh2)

说明：
常用于动画的控制管理。

【dhon 动画监听事件】
用法：
//========动画（非队列动画）设置监听事件========================
dhon(dh)
{
//当结束动画时
syso("End")
}

//或

dhon(dh)
{
//当结束动画时
syso("End")
}
else
{
//当重复动画时
syso("Repeat")
}
else
{
//当启动动画时
syso("Start")
}

//========队列动画设置监听事件========================

dhon(dh)
{
//当结束动画时
syso("End")
}

//或

dhon(dh)
{
//当结束动画时
syso("End")
}
else
{
//当重复动画时
syso("Repeat")
}
else
{
//当启动动画时
syso("Start")
}
else
{
//当取消动画时
syso("Cancel")
}

说明：
常用于动画状态的监听。

提示：
该事件使用的选择性，可顺序选择性保留。

【dhb 动画背景】
用法：
//创建动画背景
//输入动画背景变量对象，输入是否重复执行
dhb(dh, true)

//添加元素
//输入动画背景变量对象，输入背景图像或图片变量或背景对象，输入显示时长
dhb(dh, "@t1.png", 1000)
dhb(dh, "@t2.png", 1000)
dhb(dh, "@t3.png", 1000)

//设为指定控件背景
us(2, "background", dh)

//启动动画
dhb(dh, "start")

//停止动画
//dhb(dh, "stop")

//是否在运行
dhb(dh, "running", b)
syso(b)

说明：
常用于组合一个背景动画。

【hsas 开启浏览器控件交互(裕语言+js+html5)】
用法：
//开启浏览器控件支持iapp交互
//输入浏览器控件ID或对象，输入是否开启
hsas(1, true)

//hsas(1, false)

说明：
常用于浏览器中的JavaScript代码于iapp代码的互相调用。

【has 裕语言交互JavaScript语言】
用法：
//首先将 web.html 放入用户文件中

//设置浏览器控件显示的html内容
s a = "@web.html"
s b = "utf-8"
fr(a, b, c)

s d = "utf-8"
s e = "text/html"
us(1, "url", c, d, e, f)

//因为浏览器加载内容属于异步操作，如果立刻执行下面的代码会执行失败
//所以将下面的代码放入某项单击事件中

s a = "go('呀！')"
//输入浏览器控件ID或对象，输入JavaScript的方法
has(1, a)

//带返回值解决方案
//s a = "go2('呀！')"
//输入浏览器控件ID或对象，输入JavaScript的方法
//has(1, a)
//tw(sss.sb)

说明：
常用于浏览器中的JavaScript代码于iapp代码的互相调用。

注意：
在载入事件设置浏览器控件的加载html内容，它不会立刻加载完成。所以如果将 裕语言交互js的代码也写在载入事件，会导致交互调用失败。必须等待浏览器加载完毕html内容后，才能交互。

注意：
建议尽量使用JavaScript调用交互裕语言，效率较高。裕语言调用执行JavaScript的方法效率要慢数倍。

注意：
has 不应该放在新线程中，测试发现5.1系统has放入新线程中报错。

注意：
本例子需要注意编码，否则将乱码。

html（web.html）文件（utf-8编码）例子：
<html>
<head>
<script type="text/javascript">
function go(o)
{
document.getElementById("sb").innerHTML += "打我" + o;
}
function go2(o)
{
document.getElementById("sb").innerHTML += "打我" + o;
iapp.s("sss.sb", document.getElementById("sb").innerHTML);
}
</script>
</head>
<p id="sb">哈哈，你来</p>
</html>


【JavaScript交互裕语言】
用法：
//首先将 web.html 放入用户文件中

//设置浏览器控件显示的html内容
s a = "@web.html"
s b = "utf-8"
fr(a, b, c)

s d = "utf-8"
s e = "text/html"
us(1, "url", c, d, e, f)

//此方法，主要是在JavaScript中写交互代码哦
//JavaScript中交互方法列表（用于交互裕语言）：

/.

//调用裕语言模块方法，不带返回变量的
iapp.fn('a.b("' + o + '")');

//调用裕语言模块方法，带返回变量的
var value = iapp.fn2('a.c("' + o + '")', b);

//设置裕语言变量数据
iapp.s(o);

//获取裕语言变量数据
var value = iapp.g(o);
./
说明：
常用于浏览器中的JavaScript代码于iapp代码的互相调用。

注意：
建议尽量使用JavaScript调用交互裕语言，效率较高。裕语言调用执行JavaScript的方法效率要慢数倍。

注意：
本例子需要注意编码，否则将乱码。


html（web.html）文件（utf-8编码）例子：
<html>
<head>
<script type="text/javascript">

//不带返回变量的
function go(o)
{
//调用的是 模块a.myu 中的 b方法
iapp.fn('a.b("' + o + '")');
}

//带返回变量的
//执行模块后，获取一个变量并返回到javascript方法里
function go2(o, b)
{
//调用的是 模块a.myu 中的 c方法
var value = iapp.fn2('a.c("' + o + '")', b);
alert('变量 sss.abc：' + value);
}

//设置全局变量数据
//同理，下面也有设置界面变量、设置局部变量的例子
function ss(o, b)
{
iapp.s(o, b);
}

//获取全局变量数据
//同理，下面也有获取界面变量、获取局部变量的例子
function gs(o)
{
var value = iapp.g(o);
alert('变量 sss.abc：' + value);
}

</script>
</head>
<p><a href="javascript:void(0)" onclick="go('呵呵')">调用裕语言的模块方法</a></p>
<p></p>
<p></p>
<p><a href="javascript:void(0)" onclick="go2('呵呵', 'sss.abc')">调用裕语言的模块方法，并返回sss.abc变量内容</a></p>
<p></p>
<p></p>
<p><a href="javascript:void(0)" onclick="ss('sss.abc', '呵呵')">设置裕语言的sss.abc全局变量数据</a></p>
<p></p>
<p></p>
<p><a href="javascript:void(0)" onclick="gs('sss.abc')">获取裕语言的sss.abc全局变量数据</a></p>
</html>

模块（a.myu）例子：
fn b(a)
//打印出数据
syso(a)
end fn

fn c(a)
//打印出数据
syso(a)
sss abc = "666呵呵"
end fn

【uxf 显示悬浮窗】
用法：

//输入界面名，输入宽度，输入高度，输入对其方式，输入赋值变量
s w = -1
s h = -1
s gravity = "top|right"
uxf("a.iyu", w, h, gravity, sss.v)


//输入界面名，输入X显示位置，输入Y显示位置，输入宽度，输入高度，输入类型的窗口，输入对其方式，输入flags，输入format，输入赋值变量
s x = 0
s y = 0
s w = -1
s h = -1
s type = 0
s gravity = "top|right"
s flags = 0
s format = 0
uxf("a.iyu", x, y, w, h, type, gravity, flags, format, sss.v)


//刷新悬浮窗口的布局，常用于通过us设置后的刷新
//输入界面根控件的控件对象
uxf(sss.v)


//移除悬浮窗口
//输入界面根控件的控件对象，输入标识
uxf(sss.v, "del")


//重置悬浮窗的属性
//输入界面根控件的控件对象，输入标识，输入X显示位置，输入Y显示位置，输入宽度，输入高度，输入对其方式
s x = 0
s y = 0
s w = -2
s h = -2
s gravity = "top|right"
uxf(sss.v, "set", x, y, w, h, gravity)

//重置悬浮窗的属性
//输入界面根控件的控件对象，输入标识，输入X显示位置，输入Y显示位置，输入宽度，输入高度，输入对其方式
s x = 0
s y = 0
s w = -1
s h = -1
s type = 0
s gravity = "top|right"
s flags = 0
s format = 0
uxf(sss.v, "set", x, y, w, h, type, gravity, flags, format)

说明：
常用于显示悬浮窗窗口。

提示：
可通过 gvs(sss.v, a.1, b) 代码进行获取悬浮窗内的子控件，然后对其进行操作。

提示：
可通过下例代码，控制窗口位置的移动
//更新窗口位置
us(sss.v, "x", 100)
us(sss.v, "y", 100)

//获取窗口位置
ug(sss.v, "x", xx)
ug(sss.v, "y", yy)

//通过us 更新后， 需要刷新悬浮窗口的布局
uxf(sss.v)


对齐方式：
center：居中
top：顶
bottom：底
left：左
right：右
center_vertical：垂直居中
center_horizontal：水平居中

输入flags：
0 不许获得焦点（编辑框输入法将无法弹出）
1 可以获得焦点，返回键将不可用


【tts 文本转换语音】
用法：
//创建一个TTS对象
//输入赋值对象
tts(a)


//创建一个TTS对象；并且直接设置播放
//输入赋值对象，输入语言代码，输入语速率，输入音高率，输入播放文字（可传入null）
tts(a, "en", "I love you", 1, 1)


//获取TTS对象初始化状态；赋值变量返回 0未完成初始化 1初始化成功 -1初始化失败 -2初始化语言失败 -3当前TTS对象不可用
//输入TTS对象，输入标识，输入赋值变量
tts(a, "zt", b)
syso(b)


//播放文字；模式 0替换以前的任务 1队列追加至后面
//输入TTS对象，输入标识，输入播放文字，输入模式，输入赋值变量
tts(a, "st", "I love you", 0, b)
syso(b)


//文字转换音频文件
//输入TTS对象，输入标识，输入文字，输入保存路径，输入赋值变量
tts(a, "ft", "I love you", "123.wav", b)
syso(b)


//设置语言
//输入TTS对象，输入标识，输入语言代码
tts(a, "lg", "en")


//设置语音播放速率。1为正常，值越低语速越慢（0.5是正常的一半），值越大语速越快（2是正常的两倍）
//输入TTS对象，输入标识，输入小数
tts(a, "se", 1)


//设置音高率，值越大声音越高音，值越小声音越低音，正常为1.0
//输入TTS对象，输入标识，输入小数
tts(a, "ph", 1)


//检查是否TTS正在播放
//输入TTS对象，输入标识
tts(a, "ip", b)
syso(b)


//释放TTS使用的资源
//输入TTS对象，输入标识
tts(a, "re")


//停止所有任务
//输入TTS对象，输入标识，输入赋值变量
tts(a, "sp", b)
syso(b)


//检查是否一个可用的TTS对象
//输入TTS对象，输入标识，输入赋值变量
tts(a, "is", b)
syso(b)


说明：
常用于文本转化为音频，并且播放。


语言代码：
- 系统默认支持语言
美国    en
德国    de
意大利  it
法国    fr

- 需安装第三方语言包（讯飞语音TTS），并且设置语言
日本    ja
韩国    ko
中国    zh


安装与设置中文语言：

下载其中一个 
(4.0系统)讯飞语音TTS http://m.yx93.com/app.aspx?id=28515  
(2.2系统)讯飞语音TTS http://m.yx93.com/app.aspx?id=28513

安装 讯飞语音TTS

安卓手机》设置》语言和输入法》文本转语音输入》选择 讯飞语音合成 ,默认引擎 讯飞语音合成 , 语言 中文
（设置因为各品牌细节不同，但是都大同小异）


注意事项：
单独TTS对象创建后，需要有一个异步初始化过程，如果创建TTS对象然后直接播放文本将无法成功。需要先完成初始化后，然后播放文本。

注意事项：
文字转语音TTS输出；默认语言状态：完全支持 中文


【blp 录制屏幕】
用法：
s b = "123.mp4"
//输入储存录制文件路径，输入视频宽度，输入视频高度，输入视频码率，输入视频帧率
blp(b, 1280, 720, 1024000, 30)

//开始录制
blp("st", b)
syso(b)

//停止录制
blp("sp", b)
syso(b)

//释放资源
blp("re", b)
syso(b)

//判断是否正在录制
blp("ip", b)
syso(b)

说明：
用于手机屏幕录制。

注意：
仅支持系统Android 5.0以及以上才有效果！
Android 5.0以下的系统，无效果！

【otob 转换为字节组】
用法：
//将文件转换为字节组，字节组将为字符串形式返回赋值给“b”
otob("%abc.txt", b)
syso(b)

//将字符串转换为字节组
otob("utf-8", "nihao", b)
syso(b)
//不设置编码
otob(null, "nihao", b)

//将文件转换成 byte[] 字节数组对象
otob("file", null, "%abc.txt", b)
syso(b)

//将字符串转换成 byte[] 字节数组对象
otob("str", "utf-8", "nihao", b)
syso(b)


说明：
将字符或文件转换为字节组

【btoo 字节组还原】
用法：
otob("%abc.txt", b)
//将字节组转换为文件，变量 b 可为byte[] 字节数组对象
btoo(b, "%abc2.txt")


otob("utf-8", "nihao", b)
//字节组转换为字符串，变量 b 可为byte[] 字节数组对象
btoo("utf-8", b, c)
syso(c)

//不设置编码，变量 b 可为byte[] 字节数组对象
btoo(null, b, c)

说明：
将字节组转换为字符或文件

【sot Socket网络通信】
用法：
//服务端
//服务端口，临时文件目录，接受客户超时，客户连接超时，是否覆盖文件
sot(8668, "%iApp/tempSocket", 0, 0, false, b)
{
//消息内容
syso(st_msG)
//连接对象
syso(st_ssR)

}

//客户端
//服务地址，服务端口，服务连接超时，是否覆盖文件
sot("192.168.1.100", 8668, 0, false, b)
{
//消息内容
syso(st_msG)
//连接对象
syso(st_ssR)

}

//发送字符串，必须放在线程内
sot(b, "str", "nihao")

//发送文件，必须放在线程内
sot(b, "file", "%abc.txt")

//发送字节组，必须放在线程内
otob("utf-8", "nihao", c)
sot(b, "bt", c)

//发送不带信息头 byte[]字节组，必须放在线程内
sot(b, "bt2", bytes)

//关闭释放sot
sot(b, "re")

//获取sot是否已释放
sot(b, "ip", c)

//获取ID总数
sot(b, "id", c)

//获取连接对象列表
sot(b, "list", c)

//获取连接对象列表的第一位
sot(b, "list", 0, c)

//获取连接总数
sot(b, "size", c)

//是否允许接受新连接
sot(b, "new", true)


说明：
Socket 管理操作。服务端发送消息将批量发送给所有连接。

服务端说明：
要求：
1.能连接公共网络 或 内网
2.拥有固定IP作为客户端连接的目标
3.电脑、手机、平板电脑等设备上运行服务端。
4.可使用iapp在自己的手机上面开发服务端，并运行服务端。

客户端说明：
要求：
1.能连接公共网络 或 内网
2.可使用iapp在自己的手机上面开发客户端，并连接服务端。

常见开发：
使用手机或电脑作为服务端，手机客户端与服务端相互传递文件、数据等。

【sota 单个Socket通信操作】
用法：
//获取连接对象列表的第一位，变量“c”属于单个Socket通信
sot(b, "sl", 0, c)

//获取通信对方的IP
sota(c, "ht", d)

//获取sota是否已释放
sota(c, "ip", d)

//关闭释放sota
sota(c, "re")

//获取socket对象
sota(c, "socket", d)

//获取连接对象ID
sota(c, "id", d)

//发送字符串，必须放在线程内
sota(c, "str", "nihao")

//发送文件，必须放在线程内
sota(c, "file", "%abc.txt")

//发送字节组，必须放在线程内
otob("utf-8", "nihao", d)
sota(c, "bt", d)

//发送不带信息头 byte[]字节组，必须放在线程内
sota(c, "bt2", bytes)

说明：
常用于单个Socket通信的操作管理


【loadso 加载动态库】
用法：
//比如加载 libabc.so
loadso("abc")

说明：
加载SO动态链接库。


【loadjar 加载jar库】
用法：
//比如加载 abc.jar
//赋值变量 库对象
loadjar("abc.jar", b)
syso(b)

//比如加载 abc.apk
//包含Activity需要传入true，赋值变量 库对象
loadjar("abc.apk", true, b)
syso(b)

说明：
用于加载一些jar，dex，apk 的 sdk。需要把jar文件载入至项目资源，加载过程将联网校验。
如果附带SO动态链接库，需要把SO文件载入至项目资源。


【cls 获取完整接口类】
用法：
//获取一个类，输入完整类名如 java.lang.Math
//赋值变量 类对象
cls("java.lang.Math", a)
syso(a)

//获取一个字符串类，常用类型可直接输入类名如 String
cls("String", b)
syso(b)

//加载SDK abc.jar，并获取SDK里一个类 输入完整类名 com.sdk.abc
loadjar("abc.jar", a)
cls(a, "com.sdk.ceshi", c)
syso(c)

用法：
获取一个类；或从 jar SDK包获取类；

注意：完整类名区分大小写

【clssm 获取类的所有接口】
用法：
cls("String", b)

//获取所有构造函数
clssm(b, "init", c)

//获取所有函数方法
clssm(b, "method", c)

//获取所有变量
clssm(b, "field", c)


说明：
返回一个数组。


【java 调用java代码方法】
用法：
//调用java api java.lang.String.indexOf(String string) 查询字符56 在123456789 中位置
cls("String", c)
javax(a, "123456789", c, "indexOf", "String", "56")
syso(a)

//初始化一个StringBuilderd
javanew(a, "java.lang.StringBuilder", "String", "12345")
java(b, a, "java.lang.StringBuilder.append", "String", "6789")
java(c, a, "java.lang.StringBuilder.toString")
syso(c)


loadjar("test.jar", jar)
cls(jar, "com.sdk.ceshi", c1)
//调用静态方法 com.sdk.ceshi类 c 方法
javax(c, null, c1, "c", "int", 123)
syso(c)

//调用静态变量 com.sdk.ceshi类 a 变量
javags(c, null, c1, "a")
syso(c)

//初始化com.sdk.ceshi类
//输入赋值对象变量，输入完整类名或 cls方法的赋值变量
javanew(a, c1)

//访问变量，com.sdk.ceshi类 b变量
javags(c, a, c1, "b")
syso(c)

//设置变量，com.sdk.ceshi类 b变量
javass(c, a, c1, "b", "123456")
syso(c)


//设置回调方法
javanew(a, "android.widget.TextView", "android.content.Context", activity)
java(b, a, "android.widget.TextView.setText", "CharSequence", "我是文本控件")
//注意回调接口类名前面需要加一个“.”，如.android.view.View.OnClickListener
java(b, a, "android.view.View.setOnClickListener", ".android.view.View$OnClickListener", null)
{
//系统赋值
syso(st_mD)
syso(st_aS)

}


说明：
支持 android 所有的api；以及 自加载的jar SDK 的 api 

注意：完整类名或 方法名 或 变量名 区分大小写

activity：默认变量 Activity组件

javax 与 java 方法区别：
javax：第3位参数完整类名，第4位参数方法名。类名可传入 cls方法的赋值变量；
java：第3位参数 完整类名和方法名。


【javax 调用java代码方法】
用法：
loadjar("test.jar", jar)
cls(jar, "com.sdk.ceshi", c1)
//调用静态方法 com.sdk.ceshi类 c 方法
javax(c, null, c1, "c", "int", 123)
syso(c)

//调用静态变量 com.sdk.ceshi类 a 变量
javags(c, null, c1, "a")
syso(c)

//初始化com.sdk.ceshi类
//输入赋值对象变量，输入完整类名或 cls方法的赋值变量
javanew(a, c1)

//访问变量，com.sdk.ceshi类 b变量
javags(c, a, c1, "b")
syso(c)

//设置变量，com.sdk.ceshi类 b变量
javass(c, a, c1, "b", "123456")
syso(c)

说明：
常用于自定义SDK加载后的操作。

javax：第3位参数完整类名，第4位参数方法名。类名可传入 cls方法的赋值变量；

【javacb 自定义回调】
用法：

loadjar("test.jar", jar)
cls(jar, "com.ceshi.dex.main", c1)
javanew(o, c1)
cls(jar, "com.ceshi.dex.main$huidiao", c2)

javacb(hd, c2)
{
//系统赋值
syso(st_mD)
syso(st_aS)

}

//设置回调
javax(a, o, c1, "sethuidiao", c2, hd)
//调用回调方法
javax(a, o, c1, "get", "String", "666")

说明：
常用于设置自定义SDK的回调方法。


【res 安装包资源管理器】
用法：
//获取应用自己的对象
res(a)

//获取其他apk安装包内的资源对象，只支持加载SD卡上的apk
res("%abc.apk", a)

//获取资源
//输入资源对象，输入资源标识或文件名(没后缀)，输入资源类型，输入赋值变量
res(a, "ic_launcher", "drawable", b)

//获取资源ID，打包测试才有效
res(a, "ic_launcher", "drawable", false, b)

//获取 AssetManager 或 Resources 对象
res(a, "asset", b)
res(a, "resources", b)

说明：
可获取的资源类型 drawable、string、color、stringarray、layout


【call 交互式语言调用】
用法：

//输入赋值变量，语言类型，模块m的abc方法，输入参数1，输入参数2
call(null, "myu", "m.abc", "nihao", 66)


//输入赋值变量，语言类型，模块mk的abc方法，输入参数1
call(a, "mlua", "mk.abcd", 123)

//输入赋值变量，语言类型，模块mk的abc方法，，输入参数1，输入参数2，输入参数3
call(a, "mjava", "mk.abcd", 123, 456, 789 )


//没有参数的
//输入赋值变量，语言类型，模块mk的abc方法
call(null, "mjs", "mk.abcdf")

说明：
用于多语言的代码交互。

注意：
此方法只能调用模块方法，输入是字符串如 m.abc 模块m 的abc方法

注意：
参数数量要与实际模块方法的参数的数量一致。

注意：
三种语言，只有 mlua 可以返回赋值变量，裕语言可以通过设置全局变量变相返回变量， mjs设置赋值变量无效。


【json json数据解析】
用法：
//解析json数据
s text = "{"id":1, "name":"xiaobai", "age":16}"
json(text, jo)
//获取id
json(jo, "get", "id", a)
syso(a)
//获取name
json(jo, "get", "name", b)
syso(b)
//获取age
json(jo, "get", "age", c)
syso(c)

//修改age数据
json(jo, "set", "age", 20)

//删除id数据
json(jo, "del", "id")

//打印json数据
json(jo, "json", text)
syso(text)



//解析json列表数据
s text = "{"userlist":[{"id":1, "name":"niubi", "age":16},{"id":2, "name":"wangba", "age":18},{"id":3, "name":"goudan", "age":17}]}"
json(text, jo)

//打印json数据
json(jo, "list", "userlist", list)
json(list, "size", size)
w(size > 0)
{
s-(1, size)
json(list, "data", size, item)

//获取id
json(item, "get", "id", a)
syso(a)
//获取name
json(item, "get", "name", b)
syso(b)
//获取age
json(item, "get", "age", c)
syso(c)

}

说明：
常用于解析服务器反馈的数据。


【utb Toolbar工具栏设置】
用法：

//设置自定义的工具栏 为当前界面的工具栏
//输入Toolbar工具栏的 控件id或控件对象
s id = 3
utb(id)


//绑定侧滑控件，侧滑控件内需要包含左侧滑，绑定后可以在Toolbar工具栏的左图标 控制左边侧滑
//输入Toolbar工具栏的 控件id或控件对象，输入侧滑的 控件id或控件对象
utb(3, 2)


//设置参数

s id = 3
utb("set", "dshe", true)

//设置左图标，可以设置事件监听
utb("left", id, "@a.png")

//设置左图标的点击事件，注意此代码需在 utb(id) 后，否则事件将无效。
utb("set", "leftck", id)
{
syso("lefticon")
}

//设置右菜单图标，无事件。可使用界面菜单事件
utb("right", id, "@b.png")


//标题
utb("set", "title", "apptitle")

//子标题
utb("set", "subtitle", "appsubtitle")

//自定义布局可输入View类型布局
utb("set", "cv", v)

//显示选项
utb("set", "do", 0)

//显示或隐藏 标题
utb("set", "dste", true)

//显示或隐藏 自定义布局
utb("set", "dsce", true)

//显示或隐藏 主页图标
utb("set", "dshe", true)


//获取参数

//标题
utb("get", "title", c)

//子标题
utb("get", "subtitle", c)

//自定义布局可输入View类型布局
utb("get", "cv", c)

//显示选项
utb("get", "do", c)

//动作栏布局高度
utb("get", "height", c)


说明：
常用于设计应用顶部工具栏。

【tws 弹窗提醒】
用法：
//获取展示的控件对象，提醒将在这个控件里展示
gvs(1, v)

//无按钮弹出提醒
//输入控件对象可设置null，输入字符，输入显示时长（值0 -1 -2）
tws(v, "ni hao!", 0)


//有按钮弹出提醒
//输入控件对象可设置null，输入字符，输入显示时长（值0 -1 -2），输入按钮标题
tws(v, "ni hao ma?", 0, "hao")
{
syso("go")
}

【uht 滑动窗体控制】
用法：

//添加新的页面，设置的界面会执行载入事件里的代码
//输入滑动窗体的 控件id或控件对象，输入标识，输入插入序号 如-1为尾部 0为头部，输入标题，输入界面名，输入控件对应的数据项...不限制数量可参考代码ula
uht(2, "add", -1, "标题", "a.iyu", 1="abc", 2="bac", 3="bbc")

//删除界面
//输入滑动窗体的 控件id或控件对象，输入标识，输入界面序号 序号以0开始 -1为尾部
uht(2, "del", 0)

//修改界面标题
//输入滑动窗体的 控件id或控件对象，输入标识，输入界面序号 序号以0开始 -1为尾部
uht(2, "title", 0, "标题2")

//获取页面总数
uht(2, "size", b)
syso(b)

//释放内存
uht(2, "close")


//绑定标签布局，绑定后滑动界面时标签布局会跟随运动，需要注意 标签布局 和 滑动窗体 的子项数量应一致，新增子项时也需要同时增加
//输入滑动窗体的 控件id或控件对象，输入标识，输入标签布局的 控件id或控件对象，是否应刷新其内容
uht(2, "bd", 3, true)
//注意：如果绑定前 标签布局 如有设置子项，绑定时会被清空。绑定后直接添加滑动窗体 的子项并设置 标题


//增加标签布局 的子项
us(3, "app_tabadd", "选项")

//添加滑动窗体 的子项
uht(2, "add", -1, "标题", "a.iyu", 1="abc", 2="bac", 3="bbc")


说明：
用于动态管理控制滑动窗体和垂直滑动窗体的 新增页面、删除页面、绑定标签布局等。


【cast 强制转换数据类型】
用法：

s a = 123
//转换数据类型并直接赋值
//输入完整类名 或 类对象，输入需要转换的数据变量
cast("String", a)
syso(a)

//获取类对象
cls("java.lang.Math", a)
//输入完整类名 或 类对象，输入需要转换的数据变量，输入赋值变量
cast(a, b, c)
syso(c)

说明：
常用于数据强制转换。


【yul 加载yul布局】
用法：

//将布局加载展示到指定的布局控件里
//输入控件id或控件对象（比如输入线性布局ID），输入 yul 布局文件名
yul(1, "a.yul")


//返回布局对象
//输入 yul 布局文件名，输入赋值变量返回一个View对象
yul("a.yul", a)
syso(a)


说明：
yul布局是以 android 的 xml布局为基础，用于动态加载布局到应用界面。和安卓xml布局用法和代码都是一致的。

在设计 yul布局 时需要自定义控件ID，如设置控件ID:123 编写代码 android:id="123" 或 android:id="@+id/s123" 两种写法都可以，效果都是ID为 123



【zj 组件控制】
用法：
//如有米广告组件，首先下载有米的组件，并且设置好组件。

//初始化有米SDK，放在第一个界面的载入事件里
//输入赋值变量，标识，发布 ID，密钥，是否开启有米的Log输出（需要换自己的渠道信息）
zj(a, "init", "String", "85aa56a59eac8b3d", "String", "a14006f66f58d5d7", "boolean", true)

//初始化积分墙
//输入赋值变量，标识
zj(a, "initjfq")

//展示积分墙
zj(a, "jfqgo")


说明：
用于控制组件。

【无障碍服务】
用法：
固定模块名为 ays_service 可创建模块 ays_service.myu，代码如下：

//事件方法 on 实时回调变化事件
fn on(e)
//获取事件类型
java(b, ays, "com.iapp.app.ays.gtype", "android.view.accessibility.AccessibilityEvent", e)
//如果事件类型
f(b == 32 || b == 2048){
  //获取事件源的对象节点列表
  java(node, ays, "com.iapp.app.ays.gall", "AccessibilityEvent", e)
  //判断事件来源是不是包名为com.iapp.app的应用
  java(gpn, ays, "com.iapp.app.ays.gpn", "AccessibilityEvent", e)
  f("com.iapp.app" == gpn)
  {
     //判断类名，根据指定的类名进行不同的操作
     java(gcn, ays, "com.iapp.app.ays.gcn", "AccessibilityEvent", e)
     f("com.iapp.app.HomeMian" == gcn)
     {
        //从对象列表搜索文本为“创建”的对象，并点击该对象
        java(b, ays, "com.iapp.app.ays.cktext", "AccessibilityNodeInfo", node, "int", 16, "String", "创建")
     }
     else f("com.iapp.app.HomeAdd" == gcn)
     {
        //根据ID获取指定的节点
        java(b, ays, "com.iapp.app.ays.id", "AccessibilityNodeInfo", node, "String", "com.iapp.app:id/ui_home_add_title")
	//设置节点的文本框输入指定字符
        java(c, ays, "com.iapp.app.ays.enter", "java.util.List", b, "String", "name")
        //根据ID获取指定的节点
        java(b, ays, "com.iapp.app.ays.id", "AccessibilityNodeInfo", node, "String", "com.iapp.app:id/ui_home_add_remark")
	//设置节点的文本框输入指定字符
        java(c, ays, "com.iapp.app.ays.enter", "java.util.List", b, "String", "remark")
        //从对象列表搜索指定ID的对象，并点击该节点对象
        java(b, ays, "com.iapp.app.ays.ckid", "AccessibilityNodeInfo", node, "int", 16, "String", "com.iapp.app:id/ui_home_add_go")
     }
  }
  //释放根源节点
  java(b, ays, "com.iapp.app.ays.re", "AccessibilityNodeInfo", node)

}

end fn

//初始化事件方法 onsc 启动时回调一次
fn onsc()
s pns = "com.iapp.app"
//设置监听指定的包名，可以设置多个包名用逗号隔开如"com.xxx.a,com.xxx.b"
javass(a, null, "com.iapp.app.ays.pns", pns)
//设置相应时间
javass(a, null, "com.iapp.app.ays.nt", 1000)
end fn


然后 权限配置管理》application配置 将下面的配置粘贴进去：
	<service
            android:name="com.iapp.app.ays"
            android:label="iapp开发工具无障碍辅助功能"
            android:permission="android.permission.BIND_ACCESSIBILITY_SERVICE">
            <intent-filter>
                <action android:name="android.accessibilityservice.AccessibilityService"/>
            </intent-filter>
            <meta-data
                android:name="android.accessibilityservice"
                android:resource="@xml/aya_config"/>
        </service>

最后，【正式打包发布】打包完成后，安装测试。记得自行去设置》辅助功能》打开我们的服务《iapp开发工具无障碍辅助功能》。
注意：直接在iapp里测试无效。


更多代码示范：

//------静态调用
//获取无障碍功能是否已经授权
java(a, null, "com.iapp.app.ays.isas", "Context", activity)

//如果没有授权，可跳转设置界面
java(a, null, "com.iapp.app.ays.goset", "Context", activity)


//------事件源操作
//获取Context功能类
java(a, ays, "com.iapp.app.ays.gbc")

//获取无障碍功能配置信息
java(a, ays, "com.iapp.app.ays.gsi")

//设置无障碍功能配置信息
java(b, ays, "com.iapp.app.ays.ssi", "AccessibilityServiceInfo", a)

//调用全局事件
//输入值：1. 返回键 2. HOME键 3. 最近打开应用列表 4. 打开通知栏 5. 设置 6. 锁屏
java(a, ays, "com.iapp.app.ays.pga", "int", 1)

//获取事件类型
//值：32 打开PopupWindow，Menu，Dialog等的事件  64 显示通知的事件  2048 更改窗口内容的事件  4194304 屏幕上显示的窗口中的事件更改
java(a, ays, "com.iapp.app.ays.gtype", "AccessibilityEvent", e)

//获取事件源类的类型
java(a, ays, "com.iapp.app.ays.gcn", "AccessibilityEvent", e)

//获取事件源的包名
java(a, ays, "com.iapp.app.ays.gpn", "AccessibilityEvent", e)

//获取事件源的是否可用
java(a, ays, "com.iapp.app.ays.ised", "AccessibilityEvent", e)

//获取事件源的节点总数
java(a, ays, "com.iapp.app.ays.gsl", "AccessibilityEvent", e)

//获取事件源的整数ID
java(a, ays, "com.iapp.app.ays.gwid", "AccessibilityEvent", e)

//获取事件源的时间
java(a, ays, "com.iapp.app.ays.gtime", "AccessibilityEvent", e)

//释放资源
java(a, ays, "com.iapp.app.ays.re", "AccessibilityEvent", e)


//------节点的操作
//获取事件源的节点对象列表
java(a, ays, "com.iapp.app.ays.gall", "AccessibilityEvent", e)

//获取窗口的对象节点列表，需要Android 4.1及以上才可调用
java(a, ays, "com.iapp.app.ays.gall")

//根据序号；获取对象的子节点
java(a, ays, "com.iapp.app.ays.gi", "AccessibilityNodeInfo", node, "int", 0)

//获取对象的子节点总数
java(a, ays, "com.iapp.app.ays.gi", "AccessibilityNodeInfo", node)

//根据当前焦点向某个方向进行搜索可以获得输入焦点的最近控件
//输入值：33 向上  130 向下  17 向左  66 向右
java(a, ays, "com.iapp.app.ays.focussearch", "AccessibilityNodeInfo", node, "int", 130)

//根据文本查询控件，返回节点列表
java(nodelist, ays, "com.iapp.app.ays.text", "AccessibilityNodeInfo", node, "String", "创建")

//根据id查询控件，返回节点列表
java(nodelist, ays, "com.iapp.app.ays.id", "AccessibilityNodeInfo", node, "String", "com.iapp.app:id/ui_home_add_go")

//根据焦点查询
//输入值：1 输入焦点  2 可访问性焦点
java(a, ays, "com.iapp.app.ays.focus", "AccessibilityNodeInfo", node, "int", 1)

//获取节点文本
java(a, ays, "com.iapp.app.ays.gt", "AccessibilityNodeInfo", node)

//获取节点类的类型
java(a, ays, "com.iapp.app.ays.gcn", "AccessibilityNodeInfo", node)

//获取节点整数ID
java(a, ays, "com.iapp.app.ays.gwid", "AccessibilityNodeInfo", node)

//获取节点ID
java(a, ays, "com.iapp.app.ays.gid", "AccessibilityNodeInfo", node)

//获取可以在节点上执行的操作
java(a, ays, "com.iapp.app.ays.gal", "AccessibilityNodeInfo", node)

//获取节点在屏幕上坐标
java(a, ays, "com.iapp.app.ays.gbis", "AccessibilityNodeInfo", node)

//获取父节点在屏幕上坐标
java(a, ays, "com.iapp.app.ays.gbip", "AccessibilityNodeInfo", node)

//获取节点的包名
java(a, ays, "com.iapp.app.ays.gpn", "AccessibilityNodeInfo", node)

//获取节点的父节点
java(a, ays, "com.iapp.app.ays.gp", "AccessibilityNodeInfo", node)

//获取此节点是否可点击
java(a, ays, "com.iapp.app.ays.isck", "AccessibilityNodeInfo", node)

//获取此节点是否已启用
java(a, ays, "com.iapp.app.ays.ised", "AccessibilityNodeInfo", node)

//获取此节点是否已选中
java(a, ays, "com.iapp.app.ays.iscd", "AccessibilityNodeInfo", node)

//获取这个节点是否被聚焦
java(a, ays, "com.iapp.app.ays.isfd", "AccessibilityNodeInfo", node)

//获取此节点是否可以长时间点击
java(a, ays, "com.iapp.app.ays.islck", "AccessibilityNodeInfo", node)

//获取此节点是否是密码
java(a, ays, "com.iapp.app.ays.ispd", "AccessibilityNodeInfo", node)

//获取节点是否可滚动
java(a, ays, "com.iapp.app.ays.isse", "AccessibilityNodeInfo", node)

//获取是否选择此节点
java(a, ays, "com.iapp.app.ays.issd", "AccessibilityNodeInfo", node)



//根据文本查询；模拟控件点击控件
java(a, ays, "com.iapp.app.ays.cktext", "AccessibilityNodeInfo", node, "int", 16, "String", "创建")

//根据ID查询；模拟控件点击控件
java(a, ays, "com.iapp.app.ays.ckid", "AccessibilityNodeInfo", node, "int", 16, "String", "com.iapp.app:id/ui_home_add_go")

//根据焦点查询；模拟控件点击控件
//输入值：1 输入焦点  2 可访问性焦点
java(a, ays, "com.iapp.app.ays.ckfocus", "AccessibilityNodeInfo", node, "int", 16, "int", 1)


	/.
	  模拟执行操作
	  1 将输入焦点输入到节点的操作
	  16 点击节点信息的动作
	  32 长时间点击节点的动作
	  32768 操作来粘贴当前的剪贴板内容
	 ./
//开始模拟控件点击
//输入节点列表
java(b, ays, "com.iapp.app.ays.ck", "java.util.List", nodelist, "int", 16)

//开始模拟控件点击
//输入节点列表，输入自定义的Bundle
java(b, ays, "com.iapp.app.ays.ck", "java.util.List", nodelist, "int", 16, "android.os.Bundle", be)

//对单项模拟控件点击
//输入节点列表
java(b, ays, "com.iapp.app.ays.ck", "AccessibilityNodeInfo", node, "int", 16)

//对单项模拟控件点击
//输入节点列表，输入自定义的Bundle
java(b, ays, "com.iapp.app.ays.ck", "AccessibilityNodeInfo", node, "int", 16, "android.os.Bundle", be)

//对单项模拟执行输入文本,Android 4.3 版本及以上
java(b, ays, "com.iapp.app.ays.enter", "AccessibilityNodeInfo", node, "String", "nihao")

//开始模拟执行输入文本,Android 4.3 版本及以上
java(b, ays, "com.iapp.app.ays.enter", "java.util.List", nodelist, "String", "nihao")

//获取节点所有子节点列表
java(nodelist, ays, "com.iapp.app.ays.ganiall", "AccessibilityNodeInfo", node)

//释放节点资源
java(b, ays, "com.iapp.app.ays.re", "AccessibilityNodeInfo", node)

说明：
无障碍功能（辅助功能）常用于简化操作，使应用或 系统的变得更智能、简便。


【自定义代码提示】
说明：
iapp允许开发者自定义代码提示，这样可以最大程度保留开发者的个人习惯，可以定义成你自己熟悉的关键词。

格式：
代码\说明
如：
abcde\变量名
abc()\方法名


配置对应文件：/data/data/com.iapp.app/files/config/srctonew.xml

【HTML5项目】
例子：
//输入浏览器控件ID或对象，输入标识，输入项目网页路径
us(1, "url", "@html5/index.html")
//us(1, "url", "%html5/index.html")

说明：
常用与运行一个HTML5项目，包括HTML5应用、HTML5游戏等。

【上传项目】

项目内导入覆盖规则：

	综合：一个完整应用项目的导入；先清空当前项目源码与资源后，导入源码与资源 以及根据需求导入项目信息与图标

	其他分类通用：
	1. 项目中mian.iyu启动界面，只导入其中有备注的控件，导入至当前项目打开的界面里；
	2. 不清空当前项目文件，直接覆盖除了mian.iyu以外的其他所有界面与资源；
	3. 覆盖过程如有模块文件重复，将以追加方式模块增加，不覆盖；
	4. 建议复杂命名界面名，复杂命名模块方法名；

项目外导入覆盖规则：
	1. 遇本地重复项目，不覆盖。
	2. 导入为完整项目。

说明：
分享技术，享受乐趣。

【代码规范】
例子：
//下面的判断语句，使用了字符串；存在规范问题，会出错；
f("1?2(3}4,5==6" == "1?2(3}4,5==6")
{
f("a"!=sb" != "a"!=sb6")
{
tw("{1},(2)")
}
}

转义关键符号，需修正为：
f("1\?2(3}4\,5\=\=6" == "1\?2(3}4\,5\=\=6")
{
f("a"\!\=sb" != "a"\!\=sb6")
{
tw("{1}\,(2)")
}
}

//下面判断读取文本文件，
fr("%ab,c.txt", "utf-8", c)
tw(c)

转义关键符号，需修正为：
fr("%ab\,c.txt", "utf-8", c)
tw(c)

以上为规范异常，系统关键符号需要进行转义，转义在符号前增加“\”。

系统关键符号(小写符号)：( ) , = ! > < ? * + { } | &

注意：
“\”作为转义符号需注意例子：

.例子1
tw("ni\nhao")
/.
输出：
ni
hao
./

.例子2
tw("ni\\nhao")
/.
输出：
ni\nhao
./

.例子3
tw("ni\\hao")
/.
输出：
ni\hao
./

.例子4
tw("ni\hao")
/.
输出：
ni\hao
./

.例子5
tw("ni\\\\hao")
/.
输出：
ni\\hao
./

.例子6
tw("ni\,hao")
/.
输出：
ni,hao
./

【单击触屏事件】

系统赋值：
st_vId：控件id
st_vW：控件对象

说明：
该事件无返回值，当用户完成单击触屏即执行事件代码。

【触屏监听事件】
用法：
[true]
tw("将返回值为true")

系统赋值：
st_vId：控件id
st_vW：控件对象
st_eA：执行的动作
st_eX：触屏位置X坐标
st_eY：触屏位置Y坐标
st_rX：原始位置X坐标
st_rY：原始位置Y坐标

说明：
该事件有返回值，不设置返回值将默认为false。当用户触屏屏幕即执行事件代码。

返回值说明：
在事件代码编辑框顶部一行填写 “[true]”，即设置为返回true
当返回true值时，说明已完成该事件的执行，将不在执行此事件。
当返回false值时，将持续执行当前事件。

【触屏长按事件】
用法：
[true]
tw("将返回值为true")

系统赋值：
st_vId：控件id
st_vW：控件对象

说明：
该事件有返回值，不设置返回值将默认为false。当用户长久触屏屏幕即执行事件代码。

返回值说明：
在事件代码编辑框顶部一行填写 “[true]”，即设置为返回true
当返回true值时，说明已完成该事件的执行，将不在执行此事件。
当返回false值时，将持续执行当前事件。

【键盘触发事件】
用法：
[true]
tw("将返回值为true")

系统赋值：
st_vId：控件id
st_vW：控件对象
st_kC：按下的物理按键对应的数值
st_eA：执行的动作
st_eR：

说明：
该事件有返回值，不设置返回值将默认为false。当用户按下物理按键即执行事件代码。

返回值说明：
在事件代码编辑框顶部一行填写 “[true]”，即设置为返回true
当返回true值时，说明已完成该事件的执行，将不在执行此事件。
当返回false值时，将持续执行当前事件。

【触屏长按菜单事件】
用法：
title:操作
case 选择A:
tw("A")
break
case 选择B:
tw("B")
break
case 选择C:
tw("C")
break
default:
tw("载入成功")
break

系统赋值：
st_vId：控件id
st_vW：控件对象

说明：
常用于需要多操作选项。

【框编辑监听事件】
用法：
[true]
tw("将返回值为true")

系统赋值：
st_vId：控件id
st_vW：控件对象
st_aI：动作的标识数值
st_eA：执行的动作
st_eR：
st_eK：键值

说明：
该事件有返回值，不设置返回值将默认为false。当用户按下动作键即执行事件代码。

注意：
需要编辑框设置相应的控件 imeoptions 属性

事件例子：
f(st_aI != 0)
{
//动作的标识数值
syso(st_aI)
}

返回值说明：
在事件代码编辑框顶部一行填写 “[true]”，即设置为返回true
当返回true值时，说明已完成该事件的执行，将不在执行此事件。
当返回false值时，将持续执行当前事件。


【文本更新监听事件】

系统赋值：
st_vId：控件id
st_vW：控件对象
st_sS：文本内容
st_sT：
st_bE：
st_cT：
st_aR：

说明：
该事件无返回值。常用于监听文本即时更新。

【获得焦点事件】

系统赋值：
st_vId：控件id
st_vW：控件对象
st_hF：是否获得焦点

说明：
该事件无返回值，当控件获得/失去焦点即执行事件代码。

【触屏滑动事件】

系统赋值：
st_vId：控件id
st_vW：控件对象
st_sE：
st_fM：
st_vT：
st_bT：

说明：
常用于滑动控件的滑动监听。


【单击项目事件】

系统赋值：
st_vId：控件id
st_vW：控件对象
st_pN：被点击视图中的位置
st_iD：被点击的项目

说明：
常用于列表项点击监听。

【浏览器事件】

说明：
常用于浏览器的互动。

【滑动窗体事件】

说明：
常用于滑动窗体的互动。

【侧滑窗体事件】

说明：
常用于侧滑窗体的互动。

【下拉菜单事件】

说明：
常用于下拉菜单的互动。

【摄像头拍摄事件】

说明：
常用于摄像头拍摄事件的互动。

【载入事件】

说明：
将于界面加载完毕后执行。

【载入完毕事件（界面可交互）】

说明：
将于界面加载完毕后，并且用户可于界面交互时执行。常用需要在载入事件中设置控件属性。

如：
使用 addv 添加将界面后，如果设置控件属性，请将设置属性的代码写入 载入完毕事件中。

【菜单事件】
用法：
case 选择A:
tw("A")
break
case 选择B:
tw("B")
break
case 选择C:
tw("C")
break
default:
tw("载入成功")
break


//参数为多个并以“|”隔开
//参数1为选项标题|参数2为图标|参数3为显示动作值分别为0 1 2 4 8|参数4为次序根据数值大小
带图标的
case 选择A|@a.png|1|1:
tw("A")
break
case 选择B|@b.png|0|2:
tw("B")
break
case 选择C|@c.png|0|3:
tw("C")
break
default:
tw("载入成功")
break


说明：
当用户触屏菜单事件。

【按键按下事件】

说明：
用户设备物理按键按下将执行。

【按键释放事件】

说明：
用户设备物理按键按下然后释放触屏，将执行。

【销毁界面事件】

说明：
当用户销毁当前界面时将执行。

【停止事件】

说明:
界面处于停止或暂停事将执行。（如：用户切出到其他应用）

【重新开始事件】

说明：
界面重新获得焦点，可视时将执行。（如：用户从其他应用切换回来了）

【回调结果事件】

系统赋值：
st_sC：请求标识数值
st_lC：结果状态数值
st_iT：结果目标对象

说明：
常用于界面或功能回调返回的结果或传递的数据。

【重力感应事件】

系统赋值：
st_x：X轴
st_y：Y轴
st_z：Z轴

说明：
获取手机的即时动作。

参考：
　　手机屏幕向上(z轴朝天)水平放置的时侯，(x，y，z)的值分别为(0，0，10);
　　手机屏幕向下(z轴朝地)水平放置的时侯，(x，y，z)的值分别为(0，0，-10);
　　手机屏幕向左侧放(x轴朝天)的时候，(x，y，z)的值分别为(10，0，0);
　　手机竖直(y轴朝天)向上的时候，(x，y，z)的值分别为(0，10，0);
