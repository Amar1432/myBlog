<template>
  <div>
    <header class="text-gray-400 bg-gray-900 body-font">
      <div
        class="container mx-auto flex flex-wrap p-5 flex-col md:flex-row items-center"
      >
        <nuxt-link to="/"
          class="flex title-font font-medium items-center text-white mb-4 md:mb-0"
        >
          <p class="ml-3 text-xl">MyBlogs</p>
        </nuxt-link >
        <nav
          class="md:ml-auto md:mr-auto flex flex-wrap items-center text-base justify-center"
        >
          <nuxt-link class="mr-5 font-bold hover:text-white" to="/">Home</nuxt-link>
          <nuxt-link class="mr-5 font-bold hover:text-white" to="/posts">Posts</nuxt-link>
          <nuxt-link class="mr-5 font-bold hover:text-white" to="/about">About</nuxt-link>
        </nav>
        <button
          class="inline-flex items-center bg-gray-800 border-0 py-1 px-3 focus:outline-none hover:bg-gray-700 rounded text-base mt-4 md:mt-0"
        >
          Login
        </button>
      </div>
    </header>
  </div>
</template>

<script>
export default {}
</script>

<style></style>
