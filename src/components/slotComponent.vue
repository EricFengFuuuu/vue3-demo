<template>
    <h4>插槽子组件</h4>
    
    <!-- 插槽 -->
    <!-- <slot>默认内容</slot> -->

    <!-- 具名插槽 -->
    <slot name="slot1">插槽1</slot> 

    <slot name="slot2">插槽2</slot>

    <slot  msg="hello1">默认内容</slot>

    <slot name="slot3" msg="hello">默认内容</slot>
    
</template>

<script>
export default{
    
    data(){
        return{
            content:"子组件内容"
        }
    },


}
</script>