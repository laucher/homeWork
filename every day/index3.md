###2017-09-18

###实现一个debounce函数,debounce(function, wait, [immed返回 function 函数的防反跳版本, 将延迟函数的执行(真正的执行)在函数最后一次调用时刻的 wait 毫秒之后. 对于必须在一些输入（多是一些用户操作）停止到达之后执行的行为有帮助。 例如: 渲染一个Markdown格式的评论预览, 当窗口停止改变大小之后重新计算布局, 等等.iate])

ex：

```
//传参 immediate 为 true， debounce会在 wait 时间间隔的开始调用这个函数 。并且在 waite 的时间之内，不会再次调用。
var lazyLayout = _.debounce(calculateLayout, 300);
$(window).resize(lazyLayout);

```

answer：

```
        function now(){
            return new Date().getTime();
        }
        
        function debounce(func, wait, immediate) {
            var timeout, args, context, timestamp, result;
    
            var later = function() {
                var last = now() - timestamp;
    
                if (last < wait && last >= 0) {
                    timeout = setTimeout(later, wait - last);
                } else {
                    timeout = null;
                    if (!immediate) {
                        result = func.apply(context, args);
                        if (!timeout) context = args = null;
                    }
                }
            };
    
            return function() {
                context = this;
                args = arguments;
                timestamp = now();
                var callNow = immediate && !timeout;
                if (!timeout) timeout = setTimeout(later, wait);
                if (callNow) {
                    result = func.apply(context, args);
                    context = args = null;
                }
    
                return result;
            };
        };

```

####link：
[jsbin链接](http://js.jirengu.com/delofakapi/2/edit?html,js,output)