<template>
  <div>
    <section class="bg-gray-900 body-font overflow-hidden min-h-screen">
      <div class="container px-5 pb-24 pt-10 mx-auto md:w-6/12">
        <div class="text-center">
          <h1 class="text-2xl text-white font-bold">Create new post</h1>
        </div>
        <form class="px-3 py-4 rounded-md" @submit.prevent="updatePost">
          <div class="my-2 block">
            <label class="text-sm text-gray-100 font-bold"
              >Enter title here</label
            >
            <input
              type="text"
              v-model="updatedPost.title"
              class="w-full sm:text-sm focus:outline-none px-2 py-2 bg-gray-400 rounded-md"
            />
          </div>
          <div class="my-3 block">
            <label class="text-sm text-gray-100 font-bold"
              >Enter description here</label
            >
            <textarea
              v-model="updatedPost.description"
              class="w-full sm:text-sm rounded-md focus:outline-none px-2 py-2 h-28 bg-gray-400"
            />
          </div>
          <div class="my-3 block">
            <label class="text-sm text-gray-100 font-bold"
              >Enter image url here</label
            >
            <input
              type="text"
              v-model="updatedPost.img"
              class="w-full sm:text-sm rounded-md focus:outline-none px-2 py-2 bg-gray-400"
            />
          </div>
          <div class="my-3 block">
            <label class="text-sm text-gray-100 font-bold"
              >Enter category here</label
            >
            <input
              type="text"
              v-model="updatedPost.category"
              class="w-full sm:text-sm rounded-md focus:outline-none px-2 py-2 bg-gray-400"
            />
          </div>
          <div class="flex justify-end">
            <NuxtLink
              to="/admin"
              class="py-2 px-4 bg-red-500 text-gray-100 rounded-md mr-2"
            >
              Discard
            </NuxtLink>
            <button class="py-2 px-4 bg-green-500 text-gray-100 rounded-md">
              Update Post
            </button>
          </div>
        </form>
      </div>
    </section>

    {{ post }}
  </div>
</template>

<script>
export default {
  data() {
    return {
      updatedPost: {
        title: '',
        description: '',
        img: '',
        category: '',
      },
    }
  },
  created() {
    ;(this.updatedPost.title = this.post.title),
      (this.updatedPost.description = this.post.description),
      (this.updatedPost.img = this.post.img),
      (this.updatedPost.category = this.post.category)
  },
  async asyncData({ params, $axios }) {
    try {
      const post = await $axios.$get(
        'https://lit-coast-09507.herokuapp.com/posts/' + params.id
      )
      return { post }
    } catch (error) {
      console.log(error)
    }
  },
  methods: {
    async updatePost() {
      try {
        await this.$axios.$patch(
          'https://lit-coast-09507.herokuapp.com/posts/' +
            this.$route.params.id,
          this.updatedPost
        )
        this.$router.push('/admin')
        this.clearPost()
      } catch (error) {
        console.log('There is an error occured')
        console.log(error)
      }
    },
    clearPost() {
      ;(this.updatedPost.title = ''),
        (this.updatedPost.description = ''),
        (this.updatedPost.img = ''),
        (this.updatedPost.category = '')
    },
  },
}
</script>

<style></style>
