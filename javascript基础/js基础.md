## 命名
- 只允许存在 字母 数字 _  $.
- 不能数字开头,严格区分大小写.
- 驼峰命名法后面的首字母大写.
- 见名知意.
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


