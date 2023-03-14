<template>
  <div>
      <h1>Todo List</h1>
      <ul>
          <li v-for="(task, index) in tasks" :key="index">
              <div v-if="editingTaskIndex === index">
                <UpdateTask></UpdateTask>
              </div>
              <div v-else>
                <EditTask></EditTask>
              </div>
          </li>
      </ul>
      <AddTask></AddTask>
      <div>You have {{ taskCount }} tasks</div>
      <ClearTasks></ClearTasks>
  </div>
</template>

<script>
  import ClearTasks from './components/ClearTasks.vue';
  import AddTask from './components/AddTask.vue';
  import EditTask from './components/EditTask.vue';
  import UpdateTask from './components/UpdateTask.vue';

  export default ({
  name: 'TodoList',
  components: {
      ClearTasks, AddTask, EditTask, UpdateTask
  },
  data() {
      return {
      tasks: [],
      editingTaskIndex: null,
      }
  },
  });
</script>

<style scoped>
header {
  top: 0;
  text-align: center;
}
h1{
  font-size: 50px;
}
</style>
