<template>
  <div>
    <h3>Escape From The Rumbling</h3>
    <MyCanvas />
  </div>
</template>
<script>
import MyCanvas from './components/MyCanvas.vue'
export default {
  name: 'App',
  components: {
    MyCanvas
  },
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
  background: #eee;
}
</style>
