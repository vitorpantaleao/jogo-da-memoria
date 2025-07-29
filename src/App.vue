<script setup>
import GetName from './components/GetName.vue';
import Grid from './components/Grid.vue';

</script>

<template>
  <div class="container">
    <GetName />
    <Grid />
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
