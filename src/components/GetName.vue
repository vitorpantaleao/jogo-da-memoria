<template>
    <div>
        <input type="text" placeholder="Digite seu nome: " v-model="name" class="input-name" @keypress="saveName" />
    </div>
</template>

<script setup>
import { onMounted, ref } from 'vue';

const name = ref('')

const saveName = () => {
    localStorage.setItem('userName', name.value)
}

const getName = () => {
    return localStorage.getItem('userName') || 'Visitante';
}

onMounted(() => {
    name.value = `Olá, ${getName()}!`;
});
</script>

<style scoped>
.input-name {
    border: 1px solid #333;
    width: 100%;
    border-radius: 8px;
    height: 60px;
    padding: 8px 16px;
}
</style>