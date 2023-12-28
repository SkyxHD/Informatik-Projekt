<template>
    <div class="createwrapper">
        <div>
          <form action="/post" id="usrform">
          </form>
          <br>
          Title: <textarea id="title" rows="1" cols="45" autofocus placeholder="Title of your Blog entry..."></textarea>
          <br>
          <br>
          <textarea rows="50" cols="100" placeholder="Content here..."></textarea>
          <button type="button" onclick="myFunction()">Press</button>
        </div>
    </div>
</template>

<script>
import axios from "axios" // Import the Axios library for making HTTP requests

export default{
    name:"CreatePostView", // Define the Vue component's name

    async createPost(post) { // Define an asynchronous method called "createPost" that takes a post object as an argument
  try {
    const response = await axios.post(`${this.url}/wp-json/wp/v2/news`, post, { headers: this.headers }); // Send a POST request to the WordPress REST API endpoint to create a new post, passing in the post object and an object containing headers for authentication
    return response.data; // Return the response data (the newly created post)
  } catch (error) {
    throw new Error(`Error while creating post: ${error}`); // If there is an error, throw a new Error object with a message containing the error
  }
}
}
function myFunction() {
  document.getElementById("title").value = "Du Hund";
}
</script>

<style>
textarea {
  resize: none;
}


</style>