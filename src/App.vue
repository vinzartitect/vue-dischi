<template>
  <div id="app">

    <!-- fascia con logo in alto -->
    <div class="logo-bar">
      <img src="./assets/logo-spotify.png" alt="">
    </div>

    <!-- main centrale con i dischi -->
    <FolderDisk/>

  </div>
</template>

<script>
import FolderDisk from './components/FolderDisk.vue'

export default {
  name: 'App',
  components: {
    FolderDisk,
  }
}
</script>

<style lang="scss">
// reset
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  background-color: #1e2d3b;
  height: 100vh;
  width: 100vw;

  .logo-bar {
    height: 8%;
    padding: 10px 20px;
    background-color: #2e3a46;

    img {
      height: 100%;
    }
  }
  
}
</style>
