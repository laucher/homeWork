### 动手测试并列出4条以上的特性区别

1. 行内元素和inline-block元素水平方向上默认情况下是按基线对齐。
2. 行内元素和inline-block元素默认是不占据一行，块级元素默认占据一行。
3. 行内元素的高度是由line-height来决定，宽度由具体的内容来决定，设置height和width无效。
4. 行内元素设置上下margin,padding,border不占据空间。
5. 行内元素的上下padding,border存在颜色，则颜色会显示。
6. 行内元素可以"感受"到浮动元素的存在。

### 什么是 CSS 继承? 哪些属性能继承，哪些不能？

css继承：继承就是子标签继承了上级标签的CSS样式的属性。
- 不可继承的：display、margin、border、padding、background、height、min-height、max-height、width、min-width、max-width、overflow、position、left、right、top、bottom、z-index、float、clear、table-layout、vertical-align、page-break-after、page-bread-before和unicode-bidi。
- 所有元素可继承：visibility和cursor。
- 内联元素可继承：letter-spacing、word-spacing、white-space、line-height、color、font、font-family、font-size、font-style、font-variant、font-weight、text-decoration、text-transform、direction。
- 终端块状元素可继承：text-indent和text-align。
- 列表元素可继承：list-style、list-style-type、list-style-position、list-style-image。
- 表格元素可继承：border-collapse。


### 如何让块级元素水平居中？如何让行内元素水平居中?

   1. margin:0 atuto; 块级元素
   2. text-align:center; 行内元素(text-align:center;仅作用在块级元素上，所以text-align:center;这个属性应该设置在行内元素的block级父元素上。)

### 用 CSS 实现一个三角形
    
    width: 0;
    height: 0;
    border: 50px solid transparent;
    border-bottom: 100px solid #000000;
    
### 单行文本溢出加 ...如何实现?

    overflow: hidden; 超出部分隐藏
    text-overflow:ellipsis; 显示省略符号
    white-space: nowrap; 不折行

### px, em, rem 有什么区别
    
   1. px 在缩放页面时无法调整那些使用它作为单位的字体、按钮等的大小。
   2. em 的值并不是固定的，会继承父级元素的字体大小，代表倍数。
   3. rem 的值并不是固定的，始终是基于根元素(html)的，也代表倍数。
    
### 解释下面代码的作用?为什么要加引号? 字体里\5b8b\4f53代表什么?
   ```
        body{
          font: 12px/1.5 tahoma,arial,'Hiragino Sans GB','\5b8b\4f53',sans-serif;
        }
   ```
    
   设置字体大小12px，行高1.5，字体取值依次是Hiragino Sans GB，宋体，sans-serif。
   
   当文字是中文时，会加引号这个名称不加引号会被识别成多个元素。
   
   `\5b8b\4f53`是Unicode码， 宋体，使用Unicode是因为网页或css编码是utf-8，直接写成中文，浏览器有可能不能识别，所以要写成Unicode编码。