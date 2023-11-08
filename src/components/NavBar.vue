<template>
    <nav>
      <router-link to="/">Home</router-link> |
      <router-link to="/posts">Posts</router-link>
    </nav>
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