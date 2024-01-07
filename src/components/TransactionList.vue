<template>
    <v-card rounded width="400px">
        <!-- <h3>History</h3> -->
        <v-list lines="one" id="list">
            <v-list-subheader>History</v-list-subheader>
            <!-- <ul id="list" class="list"> -->
                <!-- <li class="minus">
                    Cash
                    <span>-400₹</span>
                    <button class="delete-btn">x</button>
                </li>
                <li class="plus">
                    Pay check
                    <span>-800₹</span>
                    <button class="delete-btn">x</button>
                </li> -->
            <!-- </ul> -->
            <v-list-item v-for="item, i in items" :class="item.class">
                <span class="ml-3 justify-space-between">{{ item.text }}{{ item.value }}</span>
                <button class="delete-btn">x</button>
            </v-list-item>
        </v-list>
    </v-card>
</template>

<script setup lang="ts">
  const items = [
    { text: 'Cash', value: '-400₹', class: 'minus' },
    { text: 'Pay Check', value: '+800₹', class: 'plus' },
  ]
</script>