<template>
  <HelloWorld/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'



export default {
  name: 'App',
  components: {
    HelloWorld,
}
}
</script>

<style>

    body {
    width: 90%;
    background-image: url('../src/assets/money1.jpg');
  }
  @media screen and (max-width: 576px) {
    body {
      width: 576px
    } 
  }
</style>
