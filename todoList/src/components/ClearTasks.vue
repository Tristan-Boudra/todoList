<template>
    <div>
      <button @click="clearTasks">Clear all tasks</button>
    </div>
</template>
  
<script>
export default ({
  name: 'ClearTasks',
  props: ['tasks'],
  methods: {
    clearTasks() {
        this.tasks = [];
        this.taskCount = 0;
    }
  }
});
</script>