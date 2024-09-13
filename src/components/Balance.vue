<template>
    <h4>Seu Saldo</h4>
    <h1 id="balance">R${{ total }}</h1>
</template>

<script setup>
    import { defineProps } from 'vue';

    const props = defineProps({
        total: {
            type: Number,
            Required: true
        }
    })
</script>