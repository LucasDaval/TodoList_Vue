<template>
    <div class="card">
        <header class="card-header">
            <p>{{ date }}</p>
            <a href="" class="has-text-primary"><strong>VueJs ToDo List</strong></a>
            <p>{{ nbTask }} tâches</p>
        </header>
        <NewToDo @sendTask="newTask"/>      <!-- @nom de l'event="nom de la méthode à utiliser" -->
        <ToDoList v-bind:tasks="listTasks" @remover="removeTask" />
    </div>
</template>

<!-- ------------------------------------------------------------------------------------------------------------------------------------------------------- -->
<!-- ------------------------------------------------------------------------------------------------------------------------------------------------------- -->

<script>
import NewToDo from "./todo-new.vue" 
import ToDoList from "./todo-list.vue" 

export default {
    name: 'ToDoCard',
    data () {
        return{
            listTasks: []
        }        
    },
    components: {
        NewToDo,
        ToDoList
    },
    computed: {
        date: function(){
            const now = new Date()
            //  Day end month created with first letter in caps
            const day = now.toLocaleString("default", { weekday : "long"}).charAt(0).toUpperCase() + now.toLocaleString("default", { weekday : "long"}).slice(1)
            const month = now.toLocaleString("default", { month : "long"}).charAt(0).toUpperCase() + now.toLocaleString("default", { month : "long"}).slice(1)
            //  Return day + actual month's number + month
            return `${day} ${now.getDay()} ${month}`
        },

        // Return tasks number created
        nbTask: function(){
            return this.listTasks.length 
        }
    },
    methods: {
        // Add a new task
        newTask(task){
            this.listTasks.push(task)
        },

        // Delete a task
        removeTask(index){
            this.listTasks.splice(index.index, 1)
        }
    },
}
</script>

<!-- ------------------------------------------------------------------------------------------------------------------------------------------------------- -->
<!-- ------------------------------------------------------------------------------------------------------------------------------------------------------- -->

<style scoped>
    .card{
        background-color: white;

        width: 80%;
        min-height: 50vh;
        height: fit-content;
        border-radius: 10px;

        margin: 4vh auto;
    }

    .card-header{
        padding: 1rem;
        justify-content: space-between;
    }
</style>