<template>
    <header>
        <h4>{{title}}</h4>
        <ButtonVue :text="showAddTask?'Close':'Add Task'" :color="showAddTask?'red':'green'" @toggleAddTaskForm="$emit('toggleAddTaskForm')"/>
    </header>
</template>
<script>
import ButtonVue from "./Button.vue"
export default {
    name: "Header",
    props:['title','showAddTask'],
    components:{
        ButtonVue
    }
}
</script>
<style scoped>
   header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 20px;
    }
</style>