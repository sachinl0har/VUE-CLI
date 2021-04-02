<template>
  <div class="post-details">
    <div class="row mb-3">
      <div class="col-auto">
        <router-link class="btn btn-block btn-info" to="/"> Go Back</router-link>
      </div>
    </div>
      <div class="card bg-dark mb-3">
        <div class="card-body">
          <h3>{{ post.title }} </h3>
          <p>{{ post.body }}</p>
        </div>
      </div>
      <PostComments />
  </div>
</template>

<script>
import axios from "axios";

import PostComments from "@/views/PostComments.vue";

export default {
name: "PostDetails",
components: {
  PostComments
},
data(){
  return {
    id: this.$route.params.id,
    post: []
  }
},
  created(){
    axios.get(`https://jsonplaceholder.typicode.com/posts/${this.id}`)
    .then(res => {
      this.post = res.data
    })
    .catch(e => {
      this.errors.push(e);
    })
  }
}
</script>

<style>

</style>