<template>
    <h4>组件A1</h4>

    <p>{{name}}</p>
    <p>{{age}}</p>

    <p v-for="hoby, index of hobys" :key="index">{{ hoby }}</p>
</template>

<script>


export default{
    data(){
        return{

        }
    },
    props:{
        name:{
            //类型校验
            type:String,
            //默认值
            default:"",
            //必传校验
            required:true

        },
        age:{
            type:[Number, String],
            default:0
        },
        hobys:{
            type:Array,
            default:function(){
                return[]
            }
        }
    }
}

</script>