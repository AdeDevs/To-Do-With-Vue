<template>
  <div
    @dblclick="$emit('toggle-reminder', task.id)"
    :class="[task.reminder ? 'reminder' : '', 'task']"
  >
    <h3>
      {{ task.text }}
      <i @click="$emit('delete-task', task.id)" class="fas fa-times"></i>
    </h3>
    <p>{{ task.day }}</p>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: {
    task: Object
  }
};
</script>

<style scope>
.fas {
  color: red;
}

.task {
  background: rgb(165, 165, 165);
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}

.task:hover {
  background-color: rgb(233, 233, 233);
  transition: 400ms;
}

.task.reminder {
  border-left: 15px solid green;
}

.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
