<script>
export default {
	data() {
		return {
}
},
inject: ['myColor']
// use provide and inject to pass values through inheritance hirarchies
}
</script>

<template>
<span :style="{ color:  myColor }">
<slot></slot>
</span>
</template>

