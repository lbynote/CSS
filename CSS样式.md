# CSS背景

## 背景色
可以使用background-color属性为元素设置背景色。这个属性接受任何合法的颜色值。  
这条规则把元素的背景设置为灰色：
``` css
p {background-color: gray;}
```
如果你希望背景色从元素中的文本向外稍有衍生，只需增加一些内边距：
``` css
p {background-color: gray; padding: 20px;}
```
可以为所有元素设置背景色，这包括body一直到em和a等行内元素。  
background-color不能继承，其默认值是transparent，即“透明”。也就是说，如果一个元素没有指定背景色，那么背景就是透明的，这样其祖先元素的背景才能可见。

## 背景图像
要把图像放入背景，需要使用background-image属性。background-image属性的默认值是none，表示背景上没有放置任何图像。  
如果需要设置一个背景图像，必须为这个属性设置一个URL值：
``` css
body {background-image: url('/i/eg_bg_04.gif/');}
```
大数背景都应用于body元素，不过并不仅限于此。  
下面例子为一个段落应用了一个背景，而不会对文档的其他部分应用背景：
``` css
p.flower {background-image: url('/i/eg_bg_o3.gif/');}
```
甚至可以为行内元素设置图像背景，下面的例子为一个链接设置了背景图像：
``` css
a.radio {background-iamge: url('/i/eg_bg_07.gif/');}
```
理论上讲，甚至可以向textareas和select等替换元素的背景应用图像，不过并不是所有用户代理都能很好地处理这种情况。  
另外还要补充一点，background-image也不能继承。事实上，所有背景属性都不能继承。

## 背景重复
如果需要在页面上对背景图像进行平铺，可以使用background-repeat属性。  
属性值repeat导致图像在水平垂直方向上都平铺。repeat-x和repeat-y分别导致图像只在水平或垂直方向上重复，no-repeat则不允许图像在任何方向上平铺。  
默认地，图像背景将从一个元素的左上角开始。
``` css
body {
    background-image: url('/i/eg_bg_03/gif/');
    background-repeat: repeat-y;
}
```

## 背景定位
可以利用background-position属性改变图像在背景中的位置。  
下面的例子在body元素中将一个背景图像居中放置：
``` css
body {
    background-image: url('/i/eg_bg_03.gif/');
    background-repeat: no-repeat;
    background-position: center;
}
```
为background-position属性提供值有很多方法。首先，可以使用一些关键字：top、botton、left、right和center。通常，这些关键字会成堆出现，不过也不总是这样。还可以只用长度值，如100px或5cm。最后也可以使用百分数值。不同类型的值对于背景图像的放置稍有差异。

### 关键字
根据规范，位置关键字可以按任何顺序出现，只要保证不超过两个关键字--一个对对应水平方向，另一个对应垂直方向。  
如果只出现一个关键字，则认为另一个关键字是center。  
如果希望每个段落的中部上方出现一个图像，只需声明如下：
``` css
p {
    background-image: url('bgimg.gif');
    background-repeat: no-repeat;
    background-position: top;
}
```

### 百分比数值
假设希望用百分数值将图像在其元素中居中：
``` css
body {
    background-image: url('/i/eg_bg_03.gif/');
    background-repeat: no-repeat;
    background-position: 50% 50%;
}
```
这会导致图像适当防止，其中心与其元素的中心对齐。换句话说，百分比数值同时应用于元素和图像。也就是说，图像中描述为50% 50%的点（中心点）与元素中描述为50% 50%的点（中心点）对齐。  
如果图像位于0% 0%，其左上角将放在元素内边距区的左上角。如果图像位置是100% 100%，会使图像的右下角放在右边距的右下角。  
如果想把图像放在水平方向2/3，垂直方向1/3处，可以这样声明：
``` css
body {
    background-image: url('/i/eg_bg_03.gif/');
    background-repeat: no-repeat;
    background-position: 66% 33%;
}
```
如果值提供一个百分数值，所提供的这个值将用作水平值，垂直值将假设为50%。这一点与关键字类似。  
background-position的默认值是0% 0%，在功能上相当于top left。这就解释了背景图像为什么总是从元素内边距区的左上角开始平铺，除非您设置了不同的位置值。

### 长度值
长度值解释的是元素内边距区左上角的偏移。偏移点是图像的左上角。  
比如，如果设置值为50px 100px，图像的左上角将在元素内边距区左上角向右50像素、向下100像素的位置上：
``` css
body {
    background-image: url('/i/rg_bg_03.gif/');
    background-repeat: no-repeat;
    background-position: 50px 100px;
}
```
注意，这一点与百分数值不同，因为偏移只是从一个左上角到另一个左上角。也就是说，图像的左上角与background-position声明中的指定的点对齐。

## 背景关联
如果文档比较长，那么当文档向下滚动时，背景图像也会随之滚动。当文档滚动到超过图像的位置时，图像就会消失。  
可以通过background-attachment属性防止这种滚动。通过这种属性，可以声明图像相对于可视区是固定的(fixed)，因此不会受滚动的影响：
``` css
body {
    background-image: url('/i/eg_bg_02.gif/');
    background-repeat: no-repeat;
    background-attachment: fixed;
}
```
background-attachment属性的默认值是scroll，也就是说，在默认情况下，背景会随文档滚动。

# CSS文本

## 缩进文本
把Web页面上的段落的第一行缩进，这是一种最常用的文本格式化效果。  
通过text-indent属性，所有元素的第一行都可以缩进一个给定的长度，甚至该长度可以是负值。  
这个属性最常见的用途是将段落的首航缩进，下面的规则会使所有段落的首行缩进5em：
``` css
p {text-indent: 5em;}
```
一般来说，可以为所有块级元素应用text-indent，但无法将该属性应用于行内元素，图像之类的替换元素上也无法应用text-indent属性，不过，如果一个块级元素（比如段落）的行首有一个图像，它会随改行的其余文本移动。  
如果想把一个行内元素的第一行“缩进”，可以用左内边距或外边距创造这种效果。

### 使用负值
text-indent还可以设置为负值。利用这种技术，可以实现很多有趣的效果，比如“悬挂缩进”，即第一行悬挂在元素中余下部分的左边：
``` css
p {text-indent: -5em;}
```
不过在为text-indent设置负值时要当心，如果对一个段落设置了负值，那么首行的某些文本可能会超出浏览器窗口的左界面。为了避免出现这种显示问题，建议针对负缩进再设置一个外边距或一些内边距：
``` css
p {text-indent: -5em; padding-left: 5em;}
```

### 使用百分比值
text-indent可以使用所有长度单位，包括百分比值。  
百分数要相对于缩进元素父元素的宽度。换句话说，如果将缩进设置为20%，所影响元素的第一行会缩进其父元素宽度的20%。  
在下例中，缩进值是父元素的20%，即100px：
``` css
div {width: 500px;}
p {text-indent: 20%;}

<div>
    <p>this is a paragraph</p>
</div>
```

### 继承
text-indent属性可以继承，如：
``` css
div#outer {width: 500px;}
div#inner {text-indent: 10%;}
p {width: 200px;}

<div id="outer">
    <div id="inner">some text. some text.
        <p>this is a paragraph.</p>
    </div>
</div>
```
以上标记中的段落也会缩进50像素，这是因为这个段落继承了id为inner的div元素的缩进值。

## 水平对齐
text-align是一个基本的属性，它会影响一个元素中的文本行互相之间的对齐方式。  
值left、right和center会导致元素中的文本分别左对齐、右对齐和居中。  
text-align的默认值是left。  
将块级元素或表居中，要通过在这些元素伤适当地设置左、右外边距来实现。 

### text-align: center与&lt;center&gt;
&lt;center&gt;不仅影响文本，还会把整个元素居中。text-align不会控制元素的对齐，而只影响内部内容。元素本身不会从一段移到另一端，只是其中的文本受影响。

### justify
最后一个水平对齐属性是justify。  
在两端对齐文本中，文本行的左右两端都放在父元素的内边界上。然后，调整单词和字母间的间距，是各行的长度恰好相等。你也许已经注意到了，两端对齐文本在打印领域很常见。  
需要注意的是，要由用户代理（而不是CSS）来确定两端对齐文本如何拉伸，以填满父元素左右边界之间的空间。

## 字间隔
word-spacing属性可以改变字（单词）之间的标准间隔，其默认值normal与设置值为0是一样的。  
word-spacing属性接受一个正长度值或负长度值。如果提供一个正长度值，那么字之间的间隔就会增加。为word-spacing设置为一个负值，会把它拉近。
``` css
p.spread {word-spacing: 30px;}
p.tight {word-spacing: -0.5em;}

<p class="spread">
This is a paragraph. The spaces between words will be increased.
</p>

<p class="tight">
This is a paragraph. The spaces between words will be decreased.
</p>
```

## 字母间隔
letter-spacing属性与word-spacing属性的区别在于，字母间隔修改的是字符或字母之间的间隔。  
与word-spacing属性一样，letter-spacing属性的可取值包括所有长度。默认关键字是normal（这与letter-spacing: 0相同）。输入的长度值会使字母之间的间隔增加或减少指定的量。
``` css
h1 {letter-spacing: -0.5em;}
h4 {letter-spacing: 20px;}

<h1>This is header 1</h1>
<h4>This is header 4</h4>
```

## 字符替换
text-transform属性处理文本的大小写。这个属性有4个值：
- none
- uppercase
- lowercase
- capitalize

默认值none对文本不做任何改动，将使用源文档中的原有大小写。顾名思义，uppercase和lowercase将文本转换为全大写和全小写字符。最后，capitalize只对每个单词的首字母大写。  
``` css
h1 {text-transform: uppercase;}
```

## 文本装饰
text-decoration属性有5个值：
- none
- underline
- overline
- line-through
- blink

underline会对元素加下划线，就像HTML中的U元素一样。  
overline会在文本的顶端画一个上划线。  
line-through则会在文本中间画一个贯穿线，等价于HTML中的S和strike元素。  
blink会让文本闪烁。  
none值会关闭原本应用到一个元素上的所有装饰。通常，无装饰的文本是默认外观，但也不总是这样。例如，链接默认地会有下划线。如果你希望去掉超链接的下划线，可以使用以下CSS来做到这一点：
``` css
a {text-decoration: none;}
```
如果显式地用这样一个规则去掉链接的下划线，那么锚与正常文本之间在视觉上的唯一差别就是颜色（至少默认是这样的，不过也不能完全保证其颜色肯定有区别）。  

还可以在一个规则中结合多种装饰。如果希望所有超链接既有下划线，又有上划线，则规则如下：
``` css
a: link a: visited {text-decoration: underline overline;}
```

## 处理空白符
white-space属性会影响到用户代理对源文档中的空格、换行和tab字符的处理。  
通过使用该属性，可以影响浏览器处理字之间和文本行之间的空白符的方式。从某种程度上讲，默认的XHTML处理已经完成了空白符处理：它会把所有空白符合并为一个空白符。  

### 值normal
可以显式地设置这种默认行为：
``` css
p {white-space: normal;}
```
上面的规则告诉浏览器按照平常的方法去处理：丢掉多余的空白符。如果给定这个值，换行字符（回车）会转换为空格，一行中多个空格的序列也会转换为一个空格。

### 值pre
如果将white-space设置为pre，受这个属性影响的元素中，空白符的处理行为就像XHTML的pre元素一样：空白符不会被忽略。  
如果white-space属性的值为pre，浏览器将会注意额外的空格，甚至回车。在这个方面，任何元素都可以相当于一个pre元素。

### 值nowrap
与之相对的值是nowrap，它会防止元素中的文本换行，除非只用了一个br元素。

### 值pre-wrap和pre-line
CSS 2.1引入了值pre-wrap和pre-line。

如果元素的white-space设置为pre-wrap，那么元素中的文本会保留空白序列，但是文本行会正常地换行。如果设置为这个值，源文本中的行分隔符以及生成的行分隔符也会保留。

pre-line与pre-wrap相反，会像正常文本中一样合并空白符序列，但保留换行符。

![white-space attribute](/img/white-spaceAttribute.jpg/)

# 字体
CSS字体属性定义文本的字体系列、大小、加粗、风格（如斜体）和变形（如小型大写字母）。

## CSS字体系列
在CSS中，有两种不同类型的字体系列名称：
- 通用字体系列 -- 拥有相似外观的字体系列组合（比如“Serif”和“Monospace”）
- 特定字体系列 -- 具体的字体系列（比如“Times”和“Courier”）

除了各种特定的字体系列外，CSS定义了5中通用字体系列：
- Serif
- Sans-serif
- Monospace
- Cursive
- Fantasy

## 指定字体系列
使用font-family属性定义文本的字体系列。  

### 使用通用字体系列
如果你希望文档使用一种sans-serif字体，但是你并不关心是哪一种字体，以下就是一个合适的声明：
``` css
body {font-family: sans-serif;}
```
这样用户代理就会从sans-serif字体系列中选择一个字体（如Helvetica），并将其应用到body元素。因为有继承，这种字体选择还将应用到body元素中包含的所有元素，除非有一种更特定的选择器将其覆盖。

### 指定字体系列
除了使用通用的字体系列，你还可以通过font-family属性设置更具体的字体。  
下面的例子为所有h1元素设置了Georgia字体：
``` css
h1 {font-family: Georgia;}
```
这样的规则同时会产生一个另外的问题，如果用户代理上没有安装Georgia字体，就只能使用用户代理的默认字体来显示h1元素，我们可以通过结合特定字体名和通用字体系列来解决这个问题：
``` css
h1 {font-family: Georgia, serif;}
```
如果用户没有安装Georgia，但安装了Times字体（serif字体系列中的一种字体），用户代理就可能对h1元素使用Time。尽管Times与Georgia并不完全匹配，但至少足够接近。  
因此，建议在所有font-family规则中都提供一个通用字体系列。这样就提供了一条后路，在用户代理无法提供与规则匹配的特定字体时，就可以选择一个候选字体。  
如果对字体非常熟悉，可以为给定的元素指定一系列类似的字体。要做到这一点，需要把这些字体按照优先顺序排列，然后用逗号进行连接：
``` css
p {font-family: Times, TimesNR, 'New Century Schoolbool', Georgia, 'New York', serif;}
```
根据这个列表，用户代理会按所列的顺序查找这些字体。如果列出的所有字体都不可用，就会简单地选择一种可用的serif字体。

### 使用引号
上面的例子中使用了单引号。只有当字体名中有一个或多个空格（比如New York），或者如果字体包括#或$之类的符号，才需要在font-family声明中加引号。  
单引号和双引号都可以接受。但是，如果把一个font-family属性放在HTML的style属性中，则需要使用该属性本身未使用的那种单引号:
``` html
<p style="font-family: Times, TimesNR, 'New Century Schoolbook', Georgia, 'New York', serif;">...</p>
```

## 字体风格
font-style属性最常用于规定斜体文本。该属性有三个值：
- normal：文本正常显示
- italic：文本斜体显示
- oblique：文本倾斜显示

### italic和oblique的区别
斜体（italic）是一种简单的字体风格，对每个字母的结构有一些小改动，来反映变化的外观。与此不同，倾斜（oblique）文本则是正常竖直文本的一个倾斜版本。  
通常情况下，italic和oblique文本在web浏览器中看上去完全一样。

## 字体变形
font-variant属性可以设定小型大写字母。  
小型大写字母不是一般的大写字母，也不是小写字母，这种字母采用不同大小的大写字母。
``` css
p.normal {font-variant: normal;}
p.small {font-variant: small-caps;}
```

## 字体加粗
font-weight属性设置文本的粗细。  
使用bold关键字可以将文本设置为粗体。  
关键字100~900为字体指定了9级加粗度。如果一个字体内置了这些加粗界别，那么这些数字就直接映射到预定义的级别，100对应最细的字体变形，900对应最粗的字体变形。数字400等价于normal，而700等价于bold。  
如果将元素的加粗设置为bolder，浏览器会设置比所继承值更粗的一个字体加粗。与此相反，关键词lighter会导致浏览器将加粗度下移而不是上移。
``` css
p.normal {font-weight: normal;}
p.thick {font-weight: bold;}
p.thicker {font-weight: 900;}
```

## 字体大小
font-size属性设置文本的大小。  
font-size值可以是绝对或相对值。  

绝对值：
- 将文本设置为指定的大小
- 不允许用户在所有浏览器中改变文本大小（不利于可用性）
- 绝对大小在确定了输出的物理尺寸时很有用

相对大小：
- 相对于周围的元素来设置大小
- 允许用户在浏览器改变文本大小

如果没有规定字体大小，普通文本（比如段落）的默认大小是16像素（16px = 1em）。

### 使用像素来设置字体大小
通过像素设置文本大小，可以对文本大小进行完全控制：
``` css
h1 {font-size: 60px;}
h2 {font-size: 40px;}
p {font-size: 14px;}
```
在FireFox、Chrome、Safari中，可以重新调整以上例子的文本大小，但是在IE中不行。  

### 使用em来设置字体大小
如果要避免在IE中无法调整文本的问题，许多开发者使用em单位代替pixels。  
1em等于当前的字体尺寸。如果一个元素的font-size为16像素，则1em就等于16像素。在设置字体大小时，em的值会相对于父元素的字体大小改变。  
但是，在IE中仍存在问题，在重设文本大小时，会比正常的尺寸更大或更小。

### 结合使用百分比和em
在所有浏览器中均有效的方案为body元素（父元素）以百分比设置默认的font-size值：
``` css
body {font-size: 100%;}
h1 {font-size: 3.75em;}
h2 {font-size: 2.5em;}
p {font-size: 0.875em;}
```
在所有浏览器中，可以显示相同的文本大小，并允许所有浏览器缩放文本的大小。

# CSS链接

## 设置链接的样式
能够设置链接样式的CSS属性有很多种（例如color，font-family，background等）。  
链接的特殊性在于能够根据它们所处的状态来设置它们的样式。  
链接的4种状态：
- a:link -- 普通的、未被访问的链接
- a:visited -- 用户已访问的链接
- a:hover -- 鼠标指针位于链接的上方
- a:active -- 链接被点击的时刻
``` css
a:link {color: #FF0000;}
a:visited {color: #00FF00;}
a:hover {color: #FF00FF;}
a:active {color: #0000FF;}
```
当为链接的不同状态设置样式时，按照以下次序规则：
- a:hover必须位于a:link和a:visited之后
- a:active必须位于a:hover之后

## 常见的链接样式

### 文本修饰
text-decoration属性大多用于去掉链接中的下划线：
``` css
a:link {text-decoration: none;}
a:visited {}
```

### 背景色
background-color属性规定了链接的背景色：
``` css
a:link {background-color: #B2FF99;}
a:visited {background-color: #FFFF85;}
a:hover {background-color: #FF704D;}
a:active {background-color: #FF704D;}
```

# CSS列表
CSS列表属性允许你防止、改变列表标志，或者将图像作为列表项标志。

## 列表

### 列表类型
要影响列表的样式，最简单（同时支持最充分）的办法就是改变其标志类型。  
例如，在一个无序列表中，列表项的标志（maker）是出现在各列表项旁边的圆点。在有序列表中，标志可能是字母、数字或另外某种特殊计数体系中的一个符号。  
要修改用于列表项的标志类型，可以使用属性list-style-type：
``` css
ul {list-style-type: square;}
```
上面把无序列表中的列表项标志设置为方块。

### 列表项图像
如果想对个各标志使用一个图像，可以利用list-style-image属性做到：
``` css
ul li {list-style-image: url(xxx.gif);}
```
只需要使用一个url()值，就可以使用图像作为标志。

### 列表标志位置
CSS 2.1可以确定标志出现在列表项内容之外还是内容内部。这是利用list-style-position完成的。

### 简写列表样式
为简单起见，可以将以上3个列表样式属性合并为一个方便的属性：list-style：
``` css
li {list-style: url(xxx.gif) square inside;}
```
list-style的值可以按任何顺序列出，而且这些值都可以忽略。只要提供了一个值，其他的就会填入默认值。

# CSS表格

## 表格边框
如需在CSS中设置表格边框，请使用border属性：
``` css
table, th, td {border: 1px solid blue;}
```
上例中的表格具有双线条边框，这是由于table、th、td元素都有独立的边框。如果需要把表格显示为单线条边框，请使用border-collapse属性。

## 折叠边框
border-collapse属性设置是否将表格边框折叠为单一边框：
``` css
table {border-collapse: collapse;}

table, th, td {border: 1px solid black;}
```

## 表格宽度和高度
通过width和height属性定义表格的宽度和高度：
``` css
table {width: 100%;}

th {height: 50px;}
```

## 表格文本对齐
text-align和vertical-align属性设置表格中文本的对齐方式。  
test-align属性设置水平对齐方式，比如左对齐、右对齐或者居中：
``` css
td {text-align: right;}
```
vertical-align属性设置垂直对齐方式，比如顶部对齐、底部对齐或者居中：
``` css
td {height: 50px; vertical-align: botton;}
```

## 表格内边距
如需控制表格中内容与边框的距离，请为td和th元素设置padding属性：
td {padding: 15px;}

## 表格颜色
``` css
table, th, td {border:1px solid green;}

th {background-color: green; color: white;}
```

# CSS轮廓
轮廓（outline）是绘制于元素周围的一条线，位于边框边缘的外围，可起到突出元素的作用。  
CSS outline属性规定元素轮廓的样式、颜色和深度。