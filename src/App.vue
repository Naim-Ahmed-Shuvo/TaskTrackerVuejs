<template lang="">
  <div class="container">
    <HeaderVue title="Task Tracker" @toggleAddTaskForm="toggleAddTaskForm" :showAddTask="showAddTask"/>
    <div v-show="showAddTask">
         <AddTask @add-task="addTask"/>
    </div>
    <div v-if="tasks.length==0">
        <h3>No Tasks Yet....</h3>
    </div>
    <Tasks :tasks="tasks" @delete-task="deleteTask" @toggle-reminder="toggleReminder"/>
  </div>
</template>



<script>
import Tasks from "./components/Tasks.vue"
import HeaderVue from "./components/Header.vue"
import AddTask from "./components/AddTAsk.vue"


//
export default {
  components: { HeaderVue, Tasks,AddTask },
  data() {
    return {
      showAddTask:false,
      tasks: [
        
      ]
    }
  },
  methods:{
     addTask(task){
        this.tasks.push(task)
    },
    deleteTask(id){
      console.log(id);
      if(confirm("Are you sure")){

        this.tasks = this.tasks.filter(task=> task.id !== id)
      }
    },
    toggleReminder(id){
        console.log(id);
        this.tasks = this.tasks.map(task=>task.id === id?{...task,reminder : !task.reminder}:task)
    },
    toggleAddTaskForm(){
      console.log("hi");
      this.showAddTask = !this.showAddTask
    },

   
   
  },

 
}
</script>



<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap");
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: "Poppins", sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
