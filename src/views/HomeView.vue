<template>
  <div>
    <div class="welcome">Welcome to my site</div>
    <div>This is the home page of my site</div>
  </div>
  
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'

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
    width: 95vw;
    border-radius: 10px;
    padding: 7px;
}

</style>