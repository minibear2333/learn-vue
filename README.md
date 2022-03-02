 vue学习备忘

### 基础知识

* 模板 `template` 也可直接在`id=root`里写，会自动识别为 `template`
* 变量-差值表达式 `{{变量}}` 

```js
        data() {
            return {
                content: 1
            }
        },
        template: '<div>{{content}}</div>'
```

* [监听某个变量](2.base/6.html)，变化时触发函数体异步操作

```js
watch:{ 
    变量(curr,prev){

    }
    }
```

* 样式绑定，使用变量的方式定义样式类、组件样式类引用，行内样式 [示例](2.base/7.html)
  * 绑定变量简写方式 `:style="styleObject"`
  * 绑定对象作为样式 `:style="styleObject"`
  * 绑定`class`变量作为样式 `:class="classArray"`
  * 子组件样式覆盖，或者复用父组件传递样式 `<demo class="green"/>`
* `v-if v-else-if v-else`  `v-show` [示例](2.base/8.html)
* 数组和对象的操作 
  * 数组的变更函数`push pop unshift shift splice sort reverse`
  * `for`循环数组或对象的方式
  * `template` 占位符，替代`for`的标签，防止空`div` 
  * [示例](2.base/9.html)
* 事件修饰符  `stop,prevent,capture,self,once,passive` [示例](2.base/10.html)
  * `.stop` 屏蔽事件冒泡
  * `.prevent` 阻止默认行为 
  * `.capture` 按捕获模式，相当于反冒泡，用的比较少 
  * `.once` 事件绑定只执行一次
  * `.passive` 提升性能，以后再了解
* 按键修饰符：`enter,tab,delete,esc,up,down,left,right` 
  * 鼠标修饰符：`left,right,middle`
  * 精确修饰符：`exact` 精确的仅按住ctrl再鼠标点击才生效，如果没有exact的话只要按住ctrl和鼠标点击，同时任意按住其他按键也生效
  * 示例按键：`@keydown.enter="handleKeyDownByEnter"`
  * 示例鼠标：`@click.right="handleClick"`
  * 示例精确：`@click.ctrl.exact="handleClick"`
  * [示例](2.base/11.html)
* 表单元素的各种绑定数据，和生成表单内容的方式 `input,textarea,checkbox,radio,select` [示例][12.html]

### 组件

组件（注意绑定顺序，`props` 传入属性值当参数）[10.html](10.html)

```js
    app.component('todo-item', {
        // 接收属性值，相当于参数
        props: ['content', 'index'],
        template: '<li>{{content}} -- {{index}}</li>'
    });
    // 要挂载的节点，注意有组件的方式需要最后挂载组件
    app.mount('#root');
```

### 生命周期

加载后执行-mounted 

```js
        // after 事件，函数
        // 在实例生成之前 会自动执行的函数
        beforeCreate() {
            console.log('beforeCreate')
        },
        // after 数据、模板、双向绑定
        // 在实例生成之后 会自动执行的函数 
        created() {
            console.log('created')
        },
        // after template编译成函数
        // 在组件内容被渲染到页面之前 会自动执行的函数
        beforeMount() {
            console.log('beforeMount')
        },
        // after vue对象 挂载到页面上
        // 在组件内容被渲染到页面之后  会自动执行的函数
        mounted() {
            console.log('mounted')
            this.message = 'abc' // 为了触发 beforeUpdated
        },
        // after  update data,but before update html
        // 当 data 中的数据发生变化时执行的函数
        beforeUpdate() {
            console.log('beforeUpdated', document.getElementById('root').innerHTML)
        },
        // 当 data 中的数据发生变化，同时页面完成更新后，会自动执行的函数
        updated() {
            console.log('updated', document.getElementById('root').innerHTML)
        },
        // app.unmount()
        // 当 Vue 应用失效时，自动执行的函数
        beforeUnmount() {
            console.log('beforeUnmount', document.getElementById('root').innerHTML)
        },
        // 当 Vue 应用失效时，且 dom 完全销毁之后，自动执行的函数
        unmounted() {
            console.log('unmounted', document.getElementById('root').innerHTML)
        },
```

### 常用函数

[示例](2.base/3.html)
* `v-html` 变量中的`html`不转义，嵌入
* `v-once` 一次性执行渲染，后面改变也不刷新
* `v-if` 直接移除`dom`的方式，是否屏蔽
* `v-show` `display:none`的方式，是否屏蔽
* `v-bind` 绑定变量到某个属性中
* `@click` 函数调用简写
* `@[event]="handleClick" :[name]="message"` 动态参数、动态属性、动态事件，使用变量来改变事件状态
* `@click.prevent="handleClick"`  阻止默认行为，并使用业务函数逻辑
* `v-model` 标签内容双向绑定

函数不仅可以`v-bind`也可以在差值表达式中使用 [4.html](4.html) 如果要触发多个函数，用逗号隔开

[计算函数](2.base/5.html) `computed:{ xxx(){ return xx * xx }}`，自动刷新  计算属性依赖的内容发生变更时才会重新计算  


