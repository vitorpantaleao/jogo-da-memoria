<template>
    <div class="get-name">
        <span>Olá, </span>
        <input type="text" placeholder="Digite seu nome aqui " v-model="name" class="input-name"
            @keyup.enter="saveName" />
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
    name.value = getName() + '!';
});
</script>

<style scoped>
.get-name {
    display: flex;
    align-items: center;
    margin-bottom: 12px;
    font-size: 18px;
}

.input-name {
    border: none;
    width: 100%;
    box-sizing: border-box;
    font-size: 18px;
    padding: 8px;
}
</style>