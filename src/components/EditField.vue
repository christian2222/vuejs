<script>
export default {
data() {
return {
text: 'Eingabe',
      before: false,
      empty: '',
      hider: true,
      entry: 10
}
},
watch: {
 entry(newValue, oldValue) {
 // side effect by change
  console.log("Value " + oldValue + " changed to " + newValue)
 }
},
methods: {
 accept() {
 alert(this.quotedText + ' als Eingabe akzeptiert')
 },
 ctrlEnter() {
 alert(this.quotedText + ' mit Ctrl-Taste akzeptiert')
 },
 shiftEnter() {
 alert(this.quotedText + ' mit Shift-Taste akzeptiert')
 }
 },
computed: {
  quotedText() {
  return '"'+this.text+'"';
  }
  },
  mounted() {
  alert('EditField-component is alive')
  this.$refs.input.focus()
  }
}
</script>

<template>
{{before?  text:empty }}<br>
<input placeholder="Insert text" type="text" v-model="text" @keyup.enter.exact="accept" @keyup.ctrl.enter.exact="ctrlEnter" @keyup.shift.enter.exact="shiftEnter"><br>
{{before? empty:text }}<br>
<button @click="before = !before">{{ before? 'Dahinter':'Davor' }}</button>
<br>
<div v-if="hider">
Hide me<br>
</div>
<div v-show="hider">
Me too, but I stay in DOM and get only display set to none.<br>
</div>

<button @click="hider = !hider">{{hider? 'Hide':'Show' }}</button>
<br>
<br>
<!-- the v-for below needs a key to work with -->
<span v-for="n in 10" :key="n">{{ n }},</span><br>
<br>
Logged on console by a watcher <input v-model="entry" ref="input" /><br>
Note: Watcher callbacks are called <em>before</em> DOM-Updates of a component! You can change this, but you need the option <em>flush: 'post'</em>.<br>
This input uses the <em>ref</em>-Attribute to be focused. Howerver the order of an array would not be the same when using refs!<br>
</template>
