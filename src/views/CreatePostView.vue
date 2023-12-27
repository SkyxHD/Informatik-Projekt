<template>
    <div class="createwrapper">
        <div>
          <form action="/post" ></form>
          Title: <textarea rows="1" cols="50" autofocus placeholder="Put your Title in here..."></textarea>
        </div>
    </div>
</template>

<script>
import axios from "axios" // Import the Axios library for making HTTP requests

export default{
    name:"CreatePostView", // Define the Vue component's name

    async createPost(post) { // Define an asynchronous method called "createPost" that takes a post object as an argument
  try {
    const response = await axios.post(`${this.url}/wp-json/wp/v2/posts`, post, { headers: this.headers }); // Send a POST request to the WordPress REST API endpoint to create a new post, passing in the post object and an object containing headers for authentication
    return response.data; // Return the response data (the newly created post)
  } catch (error) {
    throw new Error(`Error while creating post: ${error}`); // If there is an error, throw a new Error object with a message containing the error
  }
}
}

</script>


<style>
textarea {
  resize: none;
}


</style>