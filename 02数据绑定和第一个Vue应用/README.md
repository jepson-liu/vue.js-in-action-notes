### Vue实例与数据绑定
#### Vue实例与数据
el是不可少的属性，它用于指定一个页面中已存在的DOM元素来挂载Vue实例。它可以是HTMLElement(document.getElementById('app')),也可以是CSS选择器（#app）。挂载成功后，可以通过app.$el访问该元素。
通过Vue实例的data属性，可以申明应用内需要双向绑定的数据。建议所有会用到的数据都预先在data内申明，实现统一管理。
除了显示的声明数据外，还可以指向一个已有的变量，并且他们之间默认建立了双向绑定。当修改其中任意一个时，另外一个也会发生变化。
#### Vue生命周期
![生命周期](lifecycle.png)
```vue
        var app=new Vue({
            el:'#app',
            data:{
                a:2
            },
            beforeCreate() {
                console.log("在实例初始化之后，数据观测 (data observer) 和 event/watcher 事件配置之前被调用")
            },
            created() {
                console.log("在实例创建完成后被立即调用。")
            },
            beforeMount() {
                console.log("在挂载开始之前被调用：相关的 render 函数首次被调用。")
            },
            mounted() {
                console.log("实例被挂载后调用，这时 el 被新创建的 vm.$el 替换了。 如果根实例挂载到了一个文档内的元素上，当mounted被调用时vm.$el也在文档内。")
            },
            beforeUpdate() {
                console.log("数据更新时调用，发生在虚拟 DOM 打补丁之前。这里适合在更新之前访问现有的 DOM，比如手动移除已添加的事件监听器。")
            },
            updated() {
                console.log("由于数据更改导致的虚拟 DOM 重新渲染和打补丁，在这之后会调用该钩子")
            },
            beforeDestroy() {
                console.log("实例销毁之前调用。在这一步，实例仍然完全可用。")
            },
            destroyed() {
                console.log("实例销毁后调用。该钩子被调用后，对应 Vue 实例的所有指令都被解绑，所有的事件监听器被移除，所有的子实例也都被销毁。")
            },
        })
```
#### 插值和表达式
使用双大括号（Mustache 语法）“{{}}”是最基本的插值语法，它会自动把双向绑定的数据实时显示出来。
Vue只支持单个表达式，不支持语句、控制流；不能使用用户自定义的全局变量，只能使用Vue白名单的全局变量（如：Date,Math）
#### 过滤器
Vue.js支持在{{}}的插值尾部添加一个管道符“|”对数据过滤。经常用于格式化文本。如日期格式化、币种转换
```vue
//示例
{{date|formatDate}}
//串联
{{amount|fitlerA|fitlerB}}
//接受参数
{{date|formatDate('yyyy-MM-dd hh:mm:ss')}}
```
### 指令与事件
指令（Directives）是Vue.js最常用的一项功能,它带有前缀v-。
+ v-model：
+ v-if：
+ v-show：
+ v-click：
+ v-on：
+ v-pre：
+ v-html：
+ v-text：
+ v-for：
+ v-if：
+ v-else-if：
+ v-else：
+ v-once：
+ v-cloak：
### 语法糖
语法糖是指在不影响某种功能的使用情况下，添加某种方法实现同样的效果。
```vue
//v-bind指令可以省略v-bind，直接使用:
<a v-bind:href="url">百度</a>
<a :href="url">百度</a>
//v-on指令可以直接用@缩写替代
<button v-on:click="doToggle">点击切换显示</button>
<button @click="doToggle">点击切换显示</button>
```