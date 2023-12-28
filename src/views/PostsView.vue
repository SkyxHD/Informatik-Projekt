<template>
  <div>

    <div v-if="loading">Content is loading...</div>

    <div v-for="post in posts" :key="`post-${post.id}`" class="post">
      <div class="header">
        <div >{{ post.acf.newstitle  }} ({{ new Date(post.date).toLocaleDateString("de-DE") }})</div>
        <div class="category">{{   post.acf.category }}</div> 
      </div>
      <img class="image" :src="post.image"/>
      <div v-html="post.acf.newscontent"></div>
    </div>

    <div class="create">
      <router-link router-link to="/createpost">
        <button class="button" type="button" >Create Post</button>
      </router-link>
    </div>


  </div>
</template>


<script>
//import axios für GET requests usw.
import axios from "axios"

export default {
  name: 'PostsView',
  data() {
    return {
      posts: [],
      loading: false
    }
  },
  async mounted() {
    this.loading = true
    const { data } = await axios.get('http://mysite.local/wp-json/wp/v2/news')
    for (let i = 0; i < data.length; i++) {
      const post = data[i]
      const { data: imageData } = await axios.get(post._links['wp:featuredmedia'][0].href)
      post.image = imageData.guid.rendered
    }
    this.posts = data
    this.loading = false
  },
}

</script>

<style scoped>
.header{
  display: flex;
}

.category{
  margin-left: auto;
}

.post{
  background-color: #eee;
  border-radius: 5px;
  box-shadow: 2px 2px 5px rgba(0, 0, 0, 0.4);
  margin: 20px;
  padding: 20px;
}

.image{
  margin: 20px 0;
}
.button {
  display: flex;
  justify-content: flex-end;
  align-items: start-flex;
  position: absolute;
  top: 75px;
  right: 50px;
  width: 150px;
  padding: 15px 32px;
  text-align: center;
  font-size: 16px;
  cursor: pointer;
  transition-duration: 0.4s;


}

.button {border-radius: 25px;}

.button { 
  background-color: white;
  color: black;
  border: 2px solid #04AA6D;
}

.button:hover {
  background-color: #04AA6D;
  color: white;
}


</style>