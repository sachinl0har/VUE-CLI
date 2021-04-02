<template>
  <div class="post-comments">
      <div class="card mb-3" v-for="comment in comments" :key="comment.id">
        <div class="row g-0">
    <div class="col-md-2">
      <img src="@/assets/alphaAI.gif">
    </div>
    <div class="col-md-10">
      <div class="card-body">
        <h5 class="card-title">{{comment.name}}</h5>
        <p class="card-text">{{comment.body}}</p>
        <p class="card-text"><small class="text-muted">{{comment.email}}</small></p>
      </div>
    </div>
  </div>
      </div>
  </div>
</template>

<script>
import axios from "axios";


export default {
name: "PostComments",
data(){
  return{
    id: this.$route.params.id,
    comments: []
  }
},
  created(){
    axios.get(`https://jsonplaceholder.typicode.com/comments?postId=${this.id}`)
    .then(res => {
      this.comments = res.data
    })
    .catch(e => {
      this.errors.push(e);
    })
  }
}
</script>

<style>

</style>