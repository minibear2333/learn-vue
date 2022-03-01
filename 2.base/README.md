lesson2
* 基础介绍 [1.html](1.html)
* 生命周期管理-自动函数执行顺序 [2.html](2.html)
* 各种函数复习 [3.html](3.html)
  * `v-html` 变量中的`html`不转义，嵌入
  * `v-once` 一次性执行渲染，后面改变也不刷新
  * `v-if` 直接移除`dom`的方式，是否屏蔽
  * `v-show` `display:none`的方式，是否屏蔽
  * `v-bind` 绑定变量到某个属性中
  * `@click` 函数调用简写
  * `@[event]="handleClick" :[name]="message"` 动态参数、动态属性、动态事件，使用变量来改变事件状态
  * `@click.prevent="handleClick"`  阻止默认行为，并使用业务函数逻辑
  * `v-model` 标签内容双向绑定
* 函数不仅可以`v-bind`也可以在差值表达式中使用 [4.html](4.html) 如果要触发多个函数，用逗号隔开
* 计算函数`computed:{ xxx(){ return xx * xx }}`，自动刷新 [5.html](5.html) 计算属性依赖的内容发生变更时才会重新计算
* 监听某个变量，变化时触发函数体异步操作  [6.html](6.html)
  ```js
    watch:{ 
      变量(curr,prev){

       }
      }
  ```
* 样式绑定，使用变量的方式定义样式类、组件样式类引用，行内样式 [7.html](7.html)
  * 绑定变量简写方式 `:style="styleObject"`
  * 绑定对象作为样式 `:style="styleObject"`
  * 绑定`class`变量作为样式 `:class="classArray"`
  * 子组件样式覆盖，或者复用父组件传递样式 `<demo class="green"/>`
* `v-if v-else-if v-else`  `v-show` [8.html](8.html)
* 数组和对象的操作 
  * 数组的变更函数`push pop unshift shift splice sort reverse`
  * `for`循环数组或对象的方式
  * `template` 占位符，替代`for`的标签，防止空`div` 
  * [9.html](9.html)
* 事件修饰符  `stop,prevent,capture,self,once,passive` [10.html](10.html)
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
  * [11.html](11.html)
* 表单元素的各种绑定数据，和生成表单内容的方式 `input,textarea,checkbox,radio,select` [12.html][12.html]