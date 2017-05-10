### form表单有什么作用？有哪些常用的input 标签，分别有什么作用？
    
   1. HTML `<form>` 元素 表示了文档中的一个区域，这个区域包含有交互控制元件，用来向web服务器提交信息，拥有以下属性。
        1. action 一个处理这个form信息的程序所在的URL。
        2. autocomplete 用于指示 input 元素是否能够拥有一个默认值，这个默认值是由浏览器自动补全的。
        3. enctype 当 method 属性值为 post 时, enctype 是提交form给服务器的内容的 MIME 类型，可能的取值有三个，application/x-www-form-urlencoded: 如果属性未指定时的默认值。multipart/form-data: 这个值用于一个 type 属性设置为 "file" 的 `<input>` 元素。text/plain (HTML5)。
        4. method 浏览器使用这种 HTTP 方式来提交 form。 可能的值有get和post。
        5. target 一个名字或者说关键字，用来指示在提交表单之后，在哪里显示收到的回复.
   2.  常见的Input标签主要由type属性控制。
        - type: 控件类型的显示。如果这个属性没有指定，默认的类型是 text。
        - type可用的值包括：
            - button：无缺省行为按钮。
            - checkbox： 复选框。必须使用 value 属性定义此控件被提交时的值。使用 checked 属性指示控件是否被选择。也可以使用 indeterminate 指示复选框在一种不确定状态（大多数平台上，显示为一条穿过复选框的水平线）。
            - color：HTML5 用于指定颜色的控件。
            - date：HTML5 用于输入日期的控件（年，月，日，不包括时间）。
            - datetime：HTML5 基于 UTC 时区的日期时间输入控件（时，分，秒及几分之一秒）。
            - datetime-local：HTML5 用于输入日期时间控件，不包含时区。
            - email：HTML5 用于编辑 e-mail 的字段。 合适的时候可以使用 :valid 和 :invalid CSS 伪类。
            - file：此控件可以让用户选择文件。使用 accept 属性可以定义控件可以选择的文件类型。
            - hidden：不显示在页面上的控件，但它的值会被提交到服务器。
            - image：图片提交按钮。必须使用 src 属性定义图片的来源及使用 alt 定义替代文本。还可以使用 height 和 width 属性以像素为单位定义图片的大小。
            - month：HTML5 用于输入年月的控件，不带时区。
            - number: HTML5 用于输入浮点数的控件。
            - password：一个值被遮盖的单行文本字段。使用 maxlength 指定可以输入的值的最大长度 。
            - radio：单选按钮。必须使用 value 属性定义此控件被提交时的值。使用checked 必须指示控件是否缺省被选择。在同一个”单选按钮组“中，所有单选按钮的 name 属性使用同一个值； 一个单选按钮组中是，同一时间只有一个单选按钮可以被选择。
            - range：HTML5 用于输入不精确值控件。
            - reset：用于将表单所内容设置为缺省值的按钮。
            - search：HTML5用于输入搜索字符串的单行文本字段。换行会被从输入的值中自动移除。
            - submit：用于提交表单的按钮。
            - tel：HTML5 用于输入电话号码的控件；换行会被自动从输入的值中移除A,，but no other syntax is enforced。可以使用属性，比如 pattern 和 maxlength 来约束控件输入的值。恰当的时候，可以应用 :valid 和 :invalid CSS 伪类。
            - text：单行字段；换行会将自动从输入的值中移除。
            - time：HTML5 用于输入不含时区的时间控件。
            - url：HTML5 用于编辑URL的字段。 The user may enter a blank or invalid address. 换行会被自动从输入值中移队。可以使用如：pattern 和 maxlength 样的属性来约束输入的值。 恰当的时候使可以应用 :valid 和 :invalid CSS 伪类。
            - week：HTML5 用于输入一个由星期-年组成的日期，日期不包括时区。
            
   3. 表单中readonly和disabled属性的区别
        - 设置了readonly的input[text]在提交表单的时候还是会提交input上声明的数据。
        - 设置了disabled的则不会提交input上声明的数据。
   
   4. 表单提交文件的正确方式
      - 添加input[type=file]的input标签
      - 设置表单的method为post
      - 设置表单的enctype为multipart/form-data
      
   5. 如何无刷新提交表单
      - 在页面设置一个iframe，设置好它的name属性值，用css控制他是'消失'的。
      - 设置form的target属性为iframe的name属性即可。
      
   6. 默认情况下，form中的button按钮不声明type属性，则一律视为submit。
   
### post 和 get 方式的区别？

   - GET后退按钮/刷新无害，POST数据会被重新提交（浏览器应该告知用户数据会被重新提交）。
   - GET书签可收藏，POST为书签不可收藏。
   - GET能被缓存，POST不能缓存 。
   - GET编码类型application/x-www-form-url，POST编码类型application/x-www-form-urlencoded 或 multipart/form-data。为二进制数据使用多重编码。
   - GET历史参数保留在浏览器历史中。POST参数不会保存在浏览器历史中。
   - GET对数据长度有限制，当发送数据时，GET 方法向 URL 添加数据；URL 的长度是受限制的（URL 的最大长度是 2048 个字符）。POST无限制。
   - GET只允许 ASCII 字符。POST没有限制。也允许二进制数据。
   - 与 POST 相比，GET 的安全性较差，因为所发送的数据是 URL 的一部分。在发送密码或其他敏感信息时绝不要使用 GET ！POST 比 GET 更安全，因为参数不会被保存在浏览器历史或 web 服务器日志中。GET的数据在 URL 中对所有人都是可见的。POST的数据不会显示在 URL 中。
    
### 在input里，name 有什么作用？
    
   由于表单提交的数据一般都是以key:value的方式提交，所以input中的name属性主要用来标识提交的数据的key值，好让服务器处理程序分辨。
   
   例如：
   ```
       <input name=name value=adam>
       <input name=age value=18>
   ```
   
   则服务器在后台收到的数据格式可能是这样的：
   
   ```
    {
        name:adam,
        age:18
    }
   ```
### radio 如何 分组?

   拥有一样name属性的radio为一组
   
### placeholder 属性有什么作用?
    
   placeholder属性一般会在输入框有一个提示，该提示会在输入字段为空时显示，并会在字段获得焦点时消失。
   
   注意：
   
   1. placeholder 属性适用于以下的 ```<input>``` 类型：text, search, url, telephone, email 以及 password。
   2. placeholder为HTML5的新属性
    
### type=hidden隐藏域有什么作用? 举例说明
    
    
    

[CSRF 详解与攻防实战](http://www.tuicool.com/articles/Z3eYraY)