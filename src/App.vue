<template>
  <div>
    <Header />
    <div class="container">
      <Balance :total="total" />
      <IncomeExpense :renda="+renda" :despesa="+despesa" />
      <TransactionList :transaction="transaction" @transactionDeleted="handleTransactionDeleted"/>
      <AddTransaction @transactionSubmitted="handleTransactionSubmitted" />
    </div>
  </div>
</template>

<script setup>
import AddTransaction from './components/AddTransaction.vue';
import Balance from './components/Balance.vue';
import Header from './components/Header.vue';
import IncomeExpense from './components/incomeExpense.vue';
import TransactionList from './components/transactionList.vue';

import { useToast } from 'vue-toastification';

import {ref, computed, onMounted} from 'vue';

const toast = useToast();

const transaction = ref([]);

onMounted(() => {
  const savedTransaction = JSON.parse(localStorage.getItem('transaction'));

  if (savedTransaction) {

    transaction.value = savedTransaction;
    
  }
})

// Get Total
const total = computed(() => {
  return transaction.value.reduce((acc, transaction) => {
    return acc + transaction.amount;
  }, 0)
})
        
// Get renda

const renda = computed(() => {
  return transaction.value.filter((transaction) => transaction.amount > 0).reduce((acc, transaction) => {
    return acc + transaction.amount;
  }, 0).toFixed(2);
})


// Get despesas
const despesa = computed(() => {
  return transaction.value.filter((transaction) => transaction.amount < 0).reduce((acc, transaction) => {
    return acc + transaction.amount;
  },0).toFixed(2)
})

// Add Transaction

const handleTransactionSubmitted = (transactionDate) => {
  transaction.value.push({
    id: generateUniqueId(),
    text: transactionDate.text,
    amount: transactionDate.amount
  });

  saveTransactionToLocalStorage();

  toast.success('Trasação adicionada');
};

// Generate unique id 

const generateUniqueId = () => {
  return Math.floor(Math.random() * 1000000);
};
 
// Delete transaction
const handleTransactionDeleted = (id) => {
  transaction.value = transaction.value.filter((transaction) => transaction.id !== id);

  saveTransactionToLocalStorage();
   
  toast.success('Trasação deleted')
};

//  Save to localstorg 

const saveTransactionToLocalStorage = () =>  {
  localStorage.setItem('transaction', JSON.stringify(transaction.value));
  
}
</script>