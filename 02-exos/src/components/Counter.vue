<script setup>
    import { ref } from "vue";

    const props = defineProps(["start", "max"])
    const count = ref(props.start)
    const decrement = () => count.value--
    const increment = () => count.value++
</script>

<template>
    <div>
        <button @click="increment">+</button>
        <p>{{ count }}</p>
        <button :on-click="decrement">-</button>
    </div>
</template>