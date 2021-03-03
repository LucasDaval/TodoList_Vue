<template>
    <div class="card">
        <header class="card-header">
            <p>{{ date }}</p>
            <a href="" class="has-text-primary"><strong>VueJs ToDo List</strong></a>
            <p>{{ nbTask }} tâches</p>
        </header>
        <NewToDo />
        <p v-for="item in tasks" :key="item">{{ item.name }}</p>
    </div>
</template>

<script>
import NewToDo from "./todo-new.vue" 

export default {
    name: 'ToDoCard',
    data () {
        return{
            tasks: []
        }
        
    },
    components: {
        NewToDo
    },
    computed: {
        date: function(){
            const now = new Date()
            const day = now.toLocaleString("default", { weekday : "long"}).charAt(0).toUpperCase() + now.toLocaleString("default", { weekday : "long"}).slice(1)
            const month = now.toLocaleString("default", { month : "long"}).charAt(0).toUpperCase() + now.toLocaleString("default", { month : "long"}).slice(1)
            return `${day} ${now.getDay()} ${month}`
        },

        nbTask: function(){
            return 0
        }
    },
    methods: {
        sendTask(task){
            this.tasks.push(task)
        }
    }
}
</script>

<style scoped>
    .card{
        background-color: white;

        width: 80%;
        height: 50vh;
        border-radius: 10px;

        margin: 4vh auto;
    }

    .card-header{
        padding: 1rem;
        justify-content: space-between;
    }
</style>