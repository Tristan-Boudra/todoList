<template>
    <form @submit.prevent="addTask">
        <input type="text" v-model="newTask" placeholder="Enter a new task...">
        <button>Add Task</button>
    </form>
</template>

<script>
    export default ({
        name: 'AddTask',
        props: ['tasks', 'taskCount'],
        data() {
            return {
                tasks: [],
                newTask: '',
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
            updateTaskCount() {
                this.taskCount = this.tasks.length;
            }
        }
    });
</script>