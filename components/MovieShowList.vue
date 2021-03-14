<template>
  <div class="grid grid-cols-10">
    <div v-for="(movie, index) in list" :key="index" class="mr-4 mt-5">
      <div>
        <img
          :src="
            'https://themoviedb.org/t/p/w600_and_h900_bestv2/' +
            movie.poster_path
          "
          alt="movie.title"
          class="w-96"
        />
      </div>
      <h3 v-if="movie.title !== ''">{{ movie.title }}</h3>
      <h3 v-if="movie.name !== ''">{{ movie.name }}</h3>
      <h3 v-if="movie.title !== ''">{{ movie.release_date }}</h3>
      <h3 v-if="movie.name !== ''">{{ movie.first_air_date }}</h3>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  name: 'MovieShowList',
  props: {
    list: Array,
  },
})
</script>

<style scoped>
.flex {
  overflow: hidden;
  overflow-x: scroll;
  min-width: 500px;
}
</style>
