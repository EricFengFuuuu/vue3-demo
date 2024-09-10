<template>
    <h4>组件B</h4>

    <!-- <componentB1 title="子传父（自定义事件）" @myevent="getHandle" />

    <p>输入内容：{{ inputValue }}</p>
    <componentB1 title="子传父（自定义事件）" @inputEvent="getInputValue"/> -->
    <p>{{ msg }}</p>
    
    <componentB1 :title="'子传父（函数）'" :onFun = "onFun" />
    
</template>

<script>
import componentB1 from './componentB1.vue'



export default {

    components:{
        componentB1
    },

    data(){
        return{
            inputValue:"",
            msg:""
        }
    },
    methods:{
        // 处理子组件传递过来的数据
        getHandle(data){
            console.log("子组件传递过来的数据:"+ data);
        },

        getInputValue(data){
            this.inputValue = data;
        },

        onFun(data){
            console.log(data);
            this.msg = data; 
        }



    }
}
</script>