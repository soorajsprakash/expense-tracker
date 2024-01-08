<template>
	<v-card>
		<h5>Add Transaction</h5>
		<v-form ref="form" id="form">
			<v-text-field
				id="text"
				type="text"
				label="Enter text.."
				placeholder="John Doe"
				required
				clearable
			></v-text-field>
			<v-text-field
				id="amount"
				type="number"
				label="Enter amount.. (-ve -> expense; +ve -> income)"
				placeholder="250"
				required
			></v-text-field>
			<v-btn
				color="error"
				class="mt-4 btn"
				block
				rounded
				@click=""
				>
				Add Transaction
				</v-btn>
		</v-form>
	</v-card>
</template>