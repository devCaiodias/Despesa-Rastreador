<template>
    <h3>Adicionar nova Transição</h3>
    <form id="form" @submit.prevent="onSubmit">
        <div class="form-control">
            <label for="text">Texto</label>
            <input type="text" id="text" v-model="text" placeholder="Dijite Texto">
        </div>
        <div class="form-control">
            <label for="amount">Quantidade <br> (Negativo - dispesa, Positivo - renda)</label>
            <input type="text" id="amount" v-model="amount" placeholder="Dijite Quantidade">
        </div>
        <button class="btn">Adicionar Transição</button>
    </form>
</template>

<script setup>
    import { ref } from 'vue';
    import { useToast } from 'vue-toastification';

    const text=  ref('');
    const amount = ref('');

    const emit = defineEmits(['transactionSubmitted']);

    const toast = useToast();


    const onSubmit= () => {
        if (!text.value || !amount.value) {
            toast.error('Ambos os campos devem ser preenchidos');
            return;
        }
        
        const transactionDate = {
            text: text.value,
            amount: parseFloat(amount.value)
        }

        emit('transactionSubmitted', transactionDate);

        text.value = '';
        amount.value = '';
    }
</script>