<template>
    {{ task }}
    <button @click="editTask(index)">Edit</button>
    <button @click="deleteTask(index)">Delete</button>
</template>

<script>
    export default ({
        name: 'EditTask',
        props: ['tasks', 'taskCount'],
        data() {
            return {
                tasks: [],
                editingTaskIndex: null,
                editingTaskValue: '',
                taskCount: 0
            }
        },
        methods: {
            deleteTask(index) {
                this.tasks.splice(index, 1);
                this.updateTaskCount();
            },
            editTask(index) {
                this.editingTaskIndex = index;
                this.editingTaskValue = this.tasks[index];
            },
            updateTaskCount() {
                this.taskCount = this.tasks.length;
            }
        }
    });
</script>