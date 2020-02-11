## html

### **1.html5有什么新特性？**

```
 新增语义化标签<header></header>、<nav></nav>等
```

 新增用于绘画的<canvas>元素

 用于媒介回放的video和audio元素

 本地缓存有更好支持（localStorage和sessionStorage）

### 2.html是什么，html文档是什么？

html是用来描述网页的一种超文本标记语言，html文档也被叫做网页，它包含html标签和纯文本

### 3.<!DOCTYPE html>是什么？

它不是html标签，它为浏览器提供一种信息声明，告诉浏览器html是用什么版本编写的，用来表示html的版本

### 4.html文档的类型

有html、html+、html2.0、html3.2、html4.01、xhtml 1.0、html5等

#  2.css

### **1.简述flex布局**

flex布局：弹性布局，设置间距相同的布局、单行单列布局的时候相当好用
display可以设置为flex、inline-flex。

设置display：flex的时候，子元素的float、clear、vertical-align属性都将全部失效。

**容器属性：**

flex-direction设置主轴的排列方向，有 row（竖直向下排列）、row-reverse（竖直向上排列）、column（垂直向右排列）、column-reverse（垂直向左排列）

flex-wrap 设置是否排列在一条线上，有nowrap、wrap和warp-reverse三个选项

flex-flow是flex-direction和flex-wrap的简写

justify-content定义项目在主轴上的对齐方式有 flex-start | flex-end | center | space-between | space-around

align-items定义交叉轴的对齐方式 flex-start | flex-end | center | baseline | stretch

align-content定义多跟轴线的对齐方式

**项目属性：**

align-self（改项目的对齐方式）

order （项目排列顺序）

flex-grow（项目放大比例）

flex-shrink（项目缩小比例）

flex-basis（在分配多余空间时，项目占据的主轴空间）

flex（flex-grow，flex-shrink，flex-basis的缩写）

### **2. 简述grid布局**

 网格布局

### **3. 几种实现水平垂直居中的方法**

- 使用display：flex，justify-content：center，align-item： center实现

- 确定高宽情况下
  .test {

  ```
  position: absolute;
  margin:auto;
  left:0;
  top:0;
  right:0;
  bottom:0;
  }，或者
  .test {
  position: absolute;
  margin:auto;
  left:50%;
  top:50%;
  margin-top： -height/50；
  margin-left： -width/50；
  }，
  ```

- 不确定高宽
  .test {

  ```
  position: absolute;
  margin:auto;
  left:50%;
  top:50%;
  transform： translate（-50%，-50%）
  }，
  ```

### **4. 常见块级元素和内联元素**

块级元素： div、form、table、p、h1-h6、dl、li、ul、ol等
内联元素： a、strong、br、img、i、span、label、input、textarea、select等

### **5. position定位有哪些**

 absolute（绝对定位，相对于值不为static的第一个父元素进行定位）

```
relative（相对定位，相对于其正常位置进行定位）
fixed（相对于浏览器窗口进行定位）
static（默认值，没有定位，元素出现在正常的流中）
inherit（继承父元素position属性的值）
sticky（relative和fixed的结合体，当元素在屏幕内饰relative，滚出屏幕时显示为fixed）
```

### **6. css3的新属性**

```
 1. transfrom（对元素进行旋转、缩放、移动或倾斜）、animation（动画效果）和transition（添加过渡效             果）
2. 三个边框效果： border-radius（创建圆角边框）、border-shadow（阴影）、border-image（使用图片绘制边框）
3. 文字效果新增word-wrap、text-overflow和text-shadow，以上等等
```

### **7.block、inline和inline-block的区别**

- display：block
  1. block元素又叫做块级元素，它独占一行，多个block元素各占一行。默认情况下block元素 宽度自动填满父元素宽度
  2. 可以设置weight和width属性，块级元素设置了width还是独占一行
  3. 可以设置padding和margin属性
- display：inline
  1.inline元素又叫内联元素，不会占一行，多个内联元素会排列在一行，一行排列不下去才会 行，，宽度随元素的内容变化
  2.设置width和weight属性无效
  3.inline元素的margin和padding属性，水平方向上都能产生边距效果，竖直方向上不会产生 效果
- display： inline-block
  1. 内联块级元素拥有inline元素的多个占据同行特性和block元素的设置高度宽度特性和设置 padding和margin特性

### **8. display：none和visiblity：hidden的区别**

 为none的时候不占空间，为hidden的时候隐藏元素依然占据空间

 为none的会产生回流和重绘，visiblity：hidden的时候只产生重绘

 visiblity：hidden的子孙元素设置visiblity：hidden时会失效

### **9. 什么是BFC， BFC用来解决什么问题**

格式化上下文：特点是内部的子元素不会影响外部的元素，可以用来解决margin穿透和清除浮动

一个块格式化上下文由以下之一创建：

```
1)根元素或其它包含它的元素
2)浮动元素 (元素的 float 不是 none)
3)绝对定位元素 (元素具有 position 为 absolute 或 fixed)
4)内联块 (元素具有 display: inline-block)
5)表格单元格 (元素具有 display: table-cell，HTML表格单元格默认属性)
6)表格标题 (元素具有 display: table-caption, HTML表格标题默认属性)
7)具有overflow 且值不是 visible 的块元素，
8)display: flow-root
9)column-span: all 应当总是会创建一个新的格式化上下文，即便具有 column-span: all 的元素并不被包裹在一个多列容器中。
```

### **10.盒子模型有哪些，如何设置**

iE盒子模型： 内容（content+padding+border）+边界margin 高宽包含padding和border

标准盒子模型： content+padding+border+边界margin 高宽指的是content

通过box-sizing：content-box设置标准盒子模型，box-sizing：border-box设置ie盒子模型

### 11.css选择器有哪些

选择器有id选择器、元素选择器、属性选择器、类选择器、后代选择器、子元素选择器、相邻兄弟选择器、伪类和伪元素。

### 12.清除浮动的四种方式

- 在浮动的元素样式中加入clear：both

- 在浮动元素下面插入清除浮动的块级元素

- 给浮动元素设置伪类，伪类样式设置display为block，clear：both

- 设置BFC（格式化上下文），如浮动父元素设置overflow：auto

  ### 13.如何用css实现一个三角形

   定义一个div元素，让它的内容高宽为0，通过border来实现

  ```
  div {
      width: 0;
      height: 0;
      border: 40px solid;
      border-color: transparent transparent red;
  }
  ```

  以上css样式通过设置底部border边为红色，其他边为透明色，实现了一个底部宽40，高20的红色的三角形

  ------

  ## js

  ### **1. addEventListener的第三个参数的作用**

  指定事件是否在捕获或者冒泡阶段执行，true为在捕获阶段执行，false默认，在冒泡阶段执行

  ### **2.什么是事件冒泡，什么是事件捕获**

  事件冒泡指事件从发生的目标开始，沿着文档逐层向上冒泡，到documnent为止，事件捕获则相反，从documnet开始，沿着文档向下，直到目标事件为止，

  ### **3.如何阻止事件冒泡和事件捕获**

  ie下设置e.cancelBubble = true，在符合w3c的浏览器设置e.stopProgation()阻止事件冒泡，也可以通过preventDefault阻止默认行为，因为事件处理的默认行为就是冒泡或者通过return false

  使用stopImmediatePropagation() 阻止事件捕获，需要注意的是stopImmediatePropagation() 也能阻止事件冒泡，调用后，不仅父类元素冒泡被阻止，同时该元素绑定的同类事件也会执行

  ### **4.typeof返回的数据类型**

  string、number、boolean、undefined、object、function

  ### **5.列举三种强制类型转换和2种隐式类型转换**

  强制（parseInt、parseFloat、number）

  隐式（== ===）

  ### 6.**split（） join（）区别**

  前者将字符串切割成数组形式，后者将数组转为字符串

  ### 7. ajax请求get和post方法的区别

  1. get主要是获取资源，post请求服务器端资源
  2. get传输数据通过url，post通过http的post机制，将要传输的数据放在请求实体中发送给服务器
  3. get传输数据量小，post传输数据量大
  4. get不安全，post安全性较高
  5. get只能支持ASCII字符传输，传递中文字符会乱码；post支持标准字符集，可以传递中文字符

  ### 8.call、apply和bind的区别

  call和apply都可以改变this的指向，区别在于传入apply的第二个参数是一个数组，call后面是对象

  bind后面的参数也是对象，但是bind不会立即执行

  ### 9.ajax请求时，如何解析json数据

  使用JSON.parse()把json数据转化为js对象，使用JSON.Stringify()把js对象转化为json字符串

  ### 10.闭包是什么，有什么特性

  闭包就是能够读取函数内部变量的函数，使得函数不被GC回收，如果过多使用，就会造成内存泄露

  

  ### 11.添加 删除 替换 插入到某个节点的方法

  1.创建新节点

  createElement（） // 创建一个具体元素

  createTextNode（） // 创建一个文本节点

  2.添加、移除、替换、插入

  appendChild（） // 添加

  removeChild（） // 移除

  replaceChild（） // 替换

  insertBefore（） // 插入

  ### 12.document onload和doucment ready的区别

  onload是在结构和样式、外部js及图片加载好后执行js，ready是在dom树创建完成后就执行，是jquery里面的方法

  ### 13.函数声明和函数表达式的区别

  函数声明在js解析时就会进行函数提升，因此在同一作用域中，不管函数声明在哪定义，该函数都可以调用，函数表达式只有在执行到那一块后，才可以调用

  ### 14. null和undefined的区别

   null表示‘空’的对象，转化为数值是0，undefined是一个表示无的原始值，转化为数值是NAN，

   变量为声明，默认是undefined，null表示尚不存在的对象

   undefined表示为未初始化的变量返回的值，null表示一个尚不存在的对象返回的值，undefined可以看做空的变量，null看做空的对象

  ### 15. new操作符干了什么

  1. 创建了一个空对象。

  2. 把所创建的空对象的_ proto _指向构造函数的prototype

  3. 执行构造函数中的代码，构造函数中的this指向对象

  4. 返回该对象（除非构造函数中返回一个对象或者函数）

     ### 16.实现深度克隆

     JSON.parse(JSON.stringify());

     ### 17.什么是同源策略

     它是浏览器的一种约定，脚本只允许访问同一站点的资源，协议相同，域名相同，端口号相同，就是同一站点

     在浏览器中，<script> 、<img> <link>等标签都可以跨域加载资源，cookie和ajax都不能跨域加载资源

     ### 18.ajax跨域

     后端服务器端设置

      res.header('Access-Control-Allow-Origin', '*'); // 设置允许所有源访问

     jsonp跨域

     JSONP是JSON with Padding的略称。它是一个非官方的**协议**，它允许在服务器端集成Script tags返回至客户端，通过javascript callback的形式实现跨域访问；实现方式是利用script中的src请求服务器端数据，服务端将需要的数据以入参的形式放入创建的函数中并返回

     ```html
     <meta content="text/html;chartset=utf-8" http-equiv="Content-type"/>
     <script type="text/javascript">
         function jsCallback(res) {
         console.log(res);
         }
     </script>   
     <script type="text/javascript" src="http://abc.com/index.php?callback=jsCallback"/>
     ```

### 19.js如何获取dom元素

- 通过ID获取（getElementById，只获取一个元素，没找到则为null）
- 通过name获取（getElementByName， 返回一个类数组，没有找到则为空数组）
- 通过标签名（getElementsByTagName，返回一个类数组，没有找到则为空数组）
- 通过类名（getElementByClassName，返回一个类数组，没找到则为空数组）
- 通过选择器获取一个元素（querySelector，返回值只取到第一个元素）
- 通过选择器获取所有元素（querySelectorAll，返回一个类数组）

### 20.原生ajax请求步骤有哪些

```js
// 创建XMLHttpRequest对象
var ajax = new XMLHttpRequest()；
// 规定请求的类型，url及是否异步处理请求
ajax.open('GET', url,true);
// 设置发送信息至服务器时内容编码格式
ajax.setRequestHeader('Content-type', 'application/x-www-from-urlencoded');
//接受服务器响应数据
ajax.onreadystatechange = function() {
    if(ajax.readyState === 4 && ajax.status === 200 || ajax.status === 304 ) {
        
    }
}
//发送请求
ajax.send(null);
```

### 21.列举数组的对象方法

| 方法         | 描述                                                     |
| ------------ | -------------------------------------------------------- |
| push（）     | 添加元素到数组末尾                                       |
| splice( )    | 删除元素，并向数组添加新元素                             |
| unshift（）  | 向数组头部添加一个元素                                   |
| pop（）      | 删除数组末尾元素                                         |
| shift（）    | 删除数组头部元素                                         |
| slice（）    | 从数组中返回特定的元素                                   |
| sort（）     | 对数组进行排序                                           |
| join（）     | 把数组所有元素放入一个字符串，元素通过指定分割符进行分隔 |
| concat（）   | 合并两个或多个数组，并合并                               |
| reverse（）  | 颠倒数组中元素的顺序                                     |
| toString（） | 把数组转化为字符串，返回结果                             |
| valueOf（）  | 返回数组对象的原始值                                     |

### 22.js实现数组去重

1.es6实现

```js
function deRep( arr ) {
    return [...new Set(arr)];
}
```

2.遍历数组

```js
function deRep (arr) {
    var a = [];
    for(let i = 0; i< arr.length;i++) {
        if(a.indexOf(arr[i]) === -1) {
            a.push(arr[i]);
        }
    }
    return a;
}
```

3.优化数组遍历，（双层循环）

```js
function deRep(arr) {
    var a = [];
    for (let i = 0; i < arr.length; i++) {
        for(let j = i+1; j < arr.length; j++ ) {
            if(arr[i] === arr[j]) {
                ++i;
            }
        }
       a.push(arr[i]);
    }
    return a;
}
```

4.排序后相邻去重

```js
function deRep(arr) {
    var a = [arr[0]];
    arr.sort();
    for(let i = 0; i < arr.length; i++ ) {
        if(arr[i] !== a[a.length - 1]) {
            a.push(arr[i]);
        }
    }
    return a;
}
```

5.利用map的key值不能重复

```js
 function deReq(arr) {
     let map = new Map();
     let a = [];
     for (let i =0 ; i< arr.length; i++) {
         if(map.has(arr[i])) {
             map.set(arr[i], true);
         } else {
             map.set(arr[i],false)
             a.push(arr[i]);
         }
     }
     return a;
 }
```

6.利用reduce（）方法

```js
function deReq(arr) {
    return arr.reduce((prev,cur) => {
        prev.includes(cur) || prev.push(cur));
        return prev;
    },[]);
}
```

### 23.数组求和

1.使用递归

```js
function sum(arr) {
    let len = arr.length;
    if(len === 0) {
        return 0;
    } else if(len === 1) {
        return arr[0];
    } else {
        return arr[0] + sum(arr.slice(1))
    }
}
```

2.forEach迭代

```js
function sum(arr) {
    let sumArr = arr;
    let sum = 0;
    sumArr.forEach((val,index,arr) => {
        sum += val;
    },0);
     return sum;
}
```

3.for循环累加

```js
function sum(arr) {
    let arr1 = arr;
    let sum = 0;
    for(let i = 0; i< arr1.length; i++) {
        sum += arr[i];
    }
    return sum;
}
```

1. 利用reduce（）方法

```js
function sum(arr) {
    let arr1 = arr;
    let sum = arr1.reduce((prev,cur,index,arr) => {
        return prev + cur;
    })
    return sum;
}
```

### 24.数组排序

1.冒泡排序

```js
function sortArr(arr) {
    if(arr.length < 1) {
        return arr;
    }
    for(let i = 0; i<arr.length; i++) {
        for(let j = 0; j <arr.length -1 - i; j++) {
            if(arr[j] < arr[j + 1] ) {
                let flag = arr [j];
                arr[j] = arr[j + 1];
                arr[j + 1] = flag;
            }
        }
    }
      return arr;
}
```

1. 自定义数组的sort方法

```
function sort(a,b) {
    return a - b;
    
}
```

3.快速排序

```js
function sortArr(arr) {
    if(arr.length < 1) {
        return arr;
    }
    let num = arr.splice([Math.floor(arr.length / 2)],1)[0];
    let left = [], right = [];
    for(var i = 0; i < arr.length; i++) {
        if(arr[i] < num) {
            left.push(arr[i]);
        } else {
            right.push(arr[i]);
        }
    }
    return sortArr(left).concat([num], sortArr(right));
}
```