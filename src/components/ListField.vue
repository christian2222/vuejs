<script>
export default {
	data() {
		return {
items: [
       {name: 'Gerd', id: 3, age: 45},
       {name: 'Franz', id: 2, age: 23},
       {name: 'Fritz', id: 1, age: 19},
       {name: 'Lilia', id: 7, age: 33},
       {name: 'Gerald', id: 6, age: 27}
],
styleObject: {
color: 'red',
       bgcolor: 'yellow',
       fontWeight: 'bold',
       fontSize: '30px'
}
}
},
computed: {
  ageSum() {
  let sum = 0
 for(let i= 0; i < this.items.length; i++) {
  sum += this.items[i].age
 }
 return sum
  }
 }
}
</script>

<template>
<p :style="styleObject">
Hello
<ul>
<li v-for="item in items" :key="item.id">
{{ item.name }} - {{ item.id }} - {{ item.age }}
</li>
</ul>
</p>
<b>Agesum: {{ ageSum }}</b><br>
</template>

