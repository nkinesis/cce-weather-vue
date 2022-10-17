<template>
  <main>
    <header>
      <h1>About CCE weather</h1>
      <HelloWorld
        msg="This is an example weather website for Montreal and other Canadian cities. Also, this is an example component." />
    </header>

    <section class="attribution">
      <h1>Icon attribution</h1>
      <ul>
        <li><a href="https://www.flaticon.com/free-icons/overcast" title="overcast icons">Overcast icons created by
            Freepik -
            Flaticon</a></li>
        <li><a href="https://www.flaticon.com/free-icons/sun" title="sun icons">Sun icons created by Freepik -
            Flaticon</a></li>
        <li> <a href="https://www.flaticon.com/free-icons/weather" title="weather icons">Weather icons created by
            KarLop19 -
            Flaticon</a></li>
        <li><a href="https://www.flaticon.com/free-icons/snow" title="snow icons">Snow icons created by Freepik -
            Flaticon</a></li>
      </ul>
    </section>
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