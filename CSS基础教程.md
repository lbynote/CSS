# CSS概述
- CSS指层叠样式表(Cascading Style Sheets)
- 样式定义如何显示HTML元素
- 把样式添加到HTML4.0中，是为了解决内容与表现分离的问题
- 外部样式表可以极大提高工作效率
- 外部样式表通常存储在CSS文件中
- 多个样式定义可层叠为一

# CSS语法
CSS规则由两个主要的部分构成：选择器以及一条或多条声明。  
每条声明由一个属性和一个值组成。  
如：
``` css
h1 {
    color: red; 
    font-size: 14px;
}
```
如果值为若干个单词，则要给值加引号。

# CSS高级语法
可以对选择器进行分组，这样，被分组的选择器就可以分享相同的声明。
``` css
h1, h2, h3, h4, h5, h6 {
    color: green;
}
```
# CSS派生选择器
通过依据元素在其位置的上下文关系来定义样式，可以使标记更加简洁。
``` css
li strong {
    font-style: italic;
    font-weight: normal;
}
```
只将改变列表中的strong元素变为斜体字，而不是通常的粗体字。

# CSS id选择器
id选择器可以为标有特定id的HTML元素指定特定的样式。  
id选择器以“#”来定义。  
CSS:
``` css
#red {color:red;}
```
HTML:
``` html
<p id="red">RED</p>
```
id属性只能在每个HTML文档中出现一次。  

在现代布局中，id选择器常常用于建立派生选择器。
``` css
#siderbar p {
    font-style: italic;
    text-align: right;
}
```

# CSS类选择器
类选择器以一个点号显示。  
CSS：
``` css
.center {text-align: center;}
```

HTML：
``` html
<h1 class="center">heading</h1>
```
和id一样，class也可被用作派生选择器。
``` css
.fancy td {
    color: #f60;
}
```
元素也可以基于它们的类而被选择
``` css
td.fancy {
    color: #f60;
}
```

# CSS属性选择器
## 属性选择器
对带有指定属性的HTML元素设置样式，而不仅限于class和id属性。  
CSS：
``` css
[title] {
    color: red;
}
``` 
HTML：
``` html
<h2 title="hello">Hello World</h2>
```

## 属性和值选择器
CSS:
``` css
[title=hello] {
    border: 5px solid blue;
}
```
HTML:
``` html
可以应用的样式：
<h2 title="hello">Hello World</h2>
不可以应用的样式：
<h2 title="blue">Hello World</h2>
```

## 属性和值选择器-多个值
为包含指定值的title属性的所有元素设置样式，适用于空格分隔的属性值：  
CSS:
``` css
[title~=hello] { color: red; }
```
html:
``` html
可以应用的样式：
<h2 title="hello world">hello world</h2>
<h2 title="hello student">hello student</h2>
不可以应用的样式：
<h2 title="world">hello world</h2>
<h2 title="student">hello world</h2>
```

为包含指定值的lang属性的所有元素设置样式。适用于有连字符分隔的属性值：  
CSS:
``` css
[lang|en] { color: red; }
```
HTML:
``` html
可以应用的样式：
<h2 lang="en">hello</h2>
<h2 lang="en-us">hello</h2>
不可以应用的样式：
<h2 lang="us">hello</h2>
```

## 设置表单样式
属性选择器在为不带有class或id的表单设置样式时特别有用：  
CSS:
``` css
input[type="text"] {
    width: 150px;
    display: block;
    margin-botton: 10px;
    background-color: yellow;
    font-family: Verdana, Arial;
}

input[type="button"] {
    width: 120px;
    margin-left: 35px;
    display: block;
    font-family: Verdana, Arial;
}
```
HTML:
``` html
<form name="input" action="" method="get">
<input type="text" name="Name" value="Bill" size="20">
<input type="button" value="Example Button">
</form>
```

# CSS创建

## 如何插入样式表
当读到一个样式表时，浏览器会根据它来格式化HTML文档。插入样式表的方法有三种：
1. 外部样式表  
    当样式需要应用于很多页面时，外部样式表将是理想的选择。在使用外部样式表的情况下，你可以通过改变一个文件来改变整个网站的外观。每个页面使用<link>标签链接到样式表。<link>标签在文档的头部。  
    ``` html
    <head>
    <link rel="stylesheet" type="text/css" href="mystyle.css">
    </head>
    ```
    浏览器会从文件mystyle.css中读到样式声明，并根据它来格式文档。  
    外部样式表可以在任何文本编辑器中进行编辑。文件不能包含任何html标签。样式表应该以.css扩展名进行保存。下面是一个样式表文件的例子：
    ``` css
    hr {color: sienna;}
    p {margin-left: 20px;}
    body {background-image: url("imgs/back40.gif");}
    ```
    不要在属性值与单位之前留有空格。
2. 内部样式表  
    当单个文档需要特殊的样式时，就应该使用n内部样式表。你可以使用\<style\>标签在文档头部定义内部样式表:
    ``` html
        <head>
        <style type="text/css">
            hr {color: sienna;}
            p {margin-left: 20px;}
            body {background-image: url("images/back40.gif");}
        </style>
        </head>
    ```
3. 内联样式  
    由于要将表现和内容混杂在一起，内联样式会损失掉样式表的许多优势。请慎用这种方法，例如当样式仅需要在一个元素上应用一次时。  
    要使用内联样式，你需要在相关的标签内使用样式(style)属性。Style属性可以包含任何CSS属性，例如：
    ``` html
    <p style="color: sinenna; margin-left: 20px;">
        This is a paragraph
    </p>
    ```