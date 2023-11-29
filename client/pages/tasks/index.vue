<script setup>
    const reponse = await fetch("http://127.0.0.1:8000/tarefas/")
    const {data} = await reponse.json()
</script>

<template>
    <div v-for="tasks in data">
        <nuxt-link :to="`http://localhost:3000/tasks/${tasks.idTarefaFK.id }`"><h1>nome da tarefa: {{ tasks.idTarefaFK.nome }}</h1></nuxt-link>
        <h2>status: {{ tasks.idTarefaFK.idStatusFK.nome }} </h2>
        <h3>ambiente: {{ tasks.idTarefaFK.idAmbienteFK.nome }}</h3>
        <h3>prazo: {{ tasks.idTarefaFK.prazo }}</h3>
    </div>
</template>