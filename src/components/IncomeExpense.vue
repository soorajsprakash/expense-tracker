<template>
	<v-card width="400px" class="inc-expense-container">
		<v-row no-gutters class="justify-center align-center mx-auto">
            <v-card-item>
                <v-card-subtitle>Income</v-card-subtitle>
                <v-card-title id="money-plus" class="money plus">+{{ income }}₹</v-card-title>
            </v-card-item>
            <v-card-item>
                <v-card-subtitle>Expense</v-card-subtitle>
                <v-card-title id="money-minus" class="money minus">{{ expenses }}₹</v-card-title>
            </v-card-item>
        </v-row>
	</v-card>
</template>

<script setup lang="ts">
import { defineProps } from 'vue';

const props = defineProps({
    income: {
        type: Number,
        required: true
    },
    expenses: {
        type: Number,
        required: true
    },
})
</script>