<script setup>
import GetName from './components/GetName.vue';
import Grid from './components/Grid.vue';
import Ranking from './components/Ranking.vue';

</script>

<template>
  <div class="container">
    <h1>Seja bem-vindo ao Jogo da Memória!</h1>
    <GetName />
    <Grid />
    <Ranking />
  </div>
</template>

<style scoped>
* {
  font-family: 'Open Sans', 'Helvetica Neue', sans-serif;
}

.container {
  max-width: 1000px;
  margin: 0 auto;
}
</style>
