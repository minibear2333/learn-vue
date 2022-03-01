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

```js
<!-- 变量中的html不转义 -->
<div v-html="message"></div>
<!-- 双向绑定,改变一个同时改变 -->
<div v-bind:title="message">hello</div>
<!-- 标签绑定数据 -->
<input v-bind:disabled="disable" />
<input v-model="inputValue"></input>
<!-- 差值表达式中可以写js表达式 -->
<div>{{Math.max(1,2)}}</div>
<!-- 一次性执行渲染 -->
<div v-once>{{message}}</div>
<!-- 变量判定是否显示 -->
<div v-if="show">{{message}}</div>
<!-- 简写形式 -->
<div @click="handleClick" :title="message">{{message}}</div>
<!-- 动态参数、动态属性、动态事件 -->
<div @[event]="handleClick" :[name]="message">
    {{message}}
</div>
<!-- 阻止默认行为，并使用业务函数逻辑 -->
<form action="https://baidu.com" @click.prevent="handleClick">
    <button type="submit">提交</button>
</form>
<ul>
    <li v-for="(item,index) of list">{{item}} {{index}}</li>
</ul>
<ul>
    <li v-for="item of list">{{item}}</li>
</ul>
```






