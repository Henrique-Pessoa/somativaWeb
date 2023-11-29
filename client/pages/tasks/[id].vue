<script setup>
import {useRoute} from "vue-router"
const route = useRoute()
const reponse = await fetch(`http://127.0.0.1:8000/tarefas/${route.params.id}`)
const {data} = await reponse.json()

const responseTarefa = await fetch(`http://127.0.0.1:8000/tarefasUsuarios?tarefa=${route.params.id}`)
const {data:dataTarefa} = await responseTarefa.json()

const responseStatus = await fetch(`http://127.0.0.1:8000/tarefasStatus?tarefa=${route.params.id}`)
const {data:dataStatus} = await responseStatus.json()

</script>

<template>
    <div>
        <div>
        <h1>Nome da tarefa: {{ data.nome }}</h1>
        <h2>Status: {{ data.idStatusFK.nome }} </h2>
        <h2>Ambiente: {{ data.idAmbienteFK.nome }}</h2>
        <h2>Prazo: {{ data.prazo }}</h2>
        <h2>Data de inicio: {{ data.dataInicio }}</h2>
        <h2>Data de termino: {{ data.dataFim }}</h2>
        <h2>Descricao: {{ data.descricao }}</h2>
        <h3>Status atual: {{ dataStatus[0].descricao }}</h3>
        </div>
        <br/>
        <br/>
        <br/>
        <div>
            <h1>Foi solicitado pelo: {{ data.idSolicitanteFK.nome }}</h1>
            <img :src="`${data.idSolicitanteFK.image}`"/>
        </div>
        <br/>
        <br/>
        <br/>
        <div v-for="usuarios in dataTarefa">
            <h1>São os responsaveis pela tarefa: {{ usuarios.idUsuarioFK.nome }}</h1>
            <img :src="`${usuarios.idUsuarioFK.image}`" alt="">
        </div>
    </div>
</template>