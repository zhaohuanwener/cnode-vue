<template>
  <div id="app">
    <NavMenu/>
    <div class="container">
      <router-view/>
    </div>
  </div>
</template>

<script>
import NavMenu from './components/NavMenu'

export default {
  name: 'App',
  components: {
    NavMenu
  }
}
</script>

<style>
#app {
  font-family: 'Source Code Pro';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
}
.container {
  margin-top: 60px;
  /* border: 1px solid red */
}
</style>
