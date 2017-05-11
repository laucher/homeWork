### CSS的全称是什么?

   层叠样式表(英文全称：Cascading Style Sheets)是一种用来表现HTML（标准通用标记语言的一个应用）或XML（标准通用标记语言的一个子集）等文件样式的计算机语言。
   
### CSS有几种引入方式? link 和@import 有什么区别?

引入方式：

   1. 在 `<head>` 里面使用 `<link rel="stylesheet" href="xxx.css">` 引用外部文件
   2. 在 `<head>` 中的 `<style>` 标签里面写样式
   3. 在要使用样式的元素中写 `<p style="xxx:xxx;">`
   4. 在 `<style>` 里面写上 `@import url("http://xxx.css")`;

区别：

   1. link 是 HTML 标签除了 CSS 还能定义别的东西，而 @import 是纯 CSS
   2. link 和页面本体是会同时加载的，而 @import 得等到页面加载完成再加载
   3. @import 是 CSS 2 标准，在多年前可能会有兼容性问题
   4. 当使用 JavaScript 控制 DOM 去改变样式的时候，只能使用 link 标签，因为 @import 不是 DOM 可以控制的
### 以下这几种文件路径分别用在什么地方，代表什么意思?
1. ``` css/a.css ```
    在当前目录下css文件夹下的a.css文件
2. ``` /css/a.css ```
   选择当前目录下css文件夹中的a.css文件
3. ``` b.css ```
    当前目录中的b.css文件
4. ``` ../imgs/a.png ```
   选择上一级目录中的imgs文件夹下的a.png文件
5. ``` /Users/hunger/project/css/a.css ```
    一般是指在相对本地路径找到User文件夹下hunger文件夹下project文件夹下css文件夹下a.css文件
6. ``` /static/css/a.css ```
    一般情况下在当前项目的根目录下的static文件下的文件下的a.css文件
7. ``` http://cdn.jirengu.com/kejian1/8-1.png ```
    一般情况下是引用http://cdn.jirengu.com这个CDN服务下的kejian1文件下的8-1.png
### 如果我想在js.jirengu.com上展示一个图片，需要怎么操作?
    
   1. 一种是将图片上传到该网站的服务
   2. 第二种生成图片的链接，然后引用图片。
    
###  列出5条以上html和 css 的书写规范
    
   [Code Guide by @AlloyTeam](http://alloyteam.github.io/CodeGuide/)