<template>
  <main>
    <h1>All Users ToDoList</h1><br><br>
    

    <div class="create-new">
      <input
        type="text"
        v-model="newTask"
        placeholder="Add a new list"
        @keypress.enter="addTask"
      />
      <button @click="addTask">Add</button>
    </div>

  <div v-for="(item,index) in $store.state.todoList " :key="index">

    <Task :todo = "item" ></Task>
  </div>


  </main>
</template>

<script>
// - {{ index}}
import Task from '../components/Task'
// <div class="tasks">
//     //   <Task v-for="(task,i ) in $store.state.ToDoList" :key=i :task="task" />
//     // </div>
export default {
  name : 'Home-view',
  components : {
    Task
  },
  data() {
    return {
      newTask: '',
    }
  },

  methods: {
   addTask() {
      if (this.newTask) {
        this.$store.dispatch('CreateToDo', {
          data: {


  "title": this.newTask,
  "description": "string",
  "created_at":  new Date().toISOString(),
  "updated_at":  new Date().toISOString(),
  "is_completed": false,
  "is_deleted": true


        }
        })

        this.newTask = ''
        //await this.$store.dispatch('GetAllToDOs')
      }
    },
  },
}
</script>