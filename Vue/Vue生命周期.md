# 生命周期
图示
![Image text](./lifecycle.png)
### 生命周期中的八个钩子函数
##### 创建周期
- beforeCreate: 初始化Vue实例中的data数据methods中的方法==.
- created : 最早可以使用data中的数据和methods中方法的时候.
- beforeMount: 实例化的Vue所控制的空间已在虚拟内存中渲染好了,但是还没有更新到页面中去.
- mounted : 此时渲染好的页面更新到了页面上.
##### 运行周期
- beforeUpdate: 数据发生更改 更新时触发,此时页面数据还没更新 data中已更新
- updated: 数据已经更新到页面上
-  *ps*:创建周期中created钩子函数更新时不会触发===>运行周期才会触发

##### 销毁周期
- beforeDestory: 销毁之前 (销毁之前触发（销毁相当于vue中的v-if=false的效果，清除掉dom元素）)
- destoryed:   销毁之后触发, Vue不会清除计时器等 ,此阶段可以用来清除计时器等
