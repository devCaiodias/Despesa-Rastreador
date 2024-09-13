<template>
    <div>
        <h3>Historico</h3>
        <ul id="list" class="list">
            <li v-for="t in transaction" :key="t.id" :class="t.amount < 0 ? 'minus': 'plus'">
                {{ t.text }} <span>R$ {{ t.amount }}</span><button class="delete-btn" @click="deleteTransaction(t.id)">X</button>
            </li>
        </ul>
    </div>
</template>

<script setup>
    import { defineProps } from 'vue';

    
    const props = defineProps({
        transaction: {
            type: Array,
            required: true
        },
    })

    const emit = defineEmits(['transactionDeleted']);
    
    const deleteTransaction = (id) => {
        emit('transactionDeleted', id);
    };
</script>