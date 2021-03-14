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
        />
      </div>
      <h3 v-if="movie.media_type === 'movie'">{{ movie.title }}</h3>
      <h3 v-else>{{ movie.name }}</h3>
      <h3 v-if="movie.media_type === 'movie'">{{ movie.release_date }}</h3>
      <h3 v-else>{{ movie.first_air_date }}</h3>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  name: 'TrendingList',
  props: {
    list: Array,
  },
})
</script>
