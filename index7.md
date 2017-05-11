### class 和 id 的使用场景?

   1. class 重在样式的复用，重普遍性。
   2. id重在划分样式区域，可以作为样式表中的命名空间来管理样式。
   3. id也可以指定某一个特殊元素的样式，重特殊性。
   
   注意：在html中声明多个一样的ID的元素，在css中该ID的样式，这些元素则都会生效。而在javascript中用DOM选择器只会选到第一个元素。
   

### CSS选择器常见的有几种?

   1. 基础选择器
   
   - 通用元素选择器
   - id选择器
   - 类选择器
   - 标签选择器
   
   2. 组合选择器
   
   - E,F 多元素选择器，用,分隔，同时匹配元素E或元素F
   - E F 后代选择器，用空格分隔，匹配E元素所有的后代元素F
   - E>F 子元素选择器，用>分隔，匹配E元素的所有直接子元素
   - E~F 普通相邻选择器（弟弟选择器），匹配E元素之后的同级元素F（无论直接相邻与否）
   - .class1.class2	id和class选择器和选择器连写的时候中间没有分隔符，. 和 # 本身充当分隔符的元素
   - element#id	 id和class选择器和选择器连写的时候中间没有分隔符，. 和 # 本身充当分隔符的元素
    
   3. 属性选择器
   
   - E[attr] 匹配所有具有属性attr的元素，div[id]就能取到所有有id属性的div
   - E[attr = value]	匹配属性attr值为value的元素，div[id=test],匹配id=test的div
   - E[attr ~= value]	匹配所有属性attr具有多个空格分隔、其中一个值等于value的元素
   - E[attr ^= value]	匹配属性attr的值以value开头的元素
   - E[attr $= value]	 匹配属性attr的值以value结尾的元素
   - E[attr *= value]	匹配属性attr的值包含value的元素
     
   4. 伪类选择器:
   
   - E:link 匹配所有未被点击的链接
   - E:visited	匹配所有已被点击的链接
   - E:active 匹配鼠标已经其上按下、还没有释放的E元素
   - E:hover	匹配鼠标悬停其上的E元素
   - E:focus	匹配获得当前焦点的E元素
   - E:nth-child(n) 匹配其父元素的第n个子元素，第一个编号为1
   - E:nth-last-child(n)	匹配其父元素的倒数第n个子元素，第一个编号为1
   - E:nth-of-type(n)	与:nth-child()作用类似，但是仅匹配使用同种标签的元素
   - E:nth-last-of-type(n)	与:nth-last-child() 作用类似，但是仅匹配使用同种标签的元素
     
   5.伪元素选择器
   
   - E::first-line	匹配E元素内容的第一行
   - E::first-letter	匹配E元素内容的第一个字母
   - E::before	在E元素之前插入生成的内容
   - E::after	在E元素之后插入生成的内容
    
### 选择器的优先级是怎样的?对于复杂场景如何计算优先级？

  css样式的简单权重级别由高到低排列：
   
   1. 在属性后面使用!important会覆盖页面内任何位置定义的元素样式。
   2. 作为style属性写在元素标签上的内联样式
   3. id 选择器
   4. 类选择器、伪类选择器、属性选择器
   7. 标签选择器、伪元素选择器
   8. 通配符选择器
   9. 浏览器自定义

  复杂场景下计算优先级：
  
   复杂场景下将选择器分为四个级别通过各级别的出现次数决定。
   四个级别分别为：行内选择符、ID选择符、类别选择符、元素选择符。
   优先级的算法：
   - 每个规则对应一个初始"四位数"：0、0、0、0
   - 若是 行内选择符，则加1、0、0、0
   - 若是 ID选择符，则加0、1、0、0
   - 若是 类选择符/属性选择符/伪类选择符，则分别加0、0、1、0
   - 若是 元素选择符/伪元素选择符，则分别加0、0、0、1

   算法：将每条规则中，选择符对应的数相加后得到的“四位数”，从左到右进行比较，大的优先级更高。
   优先级相同时，采用就近原则，即最后出现的样式。

### a:link, a:hover, a:active, a:visited 的顺序是怎样的？ 为什么？
   
   1. 样式声明顺序a:link;a:visited;a:hover;a:active.
   2. 
      - :link代表为访问链接的样式，所以只要你是超链接，且未被访问过，则链接都会按照你设定的样式显示，所以它的位置顺序无所谓。
      - :visited代表链接访问后的样式，则链接一旦被访问，则之后它的样式就会是你所设置的visited样式
      - :active 选择器用于选择活动链接。当您在一个链接上点击时，它就会成为活动的（激活的）。
      - :hover 代表的是你光标经过某一元素时的样式，如果将此样式放在:active之后，则当链接激活时，显示:active样式，当光标经过此链接时，会显示hover的样式，因为hover排在后，会覆盖active样式。如果:hover排在前，:active排在后，则当光标激活时显示:active的样式，但当光标经过链接时，样式并未显示:hover的样式，而是:active的样式，因为应用的active样式在hover之后，覆盖了前面的样式。
   3. 同理我们可以理清:link,:visited,:focus,:hover,:active的顺序，即为:link,:visited,:focus,:hover,:active。
    
### 以下选择器分别是什么意思?
```
   #header{
   } /* id为header的css样式 */
   .header{
   }/* class为header的css样式 */
   .header .logo{
   }/* class为header的元素后代中所有class为logo的元素的css样式 */
   .header.mobile{
   }/* class包含header和mobile的元素的css样式 */
   .header p, .header h3{
   }/* class为header的元素后代中p元素和h3元素的css样式 */
   #header .nav>li{
   }/* id为header元素后代中有class为nav的元素的直接子元素li的css样式 */
   #header a:hover{
   }/* id为header元素的后代中a元素的状态为鼠标悬停其上的css样式 */
   #header .logo~p{
   }/* id为header元素的所有后代元素中，class为logo的元素之后的所有同级元素p的css样式 */
   #header input[type="text"]{
   }/* id为header元素的所有后代元素中，所有type="text"的input标签的css样式 */
```
### 列出你知道的伪类选择器
    
   - E:link
    匹配所有未被点击的链接E
   - E:hover
    匹配所有鼠标悬停其上的元素E
   - E:active
    匹配所有鼠标已在其上按着，还未释放的元素E
   - E:visited
    匹配所有已被点击的链接E
   - E:focus
    匹配所有获得当前焦点的元素E
   - E:lang(c)
    匹配lang属性为c的E元素
   - E:enabled
    匹配表单可用的E元素
   - E:disabled
    匹配表单被禁用的E元素
   - E: checkbox
    匹配表单中被选中的radio或checkbox元素
   - E:selection
    匹配用户当前选中的元素
   - E:root
    匹配文档的根元素，对于html文档，就是html元素
   - E:first-child
    匹配作为长子（第一个子女）的元素E
   - E:last-child
    匹配作为最后一个子代元素的元素E
   - E:nth-child(n)
    匹配其父元素的第n个子元素，第一个n为1
   - E:nth-last-child(n)
    匹配其父元素的倒数第n个子元素，倒数第一个n为1
   - E:nth-of-type(n)
    匹配其父元素下同种标签的第n个子元素
   - E:nth-of-last-type(n)
    匹配其父元素下同种标签的倒数第n个子元素
    
### div:first-child、div:first-of-type、div :first-child和div :first-of-type的作用和区别 （注意空格的作用）
   - div:first-child  匹配父元素下，作为第一个子元素的div元素
   - div:first-of-type  匹配父元素的子元素中，第一个div元素
   - div :first-child 匹配所有div元素内所有元素中属于其父元素的首个子元素
   - div :first-of-type 匹配所有div元素内所有元素中属于其父元素的首个类型的子元素
### 运行如下代码，解析下输出样式的原因。
   ```
    <style>
    .item1:first-child{
      color: red;
    }
    .item1:first-of-type{
      background: blue;
    }
    </style>
    <div class="ct">
       <p class="item1">aa</p>
       <h3 class="item1">bb</h3>
       <h3 class="item1">ccc</h3>
    </div>
     
   ```
   - aa字体为红色： .item1:first-child 匹配元素class包含item1的第一个子元素 aa，所以为颜色变为红色
   - aa bb的背景色为蓝色： .item1:first-of-type 匹配的是class包含item1其父元素下相同类型子元素中的第一个，所以第一个p 第一个h3变蓝
     
