<template>
  <div>

    <div v-if="loading">Content is loading...</div>

    <div v-for="post in posts" :key="`post-${post.id}`" class="post">
      <div class="header">
        <div >{{ post.title.rendered  }} ({{ new Date(post.date).toLocaleDateString("de-DE") }})</div>
        <div class="category">{{   post.acf.category }}</div> 
      </div>
      <img class="image" :src="post.image"/>
      <div v-html="post.acf.newscontent"></div>
    </div>

    <div class="create">

      <router-link to="/createpost">Create Post</router-link>

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
    const { data } = await axios.get('http://news.com/wp-json/wp/v2/news')
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
.create {
  display: flex;
  justify-content: flex-end;
  align-items: start-flex;
  margin-right: 100px;


}
</style>