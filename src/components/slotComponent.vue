<template>
    <h4>插槽子组件</h4>
    
    <!-- 无名插槽 -->
    <slot>插槽默认内容</slot>
    <br/>
    <!-- 具名插槽 -->
    <slot name="slot1">111</slot> 
    <br/>
    <slot name="slot2">222</slot>
    <br/>
    <slot name="slot3">333</slot>

    <br/>
    <!-- 作用域插槽 -->

    <slot :code="childContent">hello</slot>
    <br/>
    <slot name="slot4" :code="childContent">444</slot>

</template>

<script>
export default{
    
    data(){
        return{
            childContent:"子组件内容"
        }
    },


}
</script>