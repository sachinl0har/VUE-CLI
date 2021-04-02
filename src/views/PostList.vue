<template>
  <div class="post-list">
      <div class="card mb-3" v-for="post of posts" :key="post.id" @dblclick="$emit('del-post', post.id)">
        <div class="card-body">
          <h3><router-link :to="`/post-details/${post.id}`">{{ post.title }}</router-link></h3>
          <p>{{ post.body }}</p>
        </div>
      </div>
      <div class="card mb-3" v-if="errors && errors.length">
        <div class="card-body">
          <p v-for="(error, index) of errors" :key="index">{{ error.message }}</p>
        </div>
      </div>
  </div>
</template>

<script>
export default {
name: "PostList",
props: ["posts"]
}
</script>

<style>

</style>