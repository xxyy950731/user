<template>
  <div>
    <p class="el-icon-user-solid">欢迎您，管理员：{{ ad }}!</p>
  </div>
</template>

<script>
    export default {
        name: "Welcome",
        props:["ad"]
    }
</script>

<style scoped>

</style>
