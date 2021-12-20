<template>
    <button class="btn" :style="{background: color}" @click="$emit('toggleAddTaskForm')">
       {{text}}
    </button>
</template>
<script>
export default {
    name: "Button",
    props:['text','color']
}
</script>
<style>
    
</style>