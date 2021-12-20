<template>
    <div v-for="task in tasks" :key="task">
      <TaskVue :task="task" @delete-task="$emit('delete-task',task.id)" @toggle-reminder="$emit('toggle-reminder',task.id)"/>
    </div>
</template>

<script>
import TaskVue from "./Task.vue"
export default {
  name: "Tasks",
  components:{
      TaskVue
  },
  emits:['delete-task','toggle-reminder'],
  props:['tasks'],

  created(){
    console.log(this.tasks);
  }
}
</script>