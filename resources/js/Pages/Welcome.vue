<script>

    import Header from '../Jetstream/Header.vue'
    import Button from '../Jetstream/Button.vue'
    import Tasks from '../Jetstream/Tasks.vue'

    export default {
        
        name: 'Welcome',
        components: {
            Header,
            laravelVersion: String,
            phpVersion: String,
            Button,
            Tasks,
        },
        methods: {
            onClick() {
                console.log('click');
            },
        },
        data() {
            return {
                tasks: []
            }
        },
        methods: {
            deleteTask(id) {
                if(confirm('Are you Sure?')){
                    this.tasks = this.tasks.filter((task) => task.id !== id)
                }
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

<template>

    <div class="container body">
        <Header title="Task Tracker"></Header>
        <Tasks @delete-task="deleteTask" :tasks="tasks"/>
        <Button @click="onClick()" color="green" text="Add task"></Button>
    </div>

</template>

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
