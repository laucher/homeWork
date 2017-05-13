### 垂直居中有几种实现方式，给出代码范例

#### Line-Height Method
![Paste_Image.png](http://upload-images.jianshu.io/upload_images/1667593-4be2e30511484b97.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

<strong>适用范围：单行文本垂直居中</strong>

代码

**html**

```
<div id="parent">
<div id="child">Text here</div>
</div>
```

**css**
```
#child {
line-height: 200px;
}
```

垂直居中一张图片，代码如下:

**html**

```
<div id="parent">
<img src="image.png" alt="" />
</div>
```
**css**

```
#parent {
line-height: 200px;
}
#parent img {
vertical-align: middle;
}
#parent:before{
  content: '';
  display: inline-block;
  height: 100%;
  vertical-align: middle;
}
```

****注：该方法的重点在于line-height的高度等于块级元素的内容框高度(一般都是指:height值)****

****line-height的垂直居中不是纯粹的垂直居中，会有点差异，需要调节vertical-align.****
#### CSS Table Method


![Paste_Image.png](http://upload-images.jianshu.io/upload_images/1667593-6ae441ff32bb4d1a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

****适用范围：通用****

代码：

**html**
```
<div id="parent">
<div id="child">Content here</div>
</div>
```
**css**
```
#parent {
display: table;
}
#child {
display: table-cell;
vertical-align: middle;
}
```
低版本 IE fix bug：
```
#child {
display: inline-block;
}
```

****注：vertical-align:middle这个属性一般情况下只对行内元素生效，对块级元素只有table-cell生效。****

#### Absolute Positioning and Negative Margin

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/1667593-ae15d6bec60157ff.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

****适用：块级元素 但在IE版本低于7时不能正常工作****

代码：

**html**

```
<div id="parent">
<div id="child">Content here</div>
</div>
```

**css**
```
#parent {
position: relative;
}
#child {
position: absolute;
top: 0;
bottom: 0;
left: 0;
right: 0;
width: 50%;
height: 30%;
margin: auto;
}
```

#### Equal Top and Bottom Padding

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/1667593-3afa5c6b05856b93.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

****适用：通用****

代码：

**html**
```
<div id="parent">
<div id="child">Content here</div>
</div>
```
**css**
```
#parent {
padding: 5% 0;
}
#child {
padding: 10% 0;
}
```
****注：用margin也可以做到同样的效果，但是必须注意下height的高度。****

#### Floater Div###

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/1667593-63db39ba5ac9e2e5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

****适用：通用。****

代码：

**html**
```
<div id="parent">
<div id="floater"></div>
<div id="child">Content here</div>
</div>
```
**css**
```
#parent {
height: 250px;
}
#floater {
float: left;
height: 50%;
width: 100%;
margin-bottom: -50px;
}
#child {
clear: both;
height: 100px;
}
```