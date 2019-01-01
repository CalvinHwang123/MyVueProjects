<template>
  <li class="list-group-item">
    <div class="handle">
      <a @click="remove" href="javascript:;">删除</a>
    </div>
    <p class="user"><span >{{ comment.name }}</span><span>说:</span></p>
    <p class="centence">{{ comment.content }}</p>
  </li>
</template>

<script>
  export default {
    props: {
      comment: Object, // 指定了属性名和属性值的类型
      removeComment: Function,
      index: Number
    },
    methods: {
      remove() {
        const { comment, removeComment, index } = this;
        // 使用 ES6 的模板字符串（反引号）引入变量
        if (window.confirm(`确认删除 ${ comment.name } 的评论吗？`)) {
          removeComment(index);
        }
      }
    }
  }
</script>

<style>
  li {
    transition: .5s;
    overflow: hidden;
  }

  .handle {
    width: 40px;
    border: 1px solid #ccc;
    background: #fff;
    position: absolute;
    right: 10px;
    top: 1px;
    text-align: center;
  }

  .handle a {
    display: block;
    text-decoration: none;
  }

  .list-group-item .centence {
    padding: 0px 50px;
  }

  .user {
    font-size: 22px;
  }
</style>
