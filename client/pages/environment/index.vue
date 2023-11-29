<script setup>
    const response = await fetch("http://127.0.0.1:8000/ambientes")
    const {data} = await response.json()
    const environment = ref("")
    const createEnvironment = async()=>{
        try{
        await useFetch("http://127.0.0.1:8000/ambientes/",{
            method:"POST",
            body:[{
                nome: environment,
            }]            
        })}
        catch(e){
            alert(e)
        }
    }
</script>

<template >
    <div v-for="environment in data">
        {{ environment.nome }}
    </div>
    <div>
        <h1>crie um novo ambiente</h1>
        <input type="text" v-model="environment"/>
        <button @click="createEnvironment">Criar</button>
    </div>
</template>