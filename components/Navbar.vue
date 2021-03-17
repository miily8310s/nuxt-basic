<template>
  <div class="pl-8 text-4xl py-3">
    <h1 class="font-bold cursor-pointer" @click="redirect">Movie Trending</h1>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  name: 'NavBar',
  methods: {
    redirect(): void {
      this.$router.push('/')
    },
  },
})
</script>
