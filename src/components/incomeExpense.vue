<template>
    <div class="inc-exp-container">
        <div>
            <h4>Renda</h4>
            <p id="money-plus" class="money plus">+R${{ renda }}</p>
        </div>
        <div>
            <h4>Despesa</h4>
            <p id="money-minus" class="money minus">R${{ despesa }}</p>
        </div>
    </div>
</template>

<script setup>
    import { defineProps } from 'vue';

    const props = defineProps({
        renda: {
            type: Number,
            Required: true
        },
        despesa: {
            type: Number,
            Required: true
        }
    });

    
</script>