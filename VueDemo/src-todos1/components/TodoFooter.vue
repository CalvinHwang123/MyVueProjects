<template>
  <div class="todo-footer">
    <label>
      <input v-model="isCheckAll" type="checkbox"/>
    </label>
    <span>
          <span>已完成 {{ completeSize }}</span> / 全部 {{ todos.length }}
        </span>
    <button v-show="completeSize" class="btn btn-danger" @click="clearCompleted">清除已完成任务</button>
  </div>
</template>

<script>
  export default {
    props: {
      todos: Array,
      checkAllTodo: Function,
      clearCompletedTodos: Function
    },
    methods: {
      clearCompleted() {
        if (window.confirm(`是否清除已完成的 ${ this.completeSize } 条任务？`)) {
          this.clearCompletedTodos();
        }
      }
    },
    computed: {
      completeSize() {
        return this.todos.reduce((totalPrev, todo) => totalPrev + (todo.complete ? 1 : 0), 0);
      },
      isCheckAll: {
        get() {
          return this.completeSize === this.todos.length && this.todos.length > 0;
        },
        set(checkAll) {
          this.checkAllTodo(checkAll);
        }
      }
    }
  }
</script>

<style>
  /*footer*/
  .todo-footer {
    height: 40px;
    line-height: 40px;
    padding-left: 6px;
    margin-top: 5px;
  }

  .todo-footer label {
    display: inline-block;
    margin-right: 20px;
    cursor: pointer;
  }

  .todo-footer label input {
    position: relative;
    top: -1px;
    vertical-align: middle;
    margin-right: 5px;
  }

  .todo-footer button {
    float: right;
    margin-top: 5px;
  }
</style>
