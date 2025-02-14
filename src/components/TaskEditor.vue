<template>
  <div class="mt-4">
    <input
      type="text"
      v-model="newTask"
      placeholder="Название задачи"
      class="form-control d-inline-block w-75"
    />
    <button @click="addTask" class="btn btn-primary">Добавить задачу</button>
    <p v-if="error" class="text-danger mt-2">{{ error }}</p>
  </div>
</template>

<script>
export default {
  name: "TaskEditor",
  data() {
    return {
      newTask: "",
      error: ""
    };
  },
  methods: {
    addTask() {
      if (!this.newTask.trim()) {
        this.error = "Название задачи не может быть пустым.";
        return;
      }
      this.$emit("add", { title: this.newTask });
      this.newTask = "";
      this.error = "";
    }
  }
};
</script>

<style scoped>
/* Стили для редактора задачи */
</style>