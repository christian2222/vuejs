<!-- Here we used composition api. You can mix composition and options api. But better not in one file! -->
<script setup>
import { ref } from 'vue'

const count = ref(0)

</script>

<template>
 <button @click="count++">You clicked me {{ count }} times</button>
</template>

