<template>
  <main>
     <div class="container">
        <h1>欢迎使用 YHY 待办事项！</h1>

        <addTodo :tid="todos.length" @addTodo="addTodo"/>

        <filterTodo :selected="filter" @change-filter="filter = $event"/>
        
        <listTodo :todos="filteredTodos"/>
     </div>
  </main>
</template>

<script> 
import { computed, ref } from 'vue'
//导入对应的组件
import addTodo from './components/addTodo.vue'
import filterTodo from './components/filterTodo.vue'
import listTodo from './components/listTodo.vue'
export default {
  name: 'App',
  components: {
    addTodo,
    filterTodo,
    listTodo
  },
  setup() {
    //定义一个默认todo的数据 相等与vue2中的data
    const todos = ref([]);
    //添加todo的事件函数 相等于vue2中methods中this.todos = todo
    const addTodo = (todo) => todos.value.push(todo);
    //保存当前选项的列表
    const filter = ref("all");
    //根据fiter的值过滤todo列表
    const filteredTodos = computed(() => {
      switch(filter.value) {
        case "done":
          return todos.value.filter((todo) => todo.completed);
        case "todo":
          return todos.value.filter((todo) => !todo.completed);
        default:
          return todos.value;
      }
    })
    // 返回数据
    return {
      todos,
      addTodo,
      filter,
      filteredTodos
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: Helvetica, "PingFang SC", "Microsoft Yahei", sans-serif;
}
/* 整个页面 */
main {
  width: 100vw;
  min-height: 100vh;
  padding: 10vh 0;
  display: grid;
  align-items: start;
  justify-items: center;
  background: #d8dfff;
}
.container {
  width: 60%;
  max-width: 400px;
  box-shadow: 0px 0px 24px rgba(0, 0, 0, 0.15);
  border-radius: 24px;
  padding: 48px 28px;
  background-color: rgb(245, 246, 252);
}
/* 标题 */
h1 {
  margin: 24px 0;
  font-size: 28px;
  color: #414873;
}

</style>
