<template>
	<v-layout class="rounded rounded-md">
		<v-app-bar color="surface-variant" title="Expense Tracker"></v-app-bar>

		<v-main class="d-flex align-center justify-center" style="min-height: 300px;">
			<div class="container">
				<Balance />
				<br>
				<IncomeExpense />
				<br>
				<TransactionList :transactions="transactions"/>
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

// wrap anything in "ref" to make it reactive
import { ref } from 'vue';

const transactions = ref([
	{ id: 1, text: 'Cash', amount: -400 },
	{ id: 2, text: 'Pay Check', amount: +800 },
	{ id: 3, text: 'Food', amount: -370 },
	{ id: 4, text: 'Auto', amount: -120 },
])
</script>