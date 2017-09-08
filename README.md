# JavaScript
记录有关JavaScript的知识

# JavaScript介绍 #

- JavaScript是运行在浏览器端的脚步语言，JavaScript主要解决的是前端与用户交互的问题，包括使用交互与数据交互。 JavaScript是浏览器解释执行的，前端脚本语言还有JScript（微软，IE独有），ActionScript( Adobe公司，需要插件)等。

- 前端三大块 
1. HTML：页面结构
2. CSS：页面表现：元素大小、颜色、位置、隐藏或显示、部分动画效果
3. JavaScript：页面行为：部分动画效果、页面与用户的交互、页面功能

# JavaScript嵌入页面的方式 #

1. 行间事件（主要用于事件）
```js
<input type="button" name="" onclick="alert('ok！');">
```
2. 页面script标签嵌入
```js
<script type="text/javascript">        
    var a = '你好！';
    alert(a);
</script>
```
3. 外部引入
```html
<script type="text/javascript" src="js/index.js"></script>
```

## javascript语句与注释 ##

1. 一条javascript语句应该以“;”结尾
```js
<script type="text/javascript">    
var a = 123;
var b = 'str';
function fn(){
    alert(a);
};
fn();
</script>
```
2. javascript注释
```js
<script type="text/javascript">    

// 单行注释
var a = 123;
/*  
    多行注释
    1、...
    2、...
*/
var b = 'str';
</script>
```
# 变量 #

- JavaScript 是一种弱类型语言，javascript的变量类型由它的值来决定。 定义变量需要用关键字 'var'
```js
 var a = 123;
 var b = 'asd';

 //同时定义多个变量可以用","隔开，公用一个‘var’关键字

 var c = 45,d='qwe',f='68';
```
## 变量类型 ##

- 5种基本数据类型：

```js
number、string、boolean、undefined、null
```
- 1种复合类型：
object

## 变量、函数、属性、函数参数命名规范 ##

1. 区分大小写
2. 第一个字符必须是字母、下划线（_）或者美元符号（$）
3. 其他字符可以是字母、下划线、美元符或数字

## 变量、函数、属性、函数参数命名规范 ##

1. 区分大小写
2. 第一个字符必须是字母、下划线（_）或者美元符号（$）
3. 其他字符可以是字母、下划线、美元符或数字

# 获取元素方法一 #

- 可以使用内置对象document上的getElementById方法来获取页面上设置了id属性的元素，获取到的是一个html对象，然后将它赋值给一个变量，比如：
```html
<script type="text/javascript">
    var oDiv = document.getElementById('div1');
</script>
....
<div id="div1">这是一个div元素</div>
```
- 上面的语句，如果把javascript写在元素的上面，就会出错，因为页面上从上往下加载执行的，javascript去页面上获取元素div1的时候，元素div1还没有加载，解决方法有两种：

- 第一种方法：将javascript放到页面最下边
```html
....
<div id="div1">这是一个div元素</div>
....

<script type="text/javascript">
    var oDiv = document.getElementById('div1');
</script>
</body>
```
- 第二种方法：将javascript语句放到window.onload触发的函数里面,获取元素的语句会在页面加载完后才执行，就不会出错了。
```html
<script type="text/javascript">
    window.onload = function(){
        var oDiv = document.getElementById('div1');
    }
</script>

....

<div id="div1">这是一个div元素</div>
```

# 操作元素属性 #

- 获取的页面元素，就可以对页面元素的属性进行操作，属性的操作包括属性的读和写。

- 操作属性的方法 
1. “.” 操作
2. “[ ]”操作

- 属性写法

1、html的属性和js里面属性写法一样
2、“class” 属性写成 “className”
3、“style” 属性里面的属性，有横杠的改成驼峰式，比如：“font-size”，改成”style.fontSize”

- 通过“.”操作属性：
```html
<script type="text/javascript">

    window.onload = function(){
        var oInput = document.getElementById('input1');
        var oA = document.getElementById('link1');
        // 读取属性值
        var val = oInput.value;
        var typ = oInput.type;
        var nam = oInput.name;
        var links = oA.href;
        // 写(设置)属性
        oA.style.color = 'red';
        oA.style.fontSize = val;
    }

</script>

......

<input type="text" name="setsize" id="input1" value="20px">
<a href="http://www.itcast.cn" id="link1">传智播客</a>
```
- 通过“[ ]”操作属性：
```html
<script type="text/javascript">

    window.onload = function(){
        var oInput1 = document.getElementById('input1');
        var oInput2 = document.getElementById('input2');
        var oA = document.getElementById('link1');
        // 读取属性
        var val1 = oInput1.value;
        var val2 = oInput2.value;
        // 写(设置)属性
        // oA.style.val1 = val2; 没反应
        oA.style[val1] = val2;        
    }

</script>

......

<input type="text" name="setattr" id="input1" value="fontSize">
<input type="text" name="setnum" id="input2" value="30px">
<a href="http://www.itcast.cn" id="link1">传智播客</a>
```
- innerHTML 
- innerHTML可以读取或者写入标签包裹的内容
```html
<script type="text/javascript">
    window.onload = function(){
        var oDiv = document.getElementById('div1');
        //读取
        var txt = oDiv.innerHTML;
        alert(txt);
        //写入
        oDiv.innerHTML = '<a href="http://www.itcast.cn">传智播客<a/>';
    }
</script>

......

<div id="div1">这是一个div元素</div>
```
# 函数 #
- 函数就是重复执行的代码片。

- 函数定义与执行

```html
<script type="text/javascript">
    // 函数定义
    function aa(){
        alert('hello!');
    }
    // 函数执行
    aa();
</script>
```

- 变量与函数预解析 
  - JavaScript解析过程分为两个阶段，先是编译阶段，然后执行阶段，在编译阶段会将function定义的函数提前，并且将var定义的变量声明提前，将它赋值为undefined。
```html
<script type="text/javascript">    
    aa();       // 弹出 hello！
    alert(bb);  // 弹出 undefined
    function aa(){
        alert('hello!');
    }
    var bb = 123;
</script>
```
- 提取行间事件 
  - 在html行间调用的事件可以提取到javascript中调用，从而做到结构与行为分离。
```html
<!--行间事件调用函数   -->
<script type="text/javascript">        
    function myalert(){
        alert('ok!');
    }
</script>
......
<input type="button" name="" value="弹出" onclick="myalert()">

<!-- 提取行间事件 -->
<script type="text/javascript">

window.onload = function(){
    var oBtn = document.getElementById('btn1');
    oBtn.onclick = myalert;
    function myalert(){
        alert('ok!');
    }
}    
</script>
......
<input type="button" name="" value="弹出" id="btn1">
```
- 匿名函数

  - 定义的函数可以不给名称，这个叫做匿名函数，可以将匿名函数直接赋值给元素绑定的事件来完成匿名函数的调用。
```html
<script type="text/javascript">

window.onload = function(){
    var oBtn = document.getElementById('btn1');
    /*
    oBtn.onclick = myalert;
    function myalert(){
        alert('ok!');
    }
    */
    // 直接将匿名函数赋值给绑定的事件

    oBtn.onclick = function (){
        alert('ok!');
    }
}

</script>
```
- 函数传参
```html
<script type="text/javascript">
    function myalert(a){
        alert(a);
    }
    myalert(12345);
</script>
```
- 函数'return'关键字 
- 函数中'return'关键字的作用：
1. 返回函数执行的结果
2. 结束函数的运行
3. 阻止默认行为
```html
<script type="text/javascript">
function add(a,b){
    var c = a + b;
    return c;
    alert('here!');
}

var d = add(3,4);
alert(d);  //弹出7
</script>
```

# 条件语句 #

- 通过条件来控制程序的走向，就需要用到条件语句。

- 运算符 
1、算术运算符： +(加)、 -(减)、 *(乘)、 /(除)、 %(求余)
2、赋值运算符：=、 +=、 -=、 *=、 /=、 %=
3、条件运算符：==、===、>、>=、<、<=、!=、&&(而且)、||(或者)、!(否)

- if else
```html
var a = 6;
if(a==1)
{
    alert('语文');
}
else if(a==2)
{
    alert('数学');
}
else if(a==3)
{
    alert('英语');
}
else if(a==4)
{
    alert('美术');
}
else if(a==5)
{
    alert('舞蹈');
}
else
{
    alert('不补习');
}
```
- switch
```html
var a = 6;

switch (a){
    case 1:
        alert('语文');
        break;
    case 2:
        alert('数学');
        break;
    case 3:
        alert('英语');
        break;
    case 4:
        alert('美术');
        break;
    case 5:
        alert('舞蹈');
        break;
    default:
        alert('不补习');
}
```
## 数组及操作方法 ##

- 数组就是一组数据的集合，javascript中，数组里面的数据可以是不同类型的。

- 定义数组的方法
```html
//对象的实例创建
var aList = new Array(1,2,3);

//直接量创建
var aList2 = [1,2,3,'asd'];
```
- 操作数组中数据的方法 
1. 获取数组的长度：aList.length;
```html
var aList = [1,2,3,4];
alert(aList.length); // 弹出4
```
2. 用下标操作数组的某个数据：aList[0];
```html
var aList = [1,2,3,4];
alert(aList[0]); // 弹出1
```
3. join() 将数组成员通过一个分隔符合并成字符串
```html
var aList = [1,2,3,4];
alert(aList.join('-')); // 弹出 1-2-3-4
```
4. push() 和 pop() 从数组最后增加成员或删除成员
```html
var aList = [1,2,3,4];
aList.push(5);
alert(aList); //弹出1,2,3,4,5
aList.pop();
alert(aList); // 弹出1,2,3,4
```
5. unshift()和 shift() 从数组前面增加成员或删除成员
```html
var aList = [1,2,3,4];
aList.unshift(5);
alert(aList); //弹出5,1,2,3,4
aList.shift();
alert(aList); // 弹出1,2,3,4
```
6. reverse() 将数组反转
```html
var aList = [1,2,3,4];
aList.reverse();
alert(aList);  // 弹出4,3,2,1
```
7. indexOf() 返回数组中元素第一次出现的索引值
```html
var aList = [1,2,3,4,1,3,4];
alert(aList.indexOf(1));
```
8. splice() 在数组中增加或删除成员
```html
var aList = [1,2,3,4];
aList.splice(2,1,7,8,9); //从第2个元素开始，删除1个元素，然后在此位置增加'7,8,9'三个元素
alert(aList); //弹出 1,2,7,8,9,4
```
- 多维数组 
- 多维数组指的是数组的成员也是数组的数组。
```html
var aList = [[1,2,3],['a','b','c']];

alert(aList[0][1]); //弹出2;
```
- 获取元素的第二种方法 
- document.getElementsByTagName(''),获取的是一个选择集，不是数组，但是可以用下标的方式操作选择集里面的dom元素。

# 循环语句 #

- 程序中进行有规律的重复性操作，需要用到循环语句。

- for循环
```html
for(var i=0;i<len;i++)
{
    ......
}
```
- while循环(不常用)
```html
var i=0;

while(i<8){

    ......

    i++;

}
```
- 数组去重
```html
var aList = [1,2,3,4,4,3,2,1,2,3,4,5,6,5,5,3,3,4,2,1];

var aList2 = [];

for(var i=0;i<aList.length;i++)
{
    if(aList.indexOf(aList[i])==i)
    {
        aList2.push(aList[i]);
    }
}

alert(aList2);
```
# 字符串处理方法

1. 字符串合并操作：“ + ”
2. parseInt() 将数字字符串转化为整数
3. parseFloat() 将数字字符串转化为小数
4. split() 把一个字符串分隔成字符串组成的数组
5. charAt() 获取字符串中的某一个字符
6. indexOf() 查找字符串是否含有某字符
7. substring() 截取字符串 用法： substring(start,end)（不包括end）
8. toUpperCase() 字符串转大写
9. toLowerCase() 字符串转小写

##字符串反转
```html
var str = 'asdfj12jlsdkf098';
var str2 = str.split('').reverse().join('');

alert(str2);
```
# 调试程序的方法

1. alert

2. console.log

3. document.title

# 定时器

- 定时器在javascript中的作用
1. 制作动画
2. 异步操作
3. 函数缓冲与节流

## 定时器类型及语法
```html
/*
    定时器：
    setTimeout  只执行一次的定时器 
    clearTimeout 关闭只执行一次的定时器
    setInterval  反复执行的定时器
    clearInterval 关闭反复执行的定时器

*/

var time1 = setTimeout(myalert,2000);
var time2 = setInterval(myalert,2000);
/*
clearTimeout(time1);
clearInterval(time2);
*/
function myalert(){
    alert('ok!');
}
```
## 定时器制作时钟
```html
<script type="text/javascript">
    window.onload = function(){    
        var oDiv = document.getElementById('div1');
        function timego(){
            var now = new Date();
            var year = now.getFullYear();
            var month = now.getMonth()+1;
            var date = now.getDate();
            var week = now.getDay();
            var hour = now.getHours();
            var minute = now.getMinutes();
            var second = now.getSeconds();
            var str = '当前时间是：'+ year + '年'+month+'月'+date+'日 '+toweek(week)+' '+todou(hour)+':'+todou(minute)+':'+todou(second);
            oDiv.innerHTML = str;
        }
        timego();
        setInterval(timego,1000);
    }

    function toweek(n){
        if(n==0)
        {
            return '星期日';
        }
        else if(n==1)
        {
            return '星期一';
        }
        else if(n==2)
        {
            return '星期二';
        }
        else if(n==3)
        {
            return '星期三';
        }
        else if(n==4)
        {
            return '星期四';
        }
        else if(n==5)
        {
            return '星期五';
        }
        else
        {
            return '星期六';
        }
    }


    function todou(n){
        if(n<10)
        {
            return '0'+n;
        }
        else
        {
            return n;
        }
    }
</script>
......
<div id="div1"></div>
```
## 定时器制作倒计时（使用较多）
```html
<script type="text/javascript">
    window.onload = function(){
        var oDiv = document.getElementById('div1');
        function timeleft(){
            var now = new Date();
            var future = new Date(2016,8,12,24,0,0);
            var lefts = parseInt((future-now)/1000);
            var day = parseInt(lefts/86400);
            var hour = parseInt(lefts%86400/3600);
            var min = parseInt(lefts%86400%3600/60);
            var sec = lefts%60;
            str = '距离2016年9月12日晚24点还剩下'+day+'天'+hour+'时'+min+'分'+sec+'秒';
            oDiv.innerHTML = str; 
        }
        timeleft();
        setInterval(timeleft,1000);        
    }

</script>
......
<div id="div1"></div>
```
# 类型转换

1. 直接转换 parseInt() 与 parseFloat()
```html
alert('12'+7); //弹出127
alert( parseInt('12') + 7 );  //弹出19 
alert( parseInt(5.6));  // 弹出5
alert('5.6'+2.3);  // 弹出5.62.3
alert(parseFloat('5.6')+2.3);  // 弹出7.8999999999999995
alert(0.1+0.2); //弹出 0.3000000000000004
alert((0.1*100+0.2*100)/100); //弹出0.3
alert((parseFloat('5.6')*100+2.3*100)/100); //弹出7.9
```
2. 隐式转换 “==” 和 “-”
```html
if('3'==3)
{
    alert('相等');
}

// 弹出'相等'
alert('10'-3);  // 弹出7
```
3. NaN 和 isNaN
```html
alert( parseInt('123abc') );  // 弹出123
alert( parseInt('abc123') );  // 弹出NaN
```
# 变量作用域

- 变量作用域指的是变量的作用范围，javascript中的变量分为全局变量和局部变量。

1. 全局变量：在函数之外定义的变量，为整个页面公用，函数内部外部都可以访问。
2. 局部变量：在函数内部定义的变量，只能在定义该变量的函数内部访问，外部无法访问。
```html
<script type="text/javascript">
    //全局变量
    var a = 12;
    function myalert()
    {
        //局部变量
        var b = 23;
        alert(a);
        alert(b);
    }
    myalert(); //弹出12和23
    alert(a);  //弹出12    
    alert(b);  //出错
</script>
```
# 封闭函数

- 封闭函数是javascript中匿名函数的另外一种写法，创建一个一开始就执行而不用命名的函数。

- 一般定义的函数和执行函数：
```html
function changecolor(){
    var oDiv = document.getElementById('div1');
    oDiv.style.color = 'red';
}
changecolor();
```
- 封闭函数：
```html
(function(){
    var oDiv = document.getElementById('div1');
    oDiv.style.color = 'red';
})();
```
- 还可以在函数定义前加上“~”和“!”等符号来定义匿名函数
```html
!function(){
    var oDiv = document.getElementById('div1');
    oDiv.style.color = 'red';
}();
```

# 闭包

## 什么是闭包 
- 函数嵌套函数，内部函数可以引用外部函数的参数和变量，参数和变量不会被垃圾回收机制收回
```html
function aaa(a){      
      var b = 5;      
      function bbb(){
           a++;
           b++;
         alert(a);
         alert(b);
      }
      return bbb;
  }

 var ccc = aaa(2);

 ccc();
 ccc();
 ```
- 改写成封闭函数的形式：
```html
var ccc = (function(a){

  var b = 5;
  function bbb(){
       a++;
       b++;
     alert(a);
     alert(b);
  }
  return bbb;

})(2);

ccc();
ccc();
```
- 用处 
1. 将一个变量长期驻扎在内存当中，可用于循环中存索引值
```html
<script type="text/javascript">
    window.onload = function(){
        var aLi = document.getElementsByTagName('li');
        for(var i=0;i<aLi.length;i++)
        {
            (function(i){
                aLi[i].onclick = function(){
                    alert(i);
                }
            })(i);
        }
    }
</script>
......
<ul>
    <li>111</li>
    <li>222</li>
    <li>333</li>
    <li>444</li>
    <li>555</li>
</ul>
```
2. 私有变量计数器，外部无法访问，避免全局变量的污染

<script type="text/javascript">

var count = (function(){
    var a = 0;
    function add(){
        a++;
        return a;
    }

    return add;

})()

count();
count();

var nowcount = count();

alert(nowcount);

</script>

# 内置对象

1. document
```html
document.referrer  //获取上一个跳转页面的地址(需要服务器环境)
```
2. location
```html
window.location.href  //获取或者重定url地址
window.location.search //获取地址参数部分
window.location.hash //获取页面锚点或者叫哈希值
```
3. Math
```html
Math.random 获取0-1的随机数
Math.floor 向下取整
Math.ceil 向上取整
```
# 面向对象（实际开发中使用较少）

## 面向过程与面向对象编程

1. 面向过程：所有的工作都是现写现用。

2. 面向对象：是一种编程思想，许多功能事先已经编写好了，在使用时，只需要关注功能的运用，而不需要这个功能的具体实现过程。

## javascript对象 
- 将相关的变量和函数组合成一个整体，这个整体叫做对象，对象中的变量叫做属性，变量中的函数叫做方法。javascript中的对象类似字典。

- 创建对象的方法 
1. 单体
```html
<script type="text/javascript">
var Tom = {
    name : 'tom',
    age : 18,
    showname : function(){
        alert('我的名字叫'+this.name);    
    },
    showage : function(){
        alert('我今年'+this.age+'岁');    
    }
}
</script>
```
2. 工厂模式
```html
<script type="text/javascript">

function Person(name,age,job){
    var o = new Object();
    o.name = name;
    o.age = age;
    o.job = job;
    o.showname = function(){
        alert('我的名字叫'+this.name);    
    };
    o.showage = function(){
        alert('我今年'+this.age+'岁');    
    };
    o.showjob = function(){
        alert('我的工作是'+this.job);    
    };
    return o;
}
var tom = Person('tom',18,'程序员');
tom.showname();

</script>
```
2. 构造函数
```html
<script type="text/javascript">
    function Person(name,age,job){            
        this.name = name;
        this.age = age;
        this.job = job;
        this.showname = function(){
            alert('我的名字叫'+this.name);    
        };
        this.showage = function(){
            alert('我今年'+this.age+'岁');    
        };
        this.showjob = function(){
            alert('我的工作是'+this.job);    
        };
    }
    var tom = new Person('tom',18,'程序员');
    var jack = new Person('jack',19,'销售');
    alert(tom.showjob==jack.showjob);
</script>
```
3. 原型模式
```html
<script type="text/javascript">
    function Person(name,age,job){        
        this.name = name;
        this.age = age;
        this.job = job;
    }
    Person.prototype.showname = function(){
        alert('我的名字叫'+this.name);    
    };
    Person.prototype.showage = function(){
        alert('我今年'+this.age+'岁');    
    };
    Person.prototype.showjob = function(){
        alert('我的工作是'+this.job);    
    };
    var tom = new Person('tom',18,'程序员');
    var jack = new Person('jack',19,'销售');
    alert(tom.showjob==jack.showjob);
</script>
```
4. 继承
```html
<script type="text/javascript">

        function fclass(name,age){
            this.name = name;
            this.age = age;
        }
        fclass.prototype.showname = function(){
            alert(this.name);
        }
        fclass.prototype.showage = function(){
            alert(this.age);
        }
        function sclass(name,age,job)
        {
            fclass.call(this,name,age);
            this.job = job;
        }
        sclass.prototype = new fclass();
        sclass.prototype.showjob = function(){
            alert(this.job);
        }
        var tom = new sclass('tom',19,'全栈工程师');
        tom.showname();
        tom.showage();
        tom.showjob();
    </script>
    ```