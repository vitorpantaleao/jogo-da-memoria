<template>
    <div>
        Quantidade de acertos: {{ props.acertos }}
    </div>
</template>

<script setup>
const props = defineProps({
    acertos: {
        type: Number,
        required: true
    }
});
</script>

<style lang="scss" scoped></style>