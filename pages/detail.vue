<template>
  <div class="bg-gradient-to-b from-gray-800 to-gray-700 text-white">
    <Navbar />
    <div class="pl-8 text-4xl py-3 bg-gray-500 w-4/5 m-auto mt-5">
      <main class="flex flex-row">
        <div class="flex flex-col">
          <img
            :src="
              'https://themoviedb.org/t/p/w600_and_h900_bestv2/' +
              movie.poster_path
            "
            alt="movie.id"
          />
          <span class="text-xl m-auto">{{ movie.tagline }}</span>
          <div class="flex space-x-3 text-3xl m-auto">
            <span>Rate</span>
            <span>People</span>
          </div>
          <div class="flex space-x-3 text-3xl m-auto">
            <span>{{ movie.vote_average }}</span>
            <span>{{ movie.vote_count }}</span>
          </div>
        </div>
        <div class="flex flex-col mx-6">
          <h1 class="mb-5">
            {{ movie.title !== undefined ? movie.title : movie.name }}
          </h1>
          <div class="flex space-x-3">
            <span v-for="(genres, i) in movie.genres" :key="i" class="genres">{{
              genres.name
            }}</span>
            <span class="runtime"
              >{{
                movie.runtime ? movie.runtime : movie.episode_run_time
              }}
              min.</span
            >
            <span class="language">{{ movie.original_language }}</span>
          </div>
          <h3 class="text-3xl mb-4">Description</h3>
          <p class="text-2xl">{{ movie.overview }}</p>
        </div>
      </main>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import Navbar from '@/components/Navbar.vue'

const MOVIEDB_API_URL = 'https://api.themoviedb.org/3/'

export default Vue.extend({
  components: {
    Navbar,
  },
  data() {
    return {
      movie: {},
      id: this.$route.query.id,
      media: this.$route.query.media,
    }
  },
  async fetch() {
    switch (this.media) {
      case 'movie': {
        this.movie = await fetch(
          `${MOVIEDB_API_URL}movie/${this.id}?api_key=${process.env.API_KEY}`
        ).then((res) => res.json())
        // const data1 = await res1.json()
        // this.movie = data1
        break
      }
      case 'tv': {
        this.movie = await fetch(
          `${MOVIEDB_API_URL}tv/${this.id}?api_key=${process.env.API_KEY}`
        ).then((res) => res.json())
        // const data2 = await res2.json()
        // this.movie = data2
        break
      }
    }
  },
})
</script>
