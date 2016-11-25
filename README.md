# vue-start
> study vue
> maginaCp

## 11-24
* 测试

## 11-25
1. remote连接成功
2. 创建vue()对象
    ```
    new Vue({ 
        el: '#app', 
        methods: { doSomething: function () { /...../ } } ,
        data: {
            msg: 'my',
            arr: [1,2,4]
        }
    })
    ```
2. 02:v-model表单元素的绑定指令
3. 03:v-for 替代了v-repeat  指令
    > 与angular相比，无需考虑数组的值相同导致的bug，angular中需要track by index修复
    > css: [v-cloak] {display:none}   防止加载直接{{}}显示，导致闪屏的问题
4. 04-05 存在bug  v-for  在 普通标签和 table系列标签中的不同
    



