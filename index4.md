### HTML、XML、XHTML 有什么区别
1. HTML

    HTML(Hyper Text Mark-up Language)即超文本标记语言或超文本链接标示语言，是目前网络上应用最为广泛的语言，也是构成网页文档的主要语言。它告诉浏览器如何显示内容。
    
    #### 主要特点 ####
    1. 简易性：超级文本标记语言版本升级采用超集方式，从而更加灵活方便。
    2. 可扩展性：超级文本标记语言的广泛应用带来了加强功能，增加标识符等要求，超级文本标记语言采取子类元素的方式，为系统扩展带来保证。
    3. 平台无关性：虽然个人计算机大行其道，但使用MAC等其他机器的大有人在，超级文本标记语言可以使用在广泛的平台上，这也是万维网（WWW）盛行的另一个原因。
    4. 通用性：另外，HTML是网络的通用语言,一种简单、通用的全置标记语言。它允许网页制作人建立文本与图片相结合的复杂页面，这些页面可以被网上任何其他人浏览到，无论使用的是什么类型的电脑或浏览器。
    
2. XML

    XML即ExtentsibleMarkupLanguage(可扩展标记语言)，是用于网络上数据交换的语言。它没有标签集，也没有语法规则，但是它有句法规则。
    
    #### 与HTML的主要区别 ####
    1. 目标 :HTML的设计目标是显示数据并集中于数据外观，而XML的设计目标是描述数据并集中于数据的内容，它的显示形式靠CSS或XSL帮完成。
    
    2. 语法：HTML的标记不是所有的都需要成对出现，XML则要求所有的标记必须成对出现；HTML标记不区分大小写，XML则大小敏感，即区分大小写。
    
    3. 更新：XML允许粒度更新，不必在XML文档每次有局部改变时都发送整个文档的内容，只有改变的元素才必须从服务器发送到客户机，而HTML却不支持这样的功能。
    
    4. 可读性：HTML侧重于网页数据表现形式的定义和描述，欠缺对文档数据含义的确切描述，不能适应对于日益增多的各类信息进行传递与存档的需求。例如```<H2>Apple</H2>```,在浏览器中显示的Apple，人们并不知道它具体是水果还是一个手机，HTML并不能解释数据Apple的含义；而XML不会给大家这个错觉如果描述的是水果中的苹果的话它会很清楚的这样表示```<水果>Apple</水果>```。所以说HTML的可读性相对较差。
    
    5. 还有一点就是XML标记由架构或文档的作者定义，并且是无限制的。HTML 标记则是预定义的;HTML 作者只能使用当前 HTML 标准所支持的标记。
3. XHTML

    意义:指扩展超文本标签语言（EXtensible HyperText Markup Language）,目标是取代HTML.
    
    #### 与HTML的主要区别 ####
    1. XHTML是当前HTML版的继承者,由于HTML的语法较为松散,对于许多其他设备的要求较高,因此就出现了由DTD定义规则,语法要求更加严格的XHTML。
    2. XHTML与HTML的最大的变化在于所有标签必须闭合。
    3. XHTML中所有的标签必须小写。
    4. XHTML 元素必须被正确地嵌套。
    5. XHTML 文档必须拥有根元素。
    
### 怎样理解 HTML 语义化

   含义:根据内容的结构化（内容语义化），选择合适的标签（代码语义化）便于开发者阅读和写出更优雅的代码的同时让浏览器的爬虫和机器很好地解析。
    
   优点:
   
   1. 为了在没有CSS的情况下，页面也能呈现出很好地内容结构、代码结构；
   2. 用户体验：例如title、alt用于解释名词或解释图片信息、label标签的活用；
   3. 有利于SEO：和搜索引擎建立良好沟通，有助于爬虫抓取更多的有效信息：爬虫依赖于标签来确定上下文和各个关键字的权重；
   4. 方便其他设备解析（如屏幕阅读器、盲人阅读器、移动设备）以意义的方式来渲染网页；
   5. 便于团队开发和维护，语义化更具可读性，是下一步吧网页的重要动向，遵循W3C标准的团队都遵循这个标准，可以减少差异化。
    
### 怎样理解内容与样式分离的原则
    
   含义:对于内容、结构与表现相分离，最早是在软件开发架构理论中提出来的,XHTML的标签只用来定义文档的结构，所有涉及表现的东西通通剥离出来，把它放到一个单独的文件里，这个单独的文件就是CSS。
    
   优点:
   
   1. 数据的多样显示。通过不同的样式表适应不同的设备，做到内容与设备无关
   2. 保持整个站点的视觉一致性变得非常简单，修改样式表就可以轻松改版;
   3. 由于结构清晰，数据的集成、更新和处理更加方便灵活；
   4. 更有意义的搜索。
    
    
### 有哪些常见的meta标签 ###

   ``< meta > `` 元素
    
   #### 概要 ####
    
   标签提供关于HTML文档的元数据。元数据不会显示在页面上，但是对于机器是可读的。它可用于浏览器（如何显示内容或重新加载页面），搜索引擎（关键词），或其他 web 服务。 —— [W3School](http://www.w3school.com.cn/)
    
   **必要属性**
    
   属性 | 值 | 描述
   -----|-----|-----
   content | some text | 定义与http-equiv或name属性相关的元信息
    
   **可选属性**
    
   属性 | 值 | 描述
   -----|-----|-----
   http-equiv | content-type / expire / refresh / set-cookie |把content属性关联到HTTP头部。
   name | author / description / keywords / generator / revised / others |把 content 属性关联到一个名称。
   content | some text | 定义用于翻译 content 属性值的格式。
    
   #### SEO优化
    
   [参考文档](http://msdn.microsoft.com/zh-cn/library/ff724016)
   
   - **页面关键词**，每个网页应具有描述该网页内容的一组唯一的关键字。使用人们可能会搜索，并准确描述网页上所提供信息的描述性和代表性关键字及短语。标记内容太短，则搜索引擎可能不会认为这些内容相关。另外标记不应超过 874 个字符。
   
       ```<meta name="keywords" content="your tags" />```
    
   - **页面描述**，每个网页都应有一个不超过 150 个字符且能准确反映网页内容的描述标签。
    
        ```<meta name="description" content="150 words" />```
    
   - **搜索引擎索引方式**，``robotterms``是一组使用逗号(,)分割的值，通常有如下几种取值：``none``，``noindex``，``nofollow``，``all``，``index``和``follow``。确保正确使用``nofollow``和``noindex``属性值。
    
   - ```<meta name="robots" content="index,follow" />```
   ``
    <!-- 
        all：文件将被检索，且页面上的链接可以被查询；
        none：文件将不被检索，且页面上的链接不可以被查询；
        index：文件将被检索； follow：页面上的链接可以被查询；
        noindex：文件将不被检索； nofollow：页面上的链接不可以被查询。
     -->
     ``
    
    
   - **页面重定向和刷新**：``content``内的数字代表时间（秒），既多少时间后刷新。如果加``url``,则会重定向到指定网页（搜索引擎能够自动检测，也很容易被引擎视作误导而受到惩罚）。
      ```<meta http-equiv="refresh" content="0;url=" />```
    
   - **其他**
      ```
      <meta name="author" content="author name" /> <!-- 定义网页作者 -->
      <meta name="google" content="index,follow" />
      <meta name="googlebot" content="index,follow" />
      <meta name="verify" content="index,follow" />
      ```
    
   #### 移动设备
   - **viewport**：能优化移动浏览器的显示。如果不是响应式网站，不要使用``initial-scal``e或者禁用缩放。大部分4.7-5寸设备的``viewport``宽设为``360px``；``5.5``寸设备设为``400px``；``iphone6``设为``375px``；``ipone6 plus``设为``414px``。
    
     ```<meta name="viewport" content="width=device-width, initial-scale=1.0,maximum-scale=1.0, user-scalable=no"/><!-- `width=device-width` 会导致 iPhone 5 添加到主屏后以 WebApp 全屏模式打开页面时出现黑边 -->```
    
     `` width``：宽度（数值 / device-width）（范围从200 到10,000，默认为980 像素）
     
     `` height``：高度（数值 / device-height）（范围从223 到10,000）
     
     `` initial-scale``：初始的缩放比例 （范围从>0 到10）
     
     ``minimum-scale``：允许用户缩放到的最小比例
     
     `` maximum-scale``：允许用户缩放到的最大比例
     
     ``user-scalable``：用户是否可以手动缩 (no,yes)
     
     ``minimal-ui``：可以在页面加载时最小化上下状态栏。（已弃用）
    
   **注意，很多人使用initial-scale=1到非响应式网站上，这会让网站以100%宽度渲染，用户需要手动移动页面或者缩放。如果和initial-scale=1同时使用user-scalable=no或maximum-scale=1，则用户将不能放大/缩小网页来看到全部的内容。**
    
   - **WebApp全屏模式**：伪装app，离线应用。
    
   ```<meta name="apple-mobile-web-app-capable" content="yes" /><!-- 启用 WebApp 全屏模式 -->```
    
   - **隐藏状态栏/设置状态栏颜色**：只有在开启WebApp全屏模式时才生效。``content``的值为default | black | black-translucent 。
    
    ```<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent" />```
    
   - **添加到主屏后的标题**
   
   ```<meta name="apple-mobile-web-app-title" content="标题">```
    
   ![](https://segmentfault.com/img/bVkgzS)![](https://segmentfault.com/img/bVkgzU)![](https://segmentfault.com/img/bVkgzV)
    
   - **忽略数字自动识别为电话号码**
    
   ```<meta content="telephone=no" name="format-detection" /> ```
    
   - **忽略识别邮箱**
    
   ``<meta content="email=no" name="format-detection" />``
    
   - **添加智能 App 广告条 Smart App Banner**：告诉浏览器这个网站对应的app，并在页面上显示下载banner(如下图)。[参考文档](https://developer.apple.com/library/ios/documentation/AppleApplications/Reference/SafariWebContent/PromotingAppswithAppBanners/PromotingAppswithAppBanners.html)
    
   ``<meta name="apple-itunes-app" content="app-id=myAppStoreID, affiliate-data=myAffiliateData, app-argument=myURL">`` 
    
   ![](https://segmentfault.com/img/bVkgzR)
    
    
   - **其他** [参考文档](http://fex.baidu.com/blog/2014/10/html-head-tags/?qq-pf-to=pcqq.c2c)
    
   ```
   <!-- 针对手持设备优化，主要是针对一些老的不识别viewport的浏览器，比如黑莓 -->
   <meta name="HandheldFriendly" content="true">
   <!-- 微软的老式浏览器 -->
    meta name="MobileOptimized" content="320">
   <!-- uc强制竖屏 -->
   <meta name="screen-orientation" content="portrait">
   <!-- QQ强制竖屏 -->
   <meta name="x5-orientation" content="portrait">
   <!-- UC强制全屏 -->
   <meta name="full-screen" content="yes">
   <!-- QQ强制全屏 -->
   <meta name="x5-fullscreen" content="true">
   <!-- UC应用模式 -->
   <meta name="browsermode" content="application">
   <!-- QQ应用模式 -->
   <meta name="x5-page-mode" content="app">
   <!-- windows phone 点击无高光 -->
   <meta name="msapplication-tap-highlight" content="no">
   ```
    
   #### 网页相关
    
   - **申明编码**
    
   ``<meta charset='utf-8' />``
    
   - **优先使用 IE 最新版本和 Chrome**
   ```
   <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1" />
   <!-- 关于X-UA-Compatible -->
   <meta http-equiv="X-UA-Compatible" content="IE=6" ><!-- 使用IE6 -->
   <meta http-equiv="X-UA-Compatible" content="IE=7" ><!-- 使用IE7 -->
   <meta http-equiv="X-UA-Compatible" content="IE=8" ><!-- 使用IE8 -->
   ```
   - **浏览器内核控制**：国内浏览器很多都是双内核（``webkit``和``Trident``），``webkit``内核高速浏览，IE内核兼容网页和旧版网站。而添加``meta``标签的网站可以控制浏览器选择何种内核渲染。[参考文档](http://se.360.cn/v6/help/meta.html)
    
     ```<meta name="renderer" content="webkit|ie-comp|ie-stand">```
    
     国内双核浏览器默认内核模式如下：1. 搜狗高速浏览器、QQ浏览器：IE内核（兼容模式）2. 360极速浏览器、遨游浏览器：Webkit内核（极速模式）
    
   - **禁止浏览器从本地计算机的缓存中访问页面内容**：这样设定，访问者将无法脱机浏览。
    
      ```<meta http-equiv="Pragma" content="no-cache">```
    
   - **Windows 8**
    
    ```
    <meta name="msapplication-TileColor" content="#000"/> <!-- Windows 8 磁贴颜色 -->
    <meta name="msapplication-TileImage" content="icon.png"/> <!-- Windows 8 磁贴图标 -->
    ```
    
   - **站点适配**：主要用于PC-手机页的对应关系。
    
      ```<meta name="mobile-agent"content="format=[wml|xhtml|html5]; url=url">
      <!--[wml|xhtml|html5]根据手机页的协议语言，选择其中一种；url="url" 后者代表当前PC页所对应的手机页URL，两者必须是一一对应关系。 -->```
    
   - **转码申明**：用百度打开网页可能会对其进行转码（比如贴广告），避免转码可添加如下meta
    
      ```<meta http-equiv="Cache-Control" content="no-siteapp" />```
    
    
    
### 文档声明的作用?严格模式和混杂模式指什么?<!doctype html> 的作用?
    
   1. 声明叫做文件类型定义（DTD），声明的作用为了告诉浏览器该文件的类型。让浏览器解析器知道应该用哪个规范来解析文档。声明必须在 HTML 文档的第一行，这并不是一个 HTML 标签。
   2.  严格模式：又称标准模式，是指浏览器按照 W3C 标准解析代码。
       混杂模式：又称怪异模式或兼容模式，是指浏览器用自己的方式解析代码。
   3. <!doctype html>的作用就是让浏览器进入标准模式，使用最新的 HTML5标准来解析渲染页面；如果不写，浏览器就会进入混杂模式，而这是我们要避免的
   
   4. 常用的 DOCTYPE 声明
      - HTML 5
      
        ```<!DOCTYPE html>```
       
      - HTML 4.01 Strict
      
        该 DTD 包含所有 HTML 元素和属性，但不包括展示性的和弃用的元素（比如 font）。不允许框架集（Framesets）
        
      - HTML 4.01 Transitional
      
        该 DTD 包含所有 HTML 元素和属性，包括展示性的和弃用的元素（比如 font）。不允许框架集（Framesets）。
       
      - HTML 4.01 Frameset
      
        该 DTD 等同于 HTML 4.01 Transitional，但允许框架集内容。
       
      - XHTML 1.0 Strict
      
        该 DTD 包含所有 HTML 元素和属性，但不包括展示性的和弃用的元素（比如 font）。不允许框架集（Framesets）。必须以格式正确的 XML 来编写标记。
       
      - XHTML 1.0 Transitional
      
        该 DTD 包含所有 HTML 元素和属性，包括展示性的和弃用的元素（比如 font）。不允许框架集（Framesets）。必须以格式正确的 XML 来编写标记。
       
      - XHTML 1.0 Frameset
      
        该 DTD 等同于 XHTML 1.0 Transitional，但允许框架集内容。
       
      - XHTML 1.1
      
        该 DTD 等同于 XHTML 1.0 Strict，但允许添加模型（例如提供对东亚语系的 ruby 支持）。

### 浏览器乱码的原因是什么？如何解决
    
   1. 文件保存的格式与meta中指定的解析格式不一样
   2. 没有指定meta的charset
   
   解决办法：指定正确的charset值
   
   常见编码集：UTF-8 UTF-16 GBK Unicode
   
   
   注意:
   
        1. 只有非英文和阿拉伯数字以外的字符才会出现乱码。
        2. 不同编码集中字符占用的byte值不一样。
  
    
### 常见的浏览器有哪些，什么内核

    这边的内核专指管理浏览器渲染行为的内核
   - Trident：IE浏览器使用的内核,该内核程序在1997年的IE4中首次被采用，是微软在Mosaic代码的基础之上修改而来的，并沿用到目前的IE8。Trident实际上是一款开放的内核，其接口内核设计的相当成熟，因此才有许多采用IE内核而非IE的浏览器涌现（如 Maxthon、The World 、TT、GreenBrowser、AvantBrowser等）。此外，为了方便也有很多人直接简称其为IE内核（当然也不排除有部分人是因为不知道内核名称而只好如此说）。
   - Gecko：Netscape6开始采用的内核，后来的Mozilla FireFox也采用了该内核，Gecko的特点是代码完全公开，因此，其可开发程度很高，全世界的程序员都可以为其编写代码，增加功能。因为这是个开源内核，因此受到许多人的青睐，Gecko内核的浏览器也很多，这也是Geckos内核虽然年轻但市场占有率能够迅速提高的重要原因。
   - Presto： 目前Opera采用的内核，该内核在2003年的Opera7中首次被使用，该款引擎的特点就是渲染速度的优化达到了极致，也是目前公认网页浏览速度最快的浏览器内核，然而代价是牺牲了网页的兼容性。
   - Webkit：苹果公司自己的内核，也是苹果的Safari浏览器使用的内核。 Webkit引擎包含WebCore排版引擎及JavaScriptCore解析引擎，均是从KDE的KHTML及KJS引擎衍生而来，它们都是自由软件，在GPL条约下授权，同时支持BSD系统的开发。所以Webkit也是自由软件，同时开放源代码。在安全方面不受IE、Firefox的制约，所以Safari浏览器在国内还是很安全的。
   - KHTML：KHTML，是HTML网页排版引擎之一，由KDE所开发。KDE系统自KDE2版起，在档案及网页浏览器使用了KHTML引擎。该引擎以C++编程语言所写，并以LGPL授权，支援大多数网页浏览标准。由于微软的Internet Explorer的占有率相当高，不少以FrontPage制作的网页均包含只有IE才能读取的非标准语法，为了使KHTML引擎可呈现的网页达到最多，部分IE专属的语法也一并支援。KHTML拥有速度快捷的优点，但对错误语法的容忍度则比Mozilla产品所使用的Gecko引擎小。
    