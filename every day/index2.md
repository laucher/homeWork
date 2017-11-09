###2017-09-18

###实现一个throttle函数,throttle(function, wait, [options]),创建并返回一个像节流阀一样的函数，当重复调用函数的时候，至少每隔 wait毫秒调用一次该函数。对于想控制一些触发频率较高的事件有帮助。

ex：

```
//默认情况下，throttle将在你调用的第一时间尽快执行这个function，
//并且，如果你在wait周期内调用任意次数的函数，都将尽快的被覆盖。
//如果你想禁用第一次首先执行的话，传递{leading: false}，
//还有如果你想禁用最后一次执行的话，传递{trailing: false}。

var throttled = throttle(updatePosition, 100);
$(window).scroll(throttled);

//效果是随着scroll事件的触发，每过100毫秒才执行一次,updatePosition函数。

```

answer:

```
        function now(){
             return new Date().getTime();
        }
       
        
        function throttle(func, wait, options) {
            var context, args, result;
            var timeout = null;
            var previous = 0;
            if (!options) options = {};
            var later = function() {
                previous = options.leading === false ? 0 : now();
                timeout = null;
                result = func.apply(context, args);
                if (!timeout) context = args = null;
            };
            return function() {
                var now = now();
                if (!previous && options.leading === false) previous = now;
                var remaining = wait - (now - previous);
                context = this;
                args = arguments;
                if (remaining <= 0 || remaining > wait) {
                    if (timeout) {
                        clearTimeout(timeout);
                        timeout = null;
                    }
                    previous = now;
                    result = func.apply(context, args);
                    if (!timeout) context = args = null;
                } else if (!timeout && options.trailing !== false) {
                    timeout = setTimeout(later, remaining);
                }
                return result;
            };
        };


```

####link：
[jsbin链接](http://js.jirengu.com/foceyugifu/2/edit?html,js,output)