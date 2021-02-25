<template>
  <div>
    <form @submit.prevent="">
      <div class="mb-6">
        <label>Email</label>
        <input type="text" class="border" :value="value" @input="$emit('inputh',$event.target.value)"/>
      </div>
      <div class="mb-6">
        <label>Password</label>
        <input type="password" class="border" />
      </div>
      <button class="border px-4 py-2 rounded-md">Login</button>
      <h1>{{$attrs}}</h1>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {}
  },
  props: {
    value: {
      type: String,
      default: '',
    },
  },
}
</script>

<style></style>
