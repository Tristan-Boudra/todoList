<template>
    <input type="text" v-model="editingTaskValue" @keydown.enter="updateTask(index)" @keydown.esc="cancelEditing">
    <button @click="updateTask(index)">Save</button>
    <button @click="cancelEditing">Cancel</button>
</template>

<script>
    export default ({
        name: 'AddTask',
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
            }
        }
    });
</script>