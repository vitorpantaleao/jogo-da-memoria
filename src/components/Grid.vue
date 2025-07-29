<template>
    <div>
        <Counter :acertos="acertos" />
        <div class="grid">
            <Card v-for="carta in sortCartas" :key="carta.id" :carta="carta" @carta-virada="verificaCarta(carta)" />
        </div>
    </div>
</template>

<script setup>
import { computed, ref } from 'vue';
import Card from './Card.vue';
import Counter from './Counter.vue';

const cartas = ref([
    { id: 1, name: 'Carta 1', virada: false },
    { id: 2, name: 'Carta 2', virada: false },
    { id: 3, name: 'Carta 3', virada: false },
    { id: 4, name: 'Carta 4', virada: false },
    { id: 5, name: 'Carta 5', virada: false },
    { id: 6, name: 'Carta 6', virada: false },
    { id: 7, name: 'Carta 7', virada: false },
    { id: 8, name: 'Carta 8', virada: false },
    { id: 9, name: 'Carta 9', virada: false },
    { id: 10, name: 'Carta 10', virada: false },
    { id: 11, name: 'Carta 1', virada: false },
    { id: 12, name: 'Carta 2', virada: false },
    { id: 13, name: 'Carta 3', virada: false },
    { id: 14, name: 'Carta 4', virada: false },
    { id: 15, name: 'Carta 5', virada: false },
    { id: 16, name: 'Carta 6', virada: false },
    { id: 17, name: 'Carta 7', virada: false },
    { id: 18, name: 'Carta 8', virada: false },
    { id: 19, name: 'Carta 9', virada: false },
    { id: 20, name: 'Carta 10', virada: false }
])

const cartasViradas = ref([])
const cartasAcertadas = ref([])
const acertos = ref(0);

const sortCartas = computed(() => {
    return cartas.value.sort(() => Math.random() - 0.5).map(carta => {
        return { ...carta, virada: false }
    })
})

const reorderCartas = () => {
    cartas.value = cartas.value.sort(() => Math.random() - 0.5);
}

const verificaCarta = (carta) => {
    console.log('Verificando carta:', carta);

    cartasViradas.value.push(carta)

    if (cartasViradas.value.length == 2) {
        if (cartasViradas.value[0].name === cartasViradas.value[1].name && cartasViradas.value[0].id !== cartasViradas.value[1].id) {
            acertos.value++;
            cartasAcertadas.value.push(cartasViradas.value[0], cartasViradas.value[1]);
            cartas.value = cartas.value.filter(c => !cartasAcertadas.value.includes(c));
            alert('Acertou!');
        } else {
            console.log('Errou!');
        }
        cartasViradas.value = []
    }
}

</script>

<style scoped>
.grid {
    display: grid;
    grid-template-columns: repeat(5, 1fr);
    gap: 16px;
    padding: 16px;
}
</style>