<template>
    <div class="createwrapper">
        <div>
            <textarea id="postname_input" rows="1" cols="20"></textarea>
        </div>
    </div>
</template>

<script>
import axios from "axios"

export default{
    name:"CreatePostView",

    async createPost(post) {
  try {
    const response = await axios.post(`${this.url}/wp-json/wp/v2/posts`, post, { headers: this.headers });
    return response.data;
  } catch (error) {
    throw new Error(`Error while creating post: ${error}`);
  }
}
}</script>