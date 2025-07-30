<template>
    <div>
        <h2>Ranking (Top 5)</h2>
        <ul>
            <li v-for="(jogador, i) in ranking" :key="i">
                <b>{{ i + 1 }}º - </b> {{ jogador.jogador }} - {{ jogador.rodadas }} rodadas
            </li>
        </ul>
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const ranking = ref([])

onMounted(() => {
    const data = localStorage.getItem('ranking')
    ranking.value = data ? JSON.parse(data) : []
})
</script>

<style scoped>
h2 {
    margin-bottom: 8px;
}

ul {
    padding: 0;
    list-style: none;
}

li {
    margin-bottom: 4px;
}
</style>
