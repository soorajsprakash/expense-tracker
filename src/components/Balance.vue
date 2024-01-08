<template>
	<v-card width="400px">
		<v-card-item>
			<v-card-subtitle>Your Balance</v-card-subtitle>
			<v-card-title id="balance">{{ total }}₹</v-card-title>
		</v-card-item>
	</v-card>
</template>

<script setup lang="ts">
import { defineProps } from 'vue';

const props = defineProps({
	total: {
		type: Number,
		required: true
	}
})
</script>