###2017-09-17

### 实现一个sortBy(list, iteratee),返回一个排序后的list拷贝副本。如果传递iteratee参数，iteratee将作为list中每个值的排序依据。迭代器也可以是字符串的属性的名称进行排序的(比如 length)。

####ex：

```
    groupBy([1.3, 2.1, 2.4], function(num){ return Math.floor(num); });
    => {1: [1.3], 2: [2.1, 2.4]}
    
    groupBy(['one', 'two', 'three'], 'length');
    => {3: ["one", "two"], 5: ["three"]}
    
```


#####answer：

```
   
   function pluck(obj, key){    
        return obj.map(function(value,index,obj){
               return value[key];
        });
   }    
    
    function sortBy(obj, iteratee) {
        return pluck(obj.map(obj, function(value, index, list) {
            return {
                value: value,
                index: index,
                criteria: iteratee(value, index, list)
            };
        }).sort(function(left, right) {
            var a = left.criteria;
            var b = right.criteria;
            if (a !== b) {
                if (a > b || a === void 0) return 1;
                if (a < b || b === void 0) return -1;
            }
            return left.index - right.index;
        }), 'value');
    };
    
```

####link：
[jsbin链接](http://js.jirengu.com/teluxuviso/2/edit?html,js,output)
