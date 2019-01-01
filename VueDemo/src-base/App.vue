<template>
  <div>
    <img class="logo" src="./assets/logo.png" alt="咯狗" />
    <!--第三步，使用组件标签-->
    <HelloWorld />
  </div>
</template>

<script>
  // 第一步，引入组件
  import HelloWorld from './components/HelloWorld'
  export default {
    // 第二步，映射组件标签
    components: { HelloWorld }
  }
</script>

<style>
  .logo { width: 500px; height: 500px; }
</style>
