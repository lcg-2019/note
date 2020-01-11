## 三大家族

### offset
- offsetElft和offsetTop: 是距离最近的有定位的父级元素的距离分别对应左边距和上边距(ps:从父亲的padding开始计算).
- offsetHeight和offsetWidth : 是自身的宽高加上padding和border的值.

- offsetParent :是最近的有定位属性的父级元素.

- offset.left和style.left的区别:
    1. style只能获取行内样式的值没有则获取不到.
    2. style.left可以设置值,offsetLeft则不可设置.
    3. style.left获得的带单位ofsetLeft没有单位
    4. . style.left 获取的值是小数点后一位(四舍五入)   offsetLeft 获取的是一个整数(四舍五入)


### scroll
- scrollLeft 和scrollTop:没有滚动条的情况下是0,有滚动条的情况下是被遮挡的部分的距离.
- scrollWidth 和 scrollHeight :
①内容没溢出情况下是==>内容宽高+上下paading+上下margin的值,宽
②内容溢出或隐藏的情况是 ==>盒子内容宽高加上左边的padding和margin.

- scrollTop 和 scollLeft :
    1. 有进度条的情况 是获取的被遮挡部分的距离.
    2. 没进度条的情况 是 0.

###### scrollTop的兼容代码 scrollLeft同(兼容ie)
```js

  function sct() {
            return document.documentElement.scrollTop || window.pageYOffset || document.body.scrollTop;
        }

        function scl() {
            return document.documentElement.scrollLeft || window.pageXOffset || document.body.scrollLeft;
        }
```
```js
    
        var box = document.querySelector('.box');
        var inner = document.querySelector('.inner');
        console.log('box.scrollHeight==>', box.scrollHeight);//内容不溢出为盒子高度//如果溢出 溢出部分影藏或auto则 得到的则是内容height + 上下padding和magin的值
        console.log('box.scrollWidth==>', box.scrollWidth);//盒子不溢出为盒子宽度//溢出影藏或auto的话 则得到的是盒子内容宽+左边的maegin和margin
        console.log('inner.scrollTop==>', document.documentElement.scrollTop);//被父元素遮挡或者页面遮挡的部分
        console.log('inner.scrollLeft==>', inner.scrollLeft.scrollLeft);//被父元素遮挡或者页面遮挡的部分
```


### client

 - clientHeight和clientWidth获得的是盒子的宽高,内容溢出不算.
 - clientTop和clientLeft获得是上左border的宽度.
 ```js
     console.log(box.clientHeight);//可视区域高度  有padding的高 内容溢出不算
        console.log(box.clientWidth);//可是区域宽度  有padding的宽度 内容溢出不算
        console.log(box.clientTop);//上border的宽度
        console.log(box.clientLeft);//左border的宽度

 ```
#### 封装动画
- 匀速动画
```js
    function eveMove(ele, end, step) {
            var start = ele.offsetLeft;
            if (start == end) return;
            if (ele.timer) clearInterval(ele.timer);
            ele.timer = setInterval(function () {
                start = ele.offsetLeft;
                step = end > start ? Math.abs(step) : -Math.abs(step);
                ele.style.left = start + step + 'px';
                if (Math.abs(end - start) < Math.abs(step)) {
                    ele.style.left = end + 'px';
                    clearInterval(ele.timer);
                    console.log('清除e')
                }

            }, 1000 / 60)
        }
```
- 变速动画
```js

        function slowlyMove(ele, end) {
            if (ele.timer) clearInterval(ele.timer);
            var start = ele.offsetLeft;
            if (end == start) return;
            ele.timer = setInterval(function () {
                start = ele.offsetLeft;
                var sep = (end - start) / 10;
                if (Math.abs(sep) < 1) {
                    sep = sep > 0 ? 1 : -1;
                }
                ele.style.left = start + sep + 'px';
                if (end == start + sep) {
                    console.log('定时器已清除')
                    clearInterval(ele.timer);

                }
            }, 1000 / 60)
        }
```

###### 多样式获取

```js
    function getStyle(ele,className){
        if(ele.currentStyle){
            return ele.currentStyle[className];
        }else{
            return window.getComputedStyle(ele,null)[className];
            //null||伪元素
        }
    }
```
### 事件对象
```js
box.onclick = function () {
            console.log(event);
            console.log('触发的事件类型', event.type);
            console.log('触发事件的目标', event.target);
            console.log('绑定事件的元素', event.currentTarget);
            console.log('鼠标距离页面左面的距离', event.pageX)
            console.log('鼠标距离页面上面的距离', event.pageY)
            console.log('鼠标距离触发元素左面的距离', event.offsetX);
            console.log('鼠标距离触发元素上面的距离', event.offsetY);
            console.log('鼠标距离可是区域左面的距离', event.clientX);
            console.log('鼠标距离可视区域上面的距离', event.clientY);
            console.log('鼠标距离屏幕上面的距离', event.screenY);
            console.log('鼠标距离屏幕左面的距离', event.screenX);
            
        }
    阻止冒泡事件:  event.stopPropagation ? event.stopPropagation() : cancelBubble = true;
    阻止默认事件:  event.preventDefault ? event.preventDefault() : event.returnValue = false;

```
- closest(选择器) 获取的是符合条件的最近的父元素没有的话就返回自己.
- 事件委托: ==================>用得多(给父元素加事件,判断是否目标元素,触发事件).

- 元素拖拽的两种方法
    1.  获取鼠标在元素中的位置的距离,移动时鼠标的位置减去获取的那个距离.
    2. 记录鼠标的位置,移动后鼠标的位置减去之前鼠标记录的位置 + 移动元素当前的位置.


#### 防抖

    ```js
        //一开始不执行 停下来就执行
            function debounce(fn,time){
                var timer = null;
                return function(){

                    if(timer){
                        clearTimeout(timer)
                    }
                    timer = setTimeout(function(){
                            fn();
                    },time)
                }
            }

    //一开始先执行一次 一直动不执行  等同下面

        function debounce(func, wait) {
            var timer = null;
            return function () {

                if (timer) {
                    clearTimeout(timer);
                } else {
                    func();
                }
                timer = setTimeout(function () {
                    timer = null;
                }, wait);
            }
        }

    ```

#### 节流

     ```js

        //每过time 执行一次 
               function throttle(fn,time){

                   var times = new Data();
                   return function(){
                       var temp = new Data();

                       if(temp - times >= time){
                           fn();
                           times = temp;
                       }
                       
                   }

               }

        //
            function throttle(fn,time){
                var timer = null;

                return function(){
                    if(!timer){
                        fn();
                    }

             timer = setTimeout(function () {
                    timer = null;
                }, 1000)

                }

            }
     ```

#### localhost

```js
        console.log("#号后跟零或多个字符 ===>", location.hash);
        console.log("返回服务器名称和端口号", location.host);
        console.log("返回不带端口号的服务器名称", location.hostname);
        console.log("返回当前加载页面的完整URL", location.href);
        console.log("返回URL中的目录和（或）文件名", location.pathname);
        console.log("返回 URL 中指定的端口号", location.port);
        console.log("返回页面使用的协议", location.protocol);
        console.log("返回URL的查询字符串", location.search);
        console.log("返回页面使用协议+网站名", location.origin);

```

#### 多媒体标签

```js
    // 多媒体的dom元素.属性的方法获取控制
     <button>currentTime获取当前进度</button>
    <button>duration总时长</button>
    <button>paused播放状态</button>
    <button>load()重新加载</button>
    <button>play()播放</button>
    <button>pause()暂停</button>
    <button>oncanplay 开始播放时触发</button>
    <button>ontimeupdate 播放中触发</button>
    <button>onended 播放完触发</button>

```
#### es5新增存储
- **seesionStroage** 和 **localStroage**

 | 传值          | 作用     |
 | :--------:   | :-----:   | :----: |
 | set(key,value)| 设置参数 |
 | get(key)      | 获取value|
 | remove(key)| 根据key移除某个参数|
 |clear()|清空存储|

 - 两者区别 前者关闭页面即清除数据,后者需手动清除. 需要相同域名下使用数据
 ##### 判断是否全屏和全屏操作

 ```js
<script>
        var inner = document.querySelector('.inner')

        // 全屏
        inner.ondblclick = function () {
            if (ifFullscreen()) {
                if (document.exitFullscreen) {
                    document.exitFullscreen();
                } else if (document.webkitCancelFullScreen) {
                    document.webkitCancelFullScreen();
                } else if (document.mozCancelFullScreen) {
                    document.mozCancelFullScreen();
                }
            } else {
                if (inner.requestFullscreen) {
                    inner.requestFullscreen();
                } else if (inner.webkitRequestFullscreen) {
                    inner.webkitRequestFullscreen();
                } else if (inner.mozRequestFullscreen) {
                    inner.mozRequestFullscreen();
                } else {
                    alert("sorry,无法全屏");
                }
            }
        }

        // 判断是否是全屏
        function ifFullscreen() {
            return document.fullscreen || document.webkitIsFullScreen || document.mozFullScreen || false;
        }
    </script>

 ```