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
    
    




