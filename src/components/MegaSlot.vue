<script>
export default {
	data() {
		return {
}
}
}
</script>

<template>
<hr>
HEADER:<br>
<slot name="header" someText="back to the parent component" passedCount="5"></slot>
<hr>
MAIN:<br>
<slot name="main"></slot>
<hr>
FOOTER:<br>
<slot name="footer"></slot>
<hr>
Note that the normal slot tag has the name default.<br>
Slots can have dynamic names.<br>
</template>

