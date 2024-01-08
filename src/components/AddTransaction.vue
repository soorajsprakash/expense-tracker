<template>
	<v-card>
		<h5>Add Transaction</h5>
		<v-form ref="form" id="form" @submit.prevent="onSubmit">
			<v-text-field id="text" type="text" v-model="text" label="Enter text.." placeholder="John Doe" required
				clearable></v-text-field>
			<v-text-field id="amount" type="text" v-model="amount" label="Enter amount.. (-ve -> expense; +ve -> income)" placeholder="250"
				required></v-text-field>
			<v-btn color="error" class="mt-4 btn" type="submit" block rounded>
				Add Transaction
			</v-btn>
		</v-form>
	</v-card>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const text = ref('')
const amount = ref('')

const onSubmit = () => {
	console.log("SUBMIT: ", text.value, amount.value)
}
</script>