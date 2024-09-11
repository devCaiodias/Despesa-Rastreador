<template>
    <h3>Historico</h3>
    <ul id="list" class="list">
        <li v-for="t in transaction" :key="t.id" :class="t.amount < 0 ? 'minus': 'plus'">
            {{ t.text }} <span>{{ t.amount }}</span><button class="delete-btn"></button>
        </li>
    </ul>
</template>

<script setup>
    import { defineProps } from 'vue';

    const props = defineProps({
        transaction: {
            type: Array,
            required: true
        },
    })
</script>