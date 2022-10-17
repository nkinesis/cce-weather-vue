<template>
  <main>
    <h1>About CCE weather</h1>
    <HelloWorld msg="This is an example weather website for Montreal and other Canadian cities. Also, this is an example component."/>
  </main>
</template>

<script>
import HelloWorld from '@/components/HelloWorld.vue'
export default {
  name: 'AboutView',
  components: {
    HelloWorld
  }
}
</script>

<style>
main {
  text-align: left;
}
</style>