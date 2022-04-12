<template>

    <div class="container body">
        <Header 
            @toggle-add-task="toggleAddTask" 
            title="Task Tracker"
        >
        </Header>
        <div v-if="showAddTask">
            <AddTask @add-task="addTask"/>
        </div>
        <Tasks 
            @toggle-reminder="toggleReminder" 
            @delete-task="deleteTask" 
            :tasks="tasks"
        />
    </div>

</template>

<script>

    import Header from '../Jetstream/Header.vue'
    import Button from '../Jetstream/Button.vue'
    import Tasks from '../Jetstream/Tasks.vue'
    import AddTask from '../Jetstream/AddTask.vue'

    export default {
        
        name: 'Welcome',
        components: {
            Header,
            laravelVersion: String,
            phpVersion: String,
            Button,
            Tasks,
            AddTask,
        },
        data() {
                return {
                    tasks: [],
                    showAddTask: false,
                }
            },
        methods: {

            addTask (task) {
                this.tasks = [...this.tasks, task]
            },

            deleteTask(id) {
                if(confirm('Are you Sure?')){
                    this.tasks = this.tasks.filter((task) => task.id !== id)
                }
            },

            toggleReminder(id){
                this.tasks = this.tasks.map((task) => 
                task.id === id ? {...task, reminder: !task.reminder} : task
                )
            },

            toggleAddTask() {
                this.showAddTask = !this.showAddTask
            },
        },

        created() {
            this.tasks = [
            {
                id: 1,
                text: 'Doctors Consult',
                day: 'March 1st at 2:30pm',
                reminder: true,
            },
            {
                id: 2,
                text: 'Doctors Apointment',
                day: 'March 2st at 2:30pm', 
                reminder: true,
            },
            {
                id: 3,
                text: 'Doctors Surgery',
                day: 'March 3st at 2:30pm',
                reminder: false,
            },
        ]},
    }

</script>


<style scoped>

@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');

* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

.body {
    font-family: 'Poppins', sans-serif;
}

.container {
    max-width: 500px;
    margin: 30px auto;
    overflow: auto;
    min-height: 300px;
    border: 1px solid rgb(28, 43, 54);
    padding: 30px;
    border-radius: 5px;
}

.btn {
    display: inline-block;
    background: #000;
    color: #fff;
    border: none;
    padding: 10px 20px;
    margin: 5px;
    border-radius: 5px;
    cursor: pointer;
    text-decoration: none;
    font-size: 15px;
    font-family: inherit;
}

.btn:focus {
    outline: none;
}

.btn:active {
    transform: scale(0.98);
}

.btn-block {
    display: block;
    width: 100%;
}

</style>
