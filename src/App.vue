<template>
<img alt="Vue logo" src="./assets/logo.png">
<HelloWorld msg="Welcome to my App"/>
<br>
{{name }}<br>
{{age }}<br>
{{msg }}<br>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

// const props = defineProps(['msg'])

export default {
name: 'App',
//      props: ['msg'],
      components: {
      HelloWorld
     },
      data() {
      return {
name: 'Michael',
      age: 45,
      msg: 'Huch'
      }
     },
      setup(props) {
      console.log(props.msg)
      }


}
</script>

<style>
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
color: #2c3e50;
       margin-top: 60px;
}
</style>
