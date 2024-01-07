<template>
  <v-layout class="rounded rounded-md">
    <v-app-bar color="surface-variant" title="Expense Tracker"></v-app-bar>

    <v-navigation-drawer location="right">
      <h3>History</h3>
    </v-navigation-drawer>

    <v-main class="d-flex align-center justify-center" style="min-height: 300px;">
      <Balance/>
    </v-main>
  </v-layout>
</template>


<script setup lang="ts">
import Balance from './components/Balance.vue';


</script>