<template>
    <div class="contador">
        <span>Quantidade de acertos: {{ props.acertos }}</span>
        <span>Quantidade de rodadas: {{ props.rodadas }}</span>
    </div>
</template>

<script setup>
const props = defineProps({
    acertos: {
        type: Number,
        required: true
    },
    rodadas: {
        type: Number,
        required: true
    }
});
</script>

<style scoped>
.contador {
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-size: 18px;
}
</style>