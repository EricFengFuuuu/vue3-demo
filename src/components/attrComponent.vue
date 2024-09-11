<template>
    <!-- 单个元素为根元素才生效 -->
    <p>透传属性</p>
</template>

<script>

export default{
    //禁用属性传递
    inheritAttrs: false,
}

</script>


<style>
.attr{
    font-size: 20px;
    color: red;
}
</style>