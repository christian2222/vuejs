<script>
// that would be composition api
//import { ref } from 'vue'

//const test = ref('Hiha')

// but here we use options api!
import EditField from './options/EditField.vue'
import ListField from './options/ListField.vue'
import MyLoop from './options/MyLoop.vue'
import UpdateParentComponent from './options/UpdateParentComponent.vue'
import SlottedButton from './options/SlottedButton.vue'
import MegaSlot from './options/MegaSlot.vue'
import ColorSpan from './options/ColorSpan.vue'
import MouseTracker from './options/MouseTracker.vue'
import BlogPost from './composition/BlogPost.vue'

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
       ColorSpan,
       MouseTracker,
       BlogPost
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
<SlottedButton>Voll <ColorSpan>mega!</ColorSpan></SlottedButton>
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
<BlogPost heading="My post list" :likes="4"/>
</template>
