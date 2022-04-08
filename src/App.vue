<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
  <FolderChild folderMsg="test import child component in child folder"/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import FolderChild from './components/folder/FolderChild.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    FolderChild
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
