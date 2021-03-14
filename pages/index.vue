<template>
  <div class="bg-gradient-to-b from-gray-800 to-gray-700 text-white">
    <Navbar />
    <main class="mt-5 ml-7">
      <span class="font-bold text-3xl py-3">Trending Now in World Wide</span>
      <TrendingList :list="worldTrending" />
      <span class="font-bold text-3xl">Popular Movies</span>
      <MovieShowList :list="popularMovies" />
      <span class="font-bold text-3xl">Popular TV shows</span>
      <MovieShowList :list="popularTVSeries" />
      <span class="font-bold text-3xl py-3">Upcoming Movies</span>
      <MovieShowList :list="upcomingMovies" />
    </main>
    <a href="https://nuxtjs.org">External Link to another page</a>
  </div>
</template>

<script>
import Vue from 'vue'
import Navbar from '@/components/Navbar.vue'
import TrendingList from '@/components/TrendingList.vue'
import MovieShowList from '@/components/MovieShowList.vue'

const MOVIEDB_API_URL = 'https://api.themoviedb.org/3/'

export default Vue.extend({
  components: {
    Navbar,
    TrendingList,
    MovieShowList,
  },
  data() {
    return {
      worldTrending: [],
      popularMovies: [],
      popularTVSeries: [],
      upcomingMovies: [],
    }
  },
  async fetch() {
    this.worldTrending = await fetch(
      `${MOVIEDB_API_URL}trending/all/day?api_key=${process.env.API_KEY}`
    )
      .then((res) => res.json())
      .then((resJson) => resJson.results)
    this.popularMovies = await fetch(
      `${MOVIEDB_API_URL}movie/popular?api_key=${process.env.API_KEY}`
    )
      .then((res) => res.json())
      .then((resJson) => resJson.results)
    this.popularTVSeries = await fetch(
      `${MOVIEDB_API_URL}tv/popular?api_key=${process.env.API_KEY}`
    )
      .then((res) => res.json())
      .then((resJson) => resJson.results)
    this.upcomingMovies = await fetch(
      `${MOVIEDB_API_URL}movie/upcoming?api_key=${process.env.API_KEY}`
    )
      .then((res) => res.json())
      .then((resJson) => resJson.results)
  },
})
</script>

<style>
/* .container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
} */

/* .title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
} */
</style>
