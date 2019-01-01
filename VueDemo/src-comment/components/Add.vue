<template>
  <div class="col-md-4">
    <form class="form-horizontal">
      <div class="form-group">
        <label>用户名</label>
        <input v-model="name" type="text" class="form-control" placeholder="用户名">
      </div>
      <div class="form-group">
        <label>评论内容</label>
        <textarea v-model="content" class="form-control" rows="6" placeholder="评论内容"></textarea>
      </div>
      <div class="form-group">
        <div class="col-sm-offset-2 col-sm-10">
          <button @click="add" type="button" class="btn btn-default pull-right">提交</button>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
  export default {
    props: {
      addComment: {
        type: Function,
        required: true
      }
    },
    data() {
      return {
        name: '',
        content: ''
      }
    },
    methods: {
      add() {
        // 获取输入的值
        const name = this.name.trim();
        const content = this.content.trim();
        // 非空判断
        if (!name || !content) {
          alert('输入的用户名或评论不能为空');
          return;
        }
        // 封装成 comment 对象
        const comment = {
          name,
          content
        }
        // 调用父组件的 addComment 方法
        this.addComment(comment);
        // 清除数据
        this.name = '';
        this.content = '';
      }
    }
  }
</script>

<style>

</style>
