<template>
    <div>
        <Counter :acertos="acertos" />
        <div class="grid">
            <Card v-for="carta in sortCartas" :key="carta.id" :carta="carta" @carta-virada="verificaCarta(carta)" />
        </div>
    </div>
</template>

<script setup>
import { nextTick, onMounted, ref } from 'vue';
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

const sortCartas = ref([]);
const cartasViradas = ref([])
const cartasAcertadas = ref([])
const acertos = ref(0);

const embaralhaCartas = () => {
    sortCartas.value = cartas.value
        .sort(() => Math.random() - 0.5)
        .map(carta => ({ ...carta, virada: false }))
}

const reorderCartas = () => {
    cartas.value = cartas.value.sort(() => Math.random() - 0.5);
}

const verificaCarta = async (carta) => {
    console.log('Verificando carta:', carta);

    if (cartasViradas.value.length >= 2 || carta.virada || cartasAcertadas.value.includes(carta.id)) return;

    carta.virada = true;
    cartasViradas.value.push(carta)

    if (cartasViradas.value.length == 2) {
        if (cartasViradas.value[0].name === cartasViradas.value[1].name && cartasViradas.value[0].id !== cartasViradas.value[1].id) {
            acertos.value++;
            cartasAcertadas.value.push(cartasViradas.value[0].id, cartasViradas.value[1].id);
            cartasViradas.value = [];

            alert('Acertou!');
        } else {
            await nextTick();

            setTimeout(() => {
                cartasViradas.value[0].virada = false;
                cartasViradas.value[1].virada = false;
                cartasViradas.value = [];
                alert('Errou! Tente novamente.');
            }, 1000);
        }
    }
}

onMounted(() => {
    embaralhaCartas();
});

</script>

<style scoped>
.grid {
    display: grid;
    grid-template-columns: repeat(5, 1fr);
    gap: 16px;
    padding: 16px;
}
</style>