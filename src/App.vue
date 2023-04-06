<!-- <template>
  <Todolist />
</template>


<script  >
import { reactive } from 'vue';
import Todolist from './components/Todolist.vue';


export default{
  components:{
    Todolist
  },
  setup(){
    const state=reactive({
      todos:[
        {id:1,content:'bihao',isCompleted:false},
        {id:2,content:'bihao',isCompleted:false},
        {id:3,content:'bihao',isCompleted:false}


      ]
    })
    return{

    }
  }
  
}

</script>

  
<style></style> -->

<template>
<el-card class="box-card">
    <template #header>
      <div class="card-header">
        <el-input v-model="input" placeholder="请输入待办事项" />
      </div>
    </template>
    <div v-for="o in 4" :key="o" class="text item">{{ 'List item ' + o }}</div>

    <div class="text">
       <el-row :gutter="15" >
            <el-col :span="8"><div class="grid-content ep-bg-purple" />共三件事情</el-col>
            <el-col :span="3"><div class="grid-content ep-bg-purple" /><el-button text>全部</el-button></el-col>
            <el-col :span="4"><div class="grid-content ep-bg-purple" /><el-button text>进行中</el-button></el-col>
            <el-col :span="4"><div class="grid-content ep-bg-purple" /><el-button text>已完成</el-button></el-col>
         </el-row>
    </div>
  </el-card>
</template>


<script setup>
import { ref } from 'vue'
const input = ref('')

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


.item {
  margin-bottom: 18px;
}

.box-card {
  margin: 50px auto;
  width: 600px;
}
</style>
