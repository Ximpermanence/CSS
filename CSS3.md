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

1、颜色

2、文本对齐的方式

3、首行缩进

4、行高

5、装饰