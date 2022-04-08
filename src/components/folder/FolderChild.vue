<template>
  <div>
    <h2>{{ folderMsg }}</h2>
  </div>
</template>

<script>
export default {
  name: 'FolderChild',
  props: {
    folderMsg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  font-size: 0.9rem;
}
</style>
