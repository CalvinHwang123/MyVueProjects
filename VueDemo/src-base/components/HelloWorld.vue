<template>
  <div>
    <p class="msg">{{ msg }}</p>
  </div>
</template>

<script>
  // 暴露一个默认配置对象（与 Vue 对象一致）
  export default {
    data() { // 必须写函数
      return {
        msg: 'Hello Vue CLI'
      }
    }
  }
</script>

<style>
  .msg { background-color: blue; color: brown; }
</style>
