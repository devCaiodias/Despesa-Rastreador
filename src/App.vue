<template>
  <Header />
  <div class="container">
    <Balance />
    <IncomeExpense /> 
    <TransactionList />
    <AddTransaction />
  </div>
</template>

<script>
  import AddTransaction from './components/AddTransaction.vue';
import Balance from './components/Balance.vue';
import Header from './components/Header.vue';
import IncomeExpense from './components/incomeExpense.vue';
import TransactionList from './components/transactionList.vue';

  export default {
    components: {
      Header,
      Balance,
      IncomeExpense,
      TransactionList,
      AddTransaction
    }
    
  }

</script>