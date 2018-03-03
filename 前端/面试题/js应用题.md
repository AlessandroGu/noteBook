1. 千分位
```js
    number.toString().replace(/(\d)(?=(?:\d{3})+$)/g, '$1,');
```
2. 将‘abcd’转换成‘a-b-c-d’
```js
    ‘abcd’.split('').join('-');
```
3. 排序（冒泡和快排）
```js
    var arr = [...];
    // 冒泡
    for(var i = 0; i < arr.length; i ++){
        for(var j = 0; i < arr.length-i-1; j ++){
            if(arr[j] < arr[j+1]){
                var temp = arr[j];
                arr[j] = arr[j+1];
                arr[j+1] = temp;
            }
        }
    }

    // 快排
    function quickSort(arr) {
        if(arr.length <= 1) return arr;
        var halfIndex = arr.length/2;
        var pivot = arr.splice(halfIndex, 1)[0];    // 中间的基准
        var left = [],
            right = [];
        // 将比基准小的放在left，大的放在right
        for(var i = 0; i < arr.length; i++){
            if(arr[i] <= pivot){
                left.push(arr[i]);
            }else{
                right.push(arr[i]);
            }
        }
        // 递归
        return quickSort(left).concat([pivot], quickSort(right));
    }
```
4. 正则匹配邮箱
```js
    var reg = /^[A-Za-z0-9_-]+@[A-Za-z0-9_-]+(\.[A-Za-z0-9_-]+)+$/g
```