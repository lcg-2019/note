##  html标签


### 常见标签
- 块元素的标签:div p h1~h7 form  ...
- 行内块元的素标签: input button ...
- 行内元素的标签:span s ins del b strong 大多为文本标签 ...

#####  文档类型`<!DOCTYPE>`
- `<!DOCTYPE html>`声明文档类型为html5

##### `<meta>标签`
- `<meta charset="UTF-8">`指定字符集编码
- `<meta name="keysworrd" content="设置的关键字">`   设置关键字 热词中间`,`隔开.
- `<meta name="desrcipition" content="设置的描述信息">`
- `<meta http-equiv="X-UA-Compatible" content="ie=edge">` 以高版本ie运行
- `<meta name="viewport" content="width=device-width, initial-scale=1.0">` 适配移动端 具体(暂未知).
##### `<title></title>`标题标签


##### `<div></div>`标签 常用于布局


##### `<p></p>` 段落标签


##### 标题标签
```html
    <h1>一级标题 一个网页只能有一个</h1>
    <h2>二级标题</h2>
    <h3>三季标题</h3>
    <h4>四级标题</h4>
    <h5>五级标题</h5>
    <h6>六级标题</h6>
```
##### 换行标签
- `<br>`换行

##### `<img>` 标签
-   `<img src="image/bf.pn" alt="无法显示......." title="野马=========">`
    - src标签的地址可以是相对或绝对路径.
    - alt地址不可用时显示.
    - title鼠标放到图片上显示的字.

| 标签|作用 |其他作用|
|:---:|:---:|:---:|
|`<b></b>`|加粗|无语意|
|`<strong></strong>`|加粗|表示内容重要的语义|
|`<del></del>`|删除线|未知|
|`<s></s>`|删除线/打折线| 无|
|`<em></em>`|倾斜|表示一段内容中着重点的语义|
|`<i></i>`|倾斜|无|
|`<ins></ins>`|下划线|未知|
#####常用的几个转义字符
- '<'`&lt;`
- '>'`&gt;`
- 空格 `&nbsp;`
##### ` <a href=""></a>` a标签
-   ` <a href="http://www.baidu.com" target="_blank">百度</a>`
target="_blank"重新打开一个网页跳转到百度
-   `<a href="http://bing.com" target="_self">bing</a>`
target="_self"当前窗口跳转到bing搜索,同时不设置默认也是.
##### `<table><table>`表格标签
```html 
<table border="1" cellspacing="0" cellpadding="10" align="center" >
        <tr>
            <th>序号</th>
            <th>书籍</th>
            <th>作者</th>
            <th>主角</th>
        </tr>
        <tr>
            <td rowspan="2">1</td>
            <td>遮天</td>
            <td rowspan="2">辰东</td>
            <td>叶凡</td>
        </tr>
        <tr>
            <td>神墓</td>
            <td>辰南</td>
        </tr>
        <tr>
            <td>2</td>
            <td>斗破苍穹</td>
            <td>天蚕土豆</td>
            <td>肖炎</td>
        </tr>
        <tr align="center">
            <td>3</td>
            <td>风凌天下</td>
            <td colspan="2">凌风</td>
        </tr>
    </table>
```
- cellpadding 是边框与其内容的间隙大小；
- cellspacing 是边框与边框之间的间隙大小；
- rowspan 跨行表格
- colspan  跨列合并
#### 表单类的标签
```html
 <!-- type属性描述输入框功能 text 文本框  password 密码输入框 radio 单选框 checkbox 复选框  button 按钮 submit 提交 reset重置 
   <input type="text"> -->
   <!-- action 提交到的地址 method提交的方式  -->
   <form action="" method="GET">
       <!-- form 表单域 -->
       <fieldset>
           <!-- fieldset  分组 -->
           <legend>基本信息</legend>
           <!-- legend 分组 -->
           <label for="use">用户名</label> <input type="text" id="use" autofocus placeholder="what">
           <!-- label绑定一个元素点击使其获取焦点 autofocus 自动获取焦点  placeholder 设置提示信息 -->
           <select name="" id="">
               <!-- select 下拉选项框 -->
               <option value="">only you</option> 
               <!-- option 下拉选项  -->
           </select>
            <input type="file" multiple>
            <!-- input 的type属性值为file则为上传 multiple为上传多个文件 -->
            <textarea name="" id="" cols="30" rows="10" style="resize: none;" readonly disabled></textarea>
            <!-- readonly 只读  disabled 禁止读写 style="resize:none"为禁止拉伸 -->
            <input type="image" src="reg.jpg">
            <!-- type 为image 则为图片样式的提交按钮 -->
       </fieldset>
   </form>
   ```
##### `<form></form>`标签
- `<form action="" method="post"></form>`
    - action属性是要提交的地址
    - method属性是提交的方式

##### ` <fieldset> </fieldset>` 用于分组
##### `   <legend>基本信息</legend>` 用于分组
##### `<label></label>`
- ` <label for="use">用户名</label>` 一般配合input使用 for属于为input的id值 点击它让对应的input标签获取焦点
##### `<input type="" value="" name="">`

 |属性|属性值|描述|
 |:----:|:----:|:----:|
 |type|text|文本输入框|
 | /  | radio|单选框 需name 配合使用|
 |/|checkbox|多选框 需name 配合使用|
|/|button|普通按钮|
|/|submit|提交按钮|
|/|reset|重置按钮|
|/|iamge|图片形式的提交按钮 有额外的src|
|/|file|上传文件 加 multiple可同时上传多个文件|
|name| 随便输入 |配合使用|
|value| 随便输入 |input的默认文本|
|checked| 多选框默认选中|/|
|autofocus|自动获得焦点|/|
|placeholder|`placeholder="任意"`|提示用的|
|required|禁止读写|/|
|readonly| 只读||
##### `<textarea>`标签
- `<textarea name="" id="" cols="100" rows="10"   required style="resize:none;vertical-align:middle"><textarea>` 文本域
- resize:none 禁止拉伸.
-------------
#### 序列标签
### 元素的特性
#### 块级元素
1. 块级元素独占一行,没有设置宽,通栏.
2. 宽和高可以有效设置
##### 行内块元素
1. 可以和其他元素共占一行,没有设置宽则为默认宽高(或内容撑开).
2. 可以有效设置宽高.
##### 行内元素
1. 可以和其他元素共占一行,没有设置宽高则为内容宽高.
2. 设置宽高无效.
