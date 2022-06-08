<template>
  <div class="container">
    <div class="w-full mx-3">
      <div class="text-center mb-5">
        <h1 class="text-5xl font-serif font-bold">Todo List</h1>
      </div>
      <div>
        <form action="#" class="flex justify-center">
          <input
            type="text"
            v-model="task"
            placeholder="Type Your Todo"
            class="input"
          />
          <input type="submit" value="+" class="Submit" @click="addTask()" />
        </form>
      </div>
      <div class="list-container">
        <div>
          <h2 class="text-lg font-bold tracking-wide">
            Make it Easier,Make it Todo.
          </h2>
        </div>
        <div class="flex justify-center">
          <button class="clear-all" @click.prevent="deleteAll()">
            clear all
          </button>
        </div>
        <div class="w-full">
          <ul class="w-full mx-1">
            <li class="task" v-for="(task, index) in tasks" :key="index">
              <span v-text="task.name"></span>
              <button class="clear" @click="deleteTask(index)"></button>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  methods: {
    addTask() {
      this.tasks.push({
        name: this.task,
      });
      this.task = "";
      if (this.task == "") return;
    },
    deleteTask(index) {
      this.tasks.splice(index, 1);
    },
    deleteAll() {
      this.tasks = [];
    },
  },
  data() {
    return {
      task: "",
      tasks: [],
    };
  },
};
</script>

<style scoped>
.Submit {
  @apply bg-blue-400 px-3 py-1 rounded-r-full hover:cursor-pointer text-lg text-white;
}
.container {
  @apply flex justify-center items-center h-screen;
}
.input {
  @apply bg-blue-100 px-3 py-1 rounded-l-full placeholder-blue-300 focus:outline-blue-400;
}
.clear-all {
  @apply bg-blue-400 px-3 py-1 rounded-lg hover:cursor-pointer text-lg text-white;
}
.list-container {
  @apply bg-blue-200 mt-4 rounded-lg shadow-lg p-4 mx-auto max-w-4xl;
}
.task {
  @apply flex justify-between items-center my-3 h-8 w-full;
}
.clear {
  @apply bg-red-700 w-5 h-5 rounded-full hidden;
}
</style>
