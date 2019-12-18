
# ES6


#### let
  - let 没有变量提升 只能声明一次;代码段中有绑定效果
  ```js
 for (var i = 0; i < 4; i++) {
            setTimeout(function () {
                console.log(i)//4,4,4,4
            })
        }
        console.log(i)//4   延迟计时器进入异步线程等待 等主线程运行完了再执行
        for (let j = 0; j < 4; j++) {

            setTimeout(() => {
                console.log(j) //0,1,2,3
            }, 200)
        }
  ```
#### const 
- const 同let不可重新定义,并且不可修改.(ps:作为引用类型数据地址的时候可以改变数据但不可改变地址)
```js
       const age = 8;
        // var age = 8; 
        try {
            age = 9;
            console.log(9)
        } catch (error) {
            console.log(error)
        }

        const obj = {
            name: '刘大',
            age: 12,

        }
        obj.name = '李四',
            console.log(obj);
```

#### 箭头函数
-     箭头函数用起来好像很方便的样子,this的指向是上级的作用域的this.

##### 设置函数的默认值
```js
    
        function fn(a, b) {
            var b = b || 0; //老写法
            return console.log(a + b);
        }
        fn(4)
        // es6 新写法 ==== 同上面挺方便
        function fn1(a, b = 0) {
            return console.log(a + b);
        }
        fn1(3)
```


#### 解构赋值
```js
     var arr = [1, 2, 3];

        var [a, b, c, d] = arr;
        console.log(a, b, c, d); //1  2  3  unfined一一对应 根据index值 多传则为unfined;


        var arr1 = [56, 6, 7, [6, [9, [10], 15], 1], 3];
        var [, , , [, [, [s],],],] = arr1; //10 还可以这么玩
        console.log(s);


        var obj = {
            name: '占三',
            age: 18
        }
        var { name, age } = obj;
        try {
            console.log(name, age, haha); //占三  18  err(haha未定义)  ----与属性一一对应 
        } catch (error) {
            console.log(error)//ReferenceError: haha is not defined
        }


        function fb({ name, age }) {
            arguments[0].name = 'lis'
            console.log(name, age)//{name:'占三',age:18}
            console.log(obj)//{name:'lis',age:18}
        }
        fb(obj);
```

##### 扩展运算
```js
            var arr = [1, 2, 3];
        var arr1 = [4, 5, 6]
        console.log(...arr);//1 2 3
        console.log(...arr1);//4 5 6
        var newArr = [...arr, ...arr1]
        console.log(newArr)//[1, 2, 3, 4, 5, 6]
        var arr2 = [...arr1];
        console.log(arr2)// 4,5,6
```
##### 将伪数组变成真数组
```js
    
        function fn() {

            console.log(Array.from(arguments));//[1, 5, 6, 6, 8]
        }
        fn(1, 5, 6, 6, 8)
        function fn1() {
            console.log(Array.prototype.slice.call(arguments));//[465, 4, 6, 46]
        }
        fn1(465, 4, 6, 46)
```
## ES6数组新方法
- **find**(ele,index,arr)**findIndex**(ele,index,arr):===> 和foreach一样遍历数组形参相同但有返回值返回的是第一个符合条件的ele (ele为数组中的每一项)findIndex则返回的是第一个符合条件的下标,=====>且一旦符合条件则不会再往下遍历直接返回. ===========>
 ```js
    var arr = [
            { age: 25 },
            { age: 13 },
            { age: 89 }
        ];


        var num = arr.find(ele => ele.age > 13); //{age: 25}
        console.log(num)
        var num1 = arr.findIndex(function (ele, index, arr) {
            console.log('ele==>', ele, 'index==>', index, 'arr=>', arr)//ele==> {age: 25} index==> 0 arr=> (3) [{…}, {…}, {…}]
            return ele.age > 13;
        })
        console.log(num1)//0
 ```

- **map**:===>map数组方法是同feach遍历 修改数据后返回修改后的数据 且是一个数组.
```js
        var arr = [
            {
                age: 25,
                sex: 0
            },
            {
                age: 13,
                sex: 0
            },
            {
                age: 89,
                sex: 1
            }
        ];

        var arr1 = arr.map(ele => {
            ele.age += 3;
            ele.sex = ele.sex === 0 ? '女' : '男';
            return ele
        })

        console.log(arr1)
        /*
          (3) [{…}, {…}, {…}]
                0: {age: 28, sex: "女"}
                1: {age: 16, sex: "女"}
                2: {age: 92, sex: "男"}

        */
```
- **filter**:返回的是数组 筛选所有符合条件;
```js
           var arr = [
            {
                age: 25,
                sex: 0
            },
            {
                age: 13,
                sex: 0
            },
            {
                age: 89,
                sex: 1
            }
        ];

        var arr1 = arr.filter(ele => ele.age > 0);
        /*
            (3) [{…}, {…}, {…}]
                0: {age: 25, sex: 0}
                1: {age: 13, sex: 0}
                2: {age: 89, sex: 1}
        */
        console.log(arr1);
```
- **array.some**方法 判断是否有符合条件的 只要有一个符合则返回true 反之则false.
- **array.every**方法 判断是否全部符合条件 只要一个不符合则返回false 反之则是true.

```js
            var arr = [
            {
                age: 25,
                sex: 0
            },
            {
                age: 13,
                sex: 0
            },
            {
                age: 89,
                sex: 1
            }
        ];


        var arr1 = arr.some(ele => ele.age > 0) //true
        console.log(arr1)
        var arr2 = arr.some(ele => ele.age > 13) //true
        console.log(arr2)
        var arr3 = arr.some(ele => ele.age > 89) //false
        console.log(arr3)

        var arr4 = arr.every(ele => ele.age > 0) //true
        console.log(arr4)
        var arr5 = arr.every(ele => ele.age > 13) //false
        console.log(arr5)

```
-  **.**includes**(xx)检查字符串 或数组 是否含有(xx),有则是true,无则是false.
```js
            
        var arr = [1, 2, 3, 4];
        var str = 'what where when'
        var bol = arr.includes(5);
        console.log(bol)// false
        bol1 = str.includes('wh')
        console.log(bol1)//true
```

-   **reduce** 返回的是数字  一共支持两个参数 ,第一个是函数(支持四个参数:第一个是累加值,第二个是每次要加的那个数组中的那,第三个是次数,第四个是原数组) 第二个是total的起始值

```js
            var arr = [
            {
                age: 25,
                sex: 0
            },
            {
                age: 13,
                sex: 0
            },
            {
                age: 89,
                sex: 1
            }
        ];

        arr.reduce(function (total, current, cs, array) {
            console.log('total==>', total, 'current==>', current, '次数==>', cs, 'array==>', array);

            /*
            {age: 25, sex: 0} {age: 13, sex: 0}
             undefined {age: 89, sex: 1}
            */

            /*
             total==> {age: 25, sex: 0} current==> {age: 13, sex: 0} 次数==> 1 array==> (3) [{…}, {…}, {…}]
            total==> undefined current==> {age: 89, sex: 1} 次数==> 2 array==> (3) [{…}, {…}, {…}]
            */

        })

        var sum = arr.reduce((total, cuurent) => {
            console.log(total) //0 25  38  127 每次打印值
            return total += cuurent.age
        }, 0)
        console.log(sum)//127
```

#### 新数据结构
- **set**// set是es6新提供的一种数据结构,其所有属性值唯一,并且为建构函数.可用于去重有//size属性与数组长度相似.// add 添加属性//delete 删除属性//has  判断是否有该属性//clear 清空

```js
          var arr = [1, 21, 5, 1, 1, 1];
        var arr1 = new Set(arr);
        console.log(arr1);//Set(3) {1, 21, 5}//去重很方便 >__<
        arr1.add(3);
        console.log(arr1)//Set(4) {1, 21, 5, 3}
        arr1.delete(1)
        console.log(arr1)//Set(3) {21, 5, 3}
        console.log(arr1.has(3))//true
        arr1.clear();
        console.log(arr1)//Set(0) {}
```
- **Map**:
```js
          var ma = new Map();
        var obj = {};

        console.log(ma.set(obj, 0))//Map(1) {{…} => 0}
        console.log(ma.get(obj))//0
        console.log(ma.set([], 6))//Map(2) {{…} => 0, Array(0) => 6}
        console.log(ma.delete([]))//删除失败返回false ps:字面量方式的数组没保存地址的话,每次都不一样.
        console.log(ma.delete(obj))//true
        console.log(ma)//Map(1) {Array(0) => 6}
        console.log(ma.has(obj));//false 判断是否有obj
        console.log(ma.clear());//清空 ma;

        //Map Es6提供的数据结构 类似对象 是key = value 的方式;
        /*
            set(任意类型,任意类型),用于添加键值对,重复则是添加.
            get(key) ,用于获取value
            delete(key),用于删除 删除失败返回false 成功则返回true;
            has(key),用于查询是否存在此key 返回是Boolean类型
            clear(),清空Map.

        */

```

##### assign 
- (目标对象, 源对象) 属于浅克隆 属性值(相当于深克隆)方法是(浅克隆) 将源对象的方法给目标对象==>无则加之有则换之.
```js
          var obj = {
            name: '李四'
        };

        var obj1 = {
            age: 18,
            say: {
                h: 'haha',
            }
        }

        Object.assign(obj, obj1);
        console.log(obj)//添加了obj1的属性 {name: "李四", age: 18, say: {…}}
        console.log(obj1)//{age: 18, say: {…}}
        obj.age = '张三';
        console.log(obj1);//{age: 18, say: {…}}
        obj.say.h = 'ee';
        console.log(obj1);//改变了 'haha' ===>'ee'
        // Object.assing(目标对象, 源对象) 属于浅克隆 属性值(相当于深克隆)方法是(浅克隆) 将源对象的方法给目标对象==>无则加之有则换之.
```