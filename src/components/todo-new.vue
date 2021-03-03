<template>
    <p>{{ errorMessage }}</p>
    <div class="addTask">
        <input v-model="task" type="text" placeholder="Nouvelle tâche...">
        <button @click="newTask(task)"><strong>+</strong></button>
    </div>
</template>

<script>
export default {
    name: 'NewToDo',
    data () {
        return {
            errorMessage: '',
        }
    },
    methods: {
        newTask(task){
            if (task.length === 0) {
                this.errorMessage = 'Veuillez entrer une nouvelle tâche'
            }else{
                this.$emit('sendTask', {name: task, status: true})
                this.errorMessage = task
            }
        }
    }
}
</script>

<style scoped>
    .addTask{
        display: flex;
        width: fit-content;
        margin: 4vh auto;
    }
    button{
        background-color: greenyellow;
        margin: 0 4vh;
        padding: 1vh;
        border: none;
        border-radius: 10px;
    }
    input{
        border: none;
        border-bottom: 2px solid turquoise;
        text-align: center;
    }
    input:focus {
        outline:  none;
    }
    input::placeholder{
        color: lightgrey;
    }
</style>