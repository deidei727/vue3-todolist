
<template>
  <el-card class="box-card">
    <template #header>
      <div class="card-header">
        <el-input v-model="input" placeholder="请输入待办事项" @keyup.enter="addTodo" />
      </div>
    </template>
    <label for="choice"></label>
    <div v-for="todo in item.todos" :key="todo.id" class="text item">
      <input type="checkbox" id="choice" @change="toggle">
      {{ todo.title }}
      <div class="delete" @click="deleteTodo(todo.id)">x</div>
    </div>
 

    <div class="text">
      <el-row :gutter="15">
        <el-col :span="5">
          <div class="grid-content ep-bg-purple" />共{{ item.todos.length }}件事情
        </el-col>
        <el-col :span="3">
          <div class="grid-content ep-bg-purple" /><el-button text>全部</el-button>
        </el-col>
        <el-col :span="4">
          <div class="grid-content ep-bg-purple" /><el-button text>进行中</el-button>
        </el-col>
        <el-col :span="7">
          <div class="grid-content ep-bg-purple" /><el-button text>已完成</el-button>
        </el-col>
        <el-col :span="4">
          <div class="grid-content ep-bg-purple" /><el-button text @click="clealAll">清空全部</el-button>
        </el-col>
      </el-row>
    </div>
  </el-card>
</template>


<script >
import { reactive, ref } from 'vue'
// import All from './components/All.vue'
// import Active from './components/Active.vue'
// import Finish from './components/Finish.vue'

export default {
  setup() {

    const input = ref('')
    
    
    const item = reactive({

      todos: [
        { id: 1, title: 'nihao', done: false },
        { id: 2, title: 'rf', done: false },
        { id: 3, title: 'ret', done: false },
      ]

    })

    function addTodo(e) {
      let idCount = item.todos.length
      let list_item = { id: ++idCount, title: input.value, done: false }
      item.todos.unshift(list_item)
      // 添加后清空input的value
      input.value = ''
    }

    function deleteTodo(id) {
      // 根据已知todo的id进行删除
      const index = item.todos.findIndex((itemId) => {
        return itemId.id === id

      })
      item.todos.splice(index, 1)
    }
    function clealAll() {
      item.todos.length = 0
    }
    function toggle(e) {
      console.log(e.target.checked)
     
    } 
    
    return {
      input,
      item,
      
      addTodo,
      deleteTodo,
      clealAll,
      toggle,
    }
  }
}


</script>

  
<style>
.el-row {
  margin-bottom: 20px;

}

.el-row:last-child {
  margin-bottom: 0;
}

.el-col {
  border-radius: 4px;
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.text {
  font-size: 14px;
}

.delete {
  float: right;
}

.delete:hover {
  cursor: pointer;
}

.item {
  margin-bottom: 18px;
}

.box-card {
  margin: 50px auto;
  width: 600px;
}
</style>
