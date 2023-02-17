# Vue 基础
* 一套用于构建用户界面的渐进式框架，被设计为自底向上逐层应用。

 * 渐进式:声明式渲染->>>组件系统component->>>客户端路由router->>>状态管理库vuex->>>构建工具(webpack)

   * 声明式渲染:核心是允许采用简洁的模板语法(v-bind，v-model，插值语法{{变量}})来声明式地将数据渲染进DOM的系统
   * 组件系统: 将UI划分为独立的、可重用的部分。组件常常被组织成层层嵌套的树状结构。
   * 路由router: 将组件映射到路由上，让vue-touter知道在哪里渲染。构建单页面应用SPA
   * 状态管理库vuex:应用集中式储存管理应用的所有组件的状态，数据共享通用

 * 自底向上
   
   * 就是对渐进式的解释，代码先简单后逐渐复杂
   
* 采用组件化模式,提高代码复用率、且让代码更好维护
   * 组件分为全局注册跟局部注册

* 声明式编码(v-bind,v-model,{{}}),让编码人员无需直接操作DOM,提高开发效率

* 使用虚拟DOM+Diff算法,尽量复用DOM节点

## new Vue({options})

* el:"#id"    // el指定当前Vue实例为哪个容器服务,值通常为css选择器字符串
* data:{}     // data用于存储数据,数据供el所指定的容器去使用
* methods:{}      // 方法
* computed:{}      // 计算属性
* watch:{}         // 监视属性
* directives:{}   // 自定义指令配置
* props:[]/{}    // 让组件接收外部传过来的数据
* minixs:[]     // 定义混入
## 语法
### 模板语法
* 指令语法 v-for v-if v-bind v-model 等
* 插值语法 {{变量/js表达式}}
### 数据绑定
* 单向数据绑定:v-bind:value="变量 js表达式"  简写:value=""   从data流入页面
* 双向数据绑定:v-model:value="变量 js表达式" 简写v-model=""  双向,只能用于表单元素 因为只有表单元素有value属性，才能页面流向data
### el与data的两种写法
* el:'css选择器'     vue实例对象.$mount('css选择器')    mount:挂载
* data:{}  对象式    data(){return{数据}} 函数式 不能使用箭头函数因为它的this指向window
### MVVM模型
* M:模型(model) 对应data中的数据
* V:视图(View)  模板
* VM:视图模型(ViewModel)  ==> DOM Listen(由视图--->模型) 和 Data Bindings(由模型--->视图)         Vue实例对象
* vue的实例对象  一般称为vm
* data中所有的属性,最后都出现在了vm身上
* vm身上所有的属性以及Vue原型上所有属性,在Vue模板中都可以直接使用
### Object.defineProperty
* Object.defineProperty(对象名,属性名,{配置项:value:值,enumerable:true(控制属性是否可以枚举),writable:true(控制属性是否可以被修改),configurable:true(控制属性是否可以被删除)})给对象添加属性  添加的属性不可以枚举(遍历)
* 高级配置项
  * get(){return 变量}}  // 当有人读取对象的值,get函数(getter)会被调用，返回的就是该对象属性的值
  * set(value){变量 = value}  // 当有人修改对象的值时,set函数(setter)会被调用,且会收到修改的具体的值   
* 枚举(遍历)
### 数据监测
#### 监测对象中的数据，通过Observer提供的setter
* 通过 Observer构造函数，实行对数据的监测  原理使用 监测对象,用keys方法换为数组，然后遍历添加gette setter，setter监测数据的变化
#### 监测数组中的数据，调用原生对应的方法对数据进行更新，重新解析模板
* 在Vue中修改数组，使用API  push()、pop()等   是vue重新封装的方法
*  或者直接使用 Vue.set()  Vue.$set()
### Vue.set(data中的属性名,属性值名,属性值)
* 向响应式对象中添加一个property,并确保这个新property同样是响应式,且触发视图更新，必须用于向响应式对象上添加新property
### 数据代理
* 通过一个对象代理对另一个对象中属性的操作(读/写)
* 更加方便的操作data中的数据
* 基本原理
 * 通过Object.defineProperty() 把data对象中所有属性添加到vm上
 * 为每一个添加到vm上的属性,都指定一个getter/setter
 * 在getter/setter内部去操作(读/写)data中对应的属性
* 配置项中data数据 赋值给vue._data。  vm对_data通过setter getter进行数据代理 
### 事件的基本使用
* 使用v-on:xxx 或 @xxx 绑定事件,其中xxx是事件名
* 事件的回调需要配置在methods对象中,最终会出现在vm上
* methods中配置的函数，不要使用箭头函数，this会变
* methods中配置的函数，都是被vue所管理的函数，this的指向是vm 或者  组件实例对象
* @click="demo" 和 @click = "demo($event)"  效果一致,后者可以传参
### 事件的修饰符
* 事件.prevent:阻止默认事件
* 事件.stop:阻止事件冒泡
* 事件.once:事件只触发一次
* 事件.capture:使用事件的捕获模式
* 事件.self:只有event.target是当前操作的元素才触发事件
* 事件.passive:事件的默认行为立即执行，无需等待事件回调执行完毕
### 键盘事件
* 回车==>enter
* 删除==> delete
* 退出==> esc
* 空格==> space
* 换行==> tab
* 上==> up
* 下==>down
* 左==>left
* 右==>right
### 计算属性
* 定义:要用的属性不存在，要通过已有属性计算得来
* 原理:底层借助了Object.defineproperty方法提供的getter和setter
* get函数什么时候执行
 * 初次读取时会执行一次
 * 当依赖的数据发生改变时会再次调用
* 优势:与methods实现相比，内部有缓存机制，效率高，方便调试
* 计算属性最终会出现在vm身上，直接读取即可
* 如果计算属性要被修改，必须写set函数去响应修改，且set要引起计算时依赖的数据发生改变
* 不考虑修改的时候 使用简写  计算属性(){return 值}
### 监视属性
* 当被监视的属性变化时，回调函数自动调用，进行相关操作
* 监视的属性必须存在，才能监视
* 监视的两种写法
 * new Vue时传入watch配置    监视属性:{handler(){},immediate:true.....,deep:true 深度监视} 
 * 通过vm.$watch(监视属性,{配置项})
* 深度监视
 * Vue中的watch默认不检测对象内部值的改变
 * 配置deep:true可以监测对象内部值改变
* 简写形式
 * 配置项只有handler的时候   监视属性(oldValue,newValue){}
### computed与watch的区别
* computed能完成的功能，watch都能完成
* watch能完成的功能，computed不一定能完成   watch可以进行异步操作
* 所有被vue管理的函数要写成普通函数，不被Vue管理的函数(定时器的回调函数、ajax的回调函数)最好写成箭头函数这样this才是vm
### 绑定样式
#### 绑定class样式
* 字符串写法  v-bind:class='字符串'/ :class='字符串'    适用于:样式的类名不确定，需要动态指定
* 数组写法  v-bind:class='data中配置的数组'/ :class='data中配置的数组'    data(){reutrn{数组名:[类名1,类名2]}   适用于:样式的个数不确定、名字不确定
* 对象写法  v-bind:class='data中配置的对象'/ :class='data中配置的对象'    data(){reutrn{对象名:{类名1:true/false}}} 适用于:样式的个数、名字确定，决定用不用
#### 绑定style样式
* :style="{fontSize:xxx}" 其中xxx是动态值
* :style="[a,b]"   其中a、b是样式对象
### 条件渲染
#### v-if
* v-if="表达式"
* v-else-if="表达式"
* v-else="表达式"
* 适用于:切换频率低
* 特点:不展示DOM元素直接移除
* v-if v-else-if v-else 要一起使用，结构不能乱
#### v-show
* v-show="表达式"
* 适用于:切换频率较低的场景
* 特点: 不展示的DOM元素直接被移除
* 注意:v-if的元素可能无法获取到，v-show的一定可以
### 列表渲染
#### v-for指令
* 用于展示列表数据
* v-for="(item,index) in xxx" :key="xxx"
* 可遍历:数组、对象、字符串、指定次数
### key的内部原理
#### 虚拟DOM中key的作用
* key是虚拟DOM的标识,当数据发生改变时，Vue会根据新数据生成新的虚拟DOM
* 随后Vue进行新虚拟DOM与旧虚拟DOM比较
#### 对比规则
* 旧虚拟DOM中找到了与新须弥DOM相同的key
 * 若虚拟DOM中内容没变，直接使用原先的真实DOM
 * 若虚拟DOM中内容改变了,则生成新的真实DOM,随后替换掉页面中之前的真实DOM
* 若虚拟DOM中未找到与新虚拟DOM相同的key
 * 创建新的真实DOM,随后渲染到页面
#### 用index作为key引发的问题
* 若对数据进行:逆序添加、逆序删除等破坏顺序操作
* 如果结构中包含输入类的DOM
#### 开发中如何选择key？
* 最好使用每条数据的唯一标识作为key
* 如果不存在逆序添加等破坏顺序操作，仅用于渲染列表可以使用index作为key
### Vue检测数据的原理(setter函数)  暂时略过
* Vue.set(target,属性名,值)
* 向响应式对象中添加一个property同样是响应式的，且触发视图更新。它必须用于
### 收集表单数据
* 若 input type="text"  则v-model收集的value值,用户输入的就是value值
* 若 input type="radio" 则v-model收集的是value值,且要给标签配置value值
* 若 input type="checkbox"
 * 没有配置input的value属性，那么收集的就是checked(勾选/未勾选,是布尔值)
 * 配置input的value属性
  * v-model的初始值是非数组，那么收集的就是checked(勾选/未勾选 是布尔值)
  * v-model的初始值是数组。那么收集的就是value组成的数组
* v-model的三个修饰符:lazy:失去焦点再收集数据   number:输入字符串转为有效的数字  trim:输入首尾空格过滤
### 过滤器
* 对要显示的数据进行特定格式化后再显示
* 语法
 * 注册过滤器:Vue.filter(name,callback)或 new Vue({filters:{}})
 * 使用过滤器:{{xxx |过滤器名}}  或 v-bind:属性 = "xxx | 过滤器名"
### 内置指令
* v-bind: 单向数据绑定解析表达式，可简写为 :xxx
* v-model: 双向数据绑定     v-model=""
* v-for: 遍历数组/对象/字符串
* v-on: 绑定事件监听、可简写为@
* v-if: 条件渲染(动态控制节点是否存在)
* v-show: 条件渲染(动态控制节点是否展示)
* v-text:向其所在的节点中渲染文本内容。 v-text会替换掉节点中的内容，{{xxx}}则不会
* v-html:会替换掉节点中所有的结构,可以识别html结构   有安全问题
* v-cloak(没有值):本质是一个特殊属性，Vue实例创建完毕并接管容器后，会删掉v-cloak属性  使用css配合v-cloak可以解决网速慢页面展示{{xxx}}的问题
* v-once: v-once所在节点初次动态渲染后，视为静态内容。以后数据的改变不会引起v-once所在结构的更新，可以用于优化性能
* v-pre: 跳过其所在节点的编译过程。可利用它跳过:没有使用指令语法、没有使用插值语法的节点、会加快编译
### 自定义指令
* 定义语法
 * 局部指令: directives:{指令名:配置对象}  directives{指令名:回调函数}
 * 全局指令: Vue.directive(指令名,配置对象)  Vue.directive(指令名,回调函数)
* 配置对象三个回调函数
 * bind:指令与元素成功绑定时调用
 * inserted: 指令所在元素被插入页面时调用
 * update: 指令所在模板结构被重新解析时调用
* 备注
 * 指令定义时不加v-，但使用时要加v-
 * 指令名如果是多个单词，要用kebab-case命名方式，不要用camelCase命名
### 生命周期:
* 生命周期回调函数、生命周期函数、生命周期钩子
* Vue在关键时刻帮我们调用的一些特殊名称的函数
* 生命周期函数的名字不可更改，但函数的具体内容是程序员需求编写的
* 生命周期函数中的this指向vm或组件实例对象

* 常用的生命周期钩子
 * mounted:发送ajax请求、启动定时器、绑定自定义事件、订阅消息等[初始化操作]
 * beforeDestory: 清除定时器、解绑自定义事件、取消订阅消息等[收尾工作]

* 关于销毁Vue实例
 * 销毁后借助Vue开发者工具看不到任何信息
 * 销毁后自定义事件会失效，但原生DOM事件依然有效
 * 一般不会再beforeDestory操作数据，因为即便操作数据，也不会再触发更新流程

### 组件
* 用来实现局部(特定)功能效果的代码集合
* 复用编码，简化代码项目，提高运行效率

* 组件本质上是一个名为VueComponent的构造函数，且不是程序员定义的,是由Vue.extend生成的
* 我们只需要写<组件名>,Vue解析时会帮我们创建组件的实例对象，即执行new VueComponent(options)
* 每次调用Vue.extend 返回的都是一个全新的VueComponent

* this指向
 * 组件配置中 函数指向vc(组件的实例化对象)
 * new Vue({})  配置函数指向Vue

* 内置关系   VueComponent.prototype.__proto__ = Vue.prototype
* 让组件实例化对象(vc) 可以访问到Vue原型上的属性、方法


## 注意点
* Vue工作,通过new创建一个Vue实例,并传入一个配置项-0
* root容器里的代码被称为[vue模板]
* vue实例和容器是一一对应的
* {{xxx}} xxx用js表达式(变量、函数、运算),且xxx可以自动读取到data中的所有属性
* 一旦data中的数据改变,模板中用到该数据的地方也会自动更新

# Vue脚手架等相关api
## 脚手架
* npm i -g @vue/cli  下载脚手架
* 创建 vue create 项目名
* npm run 名字 启动脚手架

## render
* 字符串模板的代替，将APP渲染到容器中

## ref属性
* 被用来给元素或子组件注册引用信息(id的替代者)
* 应用在html标签上获取的是真实DOM元素，应用在组件标签上是组件实例对象(vc)
* 使用方式:
 打标识:<h1 ref="xxx">。。。</h1> 或 <School ref="xxx"></School>
  获取: this.$refs.xxx

## 配置props
### 传递数据
* <Demo name="xxx"  :age='19'(v-bind绑定值为数值)/>
### 接收数据
* 第一种方式(只接收): props:['name']
* 第二种方式(限制类型): props:{name:String}
* 第三种方式(限制类型、限制必要性、指定默认值): props:{name:{type:String//类型,required:true//必要性,default:'老王'//默认值}}

## mixin(混入)
* 功能: 可以把多个组件共用的配置提取成一个混入对象
* 使用方式: 第一步定义混合,创建一个mixin.js  export const mixin={data(){},methods:{}}
            第二步使用混入,例如:(1).全局混入:Vue.mixin(xxx) (2).局部混入:mixins:['xxx']  import引入下

## 插件
* 功能:用于增强vue
* 本质:包含install方法的一个对象。install的第一个参数是Vue.第二个以后的参数是插件使用者传递的数据
  定义插件:对象.install = function(Vue,option){}    install(){}
         1. 添加全局过滤器
          Vue.filter(...)
         2. 添加全局指令
          Vue.directive(...)
         3. 配置全局混入(合)
         Vue.mixin()
         4. 添加实例方法
         Vue.prototype.$myMethod = funciton(){}
    使用插件 Vue.use(插件,其余参数)

## scoped样式
* 作用: 让样式在局部生效，防止冲突
* 写法: <style scoped lang="css/less">

## 组件的自定义事件
* 组件间通信的方式,适用于:子组件==>父组件
* 使用场景:A是父组件，B是子组件，B想给A传数据,那么就要在A中给B绑定自定义事件(事件的回调在A中)
* 绑定自定义事件: 
  * 第一种:在父组件中: <Demo @atguigu="test"/> 或 <Demo v-on:atguigu="test"/>
  * 第二种:<Demo ref="demo">   mounted(){this.$ref.xxx.$on('atguigu',this.test)}
  * 若想让自定义事件触发一次，可以使用once修饰符，或者用$once方法
* 触发自定义事件:this.$emit('事件名',数据)
* 解绑自定义事件:this.$off('atguigu')
* 组件上也可以绑定原生DOM事件,需要使用native修饰符
* 通过this.$refs.xxx.$on('事件名',回调)绑定自定义事件时，回调要么放methods中，要么用箭头函数，否则this执行会出问题

## 全局事件总线
* 一种组件间通信的方式，适用于任意组件间通信
* 安装全局事件总线   beforecreate(){Vue.prototype.$bus = this(vm)}
* 接收数据: mounted(){this.$bus.$on('事件名',(data)=>{})}
* 发送数据: mounted(){this.$bus.$emit('事件名',数据)}
* 最好在beforeDestory中,用$off去解绑当前组件所用到的事件

## 消息订阅与发布
* 一种组件间通信的方式,适用于任意组件间通信
* 安装pubsub npm i pubsub-js
* 引入: import pubsub from 'pubsub-js'
* 订阅消息: pubsub.subscribe('消息名',回调)
* 发布消息: pubsub.publish('消息名',data)
* beforeDestory中，用PubSub.unsubcribe(订阅消息的名字)取消订阅

## $nextTick(回调函数)
* this.$nextTick(回调函数)
* 作用:在下一次DOM更新结束后执行其指定的回调
* 什么时候使用:当改变数据后,要基于更新后的新DOM进行某些操作时，要在nextTick所指定的回调函数中执行

## 动画(没复习)

## Vue脚手架配置代理
### 在vue.config.js中添加配置
* devServer:{proxy(代理):'url'}
### 编写vue.config.js配置具体代理规则
* devServer:{
  proxy:{
    '/api':{  // 匹配所有以 '/api'开头请求的路径
        target:'url',
        changeOrigin:true(是否撒谎跨域),
        pathRewrite('^/api':'') 正则匹配替换
    }
  }


}

## 插槽
* 让父组件向子组件指定位置插入html结构，也是一种组件间通信的方式,适用于父组件===>子组件
### 默认插槽
* 在组件标签中嵌套<Student><img src=""/></Student>
* 在组件中写入<slot></slot> 占位 img会在此渲染
### 具名插槽
* 在组件标签中嵌套<Student><img slot="插槽名" src=""/></Student>
* 在组件中写入<slot name="插槽名"></slot> 占位 img会在此渲染
### 作用域插槽
* 数据在组件自身，但根据数据生成的结构需要组件的使用者来决定(games数据在Category组件中,但使用数据所遍历出来的结构由App组件决定)
* 在组件标签中嵌套<Category>
                        <template slot='scopeData'>
                                <ul><li></li></ul>
                             </template>
                            </Category>
* 子组件中   <div><slot :game="game"><slot></div>

## Vuex
* 在Vue中实现集中式状态(数据)管理的一个Vue插件,对vue应用中多个组件的共享状态进行集中式的管理,也是一种组件间通信的方式,且适用于任意组件通信
### 搭建Vuex
* npm i vuex@3
* 创建vuex文件夹/index.js
* 引入Vue
* 引入Vuex
* Vue.use(vuex)
* 创建三个配置项 
* const actions = {}  // 响应组件中的动作   动作名(context,value){context.commit('mutations方法名',value)}
* const mutations={}  // 修改state中的数据  mutations方法名(state,value){处理数据}
* const state = {}    // 储存数据  
* const getters = {}   // 计算属性(state){return}         
* 创建vuex实例   const store = new Vuex.Store({actions,mutations,state,getters})
* 暴露store    export default store

### 引入vuex
* import store from './vuex'
* 注册 store

### vuex方法基本使用
* 方法名(){this.$store.dispatch('动作名',值)}
* 方法名(){this.$store.commit('动作名',值)}

### mapAction mapMutation mapGetters mapState
* ...mapAction({方法名:"Action中的方法名"})  // 对象式
* ...mapAction(['Action中的方法名'])    //  数组式

### 模块化+命名空间
* const countAbout ={ namespaced:true//开启命名空间,state:{},mutations:{},actions:{},getters:{}}
* const personAbout ={ namespaced:true//开启命名空间,state:{},mutations:{},actions:{},getters:{}}
* export default new Vuex.Store({module:{countAbout,personAbout}})

* ...mapState('countAbout',{}/[])
* ...mapState('personAbout',{}/[])
* ...mapActions('countAbout/方法名',值)

* 理解: 有方法的对象用  模块名/方法名  没属性的对象用 ('模块名',{}/[])

## vue-router
* 一个路由(route)就是一组映射关系(key-value),多个路由需要路由器(router)进行管理
* 前端路由:key是路径,value是组件

### 搭建VueRouter
* npm i vue-router@3
* 创建router文件夹/index.js
* 引入 Vue 
* 引入 VueRouter
* 注册插件Vue.use(VueRouter)
* export default new VueRouter({
      routes:[
        {path:''   // 父路径  /路径名
         component:,
         children:[
           {
             path:''   // 子路径 直接路径名
             component:
           }
         ]
        }
      ]
  })
* main.js 引入VueRouter  注册router
### 入口使用
#### query参数的to写法
* <router-link to="/父路径/(子路径)?query参数名=query值&query参数名=query值"><router-link>
* <router-link :to="`/父路径/(子路径)?query参数名=${变量}&query参数名=${变量}`"><router-link>
#### query参数的对象写法
* <router-link :to="{path:'',query:{key:value}}"><router-link>
* <router-link :to="{name:'',query:{key:value}}"><router-link>
#### params参数的to写法
*  <router-link to="/父路径/(子路径)/params值/params值"><router-link>
*  <router-link to="`/父路径/(子路径)/params值${}/`"><router-link>
* 对应路径需要配置 path:"路径名/:params名/:params名"
#### params参数的对象写法
* <router-link :to="{name:'',params:{key:value}}"><router-link>
*  使用params  to 的对象写法必须使用name 不能使用path
#### 路由props配置传参
* 对象写法: props:{a:1,b:'三'}    对应路由组件配置props:['a',''b]
* 布尔值写法: props:true   仅用于params参数   对应路由组件配置props['params名'] / $route.params.名
* 函数写法: props(route){return {id:route.params.名}}  / props(route){return {id:route.query.名}} 

### 接收参数
* $route.params.名
* $route.query.名

### router-link 的 push合replace属性
* push是追加历史记录(倒退可以指针一步一步倒退)
* replace是替换当前记录(直接倒退到最初始)

### 编程式路由导航(不借助router-link)
* this.$router.push({name:'',query/params})
* this.$router.replace({name:'',params})
* this.$router.forward() // 前进
* this.$router.back()  // 后退
* this.$router.go(数值可正可负)  // 可前进可后退  看数字多少

### 缓存路由组件
* <keep-alive include="缓存的路由组件名"> <router-view></router-view></keep-alive>   缓存一个
* <keep-alive :include="[缓存的路由组件名,缓存的路由组件名2]"> <router-view></router-view></keep-alive>   缓存多个

### 两个新的生命周期钩子
* 路由组件独有的2个钩子,用于捕获路由组件的激活状态
* activated(){}   路由被激活时触发
* deactivated(){}  路由组件失活时触发

### 路由守卫
#### 全局前置路由守卫
* router.beforeEach((to,from,next)=>{})    to,from对象中包含重要信息 next()放行
* router.afterEach((to,from,next)=>{})     to,from对象中包含重要信息 next()放行
#### 独享守卫
* 在对应的路由里配置 beforeEnter(to,from,next){}
#### 组件内守卫
* 在对应组件中配置，配置项 beforeRouteEnter(to,from,next){}
* 在对应组件中配置，配置项 beforeRouteLeave(to,from,next){}

## 路由的两种工作模式
* hash值   /#/     不美观，兼容性好
* history  / /    地址干净 兼容性不好

## Vue的生命周期
* beforeCreate   无法访问data中的数据、methods中的方法       初始化:生命周期、事件，数据代理未开始
* Create         可以访问到data中的数据、methods中的方法     初始化:数据监测、数据代理
* beforeMount    页面呈现的是未经vue编译的DOM结构，所有对DOM的操作都不奏效。     解析模板生成虚拟DOM，页面还不能显示
* Mount          页面呈现的是经过Vue编译的DOM,开启定时器发送ajax请求            将内存中的虚拟DOM转换为真实DOM插入页面
* beforeUpdate   数据是新的，但是页面是旧的，页面尚未和数据保持同步
* updated        数据是新的，页面也是新的，页面和数据保持同步
* beforeDestory  vm中的data、methods、指令都可以使用，马上执行销毁流程。关闭定时器、取消订阅消息、解绑自定义事件
* destroyed


# VueAPI
## 全局API
* Vue.extend({options})     // 创建Vuecomponent
* Vue.nextTick(function)   //  在同一个事件处理函数中，如果其中有dom发生改变，并想在dom发生改变后处理一些事情，则需要使用this.$nextTick/Vue.nextTick
* Vue.set(target,propertyName,value)  // 向一个响应式对象中添加新的数据，如果直接添加 this.myobject.newPropertyName = 'newValue'  这个时候不能触发视图更新，不能将此数据纳入到响应式对象中。  需要使用Vue.set()   只能往事先预设好的根数据对象里的 object/array 里面添加响应式数据  
* Vue.component([string组件的名字],组件)        注册全局组件
* Vue.use([object||function])       安装Vue插件，如果插件是一个对象，其里面要有install方法; 如果插件是一个函数，会被当做install方法调用
* Vue.mixin([object])    全局注册一个混入

## 选项配置属性
* data:组件中必须使用函数形式(因为组件会被复用，如果使用对象形式，多个相同组件会操作同一个对象)  数据代理、数据劫持
* props: 用于父给子传参  props的类型有 数组Array、对象{属性名:type(String/Number等)}、对象{属性名:{type,default,required,validator}}
* propsData:只用于Vue实例  不常用
* computed:计算属性 object 里面有两个方法 get(初次读取计算属性会调用,所依赖数据发生变化时会被调用) 和 set   如果只使用get  可简写为 计算属性名(){return xxxx}
           计算属性有缓存，当使用多次 get只调用一次
* methods:object    里面是众多的方法
* watch: object  data中存在的属性:{immediate 立即监视  deep 深度监视  handler(newvale,oldvalue{})}  如果不需要配置项可以简写  监视属性名(){}

# Vue其它功能
* mixins混入  全局混入、局部混入   将有相同需求的放到一起
* 插件plugin 两种类型:第一种对象 const plugin = {install(Vue){}}  一定要有install方法  第二种函数 function plugin(Vue){}   
   使用 Vue.use(plugin)  函数注入会自动定义为 install(Vue)
* 插槽:默认插槽、具名插槽slot、作用域插槽scope
# Vue思考
## 响应式数据
* 简单理解就是 代码数据发生改变，界面数据发生改变，界面数据发生改变，代码数据发生改变。
* 实现的API是  Object.defineProperty(对象,propertyName,{get(){},set(){}})
* 数据代理:使data中的众多属性可以直接在vue中被访问
           在vue代码执行时 会将 data = this._data   这样我们在模板里面可以直接使用 _data.属性名 不方便
           于是借助数据代理   将vue._data 中的数据 代理到vue自身   Object.defineProperty(vue,propertyName,{get(){}}) 
           于是可以直接访问 想要的属性名， 不用再使用_data.属性名
* 数据劫持:使用data中的所有属性都进行响应式处理
           就是将data中的数据 全部进行响应式处理(在数据代理执行前进行)  通过Object.keys(data) 遍历生成一个包含data中所有属性名的数组
           然后使用forEach()  为每个属性添加响应式  借助Object.defineProperty
## 数据双向绑定
* vue是数据双向绑定的框架， 它主要参考了MVVM模型。这个框架由三部分组成(M:model模型数据 V:view视图 VM:视图模型)
* ViewModel(vm)数据变化后更新视图，视图变化后更新数据
* vm由两部分组成:监听器Observer 对所有数据进行响应式处理 和 解析器Compiler 跟踪解析模板指令 更新替换数据
* Observer:为data中所有数据添加响应式  关注model层数据
* Compile: 为解析模板中所有v-bind、v-model、插值语法进行数据绑定(多添加一个v-bind我就多编译绑定一个)
* Dep: 管理data中所有的属性  一个dep管理一个key  一个key可能会在多个地方使用 
* Watcher:每个watcher负责管理一个模板中的key 一个key会被多次使用
* updater:当view数据发生变化 或者model中数据发生变化，都会执行updater函数
