### JS的学习笔记

##### 对于在引入js文件
`<script src=""></script>`
##### js中一般使用单引号

#### 1.预问题
##### 1.基础输出
```javascript
alert('');
prompt('');
console.log();
```

##### 2.变量代码`var`(varible)
`var a = '1a'`

##### 3.数字类型
```
八进制 0
十六进制 0x
Number.MAX_VALUE(MIN)
Infinity and -Infinity
NaN  not a number
isNAN() 返回 false or true
```

##### 4.字符串问题
```
var str = 'my name is ';
console.log(str.length);
console.log('ab'+'cd');//拼接
console.log('12' + 12);//1212当存在字符串的时候则会变为字符串
//数字相加，字符相连
```

##### 5.数据类型
```
var str = ;
typeof str;//获取其类型
//蓝色：数字型
//黑色：字符串型
//墨绿色：布尔型
//转换字符串型
var str = num.toString();
var num = 1; String(num);
console.log(num + "");//隐式转换（重点）
//转换数字型
parseInt(age);//取整数
parseFloat('3.14');//取小数
Number(str);
console.log('12' - 0);//12 隐式转换(* / -)
//转换布尔型
Boolean();//('' 0 NaN null undefined)为false 其余为true
```

##### 6.逻辑中断问题
```
123 && 456//从左到右，一旦左边为1，则往后判断，若已至结尾则返回表达式
123 || 456//从左到右，一旦左边为1，则直接返回表达式，后续不执行
```

##### 7.`.length`
##### 8.数组中可以直接追加元素，也可以直接替换元素//不要直接把数组名赋值
##### 9.`newArr[newArr.length] = arr[i];`
##### 10.函数
```
fuction 函数名 (){

}
函数名();
```
##### 11.return返回
```
return xxx;//返回多个值可以返回数组
```
##### 12.arguments伪数组//每个函数都含有arguments内置对象
1.具有数组的length属性
2.按照索引的方式进行存储
3.没有真正数组的方法pop() push()

##### 13.运行
(1) 预解析 js引擎会把js里面所有var 和 function 提升到当前作用域的最前面
(2) 代码执行 
//变量提升 把所有变量提升到当前作用域的最前面 不进行赋值操作/不进行函数调用
注：当 `var a = b = c = 9` 时 为 `var a = 9; b = 9; c = 9;` //此时b和c为全局变量(未定义var)

#### 2.对象
##### 14.对象
js中，对象时一组无序的相关属性(特征，名词)和方法(行为，动词)的集合
1.
``` js
var obj = {
	uersName:'',
	age:18，
	sayHi:function(){
		console.lob('hi');
	}
}
//属性调用
console.log(obj.userName);
console.log(obj['age']);
//方法调用 对象.方法名()
obj.sayHi();
```
2.

```js
	var obj = new Object();//创建一个空的对象
	obj.uname = '';
	obj.sayHi = function(){
		console.log('hi');
	}
```
```js
//构造函数
function Obj(uname, age, sex){
	this.uname = uname;
	this.age = age;
	this.sex = sex;
}
new Obj('aa', 18, 'm');
//1.构造对象名字首字母要大写
//2.不需要return 就可以返回结果
```

##### 15.for...in 遍历对象
```js
for(var k in obj){
//k为属性
	console.log(k);
	console.log(obj.k);
}
```

##### 16.内置对象Math
```js
Math.max()
Math.min()
Math.random()
```

##### 17.日期对象date
```js
//date要使用时必须使用new 构造函数 创建日期对象
var date = new Date();
//当小于10时用此方法补齐0
h = h < 10 ? '0' + h : h;
```

##### 18.对于获取现在时间的函数
```js
//从1970.1.1开始计算 由于永远不会重复，所以会用于加密
var date = new Date();
date.valueOf();
date.getTime();
//
var date1 = +new Date();//最常用的方法
//
Date.now();//H5 新增的
//
//部分应用 关于倒计时
function countDown(time){
var nowTime = +new Date();//返回的是当前时间的总毫秒数
var inputTime = +new Date(time);//返回的是用户输入时间的总毫秒数
var time1 = (inputTime - nowTime) / 1000;//time1是剩余时间的总秒数
var d = parseInt(time1 / 60 / 60 / 24);//date
var h = parseInt(time1 / 60 / 60 % 24);//hour
var m = parseInt(time1 / 60 % 60);//minute
var s = parseInt(time1 % 60);//second
return d + '天' + h + '时' + m + '分' + s + '秒';
}
```

#### 3.数组
##### 19.检测是否为数组
```js
var arr = [];
var obj = {};
//(1) instanceof
arr instanceof Array//前面的arr的检测
obj instanceof Array//前面的arr的检测
//(2) Array.isArray(); //H5新增
Array.ifArray(arr);
Array.ifArray(obj);
```

##### 20.添加删除数组元素的方法
```js
//1. push(); 在末尾 添加一个或多个元素
arr.push();//返回的结果时新数组的长度
//2. unshift(); 在数组的开头 添加一个或多个元素 与上同理
arr.unshift();
//3. pop(); 删除数组最后一个元素 返回的是所删除的元素 一次只能删除一个元素
arr.pop();
//4. shift(); 删除开头的元素 与上同理
arr.shift();
```

##### 21.翻转数组元素的函数`arr.reverse();`

##### 22.排序数组元素的函数
```js
arr.sort(function(a, b)){
	return a - b;//升序
}
```

##### 23.返回数组元素的索引号 `indexOf();` `lastIndexOf()`
数组去重
```js
        function ji(arr) {
            var newArr = ['a'];
            for (var i = 0; i < arr.length; i++)
                if (newArr.indexOf(arr[i]) === -1) {
                    newArr.push(arr[i]);

                }
            return newArr;
        }
        var demo = ji(['a', 'c', 'a'])
        console.log(demo);
```

##### 24.数组转换为字符串
```js
//返回字符串
//1.用toString()
	var arr = [1, 2, 3];
	console.log(arr.toString());//1,2,3
//2.用join(分隔符)
	var arr = [1, 2, 3];
	console.log(arr1.join('&'));//1&2&3
```

##### 25.
```js
concat()//链接两个或多个数组 不影响原数组。返回一个新的数组
slice()//数组截取slice(begin,end)。 返回被截取项目的新数组
splice()//数组杉树splice(第几个开始，要删除个数)。 返回被删除项目的新数组
```

##### 26.js会有基本包装类型，即基本数据类型自动包装为复杂数据类型，然后具有属性和方法
```js
var str = 'andy';
console.log(str.length);//4
//运用了属性

//实质执行过程
//1.生成临时变量，把简单类型包装为复杂数据类型
var temp = new String('andy');
//2.赋值给我们声明的字符变量
str = temp;
//3.销毁临时变量
temp = null;
```

#### 4.字符串对象
##### 27.字符串具有不可变性，即里面的值不可变，看上去可以改变内容，实质为地址的改变，会开辟新的空间。因此不要大量拼接字符。

##### 28.字符返回位置`str.indexOf('要查找的字符',[起始的位置])`

##### 29.根据位置返回字符
```js
charAt(index)//返回指定位置的字符(index字符串的索引号) str.charAt(0)
//str[index] 等效
charCodeAt(index)//获取指定位置处字符的ASCII码(index索引号) str.charCodeAt(0)
```

##### 30.统计出现最多的字符和次数
对象['属性']
```js
var str = 'abdojodaa';
var o = {};
for (var i = 0; i < str.length; i++){
	var chars = str.charAt(i);//chars 是字符串中的每一个字符
	if (o[chars]) {//o[chars] 得到的是属性值
		o[chars]++;
	} else {
		o[chars] = 1;
	}
}
console.log(o);
//2.遍历对象
var max = 0;
var ch = '';
for (var k in o) {
	// k 得到的是属性名
	// o[k] 得到的是属性值
	if (o[k] > max) {
		max = o[k];
		ch = k;
	}
}
console.log(max);
console.log('最多的字符是' + ch);
```

##### 31.字符串操作方法
```
1.concat('字符串1','字符串2'....);
2.substr('截取的起始位置','截取几个字符'); //类似于splice 取截取的片段
3.替换字符 replace('被替换字符', '替换为的字符') //只替换第一个字符
4.若要求把所有的 o 替换为 *
var str1 = 'adjjioookjo';
while(str1.indexOf('o') !== -1){
	str1 = str1.replace('o','*');
}
5.字符转换为数组 split('分隔符') //与 join 相反 其为把数组转换为字符串
6.toUpperCase() //转换大写
7.toLowerCase() //转换小写
```

##### 32.简单类型与复杂类型
```
//1.简单类型又称基本数据类型或者值类型，复杂类型又叫做引用类型
值类型：在存储时变量中存储的是值本身
如 string, number, boolean, undifined, null(是一个空对象)
引用类型： 在存储时变量存储的仅仅是地址(引用)
如 通过new关键字创建的对象(系统对象、自定义对象)， 如Object、Array、Date等
//2.堆与栈
1.栈(操作系统)：由操作系统自动分配释放存放函数的参数值、局部变量的值等。其操作方式类似于数据结构中的栈;简单数据类型存放到栈里面
2.堆(操作系统)：存放发杂类型(对象)，一般由程序员分配释放，若程序员不是放，由垃圾回收机制回收;复杂数据类型存放到堆里面
1.简单数据类型 是存放在栈里面 里面直接开辟一个空间 存放的是值
2.复杂数据类型 首先在栈里面存放地址 十六进制表示 然后这个地址指向堆里面的数据
//3.传参
1.简单数据类型传参：函数的形参也可以看作是一个变量，当我们把一个值类型变量作为参数传给函数的形参的时，其实是把变量在栈空间里的值复制了一份给形参，那么方法内部对形参做任何修改，都不会影响到外部变量。
2.复杂数据类型：当我们把引用变量传给形参时，其实是把变量在栈空间里保存的堆地址复制给了形参，形参和实参其实保存的是同一个堆地址，所以操作的是同一个对象。
```

### Web API 和API
##### 1.API 应用程序编程接口(Application Programming Interface) 是一些预先定义的函数，目的是提供应用程序与开发人员基于某软件或者硬件得以访问一组例程的能力，而又无需访问源码，或理解内部工作机制的细节。
##### 2.DOM 文档对象模型(Document Object Modle) 处理可扩展标记语言(HTML、XML)的标准编程接口

##### 3.getElementById
```js
//返回的是元素对象
var timer = document.getElementById('time');
console.log(timer);
console.dir(timer);//打印元素对象，更好查看属性和方法
```

##### 4.获取元素
1.getElementsByTagName()`element.getElementsByTagName('标签名')`
2.返回的是获取过来元素对象的集合，以伪数组的形式存储
3.getElementsByClassName
4.querySelector('.box')  返回指定选择器的第一个元素对象
5.querySelectorAll()
6.document.body 返回body元素对象
7.document.documentElement 返回html元素对象


##### 5.事件
1.事件源 时间被触发的对象
2.事件类型 如何触发
3.事件处理程序 通过一个函数赋值的方式完成
```js
<button id="btn">1</button>
var btn = document.getElementById('btn');
btn.onclick = fuction(){
	alert('!');
}
```
1.获取事件源
2.绑定事件 注册事件
3.添加事件处理程序

##### 6.操作元素 
1.修改元素内容
```js
//innerText 不识别html标签 去除空格和换行
//1.获取元素
var btn = document.querySelector('button');
var div = document.querySelector('div');
//2.注册事件
btn.onclick = function (){
	div.innerText = getDate();
}

function getDate(){
	...
}
//innerHTML 识别html标签 保留空格和换行
//两个属性可读写 可以获取元素里面的内容
