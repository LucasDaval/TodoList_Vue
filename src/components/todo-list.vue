<template>
    <ul id="todoList">
        <li v-for="(task,index) in tasks" :key="index">
            <input v-bind:class="{ active: checked }" type="checkbox" id="">
            <label for="">{{ task.name }}</label>
            <button><i class="fas fa-trash-alt"></i></button>
        </li>
    </ul>
</template>

<script>
export default {
    name: 'ToDoList', 
    // methods: {
    //     remover(index){
    //         this.events.splice(index, 1);
    //     }
    // },
    props: {
        tasks:{
            type: Array
        },
    }
}
</script>

<style scoped>
    .fas{
        color: white;
    }
    input{
        border-radius: 10%;
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