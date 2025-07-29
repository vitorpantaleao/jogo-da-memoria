<template>
    <div class="card" @click="handleVirarCarta()">
        <div class="carta-virada" v-if="!virarCarta">
            Carta Virada
        </div>
        <div class="carta-desvirada" v-else>
            {{ carta.name }}
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue';

const virarCarta = ref(false);

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
.carta-virada {
    height: 200px;
    border-radius: 12px;
    text-align: center;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 18px;
    background-color: #DDD;
    color: white;
}

.carta-desvirada {
    height: 200px;
    border-radius: 12px;
    text-align: center;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 18px;
    background-color: #a7ff7454;
    color: black;
}
</style>