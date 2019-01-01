<template>
  <div>
    <header class="site-header jumbotron">
      <div class="container">
        <div class="row">
          <div class="col-xs-12">
            <h1>请发表对 Vue.js 的评论</h1>
          </div>
        </div>
      </div>
    </header>
    <div class="container">
      <Add :addComment="addComment" />
      <!--声明属性，给子组件调用-->
      <List :comments="comments" :removeComment="removeComment" />
    </div>
  </div>
</template>

<script>
  import Add from './components/Add'
  import List from './components/List'
  export default {
    data() {
      return {
        comments: [ // 数据在哪个组件，更新数据的行为就在哪个组件
          { name: 'calvin', content: 'Vue.js 大法好' },
          { name: 'kevin', content: 'Vue.js 不错啊' },
          { name: 'tomcat', content: 'Vue.js 真不错' }
        ]
      }
    },
    methods: {
      addComment(comment) {
        this.comments.unshift(comment);
      },
      removeComment(index) {
        this.comments.splice(index, 1); // 删除一个 index 位置的元素
      }
    },
    components: {
      Add,
      List
    }
  }
</script>

<style>

</style>
