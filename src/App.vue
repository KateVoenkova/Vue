<script>

import {defineComponent} from "vue";
import NavBar from "@/components/NavBar.vue";
import TaskEditor from "@/components/TaskEditor.vue";
import TaskItem from "@/components/TaskItem.vue";

export default defineComponent({
  components: {TaskItem, TaskEditor, NavBar}
})
</script>

<template>
<NavBar />
  <TaskEditor></TaskEditor>
  <TaskItem></TaskItem>
</template>

<style scoped>
</style>
