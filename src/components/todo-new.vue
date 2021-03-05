<template>
    <p>{{ errorMessage }}</p>
    <div class="addTask">
        <input v-model="task" type="text" placeholder="Nouvelle tâche..." required>
        <button v-on:click="sendTask(task)"><i class="fas fa-plus"></i></button>
    </div>
</template>

<!-- ------------------------------------------------------------------------------------------------------------------------------------------------------- -->
<!-- ------------------------------------------------------------------------------------------------------------------------------------------------------- -->

<script>
export default {
    name: 'NewToDo',
    data () {
        return {
            errorMessage: '',
        }
    },
    methods: {
        sendTask(task){
            if (task.length === 0) {
                this.errorMessage = 'Veuillez entrer une nouvelle tâche'
            }else{
                this.$emit('sendTask', {name: task, status: true})      // $emit('event name', params to send)
            }
        }
    }
}
</script>

<!-- ------------------------------------------------------------------------------------------------------------------------------------------------------- -->
<!-- ------------------------------------------------------------------------------------------------------------------------------------------------------- -->

<style scoped>
    .fas{
        color: white;
    }
    .addTask{
        display: flex;
        width: fit-content;
        margin: 4vh auto;
    }
    button{
        background-color: greenyellow;
        margin: 0 4vh;
        padding: 0.5em 0.8em;
        border: none;
        border-radius: 50%;
        font-size: 1rem;
        cursor: pointer;
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