<template>
    <header>
        <h1>{{ title }}</h1>
        <Button 
            @btn-click="$emit('toggle-add-task')" 
            :text="showAddTask ? 'Close' : 'Add Task'" 
            :color="showAddTask ? '#ff0000' : '#008000'"
        />
    </header>
</template>

<script>
import Button from './Button.vue'

export default {
    name: 'Header',
    props: {
        title: {
            type: String,
            default: 'Hello World',
            showAddTask: Boolean,
        }
    },

    components: {
        Button,
    },
}

</script>

<style scoped>

header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
}

</style>