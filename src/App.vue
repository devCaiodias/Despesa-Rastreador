<template>
  <Header />
  <div class="container">
    <Balance />
    <IncomeExpense /> 
    <TransactionList :transaction="transaction" />
    <AddTransaction />
  </div>
</template>

<script setup>
import AddTransaction from './components/AddTransaction.vue';
import Balance from './components/Balance.vue';
import Header from './components/Header.vue';
import IncomeExpense from './components/incomeExpense.vue';
import TransactionList from './components/transactionList.vue';

import {ref} from 'vue';

const transaction = ref([
    { id: 1, text: 'Flower', amount: -19.99},
    { id: 2, text: 'Salary', amount: 299.97},
    { id: 3, text: 'Book', amount: -10},
    { id: 4, text: 'Camera', amount: 150},
]);
        

</script>