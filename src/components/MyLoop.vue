<script>
export default {
	data() {
		return {
}
},
emits: [
'killComponent'
],
props: {
 length: {
  type: Number,
  required: true
 }
}
}
</script>

<template>
<p>
Lange Liste von Zahlen
<ul>
<li v-for="n in length" :key="n">{{ n }}</li>
</ul>
<button @click="$emit('killComponent')">Delete whole component</button>
</p>
</template>

