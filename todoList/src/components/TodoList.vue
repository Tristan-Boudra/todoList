<template>
    <div>
        <h1>Todo List</h1>
        <ul>
            <li v-for="(task, index) in tasks" :key="index">
                <div v-if="editingTaskIndex === index">
                    <input type="text" v-model="editingTaskValue" @keydown.enter="updateTask(index)" @keydown.esc="cancelEditing">
                    <button @click="updateTask(index)">Save</button>
                    <button @click="cancelEditing">Cancel</button>
                </div>
                <div v-else>
                    {{ task }}
                    <button @click="editTask(index)">Edit</button>
                    <button @click="deleteTask(index)">Delete</button>
                </div>
            </li>
        </ul>
        <form @submit.prevent="addTask">
            <input type="text" v-model="newTask" placeholder="Enter a new task...">
            <button>Add Task</button>
        </form>
        <div>You have {{ taskCount }} tasks</div>
        <ClearTasks></ClearTasks>
      <!-- <button @click="clearTasks">Clear all tasks</button> -->
    </div>
</template>
  
<script>
    import { defineComponent } from 'vue';
    import ClearTasks from './ClearTasks.vue';
  
    export default ({
    name: 'TodoList',
    components: {
        ClearTasks
    },
    data() {
        return {
        tasks: [],
        newTask: '',
        editingTaskIndex: null,
        editingTaskValue: '',
        taskCount: 0
        }
    },
    methods: {
        addTask() {
            if (this.newTask.trim() !== '') {
            this.tasks.push(this.newTask.trim());
            this.newTask = '';
            this.updateTaskCount();
            }
        },
        deleteTask(index) {
            this.tasks.splice(index, 1);
            this.updateTaskCount();
        },
        editTask(index) {
            this.editingTaskIndex = index;
            this.editingTaskValue = this.tasks[index];
        },
        updateTask(index) {
            if (this.editingTaskValue.trim() !== '') {
            this.tasks[index] = this.editingTaskValue.trim();
            this.cancelEditing();
            this.updateTaskCount();
            }
        },
        cancelEditing() {
            this.editingTaskIndex = null;
            this.editingTaskValue = '';
        },
        updateTaskCount() {
            this.taskCount = this.tasks.length;
        },
        // clearTasks() {
        //     this.tasks = [];
        //     this.taskCount = 0;
        // }
    }
    });
</script>