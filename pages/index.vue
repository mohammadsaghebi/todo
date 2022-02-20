<template>
  <main>
    <h1>تابلو وظایف</h1>
    <p>یک لیست از وظابف تعریف کنید</p>

    <div class="create-new">
      <input
        type="text"
        v-model="newTask"
        placeholder="اضافه کردن وظیفه"
        @keypress.enter="addTask"
      />
      <button @click="addTask">اضافه</button>
    </div>

    <div class="tasks">
      <Task v-for="(task, i) in $store.state.tasks" :key="i" :task="task" />
    </div>
  </main>
</template>

<script>
export default {
  data() {
    return {
      newTask: "",
    };
  },
  methods: {
    addTask() {
      if (this.newTask) {
        this.$store.commit("ADD_TASK", this.newTask);
        this.newTask = "";
      }
    },
  },
};
</script>
