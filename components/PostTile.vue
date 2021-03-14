<template>
  <div v-if="posts.length">
    <div
      class="py-8 flex flex-wrap md:flex-nowrap border-b-2 border-gray-800"
      v-for="post in posts"
      :key="post._id"
    >
      <div class="md:w-64 md:mb-0 mb-6 flex-shrink-0 flex flex-col">
        <span class="font-semibold title-font text-white">{{
          post.category
        }}</span>
        <span class="mt-1 text-gray-500 text-sm">{{ post.date }}</span>
      </div>
      <div class="md:flex-grow">
        <h2 class="text-2xl font-medium text-white title-font mb-2">
          {{ post.title }}
        </h2>
        <p class="leading-relaxed">
          {{ post.description.replace(/^(.{80}[^\s]*).*/, '$1') }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
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
