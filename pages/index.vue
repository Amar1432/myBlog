<template>
  <div>
    <HeroComponent/>
    <FeaturedPost/>
    <FooterComponent/>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: 'abcd',
    }
  },
  methods: {
    hInput(data) {
      this.email = data
    },
  },
}
</script>

<style></style>
