### text-align: center的作用是什么，作用在什么元素上？能让什么元素水平居中
     
   text-align CSS属性定义行内内容（例如文字）如何相对它的块父元素对齐，text-align并不控制块元素自己的对齐，只控制它的行内内容的对齐。
   
   1. text-align:center的意思是块级元素中的行内内容居中。
   2. 作用在block-level元素上(包括了block和inline-block);
   3. 能让block-level的元素中的行内元素，替换元素和inline-block元素居中。
   
### IE 盒模型和W3C盒模型有什么区别?
    
   W3C标准中padding、border所占的空间不在width,height范围内，IE的盒模型width,height包括content尺寸 + padding + border;
    
### *{ box-sizing: border-box;}的作用是什么？
    
   把所有元素的盒模型设置为width,height包括content尺寸 + padding + border。
    
### line-height: 2和line-height: 200%有什么区别?
    
   1. 计算标准：line-height: 2根据自身元素的字体大小来计算，line-height: 200%根据父元素的字体大小来计算。
   2. 继承：line-height: 2继承给子元素的是2这个缩放因子，line-height: 200%继承给子元素的是200%计算后的值。
    
### inline-block有什么特性？如何去除缝隙？高度不一样的inline-block元素如何顶端对齐?
   
   特性:
   
   1. 默认不占据一行。
   2. 设置的上下`padding`、`margin`、`border`占据文档空间。
   3. 水平排列按照`base-line`对齐，且元素之间会存在一个'空'元素的缝隙。
   4. 可以用`vertical-align`设置垂直对齐。
   5. 可以设置`text-align`属性有效。
   6. 会形成一个BFC(块级格式化上下文)。
   
   总结：一个拥有正常盒模型的行内元素，既拥有inline的特点，也有block的特性，
   
   去除缝隙：
   
   1. 修改html不换行。
   2. 父元素设置`font-size:0;`
   3. 设置负`margin`值。
   4. 元素设置浮动。
   
   高度不一致的inline-block的顶端对齐
   
   `vertical-align:top;`
       
### CSS sprite 是什么?
    
   CSS sprite又称之为精灵图。
   
   原理：把多个小icon合成一个大的图片，使用的时候，元素以这张合成后的大图为背景，通过设置`background-position`的属性来获取指定icon。
   
   优点：合并原来图片的请求，减少http的性能消耗。
   缺点：CSS sprite不能太大，不然下载图片的时间会过长。
   
   应用：
   1. 制作一张网页的图标。
   2. 制作动画。
   
   潜伏题：
   
   域名发散和域名收敛
    
    
### 让一个元素"看不见"有几种方式？有什么区别?
    
   常规：
   
   1. `display:none;`
   2. `visibility:hidden;`
   3. `opacity:0;`
   
   其他(以下消失都是有前提条件的)：
   
   1. height:0;width:0;padding:0;margin:0;border:0; ... etc
   2. position:absolute; left:1000000px; top:100000px; ...etc;
   3. z-index:-1000;...etc
   4. background-color:rgba(0,0,0,0);
   
   总结：
   元素"看不见"的方式主要方式让元素用户在当前页面展示的视口里看不见。
   
   区别：
   1. `display:none;`从文档流消失，不占据文档空间，但是还存在DOM树中。
   2. `visibility:hidden;`和`opacity:0;`还是会占据文档空间。
   3. `display:none;`和`visibility:hidden;`绑定的事件不会触发。
   4. `opacity:0;`的元素绑定的事件还是会触发事件。
   
   潜伏题：
    jQuer是如何实现获取一个元素的正常宽高的。