<script setup>
import { defineProps, ref } from 'vue'

/*const attrs = */defineProps({
  heading: String,
  likes: Number
})

const posts = ref([
  { id: 1, title: 'My journey with Vue' },
  { id: 2, title: 'Blogging with Vue' },
  { id: 3, title: 'Why Vue is so fun' }
])

</script>

<template>
<h2> {{ heading }} </h2>
<p>
<ul>
<li v-for="post in posts" :key="post.id">
{{ post.title }}
</li>
</ul>
We got {{ likes }} likes.
</p>
</template>
