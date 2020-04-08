# CSS 元素选择器

## CSS 元素选择器
最常见的CSS选择器是元素选择器。换句话说，文档的元素就是最基本的选择器。  
如果设置HTML的样式，选择器通常将是某个HTML元素，甚至可以是HTML本身：
``` css
html {color: black;}
h1 {color: blue;}
```

## 类型选择器
在W3C标准中，元素选择器又称为类型选择器(type selelctor)。  
“类型选择器匹配文档语言元素类型的名称。类型选择器匹配文档树中该元素的每一个实例。”  
因此，也可以为XML文档中的元素设置样式。

# CSS 分组

## 选择器分组
将不同选择器放在规则左边，然后用逗号分隔，就定义了一个规则：其右边的样式将应用到这几个选择器所引用的元素。可以将任意多个选择器分组在仪器，对此没有限制。  

## 通配符选择器
CSS 2引入了一种新的简单选择器--通配选择器(universal selector)，显示为*。该选择器可以与任何元素匹配，就像是一个通配符。  
例如，下面的规则可以是文档中的每个元素都为红色：
``` css
* {color: red;}
```

## 声明分组
我们既可以对选择器进行分组，也可以对声明分组。  
``` css
h1 {font: 28px Verdana; color: white; background: black;}
```
对声明分组，一定要在各个声明的最后使用分号。浏览器会忽略样式表中的空白符。

# CSS 类选择器详解
类选择器允许以一种独立于文档元素的方式来指定样式。

## CSS 类选择器
类选择器允许以一种独立于文档元素的方式来指定样式。  
该选择器可以单独使用，也可以与其他元素结合使用。  
要应用样式而不考虑具体设计的元素，最常用的方法就是使用类选择器。  

### 修改HTML代码
在使用类选择器之前，需要修改具体的文档标记，以便类选择器正常工作。  
为了将类选择器的样式与元素关联，必须将class指定为一个适当的值：
``` html
<h1 class="important">This is heading</h1>
<p class="important">This is a paragraph</p>
```
在上面的代码中，两个元素的class都指定为important。

### 语法
使用以下语法向这些归类的元素应用样式，即类名之前有一个点号，然后结合通配选择器：
``` css
*.important {color: red;}
```

### 结合元素选择器
类选择器可以结合元素选择器来使用。  
``` css
p.important {color: red;}
```
选择器现在会匹配class属性包含important的所有p元素。

## CSS 多类选择器
在HTML中，一个class值可能包含了一个词列表，各个词之间用空格分隔：
``` html
<p class="important warning">This is a paragraph</p>
```
这两个词无关顺序。  
假设class为important的所有元素都是粗体，而class为warning的所有元素为斜体，class中同时包含important和warning的所有元素还有一个银色的背景，就可以写作：
``` css
*.important {font-weight: bold;}
*.warning {font-style: italic;}
*.important.warning {background: silver;}
```
通过把两个类选择器链接在一起，仅可以选择同时包含这些类型的元素（类名的顺序不限）。  
如果一个多类选择器包含类名列表中没有一个类型，匹配就会失败。

# CSS ID选择器详解
ID选择器允许以一种独立于文档元素的方式来指定样式。

## CSS ID选择器
在某些方面，ID选择器类似于类选择器，不过也有一些重要差别。

### 语法
首先，ID选择器前面有一个#号:
``` css
*#intro {font-weight: bold;}
```
ID选择器要引用id属性中的值：
``` html
<p id="intro">This is a pagagraph</p>
```

## 类选择器和ID选择器

区别：
1. 在一个HTML文档中，ID选择器只能使用一次。
2. ID选择器不能结合使用，因为ID属性不允许有以空格分隔的词列表。
3. 可以声明独立的ID选择器，并附加到不同的元素上（不同文档中）。

# CSS属性选择器

CSS 2引入了属性选择器。属性选择器可以根据元素的属性及属性值来选择元素。

## 简单属性选择
如果希望选择有某个属性的元素，而不论属性是什么，可以使用简单属性选择器。

### 例1
如果希望把包含标题（title）的所有元素变为红色，可以写作：
``` css
*[title] {color: red;}
```

### 例2
对有href属性的锚应用样式：
``` css
a[href] {color: red;}
```

### 例3
根据多个属性进行选择，只需将属性选择器链接在一起即可。  
将同时又href和title属性的超链接的文本设置为红色：
``` css
a[href][title] {color: red;}
```

## 根据具体属性值选择
出了选择拥有某些属性的元素，还可以进一步缩小选择范围，只选择有特定属性值的元素。

### 例1
假设希望将指向Web服务器上某个指定文档的超链接变为红色：
``` css
a[href="..."] {color: red;}
```

### 例2
与简单属性选择器类似，可以把多个属性值选择器链接在一起来选择一个文档：
``` css
a[href="..."][title="..."] {color: red;}
```

### 属性与属性值必须完全匹配
如果属性值包含用空格分隔的值列表，匹配可能出问题。  

## 根据部分属性值选择
如果需要根据属性值中的词列表的某个词进行选择，则需要使用波浪号（~）。  
假设想选择class属性中包含improtant元素：
``` css
p[class~="important"] {color: red;}
```
如果忽略了波浪号，则说明需要完成完全值匹配。

## 子串匹配属性选择器
| 类型 | 描述 |
| :-: | :-: |
| [abc^="def"] | 选择abc属性值以“def”开头的元素 |
| [abc$="def"] | 选择abc属性值以“def”开头的元素 |
| [abc*="def"] | 选择abc属性值以“def”开头的元素 |


## 特定属性选择类型
``` css
*[lan|="en"] {color: red;}
```
上面的规则会选择lang属性等于en或以en-开头的所有元素。

# CSS 后代选择器
后代选择器（descendant selector）又称为包含选择器。  
后代选择器可以选择作为某元素后代的元素。

## 根据上下文选择元素
我们可以定义后代选择器来创建一些规则，是这些规则在某些文档结构中起作用，而在另外一些结构中不起作用。  
如果希望只对h1元素中的em元素应用样式：
``` css
h1 em {color: red;}
```

## 语法解释
在后代选择器中，规则左边的选择器一段包含两个或多个用空格分隔的选择器。选择器之间的空格是一种结合符（combinator）。

# CSS子元素选择器
与后代选择器相比，子元素选择器（child selctors）只能选择作为某元素子元素的元素。

## 选择子元素
如果不下网选择任意的后代元素，而是只选择某个元素的子元素，使用子元素选择器。  
例如，希望只选择作为h1元素子元素的strong元素：
``` css
h1 > strong {color: red;}
```
这个规则会把第一个h1下面的两个strong元素变为红色，但是第二个h1中的strong不受影响：
``` html
<h1>This is <strong>very</strong> important.</h1>
<h1>This is <em>really <strong>very</strong></em> important.</h1>
```

## 语法解释
子选择器使用大于号作为子结合符。子结合符两边可以有空白符。

## 结合后代选择器和子选择器
``` css
table.company td > p
```
上面的规则会选择作为td元素子元素的所有p元素，这个td元素本身从table元素继承，该table元素有一个包含company的class属性。

# CSS 相邻兄弟选择器
相邻兄弟选择器（adjacent sibling selector）可选择紧接在另一元素后的元素，且两者有相同父元素。

## 选择相邻兄弟
如果需要选择紧接在另一个元素后的元素，而且两者有相同的父元素，可以使用相邻兄弟选择器。  
如果要增加紧接在h1元素后出现的段落的上边距：
``` css
h1 + p {color: red;}
```

## 语法解释
相邻兄弟选择器使用了加号（+），即相邻兄弟结合符。  

### 结合其他选择器
``` css
html > body table + ul {margin-top: 20px;}
```
选择紧接在table元素后出现的所有兄弟ul元素，该table元素包含在一个body元素中，body元素本身是html元素的子元素。

# CSS 伪类（pseudo-classes）
CSS伪类用于向某些选择器添加特殊的效果。

## 语法
伪类的语法：
``` css
selelctor : pseudo-class {property: value;}
```
CSS类也可与伪类配合使用：
``` css
selector.class : pseudo-class {property: value;}
```

## 锚伪类
在支持CSS的浏览器中，链接的不同状态都可以用不同的方式显示：
``` css
a:link {color: #FF0000;}        /* 为访问的链接 */
a:visited {color: #00FF00;}     /* 已访问的链接 */
a:hover {color: #FF00FF;}       /* 鼠标移动到链接上 */
a:active {color: #0000FF;}      /* 选定的链接 */
```

## 伪类与CSS类
伪类可以与CSS类配合使用：
``` html
a.red:visited {color: #FF0000;}

<a class="red" href="...">CSS</a>
```

## CSS 2 :first-child伪类
使用:first-child伪类来选择元素的第一个子元素。
``` css
p:first-child {font-weight: bold;}
```
将作为某元素第一个子元素的所有p元素设置为粗体。

## CSS 2 :lang伪类
:lang伪类为不同的语言定义特殊的规则。  
为属性值为no的q元素定义引号的类型：
``` css
q:lang(no) {quotes: "~""~";}
```

# CSS 伪元素

## 语法
``` css
selector:pseudo-element {property: value;}
```
CSS类也可以与伪元素配合使用：
``` css
selector.class:pseudo-element {property: value;}
```

## :first-line伪元素
用于向文本的首行设置特殊样式。  
根据“first-line”伪元素中的样式对p元素的第一行文本进行格式化：
``` css
p:first-line {
    color: ##FF0000;
    font-variant: small-caps;
}
```
fitst-line伪元素只能用于块级元素

## :first-letter伪元素
用于向文本的首字母设置特殊样式

## 伪元素和CSS类
伪元素可以与CSS类配合使用：
``` css
p.article:first-letter {color: #FF0000;}
```

## 多重伪元素
可以结合多个伪元素来使用。  
``` css
p:first-letter {
    color: #FF0000;
    font-size: xx-large;
}

p:first-line {
    color: #0000FF;
    font-variant: small-caps;
}
```
段落的第一个字母将显示为红色，其字体大小为xx-large。第一行中的其余文本将为蓝色，并以小型大写字母显示。

## CSS 2 :before
可以在元素的前面插入新内容。
``` css
h1:before {content: url(...);}
```

## CSS 2 :after
在元素的内容之后插入新内容。