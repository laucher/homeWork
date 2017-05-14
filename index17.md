### 题目1： 如何全局安装一个 node 应用?
`npm install -g <module-name>`

### 题目2： package.json 有什么作用？
每个项目的根目录下面，一般都有一个 package.json 文件，定义了这个项目所需要的各种模块，以及项目的配置信息（比如名称、版本、许可证等元数据）。npm install 命令根据这个配置文件，自动下载所需的模块，也就是配置项目所需的运行和开发环境。

```
{
  "name": "test",  //名称
  "version": "0.0.1",  //版本
  "description": "This is my first node.js program.",  //描述
  "main": "index.js",  //入口
  "keywords": [  //关键字
                       "node.js",
                       "javascript"
  ],
  "scripts": {  //执行命令行
	  "start": "node index.js"
  },
  "author": "Mike",  //作者
  "license":"MIT",  //认证
  "dependencies": {  //生产环境依赖
	              "express": "latest"
  },
  "devDependencies": {  //开发环境依赖
		   "bower": "~1.2.8",
		   "grunt": "~0.4.1"
  }
}
```
### 题目3： npm install --save app 与 npm install --save-dev app有什么区别?
- --save 将产品运行时（或生产环境）需要的依赖模块添加到 package.json 的 dependencies 中，
在发布后还需要继续使用，否则就运行不了。
- --save-dev 将产品的开发环境需要的依赖模块添加到 package.json 的 devDependencies 中，
只在开发时才用到，发布后用不到它。

### 题目4： node_modules的查找路径是怎样的?
从当前文件目录开始查找node_modules目录；然后依次进入父目录，查找父目录下的node_modules目录；依次迭代，直到根目录下的node_modules目录。
比如某个模块的绝对路径是/home/user/foo.js，在该模块中使用require('bar')方式加载模块时，node将在下面的位置进行搜索：

/home/user/node_modules/bar

/home/node_modules/bar

/node_modules/bar

### 题目6： webpack是什么？和其他同类型工具比有什么优势？
webpack是一款模块加载器兼打包工具，它能把各种资源JS/CSS/图片等都作为模块来使用和处理。
优势如下：

- webpack 是以 commonJS 的形式来书写脚本，但对 AMD/CMD 的支持也很全面，方便旧项目进行代码迁移。
- webpack可以将代码拆分成多个区块，每个区块包含一个或多个模块，它们可以按需异步加载，极大地减少了页面初次加载时间。
- webpack 本身只能处理原生的 JS 模块，但是 loader 转换器可以将各种类型的资源转换成 JS 模块。这样，任何资源都可以成为 webpack 可以处理的模块。
- webpack 有一个智能解析器，几乎可以处理任何第三方库，无论它们的模块形式是 CommonJS、 AMD 还是普通的 JS 文件。
- webpack 还有一个功能丰富的插件系统。大多数内容功能都是基于这个插件系统运行的，还可以开发和使用开源的 webpack 插件，来满足各式各样的需求。
- webpack使用异步 I/O 和多级缓存提高运行效率，使得它能够快速增量编译。

### 题目7：npm script是什么？如何使用？
package.json 文件有一个 scripts 字段，可以用于指定脚本命令，供 npm 直接调用。
npm 内置了两个简写的命令：npm test 和 npm start，其它命令要写成 npm run xxx 形式。

#### 题目9：gulp是什么？使用 gulp 实现图片压缩、CSS 压缩合并、JS 压缩合并
gulp 是一个自动化构建工具，开发者可以使用它在项目开发过程中自动执行常见任务。
```
//安装插件
npm install gulp-imagemin --save-dev //图片压缩
npm install gulp-cssnano --save-dev //css压缩
npm install uglify --save-dev //js压缩
npm install gulp-jshint --save-dev //js规范检查
npm install gulp-concat --save-dev //文件合并
npm install gulp-rename --save-dev //重命名

//gulpfile.js
//引入插件
var gulp = require('gulp'),
    cssnano = require('gulp-cssnano'),
    concat = require('gulp-concat'),
    jshint = require('gulp-jshint'),
    uglify = require('gulp-uglify'),
    imagemin = require('gulp-imagemin'),
    rename = require('gulp-rename'),
 
  //css合并压缩
  gulp.task('build:css', function() {
      gulp.src('./src/css/*.css')
        .pipe(concat('merge.css'))
        .pipe(rename({
            suffix: '.min'
        }))
        .pipe(cssnano())
        .pipe(gulp.dest('dist/css/'));
  })

  //js合并压缩
   gulp.task('build:js', function() {
      gulp.src('src/js/*.js')
        .pipe(jshint())
        .pipe(jshint.reporter('default'))
        .pipe(concat('merge.js'))
        .pipe(rename({
          suffix: '.min'
        }))
        .pipe(uglify())
        .pipe(gulp.dest('dist/js/'));
  })

  //图片压缩
  gulp.task('build:image', function() {
      gulp.src('src/imgs/*')
        .pipe(imagemin())
        .pipe(gulp.dest('dist/imgs/'));
  })

gulp.task('build', ['build:css', 'build:js', 'build:image']);

//命令行
gulp build
```