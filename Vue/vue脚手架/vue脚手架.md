##  Vue 脚手架

##### import  

+ 引入 组件 import  **name** from  ' **路径**'
+  引入 图片 import  **name** from ''**路径**''
+  引入背景图片 import  ==> ` background( url(~'路径') no-repeat... )`
+  引入 css 或者js ... import  '路径'



##### export

+ export default 变量 的方式  暴露 
  - imporet 引入的时候   ` import  name from  ' 路径' ` 可以这样直接拿

+ export  = {} 的方式 暴露 
  - imporet 引入的时候   ` import  {name} from  ' 路径'` .

### 路由 

router/index 可设置路由

```js
//引入Vue
import Vue from 'vue'
// 引入路由
import VueRouter from 'vue-router'
//注册 路由
Vue.use(VueRouter)

const router = new VueRouter({
    //取消hash
    mode: 'history',
    /清除
    base: process.env.BASE_URL,
    //配置的路由
    routes, ==>  转 圈1 
    //可以在切换页面的时候 让滚动条 回到最上面
    scrollBehavior (to, from, savedPosition) {
        return new Promise((resolve, reject) => {
            setTimeout(() => {
                resolve({ x: 0, y: 0 })
            })
        })
    },
})

//圈1 ==>
const routes = [
    {
        //路由地址
        path: '/',
        
       // path: '/:id', 动态路由  可跳转的时候传值(不传值不跳随便传都跳转)
        
        //组件的名称
        name: 'home',
        //懒加载 
        component: () => import('../views/Home.vue'),
        //元信息 ===> 路由守卫 to里面可以拿到 meta的内容
        meta: {
            title: 'home',
            user: ['中丧生']
        },
         redirect:'/home/info', //定向路由 一跳转到当前路由 就进入路由 '/home/info'
            //组件守卫  加了路由守卫 没有next()是不会往下跳转的  
               // 不！能！获取组件实例 `this`
          beforeEnter:(to,from,next)=>{
              	//to.meta  对象  拿到元信息  
           
              //进行跳转   next('/index')跳转到指定路由
              	next()
              //from 是跳转之前的页面的信息  有 path 等信息
                //to 是要跳转到的页面的信息  有 path 等信息
             } ,
                  //子路由
        children:[
            {
                //不能加/  不能加斜杠
                path:'info',
                name:'info',
                component:()=>import(''../views/info.vue')
            }
        ]
    },

```



##### router-views 渲染组件的标签

#####  router-link 标签 

- to属性  跳转的路由
- tag属性 设置标签类型

- params传值

```js
//this.$route.params  拿到对象 this.$route.params.id  ==>  1
<router-link tag="span" :to="`/index/${动态路由传值}/${动态路由传值可重复写}/`"> 跳转  </router-link>
//写成对象的形式 params 传值 
<router-link :to="{name:'mine',params:{id:1}}">跳转到mine页</router-link>


```



- query传值 	

```js
// 可通过  this.$route.query的方式拿值  是一个对象    this.$route.query.name ==> '张三
<router-link  :to="/index?=name='张三'&id='1331' "> 跳转  </router-link>
```





#####  路由守卫

```js
//全局守卫 (有个问题 没有next  复制了 路由是可以直接跳转到)
router.beforeEach(to,from,next){
        //进行跳转   next('/index')跳转到指定路由
              	next()
              //from 是跳转之前的页面的信息  有 path 等信息
                //to 是要跳转到的页面的信息  有 path 等信息
}


```

###### 

```js
//组件守卫

beforeRouteUpdate(to,from,next){
    //组件复用时 触发
     //可以解决组件复用 不会重复  加载 this.$route.query和  this.$route.params===>
  ===>  可在to中获取 相当于 this
}
   //跳转到其他路由 或者关闭组件时触发
beforeRouteLeave (to, from , next) {
  const answer = window.confirm('Do you really want to leave? you have unsaved changes!')
  if (answer) {
    next()
  } else {
    next(false)
  }
}
```



### transition 标签

```js
默认css类名 .v-enter  .v-enter-to    .v-leave  .v-leave-to     进入离开样式
v-enter-active   .v-leave-active{
  // 过渡 效果  transioion: all 3s ease; ....
} 

//加了name  就是自定义前缀  .v-enter ==> .foo-enter  
<transition  name="foo"  > </transition>
//引入 第三方样式  duration 持续时间  mode="out-in " 和"in-out"  先离开 还是先进入
 <transition enter-active-class=" bounceInDown" leave-active-class=" bounceOutDown" :duration="{ leave:800}">
            <h3 v-if="flag" class="animated">这是h3标题</h3>
        </transition>
```



----------

##  vuex

​	 

## vuex辅助函数 帮助我们节省代码的语法糖

1. mapState  --  当一个组件需要获取多个状态时候，将这些状态都声明为计算属性会有些重复和冗余。为了解决这个问题，我们可以使用 mapState 辅助函数帮助我们生成计算属性，让你少按几次键。(其实就是我们在vuex里面定义的变量  接收的时候还要再定义变量去接收 很麻烦 vuex辅助函数呢 可以帮我们解决这种麻烦)
2. mapGetters -- 将store中的多个getter映射到局部组件的计算属性中
3. mapMutations 将组件中的 methods 映射为 store.commit 调用。
4. mapActions 将组件的 methods 映射为 store.dispatch 调用

### mapState 的三种种写法

```js
export default {
  name: 'home',
  components: {
    HelloWorld
  },
  data () {
    return {
      username:"用户名"
    }
  },
  computed: {
    ...mapState({
      age:state => state.age,  // 第一种  箭头函数 
      num:"num",  // 传字符串参数 'num' 等同于 `state => state.num`
      name (state) {  // 第三种呢 等同于第一种  只不过第三种可以使用this 方便vuex里面的数据结合本地的数据
        return this.username + state.name ;
      }
    })
  }
}
```

### mapGetters  getters的辅助函数

```
import HelloWorld from '@/components/HelloWorld.vue'
import { mapState , mapGetters , mapMutations , mapActions } from "vuex"
export default {
  name: 'home',
  components: {
    HelloWorld
  },
  data () {
    return {
      username:"用户名"
    }
  },
  computed: {
    ...mapState({
      num:"num",
      age:state => state.age,
      name (state) {
        return this.username + state.name ;
      }
    }),
    ...mapGetters({
      price:"price"
    })
  }
}
```

### mapMutations mutations的辅助函数的两种写法

```
methods: {
    ...mapMutations([     // 第一种
      "add",  // 调用的时候执行this.add()  映射为 `this.$store.commit('add')`
      "adds"  // 如果需要提交载荷  直接调用 this.adds(num ) 映射为 `this.$store.commit('adds', num)`
    ]),
    ...mapMutations({
      add: 'add' // 将 `this.add()` 映射为 `this.$store.commit('add')` 
    })
  }
```

### mapActions  actions的辅助函数

```
 methods: {
    ...mapActions([
      'increment', // 将 `this.increment()` 映射为 `this.$store.dispatch('increment')`

      // `mapActions` 也支持载荷：
      'incrementBy' // 将 `this.incrementBy(amount)` 映射为 `this.$store.dispatch('incrementBy', amount)`
    ]),
    ...mapActions({
      add: 'increment' // 将 `this.add()` 映射为 `this.$store.dispatch('increment')`
    })
  }
```

## Module  vuex模块化 

### vuex官方解释 

由于使用单一状态树，应用的所有状态会集中到一个比较大的对象。当应用变得非常复杂时，store 对象就有可能变得相当臃肿。为了解决以上问题，Vuex 允许我们将 store 分割成模块（module）。每个模块拥有自己的 state、mutation、action、getter、甚至是嵌套子模块——从上至下进行同样方式的分割：

### 通俗点的说法

当我们写大型的项目的时候  我们所有的需要共享的信息或状态都写在同一个state里面  导致state或其他的操作比较臃肿 那么 为了解决这个问题 vuex提出了模块化  module

下面呢 是我们模块化的写法 在main.js的同级新建一个store文件夹 在这个store文件夹新建一个index.js 里面写上一下内容 

```
import Vue from 'vue'
import Vuex from 'vuex'

Vue.use(Vuex)

import moduleA from "./modules/moduleA"
import moduleB from "./modules/moduleB"
export default new Vuex.Store({
  modules: {
    a: moduleA,   
    b: moduleB
  }
})
```

在index.js的同级新建一个modules的文件夹 这个文件夹分别有两个js 分别为 moduleA 和 moduleB 内容分别为以下内容 再在main.js里面引入index.js 这个模块化的写法就已经完成 

```
const moduleA = {   // moduleA
    state: { num:1 },
    mutations: {  
        addNum(state){
            state.num += 2  // 调用的时候执行 this.$store.commit('addNum')
        }
    },
    actions: { 
        syncAddNum(context,val){
            context.commit("addNum",val) // 调用的时候执行 this.$store.dispatch('syncAddNum')
        }
    },
    getters: { 
        addNums(state){
            return state.num + "元 "  // 调用的时候执行 this.$store.getters.addNums
        }
    }
}
export default moduleA

const moduleB = {
    state: { num:2 },
    mutations: { 
        addNum(state){
            state.num += 3
        }
     },
    actions: {  },
    
  }
export default moduleB
```

### 模块化注意点  

1. 对于上面的模块化的写法  只有state是模块化的 其他的诸如 getters mutations actions不是模块化 
2. 如果想实现getters mutations actions实现模块化 那么 得在每个模块的js里面加入 ***命名空间 ***
   `namespaced: true,` 
3. 启用命名空间之后 获取getters mutations actions的写法都要变 

```
const moduleA = {   // moduleA
    namespaced: true,
    state: { num:1 },
    mutations: {  
        addNum(state){
            state.num += 2  // 调用的时候执行 this.$store.commit('a/addNum',3)
        }
    },
    actions: { 
        syncAddNum(context,val){
            context.commit("addNum",val)  // 调用的时候执行 this.$store.dispatch('a/syncAddNum',3)
        }
    },
    getters: { 
        addNums(state){
            return state.num + "元 "  // 调用的时候执行 this.$store.getters['a/addNum2']
        }
    }
}
export default moduleA

const moduleB = {
    namespaced: true,
    state: { num:2 },
    mutations: { 
        addNum(state){
            state.num += 3
        }
     },
    actions: {  },
    
  }
export default moduleB
```

4. 启用命名空间后辅助函数 mapState mapGetters mapMutations mapActions 的写法

- 启用命名空间后的mapState的写法 

```
...mapState({
    a1: state => state.b.num,  
}),
```

- 启用命名空间后的mapGetters的写法 

```
 ...mapGetters({
    a2: "b/addNum1"
}),
```

- 启用命名空间后的mapMutations的写法 

```
 ...mapMutations({event : "b/addNum"})  // this.event(3) 附带参数的写法 
```

- 启用命名空间后的mapActions的写法 

```
...mapActions({events : "b/syncAddNum"}),  // this.events(4) 附带参数的写法 
```

### 监听路由变化执行动画效果 

```js
<script>
  watch: {
    "$route":function (to,from) {
      var toPath  = to.fullPath.split("/").length;
      var fromPath  = from.fullPath.split("/").length;
      console.log("toPath",toPath,"fromPath",fromPath);
      if(toPath>fromPath) { // 进入某个内页
        this.classname = "fadeInRight animated"
      }else if(toPath<fromPath){ // 离开内页
        this.classname = "fadeInLeft animated"
      }else{
        this.classname = "fadeIn animated"
      }
      // if(to.name == "info"){
      //   this.classname = "fadeInRight  animated"
      // }else{
      //   this.classname = "fadeInLeft  animated"
      // }
    }
  }
</script>
```