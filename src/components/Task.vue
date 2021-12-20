<template>
<div :class="[task.reminder?'reminder':'','task']" @dblclick="$emit('toggle-reminder')">
     <h3>{{task.text}} <i class="fas fa-x" @click="$emit('delete-task',task.title)"></i></h3>
     <p>{{ task.date }}</p>
</div>
</template>


<script>
  export default {
      name:"Task",
      props: {
          task: Object
      },
      emits:['delete-task','toggle-reminder'],
      methods:{
          onDelete(title){
            //   console.log(title);
              this.$emit("delete-task",title)
          }
      }
  }
</script>

<style scoped>
.fas {
  color: red;
}
.task {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}
.task.reminder {
  border-left: 5px solid green;
}
.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>