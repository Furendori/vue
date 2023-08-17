<script setup>
import { ref } from 'vue';

const message = ref('Hello')
const reversed = () => {
    console.log('computed');
    return message.value.split('').reverse().join('')
}
</script>

<template>
    <h2>Computed</h2>
    <p>{{ message }} à l'envers {{ reversed() }}</p>
    <input type="text" v-model="message">
</template>