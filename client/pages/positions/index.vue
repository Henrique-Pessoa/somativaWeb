<script setup>
const reponse = await fetch("http://127.0.0.1:8000/cargos/")
const {data} = await reponse.json()
</script>

<template>
    <div v-for="positions in data">
        <H1>{{ positions.nome }}</H1>
    </div>
</template>