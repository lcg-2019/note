### 节点的获取方法
```js
      document.getElementById('id')//根据id找元素---返回的是对象
        document.getElementsByClassName('类名')//根据类名找元素---返回的是伪数组
        document.getElementsByTagName('标签名')//根据标签名找元素---返回的伪是数组
        element.parentNode;//获取的是父级节点 ---返回的是对象
        element.childNodes;//获取的是***所有***的子节点---返回的是伪数组
        element.children;//获得的是所有的子元素---返回的是伪数组
        element.previousElementSibling;//获得的是前一个兄弟元素 ----返回的是对象
        element.previousSibling//获得是前一个节点---返回的是对象.----ie678获取的是元素节点
        element.nextElementSibling;//获得的是后一个兄弟元素 ---返回的是对象
        element.nextSibling;//获得的是后面一个节点---返回的是对象.----ie678获取的是元素节点
        element.firstElementChild;//获取的是第一个子元素
        element.firstChild;//获取的是第一个子节点 ---返回的是对象;ie678获取的是元素节点
        element.lastElementChild;//获取的是最后一个子元素
        element.lastChild;//获取的是最后一个子节点 ---返回的是对象;ie678获取的是元素节点
        
        -------------
            //兼容代码  其它同理
        element.previousElementSibling =  element.previousElementSibling  || element.previousSibling;
        element.firstElementChild =  element.firstElementChild || element.firstChild;


        function childnode(ele){
            var arr = ele.childNodes;
            var newArr = [];
            for(var i = 0 ;i < arr.length; i++){
                // console.log(arr[i]);
                if (arr[i].nodeType == 1){
                    newArr.push(arr[i]);
                }
            }
            return newArr;
        }

```

#### 元素的创建 添加 删除
```js
    
        //创建元素与添加
        document.createElement('标签');//创建标签
        element.cloneNode('teue/false');//默认false只克隆本身 为true则克隆其及其所有子元素;
        element.appendChild(document.createElement('标签'));//添加在子元素的最后一个; 不能重复插入是剪切效果
        element.insertBrfore(document.createElement('标签'),参考节点);//父节点.insertBefore(新的子节点, 作为参考的子节点);插在参考节点之前


         //删除节点
        element.removeChild(子节点);//删除子节点
        element.parentNode.removeChild(element);//自己删除自己

```

####　操作属性
```js 
            
            //获取属性 
            // 直接 . ; element.style   element.style.width  element.className ...
            element.getAttribute('属性名')//获取属性
            element.setAttribute('属性名')//设置属性
            element.removeAttribute('属性名')//删除属性

```

#### 类名的操作

```js
            
            // 类名的追加
            element.classList.add('类名')
            // 类名的移除
            element.classList.remove('类名')
            // 有此类名就移除 无则添加
            element.classList.toggle('类名')
            // 检测是否有此类名返回true/flase
            element.classList.contains('类名')

```