<template>
    <div class="card">
        <header class="card-header">
            <p>{{ date }}</p>
            <a href="" class="has-text-primary"><strong>VueJs ToDo List</strong></a>
            <p>{{ nbTask }} tâches</p>
        </header>
        <NewToDo @sendTask="newTask"/>
        <ToDoList v-bind:tasks="listTasks"/>
    </div>
</template>

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
            const day = now.toLocaleString("default", { weekday : "long"}).charAt(0).toUpperCase() + now.toLocaleString("default", { weekday : "long"}).slice(1)
            const month = now.toLocaleString("default", { month : "long"}).charAt(0).toUpperCase() + now.toLocaleString("default", { month : "long"}).slice(1)
            return `${day} ${now.getDay()} ${month}`
        },

        nbTask: function(){
            return this.listTasks.length 
            // return 0 
        }
    },
    methods: {
        newTask(task){
            // console.log("Mère : " + task);
            this.listTasks.push(task);
            // console.log(this.listTasks);
        }
    },
}
</script>

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

    /* p{
        text-decoration: line-through;
    } */
</style>