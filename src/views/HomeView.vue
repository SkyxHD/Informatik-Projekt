<template>
  <div class = "container">
    <div>
      <div class="welcome">Dies ist die Website von Marlon und Philip für den Informatik Kurs von Frau Hoche</div>
      <br>
      <div>Diese Website kann Blogposts, welche in deiner Wordpress Datanbank gespeichert werden, abrufen. Sowie neue Posts erstellen.</div>
    </div>
    
    <div class="Login">
        <router-link router-link to="/login">
          <button class="loginbutton" type="button" >Login</button>
        </router-link>
      </div>
  </div>
</template>

<script>
//component wird eingefügt
export default {
  name: 'HomeView',
  // components: {
  //   HelloWorld
  // }
}
</script>

<style>
  .welcome{
    background: #eee;
    border-radius: 10px;
    padding: 7px;
}

.loginbutton{
  display: flex;
  justify-content: flex-end;
  position: absolute;
  top: 30px;
  right: 50px;
  width: 108px;
  padding: 15px 32px;
  text-align: center;
  font-size: 16px;
  cursor: pointer;
  transition-duration: 0.4s;
  background-color: white;
  color: black;
  border: 2px solid #04AA6D;
  border-radius: 25px;
}
</style>