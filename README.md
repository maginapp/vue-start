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
               