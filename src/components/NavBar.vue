<template>
  <div class="navbar">
    <div class="navbar-item">Home</div>
    <div class="navbar-item">View posts</div>
  </div>
</template>

<script>
export default {
  name: 'NavBar'
}
</script>

<style scoped>
.navbar {
  display: flex
}
.navbar-item {
  margin-right: 20px
}
.navbar-item:last-of-type {
  margin-right: 0
}
</style>
