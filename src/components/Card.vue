<template>
    <div class="card" @click="handleVirarCarta">
        <div class="carta-virada" v-if="!carta.virada">
            Virar Carta
        </div>
        <div class="carta-desvirada" v-else>
            {{ carta.name }}
        </div>
    </div>
</template>

<script setup>
const props = defineProps({
    carta: {
        type: Object,
        required: true
    }
});

const emit = defineEmits(['cartaVirada']);

const handleVirarCarta = () => {
    emit('cartaVirada', props.carta);
}
</script>

<style scoped>
.card>div {
    height: 200px;
    border-radius: 12px;
    text-align: center;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 18px;
    color: black;
}

.carta-virada {
    background-color: #DDD;
}

.carta-desvirada {
    background-color: #a7ff7454;
    font-weight: bold;
}

@media (max-width: 768px) {
    .card>div {
        height: 100px;
        font-size: 16px;
    }
}
</style>