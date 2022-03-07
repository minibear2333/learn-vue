lesson3 组件
* 组件的定义、复用性 [示例](1.html)
  * 全局组件`app.component('counter', {});`
  * 组件的包含 

```js
app.component('counter-parent', {
        template: `<counter/>`
    });
```
* 局部组件`const HelloWorld = {}` [示例](3.html)
  * 局部组件要注册才能用
  * 命名方式：全局组件使用 `xx-xx` 的方式，局部组件使用 驼峰 的方式
```js
const app = Vue.createApp({
        // 局部组件的使用方式，不用的时候就是一个变量，性能好，但是要注册了才能使用
        components: { HelloWorld },
        template: `
        <div>
            <hello-world/>
            <HelloWorld/>
        </div>`
    });
```
* 组件变量的传递，变量的校验
```js
app.component('test', {
    // props: ['content'],
    props: {
        // type: String Boolean Array Object Function Symbol(占位符，不常用)
        // required default
        content: {
            type: String,
            default: '123',
            // default: ()=>{
            //     return '456'
            // },
            required: true,
            validator(value) {
                return value.length > 0
            }
        },
        func: Function
    },

    template: `<div @click="this.func()">{{content}}</div>`
});
```