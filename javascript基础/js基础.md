## 命名
- 只允许存在 字母 数字 _  $ 
- 不能数字开头,严格区分大小写.
- 驼峰命名法后面的首字母大写.
- 见名知意.
- 不能是关键字和保留字
## 数据类型

#### 基本数据类型

#### 数字类型 

-  number   `console.log(typeof 10);// number`
##### 其他数据类型转换成数字类型
- 第一种方法
```js
                //字符串转换成数字
                console.log(Number('222'));//222
                console.log(Number('abc'));//NaN
                console.log(Number('dsa4564'));//NaN
                console.log(Number(''));//0  空字符串
                console.log(Number('    '));//0  全空格的字符串
                // 布尔类型转换成数字
                console.log(Number(true));//1
                console.log(Number(false));//0
                // undefined转换成数字
                console.log(Number(undefined));//NaN       
                // null转换成数字
                console.log(Number(null));//0
                //NaN转换成数字
                console.log(Number(NaN));//NaN

```
- 第二种方法
    ```js
                 //字符串转换成数字
                console.log(parseInt('222'));//222
                console.log(parseInt('abc'));//NaN
                console.log(parseInt('dsa4564'));//NaN
                console.log(parseInt('1651.15.sda'));//1651
                console.log(parseInt(''));//NaN  空字符串
                console.log(parseInt('    '));//NaN  全空格的字符串
                // 布尔类型转换成数字
                console.log(parseInt(true));//NaN
                console.log(parseInt(false));//NaN
                // undefined转换成数字
                console.log(parseInt(undefined));//NaN       
                // null转换成数字
                console.log(parseInt(null));//NaN
                console.log(parseInt(NaN));//NaN
    ```
###### parseInt
- parseInt(数值,进制);
```js
                        console.log(parseInt(18,16));//24
                         console.log(parseInt(18,10));//18
```
#### 字符串类型

-  string   `console.log(typeof '10');//string`
##### 其他数据类型转换成字符串类型
- 第一种方法
```js
                // 第一种方法
                // 数字转换成字符串
                console.log(String(1515));//"1515"
                // Boolean转换成字符串
                console.log(String(true));//"true"
                console.log(String(false));//"false"
                //undefined转换成字符串
                console.log(String(undefined));//"undefined"
                //null转换成字符串
                console.log(String(null));//"null"
                //NaN转换成字符串
                console.log(String(NaN));//"NaN"
```
- 第二种方法
```js
                 // 数字转换成字符串
                console.log(""+1515);//"1515"
                // Boolean转换成字符串
                console.log(""+true);//"true"
                console.log(""+false);//"false"
                //undefined转换成字符串
                console.log("231"+undefined);//"231undefined"
                //null转换成字符串
                console.log("sad"+null);//"sadnull"
                //NaN转换成字符串
                console.log(null+"15");//"null15"
```
#### Boolean类型
-  Boolean  `console.log(typeof true);//Boolean`
##### 其他数据类型转换成布尔类型
```js 
                 // 数字转换成布尔类型
                console.log(Boolean(151));//true
                console.log(Boolean(0));//false
                // 字符串转换成布尔类型
                console.log(Boolean('dsadas'));//true
                console.log(Boolean('   '))//true 有空格的字符串
                console.log(Boolean(""));//false 空字符串
                // undefined转换成布尔类型
                console.log(Boolean(undefined));//false
                // null转换成布尔类型
                console.log(Boolean(null));//false
                //NaN转换成布尔类型
                console.log(Boolean(NaN));//false
                //空对象也是true
                console.log(Boolean({}));//true
```

#### undefined
-  undefined `console.log(typeof undefined);//undefined`

#### null
-  null`console.log(typeof null);//null`

### 引入数据类型

####   数组
- object `console.log(typeof [10,10]);//object`

####  函数
-  function` console.log(typeof Math.max)//function`

####  对象
-  object `console.log(typeof {});//object`

### 算数运算符
> 当对非 Number 类型的值进行运算（ 包括 -、 * 、/）时，会将这些值转换为 Number 然后再运算。任何的值和字符串做加法运算，都会先转换为字符串，然后再做拼串操作。+ 加法运算  有一边 是 字符串,都会把另一边转换成字符串,进行拼接操作.
```js
        console.log('10'-5);//5
        console.log(true - 5);//-4
        console.log(false * 5);//0
        console.log(undefined / 1);//NaN
        console.log(null + 20);//20
        console.log(NaN % 4);//NaN
```
- 自增 自减
```js
        //先运算再自加
            var num = 0;
             var sum = num++ + 10;
             console.log(num);//1
             console.log(sum);//10
            var num1 = 0;
        //先自加再运算
            var num1 = 0;
            var sum1 = ++num1 + 10;
             console.log(num1);//1
             console.log(sum1);//11
        //先运算再自减
            var num2 = 0;
            var sum2 = num2-- +10;
            console.log(num2);//-1
            console.log(sum2);//10
        //先自减再运算
            var num3 = 0;
            var sum3 = --num3 +10;
            console.log(num3);//-1
            console.log(sum3);//9
```
### 比较运算符
- 对于非数值进行比较时，会将其转换为数字然后再比较。
```js
         var num = 1;
        console.log(num > true );//false 
        console.log(false  == 0);//true
        console.log(num >= 'dsa');//false
        console.log(16 > '6546');//false
     
        console.log(NaN >= 58);//false 任何值和NaN做任何比较都是false
        // 两边都是字符串则比较的是Unicode码表的顺序
        console.log('99' < '11111111'); //false

```
-     ==  不严谨   != 等于== 取反
       ```js
        console.log('我' == '我');//true
        console.log('1' == 1);//true
        console.log(undefined == null); // true undefined 衍生自null
        console.log(NaN == NaN);//false 任何值和NaN做任何比较都是false
       ```
-     === 严谨   !== 等于 ====取反
      ```js

        console.log('1' === 1);//false
        console.log('10' === '10');//true

       ```

----------------------------------------------
## 对象

- 创建对象的三种方法

```js
               // 创建对象的方法
        // 第一种 字面量的方式创建对象
        var user = {
            name : '刘大',
            sex : '男',
            '年龄' : '39',
            '能力' : function(){
                console.log('装怂');
            }
        };
        console.log(user['年龄']);
        user['能力']();
        console.log(user,typeof user);

        //第二种内置构建函数创建对象
        var user1 = new Object;
        user1.name = '关二';
        user1.sex = '男';
        user1['年龄'] = '28';
        user1['能力'] = function(){
            console.log('牛逼就完了');
        };

        console.log(user1,typeof user1);
        //第三种 自定义构建函数的方法创建函数
         function Parson(name,sex,age){
            this.name = name;
            this.sex = sex;
            this.age = age;
            this['能力'] = function () {
                console.log('what');
            };
        };


        //this 指向调用者本身
        var user2 = new Parson('张三','男',16);
        console.log(user2,typeof user2);
        var user3 = new Parson('赵四','男',18);
        var user4 = new Parson('黄五','男',59);
        var user5 = new Parson('马六','男',21);
        console.log(user3);
        console.log(user4);
        console.log(user5);

```
-  this 指向调用者本身
- delete 对象.属于 可以删除属性 `delete  obj.type`;
 #### Math对象
###### Math对象内置的方法
- `Math.abs()` 绝对值
- `Math.floor()` 向下取整(向小取整)
- `Math.ceil()` 向上取整(向大取整)
- `Math.pow(x,y)` 表示x的y次幂
- `Math.PI` π
- `Math.round()` 正数四舍五入 负数五舍六入
- `Math.random()` 随机 0~1之间的小数(很多位的小数,且取不到1)
- `Math.sqrt(3)` 开方 (根号3); 
```js
     console.log(Math.abs(-88));//88 绝对值
        console.log(Math.floor(1.9));//1 向下取整 /向下取整
        console.log(Math.ceil(1.1));//2 向上取整 /向大取整
        console.log(Math.pow(2,3));//2的3三次幂 
        console.log(Math.random());;//随机数 0-1之间
        console.log(Math.sqrt(25));//25开方
        console.log(Math.round(-0.5));//-0 正数四舍五入 负数 五舍六入
        console.log(Math.round(2.5));//3   
 ```
 #### Date对象
 ###### Date内置对象的方法
 ```js
     var date = new Date();   
        console.log('年份' +  date.getFullYear()); //获取年份
        console.log('月份' +   (date.getMonth()+1));//获取月份 因为月份从0开始所以要加1;
        console.log('周' + date.getDay());
        console.log('日' + date.getDate());
        console.log('时' + date.getHours());
        console.log('分' + date.getMinutes());
        console.log('秒' + date.getSeconds());
        console.log('毫秒' + date.getMilliseconds());
        console.log('时间戳' + date.getTime());
        console.log('时间戳' + Date.now());

        //指定时间
        var dat = new Date('2019/10/22 20:20:20');
        //再使用date的方法 获取的就是指定时间的数据.

```
#### string 的方法
- str.charAt(索引);
- str.charCodeAt(索引)
- str.indexOf(元素)
- str.lastIndexOf(元素)
- str.concat(str,str)
- str.slice(一个或多个索引)
- str.substr(一个或多个索引)
- str.toUpperCase(不用参数)
- str.toLowerCase(不用参数);


```js
        
         var  str = 'dsadasdsa12';
         console.log(str.charAt(8));// 返回值是括号内索引所选中的字符
         console.log(str.charCodeAt(0))//返回值是索引值选中字符的Unicode码表对应的编码.
         console.log(str.indexOf('sa',2))//返回对应元素的索引. 第二个参数是开始的位置
        console.log(str.lastIndexOf('sa',4))//返回对应元素的索引 ,同indexOf 只不过是相反的.
        console.log(str.concat(str,str,str)); //返回值是新的字符串;从后面添加.
        console.log(str.slice(1,5));//返回值是截取的字符串部分,如果只一个表示从这个索引截取到结束 为0的话可以用于复制.
        console.log(str.substr(0,2));//返回值是截取的部分从索引0 开始截取2个;(只能两个多传无效) 为0的话可以用于复制.
        console.log(str.toUpperCase())//返回值是新的字符串 .改变大小写.
        console.log(str.toLowerCase());//返回值是新的字符串 .改变大小写.


```
#### Array对象
> 数组内数据尽量保持同一类型
###### 创建数组的两种方法
1. **字面量**的方法 `var arr = []`;
2. 用**构建函数**的方法`var arr = new Array()`;如果括号内为一个数字类型的元素 则表示该书组的长度,里面的数组元素都是empty;
######  数组的方法
- `array.pop(没有参数)`--------------------- 返回值是 删除的元素;不用传参; 删除最后一个元素;
- `array.push(没有参数)` ------------------返回值是数组长度;可以传一个到多个 ;从最后面添加元素; 
- `array.shift(没有参数)` -----------------返回值是删除的元素;不用传参;删除第一个元素;
- `array.unshift(没有参数)`------------------返回值是数组长度;可以传一个到多个参数;从前面添加元素;
- `array.contcat(参数为一个或多个数组)`----------------返回值是新的数组;传的值为一个或多个数组,逗号隔开; 从后面添加数组;
- `array.join(连接符('-'),----------------返回元素个数)`返回值是字符串;传的值一个是为字符串的连接符,两个值的时候第二个值为返回的元素数量;将数组元素用连接符连接起来转换成字符串.
- `array.split(任意参照物)`-----------返回是分割后的数组;传一个值为分割的参照物;将数组分割成数组
- `array.slice(索引1~2)`--------------返回值是截取的部分;一个参数(索引)时 从该参数直接取到结尾,两个参数的时候则从第一个参数取到第二个参数(不包括第二个参数);截取数组;  -----如果索引只有一个且为0 则可当复制数组使用.
- `array.splice(索引1,个数,添加的任意元素可以多个)` ------------返回值是删除的部分;一个参数时为从头开始删除到该参数(索引),两个参数则表示从第一个参数开始删除多少个,两个以上则表示在删除的元素后面添加元素; 删除指定部分的数组元素.
- `array.indexOf()` --------------------返回值是搜索到的元素的索引;一个参数(搜索的元素),两个参数 第二个参数为开始位置的索引; 主要用于搜索数组元素的索引;
- forEach
- ```js
            var arr = [1,656,161,61,61,6164,46];
            arr.forEach(function(item,index,array){
                    console.log(item,index,array)//值,索引,原数组(没卵用),一般传两个参数.

            })

```
```js
    
        var ar = new Array();


        arr = [1,12,12,1,21,31,31,3,13,13];

        var a = arr.shift();//返回的是删除掉的  删除掉第一个元素
        console.log(a,arr);
        var h = arr.pop();//返回删除元素的最后一个  
        console.log(h,arr);


        var chang = arr.unshift('添加在最前面','可以添加多个');// 返回的是数组的长度
        console.log(chang,arr);
         var  mb = arr.push('添加到最后边','也可以多个');//返回的是数组的长度
         console.log(mb ,arr);


         var ar1 = [1,2,13,213];
         var ar2 = new Array(123,123,123);//只填一个数字的时候是设置长度 元素师empty
         var newArr = ar1.concat(ar2);//数组拼接 返回的是拼接后的数组
          console.log(newArr,ar1,ar2);


          var nums = [1,2312,12,13,13];
         var newNums = nums.join('不写默认,号');//转成字符串 
         console.log(newNums,nums);


         var nums1 = nums.toString();//返回带逗号分割的数组
         console.log(nums1 , nums);

         var nums2 = nums1.split(',',3);//不写默认按逗号分割字符串成数组 第二个参数 设置返回元素数量(可不输)
         console.log(nums2,nums1);

         var shuZu = [1,2,3,4,5,6,7];
         var a1 = shuZu.slice(1,2); //从索引1 开始取到2(不包括2) 只有一个参数默认为开始并取到结尾,用于截取数组
         console.log(a1,shuZu);
        var a2 = shuZu.splice(1,2,'添加的元素','可以多个,也可以不输');//一个参数的话从头开始删除几个元素 两个的话为索引(1~2)包括1和2
        console.log(a2,shuZu);

        var shuz = ['a','b','c','d'];
         shuz.indexOf('b',0);//搜索元素的索引 第二个值为开始的位置.
```
---------------------
### 循环

##### for循环
> 
##### if  循环 if else 循环 if (else if)  else

##### while 循环 do while

###### 三种排序方法
```js
      // //插入排序
        var arr = [131,516,156,61,6,66,0,36,15161,61,61,3,30,30,30];
    //     var j = 0;
    //     for(var i = 0;i < arr.length ;i++ ){
    //         j = i -1 ;
    //         var temp = arr[i];
    //         while(j>=0 && temp<arr[j]){
    //             arr[j+1] = arr[j];
    //             j--;
    //         };
    //         arr[j+1] = temp;
    //     }
    //     console.log(arr);

    //冒泡排序

        for(var i = 0;i<arr.length-1;i++){
            for(var j = 0 ;j < arr.length - 1 - i;j++){
                if(arr[j]>arr[j+1]){
                    var temp = arr[j];
                    arr[j] = arr[j+1];
                    arr[j+1] = temp;
                };
            };
        };
        console.log(arr);


       // 选择排序法
        var  min = 0;
        for(var i = 0; i<arr.length ;i++){
            for(var j = i+1;j < arr.length; j++){
                min = i;
                if(arr[min] > arr[j]){
                    min = j;    
              }
                     var temp = arr[min];
                      arr[min] = arr[i];
                        arr[i] = temp;

            }
        }
        console.log(arr);
```
- 内置数组 sort排序的方法
1 不带参数 则默认用Ascall码表的顺序排序.
2 带参数如下
```js
    var nums = [15,61,61,61,6,64,646];
    nums.sort(function(a,b){
       return a - b;//从小到大排序
        // b > a;// 从大到小排序

    })

```






-----------------------------------------------------
## 注意事项
- **声明提升** 变量的声明(变量的赋值不会提前)和函数会提升到script标签的最前面.
- **作用域** 上级不会去下级需找, 下级在自己作用范围内找不到就会去上级需找,直到window下面找到,而且是就近原则.
