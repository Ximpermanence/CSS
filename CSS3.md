## 1、什么是CSS

如何学习

1. CSS是什么
2. CSS怎么用（快速入门）
3. **CSS选择器（重点+难点）**
4. 美化网页（文字，阴影，超链接，列表，渐变...）
5. 盒子模型
6. 浮动
7. 定位
8. 网页动画（特效）


### 1.1、 什么是CSS

Cascading Style Sheet 层叠级联样式表

CSS：表现（美化网页）

字体，颜色，边距，高度，宽度，背景图片，网页定位，网页浮动

### 1.2、 发展史

CSS1.0

CSS2.0	DIV+CSS，HTML与CSS结构分离的思想，网页变得简单，利于SEO（搜索引擎优化）

CSS2.1 浮动，定位

CSS3.0 圆角边框，阴影，动画。。。 浏览器兼容性



### 1.3 、 快速入门

程序文件位置拜访参照第一个css程序

style

**基本入门**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>

    <!--    规范,<style> 可以编写css的代码,每一个声明最好使用分号结尾
         语法：
                选择器{
                    声明1;
                    声明2;
                    声明3;
                }
    
    -->
    <style>
        h1{
            color: red;
        }
    </style>
</head>
<body>


<h1>我是标题</h1>

</body>
</html>
```

建议使用分离的规范，用link引入

```html
<link rel="stylesheet" href="css/style.css">
```

css分离的优势：

1. 内容和表现分离
2. 网页结构表现统一，可以实现复用
3. 样式十分的丰富
4. 建议使用独立于html的css文件
5. 利用SEO,容易被搜索引擎收录！

### 1.4、CSS的3种导入方式



```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>

    <!--    外部样式表-->
    <link rel="stylesheet" href="./css/style.css">

    <!--    内部样式表-->
    <style>
        h1{
            color: green;
        }
    </style>

</head>
<body>


<!--优先级：就近原则-->
<!--行内样式：在标签元素中，编写一个style属性，编写样式即可-->
<h1 style="color: red">我是标题</h1>

</body>
</html>
```

拓展：外部样式两种写法

- 链接式(CSS3.0)

​	html

````html
    <!--    外部样式表-->
<link rel="stylesheet" href="./css/style.css">
````

- 导入式(CSS2.1)

```html
<!--    导入式-->
<style>
    @import url("css/style.css");
</style>
```





## 2、选择器

> 作用: 选择页面上的某一个或者某一类元素

### 2.1、基本选择器

1. 标签选择器：选择一类标签 标签{}

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>

    <style>
        /*标签选择器，会选择页面上所有的这个标签的元素*/
        h1{
            color: #ff0101;
            background: aquamarine;
            border-radius: 24px;
        }
        p{
            font-size: 80px;
        }
    </style>

</head>
<body>


<h1>学java</h1>
<p>听狂神说</p>

</body>
</html>
```



2. 类选择器 class：选中所有class属性一致的标签，跨标签 .类名{}

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>


    <style>
        /*类选择器的格式  .class的名称{}
        好处，可以多个标签归类，是同一个class
        */
        .b1{
            color: cyan;
        }
        .b2{
            color: brown;
        }
    </style>

</head>
<body>

<h1 class="b1">标题1</h1>
<h1 class="b2">标题2</h1>
<h1 class="b3">标题3</h1>
<p class="b1">P标签</p>

</body>
</html>
```

3. id选择器：全局唯一！#id名{}

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>

    <style>
        /**id选择器   : id必须保证全局唯一！
        #id{}
        不遵循就近原则，固定的
        id选择器 > class 选择器 > 标签选择器

        */
        #b1{
            color: cyan;
        }
        .style1{
            color: aliceblue;
        }
        h1{
            color: blueviolet;
        }

    </style>

</head>
<body>

<h1 id="b1" class="style1">标题一</h1>
<h1 class="style1">标题二</h1>
<h1 class="style1">标题三</h1>
<h1>标题四</h1>
<h1>标题五</h1>

</body>
</html>
```

优先级：id>class>标签



### 2.2、层次选择器

1、后代选择器：在某个元素的后面

```css
/*后代选择器*/
body p{
    background: red;
}
```

2、子选择器 只有一代

```css
/*子选择器*/
body>p{
    background: blue;
}
```

3、相邻兄弟选择器

```css
/*相邻兄弟选择器：只有一个，相邻（向下）*/
.active + p{
    background: aqua;
}
```

4、通用选择器

```css
/*通用兄弟选择器，当前选中元素的向下的所有兄弟元素*/
.active~p{
    background: #57f3ff;
}
```

### 2.3、结构 伪类选择器

伪类：条件

```css
 /*ul的第一个子元素*/
ul li:first-child{
    background: #57f3ff;
}
 /*ul的最后一个子元素*/
 ul li:last-child{
     background: #57f3ff;
 }

/*选中p1：定位到父元素，选择当前的第一个元素
选择当前p元素的父级元素，选中第一个父级元素的第一个子元素，并且是当前元素才生效，按顺序

*/
p:nth-child(1){
    background: green;
}

/**
选中父元素下的p元素的第二个，按类型
*/
p:nth-of-type(2){
    background: yellow;
}
```

### 2.4、属性选择器 常用

id+class结合

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>

    <style>
        .demo a{
            float: left;
            display: block;
            height: 50px;
            width: 50px;
            border-radius: 10px;
            background: blue;
            text-align: center;
            color: gray;
            text-decoration: none;
            margin-right: 5px;
            font:bold 20px/50px Arial;
        }

        /*  属性名，属性名=属性值（正则）
        = 绝对等于
        *= 包含这个元素
        ^= 以这个开头
        $= 以这个结尾

        */
        /** 存在id属性的元素  a[]{}*/
        /*a[id]{*/
        /*    background: yellow;*/
        /*}*/

        /*id=first的元素*/
        /*a[id=first]{*/
        /*    background: green;*/
        /*}*/

        /*class种有link的元素,id唯一 class可以有多个，所以这里要带 ""*/
        /*a[class*="links"]{*/
        /*    background: #57f3ff;*/
        /*}*/


        /* 选中href中以http开头的元素*/
        /*a[href^=http]{*/
        /*    background: yellow;*/
        /*}*/

        a[href$=pdf]{
            background: yellow;
        }

    </style>
</head>
<body>

<p class="demo">
    <a href="http://www.baidu.com" class="links item first" id="first">1</a>
    <a href="http://www.chdw.online" class="links item active" target="_blank" title="test">2</a>
    <a href="images/123.html" class="links item">3</a>
    <a href="images/123.png" class="links item">4</a>
    <a href="images/123.jpg" class="links item">5</a>
    <a href="abc" class="links item">6</a>
    <a href="/a.pdf" class="links item">7</a>
    <a href="/abc.pdf" class="links item">8</a>
    <a href="abc.doc" class="links item">9</a>
    <a href="abcd.doc" class="links item last">10</a>

</p>
</body>
</html>
```



```html
=
*=
^=
$=
```

## 3 、美化网页元素

### 3.1、为什么要美化网页

1、 有效的传递页面信息

2、美化网页，页面漂亮，才能吸引用户

3、凸显页面的主体

4、提高用户的体验



span标签：重点要突出的字，使用span套起来

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>

  <style>
    #title1{
      font-size: 50px;
    }
  </style>

</head>
<body>

欢迎学习 <span id="title1">java</span>


</body>
</html>
```



### 3.2、字体样式

```html
<!--    font-family: 字体
        font-size:  字体大小
        font-weight:  字体粗细
        color:  字体颜色

-->
<style>
    body {
        font-family:"Arial Black" ,楷体;
        color: brown;
    }

    h1 {
        font-size: 50px;

    }

    .p1 {
        font-weight: bold;
    }
</style>
```

### 3.3、文本样式

1、颜色	color rgb rgba

2、**文本对齐的方式	text-align=center**

3、**首行缩进	text-indent:2em**

4、**行高	line-height:**单行文字上下居中！ line-height = height

5、装饰	text-decoration

6、文本图片水平对齐 vertical-align:middle

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>

<!--
    颜色：
        单词
        RGB  0~F
        RGBA A是透明度(0~1)

    text-align: center;  排版，居中
    text-indent: 2em;   段落 首行缩进
    height: 100px;    line-height: 100px; 行高，和快的高度一致， 就可以上下居中


-->


    <style>
        h1{
            color: rgba(0,255,255,0.5);
            text-align: center;
        }
        .p1{
            text-indent: 2em;
        }
        .p3{
            background: blue;
            height: 100px;
            line-height: 100px;
        }
        /*下划线*/
        .l1{
            text-decoration: underline;
        }
        /*中划线*/
        .l2{
            text-decoration: line-through;
        }
        /*上划线*/
        .l3{
            text-decoration: overline;
        }
        /*超链接去下划线*/
        a{
            text-decoration: none;
        }
        /*水平对齐~ 参照物， a,b*/
        img,span{
            vertical-align: middle;
        }
    </style>

</head>
<body>


<h1>故事介绍</h1>

<p class="l1">123123</p>
<p class="l2">123123</p>
<p class="l3">123123</p>

<p class="p1">
    这个世界名为元泱境界，脉（本质为振动）是构成万物的基础。每隔333年，会有一个神秘而强大的异常生物重生，它就是魁拔！魁拔的每一次出现，都会给元泱境界带来巨大的灾难！即便是天界的神族，也在劫难逃。在天地两界各种力量的全力打击下，魁拔一次次被消灭，但又总是按333年的周期重新出现。魁拔纪元1664年，天神经过精确测算后，在魁拔苏醒前一刻对其进行毁灭性打击。但谁都没有想到，由于一个差错导致新一代魁拔成功地逃脱了致命一击。很快，天界魁拔司和地界神圣联盟均探测到了魁拔依然生还的迹象。因此，找到魁拔，彻底消灭魁拔，再一次成了各地热血勇士的终极目标。
</p>

<p>
    在偏远的兽国窝窝乡，蛮大人和蛮吉每天为取得象征成功和光荣的妖侠纹耀而刻苦修炼，却把他们生活的村庄搅得鸡犬不宁。村民们绞尽脑汁把他们赶走。一天，消灭魁拔的征兵令突然传到窝窝乡，村长趁机怂恿蛮大人和蛮吉从军参战。然而，在这个一切都凭纹耀说话的世界，仅凭蛮大人现有的一块冒牌纹耀，不要说参军，就连住店的资格都没有。受尽歧视的蛮吉和蛮大人决定，混上那艘即将启程去消灭魁拔的巨型战舰，直接挑战魁拔，用热血换取至高的荣誉。
</p>
<p class="p3">All it took was one glance。Now all I ask is one chance，to try to win your heart。Just give me a chance to start。I'll
    show you it was meant to be。To be together is our destiny。
</p>
<p>
    <img src="images/a.gif" alt="">
    <span>asdaakdhjasdjks</span>
</p>

</body>
</html>
```



### 3.4、阴影

```css
 /*text-shadow：阴影颜色，水平偏移，垂直偏移，阴影半径*/
        #price{
            text-shadow: skyblue 10px -10px 2px;

        }
```

### 3.5、 超链接伪类

正常情况下 a和a:hover

```css
 /*默认的颜色*/
        a{
            text-decoration: none;
            color: black;
        }
        /*鼠标悬浮的状态（只需要记住 hover）*/
        a:hover{
            color: orange;
            font-size: 50px;
        }
```



### 3.6、列表

```css
#nav{
    width: 300px;
    background: gray;
}

.title{
    font-size: 18px;
    font-weight: bold;
    text-indent: 1em;
    line-height: 35px;
    background: red;
}

/*ul li*/
/**
list-style:
none 去掉原点
circle 空心圆
decimal 数字
square 正方形

 */
ul{
    /*background: gray;*/
}

ul li{
    height: 30px;
    list-style: none;
    text-indent: 1em;
}

a{
    text-decoration: none;
    font-size: 14px;
    color: #000;
}
a:hover{
    color: orange;
    text-decoration: underline;
}
```



### 3.7、背景

背景颜色

背景图片





```css
div{
    width: 1000px;
    height: 700px;
    border: 1px solid red;
    background-image: url("images/2.gif");
    /*默认是全部平铺的*/

}
.div1{
    background-repeat: repeat-x;
}
.div2{
    background-repeat: repeat-y;
}
.div3{
    background-repeat: no-repeat;
}
```

### 3.8、渐变

```
background-color: #4158D0;
background-image: linear-gradient(43deg, #4158D0 0%, #C850C0 46%, #FFCC70 100%);

```



## 4、盒子模型

### 4.1、什么是盒子模型

margin:外边距

padding:内边距

border:边框

### 4.2、 边框

1、边框的粗细

2、边框的样式

3、边框的颜色