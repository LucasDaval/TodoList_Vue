<template>
    <ul id="todoList">
        <li v-for="(task,index) in tasks" :key="index">
            <input type="checkbox" id="">
            <label for="">{{ task.name }}</label>
            <button v-on:click="remover(index)"><i class="fas fa-trash-alt"></i></button>
        </li>
    </ul>
</template>

<!-- ------------------------------------------------------------------------------------------------------------------------------------------------------- -->
<!-- ------------------------------------------------------------------------------------------------------------------------------------------------------- -->

<script>
export default {
    name: 'ToDoList', 
    
    props: {
        tasks:{     // Nouveau tableau qui stock listTasks du todo-card par le v-bind
            type: Array
        },
    },
    methods: {
        // Event to remove a task by index
        remover(index){
            this.$emit('remover', {index})
        },

        // Event to try to change checkbox state
        checkChange(task){
            if (task.check) {
                return this.task.check = false
            }else{
                return this.task.check = true
            }
        }
    },
}
</script>

<!-- ------------------------------------------------------------------------------------------------------------------------------------------------------- -->
<!-- ------------------------------------------------------------------------------------------------------------------------------------------------------- -->

<style scoped>
    .fas{
        color: white;
    }
    input{
        border-radius: 10%;
    }
    .lineThrough{
        text-decoration: line-through;
    }

    button{
        background-color: red;
        margin: 0 4vh;
        padding: 0.2em 0.5em;
        border: none;
        border-radius: 50%;
        font-size: 1rem;
        cursor: pointer;
    }

    #todoList{
        width: 80%;
        margin: 4vh auto;
    }

    #todoList li{
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin: 2vh 0;
    }
</style>