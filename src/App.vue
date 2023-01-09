<template>
  <div class="container">
    <Header title="Task Tracker" />
    <AddTask @add-task="addTask" />
    <Tasks
      @toggle-reminder="toggleReminder"
      @delete-task="deleteTask"
      :tasks="tasks"
    />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Tasks from "./components/Tasks.vue";
import AddTask from "./components/AddTask.vue";

export default {
  name: "App",
  components: {
    Header,
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks: [],
    };
  },
  methods: {
    addTask(task) {
      this.tasks = [...this.tasks, task];
    },
    deleteTask(id) {
      if (confirm("Are You Sure?")) {
        this.tasks = this.tasks.filter((task) => task.id !== id);
      }
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      );
    },
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Go make breakfast",
        day: "January 9th at 12:00",
        reminder: true,
      },
      {
        id: 2,
        text: "Go commit code",
        day: "January 9th at 14:00",
        reminder: false,
      },
      {
        id: 3,
        text: "Go play FIFA",
        day: "January 9th at 20:00",
        reminder: true,
      },
      {
        id: 4,
        text: "Go eat dinner",
        day: "January 9th at 21:00",
        reminder: false,
      },
      {
        id: 5,
        text: "Go push code to GitHub",
        day: "January 9th at 22:00",
        reminder: true,
      },
    ];
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins&display=swap");
body {
  font-family: "Poppins", sans-serif;
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  height: auto;
  width: 99%;
  border: 1px solid steelblue;
  padding: 15px;
  box-sizing: border-box;
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
