<template>
  <section class="text-gray-400 bg-gray-900 body-font">
    <div class="container px-5 py-24 mx-auto">
      <h1 class="my-2 font-bold text-2xl">Featured Posts</h1>
      <div class="flex flex-wrap -m-4" v-if="posts.length">
        <div class="w-1/3 p-4" v-for="post in posts" :key="post._id">
          <PostCard
            :title="post.title"
            :description="post.description"
            :image="post.img"
            :category="post.category"
          />
        </div>
      </div>
      <div v-else>
        <div class="w-full text-center p-5">
          <h1>Loading...</h1>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      test: 'Hello',
      posts: [],
    }
  },
  async created() {
    try {
      this.posts = await this.$axios.$get(
        'https://lit-coast-09507.herokuapp.com/posts'
      )
    } catch (error) {
      console.log(error)
    }
  },
}
</script>

<style></style>
