<template>
  <div class="home">
    <Hero />     
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data(){
    return {
      movies: [],
    }
  },
  async fetch(){
    await this.getMovies()
  },
  methods: {
    async getMovies() {
      const data = axios.get('https://api.themoviedb.org/3/movie/now_playing?api_key=b810837502842dbe5c8955ffa74cf870&language=en-US&page=1')
      const result = await data;
      result.data.results.forEach((movie) => {
        this.movies.push(movie)
      })
      // console.log(result.data.results)
      // console.log(this.movies)
    }
  }  
}
</script>
