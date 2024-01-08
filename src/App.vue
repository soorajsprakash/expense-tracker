<template>
	<v-layout class="rounded rounded-md">
		<v-app-bar color="surface-variant" title="Expense Tracker"></v-app-bar>

		<v-main class="d-flex align-center justify-center" style="min-height: 300px;">
			<div class="container">
				<Balance/>
				<br>
				<IncomeExpense/>
				<br>
				<TransactionList />
				<br>
				<AddTransaction />
			</div>
		</v-main>
	</v-layout>
</template>


<script setup lang="ts">
import Balance from './components/Balance.vue';
import IncomeExpense from './components/IncomeExpense.vue';
import TransactionList from './components/TransactionList.vue';
import AddTransaction from './components/AddTransaction.vue';
</script>