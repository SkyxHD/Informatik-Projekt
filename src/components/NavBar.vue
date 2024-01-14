<template>
    <nav class="navbar">
      <router-link router-link to="/">
        <button class="navbar-item1" type="button">Home</button>
      </router-link> 
      <router-link router-link to="/posts">
        <button class=" navbar-item2" type="button">Posts</button>
      </router-link>
    </nav>
</template>

<script>
export default {
  name: 'NavBar'
}
</script>

<style scoped>
.navbar {
  display: flex;
  justify-content: center;
  background-color:rgb(119, 119, 119);
  border-radius: 10px;
}
.navbar-item1 {
  margin-right: 10px;
  font-size: 16px;
  cursor: pointer;
  border-radius: 5px;
  padding: 3px;
  border: 2px solid #04AA6D;
  transition-duration: 0.4s;
  padding: 15px 32px;
  border-radius: 20px;
}
.navbar-item2 {
  margin-left: 10px;
  font-size: 16px;
  cursor: pointer;
  border-radius: 5px;
  padding: 3px;
  border: 2px solid #04AA6D;
  transition-duration: 0.4s;
  padding: 15px 32px;
  border-radius: 20px;
}
.navbar-item2:hover{
  background-color: #04AA6D;
  color: white;
}
.navbar-item1:hover{
  background-color: #04AA6D;
  color: white;
}
</style>