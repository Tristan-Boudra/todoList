<template>
    <div>
      <button @click="clearTasks">Clear all tasks</button>
    </div>
</template>
  
<script>
import { defineComponent } from 'vue';

export default ({
  name: 'ClearTasks',
  data() {
    return {}
  },
  methods: {
        clearTasks() {
            this.tasks = [];
            this.taskCount = 0;
        }
  }
});
</script>