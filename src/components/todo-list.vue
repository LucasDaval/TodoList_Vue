<template>
    <div class="card">
        <header class="card-header">
            <p>Date</p>
            <a href="" class="has-text-primary"><strong>VueJs ToDo List</strong></a>
            <p>Nb tâches</p>
        </header>
    </div>
</template>

<script>
export default {
    name: 'ToDoList'
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