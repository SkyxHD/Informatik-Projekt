<template>
  <form>      
    <input name="name" type="text" class="feedback-input" placeholder="Name" />   

    <input name="email" type="text" class="feedback-input" placeholder="Title" />

    <textarea name="text" class="feedback-input" placeholder="Content"></textarea>

    <input name="img" type="file" class="img" >

    <input type="submit" value="POST"/>
  </form>
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


</script>

<style>

@import url(https://fonts.googleapis.com/css?family=Montserrat:400,700);

form { max-width:420px; margin:50px auto; }

.feedback-input {
  color:rgb(0, 0, 0);
  font-family: Helvetica, Arial, sans-serif;
  font-weight:500;
  font-size: 18px;
  border-radius: 5px;
  line-height: 22px;
  background-color: transparent;
  border:2px solid #04AA6D;
  transition: all 0.3s;
  padding: 13px;
  margin-bottom: 15px;
  width:100%;
  box-sizing: border-box;
  outline:0;
}

.feedback-input:focus { border:2px solid #04AA6D; }

textarea {
  height: 150px;
  line-height: 150%;
  resize:vertical;
}
.img{
  border-color:#04AA6D;
  border-radius: 2px;
}
[type="submit"] {
  font-family: 'Montserrat', Arial, Helvetica, sans-serif;
  width: 100%;
  background:#04AA6D;
  border-radius:5px;
  border:0;
  cursor:pointer;
  color:white;
  font-size:24px;
  padding-top:10px;
  padding-bottom:10px;
  transition: all 0.3s;
  margin-top: 10px;
  font-weight:700;
}
[type="submit"]:hover { background:#036d46; }
</style>