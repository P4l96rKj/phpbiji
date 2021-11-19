纯纯写作

PHP

PHP基础

# <p align="center">PHP基础</p> 
## 1.静态网站和动态网站
静态:**没有**数据交互的网站(.html .htm)
动态:**支持**数据交互的网站 实现动态网站的技术
>ASP .asp  
>PHP .php  
>.net .aspx  
>Java .jsp  
## 2.客户端和服务器端
　　客户端给服务器端发送一个http请求，服务器端把静态资源(html,js,css)发送给客户端(http响应)，客户端通过浏览器解析返回的代码，形成了页面。  
　　动态页面，则会先经过php预处理，将处理结果(静态页面)返回给客户端，**客户端看不到php代码**。
## 3.端口
端口号范围0-65535 **1024**以内保留给系统
Windows使用`netstat -ano`查看端口占用
>80端口-Web服务  
>21端口-FTP服务  
>25端口-邮件服务  
>3306端口-MySQL服务  
## 4.B/S架构 C/S架构  
B/S浏览器/服务器
C/S客户端/服务器
## <font color="red">5.什么是PHP</font>
　　**超文本预处理器开源脚本语言。**
运行原理：
　　运行在服务器端的,内嵌在html中的脚本语言。
### 集成环境有哪些
> * phpstudy xmapp vampserver... 
> * php(编程语言)、>mysql(数据库)、apache(web服务器软件)
> * 访问: localhost 本机服务器/php文件服务器软件 & 127.0.0.1 本机的ip地址/php文件
> * 注意:php文件写在网站根目录下
D:\phpStudy_pro\www
> * 工具: vscode hbuider sublime...
> * phpinfo();显示php信息函数。

PHP基本语法

# <p align="center">PHP基本语法</p>
## 1.php标记
- 标准 `<?php ?>`  
- 设置编码格式：
```
header("Content-Type:text/html;charset=utf-8");
```
- 输出 `echo` 变量/常量/字符串
- var_dump() 数组/变量类型/值
- gettype() 只获取类型 echo gettype($a)
- print_r() 数组
## 2.注释
- //单行注释
- #单行注释
- /*
多行注释
*/
## 3.标识符命名规则
- 只能由字母、数字、下划线组成，**不能以数字开头**。
- userName user_name
- 见名知意
- 区分大小写：变量名，常量名，属性名。
- 不区分大小写：函数名、方法名、接口名、类名。
## 4.关键字：不区分大小写

## 5.常量
当一个值在脚本执行周期内不发生变化，就可以声明成常量。
- **自定义常量：**
>define(常量名,常量值);  
>define('name','张三');  
>define('PAI',3.14);  
>默认区分大小写  
>define('PAI',3.14,true); “true”表示不区分大小写  
（低版本）  
<font color="red">**常量不能重复定义**</font>  
```
if(!defined('PAI')){
define('PAI',3.14);
}
```
- **预定义常量**
> 1. 核心常量
>PHP_VERSION   PHP版本
>PHP_OS            操作系统
> 2. php扩展功能携带的常量，例如开启和关闭MySQL扩展。
get_defined_constants()得到所有的常量
在php.ini配置文件中修改
**extensiona＝php_mysqli.dll**
> 3. 魔术常量（不区分大小写）  
__FILE__文件名  
__DIR__目录  
__LINE__行号  
## 6.变量
在程序执行期间可以变化的量，用变量保存值，变量是计算机内存中的一段。
### 1.变量的赋值方式：
 - 传值赋值方式
 ```
 $a = 10;
$b = $a;
$a++;
echo $b;     10
 ```
 - 传址赋值方式
 `$b = &$a;`

### 2.变量的数据类型（用`var_dump`输出类型和值）
#### 标量类型
- **布尔型** bool： `true` `false`
- **整形** int： 存放整数 （PHP_INT_MAX 最大整数）
- **浮点型** float： 存放小数
- **字符串** string： 单引号字符串和双引号字符串  
{双引号解析变量，单引号不解析变量（执行效率高）  
单引号只解析`\'`和`\\`转义字符}
#### 复合类型
##### 数组array：计算机内存中一段连续空间，通过下标区分数组。
1. 索引数组：通过元素位置进行下标。
```
$stu = array('小明','小华','小李');
echo $stu[0];
```
2. 关联数组：用字符串作下标。
```
$stu = array('name'=>'张三',
'gender'=>'男',
'age'=>18
);
var_dump($stu2);
echo $stu2['name'];
```
##### 对象object
#### 资源类型 `resource`  
php的外部数据称为资源  
`$res = fopen('text.txt','r');`
#### 空null
未声明的变量值为`null`  
声明变量赋值为`null`  
通过`unset()`注销的变量  
3. 数据类型检测
> is_int() is_float() is _string() is_bool() is_array()  
> is_object() is_resource() is_null()
> is_numeric() 检测是否为数值或数值型字符串
4. 可变变量：
变量名由另一个变量充当
`$$nickname`
5. 数据类型转换
- 自动类型转换
* 1. 转换为布尔型  
 数值型->布尔型：0值转换为false  
 字符串型->布尔型：' ' 和'0'转换为false  
 数组->布尔型：array()转换为false  
所有的 对象\资源 ->布尔型均为true  
 null->布尔型为false
* 2. 转换为整型（浮点型）
 从字符串开头开始，将符合整型（浮点型）规则的部分提取转换，如果开头没有则转换为0。
- 强制类型转换
（目标类型）数据`（int）$name`  
目标类型：int float string object bool array 
unset（转换为空） <font color="red">不能转换为资源类型</font>
**注意：源数据类型没有改变。**
修改变量数据类型setType（变量，类型）
`setType（$name,'int'）`
7. 运算符
- 1. 算术运算符
 `+ - * / %（取余） ++自增 --自减`
`++$a ++前置` 先自增再输出
`$a++ ++后置` 先输出再自增
- 2. 字符串连接运算符
变量.变量
- 3. 赋值运算符
= 
自赋值运算符
`+= -= *= /= .=`
- 4. 比较运算符
`> >= < <=` `==相等` `!=` `===全等` `!==`
- 5. 逻辑运算符
用来连接表达式
&&与     ||或       !非
`$ch>=99&&&math>=90`
- 6. 三元运算符
`3>2?'ture':'false'`
- 7. 错误抑制符 @
运算符优先级：括号最优先，赋值最低。
!>算数>比较>逻辑
8. 流程控制语句
- * （1）. 多分支
```
if(条件){
}
elseif(条件){
}
else{
}
```
判断是否点击提交按钮
```
if(isset($_POST['btn'])){

}
```
- * （2）. 多路选择
```
switch(表达式)
{case 常量1:
        代码1;
        [break;]
case 常量2:
        代码2;
        [break;]
default:
        代码3;
}
```
![多语句选择流程图](https://i.loli.net/2021/09/20/byGVrSXN2KfmDTt.jpg)
- * （3）.循环语句
* 1. for循环
```
for(初始值;条件;增量){
//循环体
}
```
* 2. while循环
```
while(条件){
//循环体
增量
}
```
* 3. do_while循环
```
do{
//循环体
}while(条件);
```
* 4. foreach **用来遍历数组**
- 语法1（值）：
```
foreach（数组 as 值变量）{
//循环体
}
```
- 语法2（取键和值）：
```
foreach（数组 as $key=>$valve）{
//循环体
}
```
- * （4）.跳转语句
`break`：**中断循环**
`continue`：**结束当前循环进入下一个循环**

函数

# <p align="center">函数</p>
## 1.自定义函数
```
function 函数名(参数){
//函数体
[return]
}
```
1. return
- 终止函数执行
- 返回值，返回到调用函数的地方（没有输出）
2. 变量的作用域
- 局部作用域
一个函数内部范围---局部变量
- 全局作用域
函数外部的范围---全局变量
- 超全局作用域
函数的内部和外部---超全局变量
`$_POST` `$_GET` `$_REQUEST` `$_SERVER` `$_SESSION` `$_COOKIE` `$_FILES` `$GLOBALS`

### 局部作用域使用全局变量
* 方法一：使用`global`
```
$v2 = 2; //全局变量
function fun2(){
  global $v2; //在函数内部声明一个和全局变量同名的局部变量
  echo $v2.'<br>';
  $v2 = 22;
  unset ($v2);
}
```
* 方法二：使用超全局变量`$GLOBALS`
```
$v4 = 4;
function fun4(){
  echo $GLOBALS['v4'].'<br>'; //使用全局变量的另一种使用形式
  $GLOBALS['v4'] = 44;
  unset ($GLOBALS['v4']); // 全局变量也销毁
}
```
3. 可变函数  
函数名由一个变量充当
4. 嵌套调用  
5. 递归调用  
 **求n!**
```
function fun5 ($n){
    if($n==1){
      return 1;
  }
  return $n*fun5($n-1);
}
```
## 2. 字符串相关函数
1. `exlode`将字符串使用某个分隔符拆分成一个数组
`$arr = explode('-',$str);`
2. `implode`将数组中的元素利用某个分隔符连成一个字符串

3. `strcmp($str1,$str2)`字符串比较（ASCII码）
***返回值*** 
> 小于0     `$str1<$str2`
> 大于0     `$str1>$str2`
> 等于0     相等  

补充：
> `strCasecmp()`不区分大小写
> `strNcmp($str1,$str2,n)`仅比较前n位

4. str_replace(查找,替换,原字符串)
5. substr 截取
　　substr（字符串，起始位置从0开始，[长度]）
　　strstr（字符串，匹配字符）
6.strlen 长度
　　UTF-8编码格式下汉字占3个字节
7. trim 去两端空格
　　Ltrim() 去左边
　　Rtrim() 去右边
8. 大小写转换
　　strtolower 全部小写
　　strtoupper 全部大写
　　Uefirst 首字母大写
9. 查找函数
strpos（字符串，查找的字符）**首次**出现的位置
strrpos（字符串，查找的字符）**最后**出现的位置
* 数学函数
`max() min() rand(0,10)`得到一个随机数
`mt_rand()`效率更高 `rand($a,2)`四舍五入
`ceil()`向上取整 `floor`向下取整
## 3. 日期和时间函数
1. 获取时间
`time()`获得当前的时间戳  
`mktime`(时，分，秒，年，月，日）  
`Microtime()`获取精确时间，精确到微妙  
　　true 默认返回字符串，加true，返回float
`strtotime()`转换为时间戳  
　　strtotime('2020-02-29 01:02:03');  
　　strtotime('+1 week');  
　　strtotime('-3 days');  
2. 格式化输出时间
　　`date()`格式化本地时间
`date('Y-m-d H-i-s',$time);`  
`date('D-M-Y H-i-s',$time);`  
　　`gmdate()`格式化格林威治平时
gmdate(),'GMT';  
3. 设置时区
配置文件`php.ini`，查看时区。  
`date.timezone=Asia/Shanghai`  
代码中设置时区  
`date_default_timezone_set('PRC');`  
获取时区  
`date_default_timezone_get();`    

+ 利用手册查找函数  
`str_repeat()`  
`str_shuffle()`  
+ 设置编码格式
`header("content-type:text/html;charset=utf-8");`

数组

# <p align="center">数组</p>
## 1. 含义：一系列数据的集合
分类：
* 索引数组
* 关联数组
## 2. 定义
`$arr[]=3;` `$arr[]=5];`
## 3. 数组取值
`$name = $stu['name'];`
## 4. 删除数组
- `unset($arr['age']);` //删除一个数组元素
- `unset($arr);`  //删除整个数组
## 5. 数组运算符
`+`将右边的数组合并到左边数组的后边，得到一个新数组，如果有重复键以左边为准
`==`相同的键名和键值（可以顺序不同，类型不同）
## 6. 数组指针函数
* `next()`将数组的内部指针向**前**移动指针
* `prev()`将数组的内部指针向**后**移动指针
* `current()`获取数组当前元素的值
* `key()`获取当前元素的下标（键名）
* `end()`将数组的内部指针移动到结尾
* `reset()`重置指针，将数组指针指向第一个元素  

**当指针位置非法时**：
current返回`false`，key返回`null`
使用reset()或end()  

`each()`获得当前元素的键和值，并且数组指针向前移动一位

双份存储 `0 key键` `1 value值`

- 利用while和each遍历数组
```
while($v1 = each($srr)){
　　echo $v1[1].'<br>';
}
```
- 利用foreach遍历数组
```
foreach($数组名 as [$key=>]$value){
}
```
- 利用list(),while(),each()遍历数组
　　list()取得一个数组中从0开始的数字下标的多个单元的值
list（变量1，变量2，变量3…）=数组
　　`变量1=$数组[0]`
　　`变量2=$数组[1]`
```
while(list ($key $value)=each($arr)){
　　each "{$key} => {$value}<br>";
}
```
## 7. 操作数组基本函数
* `is_array()`判断是否为数组
* `count()`统计数组中元素的个数
* `array_unique`移除数组中的重复元素
1. 键值对相关函数
> - `array_search()`在数组中查找某个元素的值，返回该元素的键  
> - `array_search` (待查找的值，数组，true);严格比较（类型值）  
> - `array_keys()`取得数组中所有的**键**，形成索引数组  
> - `array_values()`取得数组中所有的**值**，形成索引数组  
2. 其他函数
sort(); 按照值，升序排序。不保持键值关联，下标重排。
rsort(); 降序
asort(); 下标保留
ksort(); 按照下标排序
krsort(); 按照下标降序
array_merge(); 合并 
array_chunk(); 拆分  
array_chunk($arr,每个数组的元素个数,true);  
> 保留原下标  
  
<u>合并注意，下标相同如何处理？</u>
- 下标为数值型，会重新索引，从0开始递增
- 下标为字符串，不会重新索引，后面覆盖前面的  

array_rand 随机从数组中取得元素，返回该元素的下标
> array_rand($arr,2);

PHP和Web页面交互

# <p align="center">PHP和Web页面交互</p>
## 1. Web表单的组成
1. from表单属性：
* `method` -- 提交方式 `get post`
* `action` --请求地址
* `enctype="multipart/from-data"` （文件上传控件）编码格式
2. isset判断变量是否赋值，并且不为空 unll
如果存在 true 不存在false
3.  empty判断变量内容是否为空，不是 null，是没数据。 没数据 true 有数据 false

0 "" "0" false null array()


### 2. input表单控件
* 1. type 属性 
text 单行文本框  
password 密码框   
radio 单选按钮  
checkbox 复选框   
file 文件域  
submit 提交按钮  
reset 重置按钮  
button 普通按钮  
image 图像形式提交按钮  
email 邮件   
url 网址  
tel 电话  
number 数值   
date 日期  

* 2. 其他属性
autofocus自动获取焦点
list下拉数据列表 
required必填 
placeholder提示信息
pattern正则表达式,验证格式
`^\d{11}$` 手机
`^[0-9]{6}$` 邮编
* 3. 其他表单元素 
1.textarea 多行文本框（注意通过resize:none;控制不能修改大小）
2.select 下拉列表

## 2. web表单数据的获取
根据不同的提交方式，使用PHP的超全局变量`$_POST`或`$_GET`
- 每个表单控件有 name 属性值，复选框的 name 值使用数组 hobby[]
- 如果不能确定 get 或 post 提交的数据，可以`$_REQUEST`超全局变量获取数据
## 3. 表单数据安全性校验
如果用户输入数据要直接输出到页面上用`htmlspecialchars()`将 html 代码转换为 html 实体  
## 4. `$_GET`   4种方式
- form提交方式get
`<a href="02.php?data1=1001&data2=hbjd">超链接</a>`
- javascript页面跳转  
`location.assign("...");`
- php页面跳转  
`header("location:...");`  
## 5. `$_REQUEST`
 是`$_POST`和`$_GET`数据的合集  
## 6. `$_SERVER`   
在一次浏览网页的过程中浏览器或服务器端
的一些信息。  
## 7. `$GLOBALS`  
用于在函数内部使用全局变量。  
`$GLOBALS['v1']`

PHP的会话技术

# <p align="center">PHP的会话技术</p>  
> 会话技术：就需要在浏览器和服务器的多次请求响应周期内，将数据保存下来的一门技术。  

典型：`cookie` `session`
1. cookie 将数据保存在浏览器端。  
`setcookie(名字,值); //设置cookie`  
`$_COOKIE` 数组获取cookie  
2. cookie有效期
`setcookie(名字,值,有效期);`  
`setcookie('name','张三',time()+60);`  
3. cookie有效范围  
`setcookie('name','张三',time()+60,'/');`  
> 默认为当前目录  
> /表示整站有效

-----------

超全局变量

# <p align="center">超全局变量</p>
函数的内部和外部---超全局变量
`$_POST` `$_GET` `$_REQUEST` `$_SERVER` `$_SESSION` `$_COOKIE` `$_FILES` `$GLOBALS`
- 均为数组
- 定义和维护都是系统完成的（我们只能使用，不能赋值和销毁）
- 具有超全局作用域
- 不同情形下值可能不同
1. `$_GET`变量：用户通过get方式提交的所有数据（共有4中形式）
- 1. 表单get方式提交
- 2. 
`<a href="目标文件.php?data01=1001&data02=hbjd">`
- 3. js中页面跳转
```
<script type="text/javascript">
location.assign("02.php?data1=1001&data2=hbjd")
</script>
```
- 4. php的跳转
```
<?php
header("location:02.php?data1=1001&data2=hbjd”)
?>
```
2. `$_REUQEST`：是`$_POST`和`$-GET`数据的合集  
3. `$_SERVER` 在一次浏览网页的过程中浏览器或服务器端的一些信息
4. `$GLOBALS`：用于在函数内部使用全局变量  
`$GLOBALS['v1']`

PHP连接数据库

# <p align="center">PHP连接数据库</p>
1. 连接数据库
`$link = mysqli_connect('localhost','root','root');`
2. 判断是否连接成功
```
if(!$link){
　　exit('数据库连接失败');
}
```
3. 设置字符集
`mysqli_set_charset($link,'utf-8);`
4. 选择数据库
`mysqli_select_db($link,'books');`
5. 准备sql语句
`$sql = "select * from bookInfo";`
6. 执行sql语句
`$obj = mysqli_query($link, $sql);`
7. 处理结果集(关联数组,一次一行)
```
$res = mysqli_fetch_assoc($obj); 
var_dump($res);
```
8. 关闭数据库
`mysqli_close($link);`

数据库语言

# <p align="center">数据库语言</p>

## 1. DDL语句（数据定义语句）
- `create table`
- `alter table`
- `drop table`
## 2. DML语句（数据操作语句）
* `insert info 表名（字段） values（值）`
* `update 表名`
* `set 字段名 = 值`
* `where 条件表达式`
* `delete from 表名`
* `where 条件表达式
* `select 字段名 from 表名`


## 其他常用函数（处理结果集）
- `$res = mysqli_fetch_row($obj);`
> 返回索引数组  
- `$res = mysqli_fetch_array($obj);`
> 返回索引数组和关联数组  
- `$res = mysqli_num_rows($obj);`
> 返回查询结果集的总行数
- `$res = mysqli_affected_rows($obj);`
> 添加、修改、操作受影响的行数
- `$res = mysqli_insert_id($link)`
> 最后插入的数据id  
 
删除  

```
$sql = "delete from bookInfo where bookId=$id;";   $bool = mysqli_query($link, $sql);  
if ($bool&&mysqli_affected_rows ($link)) {   
echo '删除成功';  
else{  
echo’删除失败’;  
}
```

修改  

```
$sql="update bookInfo
　　set typeId=$typeId,bookName='$bookName' 
　　where bookId=$id;";
$bool=mysqli_query($link,$sql); //判断是否修改成功
if($bool&&mysqli_affected_rows($link)) {
echo '修改成功<a href="booklist.php">返回</a>';
}
else {
echo '修改失败’;
}
```

添加  

```
$sql = "insert into bookInfo(typeId, bookName)
values($typeId,'$bookName')";
//echo $sql;
$bool = mysqli_query($link,$sql);
$id = mysqli_insert_id($link);
if($id){
echo '添加成功<a href="booklist. php">返回</a>';
}
else {
echo ’添加失败’;
}
```

* 分页  
1. 求出总条数
`select count(*) from bookInfo;`
2. 每页显示数
`$num = 4;`
3. 求出总页数
`$pageCount = ceil($count/$num);`
4. 求出偏移量
`$offset = ($page-1)*$num;`
