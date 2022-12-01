<script>
export default {
	data() {
		return {
}
},
emits: [
'update:title'
],
props: {
 title: {
  type: String,
  required: false
 }
}
}
</script>

<template>
<p>
<input type="text" :value="title" @input="$emit('update:title', $event.target.value)" placeholder="update parent variable" />
</p>
</template>

