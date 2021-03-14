<template>
  <div>
    <section class="bg-gray-900 body-font overflow-hidden min-h-screen">
      <div class="container px-5 pb-24 pt-10 mx-auto md:w-6/12">
        <div class="flex justify-between items-center">
          <h1 class="text-gray-500 font-bold py-4">Your Posts</h1>
          <button
            class="bg-blue-800 border-0 py-2 px-3 focus:outline-none hover:bg-blue-700 rounded text-base text-white font-bold"
          >
            <NuxtLink to="/admin/newPost">Create New Post</NuxtLink>
          </button>
        </div>
        <div
          class="w-full h-1/6 bg-gray-600 px-4 py-3 my-2 rounded-md flex justify-between items-center"
          v-for="post in postlist"
          :key="post._id"
        >
          <div class="w-8/12 border-r-1 border-purple-500">
            <h1 class="text-2xl text-gray-50">{{ post.title }}</h1>
            <p class="text-sm text-gray-300">
              {{ post.description.replace(/^(.{40}[^\s]*).*/, '$1') }}...
            </p>
          </div>
          <div class="flex flex-col md:flex-row">
            <button
              @click="update(post._id)"
              class="p-2 bg-green-500 rounded-md mb-2 md:mb-0 md:mr-2 text-white font-bold"
            >
              Update
            </button>
            <button
              @click="deletePost(post._id)"
              class="p-2 bg-red-500 rounded-md text-white font-bold"
            >
              Delete
            </button>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios }) {
    try {
      const postlist = await $axios.$get(
        'https://lit-coast-09507.herokuapp.com/posts'
      )
      return { postlist }
    } catch (error) {
      console.log(error)
    }
  },
  methods: {
    update(postId) {
      this.$router.push('/admin/' + postId)
    },
    async deletePost(postId) {
      try {
        await this.$axios.delete(
          'https://lit-coast-09507.herokuapp.com/posts/' + postId
        )
        const postIndex = this.postlist.findIndex((p) => p._id === postId)
        this.postlist.splice(postIndex, 1)
        console.log('Post deleted')
      } catch (error) {
        console.log('An error occured')
        console.log(error)
      }
    },
  },
}
</script>

<style></style>
