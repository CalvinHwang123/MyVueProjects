<template>
  <li @mouseenter="handleEnter(true)" @mouseleave="handleEnter(false)"
      :style="{ background: bgColor }">
    <label>
      <input type="checkbox" v-model="todo.complete"/>
      <span>{{ todo.title }}</span>
    </label>
    <button v-show="isShow" @click="deleteItem" class="btn btn-danger" style="display:none">删除</button>
  </li>
</template>

<script>
  export default {
    props: {
      todo: Object,
      index: Number,
      deleteTodo: Function
    },
    data() {
      return {
        bgColor: 'white',
        isShow: false
      }
    },
    methods: {
      handleEnter(isEnter) {
        if (isEnter) {
          this.bgColor = '#aaa';
          this.isShow = true;
        } else {
          this.bgColor = '#fff';
          this.isShow = false;
        }
      },
      deleteItem() {
        const { todo, index, deleteTodo } = this;
        if (window.confirm(`确认删除 ${ todo.title } ？`)) {
          deleteTodo(index);
        }
      }
    }
  }
</script>

<style>
  /*item*/
  li {
    list-style: none;
    height: 36px;
    line-height: 36px;
    padding: 0 5px;
    border-bottom: 1px solid #ddd;
  }

  li label {
    float: left;
    cursor: pointer;
  }

  li label li input {
    vertical-align: middle;
    margin-right: 6px;
    position: relative;
    top: -1px;
  }

  li button {
    float: right;
    display: none;
    margin-top: 3px;
  }

  li:before {
    content: initial;
  }

  li:last-child {
    border-bottom: none;
  }
</style>
