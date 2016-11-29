# vue-start
> study vue
> maginaCp

## 11-24
* 测试

## 11-25
1. remote连接成功
2. 创建vue()对象

        new Vue({ 
            el: '#app', 
            methods: { doSomething: function () { /...../ } } ,
            data: {
                msg: 'my',
                arr: [1,2,4]
            }
        })
2. 02:v-model表单元素的绑定指令
3. 03:v-for 替代了v-repeat  指令
    > 与angular相比，无需考虑数组的值相同导致的bug，angular中需要track by index修复
    > css: [v-cloak] {display:none}   防止加载直接{{}}显示，导致闪屏的问题
4. 04-05 存在bug  v-for  在 普通标签和 table系列标签中的不同

## 11-26
1. 11-25--bug解决
    > tr 标签外缺少table标签原因不明
2. 事件的绑定
    * v-on:事件名（click）='cliclhandler()'
    * @+ 事件名：  @click = 
3. 事件中数据的操作

        eventHandler(){
            //this ??
            //this[变量名]  ==>指向 data中绑定的变量名 
            //双向绑定--对应页面的数据        
        }
4. 过滤器 自定义过滤器

    > 常用 orderBy [param]和filterBy [param]
    > 多个过滤器用 | 隔开    data | orderBy 'name' | uppercase 
    
    * uppercase
    * orderBy
        > [{a:1,b:2},{a:2,b:4},{a:3,b:4}] | orderBy 'a'(可用变量名替代)
    * filterBy
    * 自定义
    
            Vue.filter('过滤器名',function(value){
                //value指代过滤的对象
                return 过滤结果
            })
6. v-if/v-else  v-show    = 'value'
    * value = false  ==> style="display:none"
    * v-if/else 可配合 template标签使用
    * v-show是始终渲染并保持在DOM节点中
5. 其他
   template 标签
   pre 标签
   
7. MD语法
   ``` 行内高亮
   换行+双tab缩进 多行文本
   ```
    
## 11-27
1. vuejs 的计算属性
    > 辅助完成一些复杂的逻辑运算
    > 页面中绑定时  变量值为 ==> 函数执行后的返回值

        new Vue({
            computed:{
                属性名: function fn(){
                    //this.data-key名 -->初始操作的值
                    return value
                }
            }
        })
    > view中绑定方法与methods，data属性  相同   
        
3. data  methods    computed
   * data --> 具体数据
   * methods --> 绑定方法
   * computed --> 处理计算逻辑 （函数自执行，返回值为绑定的值）
     
2. commonjs/CMD(seajs)/AMD(requirejs)
    > ???
    *配合vue.common.js?*
      
            var Vue = require('vue');
            Vue.use(require('vue-resource'));

4. vue-resource插件----AJAX和jsonP
    1. 引用
        * 遵循CommonJS规范如3
        * 直接引用vue-resource包
    2. 用法
        * Vue实例中新增：ready对象，页面加载完成是请求
                    
                this.$http.get(url,callback[data])
                    .error(callback[data,status,request])
                    
                this.$http.post(url,postdata,callback[data])
                     .error(callback[data,status,request])
                
                function callback(data){
                    //'books'  -- data对象的键名
                    this.$set('books', data);
                }
        * post请求头设置 -- Vue实例中添加如下内容
                
                http: { headers: {'Content-Type': 'application/x-www-form-urlencoded'} }
     
## 11-28

1.  “Mustache” 语法（双大括号）
    {{}}纯文本  v-html=‘’ -html格式
2. js简单语法，字符串方法

        <!-- 这是语句，不是表达式 -->
        {{ var a = 1 }}
        <!-- 流控制也不会生效，请使用三元表达式 -->
        {{ if (ok) { return message } }}
        
3. v-bind:属性名
    > Mustache 不能在 HTML 属性中使用，应使用 v-bind 指令：

        v-bind:disabled='false|true'
        v-bind:id='testId'
        
4. 自定义过滤器的另外一种方法    
    > 写在Vue实例内部

        new Vue({
          // ...
          filters: {
            capitalize: function (value) {
              if (!value) return ''
         
              value = value.toString()
              return value.charAt(0).toUpperCase() + value.slice(1)
            }
          }
        })
 
    * 过滤器可以串联：

            {{ message | filterA | filterB }}
    * 过滤器是 JavaScript 函数，因此可以接受参数：
    > 默认已经有了一个默认的参数value

            {{ message | filterA('arg1', arg2) }}        
    > 这里，字符串 'arg1' 将传给过滤器作为第二个参数
    > arg2 表达式的值将被求值然后传给过滤器作为第三个参数。    
    
## 11-29
1. 指令
    * 参数：
    > 一些指令能接受一个“参数”，在指令后以冒号指明  类别与值。
        * v-bind:href='url'
        > 更新HTML元素属性
        * v-on:click='fn'
        > 操作DOM，监听事件
    
    * 修饰符
    > 修饰符（Modifiers）是以`' . '`指明的特殊后缀，用于指出一个指定应该以特殊方式绑定    
    > 例如.prevent 修饰符告诉 v-on 指令对于触发的事件调用 event.preventDefault()
    
            <form v-on:submit.prevent="onSubmit"></form>
            
2. 缩写

* v-bind
        
        v-bind:id='variable'
        :id='variable'
        
* v-on
        
        v-on:mouseover='doneIt'
        @mouseover='doneIt'
         