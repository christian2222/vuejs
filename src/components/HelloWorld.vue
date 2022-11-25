<script setuo>
// that would be composition api
//import { ref } from 'vue'

//const test = ref('Hiha')

// but here we use options api!
import EditField from './EditField.vue'
import ListField from './ListField.vue'
import MyLoop from './MyLoop.vue'
import UpdateParentComponent from './UpdateParentComponent.vue'
import SlottedButton from './SlottedButton.vue'
import MegaSlot from './MegaSlot.vue'
import RedSpan from './RedSpan.vue'
import MouseTracker from './MouseTracker.vue'

export default {
data() {
return { test: 'Hiha',
showSubcomponent: true,
changedByChild: ""
}
},
props: ['msg'],
       components: {
       EditField,
       ListField,
       MyLoop,
       UpdateParentComponent,
       SlottedButton,
       MegaSlot,
       RedSpan,
       MouseTracker
       },
methods: {
 removeComp() {
 this.showSubcomponent = false;
 },
 change(newTitle) {
this.changedByChild = newTitle
 //console.log('Changed')
 if(this.changedByChild == '') return
 if(this.changedByChild.charAt(0) == 'L') {
 this.changedByChild = this.changedByChild.toUpperCase();
 } else {
 this.changedByChild = this.changedByChild.toLowerCase();
 }
 }
 }
}
</script>


<template>
<h1>Here is my child component!</h1>
Test
<MyButton /><br>
{{ msg }}
<MyButton /><br>
{{ test }}
<MyButton /><br>
<EditField />
<ListField />
<div v-if="showSubcomponent">
<MyLoop :length="25" @killComponent="removeComp" />
{{ changedByChild }}<br>
<UpdateParentComponent @update:title="change" :title="changedByChild" /><br>
{{ changedByChild }}<br>
<SlottedButton>Slotted Button</SlottedButton>
<SlottedButton></SlottedButton>
Note: You can use slotted components in other slots:
<SlottedButton>Voll <RedSpan>mega!</RedSpan></SlottedButton>
Slotted components have no access to the child component's data!
<MegaSlot>
 <template v-slot:header="slotProps">
  My personal header.
 <p> {{ slotProps.someText }} </p>
  <p>{{ slotProps.passedCount }} </p>
 </template>
 <template #main> <!-- shorthand for v-slot -->
  The main content.
 </template>
 <template v-slot:footer>
  A general footer.
 </template>
</MegaSlot>
<p>
<MouseTracker v-slot="{ x, y }">
Mouse is at: {{ x }}, {{ y }}
</MouseTracker>
by a <em>renderless component</em>
</p>
</div>
</template>
