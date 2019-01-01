<template>
  <div class="todo-container">
    <div class="todo-wrap">
      <!--<TodoHeader @addTodo="addTodo" />--><!--为 TodoHeader 标签对象绑定 addTodo 事件监听-->
      <TodoHeader ref="header" />
      <TodoList :todos="todos" :deleteTodo="deleteTodo" />
      <todo-footer :todos="todos" :checkAllTodo="checkAllTodo" :clearCompletedTodos="clearCompletedTodos" />
    </div>
  </div>
</template>

<script>
  import TodoHeader from './components/TodoHeader'
  import TodoList from './components/TodoList'
  import TodoFooter from './components/TodoFooter'
  export default {
    data() {
      return {
        /*todos: [
          { title: '吃饭', complete: false },
          { title: '睡觉', complete: true },
          { title: '打豆豆', complete: false }
        ]*/

        // 从 localStorage 中取值
        todos: JSON.parse(window.localStorage.getItem('todos_key') || '[]')
      }
    },

    mounted() { // 常用于执行异步代码
      // 给 <TodoHeader /> 标签对象绑定事件监听
      this.$refs.header.$on('addTodo', this.addTodo);
    },

    methods: {
      addTodo(todo) {
        this.todos.unshift(todo);
      },
      deleteTodo(index) {
        this.todos.splice(index, 1);
      },

      // 全选 / 取消全选
      checkAllTodo(check) {
        this.todos.forEach(todo => todo.complete = check);
      },
      // 清除已完成的任务
      clearCompletedTodos() {
        this.todos = this.todos.filter(todo => !todo.complete);
      }
    },

    watch: {
      todos: {
        deep: true, // 深度监视
        handler: function (value) {
          // 将监视到的 todos 最新值保存在 localStorage 内
          window.localStorage.setItem('todos_key', JSON.stringify(value));
        }
      }
    },

    components: {
      TodoHeader,
      TodoList,
      TodoFooter
    }
  }
</script>

<style>
  /*app*/
  .todo-container {
    width: 600px;
    margin: 0 auto;
  }
  .todo-container .todo-wrap {
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 5px;
  }
</style>
