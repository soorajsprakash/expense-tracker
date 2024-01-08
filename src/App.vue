<template>
	<v-layout class="rounded rounded-md">
		<v-app-bar color="surface-variant" title="Expense Tracker"></v-app-bar>

		<v-main class="d-flex align-center justify-center" style="min-height: 300px;">
			<div class="container">
				<Balance :total="+total"/>
				<br>
				<IncomeExpense :income="+income" :expenses="+expenses"/>
				<br>
				<TransactionList :transactions="transactions" @deleteTransaction="handleDeleteTransaction"/>
				<br>
				<AddTransaction @submitTansaction="handleNewTransaction"/>
			</div>
		</v-main>
		<v-snackbar v-model="toast" timeout="2000" color="green">
			{{ toastBody }}
			<template v-slot:actions>
				<v-btn variant="text" @click="toast = false">
					x
				</v-btn>
			</template>
		</v-snackbar>
	</v-layout>
</template>


<script setup lang="ts">
import Balance from './components/Balance.vue';
import IncomeExpense from './components/IncomeExpense.vue';
import TransactionList from './components/TransactionList.vue';
import AddTransaction from './components/AddTransaction.vue';

// wrap anything in "ref" to make it reactive
import { ref, computed, onMounted } from 'vue';

export interface TransactionType {
	id: number,
	text: string,
	amount: number
}

enum LocalStorageKey {
	TRANSACTIONS = 'transactions'
}

const transactions = ref<TransactionType[]>([])

onMounted(() => {
	const savedTransactions = JSON.parse(localStorage.getItem(LocalStorageKey.TRANSACTIONS) as string)
	if (savedTransactions) {
		transactions.value = savedTransactions
	}
})

const toast = ref(false)
const toastBody = ref('')

// get total balancec
const total = computed(() => {
	return transactions.value.reduce((acc, transaction) => {
		return acc + transaction.amount
	}, 0)
})

// get income: toFixed will make it a string rather than a number
const income = computed(() => {
	return transactions.value
		.filter((transaction) => transaction.amount > 0)
		.reduce((acc, transaction) => {
			return acc + transaction.amount
		}, 0)
		.toFixed(2)
})

// get expenses
const expenses = computed(() => {
	return transactions.value
		.filter((transaction) => transaction.amount < 0)
		.reduce((acc, transaction) => {
			return acc + transaction.amount
		}, 0)
		.toFixed(2)
})

// generates unique unique ID
const generateUniqueId = () => {
	return transactions.value.length + 1
}

// add new transaction
const handleNewTransaction = (newTransaction: Partial<TransactionType>) => {
	transactions.value.push({
		id: generateUniqueId(),
		text: newTransaction.text ?? "",
		amount: newTransaction.amount ?? 0
	})
	saveToLocalstorage()
	toastBody.value = 'Successfully added new transaction'
	toast.value = true
}

// handle delete transaction
const handleDeleteTransaction = (id: number) => {
	transactions.value = transactions.value.filter((each) => each.id !== id)
	saveToLocalstorage()
	toastBody.value = 'Transaction deleted'
	toast.value = true
}

// save to localstorage
const saveToLocalstorage = () => {
	localStorage.setItem(LocalStorageKey.TRANSACTIONS, JSON.stringify(transactions.value))
}
</script>