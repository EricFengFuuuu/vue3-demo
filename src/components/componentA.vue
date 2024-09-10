<template>
    <h4>组件A</h4>
    <!-- 父组件传递参数给子组件 -->
    <componentA1 :name="name" :age="age" :hobys = "hobys" />
    
</template>

<script>
import componentA1 from './componentA1.vue';

export default{
    components:{
        componentA1
    },
    data(){
        return{
            name:"张三",
            age:18,
            hobys:['唱歌','跳舞', '篮球']
        }
    }
}
</script>