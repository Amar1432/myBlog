<template>
  <div>
    <header class="text-gray-400 bg-gray-900 body-font">
      <div
        class="container mx-auto flex flex-wrap p-5 flex-col md:flex-row items-center"
      >
        <nuxt-link
          to="/"
          class="flex title-font font-medium items-center text-white mb-4 md:mb-0"
        >
          <p class="text-xl font-bold">MyBlogs</p>
        </nuxt-link>
        <nav
          class="md:mx-auto flex flex-wrap items-center text-base justify-center"
        >
          <nuxt-link class="mr-5 font-bold hover:text-white" to="/"
            >Home</nuxt-link
          >
          <nuxt-link class="mr-5 font-bold hover:text-white" to="/posts"
            >Posts</nuxt-link
          >
          <nuxt-link class="font-bold hover:text-white" to="/contact"
            >Contact</nuxt-link
          >
        </nav>
        <div>
          <button
            class="inline-flex items-center bg-gray-800 border-0 py-1 px-3 focus:outline-none hover:bg-gray-700 rounded text-base mt-4 md:mt-0 mr-2"
            v-if="isLogin"
          >
            <NuxtLink to="/admin">Admin</NuxtLink>
          </button>
          <button
            class="bg-gray-800 border-0 py-1 px-3 focus:outline-none hover:bg-gray-700 rounded text-base mt-4 md:mt-0"
            v-if="isLogin"
          >
            Logout
          </button>
          <button
            class="bg-gray-800 border-0 py-1 px-3 focus:outline-none hover:bg-gray-700 rounded text-base mt-4 md:mt-0"
            v-else
          >
            Login
          </button>
        </div>
      </div>
    </header>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isLogin: true,
    }
  },
}
</script>

<style></style>
