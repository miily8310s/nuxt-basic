<template>
  <div class="grid grid-cols-10">
    <div
      v-for="(movie, index) in list"
      :key="index"
      class="mr-4 mt-5 relative overflow-hidden cursor-pointer"
      @click="openDetailPage(movie.id, movie.media_type)"
    >
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
      <div
        class="absolute top-0 right-0 m-3 py-2 px-3 bg-yellow-300 rounded-2xl font-bold"
      >
        {{ getAverage(movie.vote_average) }}
      </div>
      <div
        class="absolute bottom-0 left-0 p-3 bg-gray-800 w-full movie-info opacity-80"
      >
        <h3>{{ movie.media_type === 'movie' ? movie.title : movie.name }}</h3>
        <h3>
          {{
            movie.media_type === 'movie'
              ? movie.release_date
              : movie.first_air_date
          }}
        </h3>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  name: 'TrendingList',
  props: {
    list: {
      type: Array,
      required: true,
    },
  },
  methods: {
    getAverage(average: string) {
      if (Number.isInteger(average)) {
        return average + '.0'
      }
      return average
    },
    openDetailPage(id: string, media: string) {
      this.$router.push(`detail?id=${id}&media=${media}`)
    },
  },
})
</script>
