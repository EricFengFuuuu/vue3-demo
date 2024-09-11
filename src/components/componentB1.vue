<template>
    <div>
        <h4>组件B1</h4>

    <!-- <button @click="$emit('myevent', 5)">传递数据给父组件1</button>
    <button @click="clickHandle">传递数据给父组件2</button> -->

    <!-- <input type="text" v-model="inputValue"> -->

    
        <p>{{ title }}</p>
        <p>{{ onFun("函数传递") }}</p>
    </div>


    


</template>

<script>
export default{

    // 声明自定义事件
    emits:['myevent', 'inputEvent'],

    // emits:{
    //     // 自定义事件(校验)
    //     myevent:(data) => {
    //         return data > 0;
    //     }
    // },


    data(){
        return{
            inputValue:''
        }
    },

    props:{
        title:String,
        onFun:Function
    },

    watch:{
        inputValue(newValue, oldValue){
            console.log(oldValue);
            console.log(newValue);
            console.log(this.inputValue);
            this.$emit("inputEvent", this.inputValue);
        }
    },

    methods:{

        // 传递数据给父组件
        clickHandle(){
            // 触发自定义事件
            console.log(111);
            this.$emit('myevent', 1);
        },

    }


}

</script>