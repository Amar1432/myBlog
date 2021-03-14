<template>
  <div class="w-full">
    <div class="border-2 border-gray-800 rounded-lg overflow-hidden">
      <img
        class="lg:h-48 md:h-36 w-full object-cover object-center"
        :src="image"
        alt="blog"
      />
      <div class="p-6 pb-0">
        <h2
          class="tracking-widest text-xs title-font font-medium text-gray-500 mb-1"
        >
          {{ category }}
        </h2>
        <h1 class="title-font text-lg font-medium text-white">
          {{ title }}
        </h1>
        <p class="leading-relaxed my-3">
          {{ description.replace(/^(.{50}[^\s]*).*/, "$1") }}...
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['title', 'description', 'image', 'category'],
}
</script>

<style></style>
