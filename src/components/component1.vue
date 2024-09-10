<template>
    <div class="component1">
        {{ message }}
    </div>

</template>


<script>

export default {
    data(){
        return{
            message:"我是组件1"
        }
    },
}


</script>

<!-- scoped: 让样式只在当前组件生效 -->
<style scoped>
    .component1{
        color: red;
        width: 100px;
        height: 100px;
    }
</style>