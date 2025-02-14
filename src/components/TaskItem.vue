<template>
  <div class="task-item">
    <div>
      <input type="checkbox" v-model="task.is_done" @change="updateTask" />
      <span
        v-if="!isEditing"
        :style="{ textDecoration: task.is_done ? 'line-through' : 'none' }"
        class="task-title"
      >
        {{ task.title }}
      </span>
      <input
        v-else
        v-model="task.title"
        @keyup.enter="saveTask"
        class="form-control d-inline-block w-50"
      />
    </div>
    <div class="task-actions">
      <button class="btn btn-sm btn-outline-primary" @click="toggleEdit">
        {{ isEditing ? 'Сохранить' : 'Редактировать' }}
      </button>
      <button class="btn btn-sm btn-outline-danger" @click="deleteTask">
        Удалить
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "TaskItem",
  props: {
    task: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      isEditing: false
    };
  },
  methods: {
    toggleEdit() {
      if (this.isEditing) {
        this.saveTask();
      } else {
        this.isEditing = true;
      }
    },
    saveTask() {
      this.$emit("save", this.task);
      this.isEditing = false;
    },
    updateTask() {
      this.$emit("save", this.task);
    },
    deleteTask() {
      this.$emit("delete", this.task.id);
    }
  }
};
</script>

<style scoped>
.task-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 10px 0;
  border-bottom: 1px solid #ddd;
}
.task-item:last-child {
  border-bottom: none;
}
.task-title {
  flex-grow: 1;
  margin-left: 10px;
}
.task-actions {
  display: flex;
  gap: 10px;
}
</style>