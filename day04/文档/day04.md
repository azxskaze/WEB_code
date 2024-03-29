[TOC]
## 一、布局方式
![定位机制0](assets\定位机制0.png)

### 1. 普通文档流

​		默认布局方式，按照代码书写顺序及标签类型从上到下，从左到右依次显示。

![普通流定位1](assets\普通流定位1.png)

### 2. 浮动布局

​		主要用于设置块元素的水平排列

![浮动流定位2](assets\浮动流定位2.png)

#### 1）属性

```
float
```

#### 2）取值 

可取 left 或 right，设置元素向左浮动或向右浮动

```css
float:left/right;
clear:left/right/both
```

#### 3）特点

- 元素设置浮动会从原始位置脱流，向左或向右依次停靠在其他元素边缘，在文档中不再占位
- 元素设置浮动，就具有块元素的特征，可以手动调整宽高
- "文字环绕"：浮动元素遮挡正常元素的位置，无法遮挡正常内容的显示，内容围绕在浮动元素周围显示

#### 4）常见问题 

子元素全部设置浮动，导致父元素高度为0，影响父元素背景色和背景图片展示,影响页面布局

#### 5）解决

- 对于内容固定的元素，如果子元素都浮动，可以给父元素固定高度(例:导航栏)
- 在父元素的末尾添加空的块元素。设置 clear:both; 清除浮动
- 为父元素设置 overflow:hidden; 解决高度为0

### 3. 定位布局

​		结合偏移属性调整元素的显示位置

![绝对与相对定位关系3](assets\绝对与相对定位关系3.png)

#### 1）属性

属性规定元素的定位类型，任何元素都可以定位，不过绝对或固定元素会生成一个块级框，而不论该元素本身是什么类型。

```css
position
```

#### 2）取值
可取relative（相对定位）/ absolute（绝对定位）/ fixed（固定定位）
```css
postion:relative/absolute/fixed
```
#### 3）偏移属性
设置定位的元素可以使用偏移属性调整距离参照物的位置
```text
top   	距参照物的顶部
right	距参照物的右侧
bottom	距参照物的底部
left	距参照物的左侧
```
#### 4）分类 
+ relative 相对定位
```text
元素设置相对定位,可参照元素在文档中的原始位置进行偏移,不会脱离文档流
```
+ absolute 绝对定位
```text
1. 绝对定位的元素参照离他最近的已经定位的祖先元素进行偏移,如果没有,则参照窗口进行偏移
2. 绝对定位的元素会脱流,在文档中不占位,可以手动设置宽高
```
使用绝对定位 : 父元素设置相对定位,子元素绝对定位，参照已定位的父元素偏移

+ fixed 固定定位
```text
1. 参照窗口进行定位,不跟随网页滚动而滚动
2. 脱离文档流
```
#### 5）堆叠次序 
元素发生堆叠时可以使用 z-index 属性调整已定位元素的显示位置，值越大元素越靠上：
+ 属性 : z-index
+ 取值 : 无单位的数值,数值越大，越靠上
+ 堆叠：
  1. 定位元素与文档中正常元素发生堆叠，永远是已定位元素在上
  2. 同为已定位元素发生堆叠，按照 HTML 代码的书写顺序，后来者居上

##  二、文本属性

### 1. 字体相关
#### 1）设置字体大小
```css
font-size:20px;
```
#### 2）设置字体粗细程度
```css
font-weight:normal;
```
取值 ：
```text
1. normal（默认值）等价于400
2. bold   (加粗) 等价于700
```
#### 3）设置斜体
```css
font-style:italic;
```
#### 4）设置字体名称
```css
font-family:Arial,"黑体","宋体"; 
```
取值 :

 1. 1.可以指定多个字体名称作为备选字体，使用逗号隔开

 2. 如果字体名称为中文，或者名称中出现了空格，必须使用引号

    例 :

```Css
font-family:Arial;
font-family:"黑体","Microsoft YaHei",Arial;
```

#### 5）字体属性简写
```css
font : style weight size family;
```
注意 :

       1. 如果四个属性值都必须设置，严格按照顺序书
       2. size family 是必填项

### 2. 文本样式
#### 1）文本颜色
```css
color:red;
```
#### 2）文本装饰线
```css
text-decoration:none;
```
取值 :
    underline		  下划线
    overline		     上划线
    line-through 	 删除线
    none			       取消装饰线

#### 3）文本内容的水平对齐方式
```css
text-align:center;
```
取值 : 
```text
left(默认值)	左对齐
center		  居中对齐
right		  右对齐
```
#### 4）行高
```css
line-height:30px;
```
使用 :
    文本在当前行中永远垂直居中，可以借助行高调整文本在元素中的垂直显示位置

     1. line-height = height 设置一行文本在元素中垂直居中
     2. line-height > height 文本下移显示
     3. line-height < height 文本靠上显示

