<template>
	<v-card rounded width="400px">
		<v-list lines="one" id="list" class="mb-0">
			<v-list-subheader>History</v-list-subheader>
			<v-list-item v-for="transaction in transactions" :class="transaction.amount > 0 ? 'plus' : 'minus'"
				:key="transaction.id">
				<span class="ml-3">{{ transaction.text }}</span>
				<span style="position: absolute; right: 5%;">{{ transaction.amount }}₹</span>
				<button class="delete-btn">x</button>
			</v-list-item>
		</v-list>
	</v-card>
</template>

<script setup lang="ts">
import { defineProps } from 'vue';
import { TransactionType } from '../App.vue';


const props = defineProps({
	transactions: {
		type: Array<TransactionType>,
		required: true
	}
})
</script>